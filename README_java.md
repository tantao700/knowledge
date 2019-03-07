# java tools

### tail
- tail -300f catalina.out # 倒数300 行实时监听文件写入模式

### grep 
- grep forest f.txt     #文件查找
- grep forest f.txt cpf.txt #多文件查找
- grep 'log' /home/admin -r -n #目录下查找所有符合关键字的文件
- cat f.txt | grep -i shopbase
- grep 'shopbase' /home/admin -r -n --include *.{vm,java} #指定文件后缀
- grep 'shopbase' /home/admin -r -n --exclude *.{vm,java} #反匹配
- seq 10 | grep 5 -A 3    #上匹配
- seq 10 | grep 5 -B 3    #下匹配
- seq 10 | grep 5 -C 3    #上下匹配，平时用这个就妥了
- cat f.txt | grep -c 'SHOPBASE'

### awk
#### 基础命令
- awk '{print $4,$6}' f.txt
- awk '{print NR,$0}' f.txt cpf.txt
- awk '{print FNR,$0}' f.txt cpf.txt
- awk '{print FNR,FILENAME,$0}' f.txt cpf.txt
- awk '{print FILENAME,"NR="NR,"FNR="FNR,"$"NF"="$NF}' f.txt cpf.txt
- echo 1:2:3:4 | awk -F: '{print $1,$2,$3,$4}

#### 内建变量
NR:NR表示从awk开始执行后，按照记录分隔符读取的数据次数，默认的记录分隔符为换行符，因此默认的就是读取的数据行数，NR可以理解为Number of Record的缩写。

FNR:在awk处理多个输入文件的时候，在处理完第一个文件后，NR并不会从1开始，而是继续累加，因此就出现了FNR，每当处理一个新文件的时候，FNR就从1开始计数，FNR可以理解为File Number of Record。

NF: NF表示目前的记录被分割的字段的数目，NF可以理解为Number of Field

### find
- sudo -u admin find /home/admin /tmp /usr -name \*.log(多个目录去找)
- find . -iname \*.txt(大小写都匹配)
- find . -type d(当前目录下的所有子目录)
- find /usr -type l(当前目录下所有的符号链接)
- find /usr -type l -name "z*" -ls(符号链接的详细信息 eg:inode,目录)
- find /home/admin -size +250000k(超过250000k的文件，当然+改成-就是小于了)
- find /home/admin f -perm 777 -exec ls -l {} \; (按照权限查询文件)
- find /home/admin -atime -1  1天内访问过的文件
- find /home/admin -ctime -1  1天内状态改变过的文件
- find /home/admin -mtime -1  1天内修改过的文件
- find /home/admin -amin -1  1分钟内访问过的文件
- find /home/admin -cmin -1  1分钟内状态改变过的文件
- find /home/admin -mmin -1  1分钟内修改过的文件

### pgm - 批量查询vm-shopbase满足条件的日志
- pgm -A -f vm-shopbase 'cat /home/admin/shopbase/logs/shopbase.log.2017-01-17|grep 2069861630'

### tsar
tsar是Ali的采集工具。很好用, 将历史收集到的数据持久化在磁盘上，所以我们快速来查询历史的系统数据。当然实时的应用情况也是可以查询的啦。大部分机器上都有安装。
- tsar  ##可以查看最近一天的各项指标
- tsar --live ##可以查看实时指标，默认五秒一刷
- tsar -d 20161218 ##指定查看某天的数据，貌似最多只能看四个月的数据
- tsar --mem
- tsar --load
- tsar --cpu #当然这个也可以和-d参数配合来查询某天的单个指标的情况

### top
- ps -ef | grep java
- top -H -p pid

### other
- netstat -nat|awk  '{print $6}'|sort|uniq -c|sort -rn #查看当前连接，注意close_wait偏高的情况，比如如下

## 排查利器
- btrace - https://github.com/btraceio/btrace
- Greys 
  - sc -df xxxx 输出当前类的详情,包括源码位置和classloader结构
- arthas
- javOSize
  - classes:过修改了字节码，改变了类的内容，即时生效。
- JProfiler
- eclipseMAT - http://www.eclipse.org/mat/
- zprofiler - 替代 eclipseMAT https://zprofiler.alibaba-inc.com
- CHLSDB 
  - sudo -u admin /opt/taobao/java/bin/java -classpath /opt/taobao/java/lib/sa-jdi.jar sun.jvm.hotspot.CLHSDB
  - http://rednaxelafx.iteye.com/blog/1847971

## VM options
- -XX:+TraceClassLoading #你的类到底是从哪个文件加载进来的？
- -XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=/home/admin/logs/java.hprof #

## jar包冲突
- mvn dependency:tree > ~/dependency.txt #打出所有依赖
- mvn dependency:tree -Dverbose -Dincludes=groupId:artifactId  #只打出指定groupId和artifactId的依赖关系
- -XX:+TraceClassLoading #vm启动脚本加入。在tomcat启动脚本中可见加载类的详细信息
- -verbose #vm启动脚本加入。在tomcat启动脚本中可见加载类的详细信息
- greys:sc #greys的sc命令也能清晰的看到当前类是从哪里加载过来的
- tomcat-classloader-locate 
  - 通过以下url可以获知当前类是从哪里加载的
  - curl http://localhost:8006/classloader/locate?class=org.apache.xerces.xs.XSObject
- ALI-TOMCAT
  - @务观
  - 列出容器加载的jar列表
  - curl http://localhost:8006/classloader/jars
  - 列出当前当当前类加载的实际jar包位置，解决类冲突时有用
    - curl http://localhost:8006/classloader/locate?class=org.apache.xerces.xs.XSObject

# other
- gpref - http://www.atatech.org/articles/33317
- dmesg 
  - 如果发现自己的java进程悄无声息的消失了，几乎没有留下任何线索，那么dmesg一发，很有可能有你想要的。
  - sudo dmesg|grep -i kill|less
- RateLimiter
  - 想要精细的控制QPS? 比如这样一个场景，你调用某个接口，对方明确需要你限制你的QPS在400之内你怎么控制？这个时候RateLimiter就有了用武之地



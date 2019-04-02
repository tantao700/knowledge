# 排查利器
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
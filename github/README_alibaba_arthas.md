# Arthas-Java诊断工具

github:https://github.com/alibaba/arthas
document:https://alibaba.github.io/arthas/

## 常用命令

### 基础命令

help——查看命令帮助信息
cls——清空当前屏幕区域
session——查看当前会话的信息
reset——重置增强类，将被 Arthas 增强过的类全部还原，Arthas 服务端关闭时会重置所有增强过的类
version——输出当前目标 Java 进程所加载的 Arthas 版本号
quit——退出当前 Arthas 客户端，其他 Arthas 客户端不受影响
shutdown——关闭 Arthas 服务端，所有 Arthas 客户端全部退出
keymap——Arthas快捷键列表及自定义快捷键
  
### jvm相关

dashboard——当前系统的实时数据面板
thread——查看当前 JVM 的线程堆栈信息
jvm——查看当前 JVM 的信息
sysprop——查看和修改JVM的系统属性
New! getstatic——查看类的静态属性

### class/classloader相关

sc——查看JVM已加载的类信息
sm——查看已加载类的方法信息
dump——dump 已加载类的 byte code 到特定目录
redefine——加载外部的.class文件，redefine到JVM里
jad——反编译指定已加载类的源码
classloader——查看classloader的继承树，urls，类加载信息，使用classloader去getResource

### monitor/watch/trace相关

monitor——方法执行监控
watch——方法执行数据观测
trace——方法内部调用路径，并输出方法路径上的每个节点上耗时
stack——输出当前方法被调用的调用路径
tt——方法执行数据的时空隧道，记录下指定方法每次调用的入参和返回信息，并能对这些不同的时间下调用进行观测
请注意，这些命令，都通过字节码增强技术来实现的，会在指定类的方法中插入一些切面来实现数据统计和观测，因此在线上、预发使用时，请尽量明确需要观测的类、方法以及条件，诊断结束要执行 shutdown 或将增强过的类执行 reset 命令。

### options

options——查看或设置Arthas全局开关

## 管道 - Arthas支持使用管道对上述命令的结果进行进一步的处理，如sm org.apache.log4j.Logger | grep
        
grep——搜索满足条件的结果
plaintext——将命令的结果去除颜色
wc——按行统计输出结果	
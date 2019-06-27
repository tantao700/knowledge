# jvm arguments 

### verbose:gc / -XX:+printGC ==> 输出jvm里面的GC信息
```
[Full GC 178K->99K(1984K)， 0.0253877 secs]

1.178K          :GC之[前] 内存容量
2.99K           :GC之[后] 内存容量
3.1984K         :内存总容量
4.0253877 secs  :执行时间
``` 

### -XX:+PrintGCDetails ==> 打印GC的详细信息

```
–Heap
– def new generation   total 13824K, used 11223K [0x27e80000, 0x28d80000, 0x28d80000)
–  eden space 12288K,  91% used [0x27e80000, 0x28975f20, 0x28a80000)
–  from space 1536K,   0% used [0x28a80000, 0x28a80000, 0x28c00000)
–  to   space 1536K,   0% used [0x28c00000, 0x28c00000, 0x28d80000)
– tenured generation   total 5120K, used 0K [0x28d80000, 0x29280000, 0x34680000)
–   the space 5120K,   0% used [0x28d80000, 0x28d80000, 0x28d80200, 0x29280000)
– compacting perm gen  total 12288K, used 142K [0x34680000, 0x35280000, 0x38680000)
–   the space 12288K,   1% used [0x34680000, 0x346a3a90, 0x346a3c00, 0x35280000)
–    ro space 10240K,  44% used [0x38680000, 0x38af73f0, 0x38af7400, 0x39080000)
–    rw space 12288K,  52% used [0x39080000, 0x396cdd28, 0x396cde00, 0x39c80000)

1.new generation    就是堆内存里面的新生代
2.eden space        就是堆内存里面的新生代
3.from space 和to space 是幸存者的两个区
4.tenured generation 就表示老年代
5.compacting perm   表示永久代
```

### -XX:+PrintGCTimeStamps ==> 打印GC发生的时间戳
```
289.556: [GC [PSYoungGen: 314113K->15937K(300928K)] 405513K->107901K(407680K), 0.0178568 secs] [Times: user=0.06 sys=0.00, real=0.01 secs] 

293.271: [GC [PSYoungGen: 300865K->6577K(310720K)] 392829K->108873K(417472K), 0.0176464 secs] [Times: user=0.06 sys=0.00, real=0.01 secs]
```

### -X:loggc:log/gc.log ==> 指定输出gc.log的文件位置
### -XX:+PrintHeapAtGC  ==> 表示每次GC后，都打印堆的信息
### -XX:+TraceClassLoading ==> 监控类的加载
```
•[Loaded java.lang.Object from shared objects file]
•[Loaded java.io.Serializable from shared objects file]
•[Loaded java.lang.Comparable from shared objects file]
•[Loaded java.lang.CharSequence from shared objects file]
•[Loaded java.lang.String from shared objects file]
•[Loaded java.lang.reflect.GenericDeclaration from shared objects file]
•[Loaded java.lang.reflect.Type from shared objects file]
```

### -XX:+PrintClassHistogram ===> 跟踪参数
这个按下Ctrl+Break后，就会打印一下信息
```
num     #instances         #bytes  class name

----------------------------------------------

   1:        890617      470266000  [B

   2:        890643       21375432  java.util.HashMap$Node

   3:        890608       14249728  java.lang.Long

   4:            13        8389712  [Ljava.util.HashMap$Node;

   5:          2062         371680  [C

   6:           463          41904  java.lang.Class
```

### -Xmx -Xms
    这个就表示设置堆内存的最大值和最小值

### -Xmn
    设置新生代的内存大小。

### -XX:NewRatio
    新生代和老年代的比例。比如：1：4，就是新生代占五分之一。

### -XX:SurvivorRatio        
    设置两个Survivor区和eden区的比例。比如：2：8 ，就是一个Survivor区占十分之一

### -XX:+HeapDumpOnOutMemoryError
    发生OOM时，导出堆的信息到文件

### -XX:+HeapDumpPath   
    表示，导出堆信息的文件路径

### -XX:OnOutOfMemoryError
    当系统产生OOM时，执行一个指定的脚本，这个脚本可以是任意功能的。比如生成当前线程的dump文件，或者是发送邮件和重启系统

### -XX:PermSize -XX:MaxPermSize
    设置永久区的内存大小和最大值。永久区内存用光也会导致OOM的发生。

### -Xss 
    设置栈的大小。栈都是每个线程独有一个，所有一般都是几百k的大小。   
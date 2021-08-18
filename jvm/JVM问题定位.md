### 相关工具

- jps：查看java进程
    - -v：输出jvm启动参数
- jstack：打印java进程的堆栈信息
    - -l：显示关于锁的附加信息
- jstat：打印jvm运行时信息，示例 jstat -gc pid 2s 1打印gc信息每两秒一次打印一次
    - 打印参数
        - class   #显示有关类加载器行为的统计信息。
        - compiler  #显示有关Java HotSpot VM即时编译器行为的统计信息。
        - gc  #显示有关垃圾回收堆的行为的统计信息。
        - gccapacity  #各个垃圾回收代容量(young,old,perm)和他们相应的空间统计。
        - gccause   #垃圾收集统计概述（同-gcutil），附加最近两次垃圾回收事件的原因。
        - gcnew  #显示新生代行为的统计信息。gcnewcapacity  #显示有关新生代及其相应空间大小的统计信息。
        - gcold   #显示有关老年代和metaspace统计信息的统计信息。
        - gcoldcapacity  #年老代行为统计。
        - gcmetacapacity  #显示有关元空间大小的统计信息。
        - gcutil  #显示关于垃圾收集统计信息的摘要。
        - printcompilation   #显示Java HotSpot VM编译方法统计信息。
    - 其他参数
        - t #jstat -gc -t pid 2s 1，表示打印时每一行信息前加一列从jvm启动开始经过的时间
        - h #jstat -gc -h 2 pid 2s 5，表示打印时每几行打印一次表头，为0时只打印一次
    - 打印分析
        - gc
          |名称|简介|
          |---|---|
          |S0C|当前survivor0区容量（kB）。 |
          |S1C|当前survivor1区容量（kB）。 |
          |S0U|survivor0区已使用的容量（KB） |
          |S1U|survivor1区已使用的容量（KB）|
          |EC|Eden区的总容量（KB） |
          |EU|当前Eden区已使用的容量（KB） |
          |OC|Old空间容量（kB）。 |
          |OU|Old区已使用的容量（KB） |
          |MC|Metaspace空间容量（KB） |
          |MU|Metacspace使用量（KB） |
          |CCSC|压缩类空间容量（kB）。|
          |CCSU|压缩类空间使用（kB）。|
          |YGC|新生代垃圾回收次数|
          |YGCT|新生代垃圾回收时间|
          |FGC|老年代 full GC垃圾回收次数|
          |FGCT|老年代垃圾回收时间|
          |GCT|垃圾回收总消耗时间|
        - gcnew：gc中与新生代有关的部分
        - gcold：gc中与老年代有关的部分
        - gccapacity
          |名称|简介|
          |---|---|
          |NGCMN|年轻代(young)中初始化(最小)的大小(KB)|
          |NGCMX|年轻代(young)的最大容量 (KB)|
          |NGC|年轻代(young)中当前的容量 (KB)|
          |S0C|年轻代中第一个survivor（幸存区）的容量 (KB)|
          |S1C|年轻代中第二个survivor（幸存区）的容量 (KB)|
          |EC|年轻代中Eden（伊甸园）的容量 (KB)|
          |OGCMN|old代中初始化(最小)的大小 (KB)|
          |OGCMX|old代的最大容量(KB)|
          |OGC|old代当前新生成的容量 (KB)|
          |OC|Old代的容量 (KB)|
          |PGCMN|perm代中初始化(最小)的大小 (KB) ，jdk1.8改为了MCMN|
          |PGCMX|perm代的最大容量 (KB)，jdk1.8改为了MCMX|
          |PGC|perm代当前新生成的容量 (KB)|
          |PC|Perm(持久代)的容量 (KB)|
          |YGC|从应用程序启动到采样时年轻代中gc次数|
          |FGC|从应用程序启动到采样时old代(全gc)gc次数|
          |MC|Metaspace空间（KB）|
          |CCSMN|压缩类空间最小容量（kB）。|
          |CCSMX|压缩类空间最大容量（kB）。|
          |CCSC|压缩类空间容量（kB）。|
        - gcoldcapacity：略
        - gcnewcapacity：略
        - gcutil选项
          |名称|简介|
          |---|---|
          |S0|幸存者0空间利用率占空间当前容量的百分比。|
          |S1|幸存者1空间利用率占空间当前容量的百分比。|
          |E|Eden空间利用率占空间当前容量的百分比。|
          |O|旧空间利用率占空间当前容量的百分比。|
          |M|Metaspace利用率占空间当前容量的百分比。|
          |CCS|压缩类空间利用率，以百分比表示。|
          |YGC|年轻一代GC事件的数量。|
          |YGCT|年轻一代的垃圾收集时间(S)。|
          |FGC|完整的GC事件的数量。|
          |FGCT|完整的垃圾收集时间(S)。|
          |GCT|垃圾收集总时间(S)。| 
        - class
          |名称|简介|
          |---|---|
          |Loaded|加载class的数量|
          |Bytes|class字节大小|
          |Unloaded|卸载的类数。|
          |Bytes|卸载的千字节数。|
          |Time|执行类加载和卸载操作的时间。|
        - compiler
          |名称|简介|
          |---|---|
          |Compiled|执行的编译任务数。|
          |Failed|编译任务的失败数量。|
          |Invalid|无效的编译任务数。|
          |Time|执行编译任务的时间。|
          |FailedType|编译最后一次失败编译的类型。|
          |FailedMethod|上次失败编译的类名称和方法|
- jmap
    - option
        - 不使用：查看进程的内存映像信息
        - heap：显示Java堆详细信息
        - histo[:live]：显示堆中对象的统计信息
        - clstats：打印类加载器信息
        - finalizerinfo： 显示在F-Queue队列等待Finalizer线程执行finalizer方法的对象
        - dump:format=b,file=xx.xx：生成堆转储快照
        - F： 当-dump没有响应时，使用-dump或者-histo参数. 在这个模式下,live子参数无效
- jcmd
    - help：显示可以使用的命令
    - GC.heap_dump filename=Myheapdump：生成dump文件，同jmap -dump
    - GC.class_histogram filename=Myheaphistogram：打印堆直方图，效果同jmap -histo
    - VM.flags：显示VM所有标志参数，没有配置时会打印默认值，效果同jino -flags
- jinfo
    - help：查看可用指令
    - flag<name>：打印指定配置的值
    - flags：打印所有VM参数
    - flag[+|-]<name>：指定配置生效或失效
    - flag<name>=<value>：设置指定jvm参数的值
    - sysprops：打印java系统配置
    - 不使用：打印以上所有值
- jvisualvm：可用来分析dump文件
- MAT：同上

### 相关启动参数

- -verbose:[option]：输出jvm运行信息
    - class：打印类装载信息
    - gc：打印gc信息
    - jni：打印java本地方法调用信息

### 死锁定位

1. 用jps查询java进程的pid
2. 用jstack查看堆栈信息
3. 可以用jconsole进行死锁检测

### FGC问题定位
1. 用jstat、jmap等工具找到问题所在

2. 根据问题现象推测原因
    - 大对象：系统一次性加载了过多数据到内存中（比如SQL查询未做分页），导致大对象进入了老年代。
    - 内存泄漏：频繁创建了大量对象，但是无法被回收（比如IO对象使用完后未调用close方法释放资源），先引发FGC，最后导致OOM.
    - 程序频繁生成一些长生命周期的对象，当这些对象的存活年龄超过分代年龄时便会进入老年代，最后引发FGC. （即本文中的案例）
    - 程序BUG导致动态生成了很多新类，使得 Metaspace 不断被占用，先引发FGC，最后导致OOM.
    - 代码中显式调用了gc方法，包括自己的代码甚至框架中的代码。
    - JVM参数设置问题：包括总内存大小、新生代和老年代的大小、Eden区和S区的大小、元空间大小、垃圾回收算法等等。
3. 根据推测的原因修改 [代码 | 配置] 并测试


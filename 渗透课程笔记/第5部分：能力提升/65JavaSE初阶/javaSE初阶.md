# 第1章-初识JAVA

   计算机语言的发展历史

  计算机编程语言的发展，是随着计算机本身硬件发展而发展的。硬件速度越快、体积越小、成本越低，应用到人类社会的场景就会越多，那么所需要的算法就会越复杂，也就要求计算机编程语言越高级。最初重达几十吨但一秒只能运算5000次的ENIAC(世界上第一台计算机)，只能做非常小的应用，比如：某些情况的弹道计算。现在任何一个人的手机运算能力都可以秒杀那个年代地球上所有计算机运算能力的总和。计算机编程语言的发展历经了从低级到高级发展。发展的核心思想就是“让人更容易编程”。越容易使用的语言，就有越多人使用；越多人使用，就有越多协作；越多协作，就可以创造越复杂的物体；计算机语言经历了三代：第一代是机器语言，第二代是汇编语言，第三代是高级语言。

 

![img](https://s2.loli.net/2023/09/01/dRG8FWCuYkKBDrX.jpg)

 

【1】第一代：机器语言（相当于人类的原始阶段） 

 

机器语言是机器指令的集合，机器指令展开来讲就是一台机器可以正确执行的命令。电子计算机的机器指令是一列二进制数字。计算机将之转变为一列高低电平，以使计算机的电子器件受到驱动，从而进行运算。上面所说的计算机，指的是可以执行机器指令，进行运算的机器。这是早期计算机的概念。早期的程序设计均使用机器语言。程序员们将用 0、1 数字编程的程序代码打在纸袋或卡片上，1打孔，0不打孔，再将程序通过纸带机或卡片机输入计算机，从而进行运算。 

应用8086CPU完成运算s=768+12288-1280，机器码如下: 

 

![img](https://s2.loli.net/2023/09/01/NMKeXPzqykOBajC.jpg)

 

假如将程序错写成以下的错误，请你找出错误: 

 

![img](https://s2.loli.net/2023/09/01/MDLzvyJiFs3ComA.jpg)

 

书写和阅读机器码程序不是一件简单的工作，要记住所有抽象的二进制码。上面只是一个非常简单的小程序，就暴露出机器码的晦涩难懂和不易查错。写如此小的一个程序尚且如此，实际上一个有用的程序至少要有几十行的机器码。那么，情况将会怎么样呢？

 

在显示器输出“welcome to masm”，机器码如下： 

看到这样的程序，你有什么感想？如果程序里有一个“1”被误写成为“0”，又如何去查找错误呢？

 

【2】第二代：汇编语言（相当于人类的手工业阶段）

 

为了编程的方便，以及解决更加复杂的问题。程序员开始改进机器语言，使用英文缩写的助记符来表示基本的计算机操作。这些助记符构成了汇编语言的基础。如下是一些常见的汇编语言助记符(单词)比如：mov，add，sub之类，这样人更容易使用了。识别几百、几千个单词，感觉要比几百几千个数字，美妙多了。汇编语言相当于人类的手工业社会，需要技术极其娴熟的工匠，但是开发效率也非常低。汇编语言虽然能编写高效率的程序，但是学习和使用都不是易事，并且很难调试。另一个复杂的问题，汇编语言以及早期的计算机语言（Basic、Fortran等）没有考虑结构化设计原则，而是使用goto语句来作为程序流程控制的主要方法。这样做的后果是：一大堆混乱的调转语句使得程序几乎不可能被读懂。对于那个时代的程序员，能读懂上个月自己写的代码都成为一种挑战。 汇编语言仍然应用于工业电子编程领域、软件的加密解密、计算机病毒分析等。 

下面以Masm软件为例，编写一个简单的“hello world!”程序。 

![img](https://s2.loli.net/2023/09/01/D9ULEiMp56WkAwY.jpg)

 

【3】第三代：高级语言（相当于人类的工业阶段）

  对于简单的任务，汇编语言可以胜任。但是随着计算机的发展，渗透到了工作生活的更多的方面，一些复杂的任务出现了，汇编语言就显得力不从心（应该说是程序员使用汇编语言解决复杂问题出现了瓶颈）。于是，出现了高级语言。像我们熟知的C、C++、Java等等都是高级语言。

高级语言允许程序员使用接近日常英语的指令来编写程序。例如下图所示: 

 

![img](https://s2.loli.net/2023/09/01/YpAjzSwbXHDtsUk.jpg)

### JAVA简史

**【1】SUN公司** 

美国SUN(Stanford University Network)公司在中国大陆的正式中文名为“太阳计算机系统（中国）有限公司” ，在台湾中文名为“升 阳电脑公司”。 

**【2】Java为什么被发明** 

Green项目。 

应用环境：像电视盒这样的消费类电子产品 

要求： 语言本身是中立的，也就是跨平台 

  1996年Java第一次发布就引起了人们的极大兴趣。关注Java的人士不仅限于计算机出版界， 还有诸如《纽约时报》《华盛顿邮报》《商业周刊》这样的主流媒体。Java 是第一种也是唯一种在National Public Radio上占用了10分钟时间来进行介绍的程序设计语言，并且还得到了$100000000的风险投资基金。这些基金全部用来支持用这种特别的计算机语言开发的产品。重温那些令人兴奋的日子是很有意思的。我们将简要地介绍一下Java语言的发展历史： 

  Java的历史要追溯到1991年，由Patrick Naughton 及其伙伴James Gosling (一个全能的计算机奇才)带领的Sun公同的工程师小组想要设计一种小型的计算机语言，主要用于像有线电视转换盒这类的消费设备。由于这些消费设备的处理能力和内存都很有限，所以语言必须非常小且能够生成非常紧凑的代码。另外，由于不同的厂商会选择不同的中央处理器(CPU)，因此这种语言的关键是不能与任何特定的体系结构捆绑在一起。这个项目被命名为"Green"。

   所有就要求有这样的一种代码： 代码短小、紧凑且与平台无关。但是，Sun公司的人都有UNIX的应用背景。因此，所开发的语言以C++为基础。 是Gosling率先创造了这个语言，把这种语言称为“Oak"(这么起名的原因大概是因为他非常喜欢自己办公室外的橡树)。Sun 公司的人后来发现Oak是一种已有的计算机语言的名字，于是，将其改名为Java。 

![img](https://image.201068.xyz/assets/clip_image012.jpg)     

​      

**【3】Java的发明人** 

James Gosling           ![img](https://image.201068.xyz/assets/clip_image014.jpg) 

 

 

**【4】经历阶段** 

1991年，James Gosling在SUN公司的工程师小组想要设计这样一种小型计算机语言。该语言主要用于像电视盒这样的消费类电子产品。另外，由于不同的厂商选择不同的CPU和操作系统，因此，要求该语言不能和特定的体系结构绑在一起，要求语言本身是中立的，也就是跨平台的。所以，将这个语言命名为“Green”，类似于绿色软件的意思。后来，改名为Oak，橡树的意思。改名后发现已经有一种语言叫这个名字了，再改名叫Java。Java语言发展到今天经历了一系列的过程： 

 1991年，SUN公司的Green项目，Oak 

 1995年，推出Java测试版 

 1996年，JDK1.0 

 1997年，JDK1.1 

 1998年，JDK1.2，大大改进了早期版本缺陷，是一个革命性的版本，更名为Java2。 

 2004年，J2SE 5.0 (1.5.0) Tiger老虎 成为Java语言发展史上的又一里程碑。为了表示该版本的重要性，J2SE1.5更名为Java SE 5.0 

 2005年，Java的各种版本已经更名，以取消其中的数字"2"： J2ME更名为Java ME， J2SE更名为Java SE， J2EE更名为Java EE； 

 2006年，J2SE 6.0 (1.6.0) Mustang野马

 2009年，甲骨文(oracle)收购SUN，交易高达价格74亿 

 2011年，JavaSE7.0  Dolphin海豚

 2014年，JavaSE8.0 

2017年，JAVA 9.0 

 2018年3月，JAVA 10 

 2018年9月，JAVA 11 

 2019年3月，JAVA 12 

 2019年9月，JAVA 13 

 2020年3月，JAVA 14 

  注意：SUN公司已经被oracle公司收购，目前每半年更新一次java的版本。但是，企业中的主流仍然以7和8为主。对于初学者，应该以企业主流应用版本为核心进行学习，没有必须在此处追求最新版本。 

​     ![img](https://image.201068.xyz/assets/clip_image016.jpg)

 

 

**【5】不同版本JDK说明** 

JDK Version 1.1 

  于1997-02-19发行。 

  引入的新特性包括： 

  引入JDBC（Java Database Connectivity）； 

  支持内部类； 

  引入Java Bean； 

  引入RMI（Remote Method Invocation）； 

  引入反射（仅用于内省）。

J2SE Version 1.2 

  开发代号为Playground（操场），于1998-12-08发行。 

  引入的新特性包括： 

  引入集合（Collection）框架； 

  对字符串常量做内存映射；

  引入JIT（Just In Time）编译器； 

  引入对打包的Java文件进行数字签名； 

  引入控制授权访问系统资源的策略工具；

  引入JFC（Java Foundation Classes），包括Swing 1.0、拖放和Java 2D类库； 

  引入Java 插件； 

  在JDBC中引入可滚动结果集、BLOB、CLOB、批量更新和用户自定义类型；

  在Applet中添加声音支持。 

J2SE Version 1.3 

 开发代号为Kestrel（红隼），于2000-05-08发行。 

  引入的新特性包括： 

  引入Java Sound API； 

  jar文件索引； 

  对Java的各个方面都做了大量优化和增强。 

J2SE Version 1.4 

  开发代号为Merlin（隼），于2004-02-06发行（首次在JCP下发行）。 

  引入的新特性包括: 

  XML处理； 

  Java打印服务； 

  引入Logging API； 

  引入Java Web Start； 

  引入JDBC 3.0 API； 

  引入断言； 

  引入Preferences API； 

  引入链式异常处理； 

  支持IPv6； 

  支持正则表达式； 

  引入Image I/O slot machine API。 

Java Version SE 5.0 

  开发代号为Tiger（老虎），于2004-09-30发行。 

  引入的新特性包括: 

  引入泛型； 

  增强循环，可以使用迭代方式； 

  自动装箱与自动拆箱； 

  类型安全的枚举； 

  可变参数； 

  静态引入； 

  元数据（注解）； 

  引入Instrumentation。 

Java Version SE 6 

  开发代号为Mustang（野马），于2006-12-11发行。 

  引入的新特性包括： 

  支持脚本语言； 

  引入JDBC 4.0 API； 

  引入Java Compiler API； 

  可插拔注解； 

  增加对Native PKI(Public Key Infrastructure)、Java GSS(Generic Security Service)、Kerberos和LDAP(Lightweight Directory Access  Protocol)的支持； 

  继承Web Services； 

  做了很多优化。 

Java Version SE 7 

  开发代号是Dolphin（海豚），于2011-07-28发行。 

  引入的新特性包括： 

  switch语句块中允许以字符串作为分支条件；

  在创建泛型对象时应用类型推断；

  在一个语句块中捕获多种异常；

  支持动态语言； 

  支持try-with-resources； 

  引入Java NIO.2开发包； 

  数值类型可以用2进制字符串表示，并且可以在字符串表示中添加下划线； 

  钻石型语法； 

  null值的自动处理。

Java Version SE 8 

  开发代号是Spider（蜘蛛），于2014-03-18发行。 

  支持 lambda支持； 

  增强日期与时间API的功能； 

  对垃圾回收的性能也进行了改进；

  并且移除了permgen区。 

  Lambdas表达式与Functional接口 

  接口的默认与静态方法 

  方法引用 

  重复注解 

  更好的类型推测机制 

  扩展注解的支持 

![img](https://s2.loli.net/2023/09/01/zaZJ456ELuDmfGq.gif) 

### JAVA体系结构

**JavaSE****（Java Standard Edition）：标准版，定位在个人计算机上的应用** 

这个版本是Java平台的核心，它提供了非常丰富的API来开发一般个人计算机上的应用程序，包括用户界面接口AWT及Swing，网络功能与国际化、图像处理能力以及输入输出支持等。在上世纪90年代末互联网上大放异彩的Applet也属于这个版本。Applet后来为Flash取代，Flash即将被HTML5取代。

**JavaEE****（Java Enterprise Edition）：企业版，定位在服务器端的应用** 

JavaEE是JavaSE的扩展，增加了用于服务器开发的类库。如：JDBC是让程序员能直接在Java内使用的SQL的语法来访问数据库内的数据；Servlet能够延伸服务器的功能，通过请求-响应的模式来处理客户端的请求；JSP是一种可以将Java程序代码内嵌在网页内的技术； 

**JavaME****（Java Micro Edition）：微型版，定位在消费性电子产品的应用上** 

JavaME是JavaSE的内伸，包含J2SE的一部分核心类，也有自己的扩展类,增加了适合微小装置的类库：javax.microedition.io.*等。该版本针对资源有限的电子消费产品的需求精简核心类库，并提供了模块化的架构让不同类型产品能够随时增加支持的能力。

​             

![img](https://s2.loli.net/2023/09/01/O7rE9YDTWxFGVy5.jpg)         

### JAVA的特性和优势

 **跨平台/可移植性**

这是Java的核心优势。Java在设计时就很注重移植和跨平台性。比如：Java的int永远都是32位。不像C++可能是16，32，可能是根据编译器厂商规定的变化。这样的话程序的移植就会非常麻烦。 

 

 **安全性** 

Java适合于网络/分布式环境，为了达到这个目标，在安全性方面投入了很大的精力，使Java可以很容易构建防病毒，防篡改的系统。 

 

 **面向对象** 

面向对象是一种程序设计技术，非常适合大型软件的设计和开发。由于C++为了照顾大量C语言使用者而兼容了C，使得自身仅仅成为了带类的C语言，多少影响了其面向对象的彻底性！Java则是完全的面向对象语言。 

 

 **简单性** 

Java就是C++语法的简化版，我们也可以将Java称之为“C++-”。跟我念“C加加减”，指的就是将C++的一些内容去掉；比如：头文件，指针运算，结构，联合，操作符重载，虚基类等等。同时，由于语法基于C语言，因此学习起来完全不费力。 

 

 **高性能**

Java最初发展阶段，总是被人诟病“性能低”；客观上，高级语言运行效率总是低于低级语言的，这个无法避免。Java语言本身发展中通过虚拟机的优化提升了几十倍运行效率。比如，通过JIT(JUST IN TIME)即时编译技术提高运行效率。 将一些“热点”字节码编译成本地机器码，并将结果缓存起来，在需要的时候重新调用。这样的话，使Java程序的执行效率大大提高，某些代码甚至接待C++的效率。 

因此，Java低性能的短腿，已经被完全解决了。业界发展上，我们也看到很多C++应用转到Java开发，很多C++程序员转型为Java程序员。 

 

 **分布式** 

Java是为Internet的分布式环境设计的，因为它能够处理TCP/IP协议。事实上，通过URL访问一个网络资源和访问本地文件是一样简单的。Java还支持远程方法调用(RMI,Remote Method Invocation)，使程序能够通过网络调用方法。 

 

 **多线程** 

多线程的使用可以带来更好的交互响应和实时行为。 Java多线程的简单性是Java成为主流服务器端开发语言的主要原因之一。

 

 **健壮性** 

Java是一种健壮的语言，吸收了C/C++ 语言的优点，但去掉了其影响程序健壮性的部分（如：指针、内存的申请与释放等）。Java程序不可能造成计算机崩溃。即使Java程序也可能有错误。如果出现某种出乎意料之事，程序也不会崩溃，而是把该异常抛出，再通过异常处理机制加以处理。 

 

总结：一句话：java很好！ 

但是，并不是说学习了java，以后所有的东西都要用java开发了：某些领域其他语言有更出色的表现，比如，Objective C和后来的Swift在iOS设备上就有着无可取代的地位。浏览器中的处理几乎完全由JavaScript掌控。Windows程序通常都用C++或C#编写。Java在服务器端编程和跨平台客户端应用领域则很有优势。 

只能说，不同的语言之间，平分秋色！

 

 

### 核心机制

#### 垃圾收集机制

垃圾收集的目的在除不再使用的对象，当对象建立的时候垃圾收集期，就开始监控对象的动态情况，垃圾收集主要是对内存的释放。创建对象的时候申请一个空间

 

  1.不再使用的内存空间应回收---》垃圾收集； 

   2.Java消除了程序员回收无用内存空间的职责；提供一种系统级线程跟踪存储空间的分配情况。在JVM的空闲时，检查并释放可被释放的存储器空间；相比c++,开发人员负责要自己收回无用内存。

  3.垃圾收集在Java程序运行过程中自动进行，程序员无法精确控制和干预； 

   4.GC的自动回收，提高了内存空间的利用效率，也提高了编程人员的效率，很大程度上减少了因为没有释放空间而导致的内存泄露。

 

后续：

更高级：

1.垃圾收集器有几种 

2.垃圾收集器底层原理剖析 

3.垃圾收集器算法，优化    

 

#### 跨平台原理

JAVA跨平台原理的解释： 

![img](https://s2.loli.net/2023/09/01/TZk1rvOCozK2U9Y.jpg)

C语言的跨平台解释： 

![img](https://s2.loli.net/2023/09/01/eI4wAaRSoh2vQr9.jpg)

总结

JVM(Java Virtual Machine)就是一个虚拟的用于执行bytecode字节码的”虚拟计算机”。他也定义了指令集、寄存器集、结构栈、垃圾收集堆、内存区域。JVM负责将Java字节码解释运行，边解释边运行，这样，速度就会受到一定的影响。

不同的操作系统有不同的虚拟机。Java 虚拟机机制屏蔽了底层运行平台的差别，实现了“一次编译，随处运行”。 Java虚拟机是实现跨平台的核心机制。如图所示：

![img](https://s2.loli.net/2023/09/01/21lSd4VBmbEeGvt.jpg)

 

 

我们说的语言跨平台是编译后的文件跨平台，而不是源程序跨平台。

接下来我们再比较下两种方式的差异：第一，C语言是编译执行的，编译器与平台相关，编译生成的可执行文件与平台相关；第二，Java是解释执行的，编译为中间码的编译器与平台无关，编译生成的中间码也与平台无关（一次编译，到处运行），中间码再由解释器解释执行，解释器是与平台相关的，也就是不同的平台需要不同的解释器. 

 

### 常用DOS命令

**【1】DOS操作系统** 

--Microsoft公司推出的操作系统。（在windows之前的操作系统） 

--DOS是英文"Disk Operating System"的缩写,其中文含意是"磁盘操作系统". 

--DOS是单用户、单任务的操作系统.（只能执行一个任务） 

![img](https://image.201068.xyz/assets/clip_image028.gif)

**【2】DOS命令** 

--在windows中，我们通过鼠标菜单等来操作系统，而在dos操作系统中，要通过dos命令来操作系统。 

--是DOS操作系统的命令，是一种面向磁盘的操作命令，

--不区分大小写。 

**【3】命令学习：** 

windows给我们保留了类似dos系统的操作界面，可以直接操作磁盘！ 

dos 也是一种[操作系统](https://www.baidu.com/s?wd=操作系统&tn=SE_PcZhidaonwhc_ngpagmjz&rsv_dl=gh_pc_zhidao)，是在windows出现以前用的，后来windows出来后基本没人用了，但是当windows崩溃的时候，还是要的dos方式解决，它是一种纯命令方式，cmd其实就是在windows状态下进入dos方式。 


 控制命令台：win+r--->cmd 

![img](https://image.201068.xyz/assets/clip_image030.jpg)

 

**【4】具体dos命令：** 

（1）切换盘符： c:  d:  e:  大小写没有区分

（2）显示详细信息：dir 

![img](https://image.201068.xyz/assets/clip_image032.jpg)

 

（3）改变当前目录：cd 

![img](https://image.201068.xyz/assets/clip_image034.jpg)

 

（4） 

. 当前目录 

.. 代表上一层目录

![img](https://image.201068.xyz/assets/clip_image036.jpg)

![img](https://image.201068.xyz/assets/clip_image038.jpg)

 

（5）清屏：cls 

（6）切换历史命令：上下箭头 

（7）补全命令： tab按键 

（8）创建目录：md 

   删除目录：rd 

![img](https://image.201068.xyz/assets/clip_image040.jpg)

（9）复制文件命令：copy: 

![img](https://image.201068.xyz/assets/clip_image042.jpg)

（10）删除文件：del 

del后面如果接的是文件夹/目录：那么删除的就是这个文件夹下的文件，而不是文件夹 

![img](https://image.201068.xyz/assets/clip_image044.jpg)

### JAVA环境准备-->JDK

#### **【1】下载JDK** 

[www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html) 

![img](https://image.201068.xyz/assets/clip_image046.jpg)

**【2】安装JDK** 

![img](https://image.201068.xyz/assets/clip_image048.jpg)

![img](https://image.201068.xyz/assets/clip_image050.jpg)

![img](https://image.201068.xyz/assets/clip_image052.jpg)

#### **【3】卸载JDK** 

控制面板卸载即可 

![img](https://image.201068.xyz/assets/clip_image054.jpg)

#### **【4】 验证JDK是否安装成功** 

（1）方式1：去安装目录下看一眼： 

![img](https://image.201068.xyz/assets/clip_image056.jpg)

（2）方式2：通过控制命令台查看： 

![img](https://image.201068.xyz/assets/clip_image058.jpg)

（3）方式3：通过控制面板查看： 

![img](https://image.201068.xyz/assets/clip_image060.jpg)

 

**【5】JDK和JRE：** 

JDK： Java Development kit  ---->编写Java程序的程序员使用的软件

JRE : Java Runtime Enviroment  ----》运行Java程序的用户使用的软件 

 

 

 

#### 安装notepad++，配置path环境变量

【1】安装记事本：notepad 

【2】安装：一直下一步 

![img](https://image.201068.xyz/assets/clip_image062.jpg)

【3】打开记事本进行设置： 

设置--》首选项： 

![img](https://image.201068.xyz/assets/clip_image064.jpg)

 

 

设置--》语言格式设置： 

![img](https://image.201068.xyz/assets/clip_image066.jpg)

 

【4】打开notepad++: 

（1）方式1：通过快捷方式： 

![img](https://image.201068.xyz/assets/clip_image068.jpg)

（2）方式2：通过可执行文件： 

![img](https://image.201068.xyz/assets/clip_image070.jpg)

（3）方式3：利用控制命令台： 

win+r-->cmd:

![img](https://image.201068.xyz/assets/clip_image072.jpg)

 

 

(4)方式4：在任意的路径下去执行notepad++.exe这个命令： 

但是发现报错：

![img](https://image.201068.xyz/assets/clip_image074.jpg)

 

需要配置系统环境变量：

![img](https://image.201068.xyz/assets/clip_image076.jpg)

找系统环境变量：

![img](https://image.201068.xyz/assets/clip_image078.jpg)

![img](https://image.201068.xyz/assets/clip_image080.jpg)

 

将notepad++.exe所在的路径配置到path环境变量中去： 

![img](https://image.201068.xyz/assets/clip_image082.jpg)

这样我就可以在任意的路径下去执行这个命令：（注意：控制命令台需要重启）

 

![img](https://image.201068.xyz/assets/clip_image084.jpg)

 

path环境变量作用： 

将命令所在的路径配置到path中去，就相当于在计算机中“注册”了一样，以后找这个命令，会直接去你配置的路径下寻找。 

达到了一个效果：在任意的路径下去执行某个命令---》path环境针对整个操作系统而言。 

 

### 第一段程序

**【1】用notepad编写代码：** 

```
public class HelloWorld{
          public static void main(String[] args){
                  System.out.println("hi 这是一段Java程序。。。");
         }
  }
```

记得保存  ctrl+s 

 

**【2】进行编译：** 

![img](https://image.201068.xyz/assets/clip_image086.jpg)

发现出错了，分析出错原因：

![img](https://image.201068.xyz/assets/clip_image088.jpg)

解决办法：

将javac.exe所在的路径 配置到 环境变量path中去，这样我就可以在任意的路径下去执行这个命令：

![img](https://image.201068.xyz/assets/clip_image090.jpg)

配置好环境变量以后发现代码可以成功编译：

![img](https://image.201068.xyz/assets/clip_image092.jpg)

验证：

![img](https://image.201068.xyz/assets/clip_image094.jpg)

 

**【3】进行解释/翻译/执行:** 

![img](https://image.201068.xyz/assets/clip_image096.jpg)

 

上面执行过程成功的原因：

 

![img](https://image.201068.xyz/assets/clip_image098.jpg)

### 程序中常见问题

【1】最低级的错误：单词拼写错误

【2】要求源文件名字和类名必须一模一样： 

![img](https://image.201068.xyz/assets/clip_image100.jpg)

出错：

![img](https://image.201068.xyz/assets/clip_image102.jpg)

 

【3】所有的标点必须是英文状态下的： 

中文状态：【】（）{} ！；：“‘《》？ 

英文状态：[]    ()  {}  !  ;  :  "  &apos;  <> ? 

 

**【4】成对编程：** 

[] {} () <> ""  &apos;&apos; 

 

**【5】注意缩进** ：只要遇到{}就进行缩进 --->为了格式好看 

缩进：tab 

向前缩进： shift+tab 

**【6】编译：** 

javac HelloWorld.java 

**【7】执行：** 

java HelloWorld 

**【8】java中大小写严格区分，大小敏感：** 

HelloWorld  Helloworld 

a  A  

public PUBLIC 

**【9】我们要写代码：就当做有一个“框子”** 

```
 
1.  public class HelloWorld{
2.          public static void main(String[] args){
3.                   
4.                  
5.          }
6.  }
```

**【10】一个源文件中可以有多个类，只能有一个类被public修饰，源文件的名字必须跟public修饰的那个类名保持一致。** 

![img](https://image.201068.xyz/assets/clip_image104.jpg)

多个类会产生独立的字节码文件：

![img](https://image.201068.xyz/assets/clip_image106.jpg)

 

执行的时候执行各自独立的字节码文件即可：

![img](https://image.201068.xyz/assets/clip_image108.jpg)

 

### 编译方式

**【1】方式1：** 

![img](https://image.201068.xyz/assets/clip_image110.jpg)

 

**【2】方式2：** 

![img](https://image.201068.xyz/assets/clip_image112.jpg)

 

**【3】方式3：** 

![img](https://image.201068.xyz/assets/clip_image114.jpg)

 

**【4】方式4：** 

在notepad中右键文件 --》打开文件夹所在命令行 

![img](https://image.201068.xyz/assets/clip_image116.jpg)

 

### 扩展：classpath环境变量

**【1】系统有一个环境变量叫：**classpath，现在我们将classpath环境变量显式的写出来： 

![img](https://image.201068.xyz/assets/clip_image118.jpg)

classpath作用：只要你配置到classpath中的路径，在执行java的字节码文件的时候，就会去这个配置的路径下找 对应的字节码文件： 

 

现在我不配置.\了 我配置： 

![img](https://image.201068.xyz/assets/clip_image120.jpg)

自从我配置了这个环境变量以后，可以在任意的路径下去执行字节码文件：

 

总结：

classpath作用：针对java执行字节码文件而产生的环境变量，只要配置了字节码文件所在的路径以后，那么以后你在任意位置都可以执行对应的字节码文件

 

### 扩展：JAVA_HOME环境变量

后续我们会用到一个软件：tomcat，在执行startup.bat的时候会出现闪退问题： 

解决： 必须要配置一个环境变量叫：JAVA_HOME 

![img](https://image.201068.xyz/assets/clip_image122.jpg)

 

我再次启动才会成功：

然后我们的path环境变量中刚好可以借助JAVA_HOME里面的内容，通过%%做引入 %JAVA_HOME%\bin 

![img](https://image.201068.xyz/assets/clip_image124.jpg)

 

### API

![img](https://image.201068.xyz/assets/clip_image126.jpg)

- JDK帮助文档     
- SUN公司为JDK工具包提供了一整套文档资料,我们习惯上称之为JDK文档。 
- JDK文档中提供了Java中的各种技术的详细资料,以及JDK中提供的各种类的帮助说明。 
- JDk文档是Java语言的完整说明,大多数书籍中的类的介绍都要参照它来完成,它是编程者经常查阅的资料 
- 如何理解API：就当做是一个“字典”，“使用手册”，API就相当于是一个电子的帮助文档，可以帮我们查看JDK提供的类的信息，平时查看的时候可结合百度一起看。 

其实API没有什么神奇的，就是一个电子文档而已，帮助我们查看JAVA中涉及到的一些技能点： 

![img](https://image.201068.xyz/assets/clip_image128.jpg)

 

### 代码量统计工具

![img](https://image.201068.xyz/assets/clip_image130.jpg)

 

#### 注释

为了方便程序的阅读，Java语言允许程序员在程序中写上一些说明性的文字，用来提高程序的可读性，这些文字性的说明就称为注释。

注释不会出现在字节码文件中，即Java编译器编译时会跳过注释语句。 

在Java中根据注释的功能不同，主要分为单行注释、多行注释和文档注释。

- 单行注释     

单行注释使用“//”开头，“//”后面的单行内容均为注释。 

- 多行注释     

多行注释以“/*”开头以“*/”结尾，在“/*”和“*/”之间的内容为注释，我们也可以使用多行注释作为行内注释。但是在使用时要注意，多行注释不能嵌套使用。

- 文档注释     

文档注释以“/**”开头以“*/”结尾， 注释中包含一些说明性的文字及一些JavaDoc标签（后期写项目时，可以生成项目的API） 

 

##### 单行注释和多行注释

```
1.  //下面是一段标准代码
2.  //这是代码的“框子”，当前阶段你可以当做一个模板
3.  //其实这就是一个类，类的名字是HelloWorld，这个名字可以随便起，但是一般首字母大写，驼峰命名，见名知意
4.  public class HelloWorld{
5.          //下面是一个main方法，方法的格式是固定的
6.          public static void main(String[] args){
7.                  //下面这句话的作用：将双引号中的内容进行原样输出
8.                  /*
9.                  这是多行注释
10.                每行都可以写
11.                单行注释和多行注释，按照你自己的需求去使用即可
12.                */
13.                System.out.println("hi....java");
14.        }
15.}
```

注意：

1.注释不会参与编译，编译后产生的字节码文件中不会有注释的内容

2.注释的作用： 

（1）注释就起到了标注解释的作用，提高代码的可读性，方便自己，方便他人--》是一个非常良好，非常专业的习惯！！！

（2）方便代码的调试： 

```
 
1.  public class HelloWorld2{
2.          public static void main(String[] args){ 
3.                  System.out.println("hi....java1");
4.                  //System.out.println("hi....java2")
5.                  System.out.println("hi....java3");
6.          }
7.  }
```

 

 

##### 文档注释

```
1.  /**
2.  文档注释
3.  @author zhaoss
4.  @version 1.0
5.  这是我们第一章文档注释的代码，比较重要
6.  */
7.  public class HelloWorld3{
8.          public static void main(String[] args){ 
9.                  System.out.println("hi....java1");     
10.        }
11.        /**
12.        @param name 姓名
13.        @param age 年龄
14.        */
15.        public void eat(String name,int age){
16.                System.out.println("hello");   
17.        }
18.}
```

一般文档注释可以配合：jdk提供的工具javadoc.exe来一起使用，通过javadoc.exe可以对文档注释进行解析，生成一套以网页文件形式体现的该程序的说明文档。（自定义类对应的API） 

![img](https://image.201068.xyz/assets/clip_image132.jpg)

![img](https://image.201068.xyz/assets/clip_image134.jpg)

![img](https://image.201068.xyz/assets/clip_image136.jpg)

![img](https://image.201068.xyz/assets/clip_image138.jpg)

 

### 反编译工具的使用

- 编译     

源代码----->class 

 

- 反编译     

class---->源代码 

 

- 反编译工具     

jd-gui.exe

![img](https://image.201068.xyz/assets/clip_image140.jpg)

 

 

### 本章最后一段代码

```
1.  public class HiWorld{
2.          public static void main(String[] args){
3.                  //进行自我介绍：
4.                  System.out.print("姓名：");
5.                  System.out.print("\t丽丽\n");
6.                  System.out.print("职业：");
7.                  System.out.print("\t学生");
8.                  /*
9.                  (1)System.out.print和System.out.println区别联系：
10.                System.out.print ： 将双引号中内容原样输出，不换行
11.                System.out.println ：将双引号中内容原样输出，换行
12.                (2)转义字符：
13.                \就是转义字符：作用：将后面普通的字母转换为特殊含义
14.                \n  : 换行
15.                \t  : 距离前面有一个制表符位置
16.                */
17.                
18.                System.out.println();//换行
19.                System.out.println("1111111111111111111");
20.                System.out.println("11111111\t2222");
21.        }
22.}
```

 

 

### 扩展面试题：JDK，JRE，JVM的区别

JDK,JRE,JVM的关系: 

![img](https://image.201068.xyz/assets/clip_image142.jpg)

先说JDK和JRE: 

初学JAVA很容易被其中的很多概念弄的傻傻分不清楚，首先从概念上理解一下吧，JDK（Java Development Kit）简单理解就是Java开发工具包，JRE(Java Runtime Enviroment)是Java的运行环境，JVM( java virtual machine)也就是常常听到Java虚拟机。JDK是面向开发者的，JRE是面向使用JAVA程序的用户，上面只是简单的区别 

 

通过上图发现发现有两个JRE文件夹，如果细看里面的内容基本上是一样的，如果是只是Java程序使用者，那么只会有最外层的那个JRE目录，JDK中是JRE自带的，你如果安装了JDK必然里面会有一个JRE.那么问题来了，为什么会有两套JRE呢？ 

从侧面证明: 

利用javac.exe进行编译: 

![img](https://image.201068.xyz/assets/clip_image144.jpg)

然后我将C:\Program Files\Java\jdk1.8.0_151\lib\tools.jar改个名字,再去编译: 

![img](https://image.201068.xyz/assets/clip_image146.jpg)

证明:dt.jar和tools.jar是两个java最基本的包，里面包含了从java最重要的lang包到各种高级功能如可视化的swing包，是java必不可少的。而path下面的bin里面都是java的可执行的编译器及其工具，如java，javadoc等,报错的原因就是输入的javac的命令不是去JDK中bin目录去找的javac.exe，而是去JDK中lib目录中的tools.jar中com.sun.tools.javac.Main中执行，因此javac.exe只是一个包装器（Wrapper），存在的目的是为了让开发者免于输入过长的指命。这个时候发现JDK里的工具几乎是用Java所编写，同属于Java应用程序，因此要使用JDK所附的工具来开发Java程序，所以自身需要附一套JRE才能运行。上图中与jdk同级目录下的JRE就是用来运行一般Java程序用的。

两套JRE运行的时候究竟运行哪一个呢，这个时候JDK中java.exe先从自身目录中找，然后父级目录中找，如果都没有就去注册表中找

![img](https://image.201068.xyz/assets/clip_image148.jpg)

 

 

再说JRE和JVM: 

JVM -- java virtual machineJVM就是我们常说的java虚拟机，它是整个java实现跨平台的最核心的部分，所有的java程序会首先被编译为.class的类文件，这种类文件可以在虚拟机上执行，class文件并不直接与机器的操作系统相对应，而是经过虚拟机间接与操作系统交互，由虚拟机将程序解释给本地系统执行，类似于C#中的CLR。 

JVM不能单独搞定class的执行，解释class的时候JVM需要调用解释所需要的类库lib。在JDK下面的的jre目录里面有两个文件夹bin和lib,在这里可以认为bin里的就是jvm，lib中则是jvm工作所需要的类库，而jvm和 lib和起来就称为jre。 

![img](https://image.201068.xyz/assets/clip_image150.jpg)

JVM+Lib=JRE，如果讲的具体点就是bin目录下的jvm.dll文件， jvm.dll无法单独工作，当jvm.dll启动后，会使用explicit的方法(就是使用Win32 API之中的LoadLibrary()与GetProcAddress()来载入辅助用的动态链接库)，而这些辅助用的动态链接库(.dll)都必须位 于jvm.dll所在目录的父目录之中。因此想使用哪个JVM，只需要设置PATH，指向JRE所在目录下的jvm.dll。

![img](https://image.201068.xyz/assets/clip_image152.jpg)

 

# 第2章_数据类型

 

#### 标识符

**【1】标识符：读音  biao zhi fu** 

**【2】什么是标识符？** 

 包，类，变量，方法.....等等,只要是起名字的地方,那个**名字**就是标识符 

**【3】标识符定义规则：** 

1.四个可以（组成部分）：数字，字母，下划线_，美元符号$ 

注意：字母概念比较宽泛，指的是英文字母，汉字，日语，俄语...... 

但是我们一般起名字尽量使用英文字母 

2.两个不可以：不可以以数字开头，不可以使用java中的关键字 

3.见名知意：增加可读性

**4.****大小写敏感**：  int a ;  int A; 

**5.****遵照驼峰命名：** 

  类名：首字母大写，其余遵循驼峰命名 

    方法名，变量名：首字母小写，其余遵循驼峰命名 

    包名：全部小写，不遵循驼峰命名 

**6.****长度无限制，但是不建议太长** **asdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasfd** 

 

#### 关键字

**关键字：**被JAVA语言赋予了特殊含义，用作专门用途的单词

特点：JAVA中所有关键字都为小写 

官网：https://docs.oracle.com/javase/tutorial/java/nutsandbolts/_keywords.html

![img](https://image.201068.xyz/assets/clip_image154.jpg)

![img](https://image.201068.xyz/assets/clip_image156.jpg)

 

#### 变量和常量

举例： 

丽丽的年龄：去年17岁，今年18岁，明年19岁

年龄：17--》18---》19 --》值不断变化  

 

年龄---》变量 

常量：  17  ，  18  ，  19   ----》 常量中的字面常量 

 

##### 字面常量

**常量分为两种：** 

常量通常指的是一个固定的值，例如：1、2、3、’a’、’b’、true、false、”helloWorld”等。 

在Java语言中，主要是利用关键字final来定义一个常量。 常量一旦被初始化后不能再更改其值。

为了更好的区分和表述，一般将1、2、3、’a’、’b’、true、false、”helloWorld”等称为字面常量，而使用final修饰的PI等称为符号常量（字符常量）。 

 

 

**字面常量的类型：**

![img](https://image.201068.xyz/assets/clip_image158.jpg)

注意：逻辑常量就两个值，一个是true，一个是false 

 

##### 变量

变量本质上就是代表一个”可操作的存储空间”，空间位置是确定的，但是里面放置什么值不确定。我们可通过变量名来访问“对应的存储空间”，从而操纵这个“存储空间”存储的值。Java是一种强类型语言，每个变量都必须声明其数据类型。变量的数据类型决定了变量占据存储空间的大小。 比如，int a=3; 表示a变量的空间大小为4个字节。变量作为程序中最基本的存储单元，其要素包括变量名，变量类型和作用域。变量在使用前必须对其声明, 只有在变量声明以后，才能为其分配相应长度的存储空间。 

 

【1】变量声明格式： 

type varName [=value][,varName[=value]...]; //[ ]中的内容为可选项，即可有可无 

数据类型 变量名 [=初始值] [,变量名 [=初始值]…]; 

案例：

int   age  = 19 , age2 = 90  ; 

int age,age2; 

【2】变量的声明： 

（1）如果你只定义一个变量，没有给变量进行赋值的话，那么其实这个变量相当于没有定义： 

![img](https://image.201068.xyz/assets/clip_image160.jpg)

 

（2）变量如果没有进行赋值的话，那么使用的时候会出错，告诉你：尚未初始化变量： 

![img](https://image.201068.xyz/assets/clip_image162.jpg)

 

 

【3】变量的赋值： 

![img](https://image.201068.xyz/assets/clip_image164.jpg)

 

我们自己定义的时候直接就可以用一句话定义：

int age = 10; 

 

变量的值可以更改：

```
1.  public class TestVar01{
2.          public static void main(String[] args){
3.                  //变量的声明（定义变量）（以年龄为案例讲解）
4.                  //java是一个强类型的语言，只要声明变量就必须定义类型：定义整数类型
5.                  int age ; //定义一个整数类型的变量，变量名字为age 
6.                  //对变量进行赋值操作：
7.                  age = 10; //变量名字为age，具体的值为10 
8.                  age = 12;
9.                  age = 20;
10.                age = age + 4;
11.                age = 9;
12.                age = 9;
13.                System.out.println(age);
14.                
15.        }
16.}
```

变量不可以重复定义：

![img](https://image.201068.xyz/assets/clip_image166.jpg)

 

【4】变量的使用： 

```
1.  public class TestVar01{
2.          public static void main(String[] args){
3.                  //变量的声明（定义变量）（以年龄为案例讲解）
4.                  //java是一个强类型的语言，只要声明变量就必须定义类型：定义整数类型
5.                  int age ; //定义一个整数类型的变量，变量名字为age 
6.                  //对变量进行赋值操作：
7.                  age = 10; //变量名字为age，具体的值为10 
8.                  age = 12;
9.                  age = 20;
10.                age = age + 4;
11.                age = 9;
12.                age = 9;
13.                System.out.println(age);
14.                System.out.println(age-2);
15.                System.out.println(age+10);
16.                int num = age + 66;
17.                System.out.println(num);
18.                
19.        }
20.}
```

扩展：

```
1.  public class TestVar02{
2.          public static void main(String[] args){
3.                  int a = 10;
4.                  int b = 20;
5.                  int c = a + b ;
6.          }
7.  }
```

 

现在对上述代码进行“反编译过程”“反汇编过程”

![img](https://image.201068.xyz/assets/clip_image168.jpg)

 

![img](https://image.201068.xyz/assets/clip_image170.jpg)

 

 

【5】变量的内存： 

![img](https://image.201068.xyz/assets/clip_image172.jpg)

 

【6】习题： 

 

```
1.  public class TestVar03{
2.          public static void main(String[] args){
3.                  int num1 = 10;
4.                  int num2 = 20;
5.                  num1 = num2;
6.                  num2 = num2 + 10;
7.                  num1 = num2 - 10;
8.                  num2 = num1;
9.                  System.out.println("num1="+num1);
10.                System.out.println("num2="+num2);
11.        }
12.}
```

内存分析：

![img](https://image.201068.xyz/assets/clip_image174.jpg)

结果：

![img](https://image.201068.xyz/assets/clip_image176.jpg)

 

 

【7】变量的作用域： 

作用域指的就是作用范围，变量在什么范围中有效

作用范围就是离它最近的{} 

 

备注：一会我们写的代码，不要去运行，会出错

```
1.  /*
2.  局部变量：定义在方法中
3.  成员变量：定义在类中，方法外
4.  */
5.  public class TestVar04{
6.          int b = 20;
7.          public static void main(String[] args){
8.                  System.out.println(a);//no
9.                  int a = 10;
10.                System.out.println(a);//yes
11.                System.out.println(b);//yes
12.                {
13.                        int c = 40;
14.                        System.out.println(c);//yes
15.                        int a = 50;//属于变量的重复定义
16.                }
17.                System.out.println(c);//no
18.        }
19.        
20.        public void eat(){
21.                System.out.println(b);//yes
22.                System.out.println(a);//no
23.                int a = 30;//不是变量的重复定义
24.                System.out.println(a);//yes
25.        }
26.}
```

 

#### 基本数据类型

Java是一种强类型语言，每个变量都必须声明其数据类型。 

Java的数据类型可分为两大类：基本数据类型（primitive data type）和引用数据类型（reference data type）。 

![img](https://image.201068.xyz/assets/clip_image178.jpg)

PS:巧妙记忆：除了基本数据类型以外的所有类型都属于引用数据类型，本章重点：基本数据类型

##### 整数类型

###### 整数类型常量

十进制整数，如：99, -500, 0 

八进制整数，要求以 0 开头，如：015 

十六进制数，要求 0x 或 0X 开头，如：0x15 

二进制：要求0b或者0B开头，如：0b11 

 

几进制：就是逢几进1的问题： 

平时实际生活中用的最多的是：十进制

计算机用二进制最多

![img](https://image.201068.xyz/assets/clip_image180.jpg)

扩展：进制转换问题

【1】二进制转换为十进制：

二进制： 1101 

  1*2^3  +  1*2^2  +  0*2^1  +   1*2^0 

=   8     +    4    +   0    +    1 

= 13 

【2】十进制转换为二进制： 

十进制  13   

![img](https://image.201068.xyz/assets/clip_image182.jpg)

 

【3】八进制转换十进制： 

八进制： 16 

 

1*8^1 +  6*8^0 

=  8   +  6 

=14

 

 

【4】十进制转换为八进制： 

十进制14： 

![img](https://image.201068.xyz/assets/clip_image184.jpg)

 

【5】八进制转换为十六进制： 

 

把十进制当做一个中转站：

八进制---》十进制---》十六进制 

 

实际上根本不用自己转换这么麻烦：我们可以直接用系统中提供给我们的计算器： 

![img](https://image.201068.xyz/assets/clip_image186.jpg)

 

 

###### 整数类型变量

**整型数据类型：** 

 

![img](https://image.201068.xyz/assets/clip_image188.jpg)

 

比如：byte的右侧表数范围127怎么算出来的？ 

byte: 1字节 =  8位 

二进制：01111111 

  1*2^6  + 1*2^5  +  1*2^4 + 1*2^3  + 1*2^2 +  1*2^1 +  1*2^0 

= 64   +   32    +   16    +8     +4       +   2    +1 

= 127 

 

 

代码：

```
1.  public class TestVar05{
2.          public static void main(String[] args){
3.                  //定义整数类型的变量：
4.                  //给变量赋值的时候，值可以为不同进制的：
5.                  int num1 = 12 ;//默认情况下赋值就是十进制的情况
6.                  System.out.println(num1);
7.                  int num2 = 012;//前面加上0，这个值就是八进制的
8.                  System.out.println(num2);
9.                  int num3 = 0x12;//前面加上0x或者0X，这个值就是十六进制的
10.                System.out.println(num3);
11.                int num4 = 0b10;//前面加上0b或者0B,这个值就是二进制的
12.                System.out.println(num4);
13.                
14.                //定义byte类型的变量：
15.                byte b = 126;//定义了一个byte类型的变量，名字叫b，赋值为12
16.                System.out.println(b);
17.                //注意：超范围的赋值会报错。
18.                short s = 30000;
19.                System.out.println(s);
20.                int i = 1234;
21.                System.out.println(i);
22.                //整数类型默认就是int类型的，所以12345678910是一个int类型的数，对于int类型来说，它超出范围了
23.                //要想把一个数给long类型变量，那么后面加上L(推荐)或者l就可以了
24.                long num5 = 12345678910L;
25.                System.out.println(num5);
26.                //注意：只有这个数超出int类型的范围了后面才需要加上L，否则无需加L也可以赋值给long类型：
27.                long num6 = 12;
28.                System.out.println(num6);
29.                
30.        }
31.}
```

##### 浮点类型

###### 浮点类型常量

（1）十进制数形式，例如:                

3.14    314.0   0.314 

（2）科学记数法形式，如 

314e2   314E2 (E的大小写没有区分)  314E-2 

double f = 314e2; //314*10^2-->31400.0 

double f2 = 314e-2; //314*10^(-2)-->3.14 

 

###### 浮点类型变量

float类型又被称作单精度类型，尾数可以精确到7位有效数字，在很多情况下，float类型的精度很难满足需求。 

而double表示这种类型的数值精度约是float类型的两倍，又被称作双精度类型，绝大部分应用程序都采用double类型。

float类型的数值有一个后缀F或者f ，没有后缀F/f的浮点数值默认为double类型。 

也可以在浮点数值后添加后缀D或者d， 以明确其为double类型。 

![img](https://image.201068.xyz/assets/clip_image190.jpg)

PS：有效数字指的是从左开始第一个不为0的数到最后一个数 

 

代码：

```
1.  public class TestVar06{
2.          public static void main(String[] args){
3.                  //浮点类型的常量有两种形式：
4.                  //十进制形式：
5.                  double num1 = 3.14;
6.                  System.out.println(num1);
7.                  //科学计数法形式：
8.                  double num2 = 314E-2;
9.                  System.out.println(num2);
10.                
11.                //浮点类型的变量：
12.                //注意：浮点型默认是double类型的，要想将一个double类型的数赋给float类型，必须后面加上F或者f
13.                float f1 = 3.14234567898623F;
14.                System.out.println(f1);
15.                //注意：double类型后面可以加D或者d，但是一般我们都省略不写
16.                double d1 = 3.14234567898623D;
17.                System.out.println(d1);
18.                
19.                //注意：我们最好不要进行浮点类型的比较：
20.                float f2 = 0.3F;
21.                double d2 = 0.3;
22.                System.out.println(f2==d2);
23.                /*
24.                区别：
25.                = 赋值运算：  将等号右侧的值赋给等号左侧
26.                == 判断==左右两侧的值是否相等  ：结果要么相等 要么不相等
27.                ==运算符的结果就是要么是true，要么是false
28.                */
29.                
30.        }
31.}
```

 

 

##### 字符类型

【1】Java中使用单引号来表示字符常量，字符型在内存中占2个字节。 

char 类型用来表示在Unicode编码表中的字符。Unicode编码被设计用来处理各种语言的文字，它占2个字节，可允许有65536个字符。 

 

【2】转义字符： 

 

![img](https://image.201068.xyz/assets/clip_image192.jpg)

 

【3】ASCII表： 

![img](https://image.201068.xyz/assets/clip_image194.jpg)

【4】Unicode编码表： 

https://www.cnblogs.com/csguo/p/7401874.html

 

 

 

代码1： 

```
1.  public class TestVar07{
2.          public static void main(String[] args){
3.                  //定义字符类型的变量：
4.                  char ch1 = 'a';
5.                  System.out.println(ch1);
6.                  char ch2 = 'A';
7.                  System.out.println(ch2);
8.                  char ch3 = '4';
9.                  System.out.println(ch3);
10.                char ch4 = '中';
11.                System.out.println(ch4);
12.                char ch5 = '?';
13.                System.out.println(ch5);
14.                //java中无论：字母，数字，符号，中文都是字符类型的常量，都占用2个字节。
15.                char ch6 = ' ';
16.                System.out.println(ch6);
17.                //字符类型：单引号引起来的单个字符
18.                System.out.println("--------------------------------");
19.                /*
20.                转义字符：
21.                \将后面的普通字符转换为特殊含义
22.                */
23.                char ch7 = '\n';
24.                System.out.println("aaa"+ch7+"bbb");
25.                
26.                System.out.println("aaa\nbbb");// \n  换行
27.                
28.                System.out.println("aaaaaaa\tbbb");  //  \t  制表符
29.                
30.                System.out.println("aaa\bbbb");//aabbb  \b  向前退一格
31.                System.out.println("aaa\rbbb");//bbb   \r 将光标到本行开头 ：回车
32.                
33.                System.out.println("\"java\""); // \" 将双引号原样输出  \' 将单引号原样输出 \\ 将\原样输出
34.        }
35.}
```

 

代码2： 

```
1.  public class TestVar08{
2.          public static void main(String[] args){
3.                  char ch1 = 'A';
4.                  System.out.println(ch1);//A
5.                  System.out.println(ch1+90);//155
6.                  System.out.println(155-ch1);//90
7.                  //char类型我们看到的样子就是它本身的字面常量,但是底层在进行计算的时候，实际上是按照一个码进行计算的。
8.                  //这个码就是ASCII
9.                  //之前说char类型是按照Unicode码表进行存储的 (Unicode兼容了ASCII码，Unicode的前128位置ASCII)
10.                
11.                char ch2 = '中';
12.                System.out.println(ch2);// 中
13.                System.out.println(ch2+90);// 20103
14.                System.out.println(20103-ch2);// 90
15.                
16.                //转换：
17.                int num1 = (int)ch2;
18.                System.out.println(num1);//20013
19.                
20.                char ch = (char)20013;
21.                System.out.println(ch);
22.                
23.                int num2 = '中';
24.                char ch5 = 20013;
25.                System.out.println(ch5);
26.                
27.                //面试题：
28.                char ch6 = '2'+2;
29.                System.out.println(ch6);//'4'--->4
30.        }
31.}
```

 

###### 编码和字符集

【1】什么是编码？

![img](https://image.201068.xyz/assets/clip_image196.jpg)

【2】通过生活案例： 

![img](https://image.201068.xyz/assets/clip_image198.jpg)

【3】由权威机构形成的编码表才可以称之为：字符集 

- ASCII 

          英文字符集   

          用一个字节的7位表示

- IOS8859-1 

          西欧字符集 

          用一个字节的8位表示

- GB2312 

          简体中文字符集 

          最多使用两个字节编码 

PS：中文：2个字节

GB2312兼容了ASCII中的字符： 

- GBK 

          GB2312的升级，加入了繁体字 

          最多使用两个字节编码 

疑问： 

![img](https://image.201068.xyz/assets/clip_image200.jpg)

首位如果是0：一个字节代码代表一个字符 

首位如果是1：那么一个字节不够，要加上后面的字节才能完整的表示一个字符。 

·   Unicode 

           国际通用字符集，融合了目前人类使用的所有字符。为每个字符分配唯一的字符码。 

退出了UTF标准：

三种编码方案：  UTF-8，UTF-16,UTF-32 




以UTF-8为案例讲解： 

中文： 珊   ---》Unicode  ： 29642 

![img](https://image.201068.xyz/assets/clip_image202.jpg)

 

![img](https://image.201068.xyz/assets/clip_image204.jpg)

底层存储： 

![img](https://image.201068.xyz/assets/clip_image206.jpg)

UTF-8标准最多可以用6个字节表示：

![img](https://image.201068.xyz/assets/clip_image208.jpg)

 

 

以后我们用的最多的就是UTF-8. 

 

###### 解释乱码问题

![img](https://image.201068.xyz/assets/clip_image210.jpg)

 

用记事本选择编码方法的时候一般要选择为ANSI---》获取当前操作系统的编码格式：GBK 

 

##### 布尔类型

boolean类型有两个常量值，true和false，在内存中占一位（不是一个字节），不可以使用 0 或非 0 的整数替代 true 和 false ，这点和C语言不同。 boolean 类型用来判断逻辑条件，一般用于程序流程控制 。 

```
1.  public class TestVar09{
2.          public static void main(String[] args){
3.                  //创建一个布尔类型的变量：
4.                  boolean flag1 = true;
5.                  System.out.println(flag1);
6.                  boolean flag2 = false;
7.                  System.out.println(flag2);
8.                  boolean flag3 = 5==9;
9.                  System.out.println(flag3);
10.                boolean flag4 = 5<9;
11.                System.out.println(flag4);
12.        }
13.}
```

 

 

##### 基本数据类型的转换

【1】什么是类型转换：

在赋值运算或者算数运算的时候，要求数据类型一致，就要进行类型的转换。

 

【2】类型转换的种类： 

自动转换，强制转换

【3】内存演示： 

![img](https://image.201068.xyz/assets/clip_image212.jpg)

【4】代码： 

```
1.  public class TestVar10{
2.          public static void main(String[] args){
3.                  //类型转换的两种形式：
4.                  double d = 6;//int-->double  自动类型转换
5.                  System.out.println(d);
6.                  int i = (int)6.5;//double--->int  强制类型转换 （强转）
7.                  System.out.println(i);
8.                  
9.                  //在同一个表达式中，有多个数据类型的时候，应该如何处理：
10.                //多种数据类型参与运算的时候，整数类型，浮点类型，字符类型都可以参与运算，唯独布尔类型不可以参与运算。
11.                //double d2 = 12+1294L+8.5F+3.81+'a'+true;
12.                double d2 = 12+1294L+8.5F+3.81+'a';
13.                System.out.println(d2);
14.                /*
15.                类型级别：(从低到高的)
16.                byte,short,char-->int--->long--->float--->double
17.                级别用来做什么？当一个表达式中有多种数据类型的时候，要找出当前表达式中级别最高的那个类型，然后
18.                其余的类型都转换为当前表达式中级别最高的类型进行计算。
19.                double d2 = 12+1294L+8.5F+3.81+'a';
20.                          = 12.0+1294.0+8.5+3.81+97.0
21.                */
22.                int i2 = (int)(12+1294L+8.5F+3.81+'a');
23.                System.out.println(i2);
24.                /*
25.                在进行运算的时候：
26.                左=右  : 直接赋值
27.                左<右  ：强转
28.                左>右  ：直接自动转换
29.                */
30.                
31.                //以下情况属于特殊情形：对于byte，short，char类型来说，只要在他们的表数范围中，赋值的时候就不需要进行
32.                //强转了直接赋值即可。
33.                byte b = 12;
34.                System.out.println(b);
35.                byte b2 = (byte)270;
36.                System.out.println(b2);
37.                
38.                
39.                
40.        }
41.}
```

 

 

##### 练习：final，字符常量，Scanner的使用

```
1.  import java.util.Scanner;//形象理解：在java.util下将Scanner拿过来用
2.  public class TestVar11{
3.          public static void main(String[] args){
4.                  //实现功能：求圆的周长和面积
5.                  //【1】提取变量：提取变量，就是为了一劳永逸，以后只要改变变量的值，下面只要用到这个变量的地方，取值也都发生变化了
6.                  //【2】一个变量被final修饰，这个变量就变成了一个常量，这个常量的值就不可变了
7.                  //     这个常量就是我们所说的 字符常量  ---》pi
8.                  //     约定俗成的规定：字符常量的名字全部大写
9.                  //【3】使用扫描器：Scanner的使用--》注意通过形象的理解去使用
10.                final double PI = 3.14;
11.                //拿来一个扫描器：
12.                Scanner sc = new Scanner(System.in);
13.                //给一个友好性的提示：
14.                System.out.print("请录入一个半径：");
15.                //让扫描器扫描键盘录入的int类型的数据：
16.                int r = sc.nextInt();
17.                
18.                //求周长：
19.                double c = 2*PI*r;
20.                System.out.println("周长为："+c);
21.                
22.                //求面积：
23.                //PI = 9.29;报错：TestVar11.java:12: 错误: 无法为最终变量pi分配值
24.                double s = PI*r*r;
25.                System.out.println("面积为："+s);
26.                
27.                
28.        }
29.}
```

 

##### 练习：加深对Scanner的使用

![img](https://image.201068.xyz/assets/clip_image214.jpg)

```
1.  import java.util.Scanner;
2.  public class TestVar12{
3.          public static void main(String[] args){
4.                  //键盘录入学生的信息：年龄，身高，姓名，性别：
5.                  //键盘录入年龄：(接收int类型数据)
6.                  Scanner sc = new Scanner(System.in);
7.                  System.out.print("请录入年龄：");
8.                  int age = sc.nextInt();
9.                  //键盘录入身高：（接收double类型数据）
10.                System.out.print("请录入身高：");
11.                double height = sc.nextDouble();
12.                //键盘录入姓名：(接收String类型数据--》字符串)
13.                System.out.print("请录入姓名：");
14.                String name = sc.next();
15.                //键盘录入性别：(接受char类型)
16.                System.out.print("请录入性别：");
17.                String sexStr = sc.next();
18.                char sex = sexStr.charAt(0);
19.                //上面两句可以合为一句表示：char sex = sc.next().charAt(0);
20.                System.out.println("该学生的信息为:姓名是："+name+",年龄是："+age+",身高为："+height+",性别是："+sex);
21.        }
22.}
```

# 第3章_运算符

 

#### Java中的运算符

【1】Java 语言支持如下运算符： 

- 算术运算符       

  +，-，*，/，%，++（自增），--（自减） 

- 赋值运算符 

  =  

- 扩展赋值运算符     

  +=，-=，*=，/= 

- 关系运算符     

  >，<，>=，<=，==，!= 

- 逻辑运算符     

  &，|， &&，||，!，^ 

- 位运算符     

   &，|，^，~ ， >>，<<，>>> (了解！！！) 

- 条件运算符     

  ？： 

【2】相关概念辨析 

\+     运算符 操作符     Operator 

5+6   表达式           expression 

5 6   操作数           Operand 

int m =5+6;   语句     Sentence 

 

#### 算术运算符

 

##### /和%

【1】/  除法运算符 ： 表示两个数相除运算  

   %  取余运算符： 用来求余数的 

```
1.  public class TestOpe01{
2.          public static void main(String[] args){
3.                  //打印结果：
4.                  System.out.println(12/3);
5.                  System.out.println(12%5);
6.                  System.out.println(12/3.0);
7.                  System.out.println(12%5.0);
8.          }
9.  }
```

【2】练习： 

```
1.  import java.util.Scanner;
2.  public class TestOpe02{
3.          public static void main(String[] args){
4.                  //实现功能：任意给出一个四位数，求出每位上的数字并输出
5.                  
6.                  //1.任意给出一个四位数：
7.                  Scanner input = new Scanner(System.in);
8.                  System.out.println("请录入一个四位数：");
9.                  int num = input.nextInt();
10.                
11.                
12.                //2.求出每位上的数字：
13.                //个位数：
14.                int num1 = num%10;
15.                //十位数：
16.                int num2 = num/10%10;//1234--->123--->3
17.                //百位数：
18.                int num3 = num/100%10;//1234--->12--->2
19.                //千位数：
20.                int num4 = num/1000;//1234--->1
21.                
22.                
23.                //3.输出每位上的数字：
24.                System.out.println("个位上的数为："+num1);
25.                System.out.println("十位上的数为："+num2);
26.                System.out.println("百位上的数为："+num3);
27.                System.out.println("千位上的数为："+num4);
28.        }
29.        
30.}
```

 

 

##### +

【1】+的作用： 

（1）表示正数 

（2）表示相加操作 

（3）进行字符串的拼接 

 

【2】代码练习： 

```
1.  public class TestOpe03{
2.          public static void main(String[] args){
3.                  //表示正数：
4.                  System.out.println(+5);//5
5.                  //相加操作：
6.                  System.out.println(5+6);//11
7.                  System.out.println(5+'6');//59
8.                  //字符串的拼接：
9.                  //规则：+左右两侧的任意一侧有字符串，那么这个加号就是字符串拼接的作用，结果一定是字符串
10.                int num = 56;
11.                System.out.println("num="+num);//"num=56" ---> num=56
12.                System.out.println(5+6+"7");//11+"7"--->"117"  --->117
13.                System.out.println(5+'6'+"7");//59 +"7"--->"597" --->597
14.                System.out.println("5"+6+"7");//"56"+"7"  --->"567"--->567
15.                System.out.println("5"+'6'+"7");//"56"+"7"--->"567"--->567
16.                System.out.println("5"+'6'+'7');//"56"+'7'--->"567"---567
17.        }
18.}
```

 

 

##### ++

【1】++： 

```
1.  public class TestOpe04{
2.          public static void main(String[] args){
3.                  int a = 5;
4.                  a++;//理解为：相当于  a=a+1 操作  
5.                  System.out.println(a);//6
6.                  
7.                  a = 5;
8.                  ++a;//理解为：相当于  a=a+1 操作  
9.                  System.out.println(a); //6
10.                
11.                //总结：++单独使用的时候，无论放在前还是后，都是加1操作
12.                
13.                //将++参与到运算中：
14.                //规则：看++在前还是在后，如果++在后：先运算，后加1   如果++在前，先加1，后运算
15.                a = 5;
16.                int m = a++ + 7;//先运算  m=a+7  再加1：  a = a+1 
17.                System.out.println(m);//12
18.                System.out.println(a);//6
19.                
20.                a = 5;
21.                int n = ++a + 7;//先加1  a=a+1  再运算：  n = a+7 
22.                System.out.println(n);//13
23.                System.out.println(a);//6
24.        }
25.}
```

无论这个变量是否参与到运算中去，只要用++运算符，这个变量本身就加1操作 

只是说如果变量参与到运算中去的话，对运算结果是产生影响：

看++在前还是在后，如果++在后：先运算，后加1  如果++在前，先加1，后运算 

 

 

【2】练习： 

```
1.  public class TestOpe05{
2.          public static void main(String[] args){
3.                  int a = 5;
4.                  System.out.println(a++ + a++);
5.                  System.out.println(a++ + ++a);
6.                  System.out.println(++a + a++);
7.                  System.out.println(++a + ++a);
8.          }
9.  }
```

 

 

运算过程：

![img](https://image.201068.xyz/assets/clip_image216.jpg)

 

 

#### 赋值运算符

【1】=的作用： 将等号右侧的值赋给等号左侧：

int age = 19; 

int age = 10+3+8; 

 

【2】练习： 

```
1.  public class TestOpe06{
2.          public static void main(String[] args){
3.                  //任意给出两个数，交换两个数并输出：
4.                  //1.给出两个数：
5.                  int num1 = 10;
6.                  int num2 = 20;
7.                  
8.                  //2.输出交换前的两个数：
9.                  System.out.println("交换前："+num1+"\t"+num2);
10.                
11.                //3.交换
12.                /*
13.                错误代码：
14.                num1 = num2;
15.                num2 = num1;    
16.                */              
17.                //解决办法：
18.                //引入一个中间变量:
19.                int t;
20.                t = num1;
21.                num1 = num2;
22.                num2 = t;
23.                /*
24.                int t;
25.                t = num2;
26.                num2 = num1;
27.                num1 = t;
28.                
29.                */
30.                
31.                //4.输出交换后的两个数：
32.                System.out.println("交换后："+num1+"\t"+num2);
33.        }
34.}
35. 
```

 

 

![img](https://image.201068.xyz/assets/clip_image218.jpg)

 

 

 

面试题：两个数交换的四种方式：https://www.cnblogs.com/Brad-Lee/p/5808299.html

 

#### 扩展赋值运算符

【1】代码：

```
1.  public class TestOpe07{
2.          public static void main(String[] args){
3.                  //实现功能：给出三个数，求和：
4.                  //1.给出三个数：
5.                  int num1 = 10;
6.                  int num2 = 20;
7.                  int num3 = 30;
8.                  //2.求和
9.                  //int sum = num1+num2+num3;
10.                //定义一个变量，用来接收和：
11.                int sum = 0;
12.                sum = sum + num1;//等效：  sum += num1;
13.                sum = sum + num2;// sum += num2;
14.                sum = sum + num3;//sum += num3;
15.                //3.将和输出：
16.                System.out.println("和："+sum);
17.        }
18.}
```

 

内存：

![img](https://image.201068.xyz/assets/clip_image220.jpg)

 

 

【2】a+=b  和 a=a+b  区别： 

（1）a+=b   可读性稍差 编译效率高  底层自动进行类型转换 

（2）a=a+b   可读性好  编译效率低  手动进行类型转换 

 

 

【3】面试题 

（1）请问a+=b相当于a=a+b,那么也相当于  a=b+a吗？ 

![img](https://image.201068.xyz/assets/clip_image222.jpg)

（2）下面的代码哪一句出错：  4 

byte a = 10;  --->1 

int b = 20;  --->2 

a+=b; ---->3 

a = a+b ;---->4 

更正：  a = (byte)(a+b); 

 

#### 关系运算符

```
1.  public class TestOpe08{
2.          public static void main(String[] args){
3.                  //>，<，>=，<=，==，!=
4.                  //关系运算符最终结果：要么是true要么是false
5.                  System.out.println(4>9);//false
6.                  System.out.println(4<9);//true
7.                  System.out.println(4>=9);//false
8.                  System.out.println(4<=9);//true
9.                  System.out.println(4==9);//false
10.                System.out.println(4!=9);//true
11.                System.out.println((5<9)!=(6==8));//true
12.        }
13.}
```

 

#### 逻辑运算符

  &，|， &&，||，!，^ 

逻辑运算符：进行逻辑运算的，运算符左右连接的都是 布尔类型的操作数，最终表达式的结果是布尔值：要么是true，要么false 

 

代码： 

```
1.  public class TestOpe09{
2.          public static void main(String[] args){
3.                  // 逻辑与 ：& 规律：只要有一个操作数是false，那么结果一定是false
4.                  System.out.println(true&true);
5.                  System.out.println(true&false);
6.                  System.out.println(false&false);
7.                  System.out.println(false&true);
8.                  
9.                  // 短路与：&& 规律：效率高一些，只要第一个表达式是false，那么第二个表达式就不用计算了，结果一定是false
10.                System.out.println(true&&true);
11.                System.out.println(true&&false);
12.                System.out.println(false&&false);
13.                System.out.println(false&&true);
14.                
15.                // 逻辑或：| 规律：只要有一个操作数是true，那么结果一定是true
16.                System.out.println(true|true);
17.                System.out.println(true|false);
18.                System.out.println(false|false);
19.                System.out.println(false|true);
20.                
21.                // 短路或：|| 规律：效率高一些，只要第一个表达式是true，那么第二个表达式就不用计算了，结果一定是true
22.                System.out.println(true||true);
23.                System.out.println(true||false);
24.                System.out.println(false||false);
25.                System.out.println(false||true);
26.                
27.                //逻辑非：   !  规律：相反结果
28.                System.out.println(!true);//false
29.                System.out.println(!false);//true
30.                
31.                //逻辑异或： ^  规律：两个操作数相同，结果为false，不相同，结果为true
32.                System.out.println(true^true);
33.                System.out.println(true^false);
34.                System.out.println(false^false);
35.                System.out.println(false^true);
36.        }
37.}
```

再做一个加深的练习：看代码 说结果： 

```
1.  public class TestOpe10{
2.          public static void main(String[] args){
3.                  int i=8;
4.                  System.out.println((5>7)&&(i++==2)); //false
5.                  System.out.println(i);  //8 
6.                  
7.                  
8.                  int a=8;
9.                  System.out.println((5>7)&(a++==2)); //false
10.                System.out.println(a); //9
11.                
12.                
13.                int m=8;
14.                System.out.println((5<7)&&(m++==2)); //false
15.                System.out.println(m); //9
16.                
17.                int b=2;
18.                System.out.println((5<7)&(b++==2)); //true
19.                System.out.println(b);  //3
20.                
21.                int c=2;
22.                System.out.println((5<7)&(++c==2)); //false
23.                System.out.println(c);  //3
24.        }
25.}
```

 

#### 条件运算符

【1】条件运算符：又称：  三元运算符/三目运算符 

【2】格式： 

 a?b:c

其中a是一个布尔类型的表达式，返回结果要么是true要么false，通过a的结果决定最终表达式的结果: 

如果a的结果是true，那么表达式最终结果为b

如果a的结果是false，那么表达式最终结果为c 

代码：

```
1.  public class TestOpe11{
2.          public static void main(String[] args){
3.                  int num = (5>7)?6:9 ;
4.                  System.out.println(num);
5.                  
6.                  String str = (4==4)?"你好":"你不好" ;
7.                  System.out.println(str);
8.                  
9.                  System.out.println((4==4)?"你好":"你不好");
10.        }
11.}
```

练习：

```
1.  import java.util.*;//*代表所有
2.  public class TestOpe12{
3.          public static void main(String[] args){
4.                  //实现功能：男孩女孩选择晚饭吃什么，如果意见一致，听男生的，如果意见不一致，听女生的
5.                  
6.                  //1.要让男孩女孩选择晚饭吃什么：
7.                  Scanner sc = new Scanner(System.in);
8.                  System.out.println("请选择今晚吃什么：1.火锅 2.烧烤 3.麻辣烫 4.西餐");
9.                  System.out.println("请男孩选择：");
10.                int boyChoice = sc.nextInt();
11.                System.out.println("请女孩选择：");
12.                int girlChoice = sc.nextInt();
13.                //2.判断：
14.                System.out.println(boyChoice==girlChoice?"听男孩的":"听女孩的");
15.        }
16.}
```

PS:三目运算符可以代替后续我们要学习的if-else 

 

#### 位运算符(了解)

位运算符：&，|，^，~ ， >>，<<，>>>

 

如何区分逻辑运算符和位运算符：

逻辑运算符：左右连接的是布尔类型的操作数

位运算符：左右连接的是具体的数值

 

 

【1】<<  左移 

 3<<2 = 12 

![img](https://image.201068.xyz/assets/clip_image224.jpg)

面试题： 4乘以8最快的方式： 4<<3 

 

【2】>> 有符号右移 

6>>2 = 1 

![img](https://image.201068.xyz/assets/clip_image226.jpg)

 

-6>>2 = -2 

![img](https://image.201068.xyz/assets/clip_image228.jpg)

 

【3】>>> 无符号右移： 

6>>>2  = 1 

![img](https://image.201068.xyz/assets/clip_image230.jpg)

 

【4】 & 与 

6&3 = 2 

![img](https://image.201068.xyz/assets/clip_image232.jpg)

 

【5】| 或 

6|3=7

![img](https://image.201068.xyz/assets/clip_image234.jpg)

 

【6】^异或： 

6^3 = 5 

 

![img](https://image.201068.xyz/assets/clip_image236.jpg)

 

【7】~反： 

~6 = -7 

![img](https://image.201068.xyz/assets/clip_image238.jpg)

PS： 

 

byte类型的表数范围的 -128是怎么算出来的 

127： 01111111 

-128： 10000000 

一看就是个负数

减1：   01111111 

取反：  10000000  ---》2^7  = 128 

加负号：  -128 

#### 运算符总结

![img](https://image.201068.xyz/assets/clip_image240.jpg)

![img](https://image.201068.xyz/assets/clip_image242.jpg)

![img](https://image.201068.xyz/assets/clip_image244.jpg)

 

#### 运算符的优先级别

![img](https://image.201068.xyz/assets/clip_image246.jpg)

不需要去刻意的记优先级关系

赋值<三目<逻辑<关系<算术<单目 

理解运算符的结合性

 

PS:实际开发中我们不会写特别复杂的表达式，你要想先算谁就用() 

 

案例：

  5<6 | &apos;A&apos;>&apos;a&apos; && 12*6<=45+23&&!true 

=5<6 | &apos;A&apos;>&apos;a&apos; && 12*6<=45+23&&false 

= 5<6 | &apos;A&apos;>&apos;a&apos; &&72<=68&&false 

= true|false&&false&&false 

= true&&false&&false 

=false&&false

=false

 

# 第4章_流程控制

#### 引入

【1】流程控制的作用：

流程控制语句是用来控制程序中各语句执行顺序的语句，可以把语句组合成能完成一定功能的小逻辑模块。

【2】控制语句的分类： 

控制语句分为三类：顺序、选择和循环。

“顺序结构”代表“先执行a，再执行b”的逻辑。 

“条件判断结构”代表“如果…，则…”的逻辑。 

“循环结构”代表“如果…，则再继续…”的逻辑。

 三种流程控制语句就能表示所有的事情！不信，你可以试试拆分你遇到的各种事情。这三种基本逻辑结构是相互支撑的，它们共同构成了算法的基本结构，无论怎样复杂的逻辑结构，都可以通过它们来表达。所以任何一种高级语言都具备上述两种结构。

本章是大家真正进入编程界的“门票”。  

【3】流程控制的流程： 

![img](https://image.201068.xyz/assets/clip_image248.jpg)

 

#### 分支结构(选择结构)

#### if

 

###### 单分支

【1】语法结构: 

  if(布尔表达式){      语句块   }   

if语句对布尔表达式进行一次判定，若判定为真，则执行{}中的语句块，否则跳过该语句块。流程图如图所示： 

 

![img](https://image.201068.xyz/assets/clip_image250.jpg)

 

【2】代码： 

```
1.  public class TestIf01{
2.          public static void main(String[] args){
3.                  //实现一个功能：给出三个数（1-6），对三个数求和计算，根据和的大小来分配不同的奖品
4.                  //1.给出三个数：
5.                  int num1 = 6;
6.                  int num2 = 2;
7.                  int num3 = 3;
8.                  //2.求和
9.                  int sum = 0;
10.                sum += num1;
11.                sum += num2;
12.                sum += num3;
13.                System.out.println("和为："+sum);
14.                
15.                //3.根据和判断奖品：
16.                //如果和大于等于14，那么就是一等奖
17.                if(sum>=14){
18.                        System.out.println("一等奖");
19.                        System.out.println("恭喜你很幸运，中了一等奖");
20.                }
21.                
22.                if(sum>=10&&sum<14){
23.                        System.out.println("二等奖");
24.                }
25.                
26.                if(sum>=6&&sum<10){
27.                        System.out.println("三等奖");
28.                }
29.                
30.                if(sum<6){
31.                        System.out.println("四等奖");
32.                }
33.                
34.                /*
35.                if-单分支：
36.                （1）结构：
37.                        if(条件表达式，这个表达式的结果是布尔值：要么是false，要么是true){
38.                                //如果上面()中的表达式返回结果是true，那么执行{}中代码
39.                                //如果上面()中的表达式返回结果是false ，那么不执行{}中代码
40.                                //PS:{}中的代码是否执行，取决于()中表达式的返回结果
41.                        }
42.                （2）上面的代码中，我用四个单分支拼凑出四个选择，每个选择是独立的，依次判断执行的
43.                （3）if后面的()中的条件，要按照自己需求尽量完善
44.                （4）{}可以省略不写,但是一旦省略，这个if就只负责后面的一句话，所以我们不建议初学者省略
45.                */
46.        }
47.}
```

 

###### 多分支

【1】语法结构：

  if(布尔表达式1)  {         语句块1;   } else if(布尔表达式2)  {         语句块2;   }……   else if(布尔表达式n){          语句块n;   } else {         语句块n+1;   }   

当布尔表达式1为真时，执行语句块1；否则，判断布尔表达式2，当布尔表达式2为真时，执行语句块2；否则，继续判断布尔表达式3······；如果1~n个布尔表达式均判定为假时，则执行语句块n+1，也就是else部分。流程图如图所示： 

![img](https://image.201068.xyz/assets/clip_image252.gif)

 

【2】数轴分析： 

![img](https://image.201068.xyz/assets/clip_image254.jpg)

 

【3】代码： 

```
1.  public class TestIf02{
2.          public static void main(String[] args){
3.                  //实现一个功能：给出三个数（1-6），对三个数求和计算，根据和的大小来分配不同的奖品
4.                  //1.给出三个数：
5.                  int num1 = 6;
6.                  int num2 = 4;
7.                  int num3 = 2;
8.                  //2.求和
9.                  int sum = 0;
10.                sum += num1;
11.                sum += num2;
12.                sum += num3;
13.                System.out.println("和为："+sum);
14.                
15.                //3.根据和判断奖品：
16.                /*
17.                利用一个多分支
18.                【1】结构：
19.                if(){
20.                        
21.                }else if(){
22.                        
23.                }else if(){
24.                        
25.                }...
26.                else{
27.                        
28.                }
29.                【2】else:隐藏了一个条件，跟上面分支条件表达式相反的功能 (详见数轴分析)
30.                【3】多分支：好处：只要满足一个 分支以后，后面的分支就不需要判断了 --》效率高
31.                【4】我们写代码的时候，尽量保证else的存在--》else分支相当于“兜底”“备胎”的作用，别的分支都不走，就会走这个分支了
32.                */
33.                if(sum>=14){
34.                        System.out.println("一等奖");
35.                }else if(sum>=10){//隐藏了sum<14
36.                        System.out.println("二等奖");
37.                }else if(sum>=6){//隐藏了sum<10
38.                        System.out.println("三等奖");
39.                }else{//隐藏了sum<6
40.                        System.out.println("四等奖");
41.                }
42.                
43.                
44.                
45.        }
46.}
```

 

###### 双分支

【1】语法结构: 

  if(布尔表达式){    语句块1   }else{      语句块2   }   

当布尔表达式为真时，执行语句块1，否则，执行语句块2。也就是else部分。流程图如图所示：

![img](https://image.201068.xyz/assets/clip_image256.jpg)

###### 随机数

随机数：这个数在生成之前我们不确定这个数是多少，不可知 

 

在java中依靠一个类：Math类帮助我们生成，这个类中有一个方法专门用来生成随机数： 

![img](https://image.201068.xyz/assets/clip_image258.jpg)

 

Math.random() -------> [0.0,1.0) 

Math.random()*6 ----->[0.0,6.0) 

(int)(Math.random()*6) ----->[0,5] 

(int)(Math.random()*6) +1 ----->[1,6] 

应用到程序中：

```
1.  int num1 = (int)(Math.random()*6) +1;
2.  int num2 = (int)(Math.random()*6) +1;
3.  int num3 = (int)(Math.random()*6) +1;
```

 

练习：

[32,98] - [0,66]+32 - (int)(Math.random()*67) + 32 

 

###### 分支的嵌套使用

 

分支结构练习1

练习： 

会员购物时，不同积分享受的折扣不同，规则如下： 

![img](https://image.201068.xyz/assets/clip_image260.jpg)

计算会员购物时获得的折扣，效果如下：

![img](https://image.201068.xyz/assets/clip_image262.jpg)

 

 

本题主要考的是 程序的优化： 

```
1.  import java.util.Scanner;
2.  public class TestIf04{
3.          public static void main(String[] args){
4.                  //1.给出积分：
5.                  Scanner sc = new Scanner(System.in);
6.                  System.out.print("请输入会员积分：");
7.                  
8.                  //先判断键盘录入的数据是不是int类型的
9.                  if(sc.hasNextInt()==true){//是int类型数据：
10.                        //将这个int类型的数据接收：
11.                        int score = sc.nextInt();
12.                        //判断这个积分是否是正数：
13.                        if(score>=0){
14.                                String discount = "";
15.                                //2.根据积分判断折扣：
16.                                if(score>=8000){
17.                                        discount = "0.6";
18.                                }else if(score>=4000){
19.                                        discount = "0.7";
20.                                }else if(score>=2000){
21.                                        discount = "0.8"; 
22.                                }else{
23.                                        discount = "0.9"; 
24.                                }
25.                                System.out.println("该会员享受的折扣为："+discount);
26.                                
27.                        }else{//score<0
28.                                System.out.println("对不起，你录入的积分是负数！不符合需求！");
29.                        }       
30.                }else{//不是int类型的数据
31.                        System.out.println("你录入的积分不是整数！");
32.                }
33.        
34.        }
35.}
```

 

 

分支结构练习2

练习： 

小朋友搬桌子：

年龄大于7岁，可以搬桌子； 

如果年龄大于5岁，性别是男，可以搬桌子； 

否则不可以搬动桌子，提示：你还太小了

 

本题主要考的是：逻辑

 

方式1：性别用0或者1接收： 

```
1.  import java.util.Scanner;
2.  public class TestIf05{
3.          public static void main(String[] args){
4.                  //1.录入小朋友的年龄：
5.                  Scanner sc = new Scanner(System.in);
6.                  System.out.println("请录入小朋友的年龄：");
7.                  int age = sc.nextInt();
8.                  
9.                  //2.根据年龄判断：
10.                if(age>=7){
11.                        System.out.println("yes");
12.                }else if(age>=5){
13.                        //录入小朋友的性别；
14.                        System.out.println("请录入小朋友的性别：男：1  女 ：0");
15.                        int sex = sc.nextInt();
16.                        if(sex==1){//男生
17.                                System.out.println("yes");
18.                        }else{//女孩
19.                                System.out.println("no");
20.                        }
21.                }else{//age<5
22.                        System.out.println("no");
23.                }
24.        }
25.}
```

方式2：性别用男或者女接收： 

```
1.  import java.util.Scanner;
2.  public class TestIf06{
3.          public static void main(String[] args){
4.                  //1.录入小朋友的年龄：
5.                  Scanner sc = new Scanner(System.in);
6.                  System.out.println("请录入小朋友的年龄：");
7.                  int age = sc.nextInt();
8.                  
9.                  //2.根据年龄判断：
10.                if(age>=7){
11.                        System.out.println("yes");
12.                }else if(age>=5){
13.                        //录入小朋友的性别；
14.                        System.out.println("请录入小朋友的性别：");
15.                        String str = sc.next();
16.                        char sex = str.charAt(0);
17.                        if(sex=='男'){
18.                                System.out.println("yes");
19.                        }else{
20.                                System.out.println("no");
21.                        }
22.                }else{//age<5
23.                        System.out.println("no");
24.                }
25.        }
26.}
```

 

 

##### switch

【1】switch多分支结构(多值情况) 

语法结构：

  switch (表达式)  {     case 值1:          语句序列1;          [break];     case 值2:          语句序列2;          [break];         … …  …   … …       [default:默认语句;]   }   

 

switch语句会根据表达式的值从相匹配的case标签处开始执行，一直执行到break语句处或者是switch语句的末尾。如果表达式的值与任一case值不匹配，则进入default语句（如果存在default语句的情况）。根据表达式值的不同可以执行许多不同的操作。switch语句中case标签在JDK1.5之前必须是整数（long类型除外）或者枚举，不能是字符串，在JDK1.7之后允许使用字符串(String)。大家要注意，当布尔表达式是等值判断的情况，可以使用if-else if-else多分支结构或者switch结构，如果布尔表达式区间判断的情况，则只能使用if-else if-else多分支结构。switch多分支结构的流程图如图所示： 

![img](https://image.201068.xyz/assets/clip_image264.gif)

 

【2】练习 

```
1.  public class TestSwitch{
2.          public static void main(String[] args){
3.                  /*
4.                  实现一个功能：
5.                  根据给出的学生分数，判断学生的等级：
6.                  >=90  -----A
7.                  >=80  -----B
8.                  >=70  -----C
9.                  >=60  -----D
10.                <60   -----E
11.                
12.                用if分支：
13.                if(score>=90){
14.                        
15.                }else if(score>=80){
16.                        
17.                }
18.                */
19.                //1.给出学生的成绩：
20.                int score = 167;
21.                //2.根据成绩判断学生的等级：
22.                switch(score/10){
23.                        case 10 : 
24.                        case 9 : System.out.println("A级");break;
25.                        case 8 : System.out.println("B级");break;
26.                        case 7 : System.out.println("C级");break;
27.                        case 6 : System.out.println("D级");break;
28.                        default:System.out.println("成绩错误");break;
29.                        case 5 :  
30.                        case 4 :  
31.                        case 3 :  
32.                        case 2 :  
33.                        case 1 :  
34.                        case 0 : System.out.println("E级");break;
35.                        
36.                }
37.                /*
38.                【1】语法结构：
39.                switch(){
40.                        case * :
41.                        case * :
42.                        .......
43.                }
44.                【2】switch后面是一个()，()中表达式返回的结果是一个等值，这个等值的类型可以为：
45.                int,byte,short,char,String,枚举类型
46.                【3】这个()中的等值会依次跟case后面的值进行比较，如果匹配成功，就执行:后面的代码
47.                【4】为了防止代码的“穿透”效果：在每个分支后面加上一个关键词break，遇到break这个分支就结束了
48.                【5】类似else的“兜底”“备胎”的分支：default分支
49.                【6】default分支可以写在任意的位置上，但是如果没有在最后一行，后面必须加上break关键字，
50.                如果在最后一行的话，break可以省略
51.                【7】相邻分支逻辑是一样的，那么就可以只保留最后一个分支，上面的都可以省去不写了
52.                【8】switch分支和if分支区别：
53.                表达式是等值判断的话--》if ，switch都可以
54.                如果表达式是区间判断的情况---》if最好
55.                【9】switch应用场合：就是等值判断，等值的情况比较少的情况下
56.                */
57.        }
58.}
```

#### 循环结构

 

##### while

【1】语法结构：

  while (布尔表达式)  {           循环体;   }   

在循环刚开始时，会计算一次“布尔表达式”的值，若条件为真，执行循环体。而对于后来每一次额外的循环，都会在开始前重新计算一次。

语句中应有使循环趋向于结束的语句，否则会出现无限循环–––"死"循环。 

while循环结构流程图如图所示: 

![img](https://image.201068.xyz/assets/clip_image266.jpg)

【2】练习：1+2+3+4+5 

```
1.  public class TestWhile{
2.          public static void main(String[] args){
3.                  //功能：1+2+3+4+5
4.                  //1.定义变量：
5.                  int num1 = 1;
6.                  int num2 = 2;
7.                  int num3 = 3;
8.                  int num4 = 4;
9.                  int num5 = 5;
10.                //2.定义一个求和变量，用来接收和：
11.                int sum = 0;
12.                sum += num1;
13.                sum += num2;
14.                sum += num3;
15.                sum += num4;
16.                sum += num5;
17.                
18.                //3.输出和
19.                System.out.println(sum);
20.        }
21.}
```

上述代码缺点：变量的定义个数太多了 

解决：

```
1.  public class TestWhile{
2.          public static void main(String[] args){
3.                  //功能：1+2+3+4+5
4.                  //1.定义变量：
5.                  int num = 1;
6.                  //2.定义一个求和变量，用来接收和：
7.                  int sum = 0;
8.                  sum += num;
9.                  num++;
10.                sum += num;
11.                num++;
12.                sum += num;
13.                num++;
14.                sum += num;
15.                num++;
16.                sum += num;
17.                num++;
18.                
19.                //3.输出和
20.                System.out.println(sum);
21.        }
22.}
```

上述代码缺点：重复写的代码太多了

解决：---》引入java中循环结构： 

```
1.  public class TestWhile{
2.          public static void main(String[] args){
3.                  //功能：1+2+3+4+5
4.                  //1.定义变量：
5.                  int num = 1;[1]条件初始化
6.                  //2.定义一个求和变量，用来接收和：
7.                  int sum = 0;              
8.                  while(num<=5){[2]条件判断
9.                          sum += num;[3]循环体
10.                        num++;[4]迭代
11.                }      
12.                //3.输出和
13.                System.out.println(sum);
14.        }
15.}
```

 

总结：

【1】循环作用：将部分代码重复执行。

        循环只是提高了程序员编写代码的效率，但是底层执行的时候依然是重复执行。

【2】循环四要素： 

 

![img](https://image.201068.xyz/assets/clip_image268.jpg)

初始化谁，就判断谁，判断谁，就迭代谁

执行过程：[1][2][3][4] [2][3][4] [2][3][4]。。。。

 

【3】循环的执行过程： 

![img](https://image.201068.xyz/assets/clip_image270.jpg)

【4】验证循环的执行过程： 

![img](https://image.201068.xyz/assets/clip_image272.jpg)

###### 练习

【1】1+2+3+4+5+。。。。+100 

【2】2+4+6+8+。。。。+998+1000

【3】5+10+15+20+。。。+100

【4】99+97+95+。。5+3+1 

【5】1*3*5*7*9*11*13 

```
1.  public class TestWhile02{
2.          public static void main(String[] args){
3.                  /*
4.                  【1】1+2+3+4+5+。。。。+100
5.                  int i = 1;
6.                  int sum = 0;
7.                  while(i<=100){
8.                          sum += i;
9.                          i++;
10.                }
11.                System.out.println(sum);
12.                【2】2+4+6+8+。。。。+998+1000
13.                int i = 2;
14.                int sum = 0;
15.                while(i<=1000){
16.                        sum += i;
17.                        i = i+2;
18.                }
19.                System.out.println(sum);
20.                【3】5+10+15+20+。。。+100
21.                int i = 5;
22.                int sum = 0;
23.                while(i<=100){
24.                        sum += i;
25.                        i = i+5;
26.                }
27.                System.out.println(sum);
28.                
29.                【4】99+97+95+。。5+3+1
30.                int i = 99;
31.                int sum = 0;
32.                while(i>=1){
33.                        sum += i;
34.                        i = i-2;
35.                }
36.                System.out.println(sum);
37.                【5】1*3*5*7*9*11*13
38.                
39.                */
40.                int i = 1;
41.                int result = 1;
42.                while(i<=13){
43.                        result *= i;
44.                        i = i+2;
45.                }
46.                System.out.println(result);
47.        }
48.}
```

 

 

##### do-while

【1】语法结构：

  do {           循环体;     } while(布尔表达式)  ;   

do-while循环结构会先执行循环体，然后再判断布尔表达式的值，若条件为真，执行循环体，当条件为假时结束循环。do-while循环的循环体至少执行一次。do-while循环结构流程图如图所示： 

![img](https://image.201068.xyz/assets/clip_image274.jpg)

 

【2】代码： 

```
1.  public class TestDoWhile{
2.          public static void main(String[] args){
3.                  //1+2+3+4+...100
4.                  //while方式:
5.                  /*
6.                  int i = 101;
7.                  int sum = 0;
8.                  while(i<=100){
9.                          sum += i;
10.                        i++;
11.                }
12.                System.out.println(i);//101
13.                System.out.println(sum);//0
14.                */
15.                //do-while方式：
16.                
17.                int i = 101;
18.                int sum = 0;
19.                do{
20.                        sum += i;
21.                        i++;
22.                }while(i<=100);//一定要注意写这个分号，否则编译出错
23.                System.out.println(i);//102
24.                System.out.println(sum);//101
25.                /*
26.                【1】while和do-while的区别:
27.                        while:先判断，再执行
28.                        do-while:先执行，再判断---》至少被执行一次，从第二次开始才进行判断
29.                【2】什么场合使用do-while:
30.                
31.                while(考试是否通过){
32.                        考试；
33.                }
34.                ---》不合适
35.                do{
36.                        考试；
37.                }while(考试是否通过);
38.                ---》合适
39.                */
40.                
41.        }
42.}
```

##### for

【1】语法结构：

  for (初始表达式;  布尔表达式; 迭代因子) {          循环体;   }   

for循环语句是支持迭代的一种通用结构，是最有效、最灵活的循环结构。for循环在第一次反复之前要进行初始化，即执行初始表达式；随后，对布尔表达式进行判定，若判定结果为true，则执行循环体，否则，终止循环；最后在每一次反复的时候，进行某种形式的“步进”，即执行迭代因子。 

1. 初始化部分设置循环变量的初值     
2. 条件判断部分为任意布尔表达式     
3. 迭代因子控制循环变量的增减     

for循环在执行条件判定后，先执行的循环体部分，再执行步进。

for循环结构的流程图如图所示： 

![img](https://image.201068.xyz/assets/clip_image276.jpg)

 

【2】代码： 

```
1.  public class TestFor01{
2.          public static void main(String[] args){
3.                  //1+2+3+..+100
4.                  //while:
5.                  /*int i = 1;
6.                  int sum = 0;
7.                  while(i<=100){
8.                          sum += i;
9.                          i++;
10.                }
11.                System.out.println(sum);
12.                */
13.                
14.                //for:
15.                int sum = 0;
16.                int i;
17.                for(i = 1;i<=100;i++){
18.                        sum += i;
19.                }
20.                System.out.println(sum);
21.                System.out.println(i);
22.                
23.                /*
24.                【1】for的结构：
25.                for(条件初始化;条件判断;迭代){
26.                        循环体；
27.                }
28.                
29.                【2】i的作用域：作用范围：离变量最近{}  --->可以自己去控制
30.                【3】for循环格式特别灵活：格式虽然很灵活，但是我们自己写代码的时候不建议灵活着写。
31.                for(;;){}  -->死循环
32.                
33.                int i = 1;
34.                for(;i<=100;){
35.                        sum += i;
36.                        i++;
37.                }
38.                
39.                【4】死循环：
40.                for(;;){}
41.                
42.                while(true){}
43.                
44.                do{
45.                        
46.                }while(true);
47.                
48.                【5】循环分为两大类：
49.                第一类：当型   while(){}   for(;;){}
50.                第二类：直到型  do{}while();
51.                
52.                【6】以后常用：for循环 
53.                【7】do-while,while,for循环谁的效率高？  一样高 
54.                */
55.        }
56.}
```

 

##### 关键字

在任何循环语句的主体部分，均可用break控制循环的流程。break用于强行退出循环，不执行循环中剩余的语句。

continue 语句用在循环语句体中，用于终止某次循环过程，即跳过循环体中尚未执行的语句，接着进行下一次是否执行循环的判定。

return的作用,结束当前所在方法的执行. 

 

###### break

【1】通过练习感受break的作用：作用：停止循环： 

```
1.  public class TestFor02{
2.          public static void main(String[] args){
3.                  //功能：求1-100的和，当和第一次超过300的时候，停止程序
4.                  int sum = 0;
5.                  for(int i=1;i<=100;i++){       
6.                          sum += i;       
7.                          if(sum>300){//当和第一次超过300的时候
8.                                  //停止循环
9.                                  break;//停止循环
10.                        }
11.                        System.out.println(sum);
12.                }
13.                
14.        }
15.}
```

【2】加深理解： 

```
1.  public class TestFor03{
2.          public static void main(String[] args){
3.                  //break的作用：停止最近的循环
4.                  /*
5.                  for(int i=1;i<=100;i++){
6.                          System.out.println(i);
7.                          if(i==36){
8.                                  break;//1-36
9.                          }
10.                }
11.                */
12.                for(int i=1;i<=100;i++){
13.                        System.out.println(i);
14.                        while(i==36){
15.                                break; //1-100  ---》break停止的是while循环，而不是外面的for循环
16.                        }
17.                }
18.        }
19.}
```

【3】break带标签的使用： 

```
1.  public class TestFor04{
2.          public static void main(String[] args){
3.                  outer:     ----》定义标签结束的位置
4.                  for(int i=1;i<=100;i++){
5.                          System.out.println(i);
6.                          while(i==36){
7.                                  break outer;    ----》根据标签来结束循环 
8.                          }
9.                  }
10.        }
11.}
```

多层循环也可以使用标签，按照自己的需求去设定即可：

![img](https://image.201068.xyz/assets/clip_image278.jpg)

 

 

 

 

 

 

###### continue

【1】通过案例感受continue的作用：结束本次循环，继续下一次循环 

```
1.  public class TestFor05{
2.          public static void main(String[] args){
3.                  //功能：输出1-100中被6整除的数：
4.                  //方式1：
5.                  /*
6.                  for(int i=1;i<=100;i++){       
7.                          if(i%6==0){//被6整除
8.                                  System.out.println(i);
9.                          }
10.                }
11.                */
12.                
13.                //方式2：
14.                for(int i=1;i<=100;i++){       
15.                        if(i%6!=0){//不被6整除
16.                                continue;//停止本次循环，继续下一次循环
17.                        }
18.                        System.out.println(i);
19.                }
20.        }
21.}
```

【2】加深理解： 

```
1.  public class TestFor06{
2.          public static void main(String[] args){
3.                  //continue:结束本次离它近的循环，继续下一次循环
4.                  /*
5.                  for(int i=1;i<=100;i++){       
6.                          if(i==36){
7.                                  continue;//1-100中间没有36
8.                          }
9.                          System.out.println(i);
10.                }
11.                */
12.                
13.                for(int i=1;i<=100;i++){       
14.                        while(i==36){
15.                                System.out.println("------");
16.                                continue; //1-35+死循环
17.                        }
18.                        System.out.println(i);
19.                }
20.        }
21.}
```

【3】continue带标签的使用： 

```
1.  public class TestFor07{
2.          public static void main(String[] args){
3.                  
4.                  outer:
5.                  for(int i=1;i<=100;i++){       
6.                          while(i==36){ 
7.                                  continue outer;  //1-100没有36
8.                          }
9.                          System.out.println(i);
10.                }
11.        }
12.}
```

 

![img](https://image.201068.xyz/assets/clip_image280.jpg)

###### return

return的作用：跟循环无关，就是程序中遇到return那么return所在的那个方法就停止执行了： 

```
1.  public class TestFor08{
2.          public static void main(String[] args){
3.                  //return:遇到return结束当前正在执行的方法
4.                  for(int i=1;i<=100;i++){       
5.                          while(i==36){ 
6.                                  return;  
7.                          }
8.                          System.out.println(i);
9.                  }
10.                
11.                System.out.println("-----");
12.        }
13.}
```

##### 循环练习

【1】练习1： 

```
1.  public class TestFor09{
2.          public static void main(String[] args){
3.                  /* 输出1-100中被5整除的数,每行输出6个*/
4.                  //引入一个计数器：
5.                  int count = 0;//初始值为0
6.                  for(int i=1;i<=100;i++){
7.                          if(i%5==0){//被5整除的数
8.                                  System.out.print(i+"\t");
9.                                  count++;//每在控制台输出一个数，count就加1操作
10.                                if(count%6==0){
11.                                        System.out.println();//换行
12.                                }
13.                        }
14.                }
15.        }
16.}
```

 

【2】练习2： 

```
1.  import java.util.Scanner;
2.  public class TestFor10{
3.          public static void main(String[] args){
4.                  /*
5.                          实现一个功能： 
6.                     【1】请录入10个整数，当输入的数是666的时候，退出程序。
7.                     【2】判断其中录入正数的个数并输出。
8.                     【3】判断系统的退出状态：是正常退出还是被迫退出。
9.                  */
10.                //引入一个计数器：
11.                int count = 0;
12.                //引入一个布尔类型的变量：
13.                boolean flag = true; //---》理解为一个“开关”，默认情况下开关是开着的
14.                Scanner sc = new Scanner(System.in);
15.                for(int i=1;i<=10;i++){//i:循环次数
16.                        System.out.println("请录入第"+i+"个数：");
17.                        int num = sc.nextInt();
18.                        if(num>0){//录入的正数
19.                                count++;
20.                        }
21.                        if(num==666){
22.                                flag = false;//当遇到666的时候，“开关”被关上了
23.                                //退出循环：
24.                                break;
25.                        }
26.                        
27.                }
28.                
29.                System.out.println("你录入的正数的个数为："+count);
30.                
31.                
32.                if(flag){//flag==true
33.                        System.out.println("正常退出！");
34.                }else{//flag==false
35.                        System.out.println("被迫退出！");
36.                }
37.                
38.                
39.                
40.        }
41.}
```

##### 循环的嵌套使用

###### 双重循环

乘法口诀

乘法口诀： 

1*1=1

1*2=2  2*2=4 

1*3=3  2*3=6  3*3=9 

1*4=4  2*4=8  3*4=12 4*4=16 

1*5=5  2*5=10 3*5=15 4*5=20 5*5=25 

1*6=6  2*6=12 3*6=18 4*6=24 5*6=30 6*6=36 

1*7=7  2*7=14 3*7=21 4*7=28 5*7=35 6*7=42 7*7=49 

1*8=8  2*8=16 3*8=24 4*8=32 5*8=40 6*8=48 7*8=56 8*8=64 

1*9=9  2*9=18 3*9=27 4*9=36 5*9=45 6*9=54 7*9=63 8*9=72 9*9=81 

 

代码：

```
1.  public class TestFor11{
2.      public static void main(String[] args){
3.                  //1*6=6   2*6=12  3*6=18  4*6=24  5*6=30  6*6=36
4.                  /*
5.                  System.out.print("1*6=6"+"\t");
6.                  System.out.print("2*6=12"+"\t");
7.                  System.out.print("3*6=18"+"\t");
8.                  System.out.print("4*6=24"+"\t");
9.                  System.out.print("5*6=30"+"\t");
10.                System.out.print("6*6=36"+"\t");
11.                
12.                for(int i=1;i<=6;i++){
13.                        System.out.print(i+"*6="+i*6+"\t");
14.                }
15.                //换行
16.                System.out.println();
17.                
18.                //1*7=7   2*7=14  3*7=21  4*7=28  5*7=35  6*7=42  7*7=49
19.                for(int i=1;i<=7;i++){
20.                        System.out.print(i+"*7="+i*7+"\t");
21.                }
22.                //换行
23.                System.out.println();
24.                
25.                //1*8=8   2*8=16  3*8=24  4*8=32  5*8=40  6*8=48  7*8=56  8*8=64
26.                for(int i=1;i<=8;i++){
27.                        System.out.print(i+"*8="+i*8+"\t");
28.                }
29.                //换行
30.                System.out.println();
31.                */
32.                
33.                for(int j=1;j<=9;j++){
34.                        for(int i=1;i<=j;i++){
35.                                System.out.print(i+"*"+j+"="+i*j+"\t");
36.                        }
37.                        //换行
38.                        System.out.println();
39.                }
40.        }
41.}
```

 

1*9=9  2*9=18 3*9=27 4*9=36 5*9=45 6*9=54 7*9=63 8*9=72 9*9=81 

1*8=8  2*8=16 3*8=24 4*8=32 5*8=40 6*8=48 7*8=56 8*8=64 

1*7=7  2*7=14 3*7=21 4*7=28 5*7=35 6*7=42 7*7=49 

1*6=6  2*6=12 3*6=18 4*6=24 5*6=30 6*6=36 

1*5=5  2*5=10 3*5=15 4*5=20 5*5=25 

1*4=4  2*4=8  3*4=12 4*4=16 

1*3=3  2*3=6  3*3=9 

1*2=2  2*2=4 

1*1=1

 

代码：

```
1.  public class TestFor12{
2.      public static void main(String[] args){
3.                  
4.                  /*
5.                  //1*8=8   2*8=16  3*8=24  4*8=32  5*8=40  6*8=48  7*8=56  8*8=64
6.                  for(int i=1;i<=8;i++){
7.                          System.out.print(i+"*8="+i*8+"\t");
8.                  }
9.                  //换行
10.                System.out.println();
11.                
12.                
13.                //1*7=7   2*7=14  3*7=21  4*7=28  5*7=35  6*7=42  7*7=49
14.                for(int i=1;i<=7;i++){
15.                        System.out.print(i+"*7="+i*7+"\t");
16.                }
17.                //换行
18.                System.out.println();
19.                 
20.                //1*6=6   2*6=12  3*6=18  4*6=24  5*6=30  6*6=36
21.                for(int i=1;i<=6;i++){
22.                        System.out.print(i+"*6="+i*6+"\t");
23.                }
24.                //换行
25.                System.out.println();
26.                
27.                
28.                
29.                
30.                */
31.                
32.                for(int j=9;j>=1;j--){
33.                        for(int i=1;i<=j;i++){
34.                                System.out.print(i+"*"+j+"="+i*j+"\t");
35.                        }
36.                        //换行
37.                        System.out.println();
38.                }
39.        }
40.}
```

打印各种形状

【1】长方形：

![img](https://image.201068.xyz/assets/clip_image282.jpg)

```
 
1.                  for(int j=1;j<=4;j++){//j:控制行数
2.                          //*********
3.                          for(int i=1;i<=9;i++){//i:控制*的个数
4.                                  System.out.print("*");
5.                          }
6.                          //换行：
7.                          System.out.println();
8.                  }
```

【2】距离前面有一定空隙的长方形： 

![img](https://image.201068.xyz/assets/clip_image284.jpg)

```
1.                 for(int j=1;j<=4;j++){//j:控制行数
2.                          //加入空格：
3.                          for(int i=1;i<=5;i++){//i:控制空格的个数
4.                                  System.out.print(" ");
5.                          }
6.                          //*********
7.                          for(int i=1;i<=9;i++){//i:控制*的个数
8.                                  System.out.print("*");
9.                          }
10.                        //换行：
11.                        System.out.println();
12.                }
```

【3】平行四边形： 

![img](https://image.201068.xyz/assets/clip_image286.jpg)

```
1.  for(int j=1;j<=4;j++){//j:控制行数
2.                          //加入空格：
3.                          for(int i=1;i<=(9-j);i++){//i:控制空格的个数
4.                                  System.out.print(" ");
5.                          }
6.                          //*********
7.                          for(int i=1;i<=9;i++){//i:控制*的个数
8.                                  System.out.print("*");
9.                          }
10.                        //换行：
11.                        System.out.println();
12.                }
```

 

【4】三角形： 

![img](https://image.201068.xyz/assets/clip_image288.jpg)

```
1.  for(int j=1;j<=4;j++){//j:控制行数
2.                          //加入空格：
3.                          for(int i=1;i<=(9-j);i++){//i:控制空格的个数
4.                                  System.out.print(" ");
5.                          }
6.                          //*********
7.                          for(int i=1;i<=(2*j-1);i++){//i:控制*的个数
8.                                  System.out.print("*");
9.                          }
10.                        //换行：
11.                        System.out.println();
12.                }
```

【5】菱形： 

![img](https://image.201068.xyz/assets/clip_image290.jpg)

```
1.  //上面三角形：
2.                  for(int j=1;j<=4;j++){//j:控制行数
3.                          //加入空格：
4.                          for(int i=1;i<=(9-j);i++){//i:控制空格的个数
5.                                  System.out.print(" ");
6.                          }
7.                          //*********
8.                          for(int i=1;i<=(2*j-1);i++){//i:控制*的个数
9.                                  System.out.print("*");
10.                        }
11.                        //换行：
12.                        System.out.println();
13.                }
14.                
15.                //下面三角形：
16.                for(int j=1;j<=3;j++){//j:控制行数
17.                        //加入空格：
18.                        for(int i=1;i<=(j+5);i++){//i:控制空格的个数
19.                                System.out.print(" ");
20.                        }
21.                        //*********
22.                        for(int i=1;i<=(7-2*j);i++){//i:控制*的个数
23.                                System.out.print("*");
24.                        }
25.                        //换行：
26.                        System.out.println();
27.                }
```

【6】空心菱形： 

![img](https://image.201068.xyz/assets/clip_image292.jpg)

```
1.  //上面三角形：
2.                  for(int j=1;j<=4;j++){//j:控制行数
3.                          //加入空格：
4.                          for(int i=1;i<=(9-j);i++){//i:控制空格的个数
5.                                  System.out.print(" ");
6.                          }
7.                          //*********
8.                          for(int i=1;i<=(2*j-1);i++){//i:控制*的个数
9.                                  if(i==1||i==(2*j-1)){
10.                                        System.out.print("*");
11.                                }else{
12.                                        System.out.print(" ");
13.                                }
14.                        }
15.                        //换行：
16.                        System.out.println();
17.                }
18.                
19.                //下面三角形：
20.                for(int j=1;j<=3;j++){//j:控制行数
21.                        //加入空格：
22.                        for(int i=1;i<=(j+5);i++){//i:控制空格的个数
23.                                System.out.print(" ");
24.                        }
25.                        //*********
26.                        for(int i=1;i<=(7-2*j);i++){//i:控制*的个数
27.                                if(i==1||i==(7-2*j)){
28.                                        System.out.print("*");
29.                                }else{
30.                                        System.out.print(" ");
31.                                }
32.                        }
33.                        //换行：
34.                        System.out.println();
35.                }
```

 

 

 

 

 

扩展：菱形打印方式2

【1】实心菱形：

![img](https://image.201068.xyz/assets/clip_image294.jpg)

```
1.  public class TestFor14{
2.      public static void main(String[] args){
3.                  //先打印出一个正方形，然后某些位置上打印* 某些位置上打印空格：
4.                  int size = 17;
5.                  int startNum = size/2+1;//起始列号
6.                  int endNum = size/2+1;//结束列号
7.                  //引入一个布尔类型的变量---》理解为“开关”
8.                  boolean flag = true;
9.                  for(int j=1;j<=size;j++){
10.                        //*****
11.                        for(int i=1;i<=size;i++){
12.                                if(i>=startNum&&i<=endNum){
13.                                        System.out.print("*");
14.                                }else{
15.                                        System.out.print(" ");
16.                                }
17.                        }
18.                        //换行
19.                        System.out.println();
20.                        if(endNum==size){
21.                                flag = false;
22.                        }
23.                        
24.                        if(flag){//flag是true相当于在菱形的上半侧   flag是false相当于在菱形的下半侧
25.                                startNum--;
26.                                endNum++;
27.                        }else{
28.                                startNum++;
29.                            endNum--;
30.                        }
31.                }
32.        }
33.}
```

【2】空心菱形： 

![img](https://image.201068.xyz/assets/clip_image296.jpg)

```
1.  public class TestFor14{
2.      public static void main(String[] args){
3.                  //先打印出一个正方形，然后某些位置上打印* 某些位置上打印空格：
4.                  int size = 17;
5.                  int startNum = size/2+1;//起始列号
6.                  int endNum = size/2+1;//结束列号
7.                  //引入一个布尔类型的变量---》理解为“开关”
8.                  boolean flag = true;
9.                  for(int j=1;j<=size;j++){
10.                        //*****
11.                        for(int i=1;i<=size;i++){
12.                                if(i==startNum||i==endNum){
13.                                        System.out.print("*");
14.                                }else{
15.                                        System.out.print(" ");
16.                                }
17.                        }
18.                        //换行
19.                        System.out.println();
20.                        if(endNum==size){
21.                                flag = false;
22.                        }
23.                        
24.                        if(flag){//flag是true相当于在菱形的上半侧   flag是false相当于在菱形的下半侧
25.                                startNum--;
26.                                endNum++;
27.                        }else{
28.                                startNum++;
29.                            endNum--;
30.                        }
31.                }
32.        }
33.}
```

 

###### 三重循环

 

百钱买百鸡

【1】二重循环可以帮我们解决：二元一次方程组的问题：

```
1.  public class TestFor15{
2.      public static void main(String[] args){
3.                  for(int a=1;a<=5;a++){
4.                          for(int b=3;b<=6;b++){
5.                                  if(a+b==7){
6.                                          System.out.println(a+"----"+b);
7.                                  }
8.                          }
9.                  }
10.        }
11.}
```

【2】三重循环可以帮我们解决：三元一次方程组的问题： 

```
1.  public class TestFor16{
2.      public static void main(String[] args){
3.                  /*
4.  百钱买百鸡：
5.  公鸡5文钱一只，母鸡3文钱一只，小鸡3只一文钱，
6.  用100文钱买一百只鸡,其中公鸡，母鸡，小鸡都必须要有，问公鸡，母鸡，小鸡要买多少只刚好凑足100文钱。
7.   
8.  数学：
9.  设未知数：
10.公鸡：x只
11.母鸡：y只
12.小鸡：z只
13.x+y+z=100只
14.5x+3y+z/3=100钱
15.                麻烦方式：
16.                for(int x=1;x<=100;x++){
17.                        for(int y=1;y<=100;y++){
18.                                for(int z=1;z<=100;z++){
19.                                        if((x+y+z==100)&&(5*x+3*y+z/3==100)&&(z%3==0)){
20.                                                System.out.println(x+"\t"+y+"\t"+z);
21.                                        }
22.                                }
23.                        }
24.                }
25.                */
26.                //优化：
27.                for(int x=1;x<=19;x++){
28.                        for(int y=1;y<=31;y++){
29.                                int z = 100-x-y;
30.                                if((5*x+3*y+z/3==100)&&(z%3==0)){
31.                                        System.out.println(x+"\t"+y+"\t"+z);
32.                                } 
33.                        }
34.                }
35.        }
36.}
37. 
```

 

# 第5章_方法的定义/调用/重载

 

#### 方法的定义和调用

【1】什么是方法？

方法(method)就是一段用来完成特定功能的代码片段，类似于其它语言的函数(function)。

方法用于定义该类或该类的实例的行为特征和功能实现。 方法是类和对象行为特征的抽象。方法很类似于面向过程中的函数。面向过程中，函数是最基本单位，整个程序由一个个函数调用组成。面向对象中，整个程序的基本单位是类，方法是从属于类和对象的。 

 

【2】方法声明格式： 

  [修饰符1   修饰符2 …] 返回值类型  方法名(形式参数列表){         Java语句；… … …   }   

 

【3】方法的调用方式： 

  对象名.方法名(实参列表)   

 

【4】方法的详细说明 

- 形式参数：在方法声明时用于接收外界传入的数据。     
- 实参：调用方法时实际传给方法的数据。     
- 返回值：方法在执行完毕后返还给调用它的环境的数据。     
- 返回值类型：事先约定的返回值的数据类型，如无返回值，必须显示指定为为void。 

 

【5】代码： 

```
1.  public class TestMethod01{
2.          
3.          //方法的定义：（写方法）
4.          public static int add(int num1,int num2){
5.                  int sum = 0;
6.                  sum += num1;
7.                  sum += num2;
8.                  return sum;//将返回值返回到方法的调用处
9.          }
10.        
11.    public static void main(String[] args){
12.                //10+20:
13.                //方法的调用：（用方法）
14.                int num = add(10,20);
15.                System.out.println(num);
16.                /*
17.                int num1 = 10;
18.                int num2 = 20;
19.                int sum = 0;
20.                sum += num1;
21.                sum += num2;
22.                System.out.println(sum);
23.                */
24.                //30+90:
25.                int sum = add(30,90);
26.                System.out.println(sum);
27.                /*
28.                int num3 = 30;
29.                int num4 = 90;  
30.                int sum1 = 0 ;
31.                sum1 += num3;
32.                sum1 += num4;
33.                System.out.println(sum1);
34.                */
35.                //50+48:
36.                System.out.println(add(50,48));
37.        
38.        }
39.        
40.        
41.}
```

【6】总结： 

 

1.方法是：对特定的功能进行提取，形成一个代码片段，这个代码片段就是我们所说的方法

2.方法和方法是并列的关系，所以我们定义的方法不能写到main方法中 

3.方法的定义--》格式：

​    修饰符 方法返回值类型 方法名(形参列表){ 

​        方法体; 

​        return 方法返回值; 

​    } 

 

4.方法的作用：提高代码的复用性 

5.总结方法定义的格式： 

\1) 修饰符: 暂时使用public static --->面向对象一章讲解 

\2) 方法返回值类型 : 方法的返回值对应的数据类型 

  数据类型： 可以是基本数据类型（byte,short,int,long,float,double,char,boolean） 也可以是引用数据类型 

\3) 方法名 :见名知意，首字母小写，其余遵循驼峰命名，  eg: addNum ,一般尽量使用英文来命名  

\4) 形参列表 :方法定义的时候需要的形式参数 ：  int  num1, int num2 -->相当于告诉方法的调用者：需要传入几个参数，需要传入的参数的类型

  实际参数：方法调用的时候传入的具体的参数：  10,20  -->根据形式参数的需要传入的 

 

5)方法体：具体的业务逻辑代码 

\6) return 方法返回值; 

方法如果有返回值的话： return+方法返回值，将返回值返回到方法的调用处 

方法没有返回值的话：return可以省略不写了，并且方法的返回值类型为：void 

 

```
1.  public class TestMethod02{
2.           
3.          public static void add(int num1,int num2){
4.                  int sum = 0;
5.                  sum += num1;
6.                  sum += num2;    
7.                  System.out.println(sum);
8.                  //return; 
9.          }
10.        
11.    public static void main(String[] args){
12.                //10+20:
13.                //方法的调用：（用方法）
14.                add(10,20); 
15.                //30+90:
16.                add(30,90);
17.                //50+48:
18.                //System.out.println(add(50,48));//报错：TestMethod02.java:22: 错误: 此处不允许使用 '空' 类型
19.   
20.        }
21. 
22.}
```

 

什么时候有返回值，什么时候没有返回值？ 看心情--》看需求 

6.方法的定义需要注意什么？ 

1）形参列表要怎么写：定义几个参数，分别是什么类型的  ---》不确定因素我们会当做方法的形参

\2) 方法到底是否需要返回值 ，如果需要的话，返回值的类型是什么 

 

7.方法的调用需要注意什么？ 

1）实际参数要怎么传入：传入几个参数，传入什么类型的

2） 方法是否有返回值需要接受 

##### 练习

【1】基本功能：

```
1.  import java.util.Scanner;
2.  public class TestMethod03{
3.      public static void main(String[] args){
4.                  //功能：我心里有一个数，你来猜，看是否猜对
5.                  //1.你猜一个数
6.                  Scanner sc = new Scanner(System.in);
7.                  System.out.println("请你猜一个数：");
8.                  int yourGuessNum = sc.nextInt();
9.                  //2.我心里有一个数
10.                int myHeartNum = 5;
11.                //3.将两个数比对：
12.                System.out.println(yourGuessNum==myHeartNum?"猜对了":"猜错了");
13.        }
14.}
```

对猜数功能提取为一个方法：

```
1.  import java.util.Scanner;
2.  public class TestMethod03{
3.      public static void main(String[] args){
4.                  //功能：我心里有一个数，你来猜，看是否猜对
5.                  //1.你猜一个数
6.                  Scanner sc = new Scanner(System.in);
7.                  System.out.println("请你猜一个数：");
8.                  int yourGuessNum = sc.nextInt();
9.                  
10.                //调用猜数的方法：
11.                guessNum(yourGuessNum);
12.        }
13.        
14.        //方法的定义：功能：实现猜数功能：
15.        public static void guessNum(int yourNum){
16.                //我心里有一个数(1-6)
17.                int myHeartNum = (int)(Math.random()*6)+1;
18.                //将两个数比对：
19.                System.out.println(yourNum==myHeartNum?"猜对了":"猜错了");     
20.        }
21.}
```

 

 

##### 面试题：两个数交换是否成功

【1】面试题：请问下面代码中两个数是否交换成功：

  public class TestM{         public static void main(String[] args){             int a=10;             int b=20;             System.out.println("输出交换前的两个数："+a+"---"+b);             changeNum(a,b);             System.out.println("输出交换后的两个数："+a+"---"+b);         }         public static void changeNum(int num1,int num2){             int t;             t=num1;             num1=num2;             num2=t;         }   }   

 

结果：没有交换成功：

![img](https://image.201068.xyz/assets/clip_image298.jpg)

 

原因：

![img](https://image.201068.xyz/assets/clip_image300.jpg)

 

#### 方法的重载

【1】什么是方法的重载：

方法的重载是指一个类中可以定义多个方法名相同，但参数不同的方法。 调用时，会根据不同的参数自动匹配对应的方法。

 

注意本质：重载的方法，实际是完全不同的方法，只是名称相同而已！

 

【2】构成方法重载的条件： 

❀不同的含义：形参类型、形参个数、形参顺序不同

❀ 只有返回值不同不构成方法的重载

如：int a(String str){}与 void a(String str){}不构成方法重载

❀ 只有形参的名称不同，不构成方法的重载

如：int a(String str){}与int a(String s){}不构成方法重载

 

【3】代码： 

```
1.  public class TestMethod05{
2.      public static void main(String[] args){
3.                  //10+20:
4.                  int sum = add(10,20);
5.                  System.out.println(sum);
6.                  
7.                  //20+40+80:
8.                  //System.out.println(add(add(20,40),80));
9.                  System.out.println(add(20,40,80));
10.                //30+60+90+120:
11.                //System.out.println(add(add(30,60),add(90,120)));
12.                System.out.println(add(30,60,90,120));
13.                //9.8+4.7:
14.                //System.out.println(add(9.8,4.7));
15.                System.out.println(add(9.8,4.7));
16.        }
17.        
18.        //定义一个方法：两个数相加：两个int类型数据相加
19.        public static int add(int num1,int num2){
20.                return num1+num2;
21.        }
22.        
23.        //定义一个方法：三个数相加：
24.        public static int add(int num1,int num2,int num3){
25.                return num1+num2+num3;
26.        }
27.        
28.        //定义一个方法：四个数相加：
29.        public static int add(int num1,int num2,int num3,int num4){
30.                return num1+num2+num3+num4;
31.        }
32.        //定义一个方法：两个数相加：两个double类型的数据相加
33.        public static double add(double num1,double num2){
34.                return num1+num2;
35.        }
36.        
37.        
38.}
```

 

总结：

1.方法的重载：在同一个类中，方法名相同，形参列表不同的多个方法，构成了方法的重载。

2.方法的重载只跟：方法名和形参列表有关，与修饰符，返回值类型无关。

3.注意：形参列表不同指的是什么？ 

（1）个数不同 

add()  add(int num1)  add(int num1,int num2) 

（2）顺序不同 

add(int num1,double num2)  add(double num1,int num2) 

（3）类型不同 

add(int num1)  add(double num1) 

 

4.请问下面的方法是否构成了方法的重载？ 

(1)add(int a)  和  add(int b)  --->不构成,相当于方法的重复定义

(2)public static int add(int a) 和  public static void add(int b)  --->不构成 

 

【4】扩充： 

```
1.  public class TestMethod06{
2.      public static void main(String[] args){
3.                  add(5);
4.                  //级别：byte,short,char-->int-->long-->float--->double
5.          }
6.          
7.          public static void add(double num1){
8.                  System.out.println("------2");
9.          }
10.        public static void add(float num1){
11.                System.out.println("------3");
12.        }
13.        public static void add(long num1){
14.                System.out.println("------4");
15.        }
16.        /*
17.        public static void add(int num1){
18.                System.out.println("------1");
19.        }
20.        */
21.}
```

# 第6章_数组

 

#### 数组的引入

【1】习题引入：

```
1.  import java.util.Scanner;
2.  public class TestArray01{
3.      public static void main(String[] args){
4.                  //功能：键盘录入十个学生的成绩，求和，求平均数：
5.                  //定义一个求和的变量：
6.                  int sum = 0;
7.                  Scanner sc = new Scanner(System.in);
8.   
9.                  for(int i=1;i<=10;i++){//i:控制循环次数
10.                        System.out.print("请录入第"+i+"个学生的成绩：");
11.                        int score = sc.nextInt();
12.                        sum += score;
13.                }
14.                
15.                System.out.println("十个学生的成绩之和为："+sum);
16.                System.out.println("十个学生的成绩平均数为："+sum/10);
17.                
18.                //本题的缺点：
19.                //求第6个学生的成绩：？？？？？---》不能
20.                
21.        }
22.}
```

缺点：就是不能求每个学生的成绩具体是多少

解决：将成绩进行存储  ----》 引入 ： 数组 

感受到数组的作用：数组用来存储数据的，在程序设计中，为了处理方便，数组用来将相同类型的若干数据组织起来。

这个若干数据的集合我们称之为数组。

 

 

 

 

 

#### 数组的学习

【1】数组的定义

数组是相同类型数据的有序集合。数组描述的是相同类型的若干个数据，按照一定的先后次序排列组合而成。其中，每一个数据称作一个元素，每个元素可以通过一个索引（下标）来访问它们。

数组的四个基本特点：

1.长度是确定的。数组一旦被创建，它的大小就是不可以改变的。 

2.其元素的类型必须是相同类型，不允许出现混合类型。

3.数组类型可以是任何数据类型，包括基本类型和引用类型。

4.数组有索引的：索引从0开始，到 数组.length-1 结束 

5.数组变量属于引用类型，数组也是对象。 

PS:数组变量属于引用类型，数组也是对象，数组中的每个元素相当于该对象的成员变量。数组本身就是对象，Java中对象是在堆中的，因此数组无论保存原始类型还是其他对象类型，数组对象本身是在堆中存储的。 

 

【2】数组的学习： 

```
1.  public class TestArray02{
2.      public static void main(String[] args){
3.                  //数组的作用：用来存储相同类型的数据
4.                  //以int类型数据为案例：数组用来存储int类型数据
5.                  //1.声明(定义数组)
6.                  int[] arr; //定义一个int类型的数组，名字叫arr
7.                  //int arr2[];
8.                  //如果数组只声明，没有后续操作，那么这个数组相当于没定义
9.                  //int[] arr3 = null;//空 辨别：数组赋值为null和什么都没有赋值  不一样的效果 
10.                
11.                //2.创建
12.                arr = new int[4];//给数组开辟了一个长度为4的空间
13.                //编译期声明和创建会被合为一句话: int[] arr = new int[4];
14.                
15.                //3.赋值
16.                arr[0] = 12;
17.                arr[3] = 47;
18.                arr[2] = 98;
19.                arr[1] = 56;
20.                arr[2] = 66;
21.                /*
22.                arr[4] = 93;
23.                出现异常：Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: 4
24.                Array 数组
25.                Index 索引
26.                OutOf 超出
27.                Bounds 界限
28.                Exception 异常
29.                ---》数组索引越界异常  
30.                */
31.        
32.                //4.使用
33.                System.out.println(arr[2]);
34.                System.out.println(arr[0]+100);
35.                //通过数组一个属性来获取  length 长度
36.                System.out.println("数组的长度是："+arr.length);
37.        }
38.}
```

 

 

##### 内存分析

![img](https://image.201068.xyz/assets/clip_image302.jpg)

 

#### 完善引入的习题_数组的遍历

【1】代码：

```
1.  import java.util.Scanner;
2.  public class TestArray03{
3.      public static void main(String[] args){
4.                  //功能：键盘录入十个学生的成绩，求和，求平均数：
5.                  //定义一个int类型的数组，长度为10 ：
6.                  int[] scores = new int[10];
7.                  //定义一个求和的变量：
8.                  int sum = 0;
9.                  Scanner sc = new Scanner(System.in);
10. 
11.                for(int i=1;i<=10;i++){//i:控制循环次数
12.                        System.out.print("请录入第"+i+"个学生的成绩：");
13.                        int score = sc.nextInt();
14.                        scores[i-1] = score;
15.                        sum += score;
16.                }
17.                
18.                System.out.println("十个学生的成绩之和为："+sum);
19.                System.out.println("十个学生的成绩平均数为："+sum/10);
20.                
21.                 
22.                //求第6个学生的成绩： 
23.                //System.out.println(scores[5]);
24.                /*
25.                System.out.println(scores[0]);
26.                System.out.println(scores[1]);
27.                System.out.println(scores[2]);
28.                System.out.println(scores[3]);
29.                //....
30.                System.out.println(scores[9]);
31.                */
32.                //将数组中的每个元素进行查看--》数组的遍历：
33.                //方式1：普通for循环---》正向遍历：
34.                for(int i=0;i<=9;i++){
35.                        System.out.println("第"+(i+1)+"个学生的成绩为："+scores[i]);
36.                }
37.                
38.                //方式2：增强for循环:
39.                //对scores数组进行遍历，遍历出来每个元素都用int类型的num接收：
40.                int count = 0;
41.                for(int num:scores){
42.                        count++;
43.                        //每次都将num在控制台输出
44.                        System.out.println("第"+count+"个学生的成绩为："+num);
45.                }
46.                
47.                /*
48.                增强for循环：
49.                优点：代码简单
50.                缺点：单纯的增强for循环不能涉及跟索引相关的操作
51.                */
52.                
53.                //方式3：利用普通for循环： 逆向遍历：
54.                for(int i=9;i>=0;i--){
55.                        System.out.println("第"+(i+1)+"个学生的成绩为："+scores[i]);
56.                }
57.                
58.        }
59.}
```

【2】用IDEA验证数组的确将数据进行存储了： 

![img](https://image.201068.xyz/assets/clip_image304.jpg)

#### 数组的三种初始化方式

数组的初始化方式总共有三种：静态初始化、动态初始化、默认初始化。

- 静态初始化     

除了用new关键字来产生数组以外，还可以直接在定义数组的同时就为数组元素分配空间并赋值。 

 

eg:

int[] arr = {12,23,45}; 

int[] arr = new int[]{12,23,45}; 

注意：

1.new int[3]{12,23,45};-->错误 

2.int[] arr ; 

  arr = {12,23,45};  --->错误 

- 动态初始化     

数组定义与为数组元素分配空间并赋值的操作分开进行。

eg:

int[] arr ; 

arr = new int[3] 

arr[0] = 12; 

arr[1] = 23; 

arr[2] = 45; 

- 默认初始化     

数组是引用类型，它的元素相当于类的实例变量，因此数组一经分配空间，其中的每个元素也被按照实例变量同样的方式被隐式初始化。

 

int[] arr = new int[3];  ---> 数组有默认的初始化值 

 

![img](https://image.201068.xyz/assets/clip_image306.jpg)

 

#### 数组的应用题

 

##### 最值问题

【1】实现一个功能：给定一个数组int[] arr = {12,3,7,4,8,125,9,45}; ，求出数组中最大的数。 

思路图：

![img](https://image.201068.xyz/assets/clip_image308.jpg)

```
1.  public class TestArray04{
2.      public static void main(String[] args){
3.                  //实现一个功能：给定一个数组int[] arr = {12,3,7,4,8,125,9,45}; ，求出数组中最大的数。
4.                  //1.给定一个数组
5.                  int[] arr = {12,3,7,4,8,125,9,45,666,36};
6.                  
7.                  //2.求出数组中的最大值：
8.                  //先找一个数上擂台，假定认为这个数最大：
9.                  int maxNum = arr[0];
10.                for(int i=0;i<arr.length;i++){
11.                        if(arr[i]>maxNum){
12.                                maxNum = arr[i];
13.                        }
14.                }
15.                System.out.println("当前数组中最大的数为："+maxNum);
16.                
17.        }
18.}
```

【2】将求最大值的方法提取出来： 

```
1.  public class TestArray04{
2.      public static void main(String[] args){
3.                  //实现一个功能：给定一个数组int[] arr = {12,3,7,4,8,125,9,45}; ，求出数组中最大的数。
4.                  //1.给定一个数组
5.                  int[] arr = {12,3,7,4,8,725,9,45,666,36};
6.                  
7.                  //2.求出数组中的最大值：
8.                  //调用方法：
9.                  int num = getMaxNum(arr);
10.                System.out.println("当前数组中最大的数为："+num);
11.        }
12.        
13.        /*
14.        想提取一个方法：求数组中的最大值
15.        求哪个数组中的最大值 ---》不确定因素：哪个数组 (形参)---》返回值：最大值
16.        */
17.        public static int getMaxNum(int[] arr){
18.                //先找一个数上擂台，假定认为这个数最大：
19.                int maxNum = arr[0];
20.                for(int i=0;i<arr.length;i++){
21.                        if(arr[i]>maxNum){
22.                                maxNum = arr[i];
23.                        }
24.                }
25.                return maxNum;
26.                
27.        }
28.}
```

【3】画内存： 

方法的实参传递给形参的时候一定要注意：一切都是值传递： 

如果是基本数据类型，那么传递的就是字面值 

如果是引用数据类型，那么传递的就是地址值 

![img](https://image.201068.xyz/assets/clip_image310.jpg)

 

 

##### 查询问题

【1】查询指定位置的元素

```
1.  public class TestArray05{
2.      public static void main(String[] args){
3.                  //查询指定位置的元素
4.                  //给定一个数组：
5.                  int[] arr = {12,34,56,7,3,10};
6.                  //查找索引为2的位置上对应的元素是什么？
7.                  System.out.println(arr[2]);
8.          }
9.  }
```

上面代码体现了数组的一个优点：

在按照位置查询的时候，直接一步到位，效率非常高

 

【2】查询指定元素的位置--》找出元素对应的索引 

 

 

```
1.  public class TestArray06{
2.      public static void main(String[] args){
3.                  //查询指定元素的位置--》找出元素对应的索引 
4.                  //给定一个数组：
5.                  int[] arr = {12,34,56,7,3,56};
6.                  //           0  1  2  3 4  5
7.                  
8.                  //功能：查询元素888对应的索引：
9.                  int index = -1; //这个初始值只要不是数组的索引即可
10.                for(int i=0;i<arr.length;i++){
11.                        if(arr[i]==12){
12.                                index = i;//只要找到了元素，那么index就变成为i
13.                                break;//只要找到这个元素，循环就停止
14.                        }
15.                }
16.                if(index!=-1){
17.                        System.out.println("元素对应的索引："+index);
18.                }else{//index==-1
19.                        System.out.println("查无次数！");
20.                }
21.        }
22.}
```

【3】将查指定元素对应的索引的功能提取为方法： 

```
1.  public class TestArray06{
2.      public static void main(String[] args){
3.                  //查询指定元素的位置--》找出元素对应的索引 
4.                  //给定一个数组：
5.                  int[] arr = {12,34,56,7,3,56};
6.                  //           0  1  2  3 4  5
7.                  
8.                  //功能：查询元素888对应的索引：
9.                  //调用方法：
10.                int index = getIndex(arr,999);
11.                //后续对index的值进行判断：
12.                if(index!=-1){
13.                        System.out.println("元素对应的索引："+index);
14.                }else{//index==-1
15.                        System.out.println("查无次数！");
16.                }
17.        }
18.        
19.        /*
20.        定义一个方法：查询数组中指定的元素对应的索引：
21.        不确定因素：哪个数组，哪个指定元素  （形参）
22.        返回值：索引
23.        
24.        */
25.        public static int getIndex(int[] arr,int ele){
26.                int index = -1; //这个初始值只要不是数组的索引即可
27.                for(int i=0;i<arr.length;i++){
28.                        if(arr[i]==ele){
29.                                index = i;//只要找到了元素，那么index就变成为i
30.                                break;//只要找到这个元素，循环就停止
31.                        }
32.                }
33.                return index;
34.        }
35.}
```

##### 添加元素

【1】实现一个功能：

添加逻辑：

![img](https://image.201068.xyz/assets/clip_image312.jpg)

 

```
1.  public class TestArray07{
2.      public static void main(String[] args){
3.                  //功能：给定一个数组,在数组下标为2的位置上添加一个元素91
4.                  
5.                  //1.给定一个数组：
6.                  int[] arr = {12,34,56,7,3,10,55,66,77,88,999,89};
7.                  //           0  1   2 3 4 5
8.                  //2.输出增加元素前的数组：
9.                  System.out.print("增加元素前的数组：");
10.                for(int i=0;i<arr.length;i++){
11.                        if(i!=arr.length-1){
12.                                System.out.print(arr[i]+",");
13.                        }else{//i==arr.length-1 最后一个元素不用加,
14.                                System.out.print(arr[i]);
15.                        }
16.                }
17.                
18.                //3.增加元素
19.                /*
20.                arr[5] = arr[4];
21.                arr[4] = arr[3];
22.                arr[3] = arr[2];
23.                */
24.                int index = 1;//在这个指定位置添加 元素
25.                for(int i=arr.length-1;i>=(index+1);i--){
26.                        arr[i] = arr[i-1];
27.                }
28.                arr[index] = 666;
29.                
30.                
31.                //4.输出增加元素后的数组：
32.                System.out.print("\n增加元素后的数组：");
33.                for(int i=0;i<arr.length;i++){
34.                        if(i!=arr.length-1){
35.                                System.out.print(arr[i]+",");
36.                        }else{//i==arr.length-1 最后一个元素不用加,
37.                                System.out.print(arr[i]);
38.                        }
39.                }
40.                
41.        } 
42.}
```

【2】将添加功能提取为一个 方法： 

```
1.  import java.util.Scanner;
2.  public class TestArray07{
3.      public static void main(String[] args){
4.                  //功能：给定一个数组,在数组下标为2的位置上添加一个元素91
5.                  
6.                  //1.给定一个数组：
7.                  int[] arr = {12,34,56,7,3,10,55,66,77,88,999,89};
8.                  //           0  1   2 3 4 5
9.                  //2.输出增加元素前的数组：
10.                /*
11.                System.out.print("增加元素前的数组：");
12.                for(int i=0;i<arr.length;i++){
13.                        if(i!=arr.length-1){
14.                                System.out.print(arr[i]+",");
15.                        }else{//i==arr.length-1 最后一个元素不用加,
16.                                System.out.print(arr[i]);
17.                        }
18.                }
19.                */
20.                
21.                //从键盘接收数据：
22.                Scanner sc = new Scanner(System.in);
23.                System.out.println("请录入你要添加元素的指定下标：");
24.                int index = sc.nextInt();
25.                System.out.println("请录入你要添加的元素：");
26.                int ele = sc.nextInt();
27.                
28.                //3.增加元素
29.                //调用方法：
30.                insertEle(arr,index,ele);
31.                
32.                
33.                
34.                //4.输出增加元素后的数组：
35.                System.out.print("\n增加元素后的数组：");
36.                for(int i=0;i<arr.length;i++){
37.                        if(i!=arr.length-1){
38.                                System.out.print(arr[i]+",");
39.                        }else{//i==arr.length-1 最后一个元素不用加,
40.                                System.out.print(arr[i]);
41.                        }
42.                }
43.                
44.        } 
45.        
46.        
47.        /*
48.        提取一个添加元素的方法：
49.        在数组的指定位置上添加一个指定的元素。
50.        在哪个数组的哪个位置添加哪个元素！
51.        不确定因素：形参：哪个数组，哪个位置，哪个元素
52.        返回值：无
53.        
54.        */
55.        public static void insertEle(int[] arr,int index,int ele){
56.                for(int i=arr.length-1;i>=(index+1);i--){
57.                        arr[i] = arr[i-1];
58.                }
59.                arr[index] = ele;
60.        }
61.}
```

##### 删除元素

【1】实现一个功能：删除指定位置上的元素

逻辑：

![img](https://image.201068.xyz/assets/clip_image314.jpg)

```
1.  import java.util.Arrays;
2.  public class TestArray08{
3.      public static void main(String[] args){
4.                  //功能：给定一个数组,删除下标为2元素
5.                  
6.                  //1.给定一个数组：
7.                  int[] arr = {12,34,56,7,3,10,34,45,56,7,666};
8.                  //           0  1   2 3 4 5
9.                  //2.输出删除前的数组：
10.                System.out.println("删除元素前的数组："+Arrays.toString(arr));
11.                
12.                //3.删除
13.                /*
14.                arr[2] = arr[3];
15.                arr[3] = arr[4];
16.                arr[4] = arr[5];
17.                */
18.                int index = 0;
19.                for(int i=index;i<=arr.length-2;i++){
20.                        arr[i] = arr[i+1];
21.                }
22.                arr[arr.length-1] = 0;
23.                
24.                //4.输出删除后的数组：
25.                System.out.println("删除元素后的数组："+Arrays.toString(arr));
26.        }
27.}
```

 

【2】实现一个功能：删除指定元素 

```
1.  import java.util.Arrays;
2.  public class TestArray09{
3.      public static void main(String[] args){
4.                  //功能：给定一个数组,删除元素3：
5.                  
6.                  //1.给定一个数组：
7.                  int[] arr = {12,34,56,7,3,10,34,45,56,7,666};
8.                   
9.                  //2.输出删除前的数组：
10.                System.out.println("删除元素前的数组："+Arrays.toString(arr));
11.                
12.                
13.                //找到要删除的元素对应的索引即可：
14.                int index = -1 ;
15.                for(int i=0;i<arr.length;i++){
16.                        if(arr[i]==1200){
17.                                index = i;
18.                                break;
19.                        }
20.                }
21.                
22.                //3.删除
23.                
24.                if(index!=-1){
25.                        for(int i=index;i<=arr.length-2;i++){
26.                                arr[i] = arr[i+1];
27.                        }
28.                        arr[arr.length-1] = 0;
29.                }else{//index==-1
30.                        System.out.println("根本没有你要删除的元素！");
31.                }
32.                
33.                
34.                //4.输出删除后的数组：
35.                System.out.println("删除元素后的数组："+Arrays.toString(arr));
36.        }
37.}
```

 

#### 详述main方法

【1】main方法：程序的入口，在同一个类中，如果有多个方法，那么虚拟机就会识别main方法，从这个方法作为程序的入口 

【2】main方法格式严格要求： 

public static void main(String[] args){} 

 

public static --->修饰符 ，暂时用这个 -->面向对象一章 

void --->代表方法没有返回值 对应的类型void 

main --->见名知意名字

String[] args  --->形参  ---》不确定因素 

 

【3】问题：程序中是否可以有其他的方法也叫main方法？ 

可以，构成了方法的重载。 

```
1.  public class TestArray10{
2.      public static void main(String[] args){
3.                  
4.          }
5.          public static void main(String str){
6.                  
7.          }
8.  }
```

【4】形参为String[] 那么实参到底是什么？ 

```
1.  public class TestArray10{
2.      public static void main(String[] args){
3.                  //从侧面验证：
4.                  //int[] arr1; //如果对数组只声明，没有后续操作，那么相当于 白定义了。
5.                  //int[] arr2 = null; 
6.                  //System.out.println(arr2.length);//Exception in thread "main" java.lang.NullPointerException
7.                  //int[] arr3 = new int[0];
8.                  //System.out.println(arr3.length);
9.                  //int[] arr4 = new int[4];
10.                //System.out.println(arr4.length);
11.                
12.                //System.out.println(args.length);//0
13.                //从这个结果证明，参数是String[],实参是  new String[0] 
14.                //默认情况下，虚拟机在调用main方法的时候就是传入了一个长度为0的数组
15.                
16.                System.out.println(args.length);
17.                for(String str:args){
18.                        System.out.println(str);
19.                }
20.        }
21.}
```

手动传入实参：

有特殊符号的时候可以加上“”

![img](https://image.201068.xyz/assets/clip_image316.jpg)

 

没有特殊符号用空格隔开即可：

![img](https://image.201068.xyz/assets/clip_image318.jpg)

 

#### 可变参数

```
1.  public class TestArray12{
2.          /*
3.          1.可变参数：作用提供了一个方法，参数的个数是可变的 ,解决了部分方法的重载问题
4.          int...num
5.          double...num
6.          boolean...num
7.          
8.          
9.          2.可变参数在JDK1.5之后加入的新特性
10.        3.方法的内部对可变参数的处理跟数组是一样
11.        4.可变参数和其他数据一起作为形参的时候，可变参数一定要放在最后
12.        5.我们自己在写代码的时候，建议不要使用可变参数。
13.        */
14.    public static void main(String[] args){
15.                //method01(10);
16.                //method01();
17.                //method01(20,30,40);
18.                method01(30,40,50,60,70);
19.                //method01(new int[]{11,22,33,44});
20.        }
21.        public static void method01(int num2,int...num){
22.                System.out.println("-----1");
23.                for(int i:num){
24.                        System.out.print(i+"\t");
25.                }
26.                System.out.println();
27.                
28.                System.out.println(num2);
29.        }
30.}
```

 

 

#### Arrays工具类

为了方便我们对数组进行操作，系统提供一个类Arrays，我们将它当做工具类来使用。 

```
1.  import java.util.Arrays;
2.  public class TestArray13{
3.          public static void main(String[] args){
4.                  //给定一个数组：
5.                  int[] arr = {1,3,7,2,4,8};
6.                  //toString:对数组进行遍历查看的，返回的是一个字符串，这个字符串比较好看
7.                  System.out.println(Arrays.toString(arr));
8.                  
9.                  //binarySearch:二分法查找：找出指定数组中的指定元素对应的索引：
10.                //这个方法的使用前提：一定要查看的是一个有序的数组：
11.                //sort：排序 -->升序
12.                Arrays.sort(arr);
13.                System.out.println(Arrays.toString(arr));
14.                System.out.println(Arrays.binarySearch(arr,4));
15.                
16.                int[] arr2 = {1,3,7,2,4,8};
17.                //copyOf:完成数组的复制：
18.                int[] newArr = Arrays.copyOf(arr2,4);
19.                System.out.println(Arrays.toString(newArr));
20.                
21.                //copyOfRange:区间复制：
22.                int[] newArr2 = Arrays.copyOfRange(arr2,1,4);//[1,4)-->1,2,3位置
23.                System.out.println(Arrays.toString(newArr2));
24.                
25.                //equals:比较两个数组的值是否一样：
26.                int[] arr3 = {1,3,7,2,4,8};
27.                int[] arr4 = {1,3,7,2,4,8};
28.                System.out.println(Arrays.equals(arr3,arr4));//true
29.                System.out.println(arr3==arr4);//false ==比较左右两侧的值是否相等，比较的是左右的地址值，返回结果一定是false
30.                
31.                //fill：数组的填充：
32.                int[] arr5 = {1,3,7,2,4,8};
33.                Arrays.fill(arr5,10);
34.                System.out.println(Arrays.toString(arr5));
35.        }
36.}
```

 

 

#### 数组的复制操作

![img](https://image.201068.xyz/assets/clip_image320.jpg)

 

![img](https://image.201068.xyz/assets/clip_image322.jpg)

 

原理：

![img](https://image.201068.xyz/assets/clip_image324.jpg)

代码：

```
1.  import java.util.Arrays;
2.  public class TestArray14{
3.          public static void main(String[] args){
4.                  //给一个源数组：
5.                  int[] srcArr = {11,22,33,44,55,66,77,88};
6.                  //给一个目标数组：
7.                  int[] destArr = new int[10];
8.                  
9.                  //复制：
10.                System.arraycopy(srcArr,1,destArr,3,3);
11.                //遍历查看目标数组：
12.                System.out.println(Arrays.toString(destArr));
13.        }
14.        
15.}
```

结果：

![img](https://image.201068.xyz/assets/clip_image326.jpg)

#### 二维数组

【1】引入：本质上全部都是一维数组：

![img](https://image.201068.xyz/assets/clip_image328.jpg)

 

【2】基本代码： 

```
1.  public class TestArray15{
2.          public static void main(String[] args){
3.                  //定义一个二维数组：
4.                  int[][] arr = new int[3][];//本质上定义了一个一维数组，长度为3
5.                  
6.                  int[] a1 = {1,2,3};
7.                  arr[0] = a1;
8.                  
9.                  arr[1] = new int[]{4,5,6,7};
10.                
11.                arr[2] = new int[]{9,10};
12. 
13.        }
14.}
```

 

对应内存：

![img](https://image.201068.xyz/assets/clip_image330.jpg)

 

【3】四种遍历方式： 

```
1.  public class TestArray15{
2.          public static void main(String[] args){
3.                  //定义一个二维数组：
4.                  int[][] arr = new int[3][];//本质上定义了一个一维数组，长度为3
5.                  
6.                  int[] a1 = {1,2,3};
7.                  arr[0] = a1;
8.                  
9.                  arr[1] = new int[]{4,5,6,7};
10.                
11.                arr[2] = new int[]{9,10};
12.                
13.                //读取6这个元素：
14.                //System.out.println(arr[1][2]);
15.                
16.                //对二维数组遍历：
17.                //方式1：外层普通for循环+内层普通for循环：
18.                for(int i=0;i<arr.length;i++){
19.                        for(int j=0;j<arr[i].length;j++){
20.                                System.out.print(arr[i][j]+"\t");
21.                        }
22.                        System.out.println();
23.                }
24.                
25.                //方式2：外层普通for循环+内层增强for循环：
26.                for(int i=0;i<arr.length;i++){
27.                        for(int num:arr[i]){
28.                                System.out.print(num+"\t");
29.                        }
30.                        System.out.println();
31.                }
32.                
33.                //方式3：外层增强for循环+内层增强for循环：
34.                for(int[] a:arr){
35.                        for(int num:a){
36.                                System.out.print(num+"\t");
37.                        }
38.                        System.out.println();
39.                }
40.                
41.                //方式4：外层增强for循环+内层普通for循环：
42.                for(int[] a:arr){
43.                        for(int i=0;i<a.length;i++){
44.                                System.out.print(a[i]+"\t");
45.                        }
46.                        System.out.println();
47.                }
48. 
49.        }
50.}
```

 

#### 二维数组的初始化方式

数组的初始化方式总共有三种：静态初始化、动态初始化、默认初始化。 

 

- 静态初始化     

除了用new关键字来产生数组以外，还可以直接在定义数组的同时就为数组元素分配空间并赋值。 

 

eg:

int[][] arr = {{1,2},{4,5,6},{4,5,6,7,8,9,9}}; 

int[][] arr =new int[][] {{1,2},{4,5,6},{4,5,6,7,8,9,9}}; 

- 动态初始化     

数组定义与为数组元素分配空间并赋值的操作分开进行。

 

eg:

int[][] arr = new int[3][]; //本质上定义了一维数组长度为3，每个“格子”中放入的是一个数组 

arr[0] = new int[]{1,2}; 

arr[1] = new int[]{3,4,5,6}; 

arr[2] = new int[]{34,45,56}; 

 

eg:

int[][] arr = new int[3][2]; 

  public class  TestArray16{         public static void main(String[] args){             int[][] arr = new int[3][2];             //本质上：定义一维数组，长度为3，每个数组“格子”中，有一个默认的长度为2的数组：                arr[1] = new int[]{1,2,3,4};                //数组遍历：             for(int[] a:arr){                 for(int  num:a){                             System.out.print(num+"\t");                 }                   System.out.println();             }            }   }   

- 默认初始化     

数组是引用类型，它的元素相当于类的实例变量，因此数组一经分配空间，其中的每个元素也被按照实例变量同样的方式被隐式初始化。 

 

 

 

# 第7章_IDEA的使用

#### IDEA

##### IDE

集成开发环境（IDE，Integrated Development Environment ）是用于提供程序开发环境的应用程序，一般包括代码编辑器、编译器、调试器和图形用户界面等工具。集成了代码编写功能、分析功能、编译功能、调试功能等一体化的开发软件服务套。所有具备这一特性的软件或者软件套（组）都可以叫集成开发环境。如微软的Visual Studio系列，Borland的C++ Builder、Delphi系列等。该程序可以独立运行，也可以和其它程序并用。IDE多被用于开发HTML应用软件。例如，许多人在设计网站时使用IDE（如HomeSite、DreamWeaver等），因为很多项任务会自动生成。编程开发软件将编辑、编译、调试等功能集成在一个桌面环境中,这样就大大方便了用户。 

 

❀优点

节省时间和精力。IDE的目的就是要让开发更加快捷方便，通过提供工具和各种性能来帮助开发者组织资源，减少失误，提供捷径。 

建立统一标准。当一组程序员使用同一个开发环境时，就建立了统一的工作标准，当IDE提供预设的模板，或者不同团队分享代码库时，这一效果就更加明显了。 

管理开发工作。首先，IDE提供文档工具，可以自动输入开发者评论，或者迫使开发者在不同区域编写评论。其次，IDE可以展示资源，更便于发现应用所处位置，无需在文件系统里面艰难的搜索。 

❀缺点

学习曲线问题。IDE基本上是比较复杂的工具，为了更好的熟练使用，需要一定的时间和耐心。 

初学者的困难。对初学者来说，使用IDE来学习开发有相当的难度，不适合学习一种新语言时使用。 

无法修复坏代码或设计。开发者不能完全依赖工具的便捷，还是必须保持专业水准和熟练度，开发的成果好坏主要还是看开发员的技术。

 

##### JetBrains公司介绍

【1】IntelliJ IDEA就是Java的IDE。 

【2】市场占有率竹节攀升，超过了Eclipse。 

【3】JetBrains公司介绍：

JetBrains是一家捷克的软件开发公司，该公司位于捷克的布拉格，并在俄罗斯的圣彼得堡及美国麻州波士顿都设有办公室，该公司最为人所熟知的产品是Java编程语言开发撰写时所用的[集成开发环境](https://baike.baidu.com/item/集成开发环境/298524)：IntelliJ IDEA。公司旗下还有其它产品，比如： 

➢WebStorm: 用于开发JavaScript、HTML5、 CS3等前端技术; 

➢PyCharm: 用于开发python（python语言热度排行榜排名第一，在人工智能大数据领域应用）

➢PhpStorm: 用于开发PHP 

➢RubyMine: 用于开发Ruby/Rails 

➢AppCode: 用于开发Objective - C/Swift,替换xcode的 

➢CLion: 用于开发C/C++ 

➢DataGrip: 用于开发数据库和SQL 

➢Rider: 用于开发.NET 

➢GoLand: 用于开发Go（区块链主流开发语言就是Go语言） 

【4】官网：https://www.jetbrains.com/ 

![img](https://image.201068.xyz/assets/clip_image332.jpg)

 

##### IntelliJ_IDEA介绍

【1】IDEA 全称IntelliJ IDEA，是用于java语言开发的集成环境IDE(Integrated Development Environment)，也可用于其他语言。 

IntelliJ在业界被公认为最好的java开发工具之一，尤其在智能代码助手、代码自动提示、重构、J2EE支持、Ant、JUnit、CVS整合、代码审查、 创新的GUI设计等方面的功能可以说是超常的。

 

IDEA是JetBrains公司的产品，这家公司总部位于捷克共和国的首都布拉格，开发人员以严谨著称的东欧程序员为主。

 

【2】IDEA的支持： 

![img](https://image.201068.xyz/assets/clip_image334.jpg)

![img](https://image.201068.xyz/assets/clip_image336.jpg)

【3】IDEA的优势（相对于Eclipse）

①强大的整合能力。比如: Git、 Maven、 Spring 等 

②提示功能的快速、便捷

③提示功能的范围广

④好用的快捷键和代码模板

⑤精准搜索

 

 

##### IntelliJ_IDEA的下载和安装的准备

【1】官网：https://www.jetbrains.com/idea/download/#section=windows

![img](https://image.201068.xyz/assets/clip_image338.jpg)

【2】安装的准备： 

（1）硬件环境： 

内存8G以上 

CPU i5以上 

安装在固态硬盘下

（2）软件环境： 

需要安装JDK 

##### IDEA的卸载

对于免安装的idea：

（1）删除安装文件 

（2）到用户下将idea的缓存，配置的目录删除掉即可 

 

安装idea: 

(1)可以用控制面板--》程序

##### IDEA的安装和破解

【1】将安装包进行解压--》选择固态盘符 

【2】发送到桌面快捷方式，生成一个快捷方式 

【3】打开： 

![img](https://image.201068.xyz/assets/clip_image340.jpg)

选择主题：

![img](https://image.201068.xyz/assets/clip_image342.jpg)

![img](https://image.201068.xyz/assets/clip_image344.jpg)

![img](https://image.201068.xyz/assets/clip_image346.jpg)

先进入再说，免费试用：

 

![img](https://image.201068.xyz/assets/clip_image348.jpg)

创建一个项目：

![img](https://image.201068.xyz/assets/clip_image350.jpg)

 

 

选择JDK： 

![img](https://image.201068.xyz/assets/clip_image352.jpg)

 

![img](https://image.201068.xyz/assets/clip_image354.jpg)

![img](https://image.201068.xyz/assets/clip_image356.jpg)

 

![img](https://image.201068.xyz/assets/clip_image358.jpg)

 

![img](https://image.201068.xyz/assets/clip_image360.jpg)

![img](https://image.201068.xyz/assets/clip_image362.jpg)

 

找到jetbrains-agent.jar 文件，然后放入合适的文件夹内（我一般直接放入idea的安装位置了，你随意，不建议有中文路径） 

点击IDEA的菜单，找到： Help---》Edit Custom VM Options 

![img](https://image.201068.xyz/assets/clip_image364.jpg)

 

 

然后在文件中最后一行填入： 

-javaagent:D:\soft_setup\IDEA\ideaIU-2019.2.3.win\jetbrains-agent.jar

注意这个jetbrains-agent.jar的路径要是你自己的真实的路径。

![img](https://image.201068.xyz/assets/clip_image366.gif)

关闭IDEA 

再次打开IDEA，点击菜单 ，Help---》Register: 

![img](https://image.201068.xyz/assets/clip_image368.jpg)

 

![img](https://image.201068.xyz/assets/clip_image370.gif)

 

 

关闭IDEA 

重启IDEA 

看到带Licenseed to..字样的 证明激活成功！ 

 

##### IDEA页面展示

【1】项目下内容：

➢工程下的src类似于Eclipse下的src目录，用于存放代码。。

➢工程下的.idea 和TestProject.iml文件都是IDEA工程特有的。类似于Eclipse 工程下的settings、.classpath、.project 等。 

【2】配置： 

![img](https://image.201068.xyz/assets/clip_image372.jpg)

 

![img](https://image.201068.xyz/assets/clip_image374.jpg)

 

 

##### Module的概念和使用

【1】在Eclipse中我们有Workspace (工作空间)和Project (工程)的概念，在IDEA中只有Project (工程)和Module (模块)的概念。 

这里的对应关系为: 

| IDEA官网说明:    An Eclipse workspace  is similar to a project in IntelliJ IDEA   An Eclipse project  maps to a module in IntelliJ IDEA |
| ------------------------------------------------------------ |
| 翻译:   Eclipse中  workspace 相当于 IDEA中的Project   Eclipse中   Project   相当于 IDEA中的Module |

在IntelliJ IDEA中Project(工程) 是最顶级的级别，次级别是Module(模块)。 

一个Project下可以有多个Module。 

 

【2】从Eclipse 转过来的人总是下意识地要在同一个窗口管理n个项目，这在Intellij IDEA是无法做到的。Intellij IDEA提供的解决方案是打开多个项目实例，即打开多个项目窗口。即:一个Project 打开一个Window窗口。 

 

【3】IDEA这样设置的原因： 

目前主流的大型项目都是分布式部署的，结构都是类似这种多Module的。 

这类项目一般是这样划分的，比如: 积分模块、任务模块、活动模块等等，模块之间彼此可以相互依赖。这些Module之间都是处于同一个项目业务下的模块，彼此之间是有不可分割的业务关系的。

![img](https://image.201068.xyz/assets/clip_image376.jpg)

 

 

 

 

 

 

【4】out目录的说明：里面存放的是编译后的字节码文件 

![img](https://image.201068.xyz/assets/clip_image378.jpg)

 

【5】删除模块： 

![img](https://image.201068.xyz/assets/clip_image380.jpg)

![img](https://image.201068.xyz/assets/clip_image382.jpg)

 

 

 

 

 

 

 

##### IDEA的常用设置

【1】进入设置：

![img](https://image.201068.xyz/assets/clip_image384.jpg)

![img](https://image.201068.xyz/assets/clip_image386.jpg)

![img](https://image.201068.xyz/assets/clip_image388.jpg)

【2】设置主题： 

![img](https://image.201068.xyz/assets/clip_image390.jpg)

【3】编辑区的字体变大或者变小： 

![img](https://image.201068.xyz/assets/clip_image392.jpg)

【4】鼠标悬浮在代码上有提示： 

![img](https://image.201068.xyz/assets/clip_image394.jpg)

 

【5】自动导包和优化多余的包： 

手动导包：快捷键：alt+enter 

自动导包和优化多余的包：

![img](https://image.201068.xyz/assets/clip_image396.jpg)

 

 

【6】同一个包下的类，超过指定个数的时候，导包合并为* 

![img](https://image.201068.xyz/assets/clip_image398.jpg)

![img](https://image.201068.xyz/assets/clip_image400.jpg)

【7】显示行号 ，  方法和方法间的分隔符： 

![img](https://image.201068.xyz/assets/clip_image402.jpg)

【8】忽略大小写，进行提示： 

![img](https://image.201068.xyz/assets/clip_image404.jpg)

【9】多个类不隐藏，多行显示： 

![img](https://image.201068.xyz/assets/clip_image406.jpg)

【10】设置默认的字体，字体大小，字体行间距：(编辑区和控制台都会变化) 

![img](https://image.201068.xyz/assets/clip_image408.jpg)

【11】修改代码中注释的字体颜色： 

![img](https://image.201068.xyz/assets/clip_image410.jpg)

 

 

 

【12】修改类头的文档注释信息：---》注意：对新建的类才有效 

/**

\* @Auther: zhaoss 

\* @Date: ${DATE} - ${MONTH} - ${DAY} - ${TIME} 

\* @Description: ${PACKAGE_NAME} 

\* @version: 1.0 

*/

![img](https://image.201068.xyz/assets/clip_image412.jpg)

 

【13】设置项目文件编码： 

![img](https://image.201068.xyz/assets/clip_image414.jpg)

文件右下角可以调节编码格式：

![img](https://image.201068.xyz/assets/clip_image416.jpg)

【14】自动编译： 

![img](https://image.201068.xyz/assets/clip_image418.jpg)

【15】省电模式： 

![img](https://image.201068.xyz/assets/clip_image420.jpg)

 

【16】代码显示结构： 

![img](https://image.201068.xyz/assets/clip_image422.jpg)

【17】导入jar包： 

![img](https://image.201068.xyz/assets/clip_image424.jpg)

【18】生成序列化版本号： 

![img](https://image.201068.xyz/assets/clip_image426.jpg)

![img](https://image.201068.xyz/assets/clip_image428.jpg)

 

 

 

##### IDEA的常用快捷键

【1】创建内容：alt+insert 

【2】main方法：psvm 

【3】输出语句：sout
 【4】复制行：ctrl+d 

【5】删除行：ctrl+y 

![img](https://image.201068.xyz/assets/clip_image430.jpg)

 

【6】代码向上/下移动：Ctrl + Shift + Up / Down 

【7】搜索类：  ctrl+n 

【8】生成代码  ：alt + Insert（如构造函数等，getter,setter,hashCode,equals,toString）

【9】百能快捷键 : alt + Enter （导包，生成变量等）

【10】单行注释或多行注释 ： Ctrl + / 或 Ctrl + Shift + / 

【11】重命名 shift+f6 

【12】for循环  直接 ：fori  回车即可 

【13】代码块包围：try-catch,if,while等  ctrl+alt+t 

【14】 代码自动补全提示: 

![img](https://image.201068.xyz/assets/clip_image432.jpg)

【15】 idea代码字体大小放大和缩小的快捷键 

![img](https://image.201068.xyz/assets/clip_image434.jpg)

【16】代码一层一层调用的快捷键： 

点进源码：ctrl+鼠标悬浮在代码上+点进去即可： 

![img](https://image.201068.xyz/assets/clip_image436.jpg)

【17】显示代码结构  : alt + 7 

【18】显示导航栏： alt +1 

【19】撤回：ctrl+z 

【20】REDO操作： 

如果跟搜狗输入法的快捷键冲突，可以选择将搜狗的快捷键取消。

![img](https://image.201068.xyz/assets/clip_image438.jpg)

 

【21】缩进：tab  取消缩进： shift+tab 

 

 

 

 

##### 模板的使用

 

###### 代码模板是什么

它的原理就是配置一些常用代码字母缩写，在输入简写时可以出现你预定义的固定模式的代码，使得开发效率大大提高，同时也可以增加个性化。最简单的例子就是在Java中输入sout会出现System.out.println();

 

（一）所处位置：

（1）Live Templates 

（2）Postfix Completion 

![img](https://image.201068.xyz/assets/clip_image440.jpg)

（二）区别：

【1】 

Live Templates中可以做用户的个性化定制。

Postfix Completion中只能用，不能修改。

【2】使用方式不同 

![img](https://image.201068.xyz/assets/clip_image442.jpg)

![img](https://image.201068.xyz/assets/clip_image444.jpg)

 

 

 

###### 修改现有模板

【1】案例1：改main方法： psvm 

![img](https://image.201068.xyz/assets/clip_image446.jpg)

![img](https://image.201068.xyz/assets/clip_image448.jpg)

 

【2】案例2：修饰属性的修饰符： 

![img](https://image.201068.xyz/assets/clip_image450.jpg)

 

![img](https://image.201068.xyz/assets/clip_image452.jpg)

 

###### 常用的代码模板

【1】模板1： main方法： 

main 或者 psvm 

 

【2】模板2：输出语句： 

sout  或者  .sout 

一些变型：
 soutp:打印方法的形参 

soutm:打印方法的名字 

soutv:打印变量 

 

【3】模板3： 循环 

普通for循环：  fori（正向）  或者  .fori （正向）  . forr(逆向) 

增强for循环：  iter  或者  .for 

（可以用于数组的遍历，集合的遍历）

 

【4】模板4： 条件判断 

ifn 或者  .null ：判断是否为null  （if null） 

inn 或者 .nn ：判断不等于null  (if not null) 

 

【5】模板5： 属性修饰符： 

prsf : private static final 

psf :public static final 

 

 

 

###### 自定义模板

【1】测试方法：

![img](https://image.201068.xyz/assets/clip_image454.jpg)

 

【2】常用属性：($$中的内容其实就是在定义光标的位置，光标可以切换，用回车切换) 

![img](https://image.201068.xyz/assets/clip_image456.jpg)

 

【3】方法注释模板： 

/**

\* 功能描述: 

\* @param: $param$ 

\* @return: $return$ 

\* @auther: $user$ 

\* @date: $date$ $time$ 

*/  

 

![img](https://image.201068.xyz/assets/clip_image458.jpg)

 

##### IDEA中的断点调试

 

###### 常用断点调试快捷键

调试在开发中大量应用： 

【1】Debug的优化设置：更加节省内存空间： 

设置Debug连接方式，默认是Socket。 Shared memory是Windows 特有的一个属性，一般在Windows系统下建议使用此设置， 

内存占用相对较少。

![img](https://image.201068.xyz/assets/clip_image460.jpg)

 

【2】常用断点调试快捷键： 

 

![img](https://image.201068.xyz/assets/clip_image462.jpg)一步一步的向下运行代码，不会走入任何方法中。 

![img](https://image.201068.xyz/assets/clip_image464.jpg)一步一步的向下运行代码，不会走入系统类库的方法中，但是会走入自定义的方法中。 

![img](https://image.201068.xyz/assets/clip_image466.jpg)一步一步的向下运行代码，会走入系统类库的方法中，也会走入自定义的方法中。 

![img](https://image.201068.xyz/assets/clip_image468.jpg)跳出方法 

![img](https://image.201068.xyz/assets/clip_image470.jpg)结束程序 

![img](https://image.201068.xyz/assets/clip_image472.jpg)进入到下一个断点，如果没有下一个断点了，就直接运行到程序结束。 

![img](https://image.201068.xyz/assets/clip_image474.jpg) 在当前次取消未执行的断点。 

 

 

###### 条件判断，查看表达式的值

 

【1】条件判断： 

说明: 

调试的时候，在循环里增加条件判断，可以极大的提高效率，心情也能惧悦。 

具体操作: 

在断点处右击调出条件断点。可以在满足某个条件下，实施断点。 

![img](https://image.201068.xyz/assets/clip_image476.jpg)

 

【2】查看表达式的值： 

选择行，alt+f8。

![img](https://image.201068.xyz/assets/clip_image478.jpg)

 

# 第8章_面向对象

 

#### 面向过程和面向对象的区别

面向过程：当事件比较简单的时候，利用面向过程，注重的是事件的具体的步骤/过程，注重的是过程中的具体的行为，以函数为最小单位，考虑怎么做。 

面向对象：注重找“参与者”,将功能封装进对象，强调具备了功能的对象，以类/对象为最小单位，考虑谁来做。

案例： 

人把大象装进冰箱： 

面向过程： 

函数1：打开冰箱(){人站在冰箱前，打开冰箱，冰箱卡到30度角的时候，冰箱的灯打开了.........} 

函数2：储存大象(){大象先迈左腿，再迈右退，考虑冰箱能不能装下......} 

函数3：关闭冰箱(){人站在冰箱前，关闭冰箱，冰箱开到30度角的时候，冰箱的灯关闭了..........} 

 

面向对象： 

人{ 

  打开(冰箱){ 

     冰箱.打开(); 

  } 

 

  存储(大象){ 

​    大象.进入(); 

    } 

 

 

 关闭(冰箱){ 

      冰箱.关闭(); 

  } 

 

 

}

 

 

冰箱{ 

 

  打开（）{ 1.2.3.} 

 关闭（）{} 

}

 

 

柜子{ 

 

 

}

 

 

大象{ 

  进入(冰箱){ 

 

  } 

 

}

 

 

面向过程 ---> 面向对象 , 其实就是由执行者 ---> 指挥者的 一个过渡

 

面向过程：编年体
 面向对象：纪传体 

 

二者相辅相成,并不是对立的。解决复杂问题,通过面向对象方式便于我们从宏观上把握事物之间复杂的关系、方便我们分析整个系统;具体到微观操作,仍然使用面向过程方式来处理 

 

#### 类和对象的关系

【1】万事万物皆对象

 

【2】 

对象：具体的事物，具体的实体，具体的实例，模板下具体的产品

类：对对象向上抽取出像的部分，公共的部分，形成类，类是抽象的，是一个模板

 

【3】一般在写代码的时候先写类，然后在根据类创建对应的对象。 

 

#### 面向对象三个阶段

面向对象三个阶段： 

【1】面向对象分析OOA  --  Object Oriented Analysis 

对象：张三，王五，朱六，你，我

抽取出一个类----》人类 

 

类里面有什么：

动词--》动态特性--》方法 

名词--》静态特性--》属性 

【2】面向对象设计OOD  --  Object Oriented Design 

先有类，再有对象：

类：人类： Person 

对象：zhangsan ，lisi，zhuliu

【3】面向对象编程OOP  --  Object Oriented Programming 

 

创建类： 

（1）属性（field 成员变量） 

属性用于定义该类或该类对象包含的数据或者说静态特征。属性作用范围是整个类体。

属性定义格式：

  [修饰符]   方法返回值类型 方法名(形参列表) {         // n条语句    }   

 

（2）方法 

方法用于定义该类或该类实例的行为特征和功能实现。方法是类和对象行为特征的抽象。方法很类似于面向过程中的函数。面向过程中，函数是最基本单位，整个程序由一个个函数调用组成。面向对象中，整个程序的基本单位是类，方法是从属于类和对象的。

方法定义格式：

  [修饰符]   方法返回值类型 方法名(形参列表) {         // n条语句    }   

void代表没有返回值；方法的作用：重用代码，封装功能，便于修改

 

代码：

```
1.  package com.msb;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   * 创建类：人类
6.   */
7.  public class Person {
8.      //名词---》属性---》成员变量---》放在类中方法外（注意：我们只把有需要的内容写到代码里，不相关的东西不要放在代码中）
9.      int age ;//年龄
10.    String name;//姓名
11.    double height;//身高
12.    double weight;//体重
13. 
14.    //动词---》方法
15.    //吃饭
16.    public void eat(){
17.        int num = 10;//局部变量：放在方法中
18.        System.out.println("我喜欢吃饭");
19.    }
20.    //睡觉：
21.    public void sleep(String address){
22.        System.out.println("我在"+address+"睡觉");
23.    }
24.    //自我介绍：
25.    public String introduce(){
26.        return "我的名字是："+name+"，我的年龄是："+age+",我的身高是："+height+",我的体重是："+weight;
27.    }
28.}
29. 
```

#### 创建对象

```
1.  package com.msb;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Test {//测试类
7.   
8.      //这是一个main方法，是程序的入口：
9.      public static void main(String[] args) {
10.        //创建一个人类的具体的对象/实例：
11.        //创建一个对象，对象的名字叫：zs
12.        //Person 属于 引用数据类型
13.        //第一次加载类的时候，会进行类的加载，初始化创建对象的时候，对象的属性没有给赋值，有默认的初始化的值。
14.        Person zs = new Person();
15.        zs.name = "张三";
16.        zs.age = 19;
17.        zs.height = 180.4;
18.        zs.weight = 170.4;
19. 
20.        //再创建一个对象：
21.        //再次创建类的时候，就不会进行类的加载了，类的加载只在第一次需要的时候加载一次
22.        Person ls = new Person();
23.        ls.name = "李四";
24.        ls.age = 18;
25.        ls.height = 170.6;
26.        ls.weight = 160.5;
27. 
28.        //对属性值进行读取：
29.        System.out.println(zs.name);
30.        System.out.println(ls.age);
31. 
32.        //对方法进行操作：
33.        //不同的对象，属性有自己的特有的值，但是方法都是调用类中通用的方法。
34.        //属性：各个对象的属性是独立的，
35.        //方法：各个对象的方法是共享的。
36.        zs.eat();
37.        ls.eat();
38.        zs.sleep("教室");
39.        /*String str = zs.introduce();
40.        System.out.println(str);*/
41.        System.out.println(zs.introduce());
42.    }
43.}
44. 
```

 

 

#### 局部变量和成员变量的区别

**区别1：**代码中位置不同 

​     成员变量：类中方法外定义的变量 

​     局部变量：方法中定义的变量  代码块中定义的变量 

**区别2：**代码的作用范围 

​     成员变量：当前类的很多方法 

​     局部变量：当前一个方法（当前代码块）  

 

**区别3：**是否有默认值 

​     成员变量：有 

​     局部变量：没有 

 

![img](https://image.201068.xyz/assets/clip_image480.jpg)

 

引用数据类型： null 

**区别4：**是否要初始化 

​     成员变量：不需要，不建议初始化，后续使用的时候再赋值即可 

​     局部变量：一定需要，不然直接使用的时候报错 

 

**区别5**：内存中位置不同 

​     成员变量：堆内存 

​     局部变量：栈内存   

**区别6：**作用时间不同 

​     成员变量：当前对象从创建到销毁 

​     局部变量：当前方法从开始执行到执行完毕 

 

 

代码： 

```
1.  package com.msb;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Student {
7.      byte e;
8.      short s;
9.      int c ;//成员变量：在类中方法外
10.    long num2;
11.    float f ;
12.    double d;
13.    char ch;
14.    boolean bo;
15.    String name;
16.    public void study(){
17.        int num = 10 ; //局部变量：在方法中
18.        System.out.println(num);//10
19.        //int num ;重复命名，出错了
20.        {
21.            int a;//局部变量：在代码块中
22.        }
23.        int a;
24.        if(1==3){
25.            int b;
26.        }
27.        System.out.println(c);
28.    }
29.    public void eat(){
30.        System.out.println(c);
31.    }
32. 
33.    //这是一个main方法，是程序的入口：
34.    public static void main(String[] args) {
35.        Student s = new Student();
36.        System.out.println(s.c);
37.        System.out.println(s.bo);
38.        System.out.println(s.ch);
39.        System.out.println(s.d);
40.        System.out.println(s.e);
41.        System.out.println(s.f);
42.        System.out.println(s.name);
43.        System.out.println(s.num2);
44.        System.out.println(s.s);
45. 
46.        s.d = 10.4;
47.    }
48.}
49. 
```

运行结果：

![img](https://image.201068.xyz/assets/clip_image482.jpg)

 

 

#### 构造器

```
1.  package com.msb2;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Person {
7.      //构造器：没有任何参数的构造器我们叫做：空参构造器--》空构造器
8.      public Person(){
9.          /*age = 19;
10.        name = "lili";
11.        height = 169.5;*/
12.    }
13.    //属性：
14.    String name;
15.    int age;
16.    double height;
17.    //方法：
18.    public void eat(){
19.        System.out.println("我喜欢吃饭");
20.    }
21.}
22. 
```

 

 

```
1.  package com.msb2;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Test {
7.      //这是一个main方法，是程序的入口：
8.      public static void main(String[] args) {
9.          //创建一个Person类的具体的对象/实例/实体：
10.        /*
11.        创建对象的过程：
12.        1.第一次遇到Person的时候，进行类的加载（只加载一次）
13.        2.创建对象，为这个对象在堆中开辟空间
14.        3.为对象进行属性的初始化动作
15. 
16.        new关键字实际上是在调用一个方法，这个方法叫构造方法（构造器）
17.        调用构造器的时候，如果你的类中没有写构造器，那么系统会默认给你分配一个构造器，只是我们看不到罢了。
18.        可以自己显式 的将构造器编写出来：
19.        构造器的格式：
20.        [修饰符] 构造器的名字(){
21. 
22.        }
23.        构造器和方法的区别：
24.        1.没有方法的返回值类型
25.        2.方法体内部不能有return语句
26.        3.构造器的名字很特殊，必须跟类名一样
27. 
28.        构造器的作用：不是为了创建对象，因为在调用构造器之前，这个对象就已经创建好了，并且属性有默认的初始化的值。
29.        调用构造器的目的是给属性进行赋值操作的。
30. 
31.        注意：我们一般不会在空构造器中进行初始化操作，因为那样的话每个对象的属性就一样了。
32.        实际上，我们只要保证空构造器的存在就可以了，里面的东西不用写
33.         */
34.        Person p = new Person();
35.        System.out.println(p.age);
36.        System.out.println(p.name);
37.        System.out.println(p.height);
38. 
39.        Person p2 = new Person();
40.        System.out.println(p2.age);
41.        System.out.println(p2.name);
42.        System.out.println(p2.height);
43.    }
44.}
45. 
```

 

 

#### 构造器的重载

```
1.  package com.msb3.msb2;
2.  /**
3.   * @Auther: msb-zhaoss
4.   */
5.  public class Person {
6.   
7.      //属性：
8.      String name;
9.      int age;
10.    double height;
11. 
12.    //空构造器
13.    public Person(){
14. 
15.    }
16.    public Person(String name,int age,double height){
17.        //当形参名字和属性名字重名的时候，会出现就近原则：
18.        //在要表示对象的属性前加上this.来修饰 ，因为this代表的就是你创建的那个对象
19.        this.name = name;
20.        this.age = age;
21.        this.height = height;
22.    }
23.    public Person(String a,int b){
24.        name = a;
25.        age = b;
26.    }
27. 
28.    //方法：
29.    public void eat(){
30.        System.out.println("我喜欢吃饭");
31.    }
32.}
```

 

```
1.  package com.msb3.msb2;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Test {
7.      //这是一个main方法，是程序的入口：
8.      public static void main(String[] args) {
9.          /*
10.        1.一般保证空构造器的存在，空构造器中一般不会进行属性的赋值操作
11.        2.一般我们会重载构造器，在重载的构造器中进行属性赋值操作
12.        3.在重载构造器以后，假如空构造器忘写了，系统也不会给你分配默认的空构造器了，那么你要调用的话就会出错了。
13.        4. 当形参名字和属性名字重名的时候，会出现就近原则：
14.        在要表示对象的属性前加上this.来修饰 ，因为this代表的就是你创建的那个对象
15. 
16.         */
17. 
18.        Person p = new Person();
19.        /*p.age = 19;
20.        p.name = "lili";
21.        p.height = 180.4;*/
22. 
23.        Person p2 = new Person("lili",19,180.4);
24.        System.out.println(p2.age);
25.        System.out.println(p2.height);
26.        System.out.println(p2.name);
27. 
28.    }
29.}
```

 

#### 内存分析

##### 代码1

   public class Person {         int id;         int age;            public static void main(String args[]){             Person p1= new Person();         }   }   

内存分析：

![img](https://image.201068.xyz/assets/clip_image484.jpg)

 

##### 代码2

```
1.  public class Person {
2.          int id;
3.          int age;
4.          String school;
5.          public Person (int a,int b,String c){
6.                  id=a;
7.                  age=b;
8.                  school=c;
9.          }
10.        public static void main(String args[]){
11.                Person p= new Person(1,20, "海淀");
12.        }
13.}
```

![img](https://image.201068.xyz/assets/clip_image486.jpg)

 

##### 代码3

  class Person{         int id;         int age;         String school;         Person (int a,int b,String c){             id=a;             age=b;             school=c;         }            public void setAge(int a){             age=a;         }   }   

 

  public class Test {     public  static void main(String[] args) {              Test t=new Test();              int age=40;              Person tom=new Person(1,20,"海淀");               Person jack=new Person(2,30,"朝阳");               t.change1(age);              t.change2(tom);              t.change3(jack);              System.out.println(age); //40                System.out.println("id:"+jack.id+",age:"+jack.age+",school:"+jack.school);  //id:2,age:66,school:"朝阳"     }     public  void change1(int i){             i=3366;     }        public  void change2(Person p){            p=new Person(3,22,"西城");      }        public  void change3(Person p){         p.setAge(66);     }      }   



 

![img](https://image.201068.xyz/assets/clip_image488.jpg)




this

【1】创建对象的过程：

（1）在第一次遇到一个类的时候，对这个类要进行加载，只加载一次。 

（2）创建对象，在堆中开辟空间 

（3）对对象进行初始化操作，属性赋值都是默认的初始值。 

（4）new关键字调用构造器，执行构造方法，在构造器中对属性重新进行赋值 

this:

![img](https://image.201068.xyz/assets/clip_image490.jpg)

 

 

![img](https://image.201068.xyz/assets/clip_image492.jpg)

从上面的效果能够看到：this指代的就是当前对象： 

 

内存：

![img](https://image.201068.xyz/assets/clip_image494.jpg)

 

 

this关键字 用法： 

（1）this可以修饰属性： 

总结：当属性名字和形参发生重名的时候，或者  属性名字 和局部变量重名的时候，都会发生就近原则，所以如果我要是直接使用变量名字的话就指的是离的近的那个形参或者局部变量，这时候如果我想要表示属性的话，在前面要加上：this.修饰 

 

如果不发生重名问题的话，实际上你要是访问属性也可以省略this. 

 

```
1.  package com.msb4;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Person {
7.      //属性
8.      int age;
9.      String name;
10.    double height;
11.    //空构造器
12.    public Person(){
13. 
14.    }
15.    //有参构造器
16.    public Person(int age,String name,double height){
17.        this.age = age;
18.        this.name = name;
19.        this.height = height;
20.    }
21.    //方法：
22.    public void eat(){
23.        int age = 10;
24.        System.out.println(age);//就近原则，age指的是离它近的age--》局部变量的age
25.        System.out.println(this.age);//这里指代的就是属性的age
26.        System.out.println("我喜欢吃饭");
27.    }
28.}
29. 
```

 

（2）this修饰方法： 

总结：在同一个类中，方法可以互相调用，this.可以省略不写。 

```
1.  package com.msb4;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Person {
7.      //属性
8.      int age;
9.      String name;
10.    double height;
11.    //空构造器
12.    public Person(){
13. 
14.    }
15.    //有参构造器
16.    public Person(int age,String name,double height){
17.        this.age = age;
18.        this.name = name;
19.        this.height = height;
20.    }
21.    //方法：
22.    /*public void eat(){
23.        int age = 10;
24.        System.out.println(age);//就近原则，age指的是离它近的age--》局部变量的age
25.        System.out.println(this.age);//这里指代的就是属性的age
26.        System.out.println("我喜欢吃饭");
27.    }*/
28. 
29.    public void play(){
30.        /*this.*/eat();
31.        System.out.println("上网");
32.        System.out.println("洗澡");
33.    }
34. 
35.    public void eat(){
36.        System.out.println(/*this.*/age);
37.        System.out.println("吃饭");
38.    }
39.}
40. 
```

（3）this可以修饰构造器： 

总结：同一个类中的构造器可以相互用this调用，注意：this修饰构造器必须放在第一行 

```
1.  package com.msb4;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Person {
7.      //属性
8.      int age;
9.      String name;
10.    double height;
11.    //空构造器
12.    public Person(){
13. 
14.    }
15.    //有参构造器
16.    public Person(int age,String name,double height){
17.        this(age,name);
18.        this.height = height;
19. 
20.    }
21.    public Person(int age,String name){
22.        this(age);
23.        this.name = name;
24.    }
25.    public Person(int age){
26.        this.age = age;
27.    }
28.    //方法：
29.    /*public void eat(){
30.        int age = 10;
31.        System.out.println(age);//就近原则，age指的是离它近的age--》局部变量的age
32.        System.out.println(this.age);//这里指代的就是属性的age
33.        System.out.println("我喜欢吃饭");
34.    }*/
35. 
36.    public void play(){
37.        /*this.*/eat();
38.        System.out.println("上网");
39.        System.out.println("洗澡");
40.    }
41. 
42.    public void eat(){
43.        System.out.println(/*this.*/age);
44.        System.out.println("吃饭");
45.    }
46.}
47. 
```

#### static

【1】static可以修饰：属性，方法，代码块，内部类。 

 

【2】static修饰属性； 

```
1.  package com.msb5;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Test {
7.      //属性：
8.      int id;
9.      static int sid;
10. 
11.    //这是一个main方法，是程序的入口：
12.    public static void main(String[] args) {
13.        //创建一个Test类的具体的对象
14.        Test t1 = new Test();
15.        t1.id = 10;
16.        t1.sid = 10;
17. 
18.        Test t2 = new Test();
19.        t2.id = 20;
20.        t2.sid = 20;
21. 
22.        Test t3 = new Test();
23.        t3.id = 30;
24.        t3.sid = 30;
25. 
26.        //读取属性的值：
27.        System.out.println(t1.id);
28.        System.out.println(t2.id);
29.        System.out.println(t3.id);
30. 
31.        System.out.println(t1.sid);
32.        System.out.println(t2.sid);
33.        System.out.println(t3.sid);
34. 
35.    }
36.}
37. 
```

内存分析：

![img](https://image.201068.xyz/assets/clip_image496.jpg)

一般官方的推荐访问方式：可以通过类名.属性名的方式去访问： 

![img](https://image.201068.xyz/assets/clip_image498.jpg)

 

 

static修饰属性总结： 

（1）在类加载的时候一起加载入方法区中的静态域中 

（2）先于对象存在 

（3）访问方式： 对象名.属性名   类名.属性名（推荐） 

 

 

static修饰属性的应用场景：某些特定的数据想要在内存中共享，只有一块 --》这个情况下，就可以用static修饰的属性 

```
1.  package com.msb5;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class MsbStudent {
7.      //属性：
8.      String name;
9.      int age;
10.    static String school;
11. 
12.    //这是一个main方法，是程序的入口：
13.    public static void main(String[] args) {
14.        MsbStudent.school = "马士兵教育";
15.        //创建学生对象：
16.        MsbStudent s1 = new MsbStudent();
17.        s1.name = "张三";
18.        s1.age = 19;
19.        //s1.school = "马士兵教育";
20. 
21.        MsbStudent s2 = new MsbStudent();
22.        s2.name = "李四";
23.        s2.age = 21;
24.        //s2.school = "马士兵教育";
25. 
26.        System.out.println(s2.school);
27. 
28. 
29. 
30. 
31.    }
32. 
33.}
34. 
```

 

属性：

静态属性 （类变量） 

非静态属性（实例变量）

 

【3】static修饰方法； 

```
1.  package com.msb5;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Demo {
7.      int id;
8.      static int sid;
9.   
10.    public void a(){
11.        System.out.println(id);
12.        System.out.println(sid);
13.        System.out.println("------a");
14.    }
15.    //1.static和public都是修饰符，并列的没有先后顺序，先写谁后写谁都行
16.    static public void b(){
17.        //System.out.println(this.id);//4.在静态方法中不能使用this关键字
18.        //a();//3.在静态方法中不能访问非静态的方法
19.        //System.out.println(id);//2.在静态方法中不能访问非静态的属性
20.        System.out.println(sid);
21.        System.out.println("------b");
22.    }
23. 
24.    //这是一个main方法，是程序的入口：
25.    public static void main(String[] args) {
26.        //5.非静态的方法可以用对象名.方法名去调用
27.        Demo d = new Demo();
28.        d.a();
29.        //6.静态的方法可以用   对象名.方法名去调用  也可以 用  类名.方法名 （推荐）
30.        Demo.b();
31.        d.b();
32.       
33.    }
34.}
35. 
```

#### 代码块

【1】类的组成：属性，方法，构造器，代码块，内部类 

【2】代码块分类：普通块，构造块，静态块，同步块（多线程） 

【3】代码： 

```
1.  package com.msb6;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Test {
7.      //属性
8.      int a;
9.      static int sa;
10. 
11.    //方法
12.    public void a(){
13.        System.out.println("-----a");
14.        {
15.            //普通块限制了局部变量的作用范围
16.            System.out.println("这是普通块");
17.            System.out.println("----000000");
18.            int num = 10;
19.            System.out.println(num);
20.        }
21.        //System.out.println(num);
22.        //if(){}
23.        //while(){}
24.    }
25.    public static void b(){
26.        System.out.println("------b");
27.    }
28. 
29.    //构造块
30.    {
31.        System.out.println("------这是构造块");
32.    }
33.    //静态块
34.    static{
35.        System.out.println("-----这是静态块");
36.        //在静态块中只能方法：静态属性，静态方法
37.        System.out.println(sa);
38.        b();
39.    }
40. 
41. 
42.    //构造器
43.    public Test(){
44.        System.out.println("这是空构造器");
45.    }
46.    public Test(int a){
47.        this.a = a;
48.    }
49. 
50. 
51.    //这是一个main方法，是程序的入口：
52.    public static void main(String[] args) {
53.        Test t = new Test();
54.        t.a();
55. 
56.        Test t2 = new Test();
57.        t2.a();
58.    }
59. 
60. 
61. 
62.}
63. 
```

 

总结：

（1）代码块执行顺序： 

最先执行静态块，只在类加载的时候执行一次，所以一般以后实战写项目：创建工厂，数据库的初始化信息都放入静态块。

一般用于执行一些全局性的初始化操作。

 

再执行构造块，（不常用）

再执行构造器，

再执行方法中的普通块。

 

 

#### 包，import

【1】生活案例：

邮寄快递：中国.北京.通州区.****小区.5号楼.3单元.101房.赵珊珊 

历史：常山赵子龙

【2】包的作用： 

为了解决重名问题（实际上包对应的就是盘符上的目录）

解决权限问题

 

【3】创建包：

![img](https://image.201068.xyz/assets/clip_image502.jpg)

![img](https://image.201068.xyz/assets/clip_image504.jpg)

 

包名定义： 

（1）名字全部小写 

（2）中间用.隔开 

（3）一般都是公司域名倒着写 ：  com.jd  com.msb 

（4）加上模块名字： 

com.jd.login   com.jd.register 

（5）不能使用系统中的关键字：nul,con,com1---com9..... 

（6）包声明的位置一般都在非注释性代码的第一行： 

![img](https://image.201068.xyz/assets/clip_image506.jpg)

【4】导包问题： 

```
1.  //声明包：
2.  package com.msb7;
3.   
4.  import com.msb2.Person; //导包：就是为了进行定位
5.   
6.  import java.util.Date;
7.   
8.  /**
9.   * @Auther: msb-zhaoss
10. */
11.public class Test {
12.    //这是一个main方法，是程序的入口：
13.    public static void main(String[] args) {
14.        new Person();
15.        new Date();
16.        new java.sql.Date(1000L);//在导包以后，还想用其他包下同名的类，就必须要手动自己写所在的包。
17.        new Demo();
18.    }
19.}
20. 
```

总结：

（1）使用不同包下的类要需要导包： import **.*.*;  例如：import java.util.Date; 

（2）在导包以后，还想用其他包下同名的类，就必须要手动自己写所在的包。 

（3）同一个包下的类想使用不需要导包，可以直接使用。 

（4）在java.lang包下的类，可以直接使用无需导包： 

![img](https://image.201068.xyz/assets/clip_image508.jpg)

（5）IDEA中导包快捷键：alt+enter  

​    可以自己设置自动导包

（6）可以直接导入*： 

![img](https://image.201068.xyz/assets/clip_image510.jpg)

 

【5】在Java中的导包没有包含和被包含的关系： 

设置目录平级的格式（不是包含和被包含的显示）：
 ![img](https://image.201068.xyz/assets/clip_image512.jpg)

 

![img](https://image.201068.xyz/assets/clip_image514.jpg)

 

 

【6】静态导入： 

```
1.  package com.msb11;
2.  //静态导入：
3.  import static java.lang.Math.*;
4.  //导入：java.lang下的Math类中的所有静态的内容
5.  /**
6.   * @Auther: msb-zhaoss
7.   */
8.  public class Test {
9.      //这是一个main方法，是程序的入口：
10.    public static void main(String[] args) {
11.        System.out.println(random());
12.        System.out.println(PI);
13.        System.out.println(round(5.6));
14.    }
15.    //在静态导入后，同一个类中有相同的方法的时候，会优先走自己定义的方法。
16.    public static int round(double a){
17.        return 1000;
18.    }
19.}
20. 
```

 

#### 三大特性

 

##### 封装(Encapsulation)

**【1】生活案例：**

ATM ,  电线 

**【2】Java中封装的理解：** 

将某些东西进行隐藏，然后提供相应的方式进行获取。

![img](https://image.201068.xyz/assets/clip_image516.jpg)

 

我们程序设计追求“高内聚，低耦合”。

➢高内聚:类的内部数据操作细节自己完成，不允许外部干涉; 

➢低耦合:仅对外暴露少量的方法用于使用。 

隐藏对象内部的复杂性，只对外公开简单的接口。便于外界调用，从而提

高系统的可扩展性、可维护性。通俗的说，把该隐藏的隐藏起来，该暴露

的暴露出来。这就是封装性的设计思想。 

**【3】封装的好处：** 

提高代码的安全性

 

**【4】代码：通过一个属性感受封装：** 

```
1.  package com.msb.test01;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Girl {//女孩
7.      //属性：
8.      private int age;
9.   
10.    //读取年龄：
11.    public int duquAge(){
12.        return age;
13.    }
14. 
15.    //设置年龄：
16.    public void shezhiAge(int age){
17.        if(age >= 30 ){
18.            this.age = 18;
19.        }else{
20.            this.age = age;
21.        }
22. 
23.    }
24. 
25. 
26.}
27. 
```

 

```
1.  package com.msb.test01;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Test {
7.      //这是一个main方法，是程序的入口：
8.      public static void main(String[] args) {
9.          //创建一个Girl类的对象：
10.        Girl g = new Girl();
11.        /*g.age = 33;
12.        System.out.println(g.age);*/
13.        //设置年龄：
14.        g.shezhiAge(31);
15.        //读取年龄：
16.        System.out.println(g.duquAge());
17. 
18.    }
19.}
20. 
```

 

上面的代码，对于属性age来说，我加了修饰符private，这样外界对它的访问就受到了限制，现在我还想加上其他的限制条件，但是在属性本身上没有办法再加了，所以我们通过定义方法来进行限制条件的添加。

以属性为案例：

进行封装：

（1）将属性私有化，被private修饰--》加入权限修饰符

一旦加入了权限修饰符，其他人就不可以随意的获取这个属性

（2）提供public修饰的方法让别人来访问/使用 

（3）即使外界可以通过方法来访问属性了，但是也不能随意访问，因为咱们在方法中可以加入 限制条件。 

 

 

**【5】实际开发中，方法一般会写成 setter，getter方法：** 

可以利用IDEA快捷键生成：alt+insert -->getter and setter: 

```
1.  public class Girl {//女孩
2.      //属性：
3.      private int age;
4.   
5.      //读取年龄：
6.      public int getAge(){
7.          return age;
8.      }
9.   
10.    //设置年龄：
11.    public void setAge(int age){
12.        if(age >= 30 ){
13.            this.age = 18;
14.        }else{
15.            this.age = age;
16.        }
17.    }
18.}
19. 
```

 

**【6】加深练习：** 

```
1.  package com.msb.test2;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Student {
7.      //属性：
8.      private int age;
9.      private String name;
10.    private String sex;
11. 
12.    //加入对应的setter和getter方法：
13.    public int getAge() {
14.        return age;
15.    }
16. 
17.    public void setAge(int age) {
18.        this.age = age;
19.    }
20. 
21.    public String getName() {
22.        return name;
23.    }
24. 
25.    public void setName(String name) {
26.        this.name = name;
27.    }
28. 
29.    public String getSex() {
30.        return sex;
31.    }
32. 
33.    public void setSex(String sex) {
34.        if("男".equals(sex) || "女".equals(sex) ){//sex是男 或者 是 女
35.            this.sex = sex;
36.        }else{
37.            this.sex = "男";
38.        }
39.    }
40. 
41.    //加入构造器：
42.    public Student(){
43. 
44.    }
45. 
46.    public Student(int age,String name,String sex){
47.        this.age = age;
48.        this.name = name;
49.        //this.sex = sex;
50.        this.setSex(sex);
51.    }
52.}
53. 
```

 

```
1.  package com.msb.test2;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Test {
7.      //这是一个main方法，是程序的入口：
8.      public static void main(String[] args) {
9.          //创建一个Student对象：
10.        Student s1 = new Student();
11.        s1.setName("nana");
12.        s1.setAge(19);
13.        s1.setSex("女");
14.        System.out.println(s1.getName()+"---"+s1.getAge()+"----"+s1.getSex());
15. 
16.        Student s2 = new Student(18,"菲菲","asdfasdfsadf");
17.        System.out.println(s2.getName()+"---"+s2.getAge()+"----"+s2.getSex());
18.    }
19.}
20. 
```

 

##### 继承(Inheritance)

**【1】类是对对象的抽象：**

举例：

荣耀20 ，小米 红米3，华为 p40 pro  ---> 类：手机类 

 

**【2】继承是对类的抽象：** 

举例：

学生类：Student： 

属性：姓名，年龄，身高，学生编号

方法：吃饭，睡觉，喊叫，学习

 

教师类：Teacher: 

属性：姓名，年龄，身高，教师编号

方法：吃饭，睡觉，喊叫，教学

 

员工类：Emploee: 

属性：姓名，年龄，身高，员工编号

方法：吃饭，睡觉，喊叫，工作

 

共同的东西：

人类：

属性：姓名，年龄，身高

方法：吃饭，睡觉，喊叫

学生类/教师类/员工类  继承 自  人类  

 

以后定义代码：

先定义人类：

人类： ---》父类，基类，超类 

属性：姓名，年龄，身高

方法：吃饭，睡觉，喊叫

 

再定义 ： ---》子类，派生类 

学生类：Student： 

属性：学生编号

方法：学习

 

教师类：Teacher: 

属性：教师编号

方法：教学

 

员工类：Emploee: 

属性：员工编号

方法：工作 

子类  继承自  父类 

狗类：

属性：姓名，年龄，身高

方法：吃饭，睡觉，喊叫

 

我们的继承关系，是在合理的范围中进行的抽取 ，抽取出子类父类的关系： 

上面的案例中：

学生类/教师类/员工类  继承 自  人类  ---》合理 

学生类/教师类/员工类  继承 自  狗类  ---》不合理 

 

区分：

学生是一个人

教师是一个人

员工是一个人  ---》合理 

 

学生是一个狗   ---》不合理 

 

总结：继承 就是  is - a 的关系 

 

**【3】代码层面的解释：** 

先写父类，再写子类：

父类：人类  Person 

子类：学生类  Student 

```
1.  package com.msb.test03;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Person {
7.      //属性：
8.      private int age;
9.      private String name;
10.    private double height;
11. 
12.    //提供setter getter方法：
13. 
14.    public int getAge() {
15.        return age;
16.    }
17. 
18.    public void setAge(int age) {
19.        this.age = age;
20.    }
21. 
22.    public String getName() {
23.        return name;
24.    }
25. 
26.    public void setName(String name) {
27.        this.name = name;
28.    }
29. 
30.    public double getHeight() {
31.        return height;
32.    }
33. 
34.    public void setHeight(double height) {
35.        this.height = height;
36.    }
37. 
38.    //方法：
39.    public void eat(){
40.        System.out.println("可以吃饭。。。");
41.    }
42. 
43.    public void sleep(){
44.        System.out.println("可以睡觉。。。");
45.    }
46. 
47.}
48. 
```

 

```
1.  package com.msb.test03;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Student extends Person {//子类Student 继承  父类Person
7.      //属性：
8.      private int sno;//学号
9.   
10.    public int getSno() {
11.        return sno;
12.    }
13. 
14.    public void setSno(int sno) {
15.        this.sno = sno;
16.    }
17. 
18.    //方法：
19.    public void study(){
20.        System.out.println("学生可以学习");
21.    }
22. 
23.}
24. 
```

 

```
1.  package com.msb.test03;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Test {
7.      //这是一个main方法，是程序的入口：
8.      public static void main(String[] args) {
9.          //创建子类Student的对象
10.        Student s = new Student();
11.        s.setSno(1001);
12.        s.setAge(18);
13.        s.setName("菲菲");
14.        s.setHeight(180.4);
15. 
16.        System.out.println("学生名字为："+s.getName()+",学生的年纪："+s.getAge());
17. 
18.        //访问方法：
19.        s.study();
20.        s.eat();
21.        s.sleep();
22.    }
23.}
24. 
```

 

 

 

**【4】继承的好处：**提高代码的复用性 

父类定义的内容，子类可以直接拿过来用就可以了，不用代码上反复重复定义了

 

需要注意的点：

父类private修饰的内容，子类实际上也继承，只是因为封装的特性阻碍了直接调用，但是提供了间接调用的方式，可以间接调用。 

 

**【5】总结：** 

 

**（1）继承关系 ：** 

父类/基类/超类 

子类/派生类 

子类继承父类一定在合理的范围进行继承的   子类 extends  父类 

**（2）继承的好处：** 

1.提高了代码的复用性，父类定义的内容，子类可以直接拿过来用就可以了，不用代码上反复重复定义了

2.便于代码的扩展 

3.为了以后多态的使用。是多态的前提。 

（3）父类private修饰的内容，子类也继承过来了。 

（4）一个父类可以有多个子类。 

（5）一个子类只能有一个直接父类。 

但是可以间接的继承自其它类。

 

![img](https://image.201068.xyz/assets/clip_image518.jpg)

 

（6）继承具有传递性： 

Student --》继承自  Person  ---》继承自Object 

Object类是所有类的根基父类。 

所有的类都直接或者间接的继承自Object。 

 

###### 内存分析

![img](https://image.201068.xyz/assets/clip_image520.jpg)

 

###### 权限修饰符

![img](https://image.201068.xyz/assets/clip_image522.jpg)

 

 

【1】private：权限：在当前类中可以访问 

![img](https://image.201068.xyz/assets/clip_image524.jpg)

![img](https://image.201068.xyz/assets/clip_image526.jpg)

![img](https://image.201068.xyz/assets/clip_image528.jpg)

 

【2】default:缺省修饰符：权限：到同一个包下的其他类都可以访问 

 

![img](https://image.201068.xyz/assets/clip_image530.jpg)

 

![img](https://image.201068.xyz/assets/clip_image532.jpg)

![img](https://image.201068.xyz/assets/clip_image534.jpg)

 

【3】protected：权限：最大到不同包下的子类 

![img](https://image.201068.xyz/assets/clip_image536.jpg)

![img](https://image.201068.xyz/assets/clip_image538.jpg)

![img](https://image.201068.xyz/assets/clip_image540.jpg)

 

【4】public：在整个项目中都可以访问 

 

 

 

总结：

属性，方法：修饰符：四种：private，缺省，protected，public 

类：修饰符：两种：缺省，public 

 

以后写代码

一般属性：用private修饰 ，方法：用public修饰 

 

 

###### 方法的重写

**【1】重写：**

发生在子类和父类中，当子类对父类提供的方法不满意的时候，要对父类的方法进行重写。

 

**【2】重写有严格的格式要求：** 

子类的方法名字和父类必须一致，参数列表（个数，类型，顺序）也要和父类一致。

 

**【3】代码：** 

```
1.  public class Person {
2.      public void eat(){
3.          System.out.println("吃食物");
4.      }
5.      public void sleep(){
6.          System.out.println("睡觉");
7.      }
8.  }
9.   
```

  

```
1.  public class Student extends Person {
2.      public void study(){
3.          System.out.println("学习");
4.      }
5.            @override
6.      public void eat(){
7.          System.out.println("我喜欢吃小龙虾喝啤酒。。");
8.      }
9.  }
```

![img](https://image.201068.xyz/assets/clip_image542.jpg)

 

```
1.  public class Test {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) {
4.          //创建一个Student类的对象：
5.          Student s = new Student();
6.          s.eat();
7.      }
8.  }
```

**【4】内存：** 

![img](https://image.201068.xyz/assets/clip_image544.jpg)

**【5】重载和重写的区别：** 

重载：在同一个类中，当方法名相同，形参列表不同的时候  多个方法构成了重载 

重写：在不同的类中，子类对父类提供的方法不满意的时候，要对父类的方法进行重写。

 

![img](https://image.201068.xyz/assets/clip_image546.jpg)

###### super

【1】super:指的是：  父类的 

【2】super可以修饰属性，可以修饰方法； 

在子类的方法中，可以通过  super.属性  super.方法 的方式，显示的去调用父类提供的属性，方法。在通常情况下，super.可以省略不写： 

![img](https://image.201068.xyz/assets/clip_image548.jpg)

在特殊情况下，当子类和父类的属性重名时，你要想使用父类的属性，必须加上修饰符super.，只能通过super.属性来调用 

在特殊情况下，当子类和父类的方法重名时，你要想使用父类的方法，必须加上修饰符super.，只能通过super.方法来调用 

在这种情况下，super.就不可以省略不写。 

 

![img](https://image.201068.xyz/assets/clip_image550.jpg)

**【3】super修饰构造器：** 

其实我们平时写的构造器的第一行都有：super()  -->作用：调用父类的空构造器，只是我们一般都省略不写 

（所有构造器的第一行默认情况下都有super(),但是一旦你的构造器中显示的使用super调用了父类构造器，那么这个super()就不会给你默认分配了。如果构造器中没有显示的调用父类构造器的话，那么第一行都有super(),可以省略不写） 

![img](https://image.201068.xyz/assets/clip_image552.jpg)

 

如果构造器中已经显示的调用super父类构造器，那么它的第一行就没有默认分配的super();了 

 

![img](https://image.201068.xyz/assets/clip_image554.jpg)

在构造器中，super调用父类构造器和this调用子类构造器只能存在一个，两者不能共存：

因为super修饰构造器要放在第一行，this修饰构造器也要放在第一行： 

![img](https://image.201068.xyz/assets/clip_image556.jpg)

改正二选一即可：

![img](https://image.201068.xyz/assets/clip_image558.jpg)

 

 

 

 

 

**【4】以后写代码构造器的生成可以直接使用IDEA提供的快捷键：** 

alt+insert

![img](https://image.201068.xyz/assets/clip_image560.jpg)

 

 

###### 继承条件下构造方法的执行过程

![img](https://image.201068.xyz/assets/clip_image562.jpg)

```
1.  package com.msb.test10;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Person {
7.      int age;
8.      String name;
9.   
10.    public Person(int age, String name) {
11.        super();
12.        this.age = age;
13.        this.name = name;
14.    }
15. 
16.    public Person() {
17.    }
18.}
19. 
```

 

```
1.  public class Student extends Person {
2.      double height ;
3.   
4.      public Student() {
5.      }
6.   
7.      public Student(int age, String name, double height) {
8.          super(age, name);
9.          this.height = height;
10.    }
11.}
12. 
```

 

```
1.  public class Test {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) {
4.          Student s = new Student(19,"feifei",160.8);
5.      }
6.  }
7.   
```

###### Object类

所有类都直接或间接的继承自Object类，Object类是所有Java类的根基类。

也就意味着所有的Java对象都拥有Object类的属性和方法。 

如果在类的声明中未使用extends关键字指明其父类，则默认继承Object类。 

![img](https://image.201068.xyz/assets/clip_image564.jpg)

 

toString()方法

**【1】Object类的toString()的作用：** 

![img](https://image.201068.xyz/assets/clip_image566.jpg)

 

方法的原理：

![img](https://image.201068.xyz/assets/clip_image568.jpg)

 

现在，使用toString方法的时候，打印出来的东西 “不好看”，对于其他人来说不友好，可读性不好 

我们现在是想知道对象的信息，名字，年龄，身高。。。。。。

现在的格式不好：

![img](https://image.201068.xyz/assets/clip_image570.jpg)

 

 

出现的问题：子类Student对父类Object提供的toString方法不满意，不满意--》对toString方法进行重写： 

 

```
1.  package com.msb.test01;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Student /*extends Object*/{
7.      private String name;
8.      private int age;
9.      private double height;
10. 
11.    public String getName() {
12.        return name;
13.    }
14. 
15.    public void setName(String name) {
16.        this.name = name;
17.    }
18. 
19.    public int getAge() {
20.        return age;
21.    }
22. 
23.    public void setAge(int age) {
24.        this.age = age;
25.    }
26. 
27.    public double getHeight() {
28.        return height;
29.    }
30. 
31.    public void setHeight(double height) {
32.        this.height = height;
33.    }
34. 
35.    public Student() {
36.    }
37. 
38.    public Student(String name, int age, double height) {
39.        this.name = name;
40.        this.age = age;
41.        this.height = height;
42.    }
43. 
44.    public String toString() {
45.        return "这是一个Student对象，这个对象的名字："+name+",年龄："+age+",身高："+height;
46.    }
47.}
48. 
```

测试类：

![img](https://image.201068.xyz/assets/clip_image572.jpg)

 

总结：toString的作用就是对对象进行“自我介绍”，一般子类对父类提供的toString都不满意，都要进行重写。

 

IDEA提供了快捷键： 

 

```
1.  package com.msb.test01;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Student /*extends Object*/{
7.      private String name;
8.      private int age;
9.      private double height;
10. 
11.    public String getName() {
12.        return name;
13.    }
14. 
15.    public void setName(String name) {
16.        this.name = name;
17.    }
18. 
19.    public int getAge() {
20.        return age;
21.    }
22. 
23.    public void setAge(int age) {
24.        this.age = age;
25.    }
26. 
27.    public double getHeight() {
28.        return height;
29.    }
30. 
31.    public void setHeight(double height) {
32.        this.height = height;
33.    }
34. 
35.    public Student() {
36.    }
37. 
38.    public Student(String name, int age, double height) {
39.        this.name = name;
40.        this.age = age;
41.        this.height = height;
42.    }
43. 
44.    /*public String toString() {
45.        return "这是一个Student对象，这个对象的名字："+name+",年龄："+age+",身高："+height;
46.    }*/
47. 
48.    @Override
49.    public String toString() {
50.        return "Student{" +
51.                "name='" + name + '\'' +
52.                ", age=" + age +
53.                ", height=" + height +
54.                '}';
55.    }
56.}
57. 
```

equals方法

```
1.  package com.msb.test02;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Phone {//手机类：
7.      //属性：
8.      private String brand;//品牌型号
9.      private double price;//价格
10.    private int year ;//出产年份
11.    //方法：
12. 
13.    public String getBrand() {
14.        return brand;
15.    }
16. 
17.    public void setBrand(String brand) {
18.        this.brand = brand;
19.    }
20. 
21.    public double getPrice() {
22.        return price;
23.    }
24. 
25.    public void setPrice(double price) {
26.        this.price = price;
27.    }
28. 
29.    public int getYear() {
30.        return year;
31.    }
32. 
33.    public void setYear(int year) {
34.        this.year = year;
35.    }
36. 
37.    @Override
38.    public String toString() {
39.        return "Phone{" +
40.                "brand='" + brand + '\'' +
41.                ", price=" + price +
42.                ", year=" + year +
43.                '}';
44.    }
45. 
46.    //构造器：
47. 
48.    public Phone() {
49.    }
50. 
51.    public Phone(String brand, double price, int year) {
52.        this.brand = brand;
53.        this.price = price;
54.        this.year = year;
55.    }
56. 
57. 
58.    //对equals方法进行重写：
59.    public boolean equals(Object obj) {//Object obj = new Phone();
60.        //将obj转为Phone类型：
61.        Phone other = (Phone)obj;//向下转型，为了获取子类中特有的内容
62.        if(this.getBrand()==other.getBrand()&&this.getPrice()==other.getPrice()&&this.getYear()==other.getYear()){
63.            return true;
64.        }
65.        return false;
66.    }
67.}
68. 
```

 

```
1.  package com.msb.test02;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Test {
7.      //这是一个main方法，是程序的入口：
8.      public static void main(String[] args) {
9.   
10.        //创建Phone类的对象：
11.        Phone p1 = new Phone("华为P40",2035.98,2020);
12.        Phone p2 = new Phone("华为P40",2035.98,2020);
13.        //比较两个对象：p1和p2对象：
14.        //==的作用：比较左右两侧的值是否想的，要么相等，返回true,要么不相等,返回false
15.        System.out.println(p1==p2);//-->>>对于引用数据类型来说，比较的是地址值。--->一定返回的是false
16. 
17.        //Object类提供了一个方法 equals方法 ：作用：比较对象具体内容是否相等。
18.        boolean flag = p1.equals(p2);//点进源码发现：底层依旧比较的是==，比较的还是地址值。
19.        System.out.println(flag);
20. 
21.    }
22.}
23. 
```

总结：

equals作用：这个方法提供了对对象的内容是否相等 的一个比较方式，对象的内容指的就是属性。

父类Object提供的equals就是在比较==地址，没有实际的意义，我们一般不会直接使用父类提供的方法，

而是在子类中对这个方法进行重写。

 

 

instanceof

![img](https://image.201068.xyz/assets/clip_image574.jpg)

 

利用集成开发工具生成equals方法

**【1】利用eclipse：** 

![img](https://image.201068.xyz/assets/clip_image576.jpg)

**【2】利用idea：** 

![img](https://image.201068.xyz/assets/clip_image578.jpg)

 

###### 类和类的关系

 

代码

总结： 

**【1】面向对象的思维：**找参与者，找女孩类，找男孩类 

**【2】体会了什么叫方法的性擦，什么叫方法的实参：** 

![img](https://image.201068.xyz/assets/clip_image580.jpg)

具体传入的内容 实参： 

![img](https://image.201068.xyz/assets/clip_image582.jpg)

**【3】类和类可以产生关系：** 

（1）将一个类作为另一个类中的方法的形参 

（2）将一个类作为另一个类的属性 

 

```
1.  public class Girl {
2.      //属性：
3.      String name;
4.      double weight;
5.      Mom m /*= new Mom()*/;
6.      //方法：
7.      public void add(int a){//参数是基本数据类型
8.          System.out.println(a);
9.          System.out.println(a+100);
10.    }
11.    //谈恋爱的方法：
12.    public void love(Boy b){//参数是引用数据类型Boy
13.        System.out.println("我男朋友的名字是："+b.name+"，我男朋友的年龄是："+b.age);
14.        b.buy();
15.    }
16. 
17.    //女孩跟妈妈聊天：
18.    public void wechat(){
19.        m.say();
20.    }
21. 
22.    //构造器：
23.    public Girl(String name, double weight) {
24.        this.name = name;
25.        this.weight = weight;
26.    }
27.}
```

 

```
1.  public class Boy {
2.      //属性：
3.      int age;
4.      String name;
5.      //方法：
6.      public void buy(){
7.          System.out.println("跟我谈恋爱，我给你买买买。。。");
8.      }
9.      //构造器：
10.    public Boy(int age, String name) {
11.        this.age = age;
12.        this.name = name;
13.    }
14.}
```

 

```
1.  public class Mom {
2.      //方法：
3.      public void say(){
4.          System.out.println("妈妈唠唠叨叨 都是爱，听妈妈的话。。");
5.      }
6.  }
7.   
```

 

```
1.  public class Test {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) {
4.          //创建一个Boy类的具体的对象：
5.          Boy boy = new Boy(30,"鹿晗");
6.          //创建一个Girl类的具体的对象：
7.          Girl girl = new Girl("关晓彤",100);
8.          //谈恋爱：
9.          //girl.love(boy);
10.        Boy boy2 = new Boy(35,"陈伟霆");
11.        girl.love(boy2);
12. 
13.        //还可以跟妈妈微信聊天：
14.        girl.m = new Mom();
15.        girl.wechat();
16.    }
17.}
```

 

 

总结

一、继承关系    

继承指的是一个类（称为子类、子接口）继承另外的一个类（称为父类、父接口）的功能，并可以增加它自己的新功能的能力。在Java中继承关系通过关键字extends明确标识，在设计时一般没有争议性。在UML类图设计中，继承用一条带空心三角箭头的实线表示，从子类指向父类，或者子接口指向父接口。 

![img](https://image.201068.xyz/assets/clip_image584.jpg)

 

 

二、实现关系    

实现指的是一个class类实现interface接口（可以是多个）的功能，实现是类与接口之间最常见的关系。在Java中此类关系通过关键字implements明确标识，在设计时一般没有争议性。在UML类图设计中，实现用一条带空心三角箭头的虚线表示，从类指向实现的接口。

![img](https://image.201068.xyz/assets/clip_image586.jpg)

 

三、依赖关系    

简单的理解，依赖就是一个类A使用到了另一个类B，而这种使用关系是具有偶然性的、临时性的、非常弱的，但是类B的变化会影响到类A。比如某人要过河，需要借用一条船，此时人与船之间的关系就是依赖。表现在代码层面，让类B作为参数被类A在某个method方法中使用。在UML类图设计中，依赖关系用由类A指向类B的带箭头虚线表示。 

 

![img](https://image.201068.xyz/assets/clip_image588.jpg)

 

四、关联关系  

关联体现的是两个类之间语义级别的一种强依赖关系，比如我和我的朋友，这种关系比依赖更强、不存在依赖关系的偶然性、关系也不是临时性的，一般是长期性的，而且双方的关系一般是平等的。关联可以是单向、双向的。表现在代码层面，为被关联类B以类的属性形式出现在关联类A中，也可能是关联类A引用了一个类型为被关联类B的全局变量。在UML类图设计中，关联关系用由关联类A指向被关联类B的带箭头实线表示，在关联的两端可以标注关联双方的角色和多重性标记。 

![img](https://image.201068.xyz/assets/clip_image590.jpg)

 

五、聚合关系    

聚合是关联关系的一种特例，它体现的是整体与部分的关系，即has-a的关系。此时整体与部分之间是可分离的，它们可以具有各自的生命周期，部分可以属于多个整体对象，也可以为多个整体对象共享。比如计算机与CPU、公司与员工的关系等，比如一个航母编队包括海空母舰、驱护舰艇、舰载飞机及核动力攻击潜艇等。表现在代码层面，和关联关系是一致的，只能从语义级别来区分。在UML类图设计中，聚合关系以空心菱形加实线箭头表示。 

![img](https://image.201068.xyz/assets/clip_image592.jpg)

 

六、组合关系    

组合也是关联关系的一种特例，它体现的是一种contains-a的关系，这种关系比聚合更强，也称为强聚合。它同样体现整体与部分间的关系，但此时整体与部分是不可分的，整体的生命周期结束也就意味着部分的生命周期结束，比如人和人的大脑。表现在代码层面，和关联关系是一致的，只能从语义级别来区分。在UML类图设计中，组合关系以实心菱形加实线箭头表示。 

![img](https://image.201068.xyz/assets/clip_image594.jpg)

 

七、总结    

对于继承、实现这两种关系没多少疑问，它们体现的是一种类和类、或者类与接口间的纵向关系。其他的四种关系体现的是类和类、或者类与接口间的引用、横向关系，是比较难区分的，有很多事物间的关系要想准确定位是很难的。前面也提到，这四种关系都是语义级别的，所以从代码层面并不能完全区分各种关系，但总的来说，后几种关系所表现的强弱程度依次为：组合>聚合>关联>依赖。

 

 

##### 多态(Polymorphism)

**【1】多态跟属性无关，多态指的是方法的多态，而不是属性的多态。**

【**2】案例代入：** 

```
1.  public class Animal {//父类：动物：
2.      public void shout(){
3.          System.out.println("我是小动物，我可以叫。。。");
4.      }
5.  }
```

 

```
1.  public class Cat extends Animal{
2.      //喊叫方法：
3.      public void shout(){
4.          System.out.println("我是小猫，可以喵喵叫");
5.      }
6.      public void scratch(){
7.          System.out.println("我是小猫，我可以挠人");
8.      }
9.  }
```

 

```
1.  public class Dog extends Animal{
2.      //喊叫：
3.      public void shout(){
4.          System.out.println("我是小狗，我可以汪汪叫");
5.      }
6.      public void guard(){
7.          System.out.println("我是小狗，我可以看家护院，保护我的小主人。。。");
8.      }
9.  }
```

 

```
1.  public class Pig extends Animal{
2.      public void shout(){
3.          System.out.println("我是小猪，我嗯嗯嗯的叫");
4.      }
5.      public void eat(){
6.          System.out.println("我是小猪，我爱吃东西。。");
7.      }
8.   
9.  }
```

 

```
1.  public class Girl {
2.      //跟猫玩耍：
3.      /*public void play(Cat cat){
4.          cat.shout();
5.      }*/
6.      //跟狗玩耍：
7.      /*public void play(Dog dog){
8.          dog.shout();
9.      }*/
10.    //跟小动物玩耍：
11.    public void play(Animal an){
12.        an.shout();
13.    }
14.}
```

 

```
1.  public class Test {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) {
4.          //具体的猫：--》猫的对象
5.          //Cat c = new Cat();
6.          //具体的小女孩：--》女孩的对象
7.          Girl g = new Girl();
8.          //小女孩跟猫玩：
9.          //g.play(c);
10.        //具体的狗---》狗的对象：
11.        //Dog d = new Dog();
12.        //小女孩跟狗玩：
13.        //g.play(d);
14.        //具体的动物：--》动物的对象：
15.        //Cat c = new Cat();
16.        //Dog d = new Dog();
17.        Pig p = new Pig();
18.        Animal an = p;
19.        g.play(an);
20.    }
21.}
```

 

 

 

**【3】总结：** 

（1）先有父类，再有子类：--》继承  先有子类，再抽取父类 ----》泛化 

（2）什么是多态： 

多态就是多种状态：同一个行为，不同的子类表现出来不同的形态。

多态指的就是同一个方法调用，然后由于对象不同会产生不同的行为。

（3）多态的好处： 

为了提高代码的扩展性，符合面向对象的设计原则：开闭原则。

开闭原则：指的就是扩展是 开放的，修改是关闭的。 

注意：多态可以提高扩展性，但是扩展性没有达到最好，以后我们会学习 反射 

 

（4）多态的要素： 

一，继承：  Cat extends Animal  ,Pig extends Animal,  Dog extends Animal 

二，重写：子类对父类的方法shout()重写 

三， 父类引用指向子类对象： 

 

```
1.  Pig p = new Pig();
2.  Animal an = p;
```

将上面的代码合为一句话：

Animal an = new Pig(); 

=左侧：编译期的类型 

=右侧：运行期的类型 

 

 

Animal an = new Pig(); 

g.play(an); // 

 

```
1.  public void play(Animal an){//Animal an = an = new Pig();
2.          an.shout();
3.      }
```

 

上面的代码，也是多态的一种非常常见的应用场合：父类当方法的形参，然后传入的是具体的子类的对象，

然后调用同一个方法，根据传入的子类的不同展现出来的效果也不同，构成了多态。

 

 

###### 内存分析

![img](https://image.201068.xyz/assets/clip_image596.jpg)

 

###### 向下转型，向上转型

![img](https://image.201068.xyz/assets/clip_image598.jpg)

![img](https://image.201068.xyz/assets/clip_image600.jpg)

 

 

现在我就想访问到eat()方法和weight属性： 

```
1.  public class Demo {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) {
4.          Pig p = new Pig();
5.          Animal an = p;//转型：向上转型
6.          an.shout();
7.   
8.          //加入转型的代码：
9.          //将Animal转为Pig类型：
10.        Pig pig = (Pig)an ;//转型：向下转型
11.        pig.eat();
12.        pig.age = 10;
13.        pig.weight = 60.8;
14.    }
15.}
```

对应内存：

![img](https://image.201068.xyz/assets/clip_image602.jpg)

 

思考之前的equals方法： 

![img](https://image.201068.xyz/assets/clip_image604.jpg)

 

 

###### 简单工厂设计模式

不仅可以使用父类做方法的形参，还可以使用父类做方法的返回值类型，真实返回的对象可以是该类的任意一个子类对象。

简单工厂模式的实现，它是解决大量对象创建问题的一个解决方案。将创建和使用分开，工厂负责创建，使用者直接调用即可。简单工厂模式的基本要求是 

² 定义一个static方法，通过类名直接调用

² 返回值类型是父类类型，返回的可以是其任意子类类型 

² 传入一个字符串类型的参数，工厂根据参数创建对应的子类产品 

 

```
1.  public class Test {
2.      public static void main(String[] args) {
3.          Girl g = new Girl();
4.   
5.          //Cat c = new Cat();
6.          //Dog d = new Dog();
7.          //Pig p = new Pig();
8.          Animal an = PetStore.getAnimal("狗");
9.   
10.        g.play(an);
11.    }
12.}
```

 

```
1.  public class PetStore {//宠物店 ---》工厂类
2.      //方法：提供动物
3.      public static Animal getAnimal(String petName){//多态的应用场合（二）
4.          Animal an = null;
5.   
6.          if("猫".equals(petName)){//petName.equals("猫") --》这样写容易发生空指针异常
7.              an = new Cat();
8.          }
9.   
10.        if("狗".equals(petName)){
11.            an = new Dog();
12.        }
13. 
14.        if("猪".equals(petName)){
15.            an = new Pig();
16.        }
17. 
18.        return an;
19.    }
20.}
```

#### final

**【1】修饰变量；**

```
1.  public class Test {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) {
4.          //第1种情况：
5.          //final修饰一个变量，变量的值不可以改变，这个变量也变成了一个字符常量，约定俗称的规定：名字大写
6.          final int A = 10;//final修饰基本数据类型
7.          //A = 20; 报错：不可以修改值
8.          //第2种情况：
9.          final Dog d = new Dog();//final修饰引用数据类型，那么地址值就不可以改变
10.        //d = new Dog(); -->地址值不可以更改
11.        //d对象的属性依然可以改变：
12.        d.age = 10;
13.        d.weight = 13.7;
14. 
15.        //第3种情况：
16.        final Dog d2 = new Dog();
17.        a(d2);
18.        //第4种情况：
19.        b(d2);
20. 
21.    }
22.    public static void a(Dog d){
23.        d = new Dog();
24.    }
25.    public static void b(final Dog d){//d被final修饰 ，指向不可以改变
26.        //d = new Dog();
27.    }
28.}
```

**【2】修饰方法；** 

final修饰方法，那么这个方法不可以被该类的子类重写： 

![img](https://image.201068.xyz/assets/clip_image606.jpg)

 

**【3】修饰类；** 

final修饰类，代表没有子类，该类不可以被继承： 

一旦一个类被final修饰，那么里面的方法也没有必要用final修饰了（final可以省略不写） 

![img](https://image.201068.xyz/assets/clip_image608.jpg)

**【4】案例：JDK提供的Math类：**看源码发现： 

（1）使用Math类的时候无需导包，直接使用即可： 

![img](https://image.201068.xyz/assets/clip_image610.jpg)

 

 

（2）Math类没有子类，不能被其他类继承了 

![img](https://image.201068.xyz/assets/clip_image612.jpg)

 

（3）里面的属性全部被final修饰，方法也是被final修饰的，只是省略不写了 

原因：子类没有必要进行重写。

 

（4）外界不可以创建对象： 

Math m = new Math(); 

![img](https://image.201068.xyz/assets/clip_image614.jpg)

 

 

（5）发现Math类中的所有的属性，方法都被static修饰 

那么不用创建对象去调用，只能通过类名.属性名  类名.方法名 去调用 

#### 抽象类，抽象方法

【1】抽象类和抽象方法的关系：

抽象类中可以定义0-n个抽象方法。 

【2】抽象类作用： 

在抽象类中定义抽象方法，目的是为了为子类提供一个通用的模板，子类可以在模板的基础上进行开发，先重写父类的抽象方法，然后可以扩展子类自己的内容。抽象类设计避免了子类设计的随意性，通过抽象类，子类的设计变得更加严格，进行某些程度上的限制。

使子类更加的通用。

【3】代码： 

```
1.  package com.msb.test03;
2.   
3.  //4.一个类中如果有方法是抽象方法，那么这个类也要变成一个抽象类。
4.  //5.一个抽象类中可以有0-n个抽象方法
5.  public abstract class Person {
6.      //1.在一个类中，会有一类方法，子类对这个方法非常满意，无需重写，直接使用
7.      public void eat(){
8.          System.out.println("一顿不吃饿得慌");
9.      }
10.    //2.在一个类中，会有一类方法，子类对这个方法永远不满意，会对这个方法进行重写。
11.    //3.一个方法的方法体去掉，然后被abstract修饰，那么这个方法就变成了一个抽象方法
12.    public abstract void say();
13.    public abstract void sleep();
14.}
15. 
16.//6.抽象类可以被其他类继承：
17.//7.一个类继承一个抽象类，那么这个类可以变成抽象类
18.//8.一般子类不会加abstract修饰，一般会让子类重写父类中的抽象方法
19.//9.子类继承抽象类，就必须重写全部的抽象方法
20.//10.子类如果没有重写父类全部的抽象方法，那么子类也可以变成一个抽象类。
21.class Student extends Person{
22. 
23.    @Override
24.    public void say() {
25.        System.out.println("我是东北人，我喜欢说东北话。。");
26.    }
27. 
28.    @Override
29.    public void sleep() {
30.        System.out.println("东北人喜欢睡炕。。");
31.    }
32.}
33. 
34.class Demo{
35.    //这是一个main方法，是程序的入口：
36.    public static void main(String[] args) {
37.        //11.创建抽象类的对象：-->抽象类不可以创建对象
38.        //Person p = new Person();
39. 
40.        //12.创建子类对象：
41.        Student s = new Student();
42.        s.sleep();
43.        s.say();
44.        
45.        //13.多态的写法：父类引用只想子类对象：
46.        Person p  = new Student();
47.        p.say();
48.        p.sleep();
49.    }
50.}
51. 
```

【4】面试题： 

（1）抽象类不能创建对象，那么抽象类中是否有构造器？ 

抽象类中一定有构造器。构造器的作用  给子类初始化对象的时候要先super调用父类的构造器。 

（2）抽象类是否可以被final修饰？ 

不能被final修饰，因为抽象类设计的初衷就是给子类继承用的。要是被final修饰了这个抽象类了，就不存在继承了，就没有子类。

#### 接口

**【1】接口声明格式：** 

  [访问修饰符]   interface 接口名  [extends 父接口1，父接口2…] {          常量定义；             方法定义；    }   

 

**【2】代码：** 

```
1.  package com.msb.test04;
2.   
3.  /**
4.   * 1.类是类，接口是接口，它们是同一层次的概念。
5.   * 2.接口中没有构造器
6.   * 3.接口如何声明：interface
7.   * 4.在JDK1.8之前，接口中只有两部分内容：
8.   * （1）常量：固定修饰符：public static final
9.   * （2）抽象方法：固定修饰符：public abstract
10. * 注意：修饰符可以省略不写，IDE会帮你自动补全，但是初学者建议写上，防止遗忘。
11. */
12.public interface TestInterface01 {
13.    //常量：
14.    /*public static final*/ int NUM = 10;
15.    //抽象方法：
16.    /*public abstract*/ void a();
17.    /*public abstract*/ void b(int num);
18.    /*public abstract*/ int c(String name);
19.}
20. 
21.interface TestInterface02{
22.    void e();
23.    void f();
24.}
25./*
26.5.类和接口的关系是什么？ 实现关系  类实现接口：
27.6.一旦实现一个接口，那么实现类要重写接口中的全部的抽象方法：
28.7.如果没有全部重写抽象方法，那么这个类可以变成一个抽象类。
29.8.java只有单继承，java还有多实现
30.一个类继承其他类，只能直接继承一个父类
31.但是实现类实现接口的话，可以实现多个接口
32.9.写法：先继承 再实现：extends Person implements TestInterface01,TestInterface02
33. */
34.class Student extends Person implements TestInterface01,TestInterface02 {
35.    @Override
36.    public void a() {
37.        System.out.println("---1");
38.    }
39. 
40.    @Override
41.    public void b(int num) {
42.        System.out.println("---2");
43.    }
44. 
45.    @Override
46.    public int c(String name) {
47.        return 100;
48.    }
49. 
50.    @Override
51.    public void e() {
52.        System.out.println("---3");
53.    }
54. 
55.    @Override
56.    public void f() {
57.        System.out.println("---4");
58.    }
59.}
60. 
61. 
62.class Test{
63.    //这是一个main方法，是程序的入口：
64.    public static void main(String[] args) {
65.        //10.接口不能创建对象：
66.        //TestInterface02 t = new TestInterface02();
67.        TestInterface02 t = new Student();//接口指向实现类 ---》多态
68. 
69.        //11.接口中常量如何访问：
70.        System.out.println(TestInterface01.NUM);
71.        System.out.println(Student.NUM);
72.        Student s = new Student();
73.        System.out.println(s.NUM);
74.        TestInterface01 t2 = new Student();
75.        System.out.println(t2.NUM);
76.    }
77.}
78. 
```

**【3】接口的作用是什么？** 

 

定义规则，只是跟抽象类不同地方在哪？它是接口不是类。

接口定义好规则之后，实现类负责实现即可。

 

**【4】** 

继承：子类对父类的继承

实现：实现类对接口的实现

 

手机  是不是  照相机 

继承：手机  extends 照相机   “is-a”的关系，手机是一个照相机 

 

上面的写法 不好： 

 

实现：  手机   implements  拍照功能  “has-a”的关系，手机具备照相的能力 

 

案例：飞机，小鸟，风筝

 定义一个接口： Flyable 

 

**【5】多态的应用场合：** 

（1）父类当做方法的形参，传入具体的子类的对象 

（2）父类当做方法的返回值，返回的是具体的子类的对象 

（3）接口当做方法的形参，传入具体的实现类的对象 

（4）接口当做方法的返回值，返回的是具体的实现类的对象 

 

**【6】接口和抽象类的区别：** 

![img](https://image.201068.xyz/assets/clip_image616.jpg)

#####   ![img](https://image.201068.xyz/assets/clip_image618.jpg) JDK1.8以后的接口新增内容

**在JDK1.8之前，接口中只有两部分内容：**
 （1）常量：固定修饰符：public static final
 （2）抽象方法：固定修饰符：public abstract 

 

**在JDK1.8之后，新增非抽象方法：** 

（1）被public default修饰的非抽象方法： 

注意1：default修饰符必须要加上，否则出错 

注意2：实现类中要是想重写接口中的非抽象方法，那么default修饰符必须不能加，否则出错。 

```
1.  public interface TestInterface {
2.      //常量：
3.      public static final int NUM= 10;
4.      //抽象方法：
5.      public abstract void a();
6.      //public default修饰的非抽象方法：
7.      public default void b(){
8.          System.out.println("-------TestInterface---b()-----");
9.      }
10.}
11.class Test implements TestInterface{
12.    public void c(){
13.        //用一下接口中的b方法：
14.        b();//可以
15.        //super.b();不可以
16.        TestInterface.super.b();//可以
17.    }
18.    @Override
19.    public void a() {
20.        System.out.println("重写了a方法");
21.    }
22. 
23.    @Override
24.    public void b() {
25. 
26.    }
27.}
```

 

（2）静态方法： 

注意1：static不可以省略不写 

注意2：静态方法不能重写 

```
1.  public interface TestInterface2 {
2.      //常量：
3.      public static final int NUM = 10;
4.      //抽象方法：
5.      public abstract  void a();
6.      //public default非抽象方法；
7.      public default void b(){
8.          System.out.println("-----TestInterface2---b");
9.      }
10.    //静态方法：
11.    public static void c(){
12.        System.out.println("TestInterface2中的静态方法");
13.    }
14.}
15. 
16.class Demo implements TestInterface2{
17.    @Override
18.    public void a() {
19.        System.out.println("重写了a方法");
20.    }
21.    public static void c(){
22.        System.out.println("Demo中的静态方法");
23.    }
24.}
25. 
26.class A {
27.    //这是一个main方法，是程序的入口：
28.    public static void main(String[] args) {
29.        Demo d = new Demo();
30.        d.c();
31.        Demo.c();
32.        TestInterface2.c();
33.    }
34.}
```

 

疑问：为什么要在接口中加入非抽象方法？？？

如果接口中只能定义抽象方法的话，那么我要是修改接口中的内容，那么对实现类的影响太大了，所有实现类都会受到影响。

现在在接口中加入非抽象方法，对实现类没有影响，想调用就去调用即可。

 

#### 内部类

##### 成员内部类

```
1.  package com.msb.test07;
2.   
3.  /**
4.   * 1.类的组成：属性，方法，构造器，代码块（普通块，静态块，构造块，同步块），内部类
5.   * 2.一个类TestOuter的内部的类SubTest叫内部类， 内部类 ：SubTest  外部类：TestOuter
6.   * 3.内部类：成员内部类 (静态的，非静态的) 和  局部内部类（位置：方法内，块内，构造器内）
7.   * 4.成员内部类:
8.   *      里面属性，方法，构造器等
9.   *      修饰符：private，default，protect，public，final,abstract
10. */
11.public class TestOuter {
12.    //非静态的成员内部类：
13.    public class D{
14.        int age = 20;
15.        String name;
16.        public void method(){
17.            //5.内部类可以访问外部类的内容
18.            /*System.out.println(age);
19.            a();*/
20.            int age = 30;
21. 
22.            //8.内部类和外部类属性重名的时候，如何进行调用：
23.            System.out.println(age);//30
24.            System.out.println(this.age);//20
25.            System.out.println(TestOuter.this.age);//10
26.        }
27.    }
28. 
29.    //静态成员内部类：
30.    static class E{
31.        public void method(){
32.            //6.静态内部类中只能访问外部类中被static修饰的内容
33.            /*System.out.println(age);
34.            a();*/
35.        }
36.    }
37.    //属性：
38.    int age = 10;
39.    //方法：
40.    public void a(){
41.        System.out.println("这是a方法");
42.        {
43.            System.out.println("这是一个普通块");
44.            class B{
45. 
46.            }
47.        }
48.        class A{
49. 
50.        }
51.        //7.外部类想要访问内部类的东西，需要创建内部类的对象然后进行调用
52.        D d = new D();
53.        System.out.println(d.name);
54.        d.method();
55. 
56.    }
57.    static{
58.        System.out.println("这是静态块");
59.    }
60.    {
61.        System.out.println("这是构造块");
62.    }
63.    //构造器：
64.    public TestOuter(){
65.        class C{
66. 
67.        }
68.    }
69. 
70.    public TestOuter(int age) {
71.        this.age = age;
72.    }
73.}
74. 
75.class Demo{
76.    //这是一个main方法，是程序的入口：
77.    public static void main(String[] args) {
78.        //创建外部类的对象：
79.        TestOuter to = new TestOuter();
80.        to.a();
81. 
82.        //9.创建内部类的对象：
83.        //静态的成员内部类创建对象：
84.        TestOuter.E e = new TestOuter.E();
85.        //非静态的成员内部类创建对象：
86.        //错误：TestOuter.D d = new TestOuter.D();
87.        TestOuter t = new TestOuter();
88.        TestOuter.D d = t.new D();
89. 
90.    }
91.}
92. 
```

 

 

##### 局部内部类

```
1.  package com.msb.test08;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class TestOuter {
7.      //1.在局部内部类中访问到的变量必须是被final修饰的
8.      public void method(){
9.          final int num = 10;
10.        class A{
11.            public void a(){
12.                //num = 20;
13.                System.out.println(num);
14.            }
15.        }
16.    }
17.    //2.如果类B在整个项目中只使用一次，那么就没有必要单独创建一个B类，使用内部类就可以了
18.    public Comparable method2(){
19.        class B implements Comparable{
20.            @Override
21.            public int compareTo(Object o) {
22.                return 100;
23.            }
24.        }
25.        return new B();
26.    }
27. 
28.    public Comparable method3(){
29.        //3.匿名内部类
30.        return new Comparable(){
31. 
32.            @Override
33.            public int compareTo(Object o) {
34.                return 200;
35.            }
36.        };
37.    }
38. 
39.    public void teat(){
40.        Comparable com = new Comparable(){
41. 
42.            @Override
43.            public int compareTo(Object o) {
44.                return 200;
45.            }
46.        };
47. 
48.        System.out.println(com.compareTo("abc"));
49.    }
50.}
51. 
```

 

 

#### 面向对象项目

 

##### 项目需求

![img](https://image.201068.xyz/assets/clip_image620.jpg)

 

##### 项目结构分析

![img](https://image.201068.xyz/assets/clip_image622.jpg)

 

##### 最终代码

匹萨父类： 

```
1.  package com.msb.test01;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   * 父类：匹萨类
6.   */
7.  public class Pizza {
8.      //属性
9.      private String name;//名称
10.    private int size;//大小
11.    private int price;//价格
12. 
13.    //方法
14. 
15.    public String getName() {
16.        return name;
17.    }
18. 
19.    public void setName(String name) {
20.        this.name = name;
21.    }
22. 
23.    public int getSize() {
24.        return size;
25.    }
26. 
27.    public void setSize(int size) {
28.        this.size = size;
29.    }
30. 
31.    public int getPrice() {
32.        return price;
33.    }
34. 
35.    public void setPrice(int price) {
36.        this.price = price;
37.    }
38. 
39.    //展示匹萨信息：
40.    public String showPizza(){
41.        return "匹萨的名字是："+name+"\n匹萨的大小是："+size+"寸\n匹萨的价格："+price+"元";
42.    }
43. 
44. 
45.    //构造器
46. 
47.    public Pizza() {
48.    }
49. 
50.    public Pizza(String name, int size, int price) {
51.        this.name = name;
52.        this.size = size;
53.        this.price = price;
54.    }
55.}
56. 
```

 

 

培根匹萨： 

 

```
1.  package com.msb.test01;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class BaconPizza extends Pizza {
7.      //属性：
8.      private int weight;
9.   
10.    public int getWeight() {
11.        return weight;
12.    }
13. 
14.    public void setWeight(int weight) {
15.        this.weight = weight;
16.    }
17. 
18.    //构造器：
19. 
20.    public BaconPizza() {
21.    }
22. 
23.    public BaconPizza(String name, int size, int price, int weight) {
24.        super(name, size, price);
25.        this.weight = weight;
26.    }
27. 
28.    //重写父类showPizza方法：
29. 
30.    @Override
31.    public String showPizza() {
32.        return super.showPizza()+"\n培根的克数是："+weight+"克";
33.    }
34.}
35. 
```

水果匹萨： 

```
1.  package com.msb.test01;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class FruitsPizza extends Pizza{
7.      //属性：
8.      private String burdening;
9.   
10.    public String getBurdening() {
11.        return burdening;
12.    }
13. 
14.    public void setBurdening(String burdening) {
15.        this.burdening = burdening;
16.    }
17. 
18.    //构造器：
19. 
20.    public FruitsPizza() {
21.    }
22. 
23.    public FruitsPizza(String name, int size, int price, String burdening) {
24.        super(name, size, price);
25.        this.burdening = burdening;
26.    }
27. 
28.    //重写父类showPizza方法：
29. 
30.    @Override
31.    public String showPizza() {
32.        return super.showPizza()+"\n你要加入的水果："+burdening;
33.    }
34.}
35. 
```

 

测试类： 

```
1.  public class Test {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) {
4.          //选择购买匹萨：
5.          Scanner sc = new Scanner(System.in);
6.          System.out.println("请选择你想要购买的匹萨（1.培根匹萨 2.水果匹萨）:");
7.          int choice = sc.nextInt();//选择
8.          //通过工厂获取匹萨：
9.          Pizza pizza = PizzaStore.getPizza(choice);
10.        System.out.println(pizza.showPizza());
11. 
12.    }
13.}
14. 
```

 

工厂类： 

```
1.  package com.msb.test01;
2.   
3.  import java.util.Scanner;
4.   
5.  /**
6.   * @Auther: msb-zhaoss
7.   */
8.  public class PizzaStore {
9.      public static Pizza getPizza(int choice){
10.        Scanner sc = new Scanner(System.in);
11.        Pizza p = null;
12.        switch (choice){
13.            case 1:
14.                {
15.                    System.out.println("请录入培根的克数：");
16.                    int weight = sc.nextInt();
17.                    System.out.println("请录入匹萨的大小：");
18.                    int size = sc.nextInt();
19.                    System.out.println("请录入匹萨的价格：");
20.                    int price = sc.nextInt();
21.                    //将录入的信息封装为培根匹萨的对象：
22.                    BaconPizza bp = new BaconPizza("培根匹萨",size,price,weight);
23.                    p = bp;
24.                }
25.                break;
26.            case 2:
27.                {
28.                    System.out.println("请录入你想要加入的水果：");
29.                    String burdening = sc.next();
30.                    System.out.println("请录入匹萨的大小：");
31.                    int size = sc.nextInt();
32.                    System.out.println("请录入匹萨的价格：");
33.                    int price = sc.nextInt();
34.                    //将录入的信息封装为水果匹萨的对象：
35.                    FruitsPizza fp = new FruitsPizza("水果匹萨",size,price,burdening);
36.                    p = fp;
37.                }
38.                break;
39.        }
40.        return p;
41.    }
42.}
43. 
```





# 第9章_异常

 

#### 习题的引入

【1】代码：

 

```
1.  public class Test {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) {
4.          //实现一个功能：键盘录入两个数，求商：
5.          Scanner sc = new Scanner(System.in);
6.          System.out.println("请录入第一个数：");
7.          int num1 = sc.nextInt();
8.          System.out.println("请录入第二个数：");
9.          int num2 = sc.nextInt();
10.        System.out.println("商："+num1/num2);
11. 
12.    }
13.}
```

运行结果：

![img](https://image.201068.xyz/assets/clip_image624.jpg)

测试过程发现问题：

录入的数据应为int类型，但是录入非int类型数据的时候，出异常： 

![img](https://image.201068.xyz/assets/clip_image626.jpg)

除数为0的时候： 

![img](https://image.201068.xyz/assets/clip_image628.jpg)

异常：Exception：在程序的运行过程中，发生了不正常的现象，阻止了程序的运行，我们称之为发生异常。 

 

#### 通过if-else解决异常

```
1.  package com.msb.test01;
2.   
3.  import java.util.Scanner;
4.   
5.  /**
6.   * @Auther: msb-zhaoss
7.   */
8.  public class Test {
9.      //这是一个main方法，是程序的入口：
10.    public static void main(String[] args) {
11.        //实现一个功能：键盘录入两个数，求商：
12.        Scanner sc = new Scanner(System.in);
13.        System.out.println("请录入第一个数：");
14.        if(sc.hasNextInt()){
15.            int num1 = sc.nextInt();
16.            System.out.println("请录入第二个数：");
17.            if(sc.hasNextInt()){
18.                int num2 = sc.nextInt();
19.                if(num2 == 0){
20.                    System.out.println("对不起，除数不能为0");
21.                }else{
22.                    System.out.println("商："+num1/num2);
23.                }
24.            }else{
25.                System.out.println("对不起，你录入的不是int类型的数据！");
26.            }
27.        }else{
28.            System.out.println("对不起，你录入的不是int类型的数据！");
29.        }
30.    }
31.}
32. 
```

 

用if-else堵漏洞的缺点： 

（1）代码臃肿，业务代码和处理异常的代码混在一起。 

（2）可读性差 

（3）程序员需要花费大量的经历来维护这个漏洞 

（4）程序员很难堵住所有的漏洞。 



#### try-catch

【1】基于if-else处理异常缺点太多，所以java中专门出了一个异常处理机制： 

“异常三连”  try-catch-finally 

【2】异常出现了以后怎么看： 

![img](https://image.201068.xyz/assets/clip_image630.jpg)

【3】捕获异常： try-catch 

对应代码：

```
1.  public class Test2 {
2.      public static void main(String[] args) {
3.          //实现一个功能：键盘录入两个数，求商：
4.          try{
5.              Scanner sc = new Scanner(System.in);
6.              System.out.println("请录入第一个数：");
7.              int num1 = sc.nextInt();
8.              System.out.println("请录入第二个数：");
9.              int num2 = sc.nextInt();
10.            System.out.println("商："+num1/num2);
11.        }catch(Exception ex){
12.            System.out.println("对不起，程序出现异常！");
13.        }
14. 
15.        System.out.println("----谢谢你使用计算器111");
16.        System.out.println("----谢谢你使用计算器222");
17.        System.out.println("----谢谢你使用计算器333");
18.        System.out.println("----谢谢你使用计算器444");
19.        System.out.println("----谢谢你使用计算器555");
20.        System.out.println("----谢谢你使用计算器666");
21.    }
22.}
```

 

原理：

把可能出现异常的代码放入try代码块中，然后将异常封装为对象，被catch后面的()中的那个异常对象接收，接收以后：执行catch后面的{}里面的代码，然后try-catch后面的代码，该怎么执行就怎么执行。 

 

详细说一下：

（1）try中没有异常，catch中代码不执行。

（2）try中有异常，catch进行捕获：

如果catch中异常类型和你出的异常类型匹配的话：走catch中的代码--》进行捕获 

如果catch中异常类型和你出的异常类型不匹配的话：不走catch中的代码--》没有捕获成功，程序相当于遇到异常了，中断了，后续代码不执行 

 

注意：

 

（1）try中如果出现异常，然后用catch捕获成功的话，那么try中后续的代码是不会执行的。 

（2）如果catch捕获异常成功，那么try-catch后面的代码该执行还是执行没有影响。

 

#### catch中如何处理异常

```
1.  package com.msb.test01;
2.   
3.  import java.util.Scanner;
4.   
5.  /**
6.   * @Auther: msb-zhaoss
7.   */
8.  public class Test3 {
9.      public static void main(String[] args) {
10.        //实现一个功能：键盘录入两个数，求商：
11.        try{
12.            Scanner sc = new Scanner(System.in);
13.            System.out.println("请录入第一个数：");
14.            int num1 = sc.nextInt();
15.            System.out.println("请录入第二个数：");
16.            int num2 = sc.nextInt();
17.            System.out.println("商："+num1/num2);
18.        }catch(Exception ex){
19.            //第一种处理：什么都不写，什么都不做
20. 
21.            //第二种处理：输出自定义异常信息
22.            //System.out.println("对不起，你的代码有问题！");
23. 
24.            //第三种处理：打印异常信息：
25.            /*(1)调用toString方法，显示异常的类名（全限定路径）*/
26.            /*System.out.println(ex);
27.            System.out.println(ex.toString());*/
28.            /*(2)显示异常描述信息对应的字符串，如果没有就显示null
29.            System.out.println(ex.getMessage());*/
30.            /*(3)显示异常的堆栈信息：将异常信息捕获以后，在控制台将异常的效果给我们展示出来，方便我们查看异常*/
31.           /* ex.printStackTrace();*/
32. 
33.            //第四种处理：抛出异常：
34.            throw ex;
35.        }
36. 
37.        System.out.println("----谢谢你使用计算器111");
38.    }
39.}
40. 
```

#### try-catch-finally

**【1】在什么情况下，try-catch后面的代码不执行？** 

（1）throw抛出异常的情况 

（2）catch中没有正常的进行异常捕获 

（3）在try中遇到return 

 

**【2】怎么样才可以将 try-catch后面的代码  必须执行？** 

只要将必须执行的代码放入finally中，那么这个代码无论如何一定执行。 

 

**【3】return和finally执行顺序？**

先执行finally最后执行return 

 

**【4】什么代码会放在finally中呢？** 

关闭数据库资源，关闭IO流资源，关闭socket资源。 

 

**【5】有一句话代码很厉害，它可以让finally中代码不执行!** 

[System.exit(0);//终止当前的虚拟机执行](System.exit(0);/终止当前的虚拟机执行) 

 

代码：

```
1.  package com.msb.test01;
2.   
3.  import java.util.Scanner;
4.   
5.  /**
6.   * @Auther: msb-zhaoss
7.   */
8.  public class Test3 {
9.      public static void main(String[] args) {
10.        //实现一个功能：键盘录入两个数，求商：
11.        try{
12.            Scanner sc = new Scanner(System.in);
13.            System.out.println("请录入第一个数：");
14.            int num1 = sc.nextInt();
15.            System.out.println("请录入第二个数：");
16.            int num2 = sc.nextInt();
17.            System.out.println("商："+num1/num2);
18.            System.exit(0);//终止当前的虚拟机执行
19.            return;
20.        }catch(ArithmeticException ex){
21.            //throw ex;
22.        }finally {
23.            System.out.println("----谢谢你使用计算器111");
24.        }
25. 
26. 
27.    }
28.}
29. 
```

 

 

#### 多重catch

【1】try中出现异常以后，将异常类型跟catch后面的类型依次比较，按照代码的顺序进行比对，执行第一个与异常类型匹配的catch语句 

【2】一旦执行其中一条catch语句之后，后面的catch语句就会被忽略了！ 

【3】在安排catch语句的顺序的时候，一般会将特殊异常放在前面（并列），一般化的异常放在后面。

先写子类异常，再写父类异常。

【4】在JDK1.7以后，异常新处理方式：可以并列用|符号连接： 

![img](https://image.201068.xyz/assets/clip_image632.jpg)

 

```
1.  package com.msb.test01;
2.   
3.  import java.util.InputMismatchException;
4.  import java.util.Scanner;
5.   
6.  /**
7.   * @Auther: msb-zhaoss
8.   */
9.  public class Test4 {
10.    public static void main(String[] args) {
11.        Integer
12.        //实现一个功能：键盘录入两个数，求商：
13.        try{
14.            Scanner sc = new Scanner(System.in);
15.            System.out.println("请录入第一个数：");
16.            int num1 = sc.nextInt();
17.            System.out.println("请录入第二个数：");
18.            int num2 = sc.nextInt();
19.            System.out.println("商："+num1/num2);
20.        }catch(ArithmeticException ex){
21.            System.out.println("对不起，除数不可以为0");
22.        }catch(InputMismatchException ex){
23.            System.out.println("对不起，你录入的数据不是int类型的数据");
24.        }catch(Exception ex){
25.            System.out.println("对不起，你的程序出现异常");
26.        }finally {
27.            System.out.println("----谢谢你使用计算器111");
28.        }
29.    }
30.}
31. 
```

#### 异常的分类

【1】层次结构：

![img](https://image.201068.xyz/assets/clip_image634.jpg)

注意：程序中语法错误，逻辑错误  都不属于上面的Error，Exception

 

【2】运行时异常： 

```
1.  public class Test5 {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) {
4.          //运行时异常：
5.          int[] arr = {1,2,3};
6.          System.out.println(arr.length);
7.          /*int[] arr2 = null;
8.          System.out.println(arr2.length);*/
9.          System.out.println(arr[10]);
10.    }
11.}
```

【3】检查异常： 

处理方式1：try-catch嵌套try-catch

```
1.  public class Test6 {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) {
4.          //检查异常：
5.          try {
6.              try {
7.                  Class.forName("com.msb.test01.Test").newInstance();
8.              } catch (InstantiationException e) {
9.                  e.printStackTrace();
10.            } catch (IllegalAccessException e) {
11.                e.printStackTrace();
12.            }
13.        } catch (ClassNotFoundException e) {
14.            e.printStackTrace();
15.        }
16.    }
17.}
```

 

 

 

处理方式2：多重catch 

```
1.  public class Test6 {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) {
4.          //检查异常：
5.          try {
6.              Class.forName("com.msb.test01.Test").newInstance();
7.          } catch (ClassNotFoundException | InstantiationException | IllegalAccessException e) {
8.              e.printStackTrace();
9.          }
10.    }
11.}
```

处理方式3：throws 

```
1.  public class Test6 {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) throws ClassNotFoundException, IllegalAccessException, InstantiationException {
4.          //检查异常：
5.          Class.forName("com.msb.test01.Test").newInstance();
6.      }
7.  }
```

#### throw和throws的区别

```
1.  package com.msb.test01;
2.   
3.  import java.util.Scanner;
4.   
5.  /**
6.   * @Auther: msb-zhaoss
7.   */
8.  public class Test7 {
9.      //这是一个main方法，是程序的入口：
10.    public static void main(String[] args) throws Exception {
11.        //实现一个功能：两个数相除，当除数为0的时候，程序出现异常。
12.        /*try {
13.            devide();
14.        } catch (Exception e) {
15.            e.printStackTrace();
16.        }*/
17.        devide();
18.    }
19.    public static void devide() throws Exception {
20.        Scanner sc = new Scanner(System.in);
21.        System.out.println("请录入第一个数：");
22.        int num1 = sc.nextInt();
23.        System.out.println("请录入第二个数：");
24.        int num2 = sc.nextInt();
25.        if(num2 == 0 ){//除数为0 ，制造异常。
26.            //制造运行时异常：
27.            /*throw new RuntimeException();*/
28.            //制造检查异常：
29.            /*try {
30.                throw new Exception();
31.            } catch (Exception e) {
32.                e.printStackTrace();
33.            }*/
34.            throw new Exception();
35.        }else{
36.            System.out.println("商："+num1/num2);
37.        }
38.    }
39.}
40. 
```

 

总结：

throw和throws的区别：

（1）位置不同： 

throw：方法内部 

throws: 方法的签名处，方法的声明处

 

（2）内容不同： 

throw+异常对象（检查异常，运行时异常） 

throws+异常的类型（可以多个类型，用，拼接） 

 

（3）作用不同： 

throw：异常出现的源头，制造异常。 

throws:在方法的声明处，告诉方法的调用者，这个方法中可能会出现我声明的这些异常。然后调用者对这个异常进行处理：

要么自己处理要么再继续向外抛出异常

##### 练习：

```
1.  package com.msb.test02;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Student {
7.      private String name;
8.      private int age;
9.      private String sex;
10. 
11.    public String getName() {
12.        return name;
13.    }
14. 
15.    public void setName(String name) {
16.        this.name = name;
17.    }
18. 
19.    public int getAge() {
20.        return age;
21.    }
22. 
23.    public void setAge(int age) {
24.        this.age = age;
25.    }
26. 
27.    public String getSex() {
28.        return sex;
29.    }
30. 
31.    public void setSex(String sex) throws Exception {
32.        if(sex.equals("男")||sex.equals("女")){
33.            this.sex = sex;
34.        }else{//非男非女
35.            //解决办法1：
36.            /*this.sex = "男";*/
37.            //解决办法2：给个友好型提示，但是打印结果为默认的null效果
38.            /*System.out.println("对不起，你的性别错误了");*/
39.            //解决办法3：
40.            //制造运行时异常：
41.            /*throw new RuntimeException("性别不对！");*/
42.            //制造检查异常
43.            /*try {
44.                throw new Exception();
45.            } catch (Exception e) {
46.                e.printStackTrace();
47.            }*/
48.            throw new Exception();
49.        }
50.    }
51. 
52.    @Override
53.    public String toString() {
54.        return "Student{" +
55.                "name='" + name + '\'' +
56.                ", age=" + age +
57.                ", sex='" + sex + '\'' +
58.                '}';
59.    }
60. 
61.    public Student() {
62.    }
63. 
64.    public Student(String name, int age, String sex) {
65.        this.name = name;
66.        this.age = age;
67.        //this.sex = sex;
68.        try {
69.            this.setSex(sex);
70.        } catch (Exception e) {
71.            e.printStackTrace();
72.        }
73.    }
74.}
75. 
```

 

```
1.  package com.msb.test02;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Test {
7.      //这是一个main方法，是程序的入口：
8.      public static void main(String[] args) {
9.          //创建一个Student的对象：
10.        /*Student s = new Student();
11.        s.setName("菲菲");
12.        s.setAge(19);
13.        try {
14.            s.setSex("asdfasdfasdf");
15.        } catch (Exception e) {
16.            e.printStackTrace();
17.        }
18.        System.out.println(s);*/
19. 
20.        Student s2 = new Student("娜娜",21,"asdfasdfasdf");
21.        System.out.println(s2);
22.    }
23.}
24. 
```

 

 

#### 重载和重写的异常

![img](https://image.201068.xyz/assets/clip_image636.jpg)

 

【1】重载： 

```
1.  public class Demo {
2.      public void a() throws Exception{
3.   
4.      }
5.      public void a(int age) throws ArithmeticException{
6.   
7.      }
8.  }
9.   
```

【2】重写： 

![img](https://image.201068.xyz/assets/clip_image638.jpg)

![img](https://image.201068.xyz/assets/clip_image640.jpg)

 

子类 <= 父类 

#### 自定义异常

自定义的异常可以继承：运行时异常 

```
1.  public class MyException extends RuntimeException {
2.      
3.      static final long serialVersionUID = -70348971907L;
4.      
5.      public MyException(){
6.   
7.      }
8.      public MyException(String msg){
9.          super(msg);
10.    }
11.}
```

也可以继承检查异常：

```
1.  public class MyException extends Exception {
2.   
3.      static final long serialVersionUID = -70348971907L;
4.   
5.      public MyException(){
6.   
7.      }
8.      public MyException(String msg){
9.          super(msg);
10.    }
11.}
12. 
```

如果继承的是运行时异常，那么在使用的时候无需额外处理

如果继承的是检查异常，那么使用的时候需要try-catch捕获或者throws向上抛 

 

# 第10章_常用类

#### 包装类

##### 引入

【1】什么是包装类：

以前定义变量，经常使用基本数据类型，

对于基本数据类型来说，它就是一个数，加点属性，加点方法，加点构造器，

将基本数据类型对应进行了一个封装，产生了一个新的类，---》包装类。 

int,byte.....--->基本数据类型 

包装类--->引用数据类型 

 

【2】对应关系： 

基本数据类型      对应的包装类         继承关系 

byte              Byte              ---》Number---》Object 

short             Short             ---》Number---》Object 

int               Integer            ---》Number---》Object 

long              Long             ---》Number---》Object 

float              Float             ---》Number---》Object 

double            Double            ---》Number---》Object 

char              Character          Object 

boolean           Boolean           Object 

 

【3】已经有基本数据类型了，为什么要封装为包装类？ 

（1）java语言 面向对象的语言，最擅长的操作各种各样的类。 

（2）以前学习装数据的---》数组，int[] String[]  double[]  Student[] 

   以后学习的装数据的---》集合，有一个特点，只能装引用数据类型的数据 

 

【4】是不是有了包装类以后就不用基本数据类型了？ 

不是。

##### Integer

【1】直接使用，无需导包：

![img](https://image.201068.xyz/assets/clip_image642.jpg)

【2】类的继承关系： 

![img](https://image.201068.xyz/assets/clip_image644.jpg)

 

【3】实现接口： 

![img](https://image.201068.xyz/assets/clip_image646.jpg)

 

【4】这个类被final修饰，那么这个类不能有子类，不能被继承： 

![img](https://image.201068.xyz/assets/clip_image648.jpg)

 

【5】包装类是对基本数据类型的封装： 对int类型封装产生了Integer 

![img](https://image.201068.xyz/assets/clip_image650.jpg)

 

【6】类的历史： 

![img](https://image.201068.xyz/assets/clip_image652.jpg)

 

【7】属性： 

```
1.  //属性：
2.          System.out.println(Integer.MAX_VALUE);
3.          System.out.println(Integer.MIN_VALUE);
4.          //“物极必反”原理：
5.          System.out.println(Integer.MAX_VALUE+1);
6.          System.out.println(Integer.MIN_VALUE-1);
```

【8】构造器（发现没有空参构造器） 

（1）int类型作为构造器的参数： 

```
1.  Integer i1 = new Integer(12);
```

 

![img](https://image.201068.xyz/assets/clip_image654.jpg)

 

（2）String类型作为构造器的参数： 

```
1.  Integer i2 = new Integer("12");
2.          Integer i3 = new Integer("abcdef");
```

 

![img](https://image.201068.xyz/assets/clip_image656.jpg)

 

【9】包装类特有的机制：自动装箱  自动拆箱： 

```
1.  //自动装箱：int--->Integer
2.          Integer i = 12;
3.          System.out.println(i);
4.          //自动拆箱：Integer--->int
5.          Integer i2 = new Integer(12);
6.          int num = i2;
7.          System.out.println(num);
```

（1）自动装箱  自动拆箱 是从JDK1.5以后新出的特性

（2）自动装箱  自动拆箱 ：将基本数据类型和包装类进行快速的类型转换。

验证：

![img](https://image.201068.xyz/assets/clip_image658.jpg)

可以自定打断点测试是否走入valueOf方法中： 

![img](https://image.201068.xyz/assets/clip_image660.jpg)

【10】常用方法： 

 

valueOf方法的底层： 

![img](https://image.201068.xyz/assets/clip_image662.jpg)

 

```
1.  package com.msb;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Test04 {
7.      //这是一个main方法，是程序的入口：
8.      public static void main(String[] args) {
9.          //compareTo：只返回三个值：要么是0,-1,1
10.        Integer i1 = new Integer(6);
11.        Integer i2 = new Integer(12);
12.        System.out.println(i1.compareTo(i2));// return (x < y) ? -1 : ((x == y) ? 0 : 1);
13.        //equals:Integer对Object中的equals方法进行了重写，比较的是底层封装的那个value的值。
14.        //Integer对象是通过new关键字创建的对象：
15.        Integer i3 = new Integer(12);
16.        Integer i4 = new Integer(12);
17.        System.out.println(i3 == i4);//false 因为==比较的是两个对象的地址
18.        boolean flag = i3.equals(i4);
19.        System.out.println(flag);
20. 
21.        //Integer对象通过自动装箱来完成：
22.        Integer i5 = 130;
23.        Integer i6 = 130;
24.        System.out.println(i5.equals(i6));//true
25.        System.out.println(i5 == i6);
26.        /*
27.        如果自动装箱值在-128~127之间，那么比较的就是具体的数值
28.        否在，比较的就是对象的地址
29.         */
30. 
31.        //intValue() :作用将Integer--->int
32.        Integer i7 = 130;
33.        int i = i7.intValue();
34.        System.out.println(i);
35. 
36.        //parseInt(String s) :String--->int:
37.        int i8 = Integer.parseInt("12");
38.        System.out.println(i8);
39. 
40.        //toString:Integer--->String
41.        Integer i10 = 130;
42.        System.out.println(i10.toString());
43. 
44.    }
45.}
46. 
```

 

#### 日期相关的类

##### java.util.Date

```
1.  package com.msb.test02;
2.   
3.  import java.util.Date;
4.   
5.  /**
6.   * @Auther: msb-zhaoss
7.   */
8.  public class Test {
9.      //这是一个main方法，是程序的入口：
10.    public static void main(String[] args) {
11.        //java.util.Date:
12.        Date d = new Date();
13.        System.out.println(d);
14.        System.out.println(d.toString());
15.        System.out.println(d.toGMTString());//过期方法，过时方法，废弃方法。
16.        System.out.println(d.toLocaleString());
17. 
18.        System.out.println(d.getYear());//120+1900=2020
19.        System.out.println(d.getMonth());//5 :返回的值在 0 和 11 之间，值 0 表示 1 月。
20.        //返回自 1970 年 1 月 1 日 00:00:00 GMT 以来此 Date 对象表示的毫秒数。
21.        System.out.println(d.getTime());//1592055964263
22.        System.out.println(System.currentTimeMillis());
23.        /*
24.        （1）疑问：以后获取时间差用：getTime()还是currentTimeMillis()
25.        答案：currentTimeMillis()--》因为这个方法是静态的，可以类名.方法名直接调用
26.        （2）public static native long currentTimeMillis();
27.        本地方法
28.        为什么没有方法体？因为这个方法的具体实现不是通过java写的。
29.        （3）这个方法的作用：
30.        一般会去衡量一些算法所用的时间
31.         */
32.        long startTime = System.currentTimeMillis();
33.        for (int i = 0; i < 100000; i++) {
34.            System.out.println(i);
35.        }
36.        long endTime = System.currentTimeMillis();
37.        System.out.println(endTime-startTime);
38.    }
39.}
40. 
```

 

##### java.sql.Date

```
1.  package com.msb.test02;
2.   
3.  import java.sql.Date;
4.   
5.  /**
6.   * @Auther: msb-zhaoss
7.   */
8.  public class Test02 {
9.      //这是一个main方法，是程序的入口：
10.    public static void main(String[] args) {
11.        //java.sql.Date:
12.        Date d = new Date(1592055964263L);
13.        System.out.println(d);
14.        /*
15.        (1)java.sql.Date和java.util.Date的区别：
16.        java.util.Date：年月日  时分秒
17.        java.sql.Date：年月日
18.        (2)java.sql.Date和java.util.Date的联系：
19.        java.sql.Date(子类) extends java.util.Date （父类）
20.         */
21. 
22.        //java.sql.Date和java.util.Date相互转换：
23.        //【1】util--->sql:
24.        java.util.Date date = new Date(1592055964263L);//创建util.Date的对象
25.        //方式1：向下转型
26.        Date date1 = (Date) date;
27.        /*
28.        父类：Animal 子类：Dog
29.        Animal an = new Dog();
30.        Dog d = (Dog)an;
31.         */
32.        //方式2：利用构造器
33.        Date date2 = new Date(date.getTime());
34. 
35. 
36.        //【2】sql-->util:
37.        java.util.Date date3 = d;
38. 
39.        //[3]String--->sql.Date:
40.        Date date4 =  Date.valueOf("2019-3-8");
41. 
42.    }
43.}
44. 
```

 

 

##### SimpleDateFormat

【1】String---》java.util.Date 类型转换： 

分解：

（1）String--->java.sql.Date 

（2）java.sql.Date--->java.util.Date 

 

```
1.  public class Test04 {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) {
4.          //（1）String--->java.sql.Date
5.          java.sql.Date date = java.sql.Date.valueOf("2015-9-24");
6.          //（2）java.sql.Date--->java.util.Date
7.          java.util.Date date2 = date;
8.          System.out.println(date2.toString());
9.      }
10.}
```

上面的代码有局限性，字符串的格式只能是年-月-日拼接的形式，换成其它类型，就会出现异常： 

![img](https://image.201068.xyz/assets/clip_image664.jpg)

 

【2】引入新的类：SimpleDateFormat 

```
1.  package com.msb.test02;
2.   
3.  import java.text.DateFormat;
4.  import java.text.ParseException;
5.  import java.text.SimpleDateFormat;
6.  import java.util.Date;
7.   
8.  /**
9.   * @Auther: msb-zhaoss
10. */
11.public class Test05 {
12.    //这是一个main方法，是程序的入口：
13.    public static void main(String[] args) {
14.        //日期转换：
15.        //SimpleDateFormat(子类) extends DateFormat（父类是一个抽象类）
16.        //格式化的标准已经定义好了：
17.        DateFormat df = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
18.        //String--->Date
19.        try {
20.            Date d = df.parse("2019-4-6 12:23:54");
21.            System.out.println(d);
22.        } catch (ParseException e) {
23.            e.printStackTrace();
24.        }
25.        //Date--->String
26.        String format = df.format(new Date());
27.        System.out.println(format);
28. 
29.        Date date = new Date();
30.        System.out.println(date.toString());
31.        System.out.println(date.toGMTString());
32.        System.out.println(date.toLocaleString());
33.    }
34.}
35. 
```

 

【3】日期格式： 

![img](https://image.201068.xyz/assets/clip_image666.jpg)

 

 

##### Calendar

```
1.  package com.msb.test02;
2.   
3.  import java.util.Calendar;
4.  import java.util.GregorianCalendar;
5.   
6.  /**
7.   * @Auther: msb-zhaoss
8.   */
9.  public class Test06 {
10.    //这是一个main方法，是程序的入口：
11.    public static void main(String[] args) {
12.        //Calendar是一个抽象类，不可以直接创建对象
13.        //GregorianCalendar()子类 extends Calendar（父类是一个抽象类）
14.        Calendar cal = new GregorianCalendar();
15.        Calendar cal2 = Calendar.getInstance();
16.        System.out.println(cal);
17. 
18.        //常用的方法：
19.        // get方法，传入参数：Calendar中定义的常量
20.        System.out.println(cal.get(Calendar.YEAR));
21.        System.out.println(cal.get(Calendar.MONTH));
22.        System.out.println(cal.get(Calendar.DATE));
23.        System.out.println(cal.get(Calendar.DAY_OF_WEEK));
24.        System.out.println(cal.getActualMaximum(Calendar.DATE));//获取当月日期的最大天数
25.        System.out.println(cal.getActualMinimum(Calendar.DATE));//获取当月日期的最小天数
26. 
27.        // set方法：可以改变Calendar中的内容
28.        cal.set(Calendar.YEAR,1990);
29.        cal.set(Calendar.MONTH,3);
30.        cal.set(Calendar.DATE,16);
31.        System.out.println(cal);
32. 
33.        //String--->Calendar:
34.        //分解：
35.        //String--->java.sql.Date:
36.        java.sql.Date date = java.sql.Date.valueOf("2020-4-5");
37.        //java.sql.Date-->Calendar:
38.        cal.setTime(date);
39.        System.out.println(cal);
40.    }
41.}
42. 
```

###### 练习

需求： 

![img](https://image.201068.xyz/assets/clip_image668.jpg)

 

```
1.  package com.msb.test02;
2.   
3.  import java.util.Calendar;
4.  import java.util.Scanner;
5.   
6.  /**
7.   * @Auther: msb-zhaoss
8.   */
9.  public class Test08 {
10.    //这是一个main方法，是程序的入口：
11.    public static void main(String[] args) {
12. 
13.        //录入日期的String：
14.        Scanner sc = new Scanner(System.in);
15.        System.out.print("请输入你想要查看的日期：（提示：请按照例如2012-5-6的格式书写）");
16.        String strDate = sc.next();
17.        /*System.out.println(strDate);*/
18.        //String--->Calendar:
19.        //String-->Date:
20.        java.sql.Date date = java.sql.Date.valueOf(strDate);
21.        //Date--->Calendar:
22.        Calendar cal = Calendar.getInstance();
23.        cal.setTime(date);
24. 
25.        //后续操作：
26.        //星期提示：
27.        System.out.println("日\t一\t二\t三\t四\t五\t六\t");
28. 
29.        //获取本月的最大天数：
30.        int maxDay = cal.getActualMaximum(Calendar.DATE);
31.        //获取当前日期中的日：
32.        int nowDay = cal.get(Calendar.DATE);
33. 
34.        //将日期调为本月的1号：
35.        cal.set(Calendar.DATE,1);
36.        //获取这个一号是本周的第几天：
37.        int num = cal.get(Calendar.DAY_OF_WEEK);
38.        /*System.out.println(num);*/
39.        //前面空出来的天数为：
40.        int day = num - 1;
41.        //引入一个计数器：
42.        int count = 0;//计数器最开始值为0
43.        //在日期前将空格打印出来：
44.        for (int i = 1; i <= day; i++) {
45.            System.out.print("\t");
46.        }
47.        //空出来的日子也要放入计数器：
48.        count = count + day;
49.        //遍历：从1号开始到maxDay号进行遍历：
50.        for (int i = 1; i <= maxDay ; i++) {
51. 
52.            if(i == nowDay){//如果遍历的i和当前日子一样的话，后面多拼一个*
53.                System.out.print(i+"*"+"\t");
54.            }else{
55.                System.out.print(i+"\t");
56.            }
57.            count++;//每在控制台输出一个数字，计数器做加1操作
58.            if(count%7 == 0){//当计数器的个数是7的倍数的时候，就换行操作
59.                System.out.println();
60.            }
61.        }
62. 
63. 
64.    }
65.}
66. 
```

##### JDK1.8新增日期时间API

###### 引入

JDK1.0中使用java.util.Date类  --》第一批日期时间API 

JDK1.1引入Calendar类  --》第二批日期时间API 

缺陷：

可变性 : 像日期和时间这样的类应该是不可变的。 

偏移性 : Date中 的年份是从1900开始的，而月份都从0开始。 

格式化 : 格式化只对Date有用，Calendar则不行。

 

JDK1.8新增日期时间API --》第三批日期时间API 

###### LocalDate/LocalTime/LocalDateTime

```
1.  package com.msb.test02;
2.   
3.  import java.time.LocalDate;
4.  import java.time.LocalDateTime;
5.  import java.time.LocalTime;
6.   
7.  /**
8.   * @Auther: msb-zhaoss
9.   */
10.public class Test09 {
11.    //这是一个main方法，是程序的入口：
12.    public static void main(String[] args) {
13.        //1.完成实例化：
14.        //方法1：now()--获取当前的日期，时间，日期+时间
15.        LocalDate localDate = LocalDate.now();
16.        System.out.println(localDate);
17.        LocalTime localTime = LocalTime.now();
18.        System.out.println(localTime);
19.        LocalDateTime localDateTime = LocalDateTime.now();
20.        System.out.println(localDateTime);
21.        //方法2：of()--设置指定的日期，时间，日期+时间
22.        LocalDate of = LocalDate.of(2010, 5, 6);
23.        System.out.println(of);
24.        LocalTime of1 = LocalTime.of(12, 35, 56);
25.        System.out.println(of1);
26.        LocalDateTime of2 = LocalDateTime.of(1890, 12, 23, 13, 24, 15);
27.        System.out.println(of2);
28. 
29.        //LocalDate,LocalTime用的不如LocalDateTime多
30.        //下面讲解用LocalDateTime：
31.        //一些列常用的get***
32.        System.out.println(localDateTime.getYear());//2020
33.        System.out.println(localDateTime.getMonth());//JUNE
34.        System.out.println(localDateTime.getMonthValue());//6
35.        System.out.println(localDateTime.getDayOfMonth());//14
36.        System.out.println(localDateTime.getDayOfWeek());//SUNDAY
37.        System.out.println(localDateTime.getHour());//22
38.        System.out.println(localDateTime.getMinute());//22
39.        System.out.println(localDateTime.getSecond());//6
40. 
41.        //不是set方法，叫with
42.        //体会：不可变性
43.        LocalDateTime localDateTime2 = localDateTime.withMonth(8);
44.        System.out.println(localDateTime);
45.        System.out.println(localDateTime2);
46. 
47.        //提供了加减的操作：
48.        //加：
49.        LocalDateTime localDateTime1 = localDateTime.plusMonths(4);
50.        System.out.println(localDateTime);
51.        System.out.println(localDateTime1);
52.        //减：
53.        LocalDateTime localDateTime3 = localDateTime.minusMonths(5);
54.        System.out.println(localDateTime);
55.        System.out.println(localDateTime3);
56. 
57. 
58.    }
59.}
60. 
```

###### DateTimeFormatter

```
1.  package com.msb.test02;
2.   
3.  import java.time.LocalDateTime;
4.  import java.time.format.DateTimeFormatter;
5.  import java.time.format.FormatStyle;
6.  import java.time.temporal.TemporalAccessor;
7.   
8.  /**
9.   * @Auther: msb-zhaoss
10. */
11.public class Test10 {
12.    //这是一个main方法，是程序的入口：
13.    public static void main(String[] args) {
14.        //格式化类：DateTimeFormatter
15. 
16.        //方式一:预定义的标准格式。如: ISO_LOCAL_DATE_TIME;ISO_LOCAL_DATE;IS0_LOCAL_TIME
17.        DateTimeFormatter df1 = DateTimeFormatter.ISO_LOCAL_DATE_TIME;
18.        //df1就可以帮我们完成LocalDateTime和String之间的相互转换：
19.        //LocalDateTime-->String:
20.        LocalDateTime now = LocalDateTime.now();
21.        String str = df1.format(now);
22.        System.out.println(str);//2020-06-15T15:02:51.29
23. 
24.        //String--->LocalDateTime
25.        TemporalAccessor parse = df1.parse("2020-06-15T15:02:51.29");
26.        System.out.println(parse);
27. 
28. 
29.        //方式二:本地化相关的格式。如: oflocalizedDateTime()
30.        //参数：FormatStyle.LONG / FormatStyle.MEDIUM / FormatStyle.SHORT
31.        //FormatStyle.LONG :2020年6月15日 下午03时17分13秒
32.        //FormatStyle.MEDIUM: 2020-6-15 15:17:42
33.        //FormatStyle.SHORT:20-6-15 下午3:18
34.        DateTimeFormatter df2 = DateTimeFormatter.ofLocalizedDateTime(FormatStyle.SHORT);
35.        //LocalDateTime-->String:
36.        LocalDateTime now1 = LocalDateTime.now();
37.        String str2 = df2.format(now1);
38.        System.out.println(str2);
39. 
40.        //String--->LocalDateTime
41.        TemporalAccessor parse1 = df2.parse("20-6-15 下午3:18");
42.        System.out.println(parse1);
43. 
44.        //方式三: 自定义的格式。如: ofPattern( "yyyy-MM-dd hh:mm:ss") ---》重点，以后常用
45.        DateTimeFormatter df3 = DateTimeFormatter.ofPattern("yyyy-MM-dd hh:mm:ss");
46.        //LocalDateTime-->String:
47.        LocalDateTime now2 = LocalDateTime.now();
48.        String format = df3.format(now2);
49.        System.out.println(format);//2020-06-15 03:22:03
50.        //String--->LocalDateTime
51.        TemporalAccessor parse2 = df3.parse("2020-06-15 03:22:03");
52.        System.out.println(parse2);
53. 
54.    }
55.}
56. 
```

 

 

#### Math类

【1】直接使用，无需导包：

![img](https://image.201068.xyz/assets/clip_image670.jpg)

 

【2】final修饰类，这个类不能被继承： 

![img](https://image.201068.xyz/assets/clip_image672.jpg)

 

【3】构造器私有化，不能创建Math类的对象： 

![img](https://image.201068.xyz/assets/clip_image674.jpg)

不能：

![img](https://image.201068.xyz/assets/clip_image676.jpg)

 

【4】Math内部的所有的属性，方法都被static修饰：类名.直接调用，无需创建对象： 

![img](https://image.201068.xyz/assets/clip_image678.jpg)

【5】常用方法： 

```
1.  package com.msb.test03;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Test01 {
7.      //这是一个main方法，是程序的入口：
8.      public static void main(String[] args) {
9.          //常用属性：
10.        System.out.println(Math.PI);
11.        //常用方法：
12.        System.out.println("随机数："+Math.random());//[0.0,1.0)
13.        System.out.println("绝对值："+Math.abs(-80));
14.        System.out.println("向上取值："+Math.ceil(9.1));
15.        System.out.println("向下取值："+Math.floor(9.9));
16.        System.out.println("四舍五入："+Math.round(3.5));
17.        System.out.println("取大的那个值："+Math.max(3, 6));
18.        System.out.println("取小的那个值："+Math.min(3, 6));
19.    }
20.}
21. 
```

【6】静态导入：

```
1.  package com.msb.test03;
2.  //静态导入：
3.  import static java.lang.Math.*;
4.  /**
5.   * @Auther: msb-zhaoss
6.   */
7.  public class Test01 {
8.      //这是一个main方法，是程序的入口：
9.      public static void main(String[] args) {
10.        //常用属性：
11.        System.out.println(PI);
12.        //常用方法：
13.        System.out.println("随机数："+random());//[0.0,1.0)
14.        System.out.println("绝对值："+abs(-80));
15.        System.out.println("向上取值："+ceil(9.1));
16.        System.out.println("向下取值："+floor(9.9));
17.        System.out.println("四舍五入："+round(3.5));
18.        System.out.println("取大的那个值："+max(3, 6));
19.        System.out.println("取小的那个值："+min(3, 6));
20.    }
21.    //如果跟Math中方法重复了，那么会优先走本类中的方法（就近原则）
22.    public static int random(){
23.        return 100;
24.    }
25.}
26. 
```



#### Random类

```
1.  package com.msb.test03;
2.   
3.  import java.util.Random;
4.   
5.  /**
6.   * @Auther: msb-zhaoss
7.   */
8.  public class Test02 {
9.      //这是一个main方法，是程序的入口：
10.    public static void main(String[] args) {
11.        //返回带正号的 double 值，该值大于等于 0.0 且小于 1.0。
12.        System.out.println("随机数："+Math.random());
13. 
14.        //学习Random类
15.        //（1）利用带参数的构造器创建对象：
16.        Random r1 = new Random(System.currentTimeMillis());
17.        int i = r1.nextInt();
18.        System.out.println(i);
19. 
20.        //（2）利用空参构造器创建对象：
21.        Random r2 = new Random();//表面是在调用无参数构造器，实际底层还是调用了带参构造器
22.        System.out.println(r2.nextInt(10));//在 0（包括）和指定值（不包括）之间均匀分布的 int 值。
23.        System.out.println(r2.nextDouble());//在 0.0 和 1.0 之间均匀分布的 double 值。
24.    }
25.}
26. 
```

![img](https://image.201068.xyz/assets/clip_image680.jpg)

 

#### String类

【1】直接使用，无需导包：

![img](https://image.201068.xyz/assets/clip_image682.jpg)

 

【2】形象说一下字符串： 

![img](https://image.201068.xyz/assets/clip_image684.jpg)

 

![img](https://image.201068.xyz/assets/clip_image686.jpg)

【3】 

![img](https://image.201068.xyz/assets/clip_image688.jpg)

 

String str = “abc”; 

"abc"就是String类下的一个具体的对象

 

【4】字符串是不可变的：？？？？ 

![img](https://image.201068.xyz/assets/clip_image690.jpg)

 

【5】这个String类不可以被继承，不能有子类： 

![img](https://image.201068.xyz/assets/clip_image692.jpg)

 

【6】String底层是一个char类型的数组

![img](https://image.201068.xyz/assets/clip_image694.jpg)

 

验证：

![img](https://image.201068.xyz/assets/clip_image696.jpg)

##### 常用方法

【1】构造器：底层就是给对象底层的value数组进行赋值操作。 

```
1.   //通过构造器来创建对象：
2.          String s1 = new String();
3.          String s2 = new String("abc");
4.          String s3 = new String(new char[]{'a','b','c'});
```

【3】常用方法：

```
1.  String s4 = "abc";
2.          System.out.println("字符串的长度为："+s4.length());
3.   
4.          String s5 = new SZtring("abc");
5.          System.out.println("字符串是否为空："+s5.isEmpty());
6.   
7.          System.out.println("获取字符串的下标对应的字符为："+s5.charAt(1));
```

【4】equals: 

```
1.          String s6 = new String("abc");
2.          String s7 = new String("abc");
3.          System.out.println(s6.equals(s7));
```

 

![img](https://image.201068.xyz/assets/clip_image698.jpg)

【5】String类实现了Comparable，里面有一个抽象方法叫compareTo，所以String中一定要对这个方法进行重写：4 

```
1.  String s8 = new String("abc");
2.          String s9 = new String("abc");
3.          System.out.println(s8.compareTo(s9));
```

 

![img](https://image.201068.xyz/assets/clip_image700.jpg)

【6】常用方法： 

```
1.  //字符串的截取：
2.          String s10 = "abcdefhijk";
3.          System.out.println(s10.substring(3));
4.          System.out.println(s10.substring(3, 6));//[3,6)
5.          //字符串的合并/拼接操作：
6.          System.out.println(s10.concat("pppp"));
7.          //字符串中的字符的替换：
8.          String s11 = "abcdeahija";
9.          System.out.println(s11.replace('a', 'u'));
10.        //按照指定的字符串进行分裂为数组的形式：
11.        String s12 = "a-b-c-d-e-f";
12.        String[] strs = s12.split("-");
13.        System.out.println(Arrays.toString(strs));
14.        //转大小写的方法：
15.        String s13 = "abc";
16.        System.out.println(s13.toUpperCase());
17.        System.out.println(s13.toUpperCase().toLowerCase());
18. 
19.        //去除收尾空格：
20.        String s14 = "    a  b  c    ";
21.        System.out.println(s14.trim());
22.        //toString()
23.        String s15 = "abc";
24.        System.out.println(s15.toString());
25. 
26.        //转换为String类型：
27.        System.out.println(String.valueOf(false));
```

##### String的内存分析

【1】字符串拼接：

```
1.  public class Test02 {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) {
4.          String s1 = "a"+"b"+"c";
5.          String s2 = "ab"+"c";
6.          String s3 = "a"+"bc";
7.          String s4 = "abc";
8.          String s5 = "abc"+"";
9.      }
10.}
```

上面的字符串，会进行编译器优化，直接合并成为完整的字符串，我们可以反编译验证： 

![img](https://image.201068.xyz/assets/clip_image702.jpg)

然后在常量池中，常量池的特点是第一次如果没有这个字符串，就放进去，如果有这个字符串，就直接从常量池中取：

 

内存：

![img](https://image.201068.xyz/assets/clip_image704.jpg)

【2】new关键字创建对象： 

```
1.  String s6 = new String("abc");
```

内存：开辟两个空间（1.字符串常量池中的字符串 2.堆中的开辟的空间） 

![img](https://image.201068.xyz/assets/clip_image706.jpg)

【3】有变量参与的字符串拼接： 

```
1.  public class Test03 {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) {
4.          String a = "abc";
5.          String b = a + "def";
6.          System.out.println(b);
7.      }
8.  }
```

a变量在编译的时候不知道a是“abc”字符串，所以不会进行编译期优化，不会直接合并为“abcdef” 

 

反汇编过程：为了更好的帮我分析字节码文件是如何进行解析的：

 

利用IDEA中的控制台： 

![img](https://image.201068.xyz/assets/clip_image708.jpg)

 

![img](https://image.201068.xyz/assets/clip_image710.jpg)

 

 

 

 

#### StringBuilder类

**【1】字符串的分类：** 

（1）不可变字符串：String 

（2）可变字符串：StringBuilder，StringBuffer 

 

疑问：

（1）可变不可变？？ 

（2）本节课重点：StringBuilder  -----》√ 

（3）StringBuilder和StringBuffer区别  ？？ 

 

**【2】StringBuilder底层：**非常重要的两个属性： 

![img](https://image.201068.xyz/assets/clip_image712.jpg)

 

**【3】对应内存分析：** 

 

 

```
1.  package com.msb.test05;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Test01 {
7.      //这是一个main方法，是程序的入口：
8.      public static void main(String[] args) {
9.          //创建StringBuilder的对象：
10.        StringBuilder sb3 = new StringBuilder();
11.        //表面上调用StringBuilder的空构造器，实际底层是对value数组进行初始化，长度为16
12.        StringBuilder sb2 = new StringBuilder(3);
13.        //表面上调用StringBuilder的有参构造器，传入一个int类型的数，实际底层就是对value数组进行初始化，长度为你传入的数字
14.        StringBuilder sb = new StringBuilder("abc");
15.        System.out.println(sb.append("def").append("aaaaaaaa").append("bbb").append("ooooooo").toString());;//链式调用方式：return this
16. 
17.    }
18.}
19. 
```

 

![img](https://image.201068.xyz/assets/clip_image714.jpg)

 

##### 解释可变和不可变字符串

【1】String---》不可变 

![img](https://image.201068.xyz/assets/clip_image716.jpg)

 

【2】StringBuilder---》可变 

可变，在StringBuilder这个对象的地址不变的情况下，想把“abc”变成“abcdef”是可能的，直接追加即可 

```
1.  public class Test02 {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) {
4.          StringBuilder sb = new StringBuilder();
5.   
6.          System.out.println(sb.append("abc")==sb.append("def"));//true
7.      }
8.  }
9.   
```

 

 

##### 常用方法

【1】StringBuilder常用方法： 

```
1.  package com.msb.test05;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Test03 {
7.      //这是一个main方法，是程序的入口：
8.      public static void main(String[] args) {
9.          StringBuilder sb=new StringBuilder("nihaojavawodeshijie");
10.        //增
11.        sb.append("这是梦想");
12.        System.out.println(sb);//nihaojavawodeshijie这是梦想
13.        //删
14.        sb.delete(3, 6);//删除位置在[3,6)上的字符
15.        System.out.println(sb);//nihavawodeshijie这是梦想
16. 
17.        sb.deleteCharAt(16);//删除位置在16上的字符
18.        System.out.println(sb);//nihavawodeshijie是梦想
19. 
20.        //改-->插入
21.        StringBuilder sb1=new StringBuilder("$23445980947");
22.        sb1.insert(3, ",");//在下标为3的位置上插入 ,
23.        System.out.println(sb1);
24.        StringBuilder sb2=new StringBuilder("$2你好吗5980947");
25.        //改-->替换
26.        sb2.replace(3, 5, "我好累");//在下标[3,5)位置上插入字符串
27.        System.out.println(sb2);
28.        sb.setCharAt(3, '!');
29.        System.out.println(sb);
30.        //查
31.        StringBuilder sb3=new StringBuilder("asdfa");
32.        for (int i = 0; i < sb3.length(); i++) {
33.            System.out.print(sb3.charAt(i)+"\t");
34.        }
35.        System.out.println();
36.        //截取
37.        String str=sb3.substring(2,4);//截取[2,4)返回的是一个新的String，对StringBuilder没有影响
38.        System.out.println(str);
39.        System.out.println(sb3);
40.    }
41.}
42. 
```

 

【2】StringBuffer常用方法： 

```
1.  package com.msb.test05;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Test03 {
7.      //这是一个main方法，是程序的入口：
8.      public static void main(String[] args) {
9.          StringBuffer sb=new StringBuffer("nihaojavawodeshijie");
10.        //增
11.        sb.append("这是梦想");
12.        System.out.println(sb);//nihaojavawodeshijie这是梦想
13.        //删
14.        sb.delete(3, 6);//删除位置在[3,6)上的字符
15.        System.out.println(sb);//nihavawodeshijie这是梦想
16. 
17.        sb.deleteCharAt(16);//删除位置在16上的字符
18.        System.out.println(sb);//nihavawodeshijie是梦想
19. 
20.        //改-->插入
21.        StringBuilder sb1=new StringBuilder("$23445980947");
22.        sb1.insert(3, ",");//在下标为3的位置上插入 ,
23.        System.out.println(sb1);
24.        StringBuilder sb2=new StringBuilder("$2你好吗5980947");
25.        //改-->替换
26.        sb2.replace(3, 5, "我好累");//在下标[3,5)位置上插入字符串
27.        System.out.println(sb2);
28.        sb.setCharAt(3, '!');
29.        System.out.println(sb);
30.        //查
31.        StringBuilder sb3=new StringBuilder("asdfa");
32.        for (int i = 0; i < sb3.length(); i++) {
33.            System.out.print(sb3.charAt(i)+"\t");
34.        }
35.        System.out.println();
36.        //截取
37.        String str=sb3.substring(2,4);//截取[2,4)返回的是一个新的String，对StringBuilder没有影响
38.        System.out.println(str);
39.        System.out.println(sb3);
40.    }
41.}
42. 
```

 

 

##### 面试题：String，StringBuilder，StringBuffer区别和联系

### String、StringBuffer、StringBuilder区别与联系 

\1. String类是不可变类，即一旦一个String对象被创建后，包含在这个对象中的字符序列是不可改变的，直至这个对象销毁。

\2. StringBuffer类则代表一个字符序列可变的字符串，可以通过append、insert、reverse、setChartAt、setLength等方法改变其内容。一旦生成了最终的字符串，调用toString方法将其转变为String 

\3. JDK1.5新增了一个StringBuilder类，与StringBuffer相似，构造方法和方法基本相同。不同是StringBuffer是线程安全的，而StringBuilder是线程不安全的，所以性能略高。通常情况下，创建一个内容可变的字符串，应该优先考虑使用StringBuilder 

    StringBuilder:JDK1.5开始  效率高  线程不安全 

    StringBuffer:JDK1.0开始  效率低   线程安全 

 

# 第11章_集合

 

## 什么是算法和数据结构

**【1】算法：**

（1）可以解决具体问题 :例如  1+2+3+4+。。。+99+100 

解题流程=算法 

（2）有设计解决的具体的流程 

算法1： 1+2=3  3+3=6 6+4=10.....加到100  --》5050 

算法2：(1+100)*50=101*50=5050-->高斯算法 

（3）有评价这个算法的具体的指标 --》时间复杂度  空间复杂度（从数学角度考虑） 

 

\---------------------------------------------------------------------

 

**【2】数据结构：**就是在计算机的缓存，内存，硬盘  如何组织管理数据的。重点在结构上，是按照什么结构来组织管理我们的数据。

![img](https://image.201068.xyz/assets/clip_image718.jpg)

数据结构分为：

（1）逻辑结构 ：--》思想上的结构--》卧室，厨房，卫生间 ---》线性表（数组，链表），图，树，栈，队列 

（2）物理结构 ：--》真实结构--》钢筋混凝土+牛顿力学------》紧密结构（顺序结构），跳转结构（链式结构） 

 

**【3】紧密结构（顺序结构），跳转结构（链式结构）** 

以线性表为例： 

线性表的逻辑结构如图所示： 

![img](https://image.201068.xyz/assets/clip_image720.jpg)

线性表特点： 

 

线性表是n个类型相同数据元素的有限序列，通常记作a0,a1,,,ai-1,ai,ai+1,,,,,an-1)。

**1.****相同数据类型** 

 在线性表的定义中,我们看到从a0到an-1的n个数据元素是具有相同属件的亓素。 

 比如说可以都是数字,例如(12,23,45,56,45); 

 也可以是宇符,例如(A,B,....Z) 

 当然也可以是具有更复杂结构的数据元素,例如学生、商品、装备等。

 相同数据类型意味着在内存中存储时,每个元素会占用相同的内存空间,便于后续的查询定位。 

**2.****序列(顺序性)** 

 在线性表的相邻数据元素之间存在若序偶关系， 

 即ai-1是ai的直接前驱,则ai是ai-1的直接后续, 

 同时ai又是ai+1的直接前驱，ai+1是ai的直接后续。 

 唯一没有直接前驱的元素a0 一端称为表头,唯一没有后续的元素an-1一端称为表尾。 

 除了表头和表尾元素外,任何一个元素都有且仅有一个直接前驱和直接后继。

**3.****有限** 

 线件表中数据元素的个数n定义为线性表的长度, n是个有限值。 

 当n=0时线性表为空表， 

 在非空的线性表中每个数据元索在线性表中都有唯一确定的序号， 

 例如a0的序号是0 ,ai的序号是i。 

 在一个具有n>0个数据元素的线性表中,数据元素序号的范围是[O, n-1]。 

 逻辑结构和物理结构的关系：

线性表逻辑结构，对应的真实结构如果是紧密结构---》典型就是  数组： 

![img](https://image.201068.xyz/assets/clip_image722.jpg)

线性表逻辑结构，对应的真实结构如果是跳转结构---》典型就是  链表： 

优点：删除元素，插入元素效率高

缺点：查询元素效率低

![img](https://image.201068.xyz/assets/clip_image724.jpg)

![img](https://image.201068.xyz/assets/clip_image726.jpg)

![img](https://image.201068.xyz/assets/clip_image728.jpg)

 

## 集合的引入

【1】数组，集合都是对多个数据进行存储操作的，简称为容器。

PS:这里的存储指的是内存层面的存储，而不是持久化存储（.txt,.avi,.jpg,数据库）。 

 

【2】数组：特点： 

（1）数组一旦指定了长度，那么长度就被确定了，不可以更改。 

int[] arr = new int[6]; 

（2）数组一旦声明了类型以后，数组中只能存放这个类型的数据。数组中只能存放同一种类型的数据。 

int[] arr,String[] s,double[] d..... 

【3】数组：缺点： 

（1）数组一旦指定了长度，那么长度就被确定了，不可以更改。 

（2）删除，增加元素  效率低。 

（3）数组中实际元素的数量是没有办法获取的，没有提供对应的方法或者属性来获取 

（4）数组存储：有序，可重复 ，对于无序的，不可重复的数组不能满足要求。 

 

【4】正因为上面的缺点，引入了一个新的存储数据的结构---》集合 

 

【5】集合一章我们会学习很多集合，为什么要学习这么多集合呢？ 

因为不同集合底层数据结构不一样。集合不一样，特点也不一样

 

 

## 简要集合结构图

![img](https://image.201068.xyz/assets/clip_image730.jpg)

## 集合应用场合

前端后端数据库交互： 

![img](https://image.201068.xyz/assets/clip_image732.jpg)

当需要将相同结构的个体整合到一起的时候，需要集合。

实际应用场合：

![img](https://image.201068.xyz/assets/clip_image734.jpg)

![img](https://image.201068.xyz/assets/clip_image736.jpg)

![img](https://image.201068.xyz/assets/clip_image738.jpg)

 

## Colletion接口

### Colletion接口常用方法

```
1.  package com.msb.test01;
2.   
3.  import java.util.ArrayList;
4.  import java.util.Arrays;
5.  import java.util.Collection;
6.  import java.util.List;
7.   
8.  /**
9.   * @author : msb-zhaoss
10. */
11.public class Test01 {
12.    //这是main方法，程序的入口
13.    public static void main(String[] args) {
14.        /*
15.        Collection接口的常用方法：
16.        增加：add(E e) addAll(Collection<? extends E> c)
17.        删除：clear() remove(Object o)
18.        修改：
19.        查看：iterator() size()
20.        判断：contains(Object o)  equals(Object o) isEmpty()
21.         */
22.        //创建对象：接口不能创建对象，利用实现类创建对象：
23.        Collection col = new ArrayList();
24.        //调用方法：
25.        //集合有一个特点：只能存放引用数据类型的数据，不能是基本数据类型
26.        //基本数据类型自动装箱，对应包装类。int--->Integer
27.        col.add(18);
28.        col.add(12);
29.        col.add(11);
30.        col.add(17);
31. 
32.        System.out.println(col/*.toString()*/);
33. 
34.        List list = Arrays.asList(new Integer[]{11, 15, 3, 7, 1});
35.        col.addAll(list);//将另一个集合添加入col中
36.        System.out.println(col);
37. 
38.        //col.clear();清空集合
39.        System.out.println(col);
40.        System.out.println("集合中元素的数量为："+col.size());
41.        System.out.println("集合是否为空："+col.isEmpty());
42. 
43.        boolean isRemove = col.remove(15);
44.        System.out.println(col);
45.        System.out.println("集合中数据是否被删除："+isRemove);
46. 
47. 
48.        Collection col2 = new ArrayList();
49.        col2.add(18);
50.        col2.add(12);
51.        col2.add(11);
52.        col2.add(17);
53. 
54.        Collection col3 = new ArrayList();
55.        col3.add(18);
56.        col3.add(12);
57.        col3.add(11);
58.        col3.add(17);
59. 
60.        System.out.println(col2.equals(col3));
61.        System.out.println(col2==col3);//地址一定不相等  false
62. 
63.        System.out.println("是否包含元素："+col3.contains(117));
64. 
65.    }
66.}
67. 
```

 

### Collection集合的遍历

迭代器简要原理图： 

![img](https://image.201068.xyz/assets/clip_image740.jpg)

 

```
1.  package com.msb.test01;
2.   
3.  import java.util.ArrayList;
4.  import java.util.Collection;
5.  import java.util.Iterator;
6.   
7.  /**
8.   * @author : msb-zhaoss
9.   */
10.public class Test02 {
11.    //这是main方法，程序的入口
12.    public static void main(String[] args) {
13.        Collection col = new ArrayList();
14.        col.add(18);
15.        col.add(12);
16.        col.add(11);
17.        col.add(17);
18.        col.add("abc");
19.        col.add(9.8);
20. 
21.        //对集合遍历（对集合中元素进行查看）
22.        //方式1：普通for循环
23.        /*for(int i= 0;i<col.size();i++){
24.            col.
25.        }*/
26. 
27.        //方式2：增强for循环
28.        for(Object o:col){
29.            System.out.println(o);
30.        }
31.        System.out.println("------------------------");
32.        //方式3：iterator()
33.        Iterator it = col.iterator();
34.        while(it.hasNext()){
35.            System.out.println(it.next());
36.        }
37.    }
38.}
39. 
```

 

### List接口

 

#### List接口的常用方法和遍历方式

```
1.  package com.msb.test01;
2.   
3.  import com.sun.org.apache.xerces.internal.dom.PSVIAttrNSImpl;
4.   
5.  import java.util.ArrayList;
6.  import java.util.Iterator;
7.  import java.util.List;
8.   
9.  /**
10. * @author : msb-zhaoss
11. */
12.public class Test03 {
13.    //这是main方法，程序的入口
14.    public static void main(String[] args) {
15.        /*
16.        List接口中常用方法：
17.        增加：add(int index, E element)
18.        删除：remove(int index)  remove(Object o)
19.        修改：set(int index, E element)
20.        查看：get(int index)
21.        判断：
22.         */
23.        List list = new ArrayList();
24.        list.add(13);
25.        list.add(17);
26.        list.add(6);
27.        list.add(-1);
28.        list.add(2);
29.        list.add("abc");
30.        System.out.println(list);
31.        list.add(3,66);
32.        System.out.println(list);
33.        list.set(3,77);
34.        System.out.println(list);
35.        list.remove(2);//在集合中存入的是Integer类型数据的时候，调用remove方法调用的是：remove(int index)
36.        System.out.println(list);
37.        list.remove("abc");
38.        System.out.println(list);
39. 
40.        Object o = list.get(0);
41.        System.out.println(o);
42. 
43.        //List集合 遍历：
44.        //方式1：普通for循环：
45.        System.out.println("---------------------");
46.        for(int i = 0;i<list.size();i++){
47.            System.out.println(list.get(i));
48.        }
49.        //方式2：增强for循环：
50.        System.out.println("---------------------");
51.        for(Object obj:list){
52.            System.out.println(obj);
53.        }
54.        //方式3：迭代器：
55.        System.out.println("---------------------");
56.        Iterator it = list.iterator();
57.        while(it.hasNext()){
58.            System.out.println(it.next());
59.        }
60. 
61. 
62.    }
63.}
64. 
```

 

 

#### ArrayList实现类（JDK1.7）

【1】在idea中切换JDK的方法： 

![img](https://image.201068.xyz/assets/clip_image742.jpg)

 

 

【2】ArrayList实现List接口的失误：

集合创始人 承认了这个失误，但是在后续的版本中没有删除，觉得没必要： 

![img](https://image.201068.xyz/assets/clip_image744.jpg)

 

【3】底层重要属性： 

![img](https://image.201068.xyz/assets/clip_image746.jpg)

在JDK1.7中：在调用构造器的时候给底层数组elementData初始化，数组初始化长度为10： 

![img](https://image.201068.xyz/assets/clip_image748.jpg)

对应内存：

![img](https://image.201068.xyz/assets/clip_image750.jpg)

调用add方法： 

```
1.          ArrayList al = new ArrayList();
2.   
3.          System.out.println(al.add("abc"));
4.          System.out.println(al.add("def"));
```

 

当数组中的10个位置都满了的![img](https://image.201068.xyz/assets/clip_image752.jpg)时候就开始进行数组的扩容，扩容长度为 原数组的1.5倍：

![img](https://image.201068.xyz/assets/clip_image754.jpg)

![img](https://image.201068.xyz/assets/clip_image756.jpg)

![img](https://image.201068.xyz/assets/clip_image758.jpg)

#### ArrayList实现类（JDK1.8）

【1】JDK1.8底层依旧是Object类型的数组，size:数组中有效长度： 

![img](https://image.201068.xyz/assets/clip_image760.jpg)

【2】ArrayList al = new ArrayList();调用空构造器：

![img](https://image.201068.xyz/assets/clip_image762.jpg)

 

【2】add方法： 

![img](https://image.201068.xyz/assets/clip_image764.jpg)

 

![img](https://image.201068.xyz/assets/clip_image766.jpg)

![img](https://image.201068.xyz/assets/clip_image768.jpg)

 

![img](https://image.201068.xyz/assets/clip_image770.jpg)

 

#### Vector实现类

【1】底层Object数组，int类型属性表示数组中有效长度： 

![img](https://image.201068.xyz/assets/clip_image772.jpg)

【2】Vector v=new Vector();调用构造器： 

![img](https://image.201068.xyz/assets/clip_image774.jpg)

 

 

【3】add方法： 

![img](https://image.201068.xyz/assets/clip_image776.jpg)

 

#### 泛型

##### 引入

【1】什么是泛型（Generic）： 

泛型就相当于标签

形式：<>  

集合容器类在设计阶段/声明阶段不能确定这个容器到底实际存的是什么类型的对象，所以在JDK1.5之前只能把元素类型设计为Object， 

JDK1.5之 后使用泛型来解决。因为这个时候除了元素的类型不确定，其他的部分是确定的，例如关于这个元素如何保存，如何管理等是确定的，因此此时把元素的类型设计成一个参数，这个类型参数叫做泛型。

Collection<E>, List<E>， ArrayList<E> 这个<E>就是类型参数，即泛型。

 

【2】没有泛型的时候使用集合： 

```
1.  package com.msb.test01;
2.   
3.  import java.util.ArrayList;
4.   
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class Test01 {
9.      //这是main方法，程序的入口
10.    public static void main(String[] args) {
11.        //创建一个ArrayList集合，向这个集合中存入学生的成绩：
12.        ArrayList al = new ArrayList();
13.        al.add(98);
14.        al.add(18);
15.        al.add(39);
16.        al.add(60);
17.        al.add(83);
18.        al.add("丽丽");
19. 
20.        //对集合遍历查看：
21.        for(Object obj:al){
22.            System.out.println(obj);
23.        }
24.    }
25.}
26. 
```

如果不使用泛型的话，有缺点：

一般我们在使用的时候基本上往集合中存入的都是相同类型的数据--》便于管理，所以现在什么引用数据类型都可以存入集合，不方便！ 

 

【3】JDK1.5以后开始使用泛型，集合中使用泛型： 

```
1.  package com.msb.test01;
2.   
3.  import java.util.ArrayList;
4.   
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class Test01 {
9.      //这是main方法，程序的入口
10.    public static void main(String[] args) {
11.        //创建一个ArrayList集合，向这个集合中存入学生的成绩：
12.        //加入泛型的优点：在编译时期就会对类型进行检查，不是泛型对应的类型就不可以添加入这个集合。
13.        ArrayList<Integer> al = new ArrayList<Integer>();
14.        al.add(98);
15.        al.add(18);
16.        al.add(39);
17.        al.add(60);
18.        al.add(83);
19.        /*al.add("丽丽");
20.        al.add(9.8);*/
21. 
22.        //对集合遍历查看：
23.        /*for(Object obj:al){
24.            System.out.println(obj);
25.        }*/
26.        for(Integer i:al){
27.            System.out.println(i);
28.        }
29.    }
30.}
31. 
```

【4】泛型总结： 

（1）JDK1.5以后 

（2）泛型实际就是 一个<>引起来的 参数类型，这个参数类型  具体在使用的时候才会确定具体的类型。 

![img](https://image.201068.xyz/assets/clip_image778.jpg)

![img](https://image.201068.xyz/assets/clip_image780.jpg)

 

（3）使用了泛型以后，可以确定集合中存放数据的类型，在编译时期就可以检查出来。 

（4）使用泛型你可能觉得麻烦，实际使用了泛型才会简单，后续的遍历等操作简单。 

（5）泛型的类型：都是引用数据类型，不能是基本数据类型。 

（6）ArrayList<Integer> al = new ArrayList<Integer>();在JDK1.7以后可以写为： 

ArrayList<Integer> al = new ArrayList<>();  --<> ---钻石运算符

 

##### 自定义泛型结构

 

###### 泛型类，泛型接口

【1】泛型类的定义和实例化：

```
1.  package com.msb.test02;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   * GenericTes就是一个普通的类
6.   * GenericTest<E> 就是一个泛型类
7.   * <>里面就是一个参数类型，但是这个类型是什么呢？这个类型现在是不确定的，相当于一个占位
8.   * 但是现在确定的是这个类型一定是一个引用数据类型，而不是基本数据类型
9.   */
10.public class GenericTest<E> {
11.    int age;
12.    String name;
13.    E sex;
14. 
15.    public void a(E n){
16. 
17.    }
18.    public void b(E[] m){
19. 
20.    }
21.}
22. 
23.class Test{
24.    //这是main方法，程序的入口
25.    public static void main(String[] args) {
26.        //GenericTest进行实例化：
27.        //(1)实例化的时候不指定泛型：如果实例化的时候不明确的指定类的泛型，那么认为此泛型为Object类型
28.        GenericTest gt1 = new GenericTest();
29.        gt1.a("abc");
30.        gt1.a(17);
31.        gt1.a(9.8);
32.        gt1.b(new String[]{"a","b","c"});
33. 
34.        //（2）实例化的时候指定泛型：---》推荐方式
35.        GenericTest<String> gt2 = new GenericTest<>();
36.        gt2.sex = "男";
37.        gt2.a("abc");
38.        gt2.b(new String[]{"a","b","c"});
39.        
40.    }
41.}
42. 
```

【2】继承情况： 

（1）父类指定泛型： 

```
1.  class SubGenericTest extends GenericTest<Integer>{
2.   
3.  }
4.   
5.  class Demo{
6.      //这是main方法，程序的入口
7.      public static void main(String[] args) {
8.          //指定父类泛型，那么子类就不需要再指定泛型了，可以直接使用
9.          SubGenericTest sgt = new SubGenericTest();
10.        sgt.a(19);
11.    }
12.}
```

（2）父类不指定泛型： 

如果父类不指定泛型，那么子类也会变成一个泛型类，那这个E的类型可以在创建子类对象的时候确定： 

```
1.  class SubGenericTest2<E> extends GenericTest<E>{
2.   
3.  }
```

 

```
1.  class Demo2{
2.      //这是main方法，程序的入口
3.      public static void main(String[] args) {
4.          SubGenericTest2<String> s = new  SubGenericTest2<>();
5.          s.a("abc");
6.          s.sex = "女";
7.      }
8.  }
```

 

【3】应用场合： 

![img](https://image.201068.xyz/assets/clip_image782.jpg)

 

 

【4】细节： 

（1）泛型类可以定义多个参数类型 

![img](https://image.201068.xyz/assets/clip_image784.jpg)

（2）泛型类的构造器的写法： 

![img](https://image.201068.xyz/assets/clip_image786.jpg)

（3）不同的泛型的引用类型不可以相互赋值： 

![img](https://image.201068.xyz/assets/clip_image788.jpg)

 

（4）泛型如果不指定，那么就会被擦除，反应对应的类型为Object类型： 

![img](https://image.201068.xyz/assets/clip_image790.jpg)

（5）反省类中的静态方法不能使用类的泛型： 

![img](https://image.201068.xyz/assets/clip_image792.jpg)

（6）不能直接使用E[]的创建： 

![img](https://image.201068.xyz/assets/clip_image794.jpg)

 

 

###### 泛型方法

```
1.  package com.msb.test04;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   * 1.什么是泛型方法：
6.   * 不是带泛型的方法就是泛型方法
7.   * 泛型方法有要求：这个方法的泛型的参数类型要和当前的类的泛型无关
8.   * 换个角度：
9.   * 泛型方法对应的那个泛型参数类型 和  当前所在的这个类 是否是泛型类，泛型是啥  无关
10. * 2.泛型方法定义的时候，前面要加上<T>
11. *     原因：如果不加的话，会把T当做一种数据类型，然而代码中没有T类型那么就会报错
12. * 3.T的类型是在调用方法的时候确定的
13. * 4.泛型方法可否是静态方法？可以是静态方法
14. */
15.public class TestGeneric<E> {
16.    //不是泛型方法 （不能是静态方法）
17.    public static void a(E e){
18. 
19.    }
20.    //是泛型方法
21.    public static <T>  void b(T t){
22. 
23.    }
24. 
25.}
26.class Demo{
27.    //这是main方法，程序的入口
28.    public static void main(String[] args) {
29.        TestGeneric<String> tg = new TestGeneric<>();
30.        tg.a("abc");
31.        tg.b("abc");
32.        tg.b(19);
33.        tg.b(true);
34.    }
35.}
36. 
```

###### 泛型参数存在继承关系的情况

![img](https://image.201068.xyz/assets/clip_image796.jpg)

 

###### 通配符

【1】在没有通配符的时候：

下面的a方法，相当于方法的重复定义，报错 

```
1.  public class Test {
2.      /*public void a(List<Object> list){
3.   
4.      }
5.      public void a(List<String> list){
6.   
7.      }
8.      public void a(List<Integer> list){
9.   
10.    }*/
11.}
12. 
```

 

 

【2】引入通配符： 

```
1.  public class Demo {
2.      //这是main方法，程序的入口
3.      public static void main(String[] args) {
4.          List<Object> list1 = new ArrayList<>();
5.          List<String> list2 = new ArrayList<>();
6.          List<Integer> list3 = new ArrayList<>();
7.   
8.          List<?> list = null;
9.          list = list1;
10.        list = list2;
11.        list = list3;
12. 
13.    }
14.}
```

发现： A 和 B是子类父类的关系，G<A>和G<B>不存在子类父类关系，是并列的 

加入通配符？后，G<?>就变成了 G<A>和G<B>的父类 

 

【3】使用通配符： 

```
1.  package com.msb.test06;
2.   
3.  import java.util.ArrayList;
4.  import java.util.List;
5.   
6.  /**
7.   * @author : msb-zhaoss
8.   */
9.  public class Test {
10.    /*public void a(List<Object> list){
11. 
12.    }
13.    public void a(List<String> list){
14. 
15.    }
16.    public void a(List<Integer> list){
17. 
18.    }*/
19.    public void a(List<?> list){
20.        //内部遍历的时候用Object即可，不用？
21.        for(Object a:list){
22.            System.out.println(a);
23.        }
24.    }
25.}
26. 
27.class T{
28.    //这是main方法，程序的入口
29.    public static void main(String[] args) {
30.        Test t = new Test();
31.        t.a(new ArrayList<Integer>());
32.        t.a(new ArrayList<String>());
33.        t.a(new ArrayList<Object>());
34.    }
35.}
```

【4】查看API中应用位置： 

![img](https://image.201068.xyz/assets/clip_image798.jpg)

 

###### 使用通配符后的细节

```
1.  public class Test {
2.      public void a(List<?> list){
3.          //1.遍历：
4.          for(Object a:list){
5.              System.out.println(a);
6.          }
7.          //2.数据的写入操作 ：
8.          //list.add("abc");-->出错，不能随意的添加数据
9.          list.add(null);
10. 
11.        //3.数据的读取操作：
12.        Object s = list.get(0);
13.    }
14.}
15. 
16.class T{
17.    //这是main方法，程序的入口
18.    public static void main(String[] args) {
19.        Test t = new Test();
20.        t.a(new ArrayList<Integer>());
21.        t.a(new ArrayList<String>());
22.        t.a(new ArrayList<Object>());
23.    }
24.}
```

###### 泛型受限

```
1.  package com.msb.test07;
2.   
3.  import java.util.ArrayList;
4.  import java.util.List;
5.   
6.  /**
7.   * @author : msb-zhaoss
8.   */
9.  public class Test {
10.    //这是main方法，程序的入口
11.    public static void main(String[] args) {
12.        //a,b,c三个集合是并列的关系：
13.        List<Object> a = new ArrayList<>();
14.        List<Person> b = new ArrayList<>();
15.        List<Student> c = new ArrayList<>();
16.        /*开始使用泛型受限：泛型的上限
17.        List<? extends Person>:
18.        就相当于：
19.        List<? extends Person>是List<Person>的父类，是List<Person的子类>的父类
20.         */
21.        List<? extends Person> list1 = null;
22.        /*list1 = a;
23.        list1 = b;
24.        list1 = c;*/
25.        /*开始使用泛型受限：泛型的下限
26.        List<? super Person>
27.        就相当于：
28.        List<? super Person>是List<Person>的父类，是List<Person的父类>的父类
29.         */
30.        List<? super Person> list2 = null;
31.        list2 = a;
32.        list2 = b;
33.        list3 = c;
34.    }
35.}
36. 
```

#### LinkedList实现类的使用

```
1.  package com.msb.test04;
2.   
3.  import java.util.Iterator;
4.  import java.util.LinkedList;
5.   
6.  /**
7.   * @author : msb-zhaoss
8.   */
9.  public class Test {
10.    //这是main方法，程序的入口
11.    public static void main(String[] args) {
12.        /*
13.        LinkedList常用方法：
14.        增加 addFirst(E e) addLast(E e)
15.             offer(E e) offerFirst(E e) offerLast(E e)
16.        删除 poll()
17.            pollFirst() pollLast()  ---》JDK1.6以后新出的方法，提高了代码的健壮性
18.            removeFirst() removeLast()
19.        修改
20.        查看 element()
21.             getFirst()  getLast()
22.             indexOf(Object o)   lastIndexOf(Object o)
23.             peek()
24.             peekFirst() peekLast()
25.        判断
26.         */
27.        //创建一个LinkedList集合对象：
28.        LinkedList<String> list = new LinkedList<>();
29.        list.add("aaaaa");
30.        list.add("bbbbb");
31.        list.add("ccccc");
32.        list.add("ddddd");
33.        list.add("eeeee");
34.        list.add("bbbbb");
35.        list.add("fffff");
36. 
37.        list.addFirst("jj");
38.        list.addLast("hh");
39. 
40.        list.offer("kk");//添加元素在尾端
41.        list.offerFirst("pp");
42.        list.offerLast("rr");
43.        System.out.println(list);//LinkedList可以添加重复数据
44.        System.out.println(list.poll());//删除头上的元素并且将元素输出
45.        System.out.println(list.pollFirst());
46.        System.out.println(list.pollLast());
47. 
48.        System.out.println(list.removeFirst());
49.        System.out.println(list.removeLast());
50.        System.out.println(list);//LinkedList可以添加重复数据
51. 
52.        /*list.clear();//清空集合
53.        System.out.println(list);*/
54.        /*System.out.println(list.pollFirst());*/
55.        /*System.out.println(list.removeFirst());报错：Exception in thread "main" java.util.NoSuchElementException*/
56. 
57. 
58.        //集合的遍历：
59.        System.out.println("---------------------");
60.        //普通for循环：
61.        for(int i = 0;i<list.size();i++){
62.            System.out.println(list.get(i));
63.        }
64.        System.out.println("---------------------");
65.        //增强for：
66.        for(String s:list){
67.            System.out.println(s);
68.        }
69.        System.out.println("---------------------");
70.        //迭代器：
71.        /*Iterator<String> it = list.iterator();
72.        while(it.hasNext()){
73.            System.out.println(it.next());
74.        }*/
75.        //下面这种方式好，节省内存
76.        for(Iterator<String> it = list.iterator();it.hasNext();){
77.            System.out.println(it.next());
78.        }
79.    }
80.}
81. 
```

 

##### LinkedList简要底层原理图

![img](https://image.201068.xyz/assets/clip_image800.jpg)

##### 模拟LinkedList源码

```
1.  package com.msb.test05;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class MyLinkedList {
7.      //链中一定有一个首节点：
8.      Node first;
9.      //链中一定有一个尾节点：
10.    Node last;
11.    //计数器：
12.    int count = 0;
13.    //提供一个构造器：
14.    public MyLinkedList(){
15. 
16.    }
17.    //添加元素方法：
18.    public void add(Object o){
19.        if(first == null){//证明你添加的元素是第一个节点：
20.            //将添加的元素封装为一个Node对象：
21.            Node n = new Node();
22.            n.setPre(null);
23.            n.setObj(o);
24.            n.setNext(null);
25.            //当前链中第一个节点变为n
26.            first = n;
27.            //当前链中最后一个节点变为n
28.            last = n;
29.        }else{//证明已经不是链中第一个节点了
30.            //将添加的元素封装为一个Node对象：
31.            Node n = new Node();
32.            n.setPre(last);//n的上一个节点一定是当前链中的最后一个节点last
33.            n.setObj(o);
34.            n.setNext(null);
35.            //当前链中的最后一个节点的下一个元素 要指向n
36.            last.setNext(n);
37.            //将最后一个节点变为n
38.            last = n;
39.        }
40.        //链中元素数量加1
41.        count++;
42.    }
43. 
44.    //得到集合中元素的数量：
45.    public int getSize(){
46.        return count;
47.    }
48. 
49.    //通过下标得到元素：
50.    public Object get(int index){
51.        //获取链表的头元素：
52.        Node n = first;
53.        //一路next得到想要的元素
54.        for(int i=0;i<index;i++){
55.            n = n.getNext();
56.        }
57.        return n.getObj();
58.    }
59.}
60.class Test{
61.    //这是main方法，程序的入口
62.    public static void main(String[] args) {
63.        //创建一个MyLinkedList集合对象：
64.        MyLinkedList ml = new MyLinkedList();
65.        ml.add("aa");
66.        ml.add("bb");
67.        ml.add("cc");
68.        System.out.println(ml.getSize());
69.        System.out.println(ml.get(0));
70.    }
71.}
```

 

 

 

 

 

 

debug验证数据添加成功： 

![img](https://image.201068.xyz/assets/clip_image802.jpg)

 

##### LinkedList源码解析

【1】JDK1.7和JDK1.8的LinkedList的源码是一致的

【2】源码： 

```
1.  public class LinkedList<E>{//E是一个泛型，具体的类型要在实例化的时候才会最终确定
2.          transient int size = 0;//集合中元素的数量
3.          //Node的内部类
4.          private static class Node<E> {
5.          E item;//当前元素
6.          Node<E> next;//指向下一个元素地址
7.          Node<E> prev;//上一个元素地址
8.   
9.          Node(Node<E> prev, E element, Node<E> next) {
10.            this.item = element;
11.            this.next = next;
12.            this.prev = prev;
13.        }
14.    }
15. 
16.        transient Node<E> first;//链表的首节点
17.        transient Node<E> last;//链表的尾节点
18.        //空构造器：
19.        public LinkedList() {
20.    }
21.        //添加元素操作：
22.        public boolean add(E e) {
23.        linkLast(e);
24.        return true;
25.    }
26.        void linkLast(E e) {//添加的元素e
27.        final Node<E> l = last;//将链表中的last节点给l 如果是第一个元素的话 l为null
28.                //将元素封装为一个Node具体的对象：
29.        final Node<E> newNode = new Node<>(l, e, null);
30.                //将链表的last节点指向新的创建的对象：
31.        last = newNode;
32.                
33.        if (l == null)//如果添加的是第一个节点
34.            first = newNode;//将链表的first节点指向为新节点
35.        else//如果添加的不是第一个节点 
36.            l.next = newNode;//将l的下一个指向为新的节点
37.        size++;//集合中元素数量加1操作
38.        modCount++;
39.    }
40.        //获取集合中元素数量
41.        public int size() {
42.        return size;
43.    }
44.        //通过索引得到元素：
45.        public E get(int index) {
46.        checkElementIndex(index);//健壮性考虑
47.        return node(index).item;
48.    }
49.        
50.    Node<E> node(int index) {
51.        //如果index在链表的前半段，那么从前往后找
52. 
53.        if (index < (size >> 1)) {
54.            Node<E> x = first;
55.            for (int i = 0; i < index; i++)
56.                x = x.next;
57.            return x;
58.        } else {//如果index在链表的后半段，那么从后往前找
59.            Node<E> x = last;
60.            for (int i = size - 1; i > index; i--)
61.                x = x.prev;
62.            return x;
63.        }
64.    }
65. 
66.}
```

#### 面试题：iterator(),Iterator,Iterable关系

【1】面试题：对应的关系：

![img](https://image.201068.xyz/assets/clip_image804.jpg)

【2】hasNext(),next()的具体实现： 

![img](https://image.201068.xyz/assets/clip_image806.jpg)

 

 

 

【3】增强for循环  底层也是通过迭代器实现的：

![img](https://image.201068.xyz/assets/clip_image808.jpg)

![img](https://image.201068.xyz/assets/clip_image810.jpg)

#### ListIterator迭代器

【1】加入字符串：

```
1.  package com.msb.test06;
2.   
3.  import java.util.ArrayList;
4.  import java.util.Iterator;
5.  import java.util.List;
6.   
7.  /**
8.   * @author : msb-zhaoss
9.   */
10.public class Test2 {
11.    //这是main方法，程序的入口
12.    public static void main(String[] args) {
13.        ArrayList<String> list = new ArrayList<>();
14.        list.add("aa");
15.        list.add("bb");
16.        list.add("cc");
17.        list.add("dd");
18.        list.add("ee");
19.        //在"cc"之后添加一个字符串"kk"
20.        Iterator<String> it = list.iterator();
21.        while(it.hasNext()){
22.            if("cc".equals(it.next())){
23.                list.add("kk");
24.            }
25.        }
26. 
27.    }
28.}
29. 
```

发现报错：

![img](https://image.201068.xyz/assets/clip_image812.jpg)

出错原因：就是迭代器和list同时对集合进行操作： 

![img](https://image.201068.xyz/assets/clip_image814.jpg)

 

解决办法：事情让一个“人”做 --》引入新的迭代器：ListIterator 

迭代和添加操作都是靠ListIterator来完成的： 

```
1.  package com.msb.test06;
2.   
3.  import java.util.ArrayList;
4.  import java.util.Iterator;
5.  import java.util.List;
6.  import java.util.ListIterator;
7.   
8.  /**
9.   * @author : msb-zhaoss
10. */
11.public class Test2 {
12.    //这是main方法，程序的入口
13.    public static void main(String[] args) {
14.        ArrayList<String> list = new ArrayList<>();
15.        list.add("aa");
16.        list.add("bb");
17.        list.add("cc");
18.        list.add("dd");
19.        list.add("ee");
20.        //在"cc"之后添加一个字符串"kk"
21.        ListIterator<String> it = list.listIterator();
22.        while(it.hasNext()){
23.            if("cc".equals(it.next())){
24.                it.add("kk");
25.            }
26.        }
27.        System.out.println(it.hasNext());
28.        System.out.println(it.hasPrevious());
29.        //逆向遍历：
30.        while(it.hasPrevious()){
31.            System.out.println(it.previous());
32.        }
33.        System.out.println(it.hasNext());
34.        System.out.println(it.hasPrevious());
35.        System.out.println(list);
36. 
37.    }
38.}
39. 
```

### Set接口

 

#### HashSet实现类的使用

【1】放入Integer类型数据： 

```
1.  package com.msb.test07;
2.   
3.  import java.util.HashSet;
4.   
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class TestInteger {
9.      //这是main方法，程序的入口
10.    public static void main(String[] args) {
11.        //创建一个HashSet集合：
12.        HashSet<Integer> hs = new HashSet<>();
13.        System.out.println(hs.add(19));//true
14.        hs.add(5);
15.        hs.add(20);
16.        System.out.println(hs.add(19));//false 这个19没有放入到集合中
17.        hs.add(41);
18.        hs.add(0);
19.        System.out.println(hs.size());//唯一，无序
20.        System.out.println(hs);
21. 
22.    }
23.}
24. 
```

【2】放入String类型数据： 

```
1.  package com.msb.test07;
2.   
3.  import java.util.HashSet;
4.   
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class TestString {
9.      //这是main方法，程序的入口
10.    public static void main(String[] args) {
11.        //创建一个HashSet集合：
12.        HashSet<String> hs = new HashSet<>();
13.        hs.add("hello");
14.        hs.add("apple");
15.        hs.add("banana");
16.        hs.add("html");
17.        hs.add("apple");
18.        hs.add("css");
19.        System.out.println(hs.size());
20.        System.out.println(hs);
21.    }
22.}
23. 
```

【3】放入自定义的引用数据类型的数据： 

```
1.  package com.msb.test07;
2.   
3.  import java.util.HashSet;
4.   
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class TestStudent {
9.      //这是main方法，程序的入口
10.    public static void main(String[] args) {
11.        //创建一个HashSet集合：
12.        HashSet<Student> hs = new HashSet<>();
13.        hs.add(new Student(19,"lili"));
14.        hs.add(new Student(20,"lulu"));
15.        hs.add(new Student(18,"feifei"));
16.        hs.add(new Student(19,"lili"));
17.        hs.add(new Student(10,"nana"));
18.        System.out.println(hs.size());
19.        System.out.println(hs);
20.    }
21.}
22. 
```

上面自定义的类型不满足 唯一，无序的特点。为什么呢？ 

 

【4】HashSet原理图：（简要原理图） 

![img](https://image.201068.xyz/assets/clip_image816.jpg)

【5】疑问： 

1.数组的长度是多少。 

2.数组的类型是什么？ 

3.hashCode，equals方法真的调用了吗？验证

4.底层表达式是什么？ 

5.同一个位置的数据 向前放  还是 向后放？ 

6.放入数组中的数据，是直接放的吗？是否封装为对象了？

 

#### LinkedHashSet使用

其实就是在HashSet的基础上，多了一个总的链表，这个总链表将放入的元素串在一起，方便有序的遍历：

（可以看到LinkedHashMap.Entry 继承自HashMap.Node 除了Node 本身有的几个属性外，额外增加了before after 用于指向前一个Entry 后一个Entry。也就是说，元素之间维持着一条总的链表数据结构。） 

 

![img](https://image.201068.xyz/assets/clip_image818.jpg)

 

代码：

```
1.  package com.msb.test07;
2.   
3.  import java.util.HashSet;
4.  import java.util.LinkedHashMap;
5.  import java.util.LinkedHashSet;
6.   
7.  /**
8.   * @author : msb-zhaoss
9.   */
10.public class TestInteger {
11.    //这是main方法，程序的入口
12.    public static void main(String[] args) {
13.        //创建一个HashSet集合：
14.        LinkedHashSet<Integer> hs = new LinkedHashSet<>();
15.        System.out.println(hs.add(19));//true
16.        hs.add(5);
17.        hs.add(20);
18.        System.out.println(hs.add(19));//false 这个19没有放入到集合中
19.        hs.add(41);
20.        hs.add(0);
21.        System.out.println(hs.size());//唯一，无序
22.        System.out.println(hs);
23.    }
24.}
25. 
```

 

#### 比较器的使用

【1】以int类型为案例： 

比较的思路：将比较的数据做差，然后返回一个int类型的数据，将这个int类型的数值 按照 =0 >0 <0 

```
1.  int a = 10;
2.          int b = 20;
3.          System.out.println(a-b); // =0  >0  <0
```

【2】比较String类型数据： 

String类实现了Comparable接口，这个接口中有一个抽象方法compareTo，String类中重写这个方法即可 

```
1.  String a = "A";
2.          String b = "B";
3.          System.out.println(a.compareTo(b));
4.   
```

【3】比较double类型数据： 

```
1.   double a = 9.6;
2.          double b = 9.3;
3.         /* System.out.println((int)(a-b));*/
4.          System.out.println(((Double) a).compareTo((Double) b));
```

【4】比较自定义的数据类型： 

（1）内部比较器： 

```
1.  package com.msb.test08;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class Student implements Comparable<Student>{
7.      private int age;
8.      private double height;
9.      private String name;
10. 
11.    public int getAge() {
12.        return age;
13.    }
14. 
15.    public void setAge(int age) {
16.        this.age = age;
17.    }
18. 
19.    public double getHeight() {
20.        return height;
21.    }
22. 
23.    public void setHeight(double height) {
24.        this.height = height;
25.    }
26. 
27.    public String getName() {
28.        return name;
29.    }
30. 
31.    public void setName(String name) {
32.        this.name = name;
33.    }
34. 
35.    public Student(int age, double height, String name) {
36.        this.age = age;
37.        this.height = height;
38.        this.name = name;
39.    }
40. 
41.    @Override
42.    public String toString() {
43.        return "Student{" +
44.                "age=" + age +
45.                ", height=" + height +
46.                ", name='" + name + '\'' +
47.                '}';
48.    }
49. 
50.    @Override
51.    public int compareTo(Student o) {
52.        //按照年龄进行比较：
53.        /*return this.getAge() - o.getAge();*/
54.        //按照身高比较
55.        /*return ((Double)(this.getHeight())).compareTo((Double)(o.getHeight()));*/
56.        //按照名字比较：
57.        return this.getName().compareTo(o.getName());
58.    }
59.}
60. 
```

 

```
1.  package com.msb.test08;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class Test02 {
7.      //这是main方法，程序的入口
8.      public static void main(String[] args) {
9.          //比较两个学生：
10.        Student s1 = new Student(14,160.5,"alili");
11.        Student s2 = new Student(14,170.5,"bnana");
12.        System.out.println(s1.compareTo(s2));
13.    }
14.}
15. 
```

（2）外部比较器： 

```
1.  package com.msb.test09;
2.   
3.  import java.util.Comparator;
4.   
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class Student{
9.      private int age;
10.    private double height;
11.    private String name;
12. 
13.    public int getAge() {
14.        return age;
15.    }
16. 
17.    public void setAge(int age) {
18.        this.age = age;
19.    }
20. 
21.    public double getHeight() {
22.        return height;
23.    }
24. 
25.    public void setHeight(double height) {
26.        this.height = height;
27.    }
28. 
29.    public String getName() {
30.        return name;
31.    }
32. 
33.    public void setName(String name) {
34.        this.name = name;
35.    }
36. 
37.    public Student(int age, double height, String name) {
38.        this.age = age;
39.        this.height = height;
40.        this.name = name;
41.    }
42. 
43.    @Override
44.    public String toString() {
45.        return "Student{" +
46.                "age=" + age +
47.                ", height=" + height +
48.                ", name='" + name + '\'' +
49.                '}';
50.    }
51. 
52. 
53.}
54. 
55. 
56. 
57.class BiJiao01 implements Comparator<Student> {
58.    @Override
59.    public int compare(Student o1, Student o2) {
60.        //比较年龄：
61.        return o1.getAge()-o2.getAge();
62.    }
63.}
64. 
65.class BiJiao02 implements Comparator<Student> {
66.    @Override
67.    public int compare(Student o1, Student o2) {
68.        //比较姓名：
69.        return o1.getName().compareTo(o2.getName());
70.    }
71.}
```

 

```
1.  class BiJiao03 implements Comparator<Student> {
2.      @Override
3.      public int compare(Student o1, Student o2) {
4.          //在年龄相同的情况下 比较身高  年龄不同比较年龄
5.          if((o1.getAge()-o2.getAge())==0){
6.              return ((Double)(o1.getHeight())).compareTo((Double)(o2.getHeight()));
7.          }else{//年龄不一样
8.              return o1.getAge()-o2.getAge();
9.          }
10.    }
11.}
```

 

```
1.  package com.msb.test09;
2.   
3.  import com.msb.test09.Student;
4.   
5.  import java.util.Comparator;
6.   
7.  /**
8.   * @author : msb-zhaoss
9.   */
10.public class Test02 {
11.    //这是main方法，程序的入口
12.    public static void main(String[] args) {
13.        //比较两个学生：
14.        Student s1 = new Student(9,160.5,"alili");
15.        Student s2 = new Student(14,170.5,"bnana");
16.        //获取外部比较器：
17.        Comparator bj1 = new BiJiao03();
18.        System.out.println(bj1.compare(s1, s2));
19.    }
20.}
21. 
```

【5】外部比较器和内部比较器 谁好呀？ 

答案：外部比较器，多态，扩展性好

 

 

#### TreeSet实现类的使用

【1】存入Integer类型数据：（底层利用的是内部比较器） 

```
1.  package com.msb.test10;
2.   
3.  import java.util.TreeSet;
4.   
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class Test01 {
9.      //这是main方法，程序的入口
10.    public static void main(String[] args) {
11.        //创建一个TreeSet:
12.        TreeSet<Integer> ts = new TreeSet<>();
13.        ts.add(12);
14.        ts.add(3);
15.        ts.add(7);
16.        ts.add(9);
17.        ts.add(3);
18.        ts.add(16);
19.        System.out.println(ts.size());
20.        System.out.println(ts);
21. 
22.    }
23.}
24. 
```

特点：唯一，无序（没有按照输入顺序进行输出）， 有序（按照升序进行遍历） 

 

【2】原理：底层：二叉树（数据结构中的一个逻辑结构） 

![img](https://image.201068.xyz/assets/clip_image820.jpg)

 

【3】放入String类型数据：（底层实现类内部比较器） 

```
1.  package com.msb.test10;
2.   
3.  import java.util.TreeSet;
4.   
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class Test02 {
9.      //这是main方法，程序的入口
10.    public static void main(String[] args) {
11.        //创建一个TreeSet:
12.        TreeSet<String> ts = new TreeSet<>();
13.        ts.add("elili");
14.        ts.add("blili");
15.        ts.add("alili");
16.        ts.add("elili");
17.        ts.add("clili");
18.        ts.add("flili");
19.        ts.add("glili");
20.        System.out.println(ts.size());
21.        System.out.println(ts);
22.    }
23.}
24. 
```

 

【4】想放入自定义的Student类型的数据： 

（1）利用内部比较器： 

```
1.  package com.msb.test10;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class Student implements Comparable<Student> {
7.      private int age;
8.      private String name;
9.   
10.    public int getAge() {
11.        return age;
12.    }
13. 
14.    public void setAge(int age) {
15.        this.age = age;
16.    }
17. 
18.    public String getName() {
19.        return name;
20.    }
21. 
22.    public void setName(String name) {
23.        this.name = name;
24.    }
25. 
26.    public Student(int age, String name) {
27.        this.age = age;
28.        this.name = name;
29.    }
30. 
31.    @Override
32.    public String toString() {
33.        return "Student{" +
34.                "age=" + age +
35.                ", name='" + name + '\'' +
36.                '}';
37.    }
38. 
39. 
40.    @Override
41.    public int compareTo(Student o) {
42.        return this.getAge()-o.getAge();
43.    }
44.}
45. 
```

 

```
1.  package com.msb.test10;
2.   
3.  import java.util.TreeSet;
4.   
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class Test03 {
9.      //这是main方法，程序的入口
10.    public static void main(String[] args) {
11.        //创建一个TreeSet:
12.        TreeSet<Student> ts = new TreeSet<>();
13.        ts.add(new Student(10,"elili"));
14.        ts.add(new Student(8,"blili"));
15.        ts.add(new Student(4,"alili"));
16.        ts.add(new Student(9,"elili"));
17.        ts.add(new Student(10,"flili"));
18.        ts.add(new Student(1,"dlili"));
19.        System.out.println(ts.size());
20.        System.out.println(ts);
21.    }
22.}
23. 
```

（2）通过外部比较器： 

```
1.  package com.msb.test10;
2.   
3.  import java.util.Comparator;
4.   
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class Student  {
9.      private int age;
10.    private String name;
11. 
12.    public int getAge() {
13.        return age;
14.    }
15. 
16.    public void setAge(int age) {
17.        this.age = age;
18.    }
19. 
20.    public String getName() {
21.        return name;
22.    }
23. 
24.    public void setName(String name) {
25.        this.name = name;
26.    }
27. 
28.    public Student(int age, String name) {
29.        this.age = age;
30.        this.name = name;
31.    }
32. 
33.    @Override
34.    public String toString() {
35.        return "Student{" +
36.                "age=" + age +
37.                ", name='" + name + '\'' +
38.                '}';
39.    }
40. 
41. 
42. 
43.}
44. 
45.class BiJiao implements Comparator<Student>{
46.    @Override
47.    public int compare(Student o1, Student o2) {
48.        return o1.getName().compareTo(o2.getName());
49.    }
50.}
51. 
```

 

```
1.  package com.msb.test10;
2.   
3.  import java.util.Comparator;
4.  import java.util.TreeSet;
5.   
6.  /**
7.   * @author : msb-zhaoss
8.   */
9.  public class Test03 {
10.    //这是main方法，程序的入口
11.    public static void main(String[] args) {
12.        //创建一个TreeSet:
13.        //利用外部比较器，必须自己制定：
14.        Comparator<Student> com = new BiJiao();
15.        TreeSet<Student> ts = new TreeSet<>(com);//一旦指定外部比较器，那么就会按照外部比较器来比较
16.        ts.add(new Student(10,"elili"));
17.        ts.add(new Student(8,"blili"));
18.        ts.add(new Student(4,"alili"));
19.        ts.add(new Student(9,"elili"));
20.        ts.add(new Student(10,"flili"));
21.        ts.add(new Student(1,"dlili"));
22.        System.out.println(ts.size());
23.        System.out.println(ts);
24.    }
25.}
26. 
```

实际开发中利用外部比较器多，因为扩展性好（多态）

 

换一种写法：

```
1.  package com.msb.test10;
2.   
3.  import java.util.Comparator;
4.  import java.util.TreeSet;
5.   
6.  /**
7.   * @author : msb-zhaoss
8.   */
9.  public class Test03 {
10.    //这是main方法，程序的入口
11.    public static void main(String[] args) {
12.        //创建一个TreeSet:
13.        //利用外部比较器，必须自己制定：
14.        /*Comparator<Student> com = new Comparator<Student>() {
15.            @Override
16.            public int compare(Student o1, Student o2) {
17.                return o1.getName().compareTo(o2.getName());
18.            }
19.        };*/
20.        TreeSet<Student> ts = new TreeSet<>(new Comparator<Student>() {
21.            @Override
22.            public int compare(Student o1, Student o2) {
23.                return o1.getName().compareTo(o2.getName());
24.            }
25.        });//一旦指定外部比较器，那么就会按照外部比较器来比较
26.        ts.add(new Student(10,"elili"));
27.        ts.add(new Student(8,"blili"));
28.        ts.add(new Student(4,"alili"));
29.        ts.add(new Student(9,"elili"));
30.        ts.add(new Student(10,"flili"));
31.        ts.add(new Student(1,"dlili"));
32.        System.out.println(ts.size());
33.        System.out.println(ts);
34.    }
35.}
36. 
```

【5】TreeSet底层的二叉树的遍历是按照升序的结果出现的，这个升序是靠中序遍历得到的：

![img](https://image.201068.xyz/assets/clip_image822.jpg)

 

 

#### Collection部分整体结构图

![img](https://image.201068.xyz/assets/clip_image824.jpg)

 

## Map接口

 

### 常用方法

```
1.  package com.msb.test11;
2.   
3.  import java.util.Collection;
4.  import java.util.HashMap;
5.  import java.util.Map;
6.  import java.util.Set;
7.   
8.  /**
9.   * @author : msb-zhaoss
10. */
11.public class Test01 {
12.    //这是main方法，程序的入口
13.    public static void main(String[] args) {
14.        /*
15.        增加：put(K key, V value)
16.        删除：clear() remove(Object key)
17.        修改：
18.        查看：entrySet() get(Object key) keySet() size() values()
19.        判断：containsKey(Object key) containsValue(Object value)
20.            equals(Object o) isEmpty()
21.         */
22.        //创建一个Map集合：无序，唯一
23.        Map<String,Integer> map = new HashMap<>();
24.        System.out.println(map.put("lili", 10101010));
25.        map.put("nana",12345234);
26.        map.put("feifei",34563465);
27.        System.out.println(map.put("lili", 34565677));
28.        map.put("mingming",12323);
29.        /*map.clear();清空*/
30.        /*map.remove("feifei");移除*/
31.        System.out.println(map.size());
32.        System.out.println(map);
33. 
34.        System.out.println(map.containsKey("lili"));
35.        System.out.println(map.containsValue(12323));
36.        Map<String,Integer> map2 = new HashMap<>();
37.        System.out.println(map2.put("lili", 10101010));
38.        map2.put("nana",12345234);
39.        map2.put("feifei",34563465);
40.        System.out.println(map2.put("lili", 34565677));
41.        map2.put("mingming2",12323);
42.        System.out.println(map==map2);
43.        System.out.println(map.equals(map2));//equals进行了重写，比较的是集合中的值是否一致
44. 
45.        System.out.println("判断是否为空："+map.isEmpty());
46. 
47.        System.out.println(map.get("nana"));
48.        System.out.println("-----------------------------------");
49.        //keySet()对集合中的key进行遍历查看：
50.        Set<String> set = map.keySet();
51.        for(String s:set){
52.            System.out.println(s);
53.        }
54.        System.out.println("-----------------------------------");
55.        //values()对集合中的value进行遍历查看：
56.        Collection<Integer> values = map.values();
57.        for(Integer i:values){
58.            System.out.println(i);
59.        }
60.        System.out.println("-----------------------------------");
61.        //get(Object key) keySet()
62.        Set<String> set2 = map.keySet();
63.        for(String s:set2){
64.            System.out.println(map.get(s));
65.        }
66.        System.out.println("-----------------------------------");
67.        //entrySet()
68.        Set<Map.Entry<String, Integer>> entries = map.entrySet();
69.        for(Map.Entry<String, Integer> e:entries){
70.            System.out.println(e.getKey()+"----"+e.getValue());
71.        }
72.    }
73.}
74. 
```

 

### TreeMap

【1】key的类型为String类型： 

```
1.  package com.msb.test11;
2.   
3.  import java.util.Map;
4.  import java.util.TreeMap;
5.   
6.  /**
7.   * @author : msb-zhaoss
8.   */
9.  public class Test02 {
10.    //这是main方法，程序的入口
11.    public static void main(String[] args) {
12.        Map<String,Integer> map = new TreeMap<>();
13.        map.put("blili",1234);
14.        map.put("alili",2345);
15.        map.put("blili",5467);
16.        map.put("clili",5678);
17.        map.put("dlili",2345);
18.        System.out.println(map.size());
19.        System.out.println(map);
20.    }
21.}
22. 
```

【2】key的类型是一个自定义的引用数据类型： 

（1）内部比较器： 

```
1.  package com.msb.test11;
2.   
3.  import java.util.Map;
4.  import java.util.TreeMap;
5.   
6.  /**
7.   * @author : msb-zhaoss
8.   */
9.  public class Test03 {
10.    //这是main方法，程序的入口
11.    public static void main(String[] args) {
12.        Map<Student,Integer> map = new TreeMap<>();
13.        map.put(new Student(19,"blili",170.5),1001);
14.        map.put(new Student(18,"blili",150.5),1003);
15.        map.put(new Student(19,"alili",180.5),1023);
16.        map.put(new Student(17,"clili",140.5),1671);
17.        map.put(new Student(10,"dlili",160.5),1891);
18.        System.out.println(map);
19.        System.out.println(map.size());
20.    }
21.}
22. 
```

 

```
1.  package com.msb.test11;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class Student implements Comparable<Student>{
7.      private int age;
8.      private String name;
9.      private double height;
10. 
11.    public int getAge() {
12.        return age;
13.    }
14. 
15.    public void setAge(int age) {
16.        this.age = age;
17.    }
18. 
19.    public String getName() {
20.        return name;
21.    }
22. 
23.    public void setName(String name) {
24.        this.name = name;
25.    }
26. 
27.    public double getHeight() {
28.        return height;
29.    }
30. 
31.    public void setHeight(double height) {
32.        this.height = height;
33.    }
34. 
35.    public Student(int age, String name, double height) {
36.        this.age = age;
37.        this.name = name;
38.        this.height = height;
39.    }
40. 
41.    @Override
42.    public String toString() {
43.        return "Student{" +
44.                "age=" + age +
45.                ", name='" + name + '\'' +
46.                ", height=" + height +
47.                '}';
48.    }
49. 
50.    @Override
51.    public int compareTo(Student o) {
52.       /* return this.getAge()-o.getAge();*/
53.        return this.getName().compareTo(o.getName());
54.    }
55.}
56. 
```

 

（2）外部比较器： 

```
1.  package com.msb.test11;
2.   
3.  import java.util.Comparator;
4.  import java.util.Map;
5.  import java.util.TreeMap;
6.   
7.  /**
8.   * @author : msb-zhaoss
9.   */
10.public class Test03 {
11.    //这是main方法，程序的入口
12.    public static void main(String[] args) {
13.        Map<Student,Integer> map = new TreeMap<>(new Comparator<Student>() {
14.            @Override
15.            public int compare(Student o1, Student o2) {
16.                return ((Double)(o1.getHeight())).compareTo((Double)(o2.getHeight()));
17.            }
18.        });
19.        map.put(new Student(19,"blili",170.5),1001);
20.        map.put(new Student(18,"blili",150.5),1003);
21.        map.put(new Student(19,"alili",180.5),1023);
22.        map.put(new Student(17,"clili",140.5),1671);
23.        map.put(new Student(10,"dlili",160.5),1891);
24.        System.out.println(map);
25.        System.out.println(map.size());
26.    }
27.}
28. 
```

 

 

### Map部分整体结构图

![img](https://image.201068.xyz/assets/clip_image826.jpg)

 

### 源码部分

#### HashMap

##### 代码展示特性

```
1.  package com.msb.test03;
2.   
3.  import java.util.HashMap;
4.   
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class Test {
9.      //这是main方法，程序的入口
10.    public static void main(String[] args) {
11.        //JDK1.7以后支持后面的<>中内容可以不写
12.        HashMap<Integer,String> hm = new HashMap<>();
13.        System.out.println(hm.put(12,"丽丽"));
14.        System.out.println(hm.put(7,"菲菲"));
15.        System.out.println(hm.put(19,"露露"));
16.        System.out.println(hm.put(12,"明明"));
17.        System.out.println(hm.put(6,"莹莹"));
18.        System.out.println("集合的长度："+hm.size());
19.        System.out.println("集合中内容查看："+hm);
20. 
21.    }
22.}
23. 
```

结果展示：

![img](https://image.201068.xyz/assets/clip_image828.jpg)

 

##### 先演示原理

先演示原理图，再看源码，直接看的话，有的人接不上就蒙了：

相当于先看原理，然后从源码中验证这个原理是否正确：把图搞懂了，就是事倍功半的效果

原理如下：(JDK1.7) 

![img](https://image.201068.xyz/assets/clip_image830.jpg)

 

 

##### 源码（JDK1.7版本）

```
1.  public class HashMap<K,V>
2.      extends AbstractMap<K,V> //【1】继承的AbstractMap中，已经实现了Map接口
3.          //【2】又实现了这个接口，多余，但是设计者觉得没有必要删除，就这么地了
4.      implements Map<K,V>, Cloneable, Serializable{
5.                  
6.                  
7.          //【3】后续会用到的重要属性：先粘贴过来：
8.      static final int DEFAULT_INITIAL_CAPACITY = 16;//哈希表主数组的默认长度
9.          //定义了一个float类型的变量，以后作为：默认的装填因子，加载因子是表示Hsah表中元素的填满的程度
10.        //太大容易引起哈西冲突，太小容易浪费  0.75是经过大量运算后得到的最好值
11.        //这个值其实可以自己改，但是不建议改，因为这个0.75是大量运算得到的
12.        static final float DEFAULT_LOAD_FACTOR = 0.75f;
13.        transient Entry<K,V>[] table;//主数组,每个元素为Entry类型
14.        transient int size;
15.        int threshold;//数组扩容的界限值,门槛值   16*0.75=12 
16.        final float loadFactor;//用来接收装填因子的变量
17.        
18.        //【4】查看构造器：内部相当于：this(16,0.75f);调用了当前类中的带参构造器
19.        public HashMap() {
20.        this(DEFAULT_INITIAL_CAPACITY, DEFAULT_LOAD_FACTOR);
21.    }
22.        //【5】本类中带参数构造器：--》作用给一些数值进行初始化的！
23.        public HashMap(int initialCapacity, float loadFactor) {
24. 
25.        //【6】给capacity赋值，capacity的值一定是 大于你传进来的initialCapacity 的 最小的 2的倍数
26.        int capacity = 1;
27.        while (capacity < initialCapacity)
28.            capacity <<= 1;
29. 
30.                //【7】给loadFactor赋值，将装填因子0.75赋值给loadFactor
31.        this.loadFactor = loadFactor;
32.                //【8】数组扩容的界限值,门槛值
33.        threshold = (int)Math.min(capacity * loadFactor, MAXIMUM_CAPACITY + 1);
34.                
35.                //【9】给table数组赋值，初始化数组长度为16
36.        table = new Entry[capacity];
37.                   
38.    }
39.        //【10】调用put方法：
40.        public V put(K key, V value) {
41.                //【11】对空值的判断
42.        if (key == null)
43.            return putForNullKey(value);
44.                //【12】调用hash方法，获取哈希码
45.        int hash = hash(key);
46.                //【14】得到key对应在数组中的位置
47.        int i = indexFor(hash, table.length);
48.                //【16】如果你放入的元素，在主数组那个位置上没有值，e==null  那么下面这个循环不走
49.                //当在同一个位置上放入元素的时候
50.        for (Entry<K,V> e = table[i]; e != null; e = e.next) {
51.            Object k;
52.                        //哈希值一样  并且  equals相比一样   
53.                        //(k = e.key) == key  如果是一个对象就不用比较equals了
54.            if (e.hash == hash && ((k = e.key) == key || key.equals(k))) {
55.                V oldValue = e.value;
56.                e.value = value;
57.                e.recordAccess(this);
58.                return oldValue;
59.            }
60.        }
61. 
62.        modCount++;
63.                //【17】走addEntry添加这个节点的方法：
64.        addEntry(hash, key, value, i);
65.        return null;
66.    }
67.        
68.        //【13】hash方法返回这个key对应的哈希值，内部进行二次散列，为了尽量保证不同的key得到不同的哈希码！
69.        final int hash(Object k) {
70.        int h = 0;
71.        if (useAltHashing) {
72.            if (k instanceof String) {
73.                return sun.misc.Hashing.stringHash32((String) k);
74.            }
75.            h = hashSeed;
76.        }
77.                //k.hashCode()函数调用的是key键值类型自带的哈希函数，
78.                //由于不同的对象其hashCode()有可能相同，所以需对hashCode()再次哈希，以降低相同率。
79.        h ^= k.hashCode();
80. 
81.        // This function ensures that hashCodes that differ only by
82.        // constant multiples at each bit position have a bounded
83.        // number of collisions (approximately 8 at default load factor).
84.                /*
85.                接下来的一串与运算和异或运算，称之为“扰动函数”，
86.                扰动的核心思想在于使计算出来的值在保留原有相关特性的基础上，
87.                增加其值的不确定性，从而降低冲突的概率。
88.                不同的版本实现的方式不一样，但其根本思想是一致的。
89.                往右移动的目的，就是为了将h的高位利用起来，减少哈西冲突
90.                */
91.        h ^= (h >>> 20) ^ (h >>> 12);
92.        return h ^ (h >>> 7) ^ (h >>> 4);
93.    }
94.        //【15】返回int类型数组的坐标
95.        static int indexFor(int h, int length) {
96.                //其实这个算法就是取模运算：h%length，取模效率不如位运算
97.        return h & (length-1);
98.    }
99.        //【18】调用addEntry
100.         void addEntry(int hash, K key, V value, int bucketIndex) {
101.                 //【25】size的大小  大于 16*0.75=12的时候，比如你放入的是第13个，这第13个你打算放在没有元素的位置上的时候
102.         if ((size >= threshold) && (null != table[bucketIndex])) {
103.                         //【26】主数组扩容为2倍
104.             resize(2 * table.length);
105.                         //【30】重新调整当前元素的hash码
106.             hash = (null != key) ? hash(key) : 0;
107.                         //【31】重新计算元素位置
108.             bucketIndex = indexFor(hash, table.length);
109.         }
110.                 //【19】将hash,key,value,bucketIndex位置  封装为一个Entry对象：
111.         createEntry(hash, key, value, bucketIndex);
112.     }
113.         //【20】
114.         void createEntry(int hash, K key, V value, int bucketIndex) {
115.                 //【21】获取bucketIndex位置上的元素给e
116.         Entry<K,V> e = table[bucketIndex];
117.                 //【22】然后将hash, key, value封装为一个对象，然后将下一个元素的指向为e （链表的头插法）
118.                 //【23】将新的Entry放在table[bucketIndex]的位置上
119.         table[bucketIndex] = new Entry<>(hash, key, value, e);
120.                 //【24】集合中加入一个元素 size+1
121.         size++;
122.     }
123.     //【27】
124.         void resize(int newCapacity) {
125.         Entry[] oldTable = table;
126.         int oldCapacity = oldTable.length;
127.         if (oldCapacity == MAXIMUM_CAPACITY) {
128.             threshold = Integer.MAX_VALUE;
129.             return;
130.         }
131.                 //【28】创建长度为newCapacity的数组
132.         Entry[] newTable = new Entry[newCapacity];
133.         boolean oldAltHashing = useAltHashing;
134.         useAltHashing |= sun.misc.VM.isBooted() &&
135.                 (newCapacity >= Holder.ALTERNATIVE_HASHING_THRESHOLD);
136.         boolean rehash = oldAltHashing ^ useAltHashing;
137.                 //【28.5】转让方法：将老数组中的东西都重新放入新数组中
138.         transfer(newTable, rehash);
139.                 //【29】老数组替换为新数组
140.         table = newTable;
141.                 //【29.5】重新计算
142.         threshold = (int)Math.min(newCapacity * loadFactor, MAXIMUM_CAPACITY + 1);
143.     }
144.         //【28.6】
145.         void transfer(Entry[] newTable, boolean rehash) {
146.         int newCapacity = newTable.length;
147.         for (Entry<K,V> e : table) {
148.             while(null != e) {
149.                 Entry<K,V> next = e.next;
150.                 if (rehash) {
151.                     e.hash = null == e.key ? 0 : hash(e.key);
152.                 }
153.                                 //【28.7】将哈希值，和新的数组容量传进去，重新计算key在新数组中的位置
154.                 int i = indexFor(e.hash, newCapacity);
155.                                 //【28.8】头插法
156.                 e.next = newTable[i];//获取链表上元素给e.next
157.                 newTable[i] = e;//然后将e放在i位置 
158.                 e = next;//e再指向下一个节点继续遍历
159.             }
160.         }
161.     }
162.  
163.  
164.  
165.  
166.  
167.  
168. }
```

 

##### 细节讲解：主数组的长度为2的倍数

【1】主数组的长度为2的倍数， 

![img](https://image.201068.xyz/assets/clip_image832.jpg)

 

因为这个length的长度，会影响 key的位置： 

key的位置的计算： 

![img](https://image.201068.xyz/assets/clip_image834.jpg)

实际上这个算法就是：  h%length  ,但是取模的话  效率太低，所以用位运算效率会很高。

 

原因1： 

![img](https://image.201068.xyz/assets/clip_image836.jpg)和![img](https://image.201068.xyz/assets/clip_image838.jpg)等效的前提就是  length必须是2的整数倍 

原因2：如果不是2的整数倍，那么 哈西碰撞 哈西冲突的概率就高了很多 

 

位运算 就  涉及  到  length是不是2的整数倍： 

比如是2的整数倍： 

![img](https://image.201068.xyz/assets/clip_image840.jpg) : 

![img](https://image.201068.xyz/assets/clip_image842.jpg)

并且这个得到的索引值，一定在 0-15之间（数组是16的时候）： 

![img](https://image.201068.xyz/assets/clip_image844.jpg)

当然如果你扩容后数组长度为 32，那么这个索引就在0-31之间 

 

比如如果不是2的整数倍： 

![img](https://image.201068.xyz/assets/clip_image846.jpg)

发现：如果不是2的整数倍，那么 哈西碰撞 哈西冲突的概率就高了很多 

##### 细节讲解：装填因子0.75的原因

如果装填因子是1， 那么数组满了再扩容，可以做到  最大的空间利用率 

但是这是一个理想状态，元素不可能完全的均匀分布，很可能就哈西碰撞产生链表了。产生链表的话 查询时间就长了。 

---》空间好，时间不好 

 

那么有人说 ，把装填因子搞小一点，0.5，  如果是0.5的话，就浪费空间，但是可以做到 到0.5就扩容 ，然后哈西碰撞就少，

不产生链表的话，那么查询效率很高   

---》时间好，空间不好 

 

所以在空间和时间中，![img](https://image.201068.xyz/assets/clip_image848.jpg) 

取中间值，平衡这个因素 就取值为 0.75 

![img](https://image.201068.xyz/assets/clip_image850.jpg)

 

##### HashSet底层原理

```
1.   
2.  public class HashSet<E>{
3.      //重要属性：
4.      private transient HashMap<E,Object> map;
5.      private static final Object PRESENT = new Object();
6.      //构造器：
7.      public HashSet() {
8.          map = new HashMap<>();//HashSet底层就是利用HashMap来完成的
9.      }
10.        
11.    public boolean add(E e) {
12.        return map.put(e, PRESENT)==null;
13.    }      
14.}
```

#### TreeMap

【1】原理大致介绍：

![img](https://image.201068.xyz/assets/clip_image852.jpg)

【2】源码：

```
1.  public class TreeMap<K,V>{
2.          //重要属性：
3.          //外部比较器：
4.          private final Comparator<? super K> comparator;
5.          //树的根节点：
6.          private transient Entry<K,V> root = null;
7.          //集合中元素的数量：
8.          private transient int size = 0;
9.          //空构造器:
10.        public TreeMap() {
11.        comparator = null;//如果使用空构造器，那么底层就不使用外部比较器
12.    }
13.        //有参构造器：
14.        public TreeMap(Comparator<? super K> comparator) {
15.        this.comparator = comparator;//如果使用有参构造器，那么就相当于指定了外部比较器
16.    }
17.        
18.        public V put(K key, V value) {//k,V的类型在创建对象的时候确定了
19.        //如果放入的是第一对元素，那么t的值为null
20.        Entry<K,V> t = root;//在放入第二个节点的时候，root已经是根节点了
21.                //如果放入的是第一个元素的话，走入这个if中：
22.        if (t == null) {
23.                        //自己跟自己比
24.            compare(key, key); // type (and possibly null) check
25.                        //根节点确定为root
26.            root = new Entry<>(key, value, null);
27.                        //size值变为1
28.            size = 1;
29.            modCount++;
30.            return null;
31.        }
32.                
33.        int cmp;
34.        Entry<K,V> parent;
35.        // split comparator and comparable paths
36.                //将外部比较器赋给cpr:
37.        Comparator<? super K> cpr = comparator;
38.                //cpr不等于null，意味着你刚才创建对象的时候调用了有参构造器，指定了外部比较器
39.        if (cpr != null) {
40.            do {
41.                parent = t;
42.                cmp = cpr.compare(key, t.key);//将元素的key值做比较
43.                                //cmp返回的值就是int类型的数据：
44.                                //要是这个值《0 =0  》0
45.                if (cmp < 0)
46.                    t = t.left;
47.                else if (cmp > 0)
48.                    t = t.right;
49.                else//cpm==0
50.                                //如果key的值一样，那么新的value替换老的value  但是key不变 因为key是唯一的
51.                    return t.setValue(value);
52.            } while (t != null);
53.        }
54.                //cpr等于null，意味着你刚才创建对象的时候调用了空构造器，没有指定外部比较器，使用内部比较器
55.        else {
56.            if (key == null)
57.                throw new NullPointerException();
58.            Comparable<? super K> k = (Comparable<? super K>) key;
59.            do {
60.                parent = t;
61.                cmp = k.compareTo(t.key);//将元素的key值做比较
62.                if (cmp < 0)
63.                    t = t.left;
64.                else if (cmp > 0)
65.                    t = t.right;
66.                else
67.                    return t.setValue(value);
68.            } while (t != null);
69.        }
70.        Entry<K,V> e = new Entry<>(key, value, parent);
71.        if (cmp < 0)
72.            parent.left = e;
73.        else
74.            parent.right = e;
75.        fixAfterInsertion(e);
76.        size++;//size加1 操作
77.        modCount++;
78.        return null;
79.    }
80.        
81.        
82.}
83. 
84. 
85. 
86. static final class Entry<K,V> implements Map.Entry<K,V> {
87.        K key;
88.        V value;
89.        Entry<K,V> left = null;
90.        Entry<K,V> right = null;
91.        Entry<K,V> parent;
92.        boolean color = BLACK;
93. }
```

##### TreeSet源码

```
1.  public class TreeSet<E> extends AbstractSet<E>
2.      implements NavigableSet<E>, Cloneable, java.io.Serializable{
3.                  //重要属性：
4.                  private transient NavigableMap<E,Object> m;
5.                  private static final Object PRESENT = new Object();
6.                  
7.                  //在调用空构造器的时候，底层创建了一个TreeMap
8.                  public TreeSet() {
9.                          this(new TreeMap<E,Object>());
10.                }
11.                
12.                TreeSet(NavigableMap<E,Object> m) {
13.                        this.m = m;
14.                }
15.                
16.                public boolean add(E e) {
17.        return m.put(e, PRESENT)==null;
18.    }
19.                
20.                
21.        }
```

 

 



## Collections工具类

```
1.  package com.msb.test12;
2.   
3.  import java.util.ArrayList;
4.  import java.util.Collections;
5.   
6.  /**
7.   * @author : msb-zhaoss
8.   */
9.  public class Test01 {
10.    //这是main方法，程序的入口
11.    public static void main(String[] args) {
12.        //Collections不支持创建对象，因为构造器私有化了
13.        /*Collections cols = new Collections();*/
14.        //里面的属性和方法都是被static修饰，我们可以直接用类名.去调用即可：
15.        //常用方法：
16.        //addAll：
17.        ArrayList<String> list = new ArrayList<>();
18.        list.add("cc");
19.        list.add("bb");
20.        list.add("aa");
21.        Collections.addAll(list,"ee","dd","ff");
22.        Collections.addAll(list,new String[]{"gg","oo","pp"});
23.        System.out.println(list);
24.        //binarySearch必须在有序的集合中查找：--》排序：
25.        Collections.sort(list);//sort提供的是升序排列
26.        System.out.println(list);
27.        //binarySearch
28.        System.out.println(Collections.binarySearch(list, "cc"));
29. 
30.        //copy:替换方法
31.        ArrayList<String> list2 = new ArrayList<>();
32.        Collections.addAll(list2,"tt","ss");
33.        Collections.copy(list,list2);//将list2的内容替换到list上去
34.        System.out.println(list);
35.        System.out.println(list2);
36. 
37.        //fill 填充
38.        Collections.fill(list2,"yyy");
39.        System.out.println(list2);
40. 
41. 
42. 
43.    }
44.}
45. 
```

 

 

# 第11章_集合补充

 

## 常见基础集合汇总

![img](https://image.201068.xyz/assets/clip_image854.jpg)

 

## 数据结构：栈

数据结构分为： 

（1）逻辑结构 ：--》思想上的结构--》卧室，厨房，卫生间 ---》线性表（数组，链表），图，树，栈，队列 

（2）物理结构 ：--》真实结构--》钢筋混凝土+牛顿力学------》紧密结构（顺序结构），跳转结构（链式结构） 

栈： 

特点：后进先出（LIFO - last in first out）： 

![img](https://image.201068.xyz/assets/clip_image856.jpg)![img](https://image.201068.xyz/assets/clip_image858.jpg)

实际应用： 

（1）内存分析：形参，局部变量放入栈中。放入的那个区域的数据结构就是按照栈来做的。

（堆：利用完全二叉树的结构来维护一组数据） 

![img](https://image.201068.xyz/assets/clip_image860.jpg)

（2）网络浏览器多会将用户最近访问过的网址组织为一个栈。这样，用户每访问一个新页面，其地址就会被存放至栈顶；而用户每按下一次“后退”按钮，即可沿相反的次序访问此前刚访问过的页面。

（3）主流的文本编辑器也大都支持编辑操作的历史记录功能（ctrl + z：撤销，ctrl + y：恢复），用户的编辑操作被依次记录在一个栈中。一旦出现误操作，用户只需按下“撤销”按钮，即可取消最近一次操作并回到此前的编辑状态。

 

## Stack

```
1.  package com.msb.test01;
2.   
3.  import java.util.Stack;
4.   
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class Test {
9.      //这是main方法，程序的入口
10.    public static void main(String[] args) {
11.        /*
12.        Stack是Vector的子类，Vector里面两个重要的属性：
13.        Object[] elementData;底层依然是一个数组
14.        int elementCount;数组中的容量
15.         */
16.        Stack s = new Stack();
17.        s.add("A");
18.        s.add("B");
19.        s.add("C");
20.        s.add("D");
21.        System.out.println(s);//[A, B, C, D]
22.        System.out.println("栈是否为空：" + s.empty());
23. 
24.        System.out.println("查看栈顶的数据，但是不移除：" + s.peek());
25.        System.out.println(s);
26. 
27.        System.out.println("查看栈顶的数据，并且不移除：" + s.pop());
28.        System.out.println(s);
29. 
30.        s.push("D");//和add方法执行的功能一样，就是返回值不同
31.        System.out.println(s);
32. 
33.    }
34.}
35. 
```

## 同步类容器

比如ArrayList，HashMap，线程不安全，现在想把线程不安全的集合转换为线程安全的集合： 

```
1.  public class Test01 {
2.      //这是main方法，程序的入口
3.      public static void main(String[] args) {
4.          //ArrayList为案例：从线程不安全  转为线程安全：
5.          List list = Collections.synchronizedList(new ArrayList());
6.      }
7.  }
```

试试ArrayList的线程不安全： 

```
1.  package com.msb.test02;
2.   
3.  import java.util.ArrayList;
4.  import java.util.concurrent.ExecutorService;
5.  import java.util.concurrent.Executors;
6.   
7.  /**
8.   * @author : msb-zhaoss
9.   */
10.public class Demo {
11.    //这是main方法，程序的入口
12.    public static void main(String[] args) {
13.        //创建一个ArrayList集合：
14.        ArrayList list = new ArrayList();
15. 
16.        //创建一个线程池：线程池定长100
17.        ExecutorService es = Executors.newFixedThreadPool(100);
18. 
19.        //并发向集合中添加10000个数据：
20.        for (int i = 0; i < 10000; i++) {
21.            //每个线程处理任务：run方法中的内容就是线程单元，任务，实际线程执行的部分
22.            es.execute(new Runnable() {
23.                @Override
24.                public void run() {
25.                    list.add("aaa");
26.                }
27.            });
28.        }
29. 
30.        //关闭线程池：
31.        es.shutdown();
32. 
33.        //监控线程是否执行完毕：
34.        while(true){
35.            //线程都执行完以后返回true
36.            if(es.isTerminated()){
37.                System.out.println("所有的子线程都执行完毕了！");
38.                //执行完毕以后看一下集合中元素的数量：
39.                System.out.println(list.size());
40.                if(list.size() == 10000){
41.                    System.out.println("线程安全！");
42.                }else{
43.                    System.out.println("线程不安全！");
44.                }
45. 
46.                //线程执行完以后，while循环可以停止：
47.                break;
48.            }
49.        }
50.    }
51.}
52. 
```

结果：

![img](https://image.201068.xyz/assets/clip_image862.jpg)

 

 

利用同步类容器解决：

```
1.  package com.msb.test02;
2.   
3.  import java.util.ArrayList;
4.  import java.util.Collections;
5.  import java.util.List;
6.  import java.util.concurrent.ExecutorService;
7.  import java.util.concurrent.Executors;
8.   
9.  /**
10. * @author : msb-zhaoss
11. */
12.public class Demo {
13.    //这是main方法，程序的入口
14.    public static void main(String[] args) {
15.        //创建一个ArrayList集合：
16.        ArrayList oldlist = new ArrayList();
17.        List list = Collections.synchronizedList(oldlist);
18. 
19.        //创建一个线程池：线程池定长100
20.        ExecutorService es = Executors.newFixedThreadPool(100);
21. 
22.        //并发向集合中添加10000个数据：
23.        for (int i = 0; i < 10000; i++) {
24.            //每个线程处理任务：run方法中的内容就是线程单元，任务，实际线程执行的部分
25.            es.execute(new Runnable() {
26.                @Override
27.                public void run() {
28.                    list.add("aaa");
29.                }
30.            });
31.        }
32. 
33.        //关闭线程池：
34.        es.shutdown();
35. 
36.        //监控线程是否执行完毕：
37.        while(true){
38.            //线程都执行完以后返回true
39.            if(es.isTerminated()){
40.                System.out.println("所有的子线程都执行完毕了！");
41.                //执行完毕以后看一下集合中元素的数量：
42.                System.out.println(list.size());
43.                if(list.size() == 10000){
44.                    System.out.println("线程安全！");
45.                }else{
46.                    System.out.println("线程不安全！");
47.                }
48. 
49.                //线程执行完以后，while循环可以停止：
50.                break;
51.            }
52.        }
53.    }
54.}
55. 
```

结果：

![img](https://image.201068.xyz/assets/clip_image864.jpg)

 

源码解析：

![img](https://image.201068.xyz/assets/clip_image866.jpg)

 

## ConcurrentMap并发容器

JDK5.0之后提供了多种并发类容器可以替代同步类容器，提升性能、吞吐量

ConcurrentHashMap替代HashMap、HashTable 

ConcurrentSkipListMap替代TreeMap 

 

简单原理：

![img](https://image.201068.xyz/assets/clip_image868.jpg)

 

并发情况下，验证提高性能：

ConcunrrentHashMap : 

```
1.  public class Test {
2.      //这是main方法，程序的入口
3.      public static void main(String[] args) {
4.          //选择一个容器：
5.          ConcurrentHashMap<String,Integer> map = new ConcurrentHashMap<>();
6.          
7.          //创建10个线程：
8.          for (int i = 0; i < 10; i++) {
9.              new Thread(new Runnable() {
10.                @Override
11.                public void run() {
12.                    long startTime = System.currentTimeMillis();
13.                    for (int j = 0; j < 1000000; j++) {
14.                        map.put("test" + j , j);
15.                    }
16.                    long endTime = System.currentTimeMillis();
17.                    System.out.println("一共需要的时间：" + (endTime - startTime));
18.                }
19.            }).start();
20.        }
21.    }
22.}
```

 

结果：

![img](https://image.201068.xyz/assets/clip_image870.jpg)

 

 

 

Hashtable： 

```
1.  package com.msb.test03;
2.   
3.  import java.util.Hashtable;
4.  import java.util.concurrent.ConcurrentHashMap;
5.   
6.  /**
7.   * @author : msb-zhaoss
8.   */
9.  public class Test {
10.    //这是main方法，程序的入口
11.    public static void main(String[] args) {
12.        //选择一个容器：
13.        //ConcurrentHashMap<String,Integer> map = new ConcurrentHashMap<>();
14.        Hashtable map = new Hashtable();
15.        //创建10个线程：
16.        for (int i = 0; i < 10; i++) {
17.            new Thread(new Runnable() {
18.                @Override
19.                public void run() {
20.                    long startTime = System.currentTimeMillis();
21.                    for (int j = 0; j < 1000000; j++) {
22.                        map.put("test" + j , j);
23.                    }
24.                    long endTime = System.currentTimeMillis();
25.                    System.out.println("一共需要的时间：" + (endTime - startTime));
26.                }
27.            }).start();
28.        }
29.    }
30.}
31. 
```

 

 

 

结果：

![img](https://image.201068.xyz/assets/clip_image872.jpg)

 

HashMap： 

```
1.  package com.msb.test03;
2.   
3.  import java.util.HashMap;
4.  import java.util.Hashtable;
5.  import java.util.concurrent.ConcurrentHashMap;
6.   
7.  /**
8.   * @author : msb-zhaoss
9.   */
10.public class Test {
11.    //这是main方法，程序的入口
12.    public static void main(String[] args) {
13.        //选择一个容器：
14.        //ConcurrentHashMap<String,Integer> map = new ConcurrentHashMap<>();
15.        //Hashtable map = new Hashtable();
16.        HashMap map = new HashMap();
17.        //创建10个线程：
18.        for (int i = 0; i < 10; i++) {
19.            new Thread(new Runnable() {
20.                @Override
21.                public void run() {
22.                    long startTime = System.currentTimeMillis();
23.                    for (int j = 0; j < 1000000; j++) {
24.                        map.put("test" + j , j);
25.                    }
26.                    long endTime = System.currentTimeMillis();
27.                    System.out.println("一共需要的时间：" + (endTime - startTime));
28.                }
29.            }).start();
30.        }
31.    }
32.}
33. 
```

 

![img](https://image.201068.xyz/assets/clip_image874.jpg)

 

线程安全的HashMap： 

```
1.  package com.msb.test03;
2.   
3.  import java.util.Collections;
4.  import java.util.HashMap;
5.  import java.util.Hashtable;
6.  import java.util.Map;
7.  import java.util.concurrent.ConcurrentHashMap;
8.   
9.  /**
10. * @author : msb-zhaoss
11. */
12.public class Test {
13.    //这是main方法，程序的入口
14.    public static void main(String[] args) {
15.        //选择一个容器：
16.        //ConcurrentHashMap<String,Integer> map = new ConcurrentHashMap<>();
17.        //Hashtable map = new Hashtable();
18.        HashMap oldmap = new HashMap();
19.        Map map = Collections.synchronizedMap(oldmap);
20.        //创建10个线程：
21.        for (int i = 0; i < 10; i++) {
22.            new Thread(new Runnable() {
23.                @Override
24.                public void run() {
25.                    long startTime = System.currentTimeMillis();
26.                    for (int j = 0; j < 1000000; j++) {
27.                        map.put("test" + j , j);
28.                    }
29.                    long endTime = System.currentTimeMillis();
30.                    System.out.println("一共需要的时间：" + (endTime - startTime));
31.                }
32.            }).start();
33.        }
34.    }
35.}
36. 
```

 

 

 

 

结果：

![img](https://image.201068.xyz/assets/clip_image876.jpg)

 

总结：

ConcurrentHashMap：性能高，线程安全 

Hashtable: 线程安全，性能低 

HashMap:线程不安全，性能高 

线程安全的HashMap：线程安全，性能低 

 

 

## COW并发容器

【1】COW类并发容器，全称：Copy  On  Write容器，写时复制容器。（读写分离容器）    

 

【2】原理： 

向容器中添加元素时，先将容器进行Copy复制出一个新容器，然后将元素添加到新容器中，再将原容器的引用指向新容器。 

并发读的时候不需要锁定容器，因为原容器没有变化，所以可以读取原容器中的值，使用的是一种读写分离的思想。

![img](https://image.201068.xyz/assets/clip_image878.jpg)

【3】这种设计的好处是什么呢？ 

注意上面的操作arr数组本身是无锁的，没有锁，在添加数据的时候，做了额外的复制， 

此时如果有线程来读数据，那么读取的是老arr的数据，此时arr的地址还没有改呢，在我添加元素的过程中， 

无论有多少个线程来读数据，都是读的原来的arr，不是新的arr 

所以性能很高，读写分离。提高了并发的性能。如果再读再复制... 

 

【4】注意： 

CopyOnWrite容器只能保证数据的最终一致性，不能保证数据实时一致性。

所以如果你希望写入的的数据，马上能读到，请不要使用CopyOnWrite容器。 

 

 

【5】适合特定场合： 

这个应用场景显而易见，适合读多写少的情况。如果一万个线程都添加操作，都在集合中添加数据，那数组不断复制，长度不断+1， 

那JVM肯定一直往上飙升，你用的时候肯定要评估使用场景的。 

由于每次更新都会复制新容器，所以如果数据量较大并且更新操作频繁则对内存消耗很高，建议在高并发读的场景下使用。

 

 

【6】主要讲解： 

COW容器有两种一种是CopyonWriteArrayList，一种是CopyOnWriteArraySet 

一个是替代ArrayList，一个是代替Set  

 

### CopyOnWriteArrayList

【1】代码：

```
1.  package com.msb.test04;
2.   
3.  import java.util.concurrent.CopyOnWriteArrayList;
4.   
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class Test {
9.      //这是main方法，程序的入口
10.    public static void main(String[] args) {
11.        CopyOnWriteArrayList<Integer> list = new CopyOnWriteArrayList<>();
12.        //添加方法：
13.        list.add(1);
14.        list.add(2);
15.        list.add(3);
16.        list.add(4);
17.        System.out.println(list);//[1, 2, 3, 4]
18.        list.add(3);//add方法无论元素是否存在，都可以添加进去--》添加重复的元素
19.        System.out.println(list);//[1, 2, 3, 4, 3]
20.        //adj. 缺席的；缺少的；心不在焉的；茫然的
21.        list.addIfAbsent(33);//添加不存在的元素--》不可以添加重复的数据
22.        System.out.println(list);//[1, 2, 3, 4, 3, 33]
23.    }
24.}
25. 
```

【2】源码分析： 

```
1.  public class CopyOnWriteArrayList<E>{
2.          //底层基于数组实现的
3.          private transient volatile Object[] array;
4.          
5.          public CopyOnWriteArrayList() {
6.          setArray(new Object[0]);
7.      }
8.          
9.          final void setArray(Object[] a) {
10.        array = a; // array = new Object[0]
11.    }
12.        //add方法：
13.        public boolean add(E e) {
14.        final ReentrantLock lock = this.lock;
15.        lock.lock();
16.        try {
17.                        //返回底层array数组,给了elements
18.            Object[] elements = getArray();
19.                        //获取elements的长度---》获取老数组的长度
20.            int len = elements.length;
21.                        //完成数组的复制，将老数组中的元素复制到新数组中，并且新数组的长度加1操作
22.            Object[] newElements = Arrays.copyOf(elements, len + 1);
23.                        //将e元素放入新数组最后位置
24.            newElements[len] = e;
25.                        //array数组的指向从老数组变为新数组
26.            setArray(newElements);
27.            return true;
28.        } finally {
29.            lock.unlock();
30.        }
31.    }
32.        
33.        
34.        final Object[] getArray() {
35.        return array;//返回底层数组
36.    }
37.        
38.        
39.        private boolean addIfAbsent(E e, Object[] snapshot) {
40.        final ReentrantLock lock = this.lock;
41.        lock.lock();
42.        try {
43.                        //取出array数组给current
44.            Object[] current = getArray();
45.            int len = current.length;
46.            if (snapshot != current) {
47.                // Optimize for lost race to another addXXX operation
48.                int common = Math.min(snapshot.length, len);
49.                                //遍历老数组：
50.                for (int i = 0; i < common; i++)
51.                                        //eq(e, current[i])将放入的元素和老数组的每一个元素进行比较，如果有重复的元素，就返回false，不添加了
52.                    if (current[i] != snapshot[i] && eq(e, current[i]))
53.                        return false;
54.                if (indexOf(e, current, common, len) >= 0)
55.                        return false;
56.            }
57.                        //完成数组的复制，将老数组中的元素复制到新数组中，并且新数组的长度加1操作
58.            Object[] newElements = Arrays.copyOf(current, len + 1);
59.                        //将e元素放入新数组最后位置
60.            newElements[len] = e;
61.                        //array数组的指向从老数组变为新数组
62.            setArray(newElements);
63.            return true;
64.        } finally {
65.            lock.unlock();
66.        }
67.    }
68.        
69.        
70.}
```

### CopyOnWriteArraySet

【1】代码： 

```
1.  /**
2.   * @author : msb-zhaoss
3.   */
4.  public class Test02 {
5.      //这是main方法，程序的入口
6.      public static void main(String[] args) {
7.          //创建一个集合：
8.          CopyOnWriteArraySet<Integer> set = new CopyOnWriteArraySet<>();
9.          //在这里也体现出Set和List的本质区别，就在于是否重复
10.        //所以add方法直接不可以添加重复数据进去
11.        set.add(1);
12.        set.add(2);
13.        set.add(2);
14.        set.add(7);
15.        System.out.println(set);//[1, 2, 7]
16.        
17.    }
18.}
19. 
```

【2】源码： 

```
1.  public class CopyOnWriteArraySet<E>{
2.          //CopyOnWriteArraySet底层基于CopyOnWriteArrayList
3.          private final CopyOnWriteArrayList<E> al;
4.          
5.          public CopyOnWriteArraySet() {
6.          al = new CopyOnWriteArrayList<E>();
7.      }
8.          
9.          //添加方法：
10.        public boolean add(E e) {
11.        return al.addIfAbsent(e);//底层调用的还是CopyOnWriteArrayList的addIfAbsent
12.    }
13.}
```

总结：

由上面的源码看出，每次调用[CopyOnWriteArraySet](CopyOnWriteArraySet)的add方法时候，其实底层是基于CopyOnWriteArrayList的addIfAbsent， 

每次在addIfAbsent方法中每次都要对数组进行遍历，所以CopyOnWriteArraySet的性能低于CopyOnWriteArrayList 

 

## 数据结构：队列

数据结构分为： 

（1）逻辑结构 ：--》思想上的结构--》卧室，厨房，卫生间 ---》线性表（数组，链表），图，树，栈，队列 

（2）物理结构 ：--》真实结构--》钢筋混凝土+牛顿力学------》紧密结构（顺序结构），跳转结构（链式结构） 

 队列：特点：先进先出 （FIFO）（first in first out） 

![img](https://image.201068.xyz/assets/clip_image880.jpg)

![img](https://image.201068.xyz/assets/clip_image882.jpg)

他有两端，一端是让新元素进去，一端是让老元素出去

在需要公平且经济地对各种自然或社会资源做管理或分配的场合，无论是调度银行和医院的服务窗口，还是管理轮耕的田地和轮伐的森林，队列都可大显身手。 

甚至计算机及其网络自身内部的各种计算资源，无论是多进程共享的 CPU 时间，还是多用户共享的打印机，也都需要借助队列结构实现合理和优化的分配。 

双端队列：两端都可以进行进队，出队的队列： 

（1）前端，后端都可以进出：

![img](https://image.201068.xyz/assets/clip_image884.jpg)

 （2）进行限制：

![img](https://image.201068.xyz/assets/clip_image886.jpg)

 

（3）特殊情况，双端队列实现栈操作: 

![img](https://image.201068.xyz/assets/clip_image888.jpg)

 栈和队列的物理结构实现 可以用线性表的数组，链表都可以

 

 

## 队列Queue

 

### 阻塞队列

 

#### BlockingQueue介绍

![img](https://image.201068.xyz/assets/clip_image890.jpg)

![img](https://image.201068.xyz/assets/clip_image892.jpg)

总结：BlockingQueue继承Queue，Queue继承自Collection 

所以Collection最基础的增删改查操作是有的，在这个基础上，多了Queue的特点，在这个基础上又多了阻塞的特点，最终形成了BlockingQueue 

 

什么叫阻塞？

 

![img](https://image.201068.xyz/assets/clip_image894.jpg)

 

![img](https://image.201068.xyz/assets/clip_image896.jpg)

 

常用的API： 

添加： 

![img](https://image.201068.xyz/assets/clip_image898.jpg)

![img](https://image.201068.xyz/assets/clip_image900.jpg)

![img](https://image.201068.xyz/assets/clip_image902.jpg)

put是阻塞的 

 

查询：

![img](https://image.201068.xyz/assets/clip_image904.jpg)

![img](https://image.201068.xyz/assets/clip_image906.jpg)

 

take是阻塞的 

 

删除：

![img](https://image.201068.xyz/assets/clip_image908.jpg)

#### BlockingQueue常见子类

 

##### ArrayBlockingQueue

源码中的注释的解释说明： 

![img](https://image.201068.xyz/assets/clip_image910.jpg)

 

【1】添加元素： 

```
1.  package com.msb.test05;
2.   
3.  import java.util.concurrent.ArrayBlockingQueue;
4.  import java.util.concurrent.TimeUnit;
5.   
6.  /**
7.   * @author : msb-zhaoss
8.   */
9.  public class Test01 {
10.    //这是main方法，程序的入口
11.    public static void main(String[] args) throws InterruptedException {
12.        //创建一个队列，队列可以指定容量指定长度3：
13.        ArrayBlockingQueue aq = new ArrayBlockingQueue(3);
14.        //添加元素：
15.        //【1】添加null元素：不可以添加null元素，会报空指针异常：NullPointerException
16.        //aq.add(null);
17.        //aq.offer(null);
18.        //aq.put(null);
19.        //【2】正常添加元素：
20.        aq.add("aaa");
21.        aq.offer("bbb");
22.        aq.put("ccc");
23.        System.out.println(aq);//[aaa, bbb, ccc]
24. 
25.        //【3】在队列满的情况下，再添加元素：
26.        //aq.add("ddd");//在队列满的情况下，添加元素 出现异常：Queue full
27.        //System.out.println(aq.offer("ddd"));//没有添加成功，返回false
28.        //设置最大阻塞时间，如果时间到了，队列还是满的，就不再阻塞了
29.        //aq.offer("ddd",2, TimeUnit.SECONDS);
30.        //真正阻塞的方法： put ,如果队列满，就永远阻塞 
31.        aq.put("ddd");
32.        System.out.println(aq);
33.    }
34.}
35. 
```

【2】获取元素： 

```
1.  package com.msb.test05;
2.   
3.  import javax.sound.midi.Soundbank;
4.  import java.util.concurrent.ArrayBlockingQueue;
5.  import java.util.concurrent.TimeUnit;
6.   
7.  /**
8.   * @author : msb-zhaoss
9.   */
10.public class Test02 {
11.    //这是main方法，程序的入口
12.    public static void main(String[] args) throws InterruptedException {
13.        //创建一个队列，队列可以指定容量指定长度3：
14.        ArrayBlockingQueue aq = new ArrayBlockingQueue(3);
15.        aq.add("aaa");
16.        aq.add("bbb");
17.        aq.add("ccc");
18.        //得到头元素但是不移除
19.        System.out.println(aq.peek());
20.        System.out.println(aq);
21.        //得到头元素并且移除
22.        System.out.println(aq.poll());
23.        System.out.println(aq);
24.        //得到头元素并且移除
25.        System.out.println(aq.take());
26.        System.out.println(aq);
27. 
28.        //清空元素：
29.        aq.clear();
30.        System.out.println(aq);
31. 
32.        System.out.println(aq.peek());//null
33.        System.out.println(aq.poll());//null
34.        //设置阻塞事件，如果队列为空，返回null，时间到了以后就不阻塞了
35.        //System.out.println(aq.poll(2, TimeUnit.SECONDS));
36.        //真正阻塞：队列为空，永远阻塞
37.        System.out.println(aq.take());
38. 
39. 
40.    }
41.}
42. 
```

【3】源码： 

```
1.  public class ArrayBlockingQueue<E> {
2.          //底层就是一个数组：
3.          final Object[] items;
4.          //取元素用到的索引，初始结果为0
5.          int takeIndex;
6.          //放元素用到的索引，初始结果为0
7.          int putIndex;
8.          //数组中元素的个数：
9.          int count;
10.        
11.        //一把锁：这个锁肯定很多方法中用到了，所以定义为属性，初始化以后可以随时使用
12.    final ReentrantLock lock;
13. 
14.    //锁伴随的一个等待吃：notEmpty
15.    private final Condition notEmpty;
16. 
17.    //锁伴随的一个等待吃：notFull
18.    private final Condition notFull;
19.        
20.        //构造器：
21.        public ArrayBlockingQueue(int capacity) {//传入队列指定的容量
22.        this(capacity, false);
23.    }
24.        
25.        public ArrayBlockingQueue(int capacity, boolean fair) {//传入队列指定的容量
26.                //健壮性考虑
27.        if (capacity <= 0)
28.            throw new IllegalArgumentException();
29.                //初始化底层数组
30.        this.items = new Object[capacity];
31.                //初始化锁 和  等待队列
32.        lock = new ReentrantLock(fair);
33.        notEmpty = lock.newCondition();
34.        notFull =  lock.newCondition();
35.    }
36.        
37.        //两个基本方法：一个是入队，一个是出队  ，是其他方法的基础：
38.        //入队：
39.        private void enqueue(E x) {
40.        // assert lock.getHoldCount() == 1;
41.        // assert items[putIndex] == null;
42.        final Object[] items = this.items;//底层数组赋给items
43.                //在对应的下标位置放入元素
44.        items[putIndex] = x;
45.        if (++putIndex == items.length) //++putIndex putIndex 索引 加1 
46.            putIndex = 0;
47.                //每放入一个元素，count加1操作
48.        count++;
49.        notEmpty.signal();
50.    }
51.        
52.        
53.        //出队：
54.        private E dequeue() {
55.        // assert lock.getHoldCount() == 1;
56.        // assert items[takeIndex] != null;
57.        final Object[] items = this.items;//底层数组赋给items
58.        @SuppressWarnings("unchecked")
59.        E x = (E) items[takeIndex];//在对应的位置取出元素
60.        items[takeIndex] = null;//对应位置元素取出后就置为null
61.        if (++takeIndex == items.length)//++takeIndex 加1操作
62.            takeIndex = 0;
63.        count--;//每取出一个元素，count减1操作
64.        if (itrs != null)
65.            itrs.elementDequeued();
66.        notFull.signal();
67.        return x;//将取出的元素作为方法的返回值
68.    }
69.        
70.        
71.        
72.        
73.}
```

takeIndex和putIndex置为0的原因： 

![img](https://image.201068.xyz/assets/clip_image912.jpg)

 

【4】其他的添加或者获取的方法都是依托与这个入队和出队的基础方法 

![img](https://image.201068.xyz/assets/clip_image914.jpg)

 

【5】感受一下put和take的阻塞：

![img](https://image.201068.xyz/assets/clip_image916.jpg)

上面的while不可以换为if，因为如果notFull中的线程被激活的瞬间，有其他线程放入元素，那么队列就又满了

那么沿着await后面继续执行就不可以，所以一定要反复确定队列是否满的，才能放入元素 

 

##### LinkedBlockingQueue

一个可选择的有边界的队列：意思就是队列的长度可以指定，也可以不指定

![img](https://image.201068.xyz/assets/clip_image918.jpg)

 

【1】添加元素： 

```
1.  package com.msb.test05;
2.   
3.  import java.util.concurrent.ArrayBlockingQueue;
4.  import java.util.concurrent.LinkedBlockingQueue;
5.  import java.util.concurrent.TimeUnit;
6.   
7.  /**
8.   * @author : msb-zhaoss
9.   */
10.public class Test01 {
11.    //这是main方法，程序的入口
12.    public static void main(String[] args) throws InterruptedException {
13.        //创建一个队列，队列可以指定容量指定长度3：
14.        LinkedBlockingQueue aq = new LinkedBlockingQueue(3);
15.        //添加元素：
16.        //【1】添加null元素：不可以添加null元素，会报空指针异常：NullPointerException
17.        //aq.add(null);
18.        //aq.offer(null);
19.        aq.put(null);
20.        //【2】正常添加元素：
21.        aq.add("aaa");
22.        aq.offer("bbb");
23.        aq.put("ccc");
24.        System.out.println(aq);//[aaa, bbb, ccc]
25. 
26.        //【3】在队列满的情况下，再添加元素：
27.        //aq.add("ddd");//在队列满的情况下，添加元素 出现异常：Queue full
28.        //System.out.println(aq.offer("ddd"));//没有添加成功，返回false
29.        //设置最大阻塞时间，如果时间到了，队列还是满的，就不再阻塞了
30.        //aq.offer("ddd",2, TimeUnit.SECONDS);
31.        //真正阻塞的方法： put ,如果队列满，就永远阻塞
32.        aq.put("ddd");
33.        System.out.println(aq);
34.    }
35.}
36. 
```

【2】取出元素： 

```
1.  package com.msb.test05;
2.   
3.  import javax.sound.midi.Soundbank;
4.  import java.util.concurrent.ArrayBlockingQueue;
5.  import java.util.concurrent.LinkedBlockingQueue;
6.  import java.util.concurrent.TimeUnit;
7.   
8.  /**
9.   * @author : msb-zhaoss
10. */
11.public class Test02 {
12.    //这是main方法，程序的入口
13.    public static void main(String[] args) throws InterruptedException {
14.        //创建一个队列，队列可以指定容量指定长度3：
15.        LinkedBlockingQueue aq = new LinkedBlockingQueue();
16.        aq.add("aaa");
17.        aq.add("bbb");
18.        aq.add("ccc");
19.        //得到头元素但是不移除
20.        System.out.println(aq.peek());
21.        System.out.println(aq);
22.        //得到头元素并且移除
23.        System.out.println(aq.poll());
24.        System.out.println(aq);
25.        //得到头元素并且移除
26.        System.out.println(aq.take());
27.        System.out.println(aq);
28. 
29.        //清空元素：
30.        aq.clear();
31.        System.out.println(aq);
32. 
33.        System.out.println(aq.peek());//null
34.        System.out.println(aq.poll());//null
35.        //设置阻塞事件，如果队列为空，返回null，时间到了以后就不阻塞了
36.        //System.out.println(aq.poll(2, TimeUnit.SECONDS));
37.        //真正阻塞：队列为空，永远阻塞
38.        System.out.println(aq.take());
39. 
40. 
41.    }
42.}
43. 
```

【3】特点： 

ArrayBlockingQueue ： 不支持读写同时操作，底层基于数组的。

LinkedBlockingQueue：支持读写同时操作，并发情况下，效率高。底层基于链表。

 

【4】源码： 

入队操作：

![img](https://image.201068.xyz/assets/clip_image920.jpg)

 

 

出队操作：

![img](https://image.201068.xyz/assets/clip_image922.jpg)

 

```
1.  public class LinkedBlockingQueue<E>{
2.          //内部类Node就是链表的节点的对象对应的类：
3.          static class Node<E> {
4.          E item;//封装你要装的那个元素
5.          
6.          Node<E> next;//下一个Node节点的地址
7.   
8.          Node(E x) { item = x; }//构造器
9.      }
10.        //链表的长度
11.        private final int capacity;
12.        //计数器：
13.        private final AtomicInteger count = new AtomicInteger();
14.        //链表的头结点
15.        transient Node<E> head;
16.        //链表的尾结点
17.        private transient Node<E> last;
18.        //取元素用的锁
19.        private final ReentrantLock takeLock = new ReentrantLock();
20.        //等待池
21.    private final Condition notEmpty = takeLock.newCondition();
22.    //放元素用的锁
23.    private final ReentrantLock putLock = new ReentrantLock();
24.    //等待池
25.    private final Condition notFull = putLock.newCondition();
26.        
27.        public LinkedBlockingQueue() {
28.        this(Integer.MAX_VALUE);//调用类本类的空构造器，传入正21亿
29.    }
30.        
31.        public LinkedBlockingQueue(int capacity) {
32.                //健壮性考虑
33.        if (capacity <= 0) throw new IllegalArgumentException();
34.                //给队列指定长度  
35.        this.capacity = capacity;
36.                //last，head指向一个新的节点，新的节点中 元素为null 
37.        last = head = new Node<E>(null);
38.    }
39.        
40.        
41.        //入队：
42.        private void enqueue(Node<E> node) {
43.        last = last.next = node;
44.    }
45.        
46.        //出队：
47.        private E dequeue() {
48.        Node<E> h = head;//h指向了head
49.        Node<E> first = h.next;//first 指向head的next
50.        h.next = h; // help GC   h.next指向自己，更容易被GC发现 被GC
51.        head = first;//head的指向指为first
52.        E x = first.item;//取出链中第一个元素，给了x
53.        first.item = null;
54.        return x;//把x作为方法的返回值
55.    }
56.}
```

【5】put的阻塞： 

 

阻塞的前提是  队列是固定长度的 

 

![img](https://image.201068.xyz/assets/clip_image924.jpg)

 

##### SynchronousQueue

![img](https://image.201068.xyz/assets/clip_image926.jpg)

 

这个特殊的队列设计的意义：

![img](https://image.201068.xyz/assets/clip_image928.jpg)

![img](https://image.201068.xyz/assets/clip_image930.jpg)

 

 

测试1：先添加元素： 

```
1.  public class Test01 {
2.      //这是main方法，程序的入口
3.      public static void main(String[] args) {
4.          SynchronousQueue sq = new SynchronousQueue();
5.          sq.add("aaa");
6.      }
7.  }
8.   
```

直接报错：说队列满了，因为队列没有容量，理解为满也是正常的：

![img](https://image.201068.xyz/assets/clip_image932.jpg)

测试2：put方法  阻塞：队列是空的，可以理解为队列满了，满的话放入元素 put 一定会阻塞： 

```
1.  public class Test01 {
2.      //这是main方法，程序的入口
3.      public static void main(String[] args) throws InterruptedException {
4.          SynchronousQueue sq = new SynchronousQueue();
5.          sq.put("aaa");
6.      }
7.  }
```

![img](https://image.201068.xyz/assets/clip_image934.jpg)

 

测试3：先取  再放： 

```
1.  package com.msb.test06;
2.   
3.  import java.util.concurrent.SynchronousQueue;
4.   
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class Test02 {
9.      //这是main方法，程序的入口
10.    public static void main(String[] args) {
11.        SynchronousQueue sq = new SynchronousQueue();
12. 
13.        //创建一个线程，取数据：
14.        new Thread(new Runnable() {
15.            @Override
16.            public void run() {
17.                while(true){
18.                    try {
19.                        System.out.println(sq.take());
20.                    } catch (InterruptedException e) {
21.                        e.printStackTrace();
22.                    }
23.                }
24.            }
25.        }).start();
26. 
27.        //搞一个线程，往里面放数据：
28.        new Thread(new Runnable() {
29.            @Override
30.            public void run() {
31.                try {
32.                    sq.put("aaa");
33.                    sq.put("bbb");
34.                    sq.put("ccc");
35.                    sq.put("ddd");
36.                } catch (InterruptedException e) {
37.                    e.printStackTrace();
38.                }
39. 
40.            }
41.        }).start();
42.    }
43.}
44. 
```

结果：

![img](https://image.201068.xyz/assets/clip_image936.jpg)

 

测试4：poll方法： 

```
1.  package com.msb.test06;
2.   
3.  import java.util.concurrent.SynchronousQueue;
4.  import java.util.concurrent.TimeUnit;
5.   
6.  /**
7.   * @author : msb-zhaoss
8.   */
9.  public class Test02 {
10.    //这是main方法，程序的入口
11.    public static void main(String[] args) {
12.        SynchronousQueue sq = new SynchronousQueue();
13. 
14.        //创建一个线程，取数据：
15.        new Thread(new Runnable() {
16.            @Override
17.            public void run() {
18.                while(true){
19.                    try {
20.                        //设置一个阻塞事件：超出事件就不阻塞了
21.                        Object result = sq.poll(5, TimeUnit.SECONDS);
22.                        System.out.println(result);
23.                        if(result == null){
24.                            break;
25.                        }
26.                    } catch (InterruptedException e) {
27.                        e.printStackTrace();
28.                    }
29.                }
30.            }
31.        }).start();
32. 
33.        //搞一个线程，往里面放数据：
34.        new Thread(new Runnable() {
35.            @Override
36.            public void run() {
37.                try {
38.                    sq.put("aaa");
39.                    sq.put("bbb");
40.                    sq.put("ccc");
41.                    sq.put("ddd");
42.                } catch (InterruptedException e) {
43.                    e.printStackTrace();
44.                }
45. 
46.            }
47.        }).start();
48.    }
49.}
```

![img](https://image.201068.xyz/assets/clip_image938.jpg)

 

注意：取出元素 不能用peek，因为peek不会将元素从队列中拿走，只是查看的效果；

 

##### PriorityBlockingQueue

带有优先级的阻塞队列。 

优先级队列，意味着队列有先后顺序的，数据有不同的权重。 

无界的队列，没有长度限制，但是在你不指定长度的时候，默认初始长度为11，也可以手动指定， 

当然随着数据不断的加入，底层（底层是数组Object[]）会自动扩容，直到内存全部消耗殆尽了，导致 OutOfMemoryError内存溢出 程序才会结束。 

![img](https://image.201068.xyz/assets/clip_image940.jpg)

 

不可以放入null元素的，不允许放入不可比较的对象（导致抛出ClassCastException），对象必须实现内部比较器或者外部比较器。 

 

测试1：添加null数据： 

```
1.  public class Test {
2.      //这是main方法，程序的入口
3.      public static void main(String[] args) {
4.          PriorityBlockingQueue pq = new PriorityBlockingQueue();
5.          pq.put(null);
6.      }
7.  }
```

![img](https://image.201068.xyz/assets/clip_image942.jpg)

 

 

测试2：添加四个数据： 

```
1.  package com.msb.test07;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class Student implements Comparable<Student> {
7.      String name;
8.      int age;
9.   
10.    public Student() {
11.    }
12. 
13.    public Student(String name, int age) {
14.        this.name = name;
15.        this.age = age;
16.    }
17. 
18.    @Override
19.    public String toString() {
20.        return "Student{" +
21.                "name='" + name + '\'' +
22.                ", age=" + age +
23.                '}';
24.    }
25. 
26.    @Override
27.    public int compareTo(Student o) {
28.        return this.age - o.age;
29.    }
30.}
31. 
```

 

```
1.  package com.msb.test07;
2.   
3.  import java.util.concurrent.PriorityBlockingQueue;
4.   
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class Test02 {
9.      //这是main方法，程序的入口
10.    public static void main(String[] args) {
11.        PriorityBlockingQueue<Student> pq = new PriorityBlockingQueue<>();
12.        pq.put(new Student("nana",18));
13.        pq.put(new Student("lulu",11));
14.        pq.put(new Student("feifei",6));
15.        pq.put(new Student("mingming",21));
16.        System.out.println(pq);
17.    }
18.}
19. 
```

结果：

![img](https://image.201068.xyz/assets/clip_image944.jpg)

发现结果并没有按照优先级顺序排列

 

测试3：取出数据： 

```
1.  package com.msb.test07;
2.   
3.  import java.util.concurrent.PriorityBlockingQueue;
4.   
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class Test02 {
9.      //这是main方法，程序的入口
10.    public static void main(String[] args) throws InterruptedException {
11.        PriorityBlockingQueue<Student> pq = new PriorityBlockingQueue<>();
12.        pq.put(new Student("nana",18));
13.        pq.put(new Student("lulu",11));
14.        pq.put(new Student("feifei",6));
15.        pq.put(new Student("mingming",21));
16.        System.out.println("------------------------------------------");
17.        System.out.println(pq.take());
18.        System.out.println(pq.take());
19.        System.out.println(pq.take());
20.        System.out.println(pq.take());
21.    }
22.}
23. 
```

![img](https://image.201068.xyz/assets/clip_image946.jpg)

 

 

从结果证明，这个优先级队列，并不是在put数据的时候计算谁在前谁在后 

而是取数据的时候，才真正判断谁在前 谁在后 

 

优先级 --》取数据的优先级 

 

 

 

#### DelayQueue

##### 一、DelayQueue是什么 

　　DelayQueue是一个无界的BlockingQueue，用于放置实现了Delayed接口的对象，其中的对象只能在其到期时才能从队列中取走。

![img](https://image.201068.xyz/assets/clip_image948.jpg)

当生产者线程调用put之类的方法加入元素时，会触发Delayed接口中的compareTo方法进行排序，也就是说队列中元素的顺序是按到期时间排序的，而非它们进入队列的顺序。排在队列头部的元素是最早到期的，越往后到期时间赿晚。

消费者线程查看队列头部的元素，注意是查看不是取出。然后调用元素的getDelay方法，如果此方法返回的值小０或者等于０，则消费者线程会从队列中取出此元素，并进行处理。如果getDelay方法返回的值大于0，则消费者线程wait返回的时间值后，再从队列头部取出元素，此时元素应该已经到期。 

注意：不能将null元素放置到这种队列中。 

##### 二、DelayQueue能做什么 

　1. 淘宝订单业务:下单之后如果三十分钟之内没有付款就自动取消订单。 
 \2. 饿了吗订餐通知:下单成功后60s之后给用户发送短信通知。 

　3. 关闭空闲连接。服务器中，有很多客户端的连接，空闲一段时间之后需要关闭之。

　4. 缓存。缓存中的对象，超过了空闲时间，需要从缓存中移出。

　5. 任务超时处理。在网络协议滑动窗口请求应答式交互时，处理超时未响应的请求等。 

案例： 

```
1.  package com.msb.test08;
2.   
3.  import java.util.concurrent.Delayed;
4.  import java.util.concurrent.TimeUnit;
5.   
6.  /**
7.   * @author : msb-zhaoss
8.   */
9.  public class User implements Delayed {
10.    private int id;//用户id
11.    private String name;//用户名字
12.    private long endTime;//结束时间
13. 
14.    public int getId() {
15.        return id;
16.    }
17. 
18.    public void setId(int id) {
19.        this.id = id;
20.    }
21. 
22.    public String getName() {
23.        return name;
24.    }
25. 
26.    public void setName(String name) {
27.        this.name = name;
28.    }
29. 
30.    public long getEndTime() {
31.        return endTime;
32.    }
33. 
34.    public void setEndTime(long endTime) {
35.        this.endTime = endTime;
36.    }
37. 
38.    public User(int id, String name, long endTime) {
39.        this.id = id;
40.        this.name = name;
41.        this.endTime = endTime;
42.    }
43. 
44.    //只包装用户名字就可以
45.    @Override
46.    public String toString() {
47.        return "User{" +
48.                "name='" + name + '\'' +
49.                '}';
50.    }
51. 
52.    @Override
53.    public long getDelay(TimeUnit unit) {
54.        //计算剩余时间 剩余时间小于0 <=0  证明已经到期
55.        return this.getEndTime() - System.currentTimeMillis();
56.    }
57. 
58.    @Override
59.    public int compareTo(Delayed o) {
60.        //队列中数据 到期时间的比较
61.        User other = (User)o;
62.        return ((Long)(this.getEndTime())).compareTo((Long)(other.getEndTime()));
63.    }
64.}
65. 
```

compareTo：看谁先被移除 

getDelay ：看剩余时间 

```
1.  package com.msb.test08;
2.   
3.  import java.util.concurrent.DelayQueue;
4.   
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class TestDelayQueue {
9.      //创建一个队列：
10.    DelayQueue<User> dq = new DelayQueue<>();
11. 
12.    //登录游戏：
13.    public void login(User user){
14.        dq.add(user);
15.        System.out.println("用户：[" + user.getId() +"],[" + user.getName() + "]已经登录，预计下机时间为：" + user.getEndTime() );
16.    }
17. 
18.    //时间到，退出游戏，队列中移除：
19.    public void logout(){
20.        //打印队列中剩余的人：
21.        System.out.println(dq);
22.        try {
23.            User user = dq.take();
24.            System.out.println("用户：[" + user.getId() +"],[" + user.getName() + "]上机时间到，自动退出游戏");
25.        } catch (InterruptedException e) {
26.            e.printStackTrace();
27.        }
28.    }
29. 
30.    //获取在线人数：
31.    public int onlineSize(){
32.        return dq.size();
33.    }
34. 
35.    //这是main方法，程序的入口
36.    public static void main(String[] args) {
37.        //创建测试类对象：
38.        TestDelayQueue test = new TestDelayQueue();
39. 
40.        //添加登录的用户：
41.        test.login(new User(1,"张三",System.currentTimeMillis()+5000));
42.        test.login(new User(2,"李四",System.currentTimeMillis()+2000));
43.        test.login(new User(3,"王五",System.currentTimeMillis()+10000));
44.        //一直监控
45.        while(true){
46.            //到期的话，就自动下线：
47.            test.logout();
48.            //队列中元素都被移除了的话，那么停止监控，停止程序即可
49.            if(test.onlineSize() == 0){
50.                break;
51.            }
52.        }
53.    }
54.}
55. 
```

 

![img](https://image.201068.xyz/assets/clip_image950.jpg)

##### 双端队列Deque

```
1.  package com.msb.test08;
2.   
3.  import java.util.Collection;
4.  import java.util.Deque;
5.  import java.util.Iterator;
6.  import java.util.LinkedList;
7.   
8.  /**
9.   * @author : msb-zhaoss
10. */
11.public class Test03 {
12.    //这是main方法，程序的入口
13.    public static void main(String[] args) {
14.        /*
15.        双端队列：
16.        Deque<E> extends Queue
17.        Queue一端放 一端取的基本方法  Deque是具备的
18.        在此基础上 又扩展了 一些 头尾操作（添加，删除，获取）的方法
19.         */
20.        Deque<String> d = new LinkedList<>() ;
21.        d.offer("A");
22.        d.offer("B");
23.        d.offer("C");
24.        System.out.println(d);//[A, B, C]
25. 
26.        d.offerFirst("D");
27.        d.offerLast("E");
28.        System.out.println(d);//[D, A, B, C, E]
29. 
30.        System.out.println(d.poll());
31.        System.out.println(d);//[A, B, C, E]
32. 
33.        System.out.println(d.pollFirst());
34.        System.out.println(d.pollLast());
35.        System.out.println(d);
36.    }
37.}
38. 
```

# 第12章_IO流

## File类

### 引入

【1】文件，目录：

文件： 

内存中存放的数据在计算机关机后就会消失。要长久保存数据，就要使用硬盘、光盘、U 盘等设备。为了便于数据的管理和检索，引入了“文件”的概念。一篇文章、一段视频、一个可执行程序，都可以被保存为一个文件，并赋予一个文件名。操作系统以文件为单位管理磁盘中的数据。 

 

一般来说，文件可分为文本文件、视频文件、音频文件、图像文件、可执行文件等多种类别，这是从文件的功能进行分类的。从数据存储的角度来说，所有的文件本质上都是一样的，都是由一个个字节组成的，归根到底都是 0、1 比特串。不同的文件呈现出不同的形态（有的是文本，有的是视频等等） 




文件夹（目录）：

成千上万个文件如果不加分类放在一起，用户使用起来显然非常不便，因此又引入了树形目录（目录也叫文件夹）的机制，可以把文件放在不同的文件夹中，文件夹中还可以嵌套文件夹，这就便于用户对文件进行管理和使用 




【2】查看文件/目录的信息： 

右键-属性 

 

 

【3】在java程序中操纵 文件/目录 ？怎么办？ 

java程序，最典型的特点，面向对象，java程序最擅长的就是操作对象，盘符上的文件/目录，将它的各种信息进行了封装，封装为一个对象，

java程序最擅长的就是操纵对象，这个对象属于 ---》File类 

 

盘符上的文件---》封装为对象---》对象属于File类的对象--》有了这个对象，我们程序就可以直接操纵这个对象，通过这个对象获取文件的各种信息，还可以对文件进行创建 ，删除。 

 

 

### 对文件进行操作

```
1.  package com.msb.file;
2.   
3.  import java.io.File;
4.  import java.io.IOException;
5.   
6.  /**
7.   * @author : msb-zhaoss
8.   */
9.  public class Test01 {
10.    //这是一个main方法，是程序的入口：
11.    public static void main(String[] args) throws IOException {
12.        //将文件封装为一个File类的对象：
13.        File f = new File("d:\\test.txt");
14.        File f1 = new File("d:\\test.txt");
15.        File f2 = new File("d:/test.txt");
16.        //File.separator属性帮我们获取当前操作系统的路径拼接符号
17.       //在windows，dos下，系统默认用“\”作为路径分隔符 ，在unix，url中，使用“/”作为路径分隔符。
18.        File f3 = new File("d:"+File.separator+"test.txt");//建议使用这种
19. 
20.        //常用方法：
21.        System.out.println("文件是否可读："+f.canRead());
22.        System.out.println("文件是否可写："+f.canWrite());
23.        System.out.println("文件的名字："+f.getName());
24.        System.out.println("上级目录："+f.getParent());
25.        System.out.println("是否是一个目录："+f.isDirectory());
26.        System.out.println("是否是一个文件："+f.isFile());
27.        System.out.println("是否隐藏："+f.isHidden());
28.        System.out.println("文件的大小："+f.length());
29.        System.out.println("是否存在："+f.exists());
30.        /*if(f.exists()){//如果文件存在，将文件删除操作
31.            f.delete();
32.        }else{//如果不存在，就创建这个文件
33.            f.createNewFile();
34.        }*/
35.        System.out.println(f == f1);//比较两个对象的地址
36.        System.out.println(f.equals(f1));//比较两个对象对应的文件的路径
37. 
38.        //跟路径相关的：
39.        System.out.println("绝对路径："+f.getAbsolutePath());
40.        System.out.println("相对路径："+f.getPath());
41.        System.out.println("toString:"+f.toString());
42. 
43.        System.out.println("----------------------");
44.        File f5 = new File("demo.txt");
45.        if(!f5.exists()){
46.            f5.createNewFile();
47.        }
48.        //绝对路径指的就是：真实的一个精准的，完整的路径
49.        System.out.println("绝对路径："+f5.getAbsolutePath());
50.        //相对路径：有一个参照物，相对这个参照物的路径。
51.        //在main方法中，相对位置指的就是：D:\IDEA_workspace\TestJavaSE
52.        //在junit的测试方法中，相对路径指的就是模块位置
53.        System.out.println("相对路径："+f5.getPath());
54.        //toString的效果永远是  相对路径
55.        System.out.println("toString:"+f5.toString());
56. 
57.        File f6 = new File("a/b/c/demo.txt");
58.        if(!f5.exists()){
59.            f5.createNewFile();
60.        }
61.        System.out.println("绝对路径："+f6.getAbsolutePath());
62.        System.out.println("相对路径："+f6.getPath());
63.    }
64.}
65. 
```

 

 

### 对目录进行操作

```
1.  package com.msb.file;
2.   
3.  import java.io.File;
4.   
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class Test02 {
9.      //这是一个main方法，是程序的入口：
10.    public static void main(String[] args) {
11.        //将目录封装为File类的对象：
12.        File f = new File("D:\\IDEA_workspace");
13.        System.out.println("文件是否可读："+f.canRead());
14.        System.out.println("文件是否可写："+f.canWrite());
15.        System.out.println("文件的名字："+f.getName());
16.        System.out.println("上级目录："+f.getParent());
17.        System.out.println("是否是一个目录："+f.isDirectory());
18.        System.out.println("是否是一个文件："+f.isFile());
19.        System.out.println("是否隐藏："+f.isHidden());
20.        System.out.println("文件的大小："+f.length());
21.        System.out.println("是否存在："+f.exists());
22.        System.out.println("绝对路径："+f.getAbsolutePath());
23.        System.out.println("相对路径："+f.getPath());
24.        System.out.println("toString:"+f.toString());
25. 
26.        //跟目录相关的方法：
27.        File f2 = new File("D:\\a\\b\\c");
28.        //创建目录：
29.        //f2.mkdir();//创建单层目录
30.        //f2.mkdirs();//创建多层目录
31. 
32.        //删除：如果是删除目录的话，只会删除一层，并且前提：这层目录是空的，里面没有内容，如果内容就不会被删除
33.        f2.delete();
34. 
35.        //查看：
36.        String[] list = f.list();//文件夹下目录/文件对应的名字的数组
37.        for(String s:list){
38.            System.out.println(s);
39.        }
40. 
41.        System.out.println("=========================");
42.        File[] files = f.listFiles();//作用更加广泛
43.        for(File file:files){
44.            System.out.println(file.getName()+","+file.getAbsolutePath());
45.        }
46.    }
47.}
48. 
```

 

 

 

 

 

 

 

## IO流

### 引入

【1】File类：封装文件/目录的各种信息，对目录/文件进行操作，但是我们不可以获取到文件/目录中的内容。 

【2】引入：IO流： 

I/O ： Input/Output的缩写，用于处理设备之间的数据的传输。 

【3】形象理解：IO流 当做一根 “管”： 

![img](https://image.201068.xyz/assets/clip_image952.jpg)

 

【4】IO流的体系结构： 

![img](https://image.201068.xyz/assets/clip_image954.jpg)

 

### 案例：通过java程序完成文件的复制操作

 

#### 功能分解1：文件--》程序：FileReader

一个字符一个字符的将文件中的内容读取到程序中了：

```
1.  package com.msb.io01;
2.   
3.  import java.io.File;
4.  import java.io.FileNotFoundException;
5.  import java.io.FileReader;
6.  import java.io.IOException;
7.   
8.  /**
9.   * @author : msb-zhaoss
10. */
11.public class Test01 {
12.    //这是一个main方法，是程序的入口：
13.    public static void main(String[] args) throws IOException {
14.        //文件--》程序：
15.        //1.有一个文件：----》创建一个File类的对象
16.        File f = new File("d:\\Test.txt");
17.        //2.利用FileReader这个流，这个“管”怼到源文件上去   ---》创建一个FileReader的流的对象
18.        FileReader fr = new FileReader(f);
19.        //3.进行操作“吸”的动作  ---》读取动作
20.        /*下面的代码我们验证了：如果到了文件的结尾处，那么读取的内容为-1
21.        int n1 = fr.read();
22.        int n2 = fr.read();
23.        int n3 = fr.read();
24.        int n4 = fr.read();
25.        int n5 = fr.read();
26.        int n6 = fr.read();
27.        System.out.println(n1);
28.        System.out.println(n2);
29.        System.out.println(n3);
30.        System.out.println(n4);
31.        System.out.println(n5);
32.        System.out.println(n6);*/
33.        //方式1：
34.        /*int n = fr.read();
35.        while(n!=-1){
36.            System.out.println(n);
37.            n = fr.read();
38.        }*/
39. 
40.        //方式2：
41.        int n;
42.        while((n = fr.read())!=-1){
43.            System.out.println((char)n);
44.        }
45. 
46.        //4.“管”不用了，就要关闭  ---》关闭流
47.        //流，数据库，网络资源，靠jvm本身没有办法帮我们关闭，此时必须程序员手动关闭：
48.        fr.close();
49.    }
50.}
51. 
```

 

想一次性读取五个字符，不够的话下次再读五个字符：

```
1.  package com.msb.io01;
2.   
3.  import java.io.File;
4.  import java.io.FileReader;
5.  import java.io.IOException;
6.   
7.  /**
8.   * @author : msb-zhaoss
9.   */
10.public class Test02 {
11.    //这是一个main方法，是程序的入口：
12.    public static void main(String[] args) throws IOException {
13.        //文件--》程序：
14.        //1.创建一个File类的对象
15.        File f = new File("d:\\Test.txt");
16.        //2.创建一个FileReader的流的对象
17.        FileReader fr = new FileReader(f);
18.        //3.读取动作
19.        //引入一个“快递员的小车”，这个“小车”一次拉5个快递：
20.        char[] ch = new char[5];//缓冲数组
21.        int len = fr.read(ch);//一次读取五个:返回值是这个数组中 的有效长度
22.        while(len!=-1){
23.            //System.out.println(len);
24.            //错误方式：
25.            /*for (int i = 0 ;i < ch.length;i++){
26.                System.out.println(ch[i]);
27.            }*/
28.            //正确方式：
29.            /*for (int i = 0 ;i < len;i++){
30.                System.out.println(ch[i]);
31.            }*/
32.            //正确方式2：将数组转为String：
33.            String str = new String(ch,0,len);
34.            System.out.print(str);
35.            len = fr.read(ch);
36.        }
37. 
38. 
39.        //4.关闭流
40.        fr.close();
41.    }
42.}
43. 
```

 

#### 功能分解2：程序--》文件：FileWriter

一个字符一个字符的向外输出： 

```
1.  package com.msb.io01;
2.   
3.  import java.io.File;
4.  import java.io.FileWriter;
5.  import java.io.IOException;
6.   
7.  /**
8.   * @author : msb-zhaoss
9.   */
10.public class Test03 {
11.    //这是一个main方法，是程序的入口：
12.    public static void main(String[] args) throws IOException {
13.        //1.有个目标文件：
14.        File f = new File("d:\\demo.txt");
15.        //2.FileWriter管怼到文件上去：
16.        FileWriter fw = new FileWriter(f);
17.        //3.开始动作：输出动作：
18.        //一个字符一个字符的往外输出：
19.        String str = "hello你好";
20.        for (int i = 0 ;i < str.length();i++){
21.            fw.write(str.charAt(i));
22.        }
23.        //4.关闭流：
24.        fw.close();
25.    }
26.}
27. 
```

发现：

如果目标文件不存在的话，那么会自动创建此文件。

如果目标文件存在的话：

[new FileWriter(f)](new FileWriter(f))  相当于对原文件进行覆盖操作。 

[new FileWriter(f,false)](new FileWriter(f,false)) 相当于对源文件进行覆盖操作。不是追加。 

 [new FileWriter(f,true)](new FileWriter(f,true))  对原来的文件进行追加，而不是覆盖。 

 

利用缓冲数组：向外输出（利用缓冲数组：）

```
1.  package com.msb.io01;
2.   
3.  import java.io.File;
4.  import java.io.FileWriter;
5.  import java.io.IOException;
6.   
7.  /**
8.   * @author : msb-zhaoss
9.   */
10.public class Test03 {
11.    //这是一个main方法，是程序的入口：
12.    public static void main(String[] args) throws IOException {
13.        //1.有个目标文件：
14.        File f = new File("d:\\demo.txt");
15.        //2.FileWriter管怼到文件上去：
16.        FileWriter fw = new FileWriter(f,true);
17.        //3.开始动作：输出动作：
18.        //一个字符一个字符的往外输出：
19.        String str = "你好中国";
20.        char[] chars = str.toCharArray();
21.        fw.write(chars);
22.        //4.关闭流：
23.        fw.close();
24.    }
25.}
26. 
```

 

#### 功能分解3：利用FileReader，FileWriter文件复制

```
1.  package com.msb.io01;
2.   
3.  import java.io.*;
4.   
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class Test04 {
9.      //这是一个main方法，是程序的入口：
10.    public static void main(String[] args) throws IOException {
11.        //1.有一个源文件
12.        File f1 = new File("d:\\Test.txt");
13.        //2.有一个目标文件：
14.        File f2 = new File("d:\\Demo.txt");
15.        //3.搞一个输入的管 怼到源文件上：
16.        FileReader fr = new FileReader(f1);
17.        //4.搞一个输出的管，怼到目标文件上：
18.        FileWriter fw = new FileWriter(f2);
19. 
20.        //5.开始动作：
21.        //方式1：一个字符一个字符的复制：
22.        /*int n = fr.read();
23.        while(n!=-1){
24.            fw.write(n);
25.            n = fr.read();
26.        }*/
27. 
28.        //方式2：利用缓冲字符数组：
29.        /*char[] ch = new char[5];
30.        int len = fr.read(ch);
31.        while(len!=-1){
32.            fw.write(ch,0,len);//将缓冲数组中有效长度写出
33.            len = fr.read(ch);
34.        }*/
35.        //方式3：利用缓冲字符数组，将数组转为String写出。
36.        char[] ch = new char[5];
37.        int len = fr.read(ch);
38.        while(len!=-1){
39.            String s = new String(ch,0,len);
40.            fw.write(s);
41.            len = fr.read(ch);
42.        }
43. 
44.        //6.关闭流：(关闭流的时候，倒着关闭，后用先关)
45.        fw.close();
46.        fr.close();
47. 
48. 
49.    }
50.}
51. 
```

 

### 警告：不要用字符流去操作非文本文件

文本文件：.txt  .java  .c  .cpp  ---》建议使用字符流操作 

非文本文件：.jpg,  .mp3  ,  .mp4 , .doc  , .ppt  ---》建议使用字节流操作

利用try-catch-finally处理异常方式

 

```
1.  package com.msb.io01;
2.   
3.  import java.io.*;
4.   
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class Test04 {
9.      //这是一个main方法，是程序的入口：
10.    public static void main(String[] args)  {
11.        //1.有一个源文件
12.        File f1 = new File("d:\\Test.txt");
13.        //2.有一个目标文件：
14.        File f2 = new File("d:\\Demo.txt");
15.        //3.搞一个输入的管 怼到源文件上：
16.        FileReader fr = null;
17.        FileWriter fw = null;
18.        try {
19.            fr = new FileReader(f1);
20.            //4.搞一个输出的管，怼到目标文件上：
21.            fw = new FileWriter(f2);
22. 
23.            //5.开始动作：
24.            char[] ch = new char[5];
25.            int len = fr.read(ch);
26.            while(len!=-1){
27.                String s = new String(ch,0,len);
28.                fw.write(s);
29.                len = fr.read(ch);
30.            }
31.        } catch (FileNotFoundException e) {
32.            e.printStackTrace();
33.        } catch (IOException e) {
34.            e.printStackTrace();
35.        } finally {
36.            //6.关闭流：(关闭流的时候，倒着关闭，后用先关)
37.            try {
38.                if(fw!=null){//防止空指针异常
39.                    fw.close();
40.                }
41.            } catch (IOException e) {
42.                e.printStackTrace();
43.            }
44. 
45.            try {
46.                if(fr!=null){
47.                    fr.close();
48.                }
49.            } catch (IOException e) {
50.                e.printStackTrace();
51.            }
52. 
53.        }
54. 
55. 
56. 
57. 
58. 
59.    }
60.}
61. 
```

 

### FileInputStream读取文件中内容

【1】读取文本文件：

```
1.  package com.msb.io02;
2.   
3.  import java.io.File;
4.  import java.io.FileInputStream;
5.  import java.io.FileNotFoundException;
6.  import java.io.IOException;
7.   
8.  /**
9.   * @author : msb-zhaoss
10. */
11.public class Test01 {
12.    //这是一个main方法，是程序的入口：
13.    public static void main(String[] args) throws IOException {
14.        //功能：利用字节流将文件中内容读到程序中来：
15.        //1.有一个源文件：
16.        File f = new File("D:\\Test.txt");
17.        //2.将一个字节流这个管 怼  到 源文件上：
18.        FileInputStream fis = new FileInputStream(f);
19.        //3.开始读取动作
20.        /*
21.        细节1：
22.        文件是utf-8进行存储的，所以英文字符 底层实际占用1个字节
23.        但是中文字符，底层实际占用3个字节。
24. 
25.        细节2：
26.        如果文件是文本文件，那么就不要使用字节流读取了，建议使用字符流。
27. 
28.        细节3：
29.        read()读取一个字节，但是你有没有发现返回值是 int类型，而不是byte类型？
30.        read方法底层做了处理，让返回的数据都是“正数”
31.        就是为了避免如果字节返回的是-1的话，那到底是读入的字节，还是到文件结尾呢。
32.         */
33.        int n = fis.read();
34.        while(n!=-1){
35.            System.out.println(n);
36.            n = fis.read();
37.        }
38.        //4.关闭流：
39.        fis.close();
40. 
41.    }
42.}
43. 
```

 

【2】利用字节流读取非文本文件：（以图片为案例：）--》一个字节一个字节的读取：

```
1.  package com.msb.io02;
2.   
3.  import java.io.File;
4.  import java.io.FileInputStream;
5.  import java.io.IOException;
6.   
7.  /**
8.   * @author : msb-zhaoss
9.   */
10.public class Test02 {
11.    //这是一个main方法，是程序的入口：
12.    public static void main(String[] args) throws IOException {
13.        //功能：利用字节流将文件中内容读到程序中来：
14.        //1.有一个源文件：
15.        File f = new File("D:\\LOL.jpg");
16.        //2.将一个字节流这个管 怼  到 源文件上：
17.        FileInputStream fis = new FileInputStream(f);
18.        //3.开始读取动作
19.        int count = 0;//定义一个计数器，用来计读入的字节的个数
20.        int n = fis.read();
21.        while(n!=-1){
22.            count++;
23.            System.out.println(n);
24.            n = fis.read();
25.        }
26.        System.out.println("count="+count);
27.        //4.关闭流：
28.        fis.close();
29. 
30.    }
31.}
32. 
```

 

【3】利用字节类型的缓冲数组： 

```
1.  package com.msb.io02;
2.   
3.  import java.io.File;
4.  import java.io.FileInputStream;
5.  import java.io.IOException;
6.   
7.  /**
8.   * @author : msb-zhaoss
9.   */
10.public class Test03 {
11.    //这是一个main方法，是程序的入口：
12.    public static void main(String[] args) throws IOException {
13.        //功能：利用字节流将文件中内容读到程序中来：
14.        //1.有一个源文件：
15.        File f = new File("D:\\LOL.jpg");
16.        //2.将一个字节流这个管 怼  到 源文件上：
17.        FileInputStream fis = new FileInputStream(f);
18.        //3.开始读取动作
19.        //利用缓冲数组：（快递员的小车）
20.        byte[] b = new byte[1024*6];
21.        int len = fis.read(b);//len指的就是读取的数组中的有效长度
22.        while(len!=-1){
23.            //System.out.println(len);
24.            for(int i = 0;i<len;i++){
25.                System.out.println(b[i]);
26.            }
27.            len = fis.read(b);
28.        }
29.        //4.关闭流：
30.        fis.close();
31. 
32.    }
33.}
34. 
```

 

### FileInputStream,FileOutputStream完成非文本文件的复制

【1】读入一个字节，写出一个字节：

```
1.  package com.msb.io02;
2.   
3.  import java.io.*;
4.   
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class Test04 {
9.      //这是一个main方法，是程序的入口：
10.    public static void main(String[] args) throws IOException {
11.        //功能：完成图片的复制：
12.        //1.有一个源图片
13.        File f1 = new File("d:\\LOL.jpg");
14.        //2.有一个目标图片：
15.        File f2 = new File("d:\\LOL2.jpg");
16.        //3.有一个输入的管道 怼 到 源文件：
17.        FileInputStream fis = new FileInputStream(f1);
18.        //4.有一个输出的管道 怼到  目标文件上：
19.        FileOutputStream fos = new FileOutputStream(f2);
20.        //5.开始复制：（边读边写）
21.        int n = fis.read();
22.        while(n!=-1){
23.            fos.write(n);
24.            n = fis.read();
25.        }
26.        //6.关闭流：(倒着关闭流，先用后关)
27.        fos.close();
28.        fis.close();
29. 
30. 
31.    }
32.}
33. 
```

【2】利用缓冲字节数组： 

```
1.  package com.msb.io02;
2.   
3.  import java.io.File;
4.  import java.io.FileInputStream;
5.  import java.io.FileOutputStream;
6.  import java.io.IOException;
7.   
8.  /**
9.   * @author : msb-zhaoss
10. */
11.public class Test05 {
12.    //这是一个main方法，是程序的入口：
13.    public static void main(String[] args) throws IOException {
14.        //功能：完成图片的复制：
15.        //1.有一个源图片
16.        File f1 = new File("d:\\LOL.jpg");
17.        //2.有一个目标图片：
18.        File f2 = new File("d:\\LOL2.jpg");
19.        //3.有一个输入的管道 怼 到 源文件：
20.        FileInputStream fis = new FileInputStream(f1);
21.        //4.有一个输出的管道 怼到  目标文件上：
22.        FileOutputStream fos = new FileOutputStream(f2);
23.        //5.开始复制：（边读边写）
24.        //利用缓冲数组：
25.        byte[] b = new byte[1024*8];
26.        int len = fis.read(b);
27.        while(len!=-1){
28.            fos.write(b,0,len);
29.            len = fis.read(b);
30.        }
31.        //6.关闭流：(倒着关闭流，先用后关)
32.        fos.close();
33.        fis.close();
34. 
35. 
36.    }
37.}
38. 
```

 

### 缓冲字节流(处理流)-BufferedInputStream ,BufferedOutputStream

【1】读入一个字节，写出一个字节：

![img](https://image.201068.xyz/assets/clip_image956.jpg)

 

 

 

【2】利用缓冲字节数组： 

![img](https://image.201068.xyz/assets/clip_image958.jpg)

 

【3】利用缓冲区： 

![img](https://image.201068.xyz/assets/clip_image960.jpg)想要完成上面的效果，单纯的靠FileInputStream,FileOutputStream是不可以完成的，这个时候就需要功能的加强，

这个加强就需要引入新的流（在FileInputStream,FileOutputStream外面再套一层流）：BufferedInputStream ,BufferedOutputStream. ----->处理流 

 

 

 

 

代码：

```
1.  package com.msb.io02;
2.   
3.  import java.io.*;
4.   
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class Test06 {
9.      //这是一个main方法，是程序的入口：
10.    public static void main(String[] args) throws IOException {
11.        //1.有一个源图片
12.        File f1 = new File("d:\\LOL.jpg");
13.        //2.有一个目标图片：
14.        File f2 = new File("d:\\LOL2.jpg");
15.        //3.有一个输入的管道 怼 到 源文件：
16.        FileInputStream fis = new FileInputStream(f1);
17.        //4.有一个输出的管道 怼到  目标文件上：
18.        FileOutputStream fos = new FileOutputStream(f2);
19.        //5.功能加强，在FileInputStream外面套一个管：BufferedInputStream:
20.        BufferedInputStream bis = new BufferedInputStream(fis);
21.        //6.功能加强，在FileOutputStream外面套一个管：BufferedOutputStream:
22.        BufferedOutputStream bos = new BufferedOutputStream(fos);
23. 
24.        //7.开始动作 ：
25.        byte[] b = new byte[1024*6];
26.        int len = bis.read(b);
27.        while(len!=-1){
28.            bos.write(b,0,len);
29.           /* bos.flush(); 底层已经帮我们做了刷新缓冲区的操作，不用我们手动完成：底层调用flushBuffer()*/
30.            len = bis.read(b);
31.        }
32. 
33.        //8.关闭流：
34.        //倒着关：
35.        //如果处理流包裹着节点流的话，那么其实只要关闭高级流（处理流），那么里面的字节流也会随之被关闭。
36.        bos.close();
37.        bis.close();
38.        /*fos.close();
39.        fis.close();*/
40.    }
41.}
42. 
```

###  

### 比对非文本文件复制的三种方法的效率

【1】读入一个字节，写出一个字节：

![img](https://image.201068.xyz/assets/clip_image962.jpg)

 

【2】利用缓冲字节数组： 

![img](https://image.201068.xyz/assets/clip_image964.jpg)

 

【3】利用缓冲区： 

![img](https://image.201068.xyz/assets/clip_image966.jpg)

 

 

 

 

代码：

```
1.  package com.msb.io02;
2.   
3.  import java.io.*;
4.   
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class Test06 {
9.      //这是一个main方法，是程序的入口：
10.    public static void main(String[] args) throws IOException {
11.        //1.有一个源图片
12.        File f1 = new File("d:\\LOL.jpg");
13.        //2.有一个目标图片：
14.        File f2 = new File("d:\\LOL2.jpg");
15.        //3.有一个输入的管道 怼 到 源文件：
16.        FileInputStream fis = new FileInputStream(f1);
17.        //4.有一个输出的管道 怼到  目标文件上：
18.        FileOutputStream fos = new FileOutputStream(f2);
19.        //5.功能加强，在FileInputStream外面套一个管：BufferedInputStream:
20.        BufferedInputStream bis = new BufferedInputStream(fis);
21.        //6.功能加强，在FileOutputStream外面套一个管：BufferedOutputStream:
22.        BufferedOutputStream bos = new BufferedOutputStream(fos);
23. 
24.        //7.开始动作 ：
25.        long startTime = System.currentTimeMillis();
26.        byte[] b = new byte[1024];
27.        int len = bis.read(b);
28.        while(len!=-1){
29.            bos.write(b,0,len);
30.           /* bos.flush(); 底层已经帮我们做了刷新缓冲区的操作，不用我们手动完成：底层调用flushBuffer()*/
31.            len = bis.read(b);
32.        }
33.        long endTime = System.currentTimeMillis();
34.        System.out.println("复制完成的时间为："+(endTime-startTime));
35.        //8.关闭流：
36.        //倒着关：
37.        //如果处理流包裹着节点流的话，那么其实只要关闭高级流（处理流），那么里面的字节流也会随之被关闭。
38.        bos.close();
39.        bis.close();
40.        /*fos.close();
41.        fis.close();*/
42.    }
43.}
44. 
```

 

### 缓冲字符流(处理流)-BufferedReader,BufferedWriter完成文本文件的复制

```
1.  package com.msb.io02;
2.   
3.  import java.io.*;
4.   
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class Test07 {
9.      //这是一个main方法，是程序的入口：
10.    public static void main(String[] args) throws IOException {
11.        //1.有一个源文件：
12.        File f1 = new File("d:\\Test.txt");
13.        //2.有一个目标文件：
14.        File f2 = new File("d:\\Demo.txt");
15.        //3.需要一个管 怼到 源文件：
16.        FileReader fr = new FileReader(f1);
17.        //4.需要一根管怼到目标文件：
18.        FileWriter fw = new FileWriter(f2);
19.        //5.套一根管在输入字符流外面：
20.        BufferedReader br = new BufferedReader(fr);
21.        //6.套一根管在输出字符流外面：
22.        BufferedWriter bw = new BufferedWriter(fw);
23.        //7.开始动作：
24.        //方式1：读取一个字符，输出一个字符：
25.        /*int n = br.read();
26.        while(n!=-1){
27.            bw.write(n);
28.            n = br.read();
29.        }*/
30. 
31.        //方式2:利用缓冲数组：
32.        /*char[] ch = new char[30];
33.        int len = br.read(ch);
34.        while(len!=-1){
35.            bw.write(ch,0,len);
36.            len = br.read(ch);
37.        }*/
38. 
39.        //方式3：读取String：
40.        String str = br.readLine();//每次读取文本文件中一行，返回字符串
41.        while(str!=null){
42.            bw.write(str);
43.            //在文本文件中应该再写出一个换行：
44.            bw.newLine();//新起一行
45.            str = br.readLine();
46.        }
47. 
48. 
49.        //8.关闭流
50.        bw.close();
51.        br.close();
52.    }
53.}
54. 
```

 

 

### 转换流-InputStreamReader,OutputStreamWriter

【1】转换流：作用：将字节流和字符流进行转换。

【2】转换流  属于 字节流还是字符流？属于字符流 

InputStreamReader  ：字节输入流 ---》字符的输入流 

OutputStreamWriter  ： 字符输出流 --》字节的输出流 

 

【3】图解：

![img](https://image.201068.xyz/assets/clip_image968.jpg)

 

 

【4】将输入的字节流转换为输入的字符流，然后完成文件--》程序 ： 

```
1.  package com.msb.io03;
2.   
3.  import java.io.*;
4.   
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class Test01 {
9.      //这是一个main方法，是程序的入口：
10.    public static void main(String[] args) throws IOException {
11.        //文件---》程序：
12.        //1.有一个源文件：
13.        File f = new File("d:\\Test.txt");
14.        //2.需要一个输入的字节流接触文件：
15.        FileInputStream fis = new FileInputStream(f);
16.        //3.加入一个转换流，将字节流转换为字符流：（转换流属于一个处理流）
17.        //将字节转换为字符的时候，需要指定一个编码，这个编码跟文件本身的编码格式统一
18.        //如果编码格式不统一的话，那么在控制台上展示的效果就会出现乱码
19.        //InputStreamReader isr = new InputStreamReader(fis,"utf-8");
20.        //获取程序本身的编码--》utf-8
21.        InputStreamReader isr = new InputStreamReader(fis);
22.        //4.开始动作，将文件中内容显示在控制台：
23.        char[] ch = new char[20];
24.        int len = isr.read(ch);
25.        while(len!=-1){
26.            //将缓冲数组转为字符串在控制台上打印出来
27.            System.out.print(new String(ch,0,len));
28.            len = isr.read(ch);
29.        }
30. 
31.        //5.关闭流：
32.        isr.close();
33.    }
34.}
35. 
```

 

### 转换流-InputStreamReader,OutputStreamWriter实现文本文件的复制

```
1.  package com.msb.io03;
2.   
3.  import java.io.*;
4.   
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class Test02 {
9.      //这是一个main方法，是程序的入口：
10.    public static void main(String[] args) throws IOException {
11.        //1.有一个源文件
12.        File f1 = new File("d:\\Test.txt");
13.        //2.有一个目标文件：
14.        File f2 = new File("d:\\Demo.txt");
15.        //3.输入方向：
16.        FileInputStream fis = new FileInputStream(f1);
17.        InputStreamReader isr = new InputStreamReader(fis,"utf-8");
18.        //4.输出方向：
19.        FileOutputStream fos = new FileOutputStream(f2);
20.        OutputStreamWriter osw = new OutputStreamWriter(fos,"gbk");
21.        //5.开始动作：
22.        char[] ch = new char[20];
23.        int len = isr.read(ch);
24.        while(len!=-1){
25.            osw.write(ch,0,len);
26.            len = isr.read(ch);
27.        }
28. 
29.        //6.关闭流：
30.        osw.close();
31.        isr.close();
32. 
33.    }
34.}
35. 
```

 

### System类对IO流的支持

 

【1】System的属性： 

System.in : “标准”输入流。---》默认情况下  从键盘输入 

System.out :“标准”输出流。 ---》默认情况下，输出到控制台。 

 

【2】System.in ：“标准”输入流。---》默认情况下  从键盘输入 

```
1.  public class Test01 {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) throws IOException {
4.          //得到的是标准的输入流：--》从键盘输入：
5.          //InputStream in = System.in;
6.          //调用方法：
7.          //int n = in.read();//read方法等待键盘的录入，所以这个方法是一个阻塞方法。
8.          //System.out.println(n);
9.   
10.        //以前案例：从键盘录入一个int类型的数据：
11.        //从上面的代码证明，键盘录入实际上是：System.in
12.        //形象的理解：System.in管，这个管怼到键盘上去了，所以你从键盘录入的话，就从这个管到程序中了
13.        //Scanner的作用：扫描器：起扫描作用的，扫键盘的从这根管出来的数据
14.        /*Scanner sc = new Scanner(System.in);
15.        int i = sc.nextInt();
16.        System.out.println(i);*/
17. 
18.        //既然Scanner是扫描的作用，不一定非得扫 System.in进来的东西，还可以扫描其他管的内容：
19.        Scanner sc = new Scanner(new FileInputStream(new File("d:\\Test.txt")));
20.        while(sc.hasNext()){
21.            System.out.println(sc.next());
22.        }
23. 
24.    }
25.}
```

 

 

 

 

 

 

【3】System.out  : 返回的输出流 、 打印流（PrintStream） 

```
1.  package com.msb.io04;
2.   
3.  import java.io.PrintStream;
4.   
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class Test02 {
9.      //这是一个main方法，是程序的入口：
10.    public static void main(String[] args) {
11.        //写到控制台：
12.        PrintStream out = System.out;
13.        //调用方法：
14.        out.print("你好1");//直接在控制台写出，但是不换行
15.        out.print("你好2");
16.        out.print("你好3");
17.        out.print("你好4");
18. 
19.        out.println("我是中国人1");//直接在控制台写出，并且换行操作
20.        out.println("我是中国人2");
21.        out.println("我是中国人3");
22.        out.println("我是中国人4");
23. 
24.        System.out.println("你是");
25.        System.out.print("中国人");
26. 
27.    }
28.}
29. 
```

 

### 练习：键盘录入内容输出到文件中

【1】解决思路：

![img](https://image.201068.xyz/assets/clip_image970.jpg)

 

【2】代码： 

```
1.  package com.msb.io04;
2.   
3.  import java.io.*;
4.   
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class Test03 {
9.      //这是一个main方法，是程序的入口：
10.    public static void main(String[] args) throws IOException {
11.        //1.先准备输入方向：
12.        //键盘录入：
13.        InputStream in = System.in;//属于字节流
14.        //字节流--》字符流：
15.        InputStreamReader isr = new InputStreamReader(in);
16.        //在isr外面再套一个缓冲流：
17.        BufferedReader br = new BufferedReader(isr);
18. 
19.        //2.再准备输出方向：
20.        //准备目标文件
21.        File f = new File("d:\\Demo1.txt");
22.        FileWriter fw = new FileWriter(f);
23.        BufferedWriter bw = new BufferedWriter(fw);
24. 
25.        //3.开始动作：
26.        String s = br.readLine();
27.        while(!s.equals("exit")){
28.            bw.write(s);
29.            bw.newLine();//文件中换行
30.            s = br.readLine();
31.        }
32. 
33.        //4.关闭流：
34.        bw.close();
35.        br.close();
36.    }
37.}
38. 
```

 

### 数据流-DataInputStream,DataOutputStream

【1】数据流：用来操作基本数据类型和字符串的

【2】 

DataInputStream:将文件中存储的基本数据类型和字符串  写入  内存的变量中 

DataOutputStream: 将内存中的基本数据类型和字符串的变量 写出  文件中 

 

【3】代码： 

利用DataOutputStream向外写出变量： 

 

 

 

```
1.  public class Test01 {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) throws IOException {
4.          //DataOutputStream:  将内存中的基本数据类型和字符串的变量 写出  文件中
5.          /*File f = new File("d:\\Demo2.txt");
6.          FileOutputStream fos = new FileOutputStream(f);
7.          DataOutputStream dos = new DataOutputStream(fos);*/
8.          DataOutputStream dos = new DataOutputStream(new FileOutputStream(new File("d:\\Demo2.txt")));
9.          //向外将变量写到文件中去：
10.        dos.writeUTF("你好");
11.        dos.writeBoolean(false);
12.        dos.writeDouble(6.9);
13.        dos.writeInt(82);
14. 
15.        //关闭流：
16.        dos.close();
17.    }
18.}
```

在Demo2.txt文件中，我们看到： 

![img](https://image.201068.xyz/assets/clip_image972.jpg)

 

发现：这个内容我们看不懂，是给程序看的

 

所以下面我们开始读取的程序：

```
1.  package com.msb.io05;
2.   
3.  import java.io.*;
4.   
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class Test02 {
9.      //这是一个main方法，是程序的入口：
10.    public static void main(String[] args) throws IOException {
11.        //DataInputStream:将文件中存储的基本数据类型和字符串  写入  内存的变量中
12.        DataInputStream dis = new DataInputStream(new FileInputStream(new File("d:\\Demo2.txt")));
13.        //将文件中内容读取到程序中来：
14.        System.out.println(dis.readUTF());
15.        System.out.println(dis.readBoolean());
16.        System.out.println(dis.readDouble());
17.        System.out.println(dis.readInt());
18. 
19.        //关闭流：
20.        dis.close();
21. 
22.    }
23.}
24. 
```

 

结果： 

![img](https://image.201068.xyz/assets/clip_image974.jpg)

 

 

验证：那个文件，我们看不懂，程序看得懂

要求：

写出的类型跟读入的类型 必须 要匹配！ 

 

### 对象流-ObjectInputStream,ObjectOutputStream

【1】对象流：ObjectInputStream，ObjectInputStream 

用于存储和读取基本数据类型数据或对象的处理流。

它的强大之处就是可以把Java中的对象写入到数据源中，也能把对象从数据源中还原回来。 

 

【2】序列化和反序列化： 

ObjectOutputStream 类 ： 把内存中的Java对象转换成平台无关的二进制数据，从而允许把这种二进制数据持久地保存在磁盘上，或通过网络将这种二进制数据传输到另一个网络节点。----》序列化 

用ObjectInputStream类 ： 当其它程序获取了这种二进制数据，就可以恢复成原来的Java对象。----》反序列化 

 

【3】代码：操作字符串对象： 

首先将一个字符串对象写到文件中去：----》序列化 

```
1.  public class Test01 {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) throws IOException {
4.   
5.          ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream(new File("d:\\Demo3.txt")));
6.          //将内存中的字符串写出到文件中：
7.          oos.writeObject("你好");
8.          //关闭流：
9.          oos.close();
10.    }
11.}
```

查看文件：

![img](https://image.201068.xyz/assets/clip_image976.jpg)

我们看不懂文件的内容，但是程序是可以看懂的，所以可以写一个程序读文件中内容：----》反序列化 

```
1.  public class Test02 {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) throws IOException, ClassNotFoundException {
4.          //将文件中保存的字符串 读入到 内存：
5.          ObjectInputStream ois = new ObjectInputStream(new FileInputStream(new File("d:\\Demo3.txt")));
6.          //读取：
7.          String s = (String)(ois.readObject());
8.          System.out.println(s);
9.          //关闭流：
10.        ois.close();
11.    }
12.}
```

控制台：

![img](https://image.201068.xyz/assets/clip_image978.jpg)

 

【4】代码：操作自定义类的对象： 

自定义的Person类： 

 

 

```
1.  public class Person {
2.      private String name;
3.      private int age;
4.   
5.      public String getName() {
6.          return name;
7.      }
8.   
9.      public void setName(String name) {
10.        this.name = name;
11.    }
12. 
13.    public int getAge() {
14.        return age;
15.    }
16. 
17.    public void setAge(int age) {
18.        this.age = age;
19.    }
20. 
21.    public Person() {
22.    }
23. 
24.    public Person(String name, int age) {
25.        this.name = name;
26.        this.age = age;
27.    }
28.}
```

测试类：

```
1.  public class Test01 {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) throws IOException {
4.          //序列化：将内存中对象 ---》 文件：
5.          //有一个对象：
6.          Person p = new Person("lili",19);
7.          //有对象流：
8.          ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream(new File("d:\\Demo4.txt")));
9.          //向外写：
10.        oos.writeObject(p);
11.        //关闭流：
12.        oos.close();
13.    }
14.}
```

运行的时候发现出现异常：

![img](https://image.201068.xyz/assets/clip_image980.jpg)

 

出现异常的原因：

你想要序列化的那个对象对应的类，必须要实现一个接口： 

![img](https://image.201068.xyz/assets/clip_image982.jpg)

接口内部，什么都没有，这种接口叫 标识接口。 

起到标识作用，标识什么呢？只要实现这个接口的类的对象才能序列化，否则不可以。 

 

解决办法：将Person 实现这个标识接口就可以： 

```
1.  public class Person implements Serializable {
2.      private String name;
3.      private int age;
4.   
5.      public String getName() {
6.          return name;
7.      }
8.   
9.      public void setName(String name) {
10.        this.name = name;
11.    }
12. 
13.    public int getAge() {
14.        return age;
15.    }
16. 
17.    public void setAge(int age) {
18.        this.age = age;
19.    }
20. 
21.    public Person() {
22.    }
23. 
24.    public Person(String name, int age) {
25.        this.name = name;
26.        this.age = age;
27.    }
28.}
```

测试：发现序列化成功，Person具备了序列化的能力。 

![img](https://image.201068.xyz/assets/clip_image984.jpg)

这个二进制数据我们看不懂，但是程序可以看懂，所以我们可以用程序实现 反序列化操作： 

将这个对象 恢复到内存中来： 

```
1.  public class Test02 {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) throws IOException, ClassNotFoundException {
4.          ObjectInputStream ois = new ObjectInputStream(new FileInputStream(new File("d:\\Demo4.txt")));
5.          //读入内存：
6.          Person p = (Person)(ois.readObject());
7.          System.out.println(p/*.toString()*/);
8.          //关闭流：
9.          ois.close();
10.    }
11.}
```

结果：

因为我们没有重写toString方法，所以结果为： 

![img](https://image.201068.xyz/assets/clip_image986.jpg)

证明了反序列化成功：  将二进制数据 --》内存 

 

【5】serialVersionUID： 

凡是实现Serializable接口（标识接口）的类都有一个表示序列化版本标识符的静态常量: 

➢private static final long serialVersionUID; 

➢serialVersionUID用来表明类的不同版本间的兼容性。简言之，其目的是以序列化对象进行版本控制，有关各版本反序加化时是否兼容。

➢如果类没有显示定义这个静态变量，它的值是Java运行时环境根据类的内部细节自动生成的。若类的实例变量做了修改，serialVersionUID 可能发生变化。故建议，显式声明。 

➢简单来说，Java的序列化机制是通过在运行时判断类的serialVersionUID来验证版本一致性的。在进行反序列化时，JVM会把传来的字节流中的serialVersionUID与本地相应实体类的serialVersionUID进行比较，如果相同就认为是一致的，可以进行反序列化，否则就会出现序列化版本不一致的异常。(InvalidCastException) 

 

我现在在Person类中加入toString方法： 

```
1.  public class Person implements Serializable {
2.      private String name;
3.      private int age;
4.   
5.      public String getName() {
6.          return name;
7.      }
8.   
9.      public void setName(String name) {
10.        this.name = name;
11.    }
12. 
13.    public int getAge() {
14.        return age;
15.    }
16. 
17.    public void setAge(int age) {
18.        this.age = age;
19.    }
20. 
21.    public Person() {
22.    }
23. 
24.    public Person(String name, int age) {
25.        this.name = name;
26.        this.age = age;
27.    }
28. 
29.    @Override
30.    public String toString() {
31.        return "Person{" +
32.                "name='" + name + '\'' +
33.                ", age=" + age +
34.                '}';
35.    }
36.}
```

 

 

再次运行测试类：

出现异常：

![img](https://image.201068.xyz/assets/clip_image988.jpg)

出现异常的原因：

![img](https://image.201068.xyz/assets/clip_image990.jpg)

解决：给这个类 加入一个 序列号：serialVersionUID 

![img](https://image.201068.xyz/assets/clip_image992.jpg)

【6】IDEA中配置序列化版本号： 

![img](https://image.201068.xyz/assets/clip_image994.jpg)

在Person类上：alt+enter: 

![img](https://image.201068.xyz/assets/clip_image996.jpg)

 

回车即可生成

![img](https://image.201068.xyz/assets/clip_image998.jpg)

 

【7】序列化细节： 

（1）被序列化的类的内部的所有属性，必须是可序列化的 （基本数据类型都是可序列化的） 

![img](https://image.201068.xyz/assets/clip_image1000.jpg)

![img](https://image.201068.xyz/assets/clip_image1002.jpg)

（2）static，transient修饰的属性 不可以被序列化。 

 

```
1.  public class Person implements Serializable {
2.   
3.      private static final long serialVersionUID = 8027651838638826533L;
4.      private transient String name;
5.      private static int age;
6.      private Famaily f = new Famaily();
7.   
8.      public String getName() {
9.          return name;
10.    }
11. 
12.    public void setName(String name) {
13.        this.name = name;
14.    }
15. 
16.    public int getAge() {
17.        return age;
18.    }
19. 
20.    public void setAge(int age) {
21.        this.age = age;
22.    }
23. 
24.    public Person() {
25.    }
26. 
27.    @Override
28.    public String toString() {
29.        return "Person{" +
30.                "name='" + name + '\'' +
31.                ", f=" + f + ",age=" + age +
32.                '}';
33.    }
34.}
```

结果：

![img](https://image.201068.xyz/assets/clip_image1004.jpg)

# 第13章_多线程

## 程序，进程，线程

【1】程序，进程，线程

➢程序(program)：是为完成特定任务、用某种语言编写的一组指令的集合,是一段静态的代码。 （程序是静态的） 

 

➢进程(process)：是程序的一次执行过程。正在运行的一个程序，进程作为资源分配的单位，在内存中会为每个进程分配不同的内存区域。 （进程是动态的）是一个动的过程 ，进程的生命周期  :  有它自身的产生、存在和消亡的过程 

 

➢线程(thread)，进程可进一步细化为线程， 是一个程序内部的一条执行路径。 

 若一个进程同一时间并行执行多个线程，就是支持多线程的。

![img](https://image.201068.xyz/assets/clip_image1006.jpg)

 

【2】单核CPU与多核CPU的任务执行：

![img](https://image.201068.xyz/assets/clip_image1008.jpg)

![img](https://image.201068.xyz/assets/clip_image1010.jpg)

 

【3】并行和并发： 

并行：多个CPU同时执行多个任务 

并发：一个CPU“同时”执行多个任务（采用时间片切换） 

## 创建线程的三种方式

## 第一种：继承Thread类

【1】在学习多线程一章之前，以前的代码是单线程的吗？不是，以前也是有三个线程同时执行的。

![img](https://image.201068.xyz/assets/clip_image1012.jpg)

【2】现在我想自己制造多线程---》创建线程 ？？ 

线程类--》线程对象 

![img](https://image.201068.xyz/assets/clip_image1014.jpg)

 

```
1.  package com.msb.test01;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   * 线程类叫：TestThread，不是说你名字中带线程单词你就具备多线程能力了（争抢资源能力）
6.   * 现在想要具备能力，继承一个类：Thread，具备了争抢资源的能力
7.   */
8.  public class TestThread extends Thread{
9.      /*
10.    一会线程对象就要开始争抢资源了，这个线程要执行的任务到底是啥？这个任务你要放在方法中
11.    但是这个方法不能是随便写的一个方法，必须是重写Thread类中的run方法
12.    然后线程的任务/逻辑写在run方法中
13.     */
14.    @Override
15.    public void run() {
16.        //输出1-10
17.        for (int i = 1; i <= 10 ; i++) {
18.            System.out.println(i);
19.        }
20.    }
21.}
22. 
```

 

```
1.  package com.msb.test01;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   * 测试类
6.   */
7.  public class Test {
8.      //这是main方法，程序的入口
9.      public static void main(String[] args) {
10.        //主线程中也要输出十个数：
11.        for (int i = 1; i <= 10 ; i++) {
12.            System.out.println("main1-----"+i);
13.        }
14. 
15.        //制造其他线程，要跟主线程争抢资源：
16.        //具体的线程对象：子线程
17.        TestThread tt = new TestThread();
18.        //tt.run();//调用run方法，想要执行线程中的任务 -->这个run方法不能直接调用，直接调用就会被当做一个普通方法
19.        //想要tt子线程真正起作用比如要启动线程：
20.        tt.start();//start()是Thread类中的方法
21. 
22.        //主线程中也要输出十个数：
23.        for (int i = 1; i <= 10 ; i++) {
24.            System.out.println("main2-----"+i);
25.        }
26.    }
27.}
28. 
```

 

运行结果：

![img](https://image.201068.xyz/assets/clip_image1016.jpg)

 

#### 设置读取线程名字

【1】setName,getName方法来进行设置读取： 

```
1.  package com.msb.test01;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   * 线程类叫：TestThread，不是说你名字中带线程单词你就具备多线程能力了（争抢资源能力）
6.   * 现在想要具备能力，继承一个类：Thread，具备了争抢资源的能力
7.   */
8.  public class TestThread extends Thread{
9.      /*
10.    一会线程对象就要开始争抢资源了，这个线程要执行的任务到底是啥？这个任务你要放在方法中
11.    但是这个方法不能是随便写的一个方法，必须是重写Thread类中的run方法
12.    然后线程的任务/逻辑写在run方法中
13.     */
14.    @Override
15.    public void run() {
16.        //输出1-10
17.        for (int i = 1; i <= 10 ; i++) {
18.            System.out.println(this.getName()+i);
19.        }
20.    }
21.}
22. 
```

 

```
1.  package com.msb.test01;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   * 测试类
6.   */
7.  public class Test {
8.      //这是main方法，程序的入口
9.      public static void main(String[] args) {
10.        //给main方法这个主线程设置名字：
11.        //Thread.currentThread()作用获取当前正在执行的线程
12.        Thread.currentThread().setName("主线程");
13.        //主线程中也要输出十个数：
14.        for (int i = 1; i <= 10 ; i++) {
15.            System.out.println(Thread.currentThread().getName()+"1-------"+i);
16.        }
17. 
18.        //制造其他线程，要跟主线程争抢资源：
19.        //具体的线程对象：子线程
20.        TestThread tt = new TestThread();
21.        tt.setName("子线程");
22.        //tt.run();//调用run方法，想要执行线程中的任务 -->这个run方法不能直接调用，直接调用就会被当做一个普通方法
23.        //想要tt子线程真正起作用比如要启动线程：
24.        tt.start();//start()是Thread类中的方法
25. 
26.        //主线程中也要输出十个数：
27.        for (int i = 1; i <= 10 ; i++) {
28.            System.out.println(Thread.currentThread().getName()+"2-------"+i);
29.        }
30.    }
31.}
32. 
```

【2】通过构造器设置 名字： 

```
1.  package com.msb.test01;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   * 线程类叫：TestThread，不是说你名字中带线程单词你就具备多线程能力了（争抢资源能力）
6.   * 现在想要具备能力，继承一个类：Thread，具备了争抢资源的能力
7.   */
8.  public class TestThread extends Thread{
9.      public TestThread(String name){
10.        super(name);//调用父类的有参构造器
11.    }
12.    /*
13.    一会线程对象就要开始争抢资源了，这个线程要执行的任务到底是啥？这个任务你要放在方法中
14.    但是这个方法不能是随便写的一个方法，必须是重写Thread类中的run方法
15.    然后线程的任务/逻辑写在run方法中
16.     */
17.    @Override
18.    public void run() {
19.        //输出1-10
20.        for (int i = 1; i <= 10 ; i++) {
21.            System.out.println(this.getName()+i);
22.        }
23.    }
24.}
25. 
```

 

 

#### 习题：买火车票

【1】原理：每个窗口都是一个线程对象：

![img](https://image.201068.xyz/assets/clip_image1018.jpg)

 

 

【2】代码： 

```
1.  package com.msb.test02;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class BuyTicketThread extends Thread {
7.      public BuyTicketThread(String name){
8.          super(name);
9.      }
10.    //一共10张票：
11.    static int ticketNum = 10;//多个对象共享10张票
12.    //每个窗口都是一个线程对象：每个对象执行的代码放入run方法中
13.    @Override
14.    public void run() {
15.        //每个窗口后面有100个人在抢票：
16.        for (int i = 1; i <= 100 ; i++) {
17.            if(ticketNum > 0){//对票数进行判断，票数大于零我们才抢票
18.                System.out.println("我在"+this.getName()+"买到了从北京到哈尔滨的第" + ticketNum-- + "张车票");
19.            }
20.        }
21.    }
22.}
23. 
```

 

```
1.  package com.msb.test02;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class Test {
7.      public static void main(String[] args) {
8.          //多个窗口抢票：三个窗口三个线程对象：
9.          BuyTicketThread t1 = new BuyTicketThread("窗口1");
10.        t1.start();
11.        BuyTicketThread t2 = new BuyTicketThread("窗口2");
12.        t2.start();
13.        BuyTicketThread t3 = new BuyTicketThread("窗口3");
14.        t3.start();
15. 
16.    }
17.}
18. 
```

 

### 第二种：实现Runnable接口

【1】代码：

```
1.  package com.msb.test03;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   * TestThread实现了这个接口，才会变成一个线程类
6.   */
7.  public class TestThread implements Runnable{
8.      @Override
9.      public void run() {
10.        //输出1-10数字：
11.        for (int i = 1; i <= 10 ; i++) {
12.            System.out.println(Thread.currentThread().getName()+"----"+i);
13.        }
14.    }
15.}
16. 
```

 

```
1.  package com.msb.test03;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class Test {
7.      public static void main(String[] args) {
8.          //创建子线程对象：
9.          TestThread tt = new TestThread();
10.        Thread t = new Thread(tt,"子线程");
11.        t.start();
12. 
13.        //主线程里面也是打印1-10数字：
14.        for (int i = 1; i <= 10 ; i++) {
15.            System.out.println(Thread.currentThread().getName()+"---"+i);
16.        }
17.    }
18.}
19. 
```

 

运行结果：

![img](https://image.201068.xyz/assets/clip_image1020.jpg)

 

 

 

#### 习题：买火车票

【1】代码：

 

```
1.  package com.msb.test04;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class BuyTicketThread implements Runnable {
7.      int ticketNum = 10;
8.      @Override
9.      public void run() {
10.        for (int i = 1; i <= 100 ; i++) {
11.            if(ticketNum > 0){
12.                System.out.println("我在"+Thread.currentThread().getName()+"买到了北京到哈尔滨的第" + ticketNum-- + "张车票");
13.            }
14.        }
15.    }
16.}
17. 
```

 

```
1.  package com.msb.test04;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class Test {
7.      //这是main方法，程序的入口
8.      public static void main(String[] args) {
9.          //定义一个线程对象：
10.        BuyTicketThread t = new BuyTicketThread();
11.        //窗口1买票：
12.        Thread t1 = new Thread(t,"窗口1");
13.        t1.start();
14.        //窗口2买票：
15.        Thread t2 = new Thread(t,"窗口2");
16.        t2.start();
17.        //窗口3买票：
18.        Thread t3 = new Thread(t,"窗口3");
19.        t3.start();
20.    }
21.}
22. 
```

【2】实际开发中，方式1 继承Thread类  还是  方式2 实现Runnable接口这种方式多呢？--》方式2 

 

（1）方式1的话有 Java单继承的局限性，因为继承了Thread类，就不能再继承其它的类了 

（2）方式2的共享资源的能力也会强一些，不需要非得加个static来修饰 

 

【3】Thread类 Runnable接口 有联系吗？ 

 

![img](https://image.201068.xyz/assets/clip_image1022.jpg)

 

 

 

 

### 第三种：实现Callable接口

对比第一种和第二种创建线程的方式发现，无论第一种继承Thread类的方式还是第二种实现Runnable接口的方式，都需要有一个run方法， 

但是这个run方法有不足： 

![img](https://image.201068.xyz/assets/clip_image1024.jpg)

（1）没有返回值 

（2）不能抛出异常 

 

基于上面的两个不足，在JDK1.5以后出现了第三种创建线程的方式：实现Callable接口： 

 

实现Callable接口好处：（1）有返回值 （2）能抛出异常 

缺点：线程创建比较麻烦

 

```
1.  package com.msb.test05;
2.   
3.  import java.util.Random;
4.  import java.util.concurrent.Callable;
5.  import java.util.concurrent.ExecutionException;
6.  import java.util.concurrent.FutureTask;
7.   
8.  /**
9.   * @author : msb-zhaoss
10. */
11.public class TestRandomNum implements Callable<Integer> {
12.    /*
13.    1.实现Callable接口，可以不带泛型，如果不带泛型，那么call方式的返回值就是Object类型
14.    2.如果带泛型，那么call的返回值就是泛型对应的类型
15.    3.从call方法看到：方法有返回值，可以跑出异常
16.     */
17.    @Override
18.    public Integer call() throws Exception {
19.        return new Random().nextInt(10);//返回10以内的随机数
20.    }
21.}
22. 
23.class Test{
24.    //这是main方法，程序的入口
25.    public static void main(String[] args) throws ExecutionException, InterruptedException {
26.        //定义一个线程对象：
27.        TestRandomNum trn = new TestRandomNum();
28.        FutureTask ft = new FutureTask(trn);
29.        Thread t = new Thread(ft);
30.        t.start();
31.        //获取线程得到的返回值：
32.        Object obj = ft.get();
33.        System.out.println(obj);
34.    }
35.}
36. 
```

 

 

## 线程的生命周期

【1】线程声明周期：线程开始--》线程消亡 

【2】线程经历哪些阶段： 

 

![img](https://image.201068.xyz/assets/clip_image1026.jpg)

 

## 线程常见方法

（1）start() :  启动当前线程，表面上调用start方法，实际在调用线程里面的run方法 

（2）run() : 线程类 继承 Thread类 或者 实现Runnable接口的时候，都要重新实现这个run方法，run方法里面是线程要执行的内容 

（3）currentThread :Thread类中一个静态方法：获取当前正在执行的线程

（4）setName 设置线程名字 

（5）getName 读取线程名字 

 

### 设置优先级

【1】同优先级别的线程，采取的策略就是先到先服务，使用时间片策略

【2】如果优先级别高，被CPU调度的概率就高 

【3】级别：1-10  默认的级别为5 

![img](https://image.201068.xyz/assets/clip_image1028.jpg)

 

【4】代码：

```
1.  package com.msb.test06;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class TestThread01 extends Thread {
7.      @Override
8.      public void run() {
9.          for (int i = 1; i <= 10; i++) {
10.            System.out.println(i);
11.        }
12.    }
13.}
14. 
15.class TestThread02 extends Thread{
16.    @Override
17.    public void run() {
18.        for (int i = 20; i <= 30 ; i++) {
19.            System.out.println(i);
20.        }
21.    }
22.}
23. 
24.class Test{
25.    //这是main方法，程序的入口
26.    public static void main(String[] args) {
27.        //创建两个子线程，让这两个子线程争抢资源：
28.        TestThread01 t1 = new TestThread01();
29.        t1.setPriority(10);//优先级别高
30.        t1.start();
31. 
32.        TestThread02 t2 = new TestThread02();
33.        t2.setPriority(1);//优先级别低
34.        t2.start();
35.    }
36.}
37. 
```

 

 

### join

join方法：当一个线程调用了join方法，这个线程就会先被执行，它执行结束以后才可以去执行其余的线程。 

注意：必须先start，再join才有效。 

```
1.  package com.msb.test07;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class TestThread extends Thread {
7.      public TestThread(String name){
8.          super(name);
9.      }
10.    @Override
11.    public void run() {
12.        for (int i = 1; i <= 10 ; i++) {
13.            System.out.println(this.getName()+"----"+i);
14.        }
15.    }
16.}
17. 
18.class Test{
19.    //这是main方法，程序的入口
20.    public static void main(String[] args) throws InterruptedException {
21.        for (int i = 1; i <= 100 ; i++) {
22.            System.out.println("main-----"+i);
23.            if(i == 6){
24.                //创建子线程：
25.                TestThread tt = new TestThread("子线程");
26.                tt.start();
27.                tt.join();//“半路杀出个程咬金”
28.            }
29. 
30.        }
31.    }
32.}
33. 
```

### sleep

https://go.zbj.com/news/20146.html （段子） 

【1】sleep : 人为的制造阻塞事件 

```
1.  public class Test01 {
2.      //这是main方法，程序的入口
3.      public static void main(String[] args) {
4.          try {
5.              Thread.sleep(3000);
6.          } catch (InterruptedException e) {
7.              e.printStackTrace();
8.          }
9.          System.out.println("00000000000000");
10.    }
11.}
12. 
```

【2】案例：完成秒表功能： 

```
1.  package com.msb.test08;
2.   
3.  import javafx.scene.input.DataFormat;
4.   
5.  import java.text.DateFormat;
6.  import java.text.SimpleDateFormat;
7.  import java.util.Date;
8.   
9.  /**
10. * @author : msb-zhaoss
11. */
12.public class Test02 {
13.    //这是main方法，程序的入口
14.    public static void main(String[] args) {
15.        //2.定义一个时间格式：
16.        DateFormat df = new SimpleDateFormat("HH:mm:ss");
17.        while(true){
18.            //1.获取当前时间：
19.            Date d = new Date();
20.            //3.按照上面定义的格式将Date类型转为指定格式的字符串：
21.            System.out.println(df.format(d));
22.            try {
23.                Thread.sleep(1000);
24.            } catch (InterruptedException e) {
25.                e.printStackTrace();
26.            }
27.        }
28.    }
29.}
30. 
```

 

 

### setDaemon

【1】设置伴随线程

将子线程设置为主线程的伴随线程，主线程停止的时候，子线程也不要继续执行了

案例：皇上 --》驾崩 ---》妃子陪葬 

```
1.  package com.msb.test09;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class TestThread extends Thread {
7.      @Override
8.      public void run() {
9.          for (int i = 1; i <= 1000 ; i++) {
10.            System.out.println("子线程----"+i);
11.        }
12.    }
13.}
14.class Test{
15.    //这是main方法，程序的入口
16.    public static void main(String[] args) {
17.        //创建并启动子线程：
18.        TestThread tt = new TestThread();
19.        tt.setDaemon(true);//设置伴随线程  注意：先设置，再启动
20.        tt.start();
21. 
22.        //主线程中还要输出1-10的数字：
23.        for (int i = 1; i <= 10 ; i++) {
24.            System.out.println("main---"+i);
25.        }
26.    }
27.}
```

 

 

结果：

![img](https://image.201068.xyz/assets/clip_image1030.jpg)

 

### stop

```
1.  package com.msb.test09;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class Demo {
7.      //这是main方法，程序的入口
8.      public static void main(String[] args) {
9.          for (int i = 1; i <= 100 ; i++) {
10.            if(i == 6){
11.                Thread.currentThread().stop();//过期方法，不建议使用
12.            }
13.            System.out.println(i);
14.        }
15.    }
16.}
17. 
```

 

 

## 线程安全问题

【1】出现问题：

（1）出现了两个10张票或者3个10张票： 

![img](https://image.201068.xyz/assets/clip_image1032.jpg)

（2）出现0，-1，-2可能： 

![img](https://image.201068.xyz/assets/clip_image1034.jpg)

 

 

上面的代码出现问题：出现了 重票，错票，---》 线程安全引起的问题 

原因：多个线程，在争抢资源的过程中，导致共享的资源出现问题。一个线程还没执行完，另一个线程就参与进来了，开始争抢。 

 

解决：

 

在我的程序中，加入“锁” --》加同步  --》同步监视器


**方法1：同步代码块**

【1】同步代码块演示1：

```
1.  package com.msb.test04;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class BuyTicketThread implements Runnable {
7.      int ticketNum = 10;
8.      @Override
9.      public void run() {
10.        //此处有1000行代码
11.        for (int i = 1; i <= 100 ; i++) {
12.            synchronized (this){//把具有安全隐患的代码锁住即可，如果锁多了就会效率低 --》this就是这个锁
13.                if(ticketNum > 0){
14.                    System.out.println("我在"+Thread.currentThread().getName()+"买到了北京到哈尔滨的第" + ticketNum-- + "张车票");
15.                }
16.            }
17.        }
18.        //此处有1000行代码
19.    }
20.}
21. 
```

 

【2】同步代码块演示2： 

```
1.  public class BuyTicketThread extends Thread {
2.      public BuyTicketThread(String name){
3.          super(name);
4.      }
5.      //一共10张票：
6.      static int ticketNum = 10;//多个对象共享10张票
7.      //每个窗口都是一个线程对象：每个对象执行的代码放入run方法中
8.      @Override
9.      public void run() {
10.        //每个窗口后面有100个人在抢票：
11.        for (int i = 1; i <= 100 ; i++) {
12.            synchronized (BuyTicketThread.class){//锁必须多个线程用的是同一把锁！！！
13.                if(ticketNum > 0){//对票数进行判断，票数大于零我们才抢票
14.                    System.out.println("我在"+this.getName()+"买到了从北京到哈尔滨的第" + ticketNum-- + "张车票");
15.                }
16.            }
17.        }
18.    }
19.}
```

【3】同步监视器总结： 

总结1：认识同步监视器（锁子）  -----  synchronized(同步监视器){ } 

1)必须是引用数据类型，不能是基本数据类型 

2)也可以创建一个专门的同步监视器，没有任何业务含义 

3)一般使用共享资源做同步监视器即可   

4)在同步代码块中不能改变同步监视器对象的引用 

![img](https://image.201068.xyz/assets/clip_image1036.jpg)

5)尽量不要String和包装类Integer做同步监视器 

6)建议使用final修饰同步监视器

 

总结2：同步代码块的执行过程 

1)第一个线程来到同步代码块，发现同步监视器open状态，需要close,然后执行其中的代码 

2)第一个线程执行过程中，发生了线程切换（阻塞 就绪），第一个线程失去了cpu，但是没有开锁open 

3)第二个线程获取了cpu，来到了同步代码块，发现同步监视器close状态，无法执行其中的代码，第二个线程也进入阻塞状态

4)第一个线程再次获取CPU,接着执行后续的代码；同步代码块执行完毕，释放锁open 

5)第二个线程也再次获取cpu，来到了同步代码块，发现同步监视器open状态，拿到锁并且上锁，由阻塞状态进入就绪状态，再进入运行状态，重复第一个线程的处理过程（加锁）

强调：同步代码块中能发生CPU的切换吗？能！！！ 但是后续的被执行的线程也无法执行同步代码块（因为锁仍旧close） 

 

总结3：其他 

1)多个代码块使用了同一个同步监视器（锁），锁住一个代码块的同时，也锁住所有使用该锁的所有代码块，其他线程无法访问其中的任何一个代码块 

2)多个代码块使用了同一个同步监视器（锁），锁住一个代码块的同时，也锁住所有使用该锁的所有代码块， 但是没有锁住使用其他同步监视器的代码块，其他线程有机会访问其他同步监视器的代码块 

 

### 方法2：同步方法

【1】代码展示：

```
1.  ublic class BuyTicketThread implements Runnable {
2.      int ticketNum = 10;
3.      @Override
4.      public void run() {
5.          //此处有1000行代码
6.          for (int i = 1; i <= 100 ; i++) {
7.              buyTicket();
8.          }
9.          //此处有1000行代码
10.    }
11. 
12.    public synchronized void buyTicket(){//锁住的是this
13.        if(ticketNum > 0){
14.            System.out.println("我在"+Thread.currentThread().getName()+"买到了北京到哈尔滨的第" + ticketNum-- + "张车票");
15.        }
16.    }
17.}
```

 

```
1.  public class BuyTicketThread extends Thread {
2.      public BuyTicketThread(String name){
3.          super(name);
4.      }
5.      //一共10张票：
6.      static int ticketNum = 10;//多个对象共享10张票
7.      //每个窗口都是一个线程对象：每个对象执行的代码放入run方法中
8.      @Override
9.      public void run() {
10.        //每个窗口后面有100个人在抢票：
11.        for (int i = 1; i <= 100 ; i++) {
12.            buyTicket();
13.        }
14.    }
15. 
16.    public static synchronized void buyTicket(){//锁住的  同步监视器： BuyTicketThread.class
17.        if(ticketNum > 0){//对票数进行判断，票数大于零我们才抢票
18.            System.out.println("我在"+Thread.currentThread().getName()+"买到了从北京到哈尔滨的第" + ticketNum-- + "张车票");
19.        }
20.    }
21. 
22.}
```

 

 

【2】总结： 

总结1： 

多线程在争抢资源，就要实现线程的同步（就要进行加锁，并且这个锁必须是共享的，必须是唯一的。

咱们的锁一般都是引用数据类型的。

目的：解决了线程安全问题。

 

总结2：关于同步方法 

\1) 不要将run()定义为同步方法 

\2) 非静态同步方法的同步监视器是this 

  静态同步方法的同步监视器是 类名.class 字节码信息对象 

\3) 同步代码块的效率要高于同步方法

   原因：同步方法是将线程挡在了方法的外部，而同步代码块锁将线程挡在了代码块的外部，但是却是方法的内部

\4) 同步方法的锁是this，一旦锁住一个方法，就锁住了所有的同步方法；同步代码块只是锁住使用该同步监视器的代码块，而没有锁住使用其他监视器的代码块 

 

### 方法3：Lock锁

【1】Lock锁引入： 

JDK1.5后新增新一代的线程同步方式:Lock锁 

与采用synchronized相比，lock可提供多种锁方案，更灵活 

 

 

synchronized是Java中的关键字，这个关键字的识别是靠JVM来识别完成的呀。是虚拟机级别的。 

但是Lock锁是API级别的，提供了相应的接口和对应的实现类，这个方式更灵活，表现出来的性能优于之前的方式。

 

 

 

 

【2】代码演示： 

```
1.  package com.msb.test04;
2.   
3.  import java.util.concurrent.locks.Lock;
4.  import java.util.concurrent.locks.ReentrantLock;
5.   
6.  /**
7.   * @author : msb-zhaoss
8.   */
9.  public class BuyTicketThread implements Runnable {
10.    int ticketNum = 10;
11.    //拿来一把锁：
12.    Lock lock = new ReentrantLock();//多态  接口=实现类  可以使用不同的实现类
13.    @Override
14.    public void run() {
15.        //此处有1000行代码
16.        for (int i = 1; i <= 100 ; i++) {
17.            //打开锁：
18.            lock.lock();
19.            try{
20.                if(ticketNum > 0){
21.                    System.out.println("我在"+Thread.currentThread().getName()+"买到了北京到哈尔滨的第" + ticketNum-- + "张车票");
22.                }
23.            }catch (Exception ex){
24.                ex.printStackTrace();
25.            }finally {
26.                //关闭锁：--->即使有异常，这个锁也可以得到释放
27.                lock.unlock();
28.            }
29. 
30.        }
31.        //此处有1000行代码
32.    }
33.}
34. 
```

 

 

【3】 Lock和synchronized的区别 

 

​    1.Lock是显式锁（手动开启和关闭锁，别忘记关闭锁），synchronized是隐式锁 

​    2.Lock只有代码块锁，synchronized有代码块锁和方法锁 

​    3.使用Lock锁，JVM将花费较少的时间来调度线程，性能更好。并且具有更好的扩展性（提供更多的子类）

 

【4】优先使用顺序： 

 

​    Lock----同步代码块（已经进入了方法体，分配了相应资源）----同步方法（在方法体之外） 

 

### 线程同步的优缺点

【1】对比： 

线程安全，效率低 

线程不安全，效率高 

 

【2】可能造成死锁： 

死锁 

\>不同的线程分别占用对方需要的同步资源不放弃，都在等待对方放弃自己需要的同步资源，就形成了线程的死锁

\>出现死锁后，不会出现异常，不会出现提示，只是所有的线程都处于阻塞状态，无法继续 

 

【3】代码演示： 

```
1.  public class TestDeadLock implements Runnable {
2.      public int flag = 1;
3.      static Object o1 = new Object(),o2 = new Object();
4.          
5.          
6.      public void run(){
7.          System.out.println("flag=" + flag);
8.          // 当flag==1锁住o1
9.          if (flag == 1) {
10.            synchronized (o1) {
11.                try {
12.                    Thread.sleep(500);
13.                } catch (Exception e) {
14.                    e.printStackTrace();
15.                }
16.                // 只要锁住o2就完成
17.                synchronized (o2) {
18.                    System.out.println("2");
19.                }
20.            }
21.        }
22.        // 如果flag==0锁住o2
23.        if (flag == 0) {
24.            synchronized (o2) {
25.                try {
26.                    Thread.sleep(500);
27.                } catch (Exception e) {
28.                    e.printStackTrace();
29.                }
30.                // 只要锁住o1就完成
31.                synchronized (o1) {
32.                    System.out.println("3");
33.                }
34.            }
35.        }
36.    }
37.        
38.        
39.    public static void main(String[] args) {
40.        // 实例2个线程类
41.        TestDeadLock td1 = new TestDeadLock();
42.        TestDeadLock td2 = new TestDeadLock();
43.        td1.flag = 1;
44.        td2.flag = 0;
45.        // 开启2个线程
46.        Thread t1 = new Thread(td1);
47.        Thread t2 = new Thread(td2);
48.        t1.start();
49.        t2.start();
50.    }
51.}
```

 

【4】解决方法： 减少同步资源的定义，避免嵌套同步 

 

 

## 线程通信问题

应用场景：生产者和消费者问题 

假设仓库中只能存放一件产品，生产者将生产出来的产品放入仓库，消费者将仓库中产品取走消费

如果仓库中没有产品，则生产者将产品放入仓库，否则停止生产并等待，直到仓库中的产品被消费者取走为止

如果仓库中放有产品，则消费者可以将产品取走消费，否则停止消费并等待，直到仓库中再次放入产品为止

 ![img](https://image.201068.xyz/assets/clip_image1038.jpg) 

 

代码结果展示：

![img](https://image.201068.xyz/assets/clip_image1040.jpg)

 

 

代码：

1.商品：属性：品牌 ，名字 

2.线程1：生产者

3.线程2：消费者

 

### 分解1

出现问题： 

1.生产者和消费者没有交替输出 

 

2.打印数据错乱 

哈尔滨 - null 

费列罗啤酒

哈尔滨巧克力

----没有加同步 

 

代码展示：

```
1.  package com.msb.test10;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class Product {//商品类
7.      //品牌
8.      private String brand;
9.      //名字
10.    private String name;
11.    //setter,getter方法；
12. 
13.    public String getBrand() {
14.        return brand;
15.    }
16. 
17.    public void setBrand(String brand) {
18.        this.brand = brand;
19.    }
20. 
21.    public String getName() {
22.        return name;
23.    }
24. 
25.    public void setName(String name) {
26.        this.name = name;
27.    }
28.}
29. 
```

 

```
1.  package com.msb.test10;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class ProducerThread extends Thread{//生产者线程
7.      //共享商品：
8.      private Product p;
9.   
10.    public ProducerThread(Product p) {
11.        this.p = p;
12.    }
13. 
14.    @Override
15.    public void run() {
16.        for (int i = 1; i <= 10 ; i++) {//生产十个商品 i:生产的次数
17.            if(i % 2 == 0){
18.                //生产费列罗巧克力
19.                p.setBrand("费列罗");
20.                try {
21.                    Thread.sleep(100);
22.                } catch (InterruptedException e) {
23.                    e.printStackTrace();
24.                }
25.                p.setName("巧克力");
26.            }else{
27.                //生产哈尔滨啤酒
28.                p.setBrand("哈尔滨");
29.                try {
30.                    Thread.sleep(100);
31.                } catch (InterruptedException e) {
32.                    e.printStackTrace();
33.                }
34.                p.setName("啤酒");
35.            }
36. 
37.            //将生产信息做一个打印：
38.            System.out.println("生产者生产了：" + p.getBrand() + "---" + p.getName());
39.        }
40.    }
41.}
42. 
```

 

```
1.  package com.msb.test10;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class CustomerThread extends Thread{//消费者线程
7.      //共享商品：
8.      private Product p;
9.   
10.    public CustomerThread(Product p) {
11.        this.p = p;
12.    }
13. 
14.    @Override
15.    public void run() {
16.        for (int i = 1; i <= 10 ; i++) {//i:消费次数
17.            System.out.println("消费者消费了：" + p.getBrand() + "---" + p.getName());
18.        }
19.    }
20.}
21. 
```

 

```
1.  package com.msb.test10;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class Test {
7.      //这是main方法，程序的入口
8.      public static void main(String[] args) {
9.          //共享的商品：
10.        Product p = new Product();
11.        //创建生产者和消费者线程：
12.        ProducerThread pt = new ProducerThread(p);
13.        CustomerThread ct = new CustomerThread(p);
14. 
15.        pt.start();
16.        ct.start();
17.    }
18.}
19. 
```

 

 

 

 

 

 

 

 

 

 

### 分解2

【1】利用同步代码块解决问题：

```
1.  package com.msb.test10;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class ProducerThread extends Thread{//生产者线程
7.      //共享商品：
8.      private Product p;
9.   
10.    public ProducerThread(Product p) {
11.        this.p = p;
12.    }
13. 
14.    @Override
15.    public void run() {
16.        for (int i = 1; i <= 10 ; i++) {//生产十个商品 i:生产的次数
17.            synchronized (p){
18.                if(i % 2 == 0){
19.                    //生产费列罗巧克力
20.                    p.setBrand("费列罗");
21.                    try {
22.                        Thread.sleep(100);
23.                    } catch (InterruptedException e) {
24.                        e.printStackTrace();
25.                    }
26.                    p.setName("巧克力");
27.                }else{
28.                    //生产哈尔滨啤酒
29.                    p.setBrand("哈尔滨");
30.                    try {
31.                        Thread.sleep(100);
32.                    } catch (InterruptedException e) {
33.                        e.printStackTrace();
34.                    }
35.                    p.setName("啤酒");
36.                }
37. 
38.                //将生产信息做一个打印：
39.                System.out.println("生产者生产了：" + p.getBrand() + "---" + p.getName());
40.            }
41.        }
42.    }
43.}
44. 
```

 

```
1.  package com.msb.test10;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class CustomerThread extends Thread{//消费者线程
7.      //共享商品：
8.      private Product p;
9.   
10.    public CustomerThread(Product p) {
11.        this.p = p;
12.    }
13. 
14.    @Override
15.    public void run() {
16.        for (int i = 1; i <= 10 ; i++) {//i:消费次数
17.            synchronized (p){
18.                System.out.println("消费者消费了：" + p.getBrand() + "---" + p.getName());
19.            }
20.        }
21.    }
22.}
23. 
```

【2】利用同步方法解决问题： 

```
1.  package com.msb.test11;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class Product {//商品类
7.      //品牌
8.      private String brand;
9.      //名字
10.    private String name;
11.    //setter,getter方法；
12. 
13.    public String getBrand() {
14.        return brand;
15.    }
16. 
17.    public void setBrand(String brand) {
18.        this.brand = brand;
19.    }
20. 
21.    public String getName() {
22.        return name;
23.    }
24. 
25.    public void setName(String name) {
26.        this.name = name;
27.    }
28. 
29.    //生产商品
30.    public synchronized void setProduct(String brand,String name){
31.        this.setBrand(brand);
32.        try {
33.            Thread.sleep(100);
34.        } catch (InterruptedException e) {
35.            e.printStackTrace();
36.        }
37.        this.setName(name);
38. 
39. 
40.        //将生产信息做一个打印：
41.        System.out.println("生产者生产了：" + this.getBrand() + "---" + this.getName());
42.    }
43. 
44.    //消费商品：
45.    public synchronized void getProduct(){
46.        System.out.println("消费者消费了：" + this.getBrand() + "---" + this.getName());
47.    }
48.}
49. 
```

 

```
1.  package com.msb.test11;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class CustomerThread extends Thread{//消费者线程
7.      //共享商品：
8.      private Product p;
9.   
10.    public CustomerThread(Product p) {
11.        this.p = p;
12.    }
13. 
14.    @Override
15.    public void run() {
16.        for (int i = 1; i <= 10 ; i++) {//i:消费次数
17.            p.getProduct();;
18.        }
19.    }
20.}
21. 
```

 

```
1.  public class ProducerThread extends Thread{//生产者线程
2.      //共享商品：
3.      private Product p;
4.   
5.      public ProducerThread(Product p) {
6.          this.p = p;
7.      }
8.   
9.      @Override
10.    public void run() {
11.        for (int i = 1; i <= 10 ; i++) {//生产十个商品 i:生产的次数
12.            if(i % 2 == 0){
13.                p.setProduct("费列罗","巧克力");
14.            }else{
15.                p.setProduct("哈尔滨","啤酒");
16.            }
17.        }
18.    }
19.}
```

（这个else中的代码在分解3中 演示了错误） 

 

 

### 分解3

【1】原理：

![img](https://image.201068.xyz/assets/clip_image1042.jpg)

【2】代码： 

```
1.  package com.msb.test11;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class Product {//商品类
7.      //品牌
8.      private String brand;
9.      //名字
10.    private String name;
11. 
12.    //引入一个灯：true:红色  false 绿色
13.    boolean flag = false;//默认情况下没有商品 让生产者先生产  然后消费者再消费
14.    //setter,getter方法；
15. 
16.    public String getBrand() {
17.        return brand;
18.    }
19. 
20.    public void setBrand(String brand) {
21.        this.brand = brand;
22.    }
23. 
24.    public String getName() {
25.        return name;
26.    }
27. 
28.    public void setName(String name) {
29.        this.name = name;
30.    }
31. 
32.    //生产商品
33.    public synchronized void setProduct(String brand,String name){
34.        if(flag == true){//灯是红色，证明有商品，生产者不生产，等着消费者消费
35.            try {
36.                wait();
37.            } catch (InterruptedException e) {
38.                e.printStackTrace();
39.            }
40.        }
41.        //灯是绿色的，就生产：
42.        this.setBrand(brand);
43.        try {
44.            Thread.sleep(100);
45.        } catch (InterruptedException e) {
46.            e.printStackTrace();
47.        }
48.        this.setName(name);
49.        //将生产信息做一个打印：
50.        System.out.println("生产者生产了：" + this.getBrand() + "---" + this.getName());
51. 
52.        //生产完以后，灯变色：变成红色：
53.        flag = true;
54.        //告诉消费者赶紧来消费：
55.        notify();
56.    }
57. 
58.    //消费商品：
59.    public synchronized void getProduct(){
60.        if(!flag){//flag == false没有商品，等待生产者生产：
61.            try {
62.                wait();
63.            } catch (InterruptedException e) {
64.                e.printStackTrace();
65.            }
66.        }
67. 
68.        //有商品，消费：
69.        System.out.println("消费者消费了：" + this.getBrand() + "---" + this.getName());
70. 
71.        //消费完：灯变色：
72.        flag = false;
73.        //通知生产者生产：
74.        notify();
75.    }
76.}
77. 
```

【3】原理： 

![img](https://image.201068.xyz/assets/clip_image1044.jpg)

 

注意：wait方法和notify方法 是必须放在同步方法或者同步代码块中才生效的 （因为在同步的基础上进行线程的通信才是有效的） 

注意：sleep和wait的区别：sleep进入阻塞状态没有释放锁，wait进入阻塞状态但是同时释放了锁 

【4】线程生命周期完整图： 

![img](https://image.201068.xyz/assets/clip_image1046.jpg)

 

### Loc锁情况下的线程通信

Condition是在[Java ](http://lib.csdn.net/base/java)1.5中才出现的，它用来替代传统的Object的wait()、notify()实现线程间的协作，相比使用Object的wait()、notify()，使用Condition1的await()、signal()这种方式实现线程间协作更加安全和高效。 

 

它的更强大的地方在于：能够更加精细的控制多线程的休眠与唤醒。对于同一个锁，我们可以创建多个Condition，在不同的情况下使用不同的Condition 

一个Condition包含一个等待队列。一个Lock可以产生多个Condition，所以可以有多个等待队列。 

在Object的监视器模型上，一个对象拥有一个同步队列和等待队列，而Lock（同步器）拥有一个同步队列和**多个**等待队列。 

Object中的wait(),notify(),notifyAll()方法是和"同步锁"(synchronized关键字)捆绑使用的；而Condition是需要与"互斥锁"/"共享锁"捆绑使用的。 

调用Condition的await()、signal()、signalAll()方法，都必须在lock保护之内，就是说必须在lock.lock()和lock.unlock之间才可以使用 

· Conditon中的await()对应Object的wait()； 

· Condition中的signal()对应Object的notify()； 

· Condition中的signalAll()对应Object的notifyAll()。 

void **await**() throws [InterruptedException](../../../../java/lang/InterruptedException.html) 

造成当前线程在接到信号或被[中断](#interrupt())之前一直处于等待状态。 

与此 Condition 相关的锁以原子方式释放，并且出于线程调度的目的，将禁用当前线程，且在发生以下四种情况*之一* 以前，当前线程将一直处于休眠状态： 

· 其他某个线程调用此 Condition 的 [signal()](#signal()) 方法，并且碰巧将当前线程选为被唤醒的线程；或者

· 其他某个线程调用此 Condition 的 [signalAll()](#signalAll()) 方法；或者 

· 其他某个线程[中断](#interrupt())当前线程，且支持中断线程的挂起；或者

· 发生“*虚假唤醒*” 

在所有情况下，在此方法可以返回当前线程之前，都必须重新获取与此条件有关的锁。在线程返回时，可以保证它保持此锁。

void **signal**()

唤醒一个等待线程。 

如果所有的线程都在等待此条件，则选择其中的一个唤醒。在从 await 返回之前，该线程必须重新获取锁。 

void **signalAll**()

唤醒所有等待线程。 

如果所有的线程都在等待此条件，则唤醒所有线程。在从 await 返回之前，每个线程都必须重新获取锁。   

 

更改代码： 

![img](https://image.201068.xyz/assets/clip_image1048.jpg)

```
1.  package com.msb.test12;
2.   
3.  import java.util.concurrent.locks.Condition;
4.  import java.util.concurrent.locks.Lock;
5.  import java.util.concurrent.locks.ReentrantLock;
6.   
7.  /**
8.   * @author : msb-zhaoss
9.   */
10.public class Product {//商品类
11.    //品牌
12.    private String brand;
13.    //名字
14.    private String name;
15. 
16.    //声明一个Lock锁：
17.    Lock lock = new ReentrantLock();
18.    //搞一个生产者的等待队列：
19.    Condition produceCondition = lock.newCondition();
20.    //搞一个消费者的等待队列：
21.    Condition consumeCondition = lock.newCondition();
22.    //引入一个灯：true:红色  false 绿色
23.    boolean flag = false;//默认情况下没有商品 让生产者先生产  然后消费者再消费
24.    //setter,getter方法；
25. 
26.    public String getBrand() {
27.        return brand;
28.    }
29. 
30.    public void setBrand(String brand) {
31.        this.brand = brand;
32.    }
33. 
34.    public String getName() {
35.        return name;
36.    }
37. 
38.    public void setName(String name) {
39.        this.name = name;
40.    }
41. 
42.    //生产商品
43.    public void setProduct(String brand,String name){
44.        lock.lock();
45.        try{
46.            if(flag == true){//灯是红色，证明有商品，生产者不生产，等着消费者消费
47.                try {
48.                    //wait();
49.                    //生产者阻塞，生产者进入等待队列中
50.                    produceCondition.await();
51.                } catch (InterruptedException e) {
52.                    e.printStackTrace();
53.                }
54.            }
55.            //灯是绿色的，就生产：
56.            this.setBrand(brand);
57.            try {
58.                Thread.sleep(100);
59.            } catch (InterruptedException e) {
60.                e.printStackTrace();
61.            }
62.            this.setName(name);
63.            //将生产信息做一个打印：
64.            System.out.println("生产者生产了：" + this.getBrand() + "---" + this.getName());
65. 
66.            //生产完以后，灯变色：变成红色：
67.            flag = true;
68.            //告诉消费者赶紧来消费：
69.            //notify();
70.            consumeCondition.signal();
71.        }finally {
72.            lock.unlock();
73.        }
74.    }
75. 
76.    //消费商品：
77.    public void getProduct(){
78.        lock.lock();
79.        try{
80.            if(!flag){//flag == false没有商品，等待生产者生产：
81.                try {
82.                   // wait();
83.                    //消费者等待，消费者线程进入等待队列：
84.                    consumeCondition.await();
85.                } catch (InterruptedException e) {
86.                    e.printStackTrace();
87.                }
88.            }
89. 
90.            //有商品，消费：
91.            System.out.println("消费者消费了：" + this.getBrand() + "---" + this.getName());
92. 
93.            //消费完：灯变色：
94.            flag = false;
95.            //通知生产者生产：
96.            //notify();
97.            produceCondition.signal();
98.        }finally {
99.            lock.unlock();
100.         }
101.     }
102. }
103.  
```

# 第14章_网络编程

## 引入

【1】网络编程：

把分布在不同地理区域的计算机与专门的外部设备用通信线路互连成一个规模大、功能强的网络系统，从而使众多的计算机可以方便地互相传递信息、共享硬件、软件、数据信息等资源。

设备之间在网络中进行数据的传输，发送/接收数据。

![img](https://image.201068.xyz/assets/clip_image1050.jpg)

 

【2】通信两个重要的要素：IP+PORT 

![img](https://image.201068.xyz/assets/clip_image1052.jpg)

域名：www.baidu.com    ------>DNS服务器解析 ----> IP地址 

​     www.mashibing.com 

​     www.sina.com 

​     www.wanda.com 

​     www.bbbb.com 

 

【3】设备之间进行传输的时候，必须遵照一定的规则 ---》通信协议： 

![img](https://image.201068.xyz/assets/clip_image1054.jpg)

 

 

![img](https://image.201068.xyz/assets/clip_image1056.jpg)

【4】TCP协议：可靠的 

建立连接：  三次握手 

![img](https://image.201068.xyz/assets/clip_image1058.jpg)

释放连接：四次挥手 

![img](https://image.201068.xyz/assets/clip_image1060.jpg)

 

【5】UDP协议：不可靠的 

![img](https://image.201068.xyz/assets/clip_image1062.jpg)

 

## InetAddress,InetSocketAddress

前情提要：File  ---》  封装盘符一个文件 

【1】InetAddress  ---》 封装了IP 

```
1.  public class Test01 {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) throws UnknownHostException {
4.          //封装IP：
5.          //InetAddress ia = new InetAddress();不能直接创建对象，因为InetAddress()被default修饰了。
6.          InetAddress ia = InetAddress.getByName("192.168.199.217");
7.          System.out.println(ia);
8.          InetAddress ia2 = InetAddress.getByName("localhost");//localhost指代的是本机的ip地址
9.          System.out.println(ia2);
10.        InetAddress ia3 = InetAddress.getByName("127.0.0.1");//127.0.0.1指代的是本机的ip地址
11.        System.out.println(ia3);
12.        InetAddress ia4 = InetAddress.getByName("LAPTOP-CRIVSRRU");//封装计算机名
13.        System.out.println(ia4);
14.        InetAddress ia5 = InetAddress.getByName("www.mashibing.com");//封装域名
15.        System.out.println(ia5);
16. 
17.        System.out.println(ia5.getHostName());//获取域名
18.        System.out.println(ia5.getHostAddress());//获取ip地址
19.    }
20.}
21. 
```

 

【2】InetSocketAddress  ---》封装了IP，端口号 

```
1.  public class Test02 {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) {
4.          InetSocketAddress isa = new InetSocketAddress("192.168.199.217",8080);
5.          System.out.println(isa);
6.          System.out.println(isa.getHostName());
7.          System.out.println(isa.getPort());
8.   
9.          InetAddress ia = isa.getAddress();
10.        System.out.println(ia.getHostName());
11.        System.out.println(ia.getHostAddress());
12.    }
13.}
```

## 网络通信原理--套接字

![img](https://image.201068.xyz/assets/clip_image1064.jpg)

 

### 基于TCP的网络编程

功能：模拟网站的登录，客户端录入账号密码，然后服务器端进行验证。

```
密码：123456kl;'
加密方式：DES
```

 ![123456kl;'](https://image.201068.xyz/assets/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202023-09-03%20022555.png?imgslim)

#### 功能分解1：单向通信

功能：客户端发送一句话到服务器： 

客户端：

```
1.  public class TestClient {//客户端
2.   
3.      //这是一个main方法，是程序的入口：
4.      public static void main(String[] args) throws IOException {
5.          //1.创建套接字：指定服务器的ip和端口号：
6.          Socket s = new Socket("192.168.199.217",8888);
7.          //2.对于程序员来说，向外发送数据 感受 --》利用输出流：
8.          OutputStream os = s.getOutputStream();
9.          DataOutputStream dos = new DataOutputStream(os);
10.        //利用这个OutputStream就可以向外发送数据了，但是没有直接发送String的方法
11.        //所以我们又在OutputStream外面套了一个处理流：DataOutputStream
12.        dos.writeUTF("你好");
13. 
14.        //3.关闭流  +  关闭网络资源：
15.        dos.close();
16.        os.close();
17.        s.close();
18.    }
19.}
```

服务器：

```
1.  public class TestServer {//服务器
2.   
3.      //这是一个main方法，是程序的入口：
4.      public static void main(String[] args) throws IOException {
5.          //1.创建套接字： 指定服务器的端口号
6.          ServerSocket ss = new ServerSocket(8888);
7.          //2.等着客户端发来的信息：
8.          Socket s = ss.accept();//阻塞方法:等待接收客户端的数据，什么时候接收到数据，什么时候程序继续向下执行。
9.          //accept()返回值为一个Socket，这个Socket其实就是客户端的Socket
10.        //接到这个Socket以后，客户端和服务器才真正产生了连接，才真正可以通信了
11.        //3.感受到的操作流：
12.        InputStream is = s.getInputStream();
13.        DataInputStream dis = new DataInputStream(is);
14. 
15.        //4.读取客户端发来的数据：
16.        String str = dis.readUTF();
17.        System.out.println("客户端发来的数据为："+str);
18.        
19.        //5.关闭流+关闭网络资源：
20.        dis.close();
21.        is.close();
22.        s.close();
23.        ss.close();
24.    }
25.}
```

测试：

（1）先开启客户端还是先开启服务器：先开服务器，再开启客户端 

侧面验证：先开客户端：出错：

![img](https://image.201068.xyz/assets/clip_image1066.jpg)

####  

#### 功能分解2：双向通信

服务器端： 

```
1.  package com.msb.test02;
2.   
3.  import java.io.*;
4.  import java.net.ServerSocket;
5.  import java.net.Socket;
6.   
7.  /**
8.   * @author : msb-zhaoss
9.   */
10.public class TestServer {//服务器
11. 
12.    //这是一个main方法，是程序的入口：
13.    public static void main(String[] args) throws IOException {
14.        //1.创建套接字： 指定服务器的端口号
15.        ServerSocket ss = new ServerSocket(8888);
16.        //2.等着客户端发来的信息：
17.        Socket s = ss.accept();//阻塞方法:等待接收客户端的数据，什么时候接收到数据，什么时候程序继续向下执行。
18.        //accept()返回值为一个Socket，这个Socket其实就是客户端的Socket
19.        //接到这个Socket以后，客户端和服务器才真正产生了连接，才真正可以通信了
20.        //3.感受到的操作流：
21.        InputStream is = s.getInputStream();
22.        DataInputStream dis = new DataInputStream(is);
23. 
24.        //4.读取客户端发来的数据：
25.        String str = dis.readUTF();
26.        System.out.println("客户端发来的数据为："+str);
27. 
28.        //向客户端输出一句话：---》操作流---》输出流
29.        OutputStream os = s.getOutputStream();
30.        DataOutputStream dos = new DataOutputStream(os);
31.        dos.writeUTF("你好，我是服务器端，我接受到你的请求了");
32. 
33. 
34.        //5.关闭流+关闭网络资源：
35.        dos.close();
36.        os.close();
37.        dis.close();
38.        is.close();
39.        s.close();
40.        ss.close();
41.    }
42.}
43. 
```

 

 

 

客户端：

```
1.  package com.msb.test02;
2.   
3.  import java.io.*;
4.  import java.net.Socket;
5.   
6.  /**
7.   * @author : msb-zhaoss
8.   */
9.  public class TestClient {//客户端
10. 
11.    //这是一个main方法，是程序的入口：
12.    public static void main(String[] args) throws IOException {
13.        //1.创建套接字：指定服务器的ip和端口号：
14.        Socket s = new Socket("192.168.199.217",8888);
15.        //2.对于程序员来说，向外发送数据 感受 --》利用输出流：
16.        OutputStream os = s.getOutputStream();
17.        DataOutputStream dos = new DataOutputStream(os);
18.        //利用这个OutputStream就可以向外发送数据了，但是没有直接发送String的方法
19.        //所以我们又在OutputStream外面套了一个处理流：DataOutputStream
20.        dos.writeUTF("你好");
21. 
22.        //接收服务器端的回话--》利用输入流：
23.        InputStream is = s.getInputStream();
24.        DataInputStream dis = new DataInputStream(is);
25.        String str = dis.readUTF();
26.        System.out.println("服务器端对我说："+str);
27. 
28.        //3.关闭流  +  关闭网络资源：
29.        dis.close();
30.        is.close();
31.        dos.close();
32.        os.close();
33.        s.close();
34.    }
35.}
36. 
```

注意：关闭防火墙

#### 功能分解3：对象流传送

封装的User类：

```
1.  package com.msb.test03;
2.   
3.  import java.io.Serializable;
4.   
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class User implements Serializable {
9.      private static final long serialVersionUID = 9050691344308365540L;
10.    private String name;
11.    private String pwd;
12. 
13.    public String getName() {
14.        return name;
15.    }
16. 
17.    public void setName(String name) {
18.        this.name = name;
19.    }
20. 
21.    public String getPwd() {
22.        return pwd;
23.    }
24. 
25.    public void setPwd(String pwd) {
26.        this.pwd = pwd;
27.    }
28. 
29.    public User(String name, String pwd) {
30.        this.name = name;
31.        this.pwd = pwd;
32.    }
33.}
34. 
```

 

客户端：

```
1.  package com.msb.test03;
2.   
3.  import java.io.*;
4.  import java.net.Socket;
5.  import java.util.Scanner;
6.   
7.  /**
8.   * @author : msb-zhaoss
9.   */
10.public class TestClient {//客户端
11. 
12.    //这是一个main方法，是程序的入口：
13.    public static void main(String[] args) throws IOException {
14.        //1.创建套接字：指定服务器的ip和端口号：
15.        Socket s = new Socket("192.168.199.217",8888);
16. 
17.        //录入用户的账号和密码：
18.        Scanner sc = new Scanner(System.in);
19.        System.out.println("请录入您的账号：");
20.        String name = sc.next();
21.        System.out.println("请录入您的密码：");
22.        String pwd = sc.next();
23.        //将账号和密码封装为一个User的对象：
24.        User user = new User(name,pwd);
25. 
26. 
27.        //2.对于程序员来说，向外发送数据 感受 --》利用输出流：
28.        OutputStream os = s.getOutputStream();
29.        ObjectOutputStream oos = new ObjectOutputStream(os);
30.        oos.writeObject(user);
31. 
32. 
33.        //接收服务器端的回话--》利用输入流：
34.        InputStream is = s.getInputStream();
35.        DataInputStream dis = new DataInputStream(is);
36.        boolean b = dis.readBoolean();
37.        if(b){
38.            System.out.println("恭喜，登录成功");
39.        }else{
40.            System.out.println("对不起，登录失败");
41.        }
42. 
43.        //3.关闭流  +  关闭网络资源：
44.        dis.close();
45.        is.close();
46.        oos.close();
47.        os.close();
48.        s.close();
49.    }
50.}
51. 
```

服务器：

```
1.  package com.msb.test03;
2.   
3.  import java.io.*;
4.  import java.net.ServerSocket;
5.  import java.net.Socket;
6.   
7.  /**
8.   * @author : msb-zhaoss
9.   */
10.public class TestServer {//服务器
11. 
12.    //这是一个main方法，是程序的入口：
13.    public static void main(String[] args) throws IOException, ClassNotFoundException {
14.        //1.创建套接字： 指定服务器的端口号
15.        ServerSocket ss = new ServerSocket(8888);
16.        //2.等着客户端发来的信息：
17.        Socket s = ss.accept();//阻塞方法:等待接收客户端的数据，什么时候接收到数据，什么时候程序继续向下执行。
18.        //accept()返回值为一个Socket，这个Socket其实就是客户端的Socket
19.        //接到这个Socket以后，客户端和服务器才真正产生了连接，才真正可以通信了
20.        //3.感受到的操作流：
21.        InputStream is = s.getInputStream();
22.        ObjectInputStream ois = new ObjectInputStream(is);
23. 
24.        //4.读取客户端发来的数据：
25.        User user = (User)(ois.readObject());
26. 
27.        //对对象进行验证：
28.        boolean flag = false;
29.        if(user.getName().equals("娜娜")&&user.getPwd().equals("123123")){
30.            flag = true;
31.        }
32. 
33.        //向客户端输出结果：---》操作流---》输出流
34.        OutputStream os = s.getOutputStream();
35.        DataOutputStream dos = new DataOutputStream(os);
36.        dos.writeBoolean(flag);
37. 
38. 
39.        //5.关闭流+关闭网络资源：
40.        dos.close();
41.        os.close();
42.        ois.close();
43.        is.close();
44.        s.close();
45.        ss.close();
46.    }
47.}
48. 
```

 

#### 功能分解4：加入完整的处理异常方式

服务器端： 

```
1.  package com.msb.test03;
2.   
3.  import java.io.*;
4.  import java.net.ServerSocket;
5.  import java.net.Socket;
6.   
7.  /**
8.   * @author : msb-zhaoss
9.   */
10.public class TestServer {//服务器
11. 
12.    //这是一个main方法，是程序的入口：
13.    public static void main(String[] args) {
14.        //1.创建套接字： 指定服务器的端口号
15.        ServerSocket ss = null;
16.        Socket s = null;
17.        InputStream is = null;
18.        ObjectInputStream ois = null;
19.        OutputStream os = null;
20.        DataOutputStream dos = null;
21.        try {
22.            ss = new ServerSocket(8888);
23.            //2.等着客户端发来的信息：
24.            s = ss.accept();//阻塞方法:等待接收客户端的数据，什么时候接收到数据，什么时候程序继续向下执行。
25.            //accept()返回值为一个Socket，这个Socket其实就是客户端的Socket
26.            //接到这个Socket以后，客户端和服务器才真正产生了连接，才真正可以通信了
27.            //3.感受到的操作流：
28.            is = s.getInputStream();
29.            ois = new ObjectInputStream(is);
30. 
31.            //4.读取客户端发来的数据：
32.            User user = (User)(ois.readObject());
33. 
34.            //对对象进行验证：
35.            boolean flag = false;
36.            if(user.getName().equals("娜娜")&&user.getPwd().equals("123123")){
37.                flag = true;
38.            }
39. 
40.            //向客户端输出结果：---》操作流---》输出流
41.            os = s.getOutputStream();
42.            dos = new DataOutputStream(os);
43.            dos.writeBoolean(flag);
44.        } catch (IOException | ClassNotFoundException e) {
45.            e.printStackTrace();
46.        } finally {
47.            //5.关闭流+关闭网络资源：
48.            try {
49.                if(dos!=null){
50.                    dos.close();
51.                }
52.            } catch (IOException e) {
53.                e.printStackTrace();
54.            }
55.            try {
56.                if(os!=null){
57.                    os.close();
58.                }
59.            } catch (IOException e) {
60.                e.printStackTrace();
61.            }
62.            try {
63.                if(ois!=null){
64.                    ois.close();
65.                }
66.            } catch (IOException e) {
67.                e.printStackTrace();
68.            }
69.            try {
70.                if(is!=null){
71.                    is.close();
72.                }
73.            } catch (IOException e) {
74.                e.printStackTrace();
75.            }
76.            try {
77.                if(s!=null){
78.                    s.close();
79.                }
80.            } catch (IOException e) {
81.                e.printStackTrace();
82.            }
83.            try {
84.                if(ss!=null){
85.                    ss.close();
86.                }
87.            } catch (IOException e) {
88.                e.printStackTrace();
89.            }
90.        }
91.        
92. 
93. 
94.        
95.    }
96.}
97. 
```

客户端：

```
1.  package com.msb.test03;
2.   
3.  import java.io.*;
4.  import java.net.Socket;
5.  import java.util.Scanner;
6.   
7.  /**
8.   * @author : msb-zhaoss
9.   */
10.public class TestClient {//客户端
11. 
12.    //这是一个main方法，是程序的入口：
13.    public static void main(String[] args){
14.        //1.创建套接字：指定服务器的ip和端口号：
15.        Socket s = null;
16.        OutputStream os = null;
17.        ObjectOutputStream oos = null;
18.        InputStream is = null;
19.        DataInputStream dis = null;
20.        try {
21.            s = new Socket("192.168.199.217",8888);
22.            //录入用户的账号和密码：
23.            Scanner sc = new Scanner(System.in);
24.            System.out.println("请录入您的账号：");
25.            String name = sc.next();
26.            System.out.println("请录入您的密码：");
27.            String pwd = sc.next();
28.            //将账号和密码封装为一个User的对象：
29.            User user = new User(name,pwd);
30.            //2.对于程序员来说，向外发送数据 感受 --》利用输出流：
31.            os = s.getOutputStream();
32.            oos = new ObjectOutputStream(os);
33.            oos.writeObject(user);
34.            //接收服务器端的回话--》利用输入流：
35.            is = s.getInputStream();
36.            dis = new DataInputStream(is);
37.            boolean b = dis.readBoolean();
38.            if(b){
39.                System.out.println("恭喜，登录成功");
40.            }else{
41.                System.out.println("对不起，登录失败");
42.            }
43.        } catch (IOException e) {
44.            e.printStackTrace();
45.        } finally{
46.            //3.关闭流  +  关闭网络资源：
47.            try {
48.                if(dis!=null){
49.                    dis.close();
50.                }
51.            } catch (IOException e) {
52.                e.printStackTrace();
53.            }
54.            try {
55.                if(is!=null){
56.                    is.close();
57.                }
58.            } catch (IOException e) {
59.                e.printStackTrace();
60.            }
61.            try {
62.                if(oos!=null){
63.                    oos.close();
64.                }
65.            } catch (IOException e) {
66.                e.printStackTrace();
67.            }
68.            try {
69.                if(os!=null){
70.                    os.close();
71.                }
72.            } catch (IOException e) {
73.                e.printStackTrace();
74.            }
75.            try {
76.                if(s!=null){
77.                    s.close();
78.                }
79.            } catch (IOException e) {
80.                e.printStackTrace();
81.            }
82.        }
83. 
84. 
85. 
86. 
87.    }
88.}
89. 
```

 

 

#### 功能分解5：多线程接收用户请求

遗留问题：服务器针对一个请求服务，之后服务器就关闭了（程序自然结束了）

现在需要解决：服务器必须一直在监听 ，一直开着，等待客户端的请求 

在当前代码中，客户端不用动了

![img](https://image.201068.xyz/assets/clip_image1068.jpg)

 

更改服务器代码：

```
1.  package com.msb.test03;
2.   
3.  import java.io.*;
4.  import java.net.Socket;
5.   
6.  /**
7.   * @author : msb-zhaoss
8.   */
9.  public class ServerThread extends Thread {//线程：专门处理客户端的请求
10.    InputStream is = null;
11.    ObjectInputStream ois = null;
12.    OutputStream os = null;
13.    DataOutputStream dos = null;
14.    Socket s = null;
15.    public ServerThread(Socket s){
16.        this.s = s;
17.    }
18.    @Override
19.    public void run() {
20.        try{
21.            //2.等着客户端发来的信息：
22. 
23.            is = s.getInputStream();
24.            ois = new ObjectInputStream(is);
25. 
26.            //4.读取客户端发来的数据：
27.            User user = (User)(ois.readObject());
28. 
29.            //对对象进行验证：
30.            boolean flag = false;
31.            if(user.getName().equals("娜娜")&&user.getPwd().equals("123123")){
32.                flag = true;
33.            }
34. 
35.            //向客户端输出结果：---》操作流---》输出流
36.            os = s.getOutputStream();
37.            dos = new DataOutputStream(os);
38.            dos.writeBoolean(flag);
39.        }catch (IOException | ClassNotFoundException e) {
40.            e.printStackTrace();
41.        }finally {
42.            try {
43.                if(dos!=null){
44.                    dos.close();
45.                }
46.            } catch (IOException e) {
47.                e.printStackTrace();
48.            }
49.            try {
50.                if(os!=null){
51.                    os.close();
52.                }
53.            } catch (IOException e) {
54.                e.printStackTrace();
55.            }
56.            try {
57.                if(ois!=null){
58.                    ois.close();
59.                }
60.            } catch (IOException e) {
61.                e.printStackTrace();
62.            }
63.            try {
64.                if(is!=null){
65.                    is.close();
66.                }
67.            } catch (IOException e) {
68.                e.printStackTrace();
69.            }
70.        }
71.    }
72.}
73. 
```

 

```
1.  package com.msb.test03;
2.   
3.  import java.io.*;
4.  import java.net.ServerSocket;
5.  import java.net.Socket;
6.   
7.  /**
8.   * @author : msb-zhaoss
9.   */
10.public class TestServer {//服务器
11. 
12.    //这是一个main方法，是程序的入口：
13.    public static void main(String[] args) {
14.        System.out.println("服务器启动了");
15.        //1.创建套接字： 指定服务器的端口号
16.        ServerSocket ss = null;
17.        Socket s = null;
18.        int count = 0;//定义一个计数器，用来计数  客户端的请求
19.        try {
20.            ss = new ServerSocket(8888);
21.            while(true){//加入死循环，服务器一直监听客户端是否发送数据
22.                s = ss.accept();//阻塞方法:等待接收客户端的数据，什么时候接收到数据，什么时候程序继续向下执行。
23.                //每次过来的客户端的请求 靠 线程处理：
24.                new ServerThread(s).start();
25.                count++;
26.                //输入请求的客户端的信息：
27.                System.out.println("当前是第"+count+"个用户访问我们的服务器,对应的用户是："+s.getInetAddress());
28.            }
29.        } catch (IOException  e) {
30.            e.printStackTrace();
31.        }
32.    }
33.}
34. 
```

 

 

### 基于UDP的网络编程

TCP: 

 

客户端：Socket                    

程序感受到的 使用流  ：输出流 

服务器端：  ServerSocket --->Socket   程序感受到的 使用流  ：输入流 

（客户端和服务器端地位不平等。）

 

 

 

UDP:

发送方：DatagramSocket  发送：数据包 DatagramPacket 

接收方：DatagramSocket  接收：数据包 DatagramPacket 

（发送方和接收方的地址是平等的。）

UDP案例： 完成网站的咨询聊天 

 

#### 功能分解1：单向通信

发送方： 

```
1.  package com.msb.test04;
2.   
3.  import java.io.IOException;
4.  import java.net.*;
5.   
6.  /**
7.   * @author : msb-zhaoss
8.   */
9.  public class TestSend {//发送方：
10. 
11.    //这是一个main方法，是程序的入口：
12.    public static void main(String[] args) throws IOException {
13.        System.out.println("学生上线。。。");
14.        //1.准备套接字： 指定发送方的端口号
15.        DatagramSocket ds = new DatagramSocket(8888);
16.        //2.准备数据包
17.        String str = "你好";
18.        byte[] bytes = str.getBytes();
19.        /*
20.        需要四个参数：
21.        1.指的是传送数据转为字节数组
22.        2.字节数组的长度
23.        3.封装接收方的ip
24.        4.指定接收方的端口号
25.         */
26.        DatagramPacket dp = new DatagramPacket(bytes,bytes.length, InetAddress.getByName("localhost"),9999);
27.        //发送：
28.        ds.send(dp);
29. 
30.        //关闭资源
31.        ds.close();
32.    }
33.}
34. 
```

接收方： 

```
1.  package com.msb.test04;
2.   
3.  import java.io.IOException;
4.  import java.net.DatagramPacket;
5.  import java.net.DatagramSocket;
6.  import java.net.SocketException;
7.   
8.  /**
9.   * @author : msb-zhaoss
10. */
11.public class TestReceive {//接收方
12. 
13.    //这是一个main方法，是程序的入口：
14.    public static void main(String[] args) throws IOException {
15.        System.out.println("老师上线了。。");
16.        //1.创建套接字：指定接收方的端口
17.        DatagramSocket ds = new DatagramSocket(9999);
18.        //2.有一个空的数据包，打算用来接收  对方传过来的数据包：
19.        byte[] b = new byte[1024];
20.        DatagramPacket dp = new DatagramPacket(b,b.length);
21.        //3.接收对方的数据包，然后放入我们的dp数据包中填充
22.        ds.receive(dp);//接收完以后 dp里面就填充好内容了
23. 
24.        //4.取出数据：
25.        byte[] data = dp.getData();
26.        String s = new String(data,0,dp.getLength());//dp.getLength()数组包中的有效长度
27.        System.out.println("学生对我说："+s);
28. 
29.        //5.关闭资源：
30.        ds.close();
31. 
32. 
33.    }
34.}
35. 
```

####  

#### 功能分解2：双向通信

发送方： 

```
1.  package com.msb.test04;
2.   
3.  import java.io.IOException;
4.  import java.net.*;
5.  import java.util.Scanner;
6.   
7.  /**
8.   * @author : msb-zhaoss
9.   */
10.public class TestSend {//发送方：
11. 
12.    //这是一个main方法，是程序的入口：
13.    public static void main(String[] args) throws IOException {
14.        System.out.println("学生上线。。。");
15.        //1.准备套接字： 指定发送方的端口号
16.        DatagramSocket ds = new DatagramSocket(8888);
17.        //2.准备数据包
18.        Scanner sc = new Scanner(System.in);
19.        System.out.print("学生：");
20.        String str = sc.next();
21.        byte[] bytes = str.getBytes();
22.        /*
23.        需要四个参数：
24.        1.指的是传送数据转为Z字节数组
25.        2.字节数组的长度
26.        3.封装接收方的ip
27.        4.指定接收方的端口号
28.         */
29.        DatagramPacket dp = new DatagramPacket(bytes,bytes.length, InetAddress.getByName("localhost"),9999);
30.        //发送：
31.        ds.send(dp);
32. 
33.        //接收老师发送回来的信息：
34.        byte[] b = new byte[1024];
35.        DatagramPacket dp2 = new DatagramPacket(b,b.length);
36.        ds.receive(dp2);//接收完以后 dp2里面就填充好内容了
37. 
38.        //取出数据：
39.        byte[] data = dp2.getData();
40.        String s = new String(data,0,dp2.getLength());//dp.getLength()数组包中的有效长度
41.        System.out.println("老师对我说："+s);
42. 
43.        //关闭资源
44.        ds.close();
45.    }
46.}
47. 
```

 

接收方：

```
1.  package com.msb.test04;
2.   
3.  import java.io.IOException;
4.  import java.net.DatagramPacket;
5.  import java.net.DatagramSocket;
6.  import java.net.InetAddress;
7.  import java.net.SocketException;
8.  import java.util.Scanner;
9.   
10./**
11. * @author : msb-zhaoss
12. */
13.public class TestReceive {//接收方
14. 
15.    //这是一个main方法，是程序的入口：
16.    public static void main(String[] args) throws IOException {
17.        System.out.println("老师上线了。。");
18.        //1.创建套接字：指定接收方的端口
19.        DatagramSocket ds = new DatagramSocket(9999);
20.        //2.有一个空的数据包，打算用来接收  对方传过来的数据包：
21.        byte[] b = new byte[1024];
22.        DatagramPacket dp = new DatagramPacket(b,b.length);
23.        //3.接收对方的数据包，然后放入我们的dp数据包中填充
24.        ds.receive(dp);//接收完以后 dp里面就填充好内容了
25. 
26.        //4.取出数据：
27.        byte[] data = dp.getData();
28.        String s = new String(data,0,dp.getLength());//dp.getLength()数组包中的有效长度
29.        System.out.println("学生对我说："+s);
30. 
31.        //老师进行回复：
32.        Scanner sc = new Scanner(System.in);
33.        System.out.print("老师：");
34.        String str = sc.next();
35.        byte[] bytes = str.getBytes();
36.        //封装数据，并且指定学生的ip和端口号
37.        DatagramPacket dp2 = new DatagramPacket(bytes,bytes.length, InetAddress.getByName("localhost"),8888);
38.        //发送：
39.        ds.send(dp2);
40.        //5.关闭资源：
41.        ds.close();
42. 
43. 
44.    }
45.}
46. 
```

 

 

#### 功能分解3：加入完整的处理异常方式

发送方： 

```
1.  package com.msb.test04;
2.   
3.  import java.io.IOException;
4.  import java.net.*;
5.  import java.util.Scanner;
6.   
7.  /**
8.   * @author : msb-zhaoss
9.   */
10.public class TestSend {//发送方：
11. 
12.    //这是一个main方法，是程序的入口：
13.    public static void main(String[] args)  {
14.        System.out.println("学生上线。。。");
15.        //1.准备套接字： 指定发送方的端口号
16.        DatagramSocket ds = null;
17.        try {
18.            ds = new DatagramSocket(8888);
19.            //2.准备数据包
20.            Scanner sc = new Scanner(System.in);
21.            System.out.print("学生：");
22.            String str = sc.next();
23.            byte[] bytes = str.getBytes();
24.        /*
25.        需要四个参数：
26.        1.指的是传送数据转为Z字节数组
27.        2.字节数组的长度
28.        3.封装接收方的ip
29.        4.指定接收方的端口号
30.         */
31.            DatagramPacket dp = new DatagramPacket(bytes,bytes.length, InetAddress.getByName("localhost"),9999);
32.            //发送：
33.            ds.send(dp);
34. 
35.            //接收老师发送回来的信息：
36.            byte[] b = new byte[1024];
37.            DatagramPacket dp2 = new DatagramPacket(b,b.length);
38.            ds.receive(dp2);//接收完以后 dp2里面就填充好内容了
39. 
40.            //取出数据：
41.            byte[] data = dp2.getData();
42.            String s = new String(data,0,dp2.getLength());//dp.getLength()数组包中的有效长度
43.            System.out.println("老师对我说："+s);
44.        } catch (SocketException e) {
45.            e.printStackTrace();
46.        } catch (UnknownHostException e) {
47.            e.printStackTrace();
48.        } catch (IOException e) {
49.            e.printStackTrace();
50.        } finally {
51.            //关闭资源
52.            ds.close();
53.        }
54. 
55. 
56. 
57.    }
58.}
59. 
```

接收方：

```
1.  package com.msb.test04;
2.   
3.  import java.io.IOException;
4.  import java.net.*;
5.  import java.util.Scanner;
6.   
7.  /**
8.   * @author : msb-zhaoss
9.   */
10.public class TestReceive {//接收方
11. 
12.    //这是一个main方法，是程序的入口：
13.    public static void main(String[] args){
14.        System.out.println("老师上线了。。");
15.        //1.创建套接字：指定接收方的端口
16.        DatagramSocket ds = null;
17.        try {
18.            ds = new DatagramSocket(9999);
19.            //2.有一个空的数据包，打算用来接收  对方传过来的数据包：
20.            byte[] b = new byte[1024];
21.            DatagramPacket dp = new DatagramPacket(b,b.length);
22.            //3.接收对方的数据包，然后放入我们的dp数据包中填充
23.            ds.receive(dp);//接收完以后 dp里面就填充好内容了
24. 
25.            //4.取出数据：
26.            byte[] data = dp.getData();
27.            String s = new String(data,0,dp.getLength());//dp.getLength()数组包中的有效长度
28.            System.out.println("学生对我说："+s);
29. 
30.            //老师进行回复：
31.            Scanner sc = new Scanner(System.in);
32.            System.out.print("老师：");
33.            String str = sc.next();
34.            byte[] bytes = str.getBytes();
35.            //封装数据，并且指定学生的ip和端口号
36.            DatagramPacket dp2 = new DatagramPacket(bytes,bytes.length, InetAddress.getByName("localhost"),8888);
37.            //发送：
38.            ds.send(dp2);
39.        } catch (SocketException e) {
40.            e.printStackTrace();
41.        } catch (UnknownHostException e) {
42.            e.printStackTrace();
43.        } catch (IOException e) {
44.            e.printStackTrace();
45.        } finally {
46.            //5.关闭资源：
47.            ds.close();
48.        }
49. 
50. 
51. 
52. 
53.    }
54.}
```

#### 功能分解4：正常通信

发送方： 

```
1.  package com.msb.test04;
2.   
3.  import java.io.IOException;
4.  import java.net.*;
5.  import java.util.Scanner;
6.   
7.  /**
8.   * @author : msb-zhaoss
9.   */
10.public class TestSend {//发送方：
11. 
12.    //这是一个main方法，是程序的入口：
13.    public static void main(String[] args)  {
14.        System.out.println("学生上线。。。");
15.        //1.准备套接字： 指定发送方的端口号
16.        DatagramSocket ds = null;
17.        try {
18.            ds = new DatagramSocket(8888);
19.            while(true){
20.                //2.准备数据包
21.                Scanner sc = new Scanner(System.in);
22.                System.out.print("学生：");
23.                String str = sc.next();
24. 
25.                byte[] bytes = str.getBytes();
26.        /*
27.        需要四个参数：
28.        1.指的是传送数据转为Z字节数组
29.        2.字节数组的长度
30.        3.封装接收方的ip
31.        4.指定接收方的端口号
32.         */
33.                DatagramPacket dp = new DatagramPacket(bytes,bytes.length, InetAddress.getByName("localhost"),9999);
34.                //发送：
35.                ds.send(dp);
36.                if(str.equals("byebye")){
37.                    System.out.println("学生下线。。");
38.                    break;
39.                }
40.                //接收老师发送回来的信息：
41.                byte[] b = new byte[1024];
42.                DatagramPacket dp2 = new DatagramPacket(b,b.length);
43.                ds.receive(dp2);//接收完以后 dp2里面就填充好内容了
44. 
45.                //取出数据：
46.                byte[] data = dp2.getData();
47.                String s = new String(data,0,dp2.getLength());//dp.getLength()数组包中的有效长度
48.                System.out.println("老师对我说："+s);
49.            }
50.        } catch (SocketException e) {
51.            e.printStackTrace();
52.        } catch (UnknownHostException e) {
53.            e.printStackTrace();
54.        } catch (IOException e) {
55.            e.printStackTrace();
56.        } finally {
57.            //关闭资源
58.            ds.close();
59.        }
60. 
61. 
62. 
63.    }
64.}
65. 
```

接收方：

```
1.  package com.msb.test04;
2.   
3.  import java.io.IOException;
4.  import java.net.*;
5.  import java.util.Scanner;
6.   
7.  /**
8.   * @author : msb-zhaoss
9.   */
10.public class TestReceive {//接收方
11. 
12.    //这是一个main方法，是程序的入口：
13.    public static void main(String[] args){
14.        System.out.println("老师上线了。。");
15.        //1.创建套接字：指定接收方的端口
16.        DatagramSocket ds = null;
17.        try {
18.            ds = new DatagramSocket(9999);
19.            while(true){
20.                //2.有一个空的数据包，打算用来接收  对方传过来的数据包：
21.                byte[] b = new byte[1024];
22.                DatagramPacket dp = new DatagramPacket(b,b.length);
23.                //3.接收对方的数据包，然后放入我们的dp数据包中填充
24.                ds.receive(dp);//接收完以后 dp里面就填充好内容了
25. 
26.                //4.取出数据：
27.                byte[] data = dp.getData();
28.                String s = new String(data,0,dp.getLength());//dp.getLength()数组包中的有效长度
29.                System.out.println("学生对我说："+s);
30.                if(s.equals("byebye")){
31.                    System.out.println("学生已经下线了，老师也下线。。。");
32.                    break;
33.                }
34. 
35.                //老师进行回复：
36.                Scanner sc = new Scanner(System.in);
37.                System.out.print("老师：");
38.                String str = sc.next();
39.                byte[] bytes = str.getBytes();
40.                //封装数据，并且指定学生的ip和端口号
41.                DatagramPacket dp2 = new DatagramPacket(bytes,bytes.length, InetAddress.getByName("localhost"),8888);
42.                //发送：
43.                ds.send(dp2);
44.            }
45.        } catch (SocketException e) {
46.            e.printStackTrace();
47.        } catch (UnknownHostException e) {
48.            e.printStackTrace();
49.        } catch (IOException e) {
50.            e.printStackTrace();
51.        } finally {
52.            //5.关闭资源：
53.            ds.close();
54.        }
55. 
56. 
57. 
58. 
59.    }
60.}
61. 
```

 

# 第15章_Junit_注解_枚举

## Junit单元测试

### 引入

【1】软件测试的目的：

软件测试的目的是在规定的条件下对程序进行操作,以发现程序错误,衡量软件质量,并对其是否能满足设计要求进行评估的过程。 

【2】测试分类： 

（1）黑盒测试： 

软件的黑盒测试意味着测试要在软件的接口处进行。这种方法是把测试对象看做一个黑盒子,测试人员完全不考虑程序内部的逻辑结构和内部特性,只依据程序的需求规格说明书,检查程序的功能是否符合它的功能说明。因此黑盒测试又叫功能测试。 

（2）白盒测试：---》Junit属于白盒测试。

软件的白盒测试是对软件的过程性细节做细致的检查。这种方法是把测试对象看做一个打开的盒子,它允许测试人员利用程序内部的逻辑结构及有关信息,设计或选择测试用例,对程序的所有逻辑路径进行测试,通过在不同点检查程序状态,确定实际状态是否与预期的状态一致。因此白盒测试又称为结构测试。 

 

![img](https://image.201068.xyz/assets/clip_image1070.jpg)

 

### 没有Junit的情况下如何测试

在没有使用Junit的时候，缺点：

（1）测试一定走main方法，是程序的入口，main方法的格式必须不能写错。 

（2）要是在同一个main方法中测试的话，那么不需要测试的东西必须注释掉。 

（3）测试逻辑如果分开的话，需要定义多个测试类，麻烦。 

（4）业务逻辑和测试代码，都混淆了。 

代码：

```
1.  package com.msb.calculator;
2.   
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Calculator {
7.      //加法：
8.      public int add(int a,int b){
9.          return a+b;
10.    }
11. 
12.    //减法：
13.    public int sub(int a,int b){
14.        return a-b;
15.    }
16.}
17. 
```

 

```
1.  public class Test {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) {
4.          //测试加法：
5.          Calculator cal = new Calculator();
6.          int result = cal.add(10, 20);
7.          System.out.println(result);
8.          //测试减法：
9.         /* int result = cal.sub(30, 10);
10.        System.out.println(result);*/
11.    }
12.}
```

 

```
1.  public class Test02 {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) {
4.          Calculator cal = new Calculator();
5.          //测试减法：
6.          int result = cal.sub(30, 10);
7.          System.out.println(result);
8.      }
9.  }
10. 
```

 

 

### Junit的使用

【1】一般测试和业务做一个分离，分离为不同的包：

建议起名：公司域名倒着写+test 

以后测试类就单独放在这个包下

【2】测试类的名字：****Test  --->见名知意 

【3】测试方法的定义--》这个方法可以独立运行，不依托于main方法 

建议：

名字：testAdd()   testSub()  见名知意 

参数：无参

返回值：void 

 

【4】测试方法定义完以后，不能直接就独立运行了，必须要在方法前加入一个注解：  @Test 

【5】导入Junit的依赖的环境： 

![img](https://image.201068.xyz/assets/clip_image1072.jpg)

【6】代码： 

```
1.  package com.msb.test;
2.   
3.  import com.msb.calculator.Calculator;
4.  import org.junit.Test;
5.   
6.  /**
7.   * @Auther: msb-zhaoss
8.   */
9.  public class CalculatorTest {
10.    //测试add方法
11.    @Test
12.    public void testAdd(){
13.        System.out.println("测试add方法");
14.        Calculator cal = new Calculator();
15.        int result = cal.add(10, 30);
16.        System.out.println(result);
17.    }
18. 
19.    //测试sub方法
20.    @Test
21.    public void testSub(){
22.        System.out.println("测试sub方法");
23.        Calculator cal = new Calculator();
24.        int result = cal.sub(10, 30);
25.        System.out.println(result);
26.    }
27.}
28. 
```

【7】判定结果： 

绿色：正常结果

红色：出现异常

【8】即使出现绿色效果，也不意味着你的测试就通过了，因为代码中逻辑也可能出现问题，这种情况怎么解决呢？ 

加入断言

```
1.  package com.msb.test;
2.   
3.  import com.msb.calculator.Calculator;
4.  import org.junit.Assert;
5.  import org.junit.Test;
6.   
7.  /**
8.   * @Auther: msb-zhaoss
9.   */
10.public class CalculatorTest {
11.    //测试add方法
12.    @Test
13.    public void testAdd(){
14.        System.out.println("测试add方法");
15.        Calculator cal = new Calculator();
16.        int result = cal.add(10, 30);
17.        //System.out.println(result);--》程序的运行结果可以不关注
18.        //加入断言：预测一下结果，判断一下我预测的结果和 实际的结果是否一致：
19.        Assert.assertEquals(40,result);//第一个参数：预测结果  第二个参数：实际结果
20.    }
21. 
22.    //测试sub方法
23.    @Test
24.    public void testSub(){
25.        System.out.println("测试sub方法");
26.        Calculator cal = new Calculator();
27.        int result = cal.sub(10, 30);
28.        System.out.println(result);
29.    }
30.}
31. 
```

 

 

 

![img](https://image.201068.xyz/assets/clip_image1074.jpg)

 

### @Before_@After

@Before: 

某一个方法中，加入了@Before注解以后，那么这个方法中的功能会在测试方法执行前先执行 

一般会在@Beforer修饰的那个方法中加入：加入一些申请资源的代码：申请数据库资源，申请IO资源，申请网络资源。。。

 

 

@After:

某一个方法中，加入了@After注解以后，那么这个方法中的功能会在测试方法执行后先执行 

一般会在@After修饰的那个方法中加入：加入释放资源的代码：释放数据库资源，释放IO资源，释放网络资源。。。

 

代码： 

```
1.  package com.msb.test;
2.   
3.  import com.msb.calculator.Calculator;
4.  import org.junit.After;
5.  import org.junit.Assert;
6.  import org.junit.Before;
7.  import org.junit.Test;
8.   
9.  /**
10. * @Auther: msb-zhaoss
11. */
12.public class CalculatorTest {
13.    @Before
14.    public void init(){
15.        System.out.println("方法执行开始了。。。");
16.    }
17.    @After
18.    public void close(){
19.        System.out.println("方法执行结束了。。。");
20.    }
21.    //测试add方法
22.    @Test
23.    public void testAdd(){
24.        System.out.println("测试add方法");
25.        Calculator cal = new Calculator();
26.        int result = cal.add(10, 30);
27.        //System.out.println(result);--》程序的运行结果可以不关注
28.        //加入断言：预测一下结果，判断一下我预测的结果和 实际的结果是否一致：
29.        Assert.assertEquals(40,result);//第一个参数：预测结果  第二个参数：实际结果
30.    }
31. 
32.    //测试sub方法
33.    @Test
34.    public void testSub(){
35.        System.out.println("测试sub方法");
36.        Calculator cal = new Calculator();
37.        int result = cal.sub(10, 30);
38.        System.out.println(result);
39.    }
40.}
41. 
```

## 注解

 

### 引入

【1】历史：

JDK5.0 新增 --- 注解（Annotation）,也叫元数据

【2】什么是注解？

注解其实就是代码里的特殊标记，这些标记可以在编译,类加载,运行时被读取,并执行相应的处理。通过使用注解,程序员可以在不改变原有逻辑的情况下，在源文件中嵌入一些补充信息。代码分析工具、开发工具和部署工具可以通过这些补充信息进行验证或者进行部署。

使用注解时要在其前面增加@符号,并把该注解当成一个修饰符使用。用于修饰它支持的程序元素。

【3】注解的重要性：

Annotation 可以像修饰符一样被使用，可用于修饰包，类，构造器,方法，成员变量,参数，局部变量的声明，这些信息被保存在Annotation的"name=value"对中。在JavaSE中，注解的使用目的比较简单，例如标记过时的功能，忽略警告等。在JavaEE/ArIdroid中注解占据了更重要的角色，例如用来配置应用程序的任何切面，代替JavaEE旧版中所遗留的繁冗代码和XML配置等。未来的开发模式都是基于注解的，JPA(java的持久化API)是基于注解的，Spring2.5以. E都是基于注解的，Hibernate3.x以后也是基于注解的，现在的Struts2有一部分也是基于注解的了，注解是一种趋势，一定程度上可以说 ：框架=注解+反射+设计模式。 

 

### 注解的使用实例

 

#### Junit的注解

@Test 

@Before

@After

 

代码：

```
1.   
2.  package com.msb.test;
3.  import com.msb.calculator.Calculator;
4.  import org.junit.After;
5.  import org.junit.Assert;
6.  import org.junit.Before;
7.  import org.junit.Test;
8.  public class CalculatorTest {
9.      @Before
10.    public void init(){
11.        System.out.println("方法执行开始了。。。");
12.    }
13.    @After
14.    public void close(){
15.        System.out.println("方法执行结束了。。。");
16.    }
17.    @Test
18.    public void testAdd(){
19.        System.out.println("测试add方法");
20.        Calculator cal = new Calculator();
21.        int result = cal.add(10, 30);
22.        Assert.assertEquals(40,result);//第一个参数：预测结果  第二个参数：实际结果
23.    }
24.}
25. 
```

 

#### 文档相关的注解

说明注释允许你在程序中嵌入关于程序的信息。你可以使用 javadoc 工具软件来生成信息，并输出到HTML文件中。 

说明注释，使你更加方便的记录你的程序信息。 

文档注解我们一般使用在文档注释中，配合javadoc工具 

javadoc 工具软件识别以下标签： 

![img](https://image.201068.xyz/assets/clip_image1076.jpg)

 

其中注意： 

Ø @param @return和@exception这三个标记都是只用于方法的。 

Ø @param的格式要求: @param 形参名 形参类型 形参说明 

Ø @return的格式要求: @return 返回值类型返回值说明，如果方法的返回值类型是void就不能写 

Ø @exception的格式要求: @exception 异常类型异常说明 

Ø @param和@exception可以并列多个

 

代码：

```
1.  package com.msb.anno;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   * @version : 1.0
6.   */
7.  public class Person {
8.      /**
9.       * 下面是eat方法，实现了XXX功能。
10.     * @param num1 就餐人数
11.     * @param num2 点了几个菜
12.     */
13.    public void eat(int num1,int num2){
14. 
15.    }
16. 
17.    /**
18.     * @param age 年龄
19.     * @return int
20.     * @exception RuntimeException 当年龄过大的时候
21.     * @exception IndexOutOfBoundsException 当年龄过小的时候
22.     * @see Student
23.     */
24.    public int sleep(int age){
25.        new Student();
26.        if(age>100){
27.            throw new RuntimeException();
28.        }
29.        if(age<0){
30.            throw new IndexOutOfBoundsException();
31.        }
32.        return 10;
33.    }
34.}
35. 
```

 

 

IDEA中的javadoc使用： 

![img](https://image.201068.xyz/assets/clip_image1078.jpg)

防止乱码： 

![img](https://image.201068.xyz/assets/clip_image1080.jpg)

 

![img](https://image.201068.xyz/assets/clip_image1082.jpg)

 

 

#### JDK内置的3个注解

@Override:限定重写父类方法，该注解只能用于方法 

| ` `  `1. public class Person {``2.   public void eat(){``3.     System.out.println("父类eat..");``4.   }``5. }``6.  ` |
| ------------------------------------------------------------ |
| ` `  `1. public class Student extends Person {``2.   /*``3.   @Override的作用：限定重写的方法，只要重写方法有问题，就有错误提示。``4.    */``5.   @Override``6.   public void eat(){``7.     System.out.println("子类eat..");``8.   }``9. }` |

@Deprecated:用于表示所修饰的元素(类,方法，构造器，属性等)已过时。通常是因为所修饰的结构危险或存在更好的选择

```
1.  public class Student extends Person {
2.      /*
3.      @Override的作用：限定重写的方法，只要重写方法有问题，就有错误提示。
4.       */
5.      @Override
6.      public void eat(){
7.          System.out.println("子类eat..");
8.      }
9.      /*
10.    在方法前加入@Deprecated，这个方法就会变成一个废弃方法/过期方法/过时方法
11.     */
12. 
13.    @Deprecated
14.    public void study(){
15.        System.out.println("学习。。");
16.    }
17.}
```

![img](https://image.201068.xyz/assets/clip_image1084.jpg)

@SuppressWarnings:抑制编译器警告 

```
1.  public class Test02 {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) {
4.          @SuppressWarnings("unused")
5.          int age = 10;
6.          
7.          int num = 10;
8.          System.out.println(num);
9.          @SuppressWarnings({"unused","rwatypes"})
10.        ArrayList al = new ArrayList();
11.    }
12.}
```

 

 

####  

####  

#### 实现替代配置文件功能的注解

在servlet3.0之前的配置： 

  <?xml version="1.0" encoding="UTF-8"?>   <web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"         version="4.0">     <!--配置Servlet-->     <!--配置Servlet的信息-->     <servlet>         <servlet-name>HelloServlet</servlet-name>         <servlet-class>com.bjsxt.servlet.HelloServlet</servlet-class>     </servlet>     <!--配置Servlet的映射路径-->     <servlet-mapping>         <servlet-name>HelloServlet</servlet-name>         <!--http://localhost:8080/01-hello-servlet/hello-->         <url-pattern>/hello</url-pattern>     </servlet-mapping>   </web-app>   

在servlet3.0之后使用注解：替代配置文件。

 

  ` ``package com.bjsxt.servlet;`` ``import javax.servlet.*;``import java.io.IOException;`` ``@WebServlet("/hello")``public class HelloServlet implements Servlet {``  @Override``  public void init(ServletConfig servletConfig) throws ServletException {`` ``  }`` ``  @Override``  public ServletConfig getServletConfig() {``    return null;``  }`` ``  /**``  * 用于提供服务, 接收请求, 处理响应``  *``  * @param servletRequest``  * @param servletResponse``  * @throws ServletException``  * @throws IOException``  */``  @Override``  public void service(ServletRequest servletRequest, ServletResponse servletResponse) throws ServletException, IOException {``    System.out.println("service方法被调用了...");``  }`` ``  @Override``  public String getServletInfo() {``    return null;``  }`` ``  @Override``  public void destroy() {`` ``  }``}`  

 

### 自定义注解

【1】自定义注解使用很少，一般情况下都是用现成的注解。

【2】如何自定义注解： 

 

![img](https://image.201068.xyz/assets/clip_image1086.jpg)

![img](https://image.201068.xyz/assets/clip_image1088.jpg)

发现定义的注解的声明使用的关键字：[@interface](@interface)，跟接口没有一点关系。 

【3】注解的内部： 

以[@SuppressWarnings](@SuppressWarnings)为例，发现内部： 

![img](https://image.201068.xyz/assets/clip_image1090.jpg)

 

这value是属性还是方法？ 

答案：看上去是无参数方法，实际上理解为一个成员变量，一个属性

无参数方法名字--》成员变量的名字 

无参数方法的返回值--》成员变量的类型 

这个参数叫 配置参数 

 

无参数方法的类型：基本数据类型（八种），String，枚举，注解类型，还可以是以上类型对应的数组。 

 

PS：注意：如果只有一个成员变量的话，名字尽量叫value。 

【4】使用注解： 

（1）使用注解的话，如果你定义了配置参数，就必须给配置参数进行赋值操作： 

```
1.  @MyAnnotation(value={"abc","def","hij"})
2.  public class Person {
3.  }
```

（2）如果只有一个参数，并且这个参数的名字为value的话，那么value=可以省略不写。 

```
1.  @MyAnnotation({"abc","def","hij"})
2.  public class Person {
3.  }
```

（3）如果你给配置参数设置默认的值了，那么使用的时候可以无需传值： 

```
1.  public @interface MyAnnotation2 {
2.      String value() default "abc";
3.  }
```

 

使用：

```
1.  @MyAnnotation2
2.  @MyAnnotation({"abc","def","hij"})
3.  public class Person {
4.  }
```

（4）一个注解的内部是可以不定义配置参数的： 

```
1.  public @interface MyAnnotation3 {
2.  }
```

内部没有定义配置参数的注解--》可以叫做标记 

![img](https://image.201068.xyz/assets/clip_image1092.jpg)

内部定义配置参数的注解--》元数据 

![img](https://image.201068.xyz/assets/clip_image1094.jpg)

 

【5】注解的使用： 

 

现在只学习注解的大致技能点，具体怎么应用  后面慢慢学习。 

 

### 元注解

元注解是用于修饰其它注解的注解。 

举例： 

![img](https://image.201068.xyz/assets/clip_image1096.jpg)

 

JDK5.0提供了四种元注解：Retention, Target, Documented, Inherited 

 

#### Retention

@Retention:用于修饰注解，用于指定修饰的那个注解的生命周期，@Rentention包含一个RetentionPolicy枚举类型的成员变量,使用@Rentention时必须为该value成员变量指定值: 

➢RetentionPolicy.SOURCE:在源文件中有效(即源文件保留),编译器直接丢弃这种策略的注释，在.class文件中不会保留注解信息 

案例： 

![img](https://image.201068.xyz/assets/clip_image1098.jpg)

![img](https://image.201068.xyz/assets/clip_image1100.jpg)

反编译查看字节码文件：发现字节码文件中没有MyAnnotation这个注解： 

![img](https://image.201068.xyz/assets/clip_image1102.jpg)

➢RetentionPolicy.CLASS:在class文件中有效(即class保留)，保留在.class文件中，但是当运行Java程序时，他就不会继续加载了，不会保留在内存中，JVM不会保留注解。如果注解没有加Retention元注解，那么相当于默认的注解就是这种状态。 

案例： 

![img](https://image.201068.xyz/assets/clip_image1104.jpg)

![img](https://image.201068.xyz/assets/clip_image1106.jpg)

反编译看字节码文件，字节码文件中带有MyAnnotation注解： 

![img](https://image.201068.xyz/assets/clip_image1108.jpg)

➢RetentionPolicy.RUNTIME:在运行时有效(即运行时保留),当运行 Java程序时，JVM会保留注释，加载在内存中了，那么程序可以通过反射获取该注释。 

#### Target

用于修饰注解的注解，用于指定被修饰的注解能用于修饰哪些程序元素。@Target也包含一个名为value的成员变量。 

案例： 

```
1.  @Target({TYPE,CONSTRUCTOR,METHOD})
2.  public @interface MyAnnotation4 {
3.  }
```

使用：

![img](https://image.201068.xyz/assets/clip_image1110.jpg)

 

#### Documented（很少）

用于指定被该元注解修饰的注解类将被javadoc工具提取成文档。默认情况下，javadoc是 不包括注解的，但是加上了这个注解生成的文档中就会带着注解了

案例： 

如果：Documented注解修饰了Deprecated注解， 

![img](https://image.201068.xyz/assets/clip_image1112.jpg)

那么Deprecated注解就会在javadoc提取的时候，提取到API中： 

![img](https://image.201068.xyz/assets/clip_image1114.jpg)

 

#### Inherited（极少）

被它修饰的Annotation将具有继承性。如果某个类使用了被

@Inherited修饰的Annotation,则其子类将自动具有该注解。

 

案例： 

注解：如果MyAnno注解使用了@Inherited之后，就具备了继承性，那么相当于子类Student也使用了这个MyAnno 

![img](https://image.201068.xyz/assets/clip_image1116.jpg)

父类：
 ![img](https://image.201068.xyz/assets/clip_image1118.jpg)

子类： 

![img](https://image.201068.xyz/assets/clip_image1120.jpg)

 

## 枚举

 

### 引入

【1】数学：枚举法：

1<x<4

2<y<5

求x+y=6 

枚举法：一枚一枚的列举出来。前提：有限，确定

 

【2】在java中，类的对象是有限个，确定的。这个类我们可以定义为枚举类。 

举例：

星期：一二三四五六日  

性别：男女

季节：春夏秋冬

 

【3】自定义枚举类：（JDK1.5之前自定义枚举类） 

```
1.  package com.msb.enum01;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   * 定义枚举类：季节
6.   */
7.  public class Season {
8.      //属性：
9.      private final String seasonName ;//季节名字
10.    private final String seasonDesc ;//季节描述
11.    //利用构造器对属性进行赋值操作：
12.    //构造器私有化，外界不能调用这个构造器，只能Season内部自己调用
13.    private Season(String seasonName,String seasonDesc){
14.        this.seasonName = seasonName;
15.        this.seasonDesc = seasonDesc;
16.    }
17. 
18.    //提供枚举类的有限的  确定的对象：
19.    public static final Season SPRING = new Season("春天","春暖花开");
20.    public static final Season SUMMER = new Season("夏天","烈日炎炎");
21.    public static final Season AUTUMN = new Season("秋天","硕果累累");
22.    public static final Season WINTER = new Season("冬天","冰天雪地");
23. 
24.    //额外因素：
25. 
26.    public String getSeasonName() {
27.        return seasonName;
28.    }
29. 
30.    public String getSeasonDesc() {
31.        return seasonDesc;
32.    }
33. 
34.    //toString();
35. 
36.    @Override
37.    public String toString() {
38.        return "Season{" +
39.                "seasonName='" + seasonName + '\'' +
40.                ", seasonDesc='" + seasonDesc + '\'' +
41.                '}';
42.    }
43.}
44. 
```

测试类： 

```
1.  public class TestSeason {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) {
4.          Season summer = Season.SUMMER;
5.          System.out.println(summer/*.toString()*/);
6.          System.out.println(summer.getSeasonName());
7.      }
8.  }
```

### JDK1_5之后使用enum关键字来创建枚举类

JDK1.5以后使用enum关键字创建枚举类： 

![img](https://image.201068.xyz/assets/clip_image1122.jpg)

变为下面的枚举类：

```
1.  package com.msb.enum02;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   * 定义枚举类：季节
6.   */
7.  public enum Season {
8.      //提供枚举类的有限的  确定的对象：--->enum枚举类要求对象（常量）必须放在最开始位置
9.      //多个对象之间用，进行连接，最后一个对象后面用;结束
10.    SPRING("春天","春暖花开"),
11.    SUMMER("夏天","烈日炎炎"),
12.    AUTUMN("秋天","硕果累累"),
13.    WINTER("冬天","冰天雪地");
14.    //属性：
15.    private final String seasonName ;//季节名字
16.    private final String seasonDesc ;//季节描述
17.    //利用构造器对属性进行赋值操作：
18.    //构造器私有化，外界不能调用这个构造器，只能Season内部自己调用
19.    private Season(String seasonName, String seasonDesc){
20.        this.seasonName = seasonName;
21.        this.seasonDesc = seasonDesc;
22.    }
23. 
24. 
25. 
26.    //额外因素：
27. 
28.    public String getSeasonName() {
29.        return seasonName;
30.    }
31. 
32.    public String getSeasonDesc() {
33.        return seasonDesc;
34.    }
35. 
36.    //toString();
37. 
38.    @Override
39.    public String toString() {
40.        return "Season{" +
41.                "seasonName='" + seasonName + '\'' +
42.                ", seasonDesc='" + seasonDesc + '\'' +
43.                '}';
44.    }
45.}
46. 
```

使用枚举类： 

```
1.  public class TestSeason {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) {
4.          Season winter = Season.WINTER;
5.          System.out.println(winter);
6.          //enum关键字对应的枚举类的上层父类是 ：java.lang.Enum
7.          //但是我们自定义的枚举类的上层父类：Object
8.          System.out.println(Season.class.getSuperclass().getName());//java.lang.Enum
9.      }
10.}
11. 
```

在源码中经常看到别人定义的枚举类形态：

```
1.  public enum Season {
2.      SPRING,
3.      SUMMER,
4.      AUTUMN,
5.      WINTER;
6.  }
7.   
```

为什么这么简单：因为这个枚举类底层没有属性，属性，构造器，toString，get方法都删掉不写了，然后案例来说应该 

写为：SPRING()  现在连（）可以省略 就变成  SPRING 

看到的形态就剩：常量名（对象名）

 

案例：

Thread中的枚举类：State

```
1.  public enum State {
2.          /**
3.           * Thread state for a thread which has not yet started.
4.           */
5.          NEW,
6.   
7.          /**
8.           * Thread state for a runnable thread.  A thread in the runnable
9.           * state is executing in the Java virtual machine but it may
10.         * be waiting for other resources from the operating system
11.         * such as processor.
12.         */
13.        RUNNABLE,
14. 
15.        /**
16.         * Thread state for a thread blocked waiting for a monitor lock.
17.         * A thread in the blocked state is waiting for a monitor lock
18.         * to enter a synchronized block/method or
19.         * reenter a synchronized block/method after calling
20.         * {@link Object#wait() Object.wait}.
21.         */
22.        BLOCKED,
23. 
24.        /**
25.         * Thread state for a waiting thread.
26.         * A thread is in the waiting state due to calling one of the
27.         * following methods:
28.         * <ul>
29.         *   <li>{@link Object#wait() Object.wait} with no timeout</li>
30.         *   <li>{@link #join() Thread.join} with no timeout</li>
31.         *   <li>{@link LockSupport#park() LockSupport.park}</li>
32.         * </ul>
33.         *
34.         * <p>A thread in the waiting state is waiting for another thread to
35.         * perform a particular action.
36.         *
37.         * For example, a thread that has called <tt>Object.wait()</tt>
38.         * on an object is waiting for another thread to call
39.         * <tt>Object.notify()</tt> or <tt>Object.notifyAll()</tt> on
40.         * that object. A thread that has called <tt>Thread.join()</tt>
41.         * is waiting for a specified thread to terminate.
42.         */
43.        WAITING,
44. 
45.        /**
46.         * Thread state for a waiting thread with a specified waiting time.
47.         * A thread is in the timed waiting state due to calling one of
48.         * the following methods with a specified positive waiting time:
49.         * <ul>
50.         *   <li>{@link #sleep Thread.sleep}</li>
51.         *   <li>{@link Object#wait(long) Object.wait} with timeout</li>
52.         *   <li>{@link #join(long) Thread.join} with timeout</li>
53.         *   <li>{@link LockSupport#parkNanos LockSupport.parkNanos}</li>
54.         *   <li>{@link LockSupport#parkUntil LockSupport.parkUntil}</li>
55.         * </ul>
56.         */
57.        TIMED_WAITING,
58. 
59.        /**
60.         * Thread state for a terminated thread.
61.         * The thread has completed execution.
62.         */
63.        TERMINATED;
64.    }
```

###  

### Enum类的常用方法

```
1.  package com.msb.enum03;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class TestSeason {
7.      //这是一个main方法，是程序的入口：
8.      public static void main(String[] args) {
9.          //用enum关键字创建的Season枚举类上面的父类是：java.lang.Enum,常用方法子类Season可以直接拿过来使用：
10.        //toString();--->获取对象的名字
11.        Season autumn = Season.AUTUMN;
12.        System.out.println(autumn/*.toString()*/);//AUTUMN
13. 
14.        System.out.println("--------------------");
15.        //values:返回枚举类对象的数组
16.        Season[] values = Season.values();
17.        for(Season s:values){
18.            System.out.println(s/*.toString()*/);
19.        }
20. 
21.        System.out.println("--------------------");
22.        //valueOf：通过对象名字获取这个枚举对象
23.        //注意：对象的名字必须传正确，否则抛出异常
24.        Season autumn1 = Season.valueOf("AUTUMN");
25.        System.out.println(autumn1);
26.    }
27.}
28. 
```

 

### 枚举类实现接口

定义一个接口： 

```
1.  public interface TestInterface {
2.      void show();
3.  }
```

枚举类实现接口，并且重写show方法： 

```
1.  public enum Season implements TestInterface {
2.      SPRING,
3.      SUMMER,
4.      AUTUMN,
5.      WINTER;
6.   
7.      @Override
8.      public void show() {
9.          System.out.println("这是Season....");
10.    }
11.}
12. 
```

测试类： 

```
1.  public class Test {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) {
4.          Season autumn = Season.AUTUMN;
5.          autumn.show();
6.          Season summer = Season.SUMMER;
7.          summer.show();
8.      }
9.  }
```

上面发现所有的枚举对象，调用这个show方法的时候走的都是同一个方法，结果都一样： 

![img](https://image.201068.xyz/assets/clip_image1124.jpg)

但是现在我想要：不同的对象  调用的show方法也不同： 

```
1.  package com.msb.enum04;
2.   
3.   
4.  import java.sql.SQLOutput;
5.   
6.  public enum Season implements TestInterface {
7.      SPRING{
8.          @Override
9.          public void show() {
10.            System.out.println("这是春天。。。");
11.        }
12.    },
13.    SUMMER{
14.        @Override
15.        public void show() {
16.            System.out.println("这是夏天。。");
17.        }
18.    },
19.    AUTUMN{
20.        @Override
21.        public void show() {
22.            System.out.println("这是秋天");
23.        }
24.    },
25.    WINTER{
26.        @Override
27.        public void show() {
28.            System.out.println("这是冬天");
29.        }
30.    };
31. 
32.    /*@Override
33.    public void show() {
34.        System.out.println("这是Season....");
35.    }*/
36.}
37. 
```

测试类：

```
1.  public class Test {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) {
4.          Season autumn = Season.AUTUMN;
5.          autumn.show();
6.          Season summer = Season.SUMMER;
7.          summer.show();
8.      }
9.  }
```

![img](https://image.201068.xyz/assets/clip_image1126.jpg)

 

 

 

### 实际应用

```
1.  package com.msb.enum05;
2.   
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class Person {
7.      //属性：
8.      private int age;
9.      private String name;
10.    private Gender sex;
11. 
12.    public int getAge() {
13.        return age;
14.    }
15. 
16.    public void setAge(int age) {
17.        this.age = age;
18.    }
19. 
20.    public String getName() {
21.        return name;
22.    }
23. 
24.    public void setName(String name) {
25.        this.name = name;
26.    }
27. 
28.    public Gender getSex() {
29.        return sex;
30.    }
31. 
32.    public void setSex(Gender sex) {
33.        this.sex = sex;
34.    }
35. 
36.    @Override
37.    public String toString() {
38.        return "Person{" +
39.                "age=" + age +
40.                ", name='" + name + '\'' +
41.                ", sex='" + sex + '\'' +
42.                '}';
43.    }
44.}
45. 
```

 

```
1.  public enum Gender {
2.      男,
3.      女;
4.  }
5.   
```

 

```
1.  public class Test {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) {
4.          Person p = new Person();
5.          p.setAge(19);
6.          p.setName("lili");
7.          p.setSex(Gender.男);//传入枚举类Gender的对象：-->在入口处对参数进行了限制
8.          System.out.println(p);
9.      }
10.}
11. 
```

 

还可以通过枚举结合switch处理： 

```
1.  public class Test02 {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) {
4.          Gender sex = Gender.男;
5.          //switch后面的（）中可以传入枚举类型
6.          //switch后面的（）:int,short,byte,char,String ,枚举
7.          switch (sex){
8.              case 女:
9.                  System.out.println("是个女孩");
10.                break;
11.            case 男:
12.                System.out.println("是个男孩");
13.                break;
14.        }
15.    }
16.}
```

 

 

 

# 第16章_反射

 

## 通过案例体会反射的好处

案例：美团外卖 --->付款  ---》要么用微信支付 要么用支付宝支付  

```
1.  package com.zhaoss.test01;
2.  //接口的制定方：美团外卖
3.  public interface Mtwm {
4.      //在线支付功能：
5.      void payOnline();
6.  }
7.   
```

 

```
1.  public class WeChat implements Mtwm{
2.      @Override
3.      public void payOnline() {
4.          //具体实现微信支付的功能：
5.          System.out.println("我已经点了外卖，正在使用微信支付");
6.      }
7.  }
```

 

```
1.  public class AliPay implements Mtwm {
2.      @Override
3.      public void payOnline() {
4.          //具体的支付宝支付：
5.          System.out.println("我已经点了外卖，我正在使用支付宝进行支付");
6.      }
7.  }
```

 

```
1.  public class BankCard implements Mtwm{
2.      @Override
3.      public void payOnline() {
4.          System.out.println("我已经定了外卖，我正在用招商银行信用卡支付");
5.      }
6.  }
```

测试类：

```
1.  package com.zhaoss.test01;
2.   
3.  public class Test {
4.      public static void main(String[] args) {
5.          //定义一个字符串，用来模拟前台的支付方式：
6.          String str = "微信";
7.          if("微信".equals(str)){//str.equals("微信")---？避免空指针异常
8.              //微信支付：
9.              //new WeChat().payOnline();
10.            pay(new WeChat());
11.        }
12. 
13.        if("支付宝".equals(str)){
14.            //支付宝支付：
15.            //new AliPay().payOnline();
16.            pay(new AliPay());
17.        }
18. 
19.        if("招商银行".equals(str)){
20.            pay(new BankCard());
21.        }
22.    }
23.    //微信支付
24.    public static void pay(WeChat wc){
25.        wc.payOnline();
26.    }
27.    //支付宝支付
28.    public static void pay(AliPay ap){
29.        ap.payOnline();
30.    }
31. 
32.    //招商银行支付
33.    public static void pay(BankCard bc){
34.        bc.payOnline();
35.    }
36.}
37. 
```

为了提高代码的扩展性---》面向对象特性：多态： 

```
1.  package com.zhaoss.test01;
2.   
3.  public class Test {
4.      public static void main(String[] args) {
5.          //定义一个字符串，用来模拟前台的支付方式：
6.          String str = "微信";
7.          if("微信".equals(str)){//str.equals("微信")---？避免空指针异常
8.              //微信支付：
9.              pay(new WeChat());
10.        }
11. 
12.        if("支付宝".equals(str)){
13.            //支付宝支付：
14.            pay(new AliPay());
15.        }
16. 
17.        if("招商银行".equals(str)){
18.            pay(new BankCard());
19.        }
20.    }
21.    //方法形参是接口，具体传入的是接口的实现类的对象---》多态的一种形式
22.    public static void pay(Mtwm m){
23.        m.payOnline();
24.    }
25. 
26. 
27.}
28. 
```

多态确实可以提高代码的扩展性，但是：扩展性没有达到最好。

怎么没有达到最好：上面的分支，还是需要手动的删除或者添加。

解决办法：反射机制

利用反射实现上述功能：

```
1.  package com.zhaoss.test01;
2.   
3.  import java.lang.reflect.InvocationTargetException;
4.  import java.lang.reflect.Method;
5.   
6.  public class Demo {
7.      public static void main(String[] args) throws Exception {
8.          //定义一个字符串，用来模拟前台的支付方式：
9.          String str = "com.zhaoss.test01.AliPay";  //字符串：实际上：就是微信类的全限定路径
10. 
11.        //下面的代码就是利用反射：
12.        Class  cls = Class.forName(str);//cls-->Class类具体的对象--》AliPay字节码信息
13.        Object o = cls.newInstance();
14.        Method method = cls.getMethod("payOnline");
15.        method.invoke(o);
16.    }
17.}
18. 
```

 

 

 

## 通过概念再体会反射

JAVA反射机制是在运行状态中，对于任意一个类，都能够知道这个类的所有属性和方法；对于任意一个对象， 

都能够调用它的任意方法和属性；这种动态获取信息以及动态调用对象方法的功能称为java语言的反射机制。 

 

在编译后产生字节码文件的时候，类加载器子系统通过二进制字节流，负责从文件系统加载class文件。 

在执行程序（java.exe）时候，将字节码文件读入JVM中--->这个过程叫做类的加载。然后在内存中对应创建一个java.lang.Class对象-->这个对象会被放入字节码信息中,这个Class对象,就对应加载那个字节码信息,这个对象将被作为程序访问方法区中的这个类的各种数据的外部接口。

所以：我们可以通过这个对象看到类的结构，这个对象就好像是一面镜子，透过镜子看到类的各种信息，我们形象的称之为反射

这种“看透”class的能力（the ability of the program to examine itself）被称为introspection（内省、内观、反省）。Reflection和introspection是常被并提的两个术语。 

 

说明：在运行期间，如果我们要产生某个类的对象，Java虚拟机(JVM)会检查该类型的Class对象是否已被加载。

如果没有被加载，JVM会根据类的名称找到.class文件并加载它。一旦某个类型的Class对象已被加载到内存，就可以用它来产生该类型的所有对象。 

补充: 

动态语膏vs静态语言 

1、动态语言 

是一类在运行时可以改变其结构的语言:例如新的函数、对象、甚至代码可以 

被引进，已有的函数可以被删除或是其他结构上的变化。通俗点说就是在运

行时代码可以根据某些条件改变自身结构。

主要动态语言: Object-C、 C#、JavaScript、 PHP、 Python、 Erlang 。 

2、静态语言 

与动态语言相对应的，运行时结构不可变的语言就是静态语言。如Java、C、 

C++。 

所以Java不是动态语言，但Java可以称之为“准动态语言”。即Java有一定的动 

态性，我们可以利用反射机制、字节码操作获得类似动态语言的特性。

Java的动态性让编程的时候更加灵活! 

Class类的理解

![img](https://image.201068.xyz/assets/clip_image1128.jpg)

 

## 提供丰富的类

```
1.  package com.zhaoss.test02;
2.  //作为一个父类
3.  public class Person {
4.      //属性
5.      private int age;
6.      public String name;
7.   
8.      //方法
9.      private void eat(){
10.        System.out.println("Person---eat");
11.    }
12.    public void sleep(){
13.        System.out.println("Person---sleep");
14.    }
15.}
16. 
```

 

```
1.  package com.zhaoss.test02;
2.  //Student作为子类
3.  public class Student extends Person {
4.      //属性：
5.      private int sno;//学号
6.      double height;//身高
7.      protected double weight;//体重
8.      public double score;//成绩
9.   
10.    //方法：
11.    public String showInfo(){
12.        return "我是一名三好学生";
13.    }
14.    private void work(){
15.        System.out.println("我以后会找工作--》成为码农  程序员 程序猿  程序媛");
16.    }
17. 
18.    //构造器
19.    public Student(){
20.        System.out.println("空参构造器");
21.    }
22.    private Student(int sno){
23.        this.sno = sno;
24.    }
25.    Student(int sno,double weight){
26.        this.sno = sno;
27.        this.weight = weight;
28.    }
29.}
30.  
```

## 获取字节码信息的四种形式

```
1.  package com.zhaoss.test02;
2.   
3.  public class Test {
4.      public static void main(String[] args) throws ClassNotFoundException {
5.          //案例：以Person的字节码信息为案例
6.          //方式1：通过getClass()方法获取
7.          Person p = new Person();
8.          Class c1 = p.getClass();
9.          System.out.println(c1);
10. 
11.        //方式2：通过内置class属性：
12.        Class c2 = Person.class;
13.        System.out.println(c2);
14. 
15.        System.out.println(c1==c2);
16. 
17.        //注意：方式1和方式2  不常用
18. 
19.        //方式3：--》用的最多：调用Class类提供的静态方法forName
20.        Class c3 = Class.forName("com.zhaoss.test02.Person");
21.        //方式4：利用类的加载器(了解技能点)
22.        ClassLoader loader = Test.class.getClassLoader();
23.        Class c4 = loader.loadClass("com.zhaoss.test02.Person");
24.    }
25.}
26. 
```

## 可以作为Class类的实例的种类

Class类的具体的实例： 

（1）类：外部类，内部类 

（2）接口 

（3）注解 

（4）数组 

（5）基本数据类型 

（6）void 

 

验证： 

```
1.  package com.zhaoss.test02;
2.   
3.  public class Demo {
4.      public static void main(String[] args) {
5.          /*
6.          Class类的具体的实例：
7.          （1）类：外部类，内部类
8.          （2）接口
9.          （3）注解
10.        （4）数组
11.        （5）基本数据类型
12.        （6）void
13.         */
14.        Class c1 = Person.class;
15.        Class c2 = Comparable.class;
16.        Class c3 = Override.class;
17. 
18.        int[] arr1 = {1,2,3};
19.        Class c4 = arr1.getClass();
20.        int[] arr2 = {5,6,7};
21.        Class c5 = arr2.getClass();
22.        System.out.println(c4==c5);//结果：true .同一个维度，同一个元素类型,得到的字节码就是同一个
23.        
24.        Class c6 = int.class;
25.        Class c7 = void.class;
26.    }
27.}
28. 
```

 

## 获取运行时类的完整结构

### 补充完善上面提供的丰富的类

```
1.  //作为一个父类
2.  public class Person implements Serializable {
3.      //属性
4.      private int age;
5.      public String name;
6.   
7.      //方法
8.      private void eat(){
9.          System.out.println("Person---eat");
10.    }
11.    public void sleep(){
12.        System.out.println("Person---sleep");
13.    }
14.}
```

 

```
1.  package com.zhaoss.test03;
2.   
3.  //Student作为子类
4.  @MyAnnotation(value="hello")
5.  public class Student extends Person implements MyInterface{
6.      //属性：
7.      private int sno;//学号
8.      double height;//身高
9.      protected double weight;//体重
10.    public double score;//成绩
11. 
12.    //方法：
13.    @MyAnnotation(value="himethod")
14.    public String showInfo(){
15.        return "我是一名三好学生";
16.    }
17.    public String showInfo(int a,int b){
18.        return "重载方法====我是一名三好学生";
19.    }
20.    private void work(){
21.        System.out.println("我以后会找工作--》成为码农  程序员 程序猿  程序媛");
22.    }
23.    void happy(){
24.        System.out.println("做人最重要的就是开心每一天");
25.    }
26.    protected int getSno(){
27.        return sno;
28.    }
29. 
30.    //构造器
31.    public Student(){
32.        System.out.println("空参构造器");
33.    }
34.    private Student(int sno){
35.        this.sno = sno;
36.    }
37.    Student(int sno,double weight){
38.        this.sno = sno;
39.        this.weight = weight;
40.    }
41.    protected Student(int sno,double height,double weight){
42.        this.sno = sno;
43.    }
44. 
45.    @Override
46.    @MyAnnotation(value="hellomyMethod")
47.    public void myMethod() {
48.        System.out.println("我重写了myMethod方法。。");
49.    }
50. 
51.    @Override
52.    public String toString() {
53.        return "Student{" +
54.                "sno=" + sno +
55.                ", height=" + height +
56.                ", weight=" + weight +
57.                ", score=" + score +
58.                '}';
59.    }
60.}
61. 
```

 

```
1.  package com.zhaoss.test03;
2.   
3.  import java.lang.annotation.Retention;
4.  import java.lang.annotation.RetentionPolicy;
5.  import java.lang.annotation.Target;
6.   
7.  import static java.lang.annotation.ElementType.*;
8.  import static java.lang.annotation.ElementType.LOCAL_VARIABLE;
9.  /*
10.@Target:定义当前注解能够修饰程序中的哪些元素
11.@Retention:定义注解的声明周期
12. */
13.@Target({TYPE, FIELD, METHOD, PARAMETER, CONSTRUCTOR, LOCAL_VARIABLE})
14.@Retention(RetentionPolicy.RUNTIME)
15.public @interface MyAnnotation {
16.    String value();//属性
17.}
18. 
19. 
20. 
```

 

```
1.  package com.zhaoss.test03;
2.   
3.  public interface MyInterface {//自定义的接口
4.      //随便定义一个抽象方法：
5.      void myMethod();
6.  }
7.   
```

### 获取构造器和创建对象

```
1.  package com.zhaoss.test03;
2.   
3.  import java.lang.reflect.Constructor;
4.  import java.lang.reflect.InvocationTargetException;
5.   
6.  public class Test01 {
7.      public static void main(String[] args) throws NoSuchMethodException, IllegalAccessException, InvocationTargetException, InstantiationException {
8.          //获取字节码信息：
9.          Class cls = Student.class;
10. 
11.        //通过字节码信息可以获取构造器：
12.        //getConstructors只能获取当前运行时类的被public修饰的构造器
13.        Constructor[] c1 = cls.getConstructors();
14.        for(Constructor c:c1){
15.            System.out.println(c);
16.        }
17. 
18.        System.out.println("-------------------");
19.        //getDeclaredConstructors:获取运行时类的全部修饰符的构造器
20.        Constructor[] c2 = cls.getDeclaredConstructors();
21.        for(Constructor c:c2){
22.            System.out.println(c);
23.        }
24.        System.out.println("-------------------");
25.        //获取指定的构造器：
26.        //得到空构造器
27.        Constructor con1 = cls.getConstructor();
28.        System.out.println(con1);
29. 
30.        //得到两个参数的有参构造器：
31.        Constructor con2 = cls.getConstructor(double.class, double.class);
32.        System.out.println(con2);
33. 
34.        //得到一个参数的有参构造器：并且是private修饰的
35.        Constructor con3 = cls.getDeclaredConstructor(int.class);
36.        System.out.println(con3);
37. 
38.        //有了构造器以后我就可以创建对象：
39.        Object o1 = con1.newInstance();
40.        System.out.println(o1);
41. 
42.        Object o2 = con2.newInstance(180.5, 170.6);
43.        System.out.println(o2);
44.    }
45.}
46. 
```

### 获取属性和对属性进行赋值

```
1.  package com.zhaoss.test03;
2.   
3.  import java.lang.reflect.Field;
4.  import java.lang.reflect.Modifier;
5.   
6.  public class Test02 {
7.      public static void main(String[] args) throws NoSuchFieldException, IllegalAccessException, InstantiationException {
8.          //获取运行时类的字节码信息：
9.          Class cls = Student.class;
10.        //获取属性：
11.        //getFields：获取运行时类和父类中被public修饰的属性
12.        Field[] fields = cls.getFields();
13.        for(Field f:fields){
14.            System.out.println(f);
15.        }
16.        System.out.println("---------------------");
17.        //getDeclaredFields：获取运行时类中的所有属性
18.        Field[] declaredFields = cls.getDeclaredFields();
19.        for(Field f:declaredFields){
20.            System.out.println(f);
21.        }
22.        System.out.println("---------------------");
23.        //获取指定的属性：
24.        Field score = cls.getField("score");
25.        System.out.println(score);
26.        Field sno = cls.getDeclaredField("sno");
27.        System.out.println(sno);
28. 
29.        System.out.println("---------------------");
30.        //属性的具体结构：
31.        //获取修饰符
32.        /*int modifiers = sno.getModifiers();
33.        System.out.println(modifiers);
34.        System.out.println(Modifier.toString(modifiers));*/
35.        System.out.println(Modifier.toString(sno.getModifiers()));
36.        //获取属性的数据类型：
37.        Class clazz = sno.getType();
38.        System.out.println(clazz.getName());
39. 
40.        //获取属性的名字：
41.        String name = sno.getName();
42.        System.out.println(name);
43.        System.out.println("-------------------------------");
44.        //给属性赋值：(给属性设置值，必须要有对象)
45.        Field sco = cls.getField("score");
46.        Object obj = cls.newInstance();
47.        sco.set(obj,98);//给obj这个对象的score属性设置具体的值，这个值为98
48.        System.out.println(obj);
49.    }
50.}
51. 
```

### 获取方法和调用方法

```
1.  package com.zhaoss.test03;
2.   
3.  import java.lang.annotation.Annotation;
4.  import java.lang.reflect.InvocationTargetException;
5.  import java.lang.reflect.Method;
6.  import java.lang.reflect.Modifier;
7.   
8.  public class Test03 {
9.      public static void main(String[] args) throws NoSuchMethodException, IllegalAccessException, InstantiationException, InvocationTargetException {
10.        //获取字节码信息：
11.        Class cls = Student.class;
12.        //获取方法：
13.        //getMethods:获取运行时类的方法还有所有父类中的方法（被public修饰）
14.        Method[] methods = cls.getMethods();
15.        for(Method m:methods){
16.            System.out.println(m);
17.        }
18.        System.out.println("-----------------------");
19.        //getDeclaredMethods:获取运行时类中的所有方法：
20.        Method[] declaredMethods = cls.getDeclaredMethods();
21.        for(Method m:declaredMethods){
22.            System.out.println(m);
23.        }
24.        System.out.println("-----------------------");
25.        //获取指定的方法：
26.        Method showInfo1 = cls.getMethod("showInfo");
27.        System.out.println(showInfo1);
28.        Method showInfo2 = cls.getMethod("showInfo", int.class, int.class);
29.        System.out.println(showInfo2);
30.        Method work = cls.getDeclaredMethod("work",int.class);
31.        System.out.println(work);
32.        System.out.println("-----------------------");
33.        //获取方法的具体结构：
34.        /*
35.        @注解
36.        修饰符 返回值类型  方法名(参数列表) throws XXXXX{}
37.         */
38.        //名字：
39.        System.out.println(work.getName());
40.        //修饰符：
41.        int modifiers = work.getModifiers();
42.        System.out.println(Modifier.toString(modifiers));
43.        //返回值：
44.        System.out.println(work.getReturnType());
45.        //参数列表：
46.        Class[] parameterTypes = work.getParameterTypes();
47.        for(Class c:parameterTypes){
48.            System.out.println(c);
49.        }
50. 
51.        //获取注解：
52.        Method myMethod = cls.getMethod("myMethod");
53.        Annotation[] annotations = myMethod.getAnnotations();
54.        for(Annotation a:annotations){
55.            System.out.println(a);
56.        }
57. 
58.        //获取异常：
59.        Class[] exceptionTypes = myMethod.getExceptionTypes();
60.        for(Class c:exceptionTypes){
61.            System.out.println(c);
62.        }
63. 
64. 
65.        //调用方法：
66.        Object o = cls.newInstance();
67.        myMethod.invoke(o);//调用o对象的mymethod方法
68. 
69.        System.out.println(showInfo2.invoke(o,12,45));;
70. 
71.    }
72.}
73. 
```

### 获取类的接口，所在包，注解

```
1.  package com.zhaoss.test03;
2.   
3.  import java.lang.annotation.Annotation;
4.   
5.  public class Test04 {
6.      public static void main(String[] args) {
7.          //获取字节码信息：
8.          Class cls = Student.class;
9.          //获取运行时类的接口：
10.        Class[] interfaces = cls.getInterfaces();
11.        for(Class c:interfaces){
12.            System.out.println(c);
13.        }
14. 
15.        //得到父类的接口：
16.        //先得到父类的字节码信息：
17.        Class superclass = cls.getSuperclass();
18. 
19.        //得到接口：
20.        Class[] interfaces1 = superclass.getInterfaces();
21.        for(Class c:interfaces1){
22.            System.out.println(c);
23.        }
24. 
25.        //获取运行时类所在的包：
26.        Package aPackage = cls.getPackage();
27.        System.out.println(aPackage);
28.        System.out.println(aPackage.getName());
29. 
30.        //获取运行类的注解：
31.        Annotation[] annotations = cls.getAnnotations();
32.        for(Annotation a:annotations){
33.            System.out.println(a);
34.        }
35. 
36.    }
37.}
38. 
```

 

 

### 关于反射的面试题

【1】问题1：创建Person的对象，以后用new Person()创建,还是用反射创建？ 

【2】问题2：反射是否破坏了面向对象的封装性？  

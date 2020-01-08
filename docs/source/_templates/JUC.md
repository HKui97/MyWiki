JVM
===

   熟悉JVM架构与GC垃圾回收机制以及相应的堆参调优，有过在linux进行系统调优的经验

一、JVM组成结构谈谈
-------------------

|image0|

JVM是运行在操作系统之上的，他与硬件没有直接的交互。

二、JVM体系结构概览
-------------------

|image1|

1. Class Loader类加载器

   负责加载class文件，class文件在文件开头有特定的文件标示，并且ClassLoader只负责class文件的加载，至于他是否可以允许，则由Execution
   Engine决定

2. Execution Engine执行引擎 ：负责解释命令，提交操作系统执行

3. Native Interface 本地接口

   Java语言本身不能对操作系统底层进行访问和操作，但是可以通过JNI接口调用其他语言来实现对底层的访问。

4. Native Method Stack 本地方法栈

   java在内存中专门开辟了一块区域\ **处理标记为native的代码**\ ，他的具体做法是Native
   Method Stack中登记native方法，\ **在Execution Engine执行时加载native
   libraies**\ 。

5. Runtime Data Area 运行数据区

6. Method Area方法区

   方法区是被所有线程共享，所有字段和方法字节码、以及一些特殊方法如构造函数，接口代码也在此定义。简单说，所有定义方法的信息都保存在该区域，\ **此区属于共享区间**\ 。用来\ **保存装载的类的元结构信息**\ 。

   静态变量+常量+类信息+运行时常量池存放在\ **方法区**

   实例变量存在\ **堆内存**\ 中

.. |image0| image:: images/1559219896(1).jpg
.. |image1| image:: images/1559220033(1).jpg
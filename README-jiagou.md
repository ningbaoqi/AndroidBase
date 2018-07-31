### Android系统架构
image1

|层次|说明|
|------|------|
|Application|与用户直接交互，都是由Java开发|
|Framework|大部分用Java语言编写，它是Android平台上Java世界的基石|
|Libraries|这一层提供动态库也叫共享库，Android运行时库，Dalvik虚拟机等，从编程语言角度来说，这一层大部分都是用C或C++编写的，所以可以叫做Native层；Andorid运行时由两部分组成：Android核心库集和ART，其中核心库集提供了java语言核心库所能使用的绝大部分功能，而虚拟机则负责运行Android应用程序，ART模式是在用户安装app时进行预编译（AOT）的，将原本在程序运行时的编译动作提前到应用安装时，这样使得程序在运行时可以减少动态编译的开销，从而提升了Androidapp的运行效率，由于ART需要在安装App时进行AOT处理，因此ART需要占用更多的存储空间，应用安装和系统启动时间会延长不少|
|Linux内核|包含了Linux内核和一些驱动模块如USB驱动，Camera驱动，蓝牙驱动等|

image1

+ 一般而言，Java世界经由JNI层通过IPC（进程间通信）方式与Native世界交互，而Android平台上的IPC方式就是Binder，Socket也是常用的IPC方式；

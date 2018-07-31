### 搭建Android系统开发环境
#### 一、安装Ubuntu操作系统
+ [Ubuntu官网](http://www.ubuntu.org)从服务器上下载最新的软件包列表`sudo apt-get update`；Ubuntu上安装4.4版本的`gcc`和`g++`的命令：

```
sudo apt-get install gcc-4.4 g++-4.4 g++-4.4-multilib gcc-4.4-multilib
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-4.4 50
sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-4.4 50
```
+ 配置选择版本的命令：
```
sudo update-alternatives --config g++
sudo update-alternatives --config gcc
```
#### 二、安装和配置`JDK1.6`

|安装`JDK1.6`步骤|
|------|
|文件名为`jdk-6u45-linux-x64.bin`[下载地址](http://www.oracle.com/technetwork/java/javase/downloads/java-archive-downloads-javase6-419409.html#jdk-6u45-oth-JPR)|
|下载完成后修改下载文件的属性为可执行，命令：`chmod +x jdk-6u45-linux-x64.bin`|
|执行下载的bin文件，这将创建包含JDK文件的目录`jdk1.6.0_45：./jdk-6u45-linux-x64.bin`|
|在Linux系统的`/usr/lib`目录下创建子目录`jvm：sudo mkdir /usr/lib/jvm`|
|移动`./jdk-6u45-linux-x64.bin`中展开的文件目录到`jvm`目录下：`sudo mv jdk1.6.0_45 /usr/lib/jvm`|

+ 配置环境变量：如果只是针对当前用户，修改`~/.bashrc`文件就可以了，在文件结尾处加上如下命令；如果想使用`root`权限进行设置，可以在`/root/.profile`文件中修改`PATH`环境变量；

```
export JAVA_HOME=/usr/bin/jvm/jdk1.6.0_45
export JRE_HOME=/usr/lib/jvm/jdk1.6.0_45/jre
export CLASSPATH=$JAVA_HOME/lib:$JRE_HOME/lib:$CLASSPATH
export PATH=$JAVA_HOME/bin:$JRE_HOME/bin:$PATH
```
+ 测试是否配置成功：`java -version`；
#### 三、安装OpenJDK1.7

```
sudo apt-get install openjdk-7-jdk
sudo update-alternatives --config java
sudo update-alternatives --config javac
```
#### 四、安装编译需要的开发包
+ 安装新的开发环境时最好到Android的官网上下载Google指定的安装包列表，[地址](http://source.android.com/source/initializing.html)；在Unbuntu12.04及以上版本需要安装下列开发包：

```
sudo apt-get install git gnupg flex bison gperf build essential zip curl libc6-dev libncurses5-dev:i386 x11proto-core-dev libx11-dev:i386 libreadline6-dev:i386 libg11-mesa-glx:i386 libg11-mesa-dev g++-multilib mingw32 tofrodos python-markdown libxm12-utils xsltproc zlib1g-dev:i386
```
#### 五、安装一些有用的工具

|工具|说明|
|------|------|
|安装AndroidSDK|AndroidSDK中附带了很多有用的工具，如`adb、ddms、hierarchyviewer`等，都是进行Android系统开发调试必须用到的；AndroidSDK需要从Android的官网上下载，下载解压缩后可以将SDK目录下的`platform_tools`和`tools`两个子目录的路径添加到`ubuntu `的`PATH`环境变量中，方便以后使用|
|安装AndroidStudio|系统级别的java开发会用到很多Android的内部类，这些类在SDK中不存在，因此，使用AndroidStudio时会报错，解决方法是从Android的源代码编译结果中找到对应的系统类库，添加到AndroidStudio的项目依赖库中就可以了，需要注意的是，这种方式只能用来解决编译问题，最后产生的APK文件并不能直接使用|
|安装SourceInsight|[SourceInsight官网](http://www.sourceinsight.com)|
|安装比较工具`Meld`|`Meld`可以通过命令安装：`sudo apt-get install meld`|


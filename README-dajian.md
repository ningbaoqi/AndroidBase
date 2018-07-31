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

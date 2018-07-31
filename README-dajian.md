### 搭建Android系统开发环境
#### 一、安装Ubuntu操作系统
+ [Ubuntu官网](http://www.ubuntu.org)；从服务器上下载最新的软件包列表：`sudo apt-get update`；Ubuntu上安装4.4版本的`gcc`和`g++`的命令：

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

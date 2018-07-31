### 下载Android源码
#### 一、`Git and Repo`简介
+ 首先通过`curl`下载`repo`的最新版本；命令为：`curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo`；下载完`repo`脚本后，需要修改文件的属性为可执行：`chmod a+x ~/bin/repo`；

|`repo`的简单用法|
|-------|
|`repo help`命令：格式为`repo help [command]`；例如：`repo help init` 将显示`init`命令的参数和用法|
|`repo init`命令：`repo init`可以使用很多参数，`-u`参数用来初始化软件仓库，如：`repo init -u git://android.git,kernel.org/platform/manifest.git`|
|`-b`参数来指定某个分支，不指定则默认为`master`分支：如：`repo init -u git://android.git.kernel.org/platform/manifest.git -b android5.0.1`|
|`repo sync`命令：`repo sync -j4`；会使用`4`个线程来同时下载|

#### 二、下载Android源码
+ 在下载代码前，需要知道版本的分支名，通过`repo`可以查看所有分支名：`repo init -u https://android.googlesource.com/platform/manifest`；`repo `的`init`指令运行后会在当前目录下创建一个隐藏的目录`.repo`，重新执行`init`指令需要先删除这个隐藏目录，否则执行会失败；下载源码的命令：

```
mkdir android5.0
cd android5.0
repo init -u https://android.googlesource.com/platform/manifest -b android-5.0.0_r1
repo sync
```

+ 如果需要通过代理服务器下载，可以使用下面的命令来设置Linux的环境变量：

```
export HTTP_PROXY=http://<user_id>:<password>@<proxy_server>:<proxy_port>
export HTTPS_PROXY=http://<user_id>:<password>@<proxy_server>:<proxy_port>
```

#### 三、下载Kernel源码
+ Google所有设备的`Kernel`源码都放在下面这些`git`库中，可以使用`git`的`clone`命令复制一份到本地：

```
git clone https://android.googlesource.com/Kernel/common.git
git clone https://android.googlesource.com/Kernel/exynos.git
git clone https://android.googlesource.com/Kernel/goldfish.git   //是模拟器的内核代码库
git clone https://android.googlesource.com/Kernel/msm.git
git clone https://android.googlesource.com/Kernel/omap.git
git clone https://android.googlesource.com/Kernel/samsung.git
git clone https://android.googlesource.com/Kernel/tegra.git
```
+ `clone`完成后还需要使用`git`的`checkout`命令检出代码，`checkout`需要使用分支名称作为参数，分支名称可以通过`git`的`branch`命令查到：`git branch -a`；这条命令将列出所有分支，知道了分支名后，就可以使用`checkout`命令来检出代码了：`git checkout branch_name`；

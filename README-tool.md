### Android常用开发工具的用法
#### 在命令行创建、删除和浏览AVD
+ 在命令行下管理AVD需要借助`android`命令，位于`AndroidSDK安装目录的tools目录下`，直接执行`android命令`会期启动`AndroidSDK管理器`，除此之外，该命令还支持如下命令：

|命令|描述|
|------|------|
|`list`|`列出机器上所有已经安装的Android版本和AVD设备`|
|`list avd`|`列出机器上所有已经安装的AVD设备`|
|`list target`|`列出机器上所有已经安装的Android版本`|
|`create avd`|`创建一个AVD设备`|
|`move avd`|`移动和重命名一个AVD设备`|
|`delete avd`|`删除一个AVD设备`|
|`update avd`|`升级一个AVD设备使之符合新的SDK环境`|
|`create project`|`创建一个新的Android项目`|
|`update project`|`更新一个已有的Android项目`|
|`create test-project`|`创建一个新的Android测试项目`|
|`update test-project`|`更新一个已有的Android测试项目`|

+ 如使用`android list`或`android list avd`；创建一个全新的AVD设备：

```
//-n -t选项是必须的，其余的选项是可选的，如果不设置-p选项，创建的AVD默认保存在%ANDROID_SDK_HOME%/.android/avd路径下
android create avd -n <avd名称> -t <Android版本> -b <CPU构架> -p <AVD设备保存位置> -s <选择AVD皮肤>
//实例为
android create avd -n creayit -t 21 -b armeabi-v7a
```

#### 使用Andorid模拟器Emulator
+ `在AndroidSDK安装目录的tools目录下有一个emulator.exe`，`使用emulator.exe启动模拟器有两种方法`：

```
emulator -avd crazity //运行名为crazity的AVD设备
emulator -data myfile //以myfile作为镜像文件来运行AVD设备
```

#### 使用Monitor进行调试
+ Android提供的一个`Monitor工具`，`该工具用于监视Android设备的运行`，他的功能强大，`运行monitor.bat就可以看见系统启动了`；其面板如下：

|面板|说明|
|------|------|
|`设备面板`|列出当前所有运行的手机和模拟器，并列出各手机内的所有进程信息，如果需要查看制定手机或制定进程信息，则应先在该面板内选中制定的手机或进程|
|`信息输出面板`|相对于java的控制台|
|`线程跟踪面板`|用于查看指定进程内所有正在执行的线程状态。如果需要让该面板显示指定进程内线程的状态，应该保证：在设备面板上选中需要查看的进程；在设备面板上单机update threads按钮|
|`Heap内存跟踪面板`|用于查看制定进程内堆内存的分配和回收信息，在设备面板上选中需要查看的进程；在设备面板上单机update heap按钮|
|`模拟器控制面板`|用于让模拟器模拟拨打电话，发送短信等，还可以设置模拟器的虚拟位置信息等|
|`文件管理器面板`|用于查看Android设备所包含的文件，也可用于将Android设备的文件导出到设备上，也可将电脑上的文件导入到Android设备中|

#### AndroidBebugBridge用法
+ `AndroidBebugBridge是一个功能强大的工具`，`他位于AndroidSDK安装目录的platform-tools中`；

|作用|说明|
|------|------|
|`查看当前运行的模拟器`|`adb devices`|
|`电脑与手机之间文件的相互复制、将电脑文件复制到模拟器中`|`adb push ./caonima.txt  /sdcard/`|
|`将模拟器文件复制到电脑上`|`adb pull /sdcard/caonima.file ./`|
|`启动模拟器的shell窗口`|`adb shell`|
|`安装APK程序`|`adb install [-r] [-s] <file>：file指的是APK文件，-r表示重新安装该apk；-s表示将apk安装到SD卡上，默认将apk安装在内部存储器上`|
|`卸载APK程序`|`adb uninstall [-k] <package>：package指定要删除的apk包，-k表示只删除该应用程序，但是保留该程序所用的数据和缓存目录`|

#### 使用mksdcard管理虚拟SD卡
+ 命令格式为：`mksdcard [-l label] <size> <file>`：`size指定虚拟SD卡的大小`；`file制定保存虚拟SD卡的文件镜像`如：`mksdcard 64M 存储路径/sdcard.img如果希望在启动模拟器时使用指定的虚拟SD卡`，可以使用：`emulator -avd crazyit -sdcard 文件镜像带路径`；
#### 项目生成工具Ant
+ 使用`ant help`目录可以查看很多信息：

|标志|说明|
|------|------|
|`clean`|`清除项目生成的内容，也就是恢复原来的样子`|
|`debug`|`打包一个调试用的Android应用的apk文件，使用debug key进行签名`|
|`release`|`打包一个发布用的Android应用的apk文件`|
|`test`|`运行测试，要求该项目必须是一个测试项目`|
|`install`|`将生成的调试用的apk包安装在模拟器上`|
|`uninstall`|`从模拟器上卸载应用程序`|

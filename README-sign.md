### 签名Android应用程序
+ `Android要求对作为产品发布的应用进行签名`；签名的作用如下：

|签名作用|
|------|
|`确定开发者的身份；由于应用开发者可以通过使用相同包名来替换已经安装的程序，因此使用签名可以避免发生这种情况`|
|`确保应用的完整性：签名会对应用包中的每个文件进行处理，从而确保程序包中的文件不会被替换`|

+ `正式发布一个Android应用，必须使用合适的数字证书来给应用签名，不能使用android studio或ant工具生成的调试证书来发布`；

#### 使用命令对APK包签名步骤

|步骤|
|------|
|`创建key stare库`，`jdk安装目录下的bin目录下提供了keytool.exe工具来生成数字证书`，在命令行输入：`keytool -genkeypair -alias crazyit -keyalg RSA -validity 400 -keystore crazyit.jks`：`-genkeypair指定生成数字证书`；`-alias制定生成数字证书的别名`；`-keyalg指定生成的数字证书的算法使用的是RSA算法`；`-validity指定生成的数字证书的有效期`；`-keystore指定所生成的数字证书的存储路径`|
|`使用jarsigner.exe命令对未签名的apk签名`，`jdk安装目录下的bin目录下提供了jarsigner.exe工具命令`为：`jarsigner -verbose -keystore crazyit.jks -signdjar HelloWorld_crazyit.apk app-release-unaligned.apk crazyit`；`-verbose指定生成详细输出`；`-keystore指定数字签名的存储路径`；`-signdjar三个参数分别`为：`签名后的apk文件`、`未签名的apk文件`、`数字证书别名`|

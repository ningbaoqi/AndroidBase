 ### Android构建流程
+ 将`Java`文件编译成`字节码文件`，然后将`字节码文件`与`jar文件`打包成`class.dex`的`Android可执行的文件`，再`打包资源文件`，最后再`.dex文件`和`safe文件`打包成`未签名的包`，最后通过`签名`打包成一个完整的包；

![image](https://github.com/ningbaoqi/AndroidBase/blob/master/gif/pic-3.jpg)

### jenkins持续集成构建
+ `jenkins`可以持续集成构建`apk`，同时需要配置`gradle文件`；

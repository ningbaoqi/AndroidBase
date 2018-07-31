### Proguard混淆
#### 一、Proguard到底是什么
+ `就是在Android打包的时候为我们压缩代码，同时混淆我们的重要信息用的`；`Proguard工具是用于压缩、优化、混淆代码，主要作用是可以移除代码中的无用类，字段，方法和属性；同时可以对他们进行混淆命名`；`缩小打包后apk的体积，并防止被别人反编译`；
#### Proguard技术的功能

|Proguard技术的功能|说明|
|------|-------|
|`压缩`|`检查并移除我们项目中没有用到的类、字段、方法、属性`|
|`优化`|`就是对我们编译好的字节码文件进行优化，移除无用的.class文件中的一些指令`|
|`混淆`|`将开发中有意义的名词，混淆成无意义的名词，防止反编译`|
|`预检测`|`在Java平台上对那些处理后的代码再次进行检测`|

#### Proguard工作原理

|Proguard工作原理|说明|
|-----|-----|
|`EntryPoint`|可以理解成一种标志，在Proguard中不会被处理的类或者方法|

```
release {
    minifyEnabled true//使用混淆
    proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'//使用默认的混淆文件和混淆规则进行混淆
}
```

### gradle
#### settings.gradle
```
# 包含构建的模块
include , ,
```
#### 根目录的build.gradle
```
buildscript {
    repositories {
        apply : google()
        jcenter()
        mavenCentral()
    }
    dependencies {
        classpath classpath }
}

allprojects {
    repositories {
        google()
        jcenter()
    }
}
ext{
    versionCode=versionName=supportVersion=butterknifeVersion=geniusVersion=glideVersion=circleimageviewVersion=geniusVersion=}
```
#### 模块下的build.gradle
```
apply : android {
    compileSdkVersion defaultConfig {
        applicationId minSdkVersion targetSdkVersion versionCode versionName testInstrumentationRunner externalNativeBuild {
            cmake {
                cppFlags }
        }
    }
    buildTypes {
        release {
            minifyEnabled proguardFiles getDefaultProguardFile(), }
    }
    externalNativeBuild {
        cmake {
            path }
    }

}

dependencies {
    implementation fileTree(include: [], dir: )
    implementation $rootProject.ext.supportVersionimplementation $rootProject.ext.supportVersionimplementation $rootProject.ext.circleimageviewVersionimplementation $rootProject.ext.geniusVersionimplementation $rootProject.ext.geniusVersionimplementation $rootProject.ext.glideVersionimplementation testImplementation androidTestImplementation androidTestImplementation implementation project()
    implementation $rootProject.ext.butterknifeVersionannotationProcessor $rootProject.ext.butterknifeVersionimplementation $rootProject.ext.supportVersion}
```
+ 可以覆盖根目录的build.gradle中的任何属性；
#### 查看编译时的具体log

```
./gradlew compileDebugJavaWithJavac --stacktrace
```

### gradle常用的几个命令

|gradle常用的几个命令|说明|
|------|------|
|./gradlew -v|当前目录中项目的版本号|
|./gradlew clean|清除当前项目app目录下的build文件夹|
|./gradlew build|检查依赖并编译打包，此命令会把debug和release环境的包都打出来，如果正式发布这个项目，只需要打release包即可|
|./gradlew assembleDebug|编译并打debug包|
|./gradlew assembleRelease|编译并打release包|
|./gradlew installRelease|通过Release模式打包并安装|
|./gradlew uninstallRelease|卸载Release模式包|

### gradle实现多渠道打包
+ 以友盟为例；需要导入友盟的SDK，在AndroidManifest中有如下的代码片段；
```
<meta-data
     android:name="UMENG_CHANNEL"//表示渠道标示
     android:value="${UMENG_CHANNEL_VALUE}" />//打包的目标
```
+ 在文件的build.gradle中设置productFlavors
```
android {
    productFlavors {
        xiaomi {
            manifestPlaceholders = [UMENG_CHANNEL_VALUE: "xiaomi"]
        }
        _360 {
            manifestPlaceholders = [UMENG_CHANNEL_VALUE: "_360"]
        }
        baidu {
            manifestPlaceholders = [UMENG_CHANNEL_VALUE: "baidu"]
        }
        wandoujia {
            manifestPlaceholders = [UMENG_CHANNEL_VALUE: "wandoujia"]
        }
    }
}
```
+ 此时执行`./gradlew assembleRelease`命令就可以实现打包操作；

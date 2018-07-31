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

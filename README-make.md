### 编译Android源代码
+ Android的编译主要利用的是mk文件；

|步骤|
|------|
|执行`source ./build/envsetup.sh`这个脚本用来设置Android的编译环境|
|执行`lunch`命令，该命令用来选择编译目标|
|`make -j32`用于编译整个系统|
|`make MediaProvider`对应于单个模块编译，会把该模块依赖的其他模块也一起编译|
|`mmm packages/providers/MediaProvider`编译指定目录下的目标模块，而不编译它所依赖的模块|
|`mm`需要先用cd命令进入packages/providers/MediaProvider目录，然后执行mm命令，该命令会编译当前目录下的模块，也不编译它所依赖的模块|

#### 常用的目标模块

|目标模块|make命令|mmm命令|
|------|-------|-------|
|init|make init|mmm system/core/init|
|zygote|make app_process|make frameworks/base/cmds/app_process|
|system_server|make services|mmm frameworks/base/services/java|
|RefBase等|make libutils|mmm frameworks/base/libs/utils|
|Looper等|make framework|mmm frameworks/base|
|AudioTrack|make libmedia|mmm frameworks/base/media/libmedia|
|AudioFlinger|make libaudioflinger|mmm frameworks/base/libs/audioflinger|
|AudioPolicyService|make libaudiopolicy|mmm hardware/msm7k/libaudio-qsd8k|
|SurfaceFlinger|make libsurfaceflinger|mmm frameworks/base/libs/surfaceflinger|
|Vold|make vold|mmm system/vold|
|Rild|make rild|mmm hardware/ril/rild|
|MediaProvider|make MediaProvider|mmm packages/providers/MediaProvider|
|Phone|make Phone|mmm packages/apps/Phone|

+ 当编译生成的东西push到指定的手机文件目录下，就可以替换以前的文件，如果想测试新模块，则需要先杀掉所有使用该模块的进程，进程重启后会重新加载模块，这时使用的就是新文件了；

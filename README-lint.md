### Android的静态lint检查
#### 一、什么是Android lint检查
+ `Android Lint`是一个`静态代码分析工具，它能够对Android项目中潜在的bug、可优化的代码、安全性、性能、可用性、可访问性、国际化等进行检查`；
#### 二、lint工作流程

image1

#### 三、如何配置lint
```
()//强制忽略lint检查
(Bundle savedInstanceState) {
    .onCreate(savedInstanceState)setContentView(R.layout.)}

```
```
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:ignore="UnusedResource"//将会忽略该布局的lint检查
    tools:context=".MainActivity">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello World!"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent" />
</LinearLayout>
```

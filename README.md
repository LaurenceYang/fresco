# 自定义Fresco

Fresco是FaceBook推出的一款功能强大的图片加载库。它能有效解决在处理图片时的内存占用问题。

但是Fresco库本身的占用空间较大，如目前的版本0.8.1大小约3M（仅armeabi，armeabi-v7a,X86平台）。
在引入到app后会导致应用的大小突增。

在当前项目中，我们会对Fresco库的代码进行删减，从而减小库的大小。

## 删减的方法
- 删除可能不需要的平台so
- 删除可能不需要支持的格式
- 其它

## 目前删减结果
目前仅删减了jni的代码，下面的统计仅包含armeabi，armeabi－v7a，X86三个平台。

- 删减前so大小总计：约2500K
- 删减后so大小总计：约1200K

## 在Android Studio中使用本项目自定义fresco
如果你使用Gradle进行编译，
在`build.gradle`文件的`repositories`添加如下所示配置：
```groovy
mavenCentral()
```

在`build.gradle`文件的`dependencies`区域内添加如下所示配置：

```groovy
compile 'com.github.theyy:fresco:0.8.3'
```

如果你需要配置so文件支持的架构，在`build.gradle`文件的`defaultConfig`区域内添加如下所示配置：
```groovy
ndk ｛
    abiFilters "armeabi" "armeabi-v7a"
｝
```

## 链接
Fresco官方开源链接：[fresco](https://github.com/facebook/fresco)
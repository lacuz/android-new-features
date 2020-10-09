# 非SDK限制

Android 11 包含更新后的受限制非 SDK 接口列表（基于与 Android 开发者之间的协作以及最新的内部测试）。在限制使用非 SDK 接口之前，我们会尽可能确保有可用的公开替代方案。

如果您的应用并非以 Android 11 为目标平台，那么其中一些变更可能不会立即对您产生影响。不过，虽然您目前可以使用一些非 SDK 接口（具体取决于应用的目标 API 级别），但只要您使用任何非 SDK 方法或字段，应用无法运行的风险终归较高。

如果您不确定自己的应用是否使用了非 SDK 接口，则可以测试该应用，进行确认。如果您的应用依赖于非 SDK 接口，您应该开始计划迁移到 SDK 替代方案。然而，我们知道某些应用具有使用非 SDK 接口的有效用例。如果您无法为应用中的某项功能找到使用非 SDK 接口的替代方案，应请求新的公共 API。

## 非 SDK 测试 API 现在受到限制
从 Android 11 开始，默认情况下，非 SDK 测试 API（即 AOSP 中带有 @TestApi 注释的 API）现在被屏蔽。这些非 SDK 接口用于在 Android 平台上执行内部测试。应用可以继续使用在其目标 API 级别上不受限制的非 SDK 测试 API，但任何新的测试 API 都会被列入屏蔽名单。


## Android 11 的列表变更
Android 11 中的列表变更分为以下几类：

* 在 Android 10（API 级别 29）中不受支持（列入了灰名单）而目前在 Android 11（API 级别 30）中被屏蔽的非 SDK 接口。
* 在 Android 11 中被添加到 Android SDK 的非 SDK 接口。

如需查看 Android 11（API 级别 30）的所有非 SDK 接口的完整列表，请下载以下文件：[hiddenapi-flags.csv](https://dl.google.com/developers/android/rvc/non-sdk/hiddenapi-flags.csv)。


## 什么是非sdk接口？
首先先了解一下android的sdk接口：[https://developer.android.google.cn/reference/packages.html](https://developer.android.google.cn/reference/packages.html)
而非SDK接口的处理是 API 抽象出来的实现细节，因此这些接口可能会在不另行通知的情况下随时发生更改。比如应用在通过反射等机制与类互动时（WebView、HTTP等），android9.0之后就不应访问 SDK 中未列出的方法或字段，否则会提示报错，意思是不要搞些花里胡哨的操作，可能会出现兼容性问题，老老实实的用谷歌大佬提供的API就好了。
![](../assets/no_sdk_notice.png)

* 所有私有 API 均在 Logcat 中显示警告。
* DP版本在 Activity 开始时会显示 Toast 警告。

## 非sdk接口扫描
方法1：手动遍历所有功能，通过系统输出日志分析。
```
*Accessinghidden field Landroid/os/Message;->flags:I (light greylist, JNI)

*Accessing hidden method

Landroid/app/ActivityThread;->currentActivityThread()Landroid/app/ActivityThread;(dark greylist, reflection)

*Accessing hidden method

Landroid/app/ActivityThread;->currentActivityThread()Landroid/app/ActivityThread;(blacklist, reflection)
```

方法二：Veridex 扫描工具扫描

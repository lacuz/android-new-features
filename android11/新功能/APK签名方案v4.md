# [APK签名方案v4](https://developer.android.google.cn/studio/command-line/apksigner#v4-signing-enabled)
Android 11 添加了对 APK 签名方案 v4 的支持。此方案会在单独的文件 (apk-name.apk.idsig) 中生成一种新的签名，但在其他方面与 v2 和 v3 类似。没有对 APK 进行任何更改。此方案支持 ADB 增量 APK 安装，这样会加快 APK 安装速度。

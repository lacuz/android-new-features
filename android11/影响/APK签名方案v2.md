# APK签名方案v2★

对于以 Android 11（API 级别 30）为目标平台，且目前仅使用 APK 签名方案 v1 签名的应用，现在还必须使用 APK 签名方案 v2 或更高版本进行签名。用户无法在搭载 Android 11 的设备上安装或更新仅通过 APK 签名方案 v1 签名的应用。

如需验证您的应用是否已使用 APK 签名方案 v2 或更高版本进行签名，您可以在命令行中使用 Android Studio 或 apksigner 工具。
>注意：为支持运行旧版 Android 的设备，除了使用 APK 签名方案 v2 或更高版本为您的 APK 签名之外，您还应继续使用 APK 签名方案 v1 进行签名。
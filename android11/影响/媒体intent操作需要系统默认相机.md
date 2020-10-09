# 媒体intent操作需要系统默认相机☆

从 Android 11 开始，只有预装的系统相机应用可以响应以下 intent 操作：

* android.media.action.VIDEO_CAPTURE
* android.media.action.IMAGE_CAPTURE
* android.media.action.IMAGE_CAPTURE_SECURE

如果有多个预装的系统相机应用可用，系统会显示一个对话框，供用户选择应用。如果您希望自己的应用使用特定的第三方相机应用来代表其捕获图片或视频，可以通过为 intent 设置软件包名称或组件来使这些 intent 变得明确。
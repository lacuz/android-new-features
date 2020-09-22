# [APP退出原因](https://developer.android.com/preview/features#app-process-exit-reasons)

Android 11 引入了 ActivityManager.getHistoricalProcessExitReasons() 方法，用于报告近期任何进程终止的原因。应用可以使用此方法收集崩溃诊断信息，例如进程终止是由于 ANR、内存问题还是其他原因所致。此外，您还可以使用新的 setProcessStateSummary() 方法存储自定义状态信息，以便日后进行分析。

getHistoricalProcessExitReasons() 方法会返回 ApplicationExitInfo 类的实例，该类包含与应用进程终止相关的信息。通过对此类的实例调用 getReason()，您可以确定应用进程终止的原因。例如，REASON_CRASH 的返回值表示应用中发生了未处理的异常。如果应用需要确保退出事件的唯一性，可以保留特定于应用的标识符，例如基于 getTimestamp() 方法的时间戳的哈希值。

使用方式：
```kotlin
val am = context!!.getSystemService(Context.ACTIVITY_SERVICE) as ActivityManager?
val list = am!!.getHistoricalProcessExitReasons(context!!.packageName, 0, 10)
for( info in list) {
    info?.let { it -> Log.i("TAG>>", it.toString()) }
}
```
![](..assets/F2B9DA5B-25DA-4458-9DBD-FCF641EAE8C7.png)
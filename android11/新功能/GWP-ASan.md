# GWP-ASan

在开发者第3预览版中，Google新增了GWP-ASan堆（Heap）分析工具， 是一种原生内存分配器功能，可帮助查找释放后使用和堆缓冲区溢出错误。GWP-ASan是采样分配工具，能以最小的成本开销和效能影响，侦测堆内存错误，在默认情况下，Google已经为平台二进制文件以及系统应用程序启用了GWP-ASan，开发者也可以为自家的应用程序启用GWP-ASan。可以全局启用此功能，也可以为应用的特定子进程启用此功能。

[使用指南](https://developer.android.google.cn/ndk/guides/gwp-asan)



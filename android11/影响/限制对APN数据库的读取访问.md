# 限制对 APN 数据库的读取访问☆

以 Android 11 为目标平台的应用现在必须具备 Manifest.permission.WRITE_APN_SETTINGS 特权，才能读取或访问电话提供程序 APN 数据库。如果在不具备此权限的情况下尝试访问 APN 数据库，会生成安全异常
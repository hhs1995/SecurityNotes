# 渗透笔记 - 善于利用Linux文件系统

------

>* 查看系统版本信息

除了`uname -a`命令以外，可以尝试读取`/etc/issue`和`/proc/version`文件内容。一般而言，基于Linux内核及衍生系统的开发者或运维者可能会修改原始`/etc/issue`中的系统版本信息，但他们一般不会注意到`/proc/version`文件。

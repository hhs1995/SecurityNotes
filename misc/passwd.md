#重置密码
--------

## RedHat/CentOS/Fedora 系统密码破解

在grub选项菜单按E进入编辑模式,编辑kernel 那行最后加上S (或者Single）,按B，启动到single-usermode,进入后执行下列命令
```
mount -t proc proc /proc
mount -o remount,rw /
passwd
sync
reboot
```

## Debian系统密码破解
在grub选项菜单'DebianGNU/Linux,...(recovery mode)'，按e进入编辑模式，编辑kernel那行最后面的 rosingle 改成 rw singleinit=/bin/bash，按b执行重启，进入后执行下列命令
···
mount -a
passwd  root
reboot
···

## Freebsd 系统密码破解

开机进入引导菜单，选择每项(按4)进入单用户模式，进入之后输入一列命令

···
mount   -a
fsck -y
passwd
init 6      //重启
···

## Solaris 系统密码破解

在grub选项菜中选择solarisfailasfe 项，系统提示Do you wish to have it mounted read-write on /a ?[y,n,?] 选择y就进入单用户模式

```
passwd
init 6    //重启
```

## NetBsd 系统密码破解

开机：当出现提示符号并开始倒数五秒时，键入以下指令：

　　boot -s    //进入单用户模式命令

在以下的提示符号中

　　Enterpathname of shell or RETURN for sh:

按下 Enter,键入以下指令：

```
mount -a
fsck -y
passwd
exit    //退出，进入多人模式
```

## SUSE 系统密码破解

1.重新启动机器，在出现grub引导界面后，在启动linux的选项里加上init=/bin/bash，通过给内核传递init=/bin/bash参数使得OS在运行login程序之前运行bash，出现命令行。

2.稍等片刻出现(none)#:命令行。

3.这时输入mount -n / -o remount,rw 表示将根文件系统重新mount为可读写，有了读写权限后就可以通过passwd命令修改密码了。

4.这时输入passwd命令就可以重置密码了

5.修改完成后记得用mount -n / -o remount,ro将根文件系统置为原来的状态。


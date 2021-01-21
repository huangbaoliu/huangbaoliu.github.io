---
layout:     post
title:      Centos 7 Petalinux工具安装
date:       2021-1-21
author:     huangbaoLiu
header-img: img/post-bg-desk.jpg
catalog: true
tags:
    - Tool skills
---

## 1、安装工具/库

```
[root@localhost ~]#install tofrodos gawk xvfb git libncurses5-dev tftpd zlib1g-dev zlib1g-dev:i386 libssl-dev flex bison chrpath socat autoconf libtool texinfo gcc-multilib libsdl1.2-dev libglib2.0-dev screen pax ncurses-devel xterm zlib-devel glib2-devel
```

## 2、构建安装目录

```
[root@localhost ~]# mkdir -p /opt/pkg/petalinux
[root@localhost ~]# chown huangbao /opt/pkg/ 
[root@localhost ~]# chgrp huangbao /opt/pkg/ 
[root@localhost ~]# chgrp huangbao /opt/pkg/petalinux/ 
[root@localhost ~]# chown huangbao /opt/pkg/petalinux/
[root@localhost ~]# chmod 07555 /opt/pkg/petalinux
```

## 3、安装包赋予可执行权限

```
[huangbao@localhost opt]$ chmod +x petalinux-v2019.2-final-installer.run
```

## 4、开始安装

```
[huangbao@localhost opt]$ ./petalinux-v2019.2-final-installer.run /opt/pkg/petalinux/
```

<!--不能采用root权限安装-->

1. 按回车看协议内容
2. 按q退出协议
3. 按y同意协议内容
4. 在安装过程中会弹出 License，按“q”退出，然后按“y”同意。  

整个安装过程如下所示：

```
[huangbao@localhost opt]$ ./petalinux-v2019.2-final-installer.run /opt/pkg/petalinux/
INFO: Checking installation environment requirements...
WARNING: This is not a supported OS
INFO: Checking free disk space
INFO: Checking installed tools
INFO: Checking installed development libraries
INFO: Checking network and other services
WARNING: No tftp server found - please refer to "PetaLinux SDK Installation Guide" for its impact and solution
INFO: Checking installer checksum...
INFO: Extracting PetaLinux installer...

LICENSE AGREEMENTS

PetaLinux SDK contains software from a number of sources.  Please review
the following licenses and indicate your acceptance of each to continue.

You do not have to accept the licenses, however if you do not then you may 
not use PetaLinux SDK.

Use PgUp/PgDn to navigate the license viewer, and press 'q' to close

Press Enter to display the license agreements
Do you accept Xilinx End User License Agreement? [y/N] > y
Do you accept Webtalk Terms and Conditions? [y/N] > y
Do you accept Third Party End User License Agreement? [y/N] > y
INFO: Installing PetaLinux...
INFO: Checking PetaLinux installer integrity...
INFO: Installing PetaLinux SDK to "/opt/pkg/petalinux/."
INFO: Installing aarch64 Yocto SDK to "/opt/pkg/petalinux/./components/yocto/source/aarch64"...
INFO: Installing arm Yocto SDK to "/opt/pkg/petalinux/./components/yocto/source/arm"...
INFO: Installing microblaze_full Yocto SDK to "/opt/pkg/petalinux/./components/yocto/source/microblaze_full"...
INFO: Installing microblaze_lite Yocto SDK to "/opt/pkg/petalinux/./components/yocto/source/microblaze_lite"...
INFO: PetaLinux SDK has been installed to /opt/pkg/petalinux/.
```

## 5、工作环境设置

```
[huangbao@localhost opt]$ source /opt/pkg/petalinux/settings.sh 
PetaLinux environment set to '/opt/pkg/petalinux'
WARNING: This is not a supported OS
INFO: Checking free disk space
INFO: Checking installed tools
INFO: Checking installed development libraries
INFO: Checking network and other services
WARNING: No tftp server found - please refer to "PetaLinux SDK Installation Guide" for its impact and solution
[huangbao@localhost opt]$ echo $PETALINUX
/opt/pkg/petalinux
```


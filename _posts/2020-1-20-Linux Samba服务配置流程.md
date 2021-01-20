---
layout:     post
title:      Linux Samba服务配置流程
date:       2021-1-18
author:     huangbaoLiu
header-img: img/post-bg-desk.jpg
catalog: true
tags:
    - Tool skills
---

## 修改smb.conf，加入共享配置

```
[root@localhost ~]# vim /etc/samba/smb.conf
```

插入配置内容：

```
[opt]
	comment = Opt Directories
	path = /opt
	browseable = Yes
	writable = Yes
	valid users = smb
	create mask = 0777
	directory mask = 0777
```

## 重启samba服务

```
[root@localhost ~]# service smb restart
Redirecting to /bin/systemctl restart smb.service
[root@localhost ~]# service nmb restart
Redirecting to /bin/systemctl restart nmb.service
```



## 设置samba账户、密码

添加samba用户smb

```
[root@localhost ~]# useradd smb
```

设置samba用户smb的密码

```
[root@localhost ~]# smbpasswd -a smb
New SMB password:
Retype new SMB password:
Added user smb.
```

## 安全配置与权限设置

禁掉selinux、关掉防火墙

```
[root@localhost ~]# setenforce 0
[root@localhost ~]# iptables -F
```

给共享文件夹/opt赋予权限

```
[root@localhost ~]# chmod 777 /opt/ -R
```


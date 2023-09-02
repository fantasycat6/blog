---
title: 课时1-10-Linux用户和权限管理
url: https://www.yuque.com/u29002979/ep2zrx/lw42v2iewcwx3u9y_gryd5v
---

<a name="DjdiU"></a>

# 课程大纲

1. 用户组
2. 用户
3. 用户管理相关**文件**
4. 用户管理基本**命令**
5. 文件和目录**归属**
6. 文件和目录**权限** <a name="a0GMV"></a>

# 用户组Group

![image.png](../../../../assets/lw42v2iewcwx3u9y_gryd5v/1668341373504-8243d500-10ce-4c86-ad2b-67119b3585ff.png)

<a name="qMj8W"></a>

## 组ID-Group ID-GID

1. root用户组: GID=0
2. 程序用户组(系统用户组) : 1-999 (CentOS7)
3. 普通用户组: 1000-65535

`cat /etc/group` <a name="YXBOB"></a>

## Group相关命令

|  操作 |  命令 |
| --- | --- |
| 查看全部组 | cat /etc/group |
| 查看用户的所属组 | groups |
| 添加用户组 | groupadd security |
| 删除用户组 | groupdel security |

<a name="f0Qo5"></a>

# 用户User

<a name="Yo9ID"></a>

## 用户ID-User ID-UID

1. root用户: UID=0 (反之也成立)
2. 程序用户(系统用户) : 1-999 (CentOS7)
3. 普通用户: 1000-65535

`cat /etc/passwd`

<a name="fO0hh"></a>

## User相关命令

|  操作 |  命令 |
| --- | --- |
| 添加用户 | useradd |
| 修改用户密码 | passwd |
| 删除用户 | userdel |
| 修改用户信息 | usermod |

<a name="xxCHT"></a>

# 用户管理相关文件

<a name="VoNwv"></a>

## /etc/group

1. 组名
2. 组密码
3. GID
4. 用户列表

影子文件:
`cat /etc/gshadow`
组名: 密码: 组管理员: 组附加用户列表

> **root:x:0:**
> **bin:x:l:**
> **daemon:x:2:**
> **sys:x:3:**
> **adm:x:4:**
> **tty:x:5:**
> **disk:x:6:**
> **lp:x:7:**
> **mem:x: 8:**
> **kmem:x:9:**
> **wheel :X: 10:**
> **cdrom:x:1l:**
> **mail:X: 12: postfix**

<a name="MqEPK"></a>

## /etc/passwd

> root : x : 0 : 0 : root : /root : /bin/bash
> bin:x:1:1:bin:/bin:/sbin/nologin
> daemon: x:2:2:daemon:/sbin:/sbin/nologin
> adm:x:3:4:adm:/var/adm: / sbin/nologin
> lp:x:4:7:lp:/var/spool/lpd:/sbin/nologin
> sync:x:5:0:sync:/sbin: /bin/sync
> shutdown:x: 6:0:shutdown: /sbin: /sbin/shutdown

1. 用户名
2. 密码
3. UID
4. GID
5. 全名
6. home路径
7. shell工具

密码在影子文件：`cat /etc/shadow` <a name="GSM15"></a>

## /etc/shadow

wuya : $1$jX8wc27p$bW2rSGQLDCsX2Hz/uwNK70 : 19157 : 0 : 99999 : 7 : : :
WWW : ! ! : 19165 : 0 : 99999 : 7 : : :
mysql : !! : 19173 : : : : : :

1. 用户名
2. 密码
3. 最后修改时间(1970年1月1日以后的多少天)
4. 最小修改间隔时间
5. 密码有效期
6. 密码需要变更前的警告天数
7. 密码过期后的宽限天数
8. 账号失效时间
9. 保留 <a name="ZOqEA"></a>

### 密码格式

命令: openssl passwd -1 -salt admin 123456
格式: $id$salt$encrypted
示例: $1 $admin$LCIYcRe.ee8dQwgrFc5nz.

|  数字 |  加密方式 |
| --- | --- |
| 1 |  MD5 |
| 2a | Blowfish (某些Linux发行版) |
| 5 | SHA-256 |
| 6 | SHA-512 |

> 加密方式MD5 单向 哈希算法(摘要算法)
> 12345 : 6e10adc3949ba59abbe56e057f20f883e
> abcdef : 7ac66c0f148de9519b8bd264312c4d64
>
> 123456 + "wuya”
> 12wuya3456              salt 盐
>
> 81ca647915e06f3826abece86d3246d0

<a name="sR7kI"></a>

## etc/sudoers

格式:
wuya ALL=(ALL) ALL
kali ALL=(ALL) NOPASSWD: /bin/useradd

全拼: super user do
`sudo -l`
sudo command (要执行的命令)

<a name="LPyxE"></a>

### 解决没有编辑sudoers权限

使用`visudo`编辑权限 <a name="ae7mq"></a>

# 基本命令

|  操作 | 命令 |
| --- | --- |
| 查询用户账号身份标识 | id |
| 查询用户账号的登录属性 | finger |
| 查询当前主机的用户登录情况 | w、who |
| 查询系统当前在线的用户 | users |
| 查看用户 | whoami |
| 切换用户 | su |

<a name="W1MA7"></a>

# 用户和文件的关系

文件所有者:所属用户、所属组
访问权限: 读、写、执行

<a name="v0OCA"></a>

## 文件和目录归属

文件的拥有者
文件的所属组
全拼: change owner
`chown -R wuya /usr/local/soft`
`chown -R redis:redis /usr/local/soft/redis` <a name="TU5md"></a>

## 文件和目录权限

|  - | rw- --- ---. | 1   |  root |  root | 2750 Jun 14 14:53 | anaconda-ks.cfg |
| --- | --- | --- | --- | --- | --- | --- |
| d | rwx r-x r-x. | 2 |  root |  root | 6 Jun  14 06:55 | Desktop |

<a name="XQOnI"></a>

### 文件类型

> -
>
> d

| 符号 | 含义   |
| --- | --- |
| d | 目录文件(文件夹) |
| - | 普通文件 |
| l | 软链接. (类似Windows的快捷方式) |
| b | 块设备文件(例如硬盘、光驱等) |
| p | 管道文件 |
| c | 字符设备文件(例如屏幕等串口设备) |
| s | 套接口文 |

<a name="dS2Lv"></a>

### 用户类别

> rw- --- ---
> rwx r-x r-x

| 符号 | 单词 | 含义   |
| --- | --- | --- |
| u | user | 所属用户(的权限) |
| g | group | 所属组别(的权限) |
| o | other | 其他用户(的权限) |

<a name="OBJYN"></a>

### 权限类别

> rw- --- ---
> rwx r-x r-x

| 符号 | 单词 | 含义   | 对于文件 | 对于目录 |
| --- | --- | --- | --- | --- |
| r | read  | 可读 | 可以读取 | 可以浏览内容 |
| w | write | 可写 | 可以修改 | 可以删除、移动内容 |
| x | execute | 可执行 | 可以执行 | 可以进入目录 |
| - |  | 没有权限 |  |  |

<a name="PVtTS"></a>

### 权限类别

![image.png](../../../../assets/lw42v2iewcwx3u9y_gryd5v/1668393003649-1238fd56-fb4c-4253-9bed-f2da11d28f8b.png)

> d rwx rwx r-x. 2 alan security 6 Jul 7 06:08 test
> 775
> 7=4+2+1
> 5=4+1

例如：

|  数值 |  权限 |  拆开3段，每3位 | 计算 |
| --- | --- | --- | --- |
| 444 | r-- r-- r-- | r--和r--和r-- | 4+0+0=4，所以444 |
| 600 | rw- --- --- | rw-和---和--- | rw-等于4+2=6, --- 等于0, 所以是600 |
| 644 | rw- r-- r-- | rw-和r--和r-- | rw-等于4+2=6，r--等于4，所以是644 |
| 666 | rw- rw- rw- | rw-和rw-和rw- | rw-等于4+2=6,所以是666 |
| 700 | rwx --- --- | rwx和---和--- | rwx等于4+2+1=7，---等于0，所以是700 |
| 744 | rwx r-- r-- | rwx和r--和r-- | rwx等于4+2+1=7，r--等于4,所以是744 |
| 755 | rwx r-x r-x | rwx和r-x和r-x | rwx等于4+2+1=7，r-x等于4+1=5. 所以是755 |
| 777  | rwx rwx rwx | rwx和rwx和rwx | rwx等于4+2+1=7，所以是777 |

<a name="Nb53d"></a>

### 修改权限

\#添加组用户的写权限。全拼: change mode
`chmod g+w test.log`
\#删除其他用户的所有权限。
`chmod o= test.log`
\#使得所有用户都没有写权限。
`chmod a-w test.log`
\#当前用户具有所有权限，组用户有读写权限，其他用户只有读权限。
`chmod u=rwx, g=rw, o=r test.log`
\#等价的八进制数表示:
`chmod 764 test.log`
\#将目录以及目录下的文件都设置为所有用户拥有读写权限。
\#注意,使用'-R'选项一定要保留当前用户的执行和读取权限，否则会报错!
`chmod -R a=rw testdir/`
\#根据其他文件的权限设置文件权限。
`chmod --reference=1.log test.log`

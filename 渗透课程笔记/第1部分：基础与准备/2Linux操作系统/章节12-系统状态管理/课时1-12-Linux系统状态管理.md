---
title: 课时1-12-Linux系统状态管理
url: https://www.yuque.com/u29002979/ep2zrx/sz2bq1c30ov5kna7_unc00d
---

<a name="MluS0"></a>

# 课程大纲

1. 查看系统信息
2. 进程管理
3. 内存使用情况
4. 磁盘使用情况
5. 定时任务

<a name="ow2y5"></a>

# 查看系统信息

1.日期时间
`date`时间

    ┌──(root㉿guoyx)-[/home/kali]
    └─# date "+%Y-%m-%d %H:%M:%S"
    2022-11-14 01:18:46

`cal` 日历

    ┌──(root㉿guoyx)-[/home/kali]
    └─# cal
       November 2022      
    Su Mo Tu We Th Fr Sa  
           1  2  3  4  5  
     6  7  8  9 10 11 12  
    13 14 15 16 17 18 19  
    20 21 22 23 24 25 26  
    27 28 29 30     

`uptime` 开机启动多少时间

    ┌──(root㉿guoyx)-[/home/kali]
    └─# uptime
     01:21:49 up 18:42,  2 users,  load average: 0.00, 0.00, 0.00

`w`显示目前登入系统的用户信息

    ┌──(root㉿guoyx)-[/home/kali]
    └─# w
     01:22:04 up 18:42,  2 users,  load average: 0.00, 0.00, 0.00
    USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
    root     tty7     :0               Sun06   18:42m  2:02   2:02  /usr/lib/xorg/Xorg
    kali     pts/0    192.168.31.119   00:25    0.00s  0.45s  0.04s sshd: kali [priv]

2.系统版本
`cat /etc/redhat-release`

    [root@xuegod63 ~]# cat /etc/redhat-release
    CentOS Linux release 7.9.2009 (Core)

`uname -a`

    [root@xuegod63 ~]# uname -a
    Linux xuegod63.cn 3.10.0-1160.80.1.el7.x86_64 #1 SMP Tue Nov 8 15:48:59 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

`cat /proc/version`

    [root@xuegod63 ~]# cat /proc/version
    Linux version 3.10.0-1160.80.1.el7.x86_64 (mockbuild@kbuilder.bsys.centos.org) (gcc version 4.8.5 20150623 (Red Hat 4.8.5-44) (GCC) ) #1 SMP Tue Nov 8 15:48:59 UTC 2022

<a name="RRRQj"></a>

# 程序、进程、服务

1. 程序 program
2. 进程 process
3. 服务 service

`systemctl list-unit-files |grep mysql`
`cat /etc/services |grep mysql` <a name="LAUyq"></a>

## 运行程序

1. 前台运行 ./xxx
2. 后台运行 nohup ./xxx & <a name="GdKgK"></a>

## 查看进程top

![image.png](../../../../assets/sz2bq1c30ov5kna7_unc00d/1668408271232-cbf3da58-1d61-4a0e-a544-8a3a34e74022.png) <a name="kjRle"></a>

## ps

全拼: process status

|   选项 |    作用 |
| --- | --- |
| -a | 显示所有进程，包括其他用户的进程; |
| -u | 选择有效的用户id或者是用户名; |
| -x | 显示没有控制终端的进程，同时显示各个命令的具体路径 |
| -e | 显示所有的进程，和-A的效果一样; |
| -f | 显示更完整;通常与-e一起用; |

<a name="MlmKr"></a>

### ps -ef

![image.png](../../../../assets/sz2bq1c30ov5kna7_unc00d/1668408710813-5942bcd8-dddb-4dc3-8cad-8f19ffd19424.png)
`ps -ef | grep mysql` <a name="rOLJH"></a>

### ps -aux

![image.png](../../../../assets/sz2bq1c30ov5kna7_unc00d/1668408800532-c65b9d5e-8abf-4f92-bc34-db6fda345c17.png) <a name="PqMmO"></a>

### pstree

`pstree -p`
`pstree mysql`
`pstree -p | grep ssh`

<a name="nCr8d"></a>

## 服务管理

systemctl

|  命令 |  作用 |
| --- | --- |
| systemctl status * .service | 查看所有服务状态 |
| systemctl start mysqld.service | 启动服务 |
| systemctl restart mysqld.service | 重启服务 |
| systemctl stop mysqld.service | 停止服务 |
| systemctl enable mysqld.service | 开机启动服务 |
| systemctl disable mysqld.service | 停止开机启动 |

<a name="j1On7"></a>

### systemctl和service

| daemon命令 | systemctl命令 |
| --- | --- |
| service \[服务] start | systemctl start \[unit type] |
| service \[服务] stop | systemctl stop \[unit type] |
| service \[服务] restart | systemctl restart \[unit type] |

<a name="Bn7VN"></a>

## 停止程序

| 信号量 | 含义 | 服务停止 |
| --- | --- | --- |
| 0 | EXIT | 程序退出时收到该信息 |
| 1 | HUP | 挂掉电话线或终端连接的挂起信号，这个信号也会造成某些进程在没有终止的情况下重新初始化 |
| 2 | INT | 表示结束进程，但并不是强制性的，常用的"Ctrl+C"组合键发出就是一个kill -2的信号 |
| 3 | QUIT | 退出 |
| 9 | KILL | 杀死进程，即强制结束进程 |
| 11 | SEGV | 段错误 |
| 15 | TERM | 正常结束进程，是kill命令的默认信号 |

`kill -9` <a name="ewrNN"></a>

# free显示内存的使用情况

`free`显示内存的使用情况
`free -h`可视化
`free -m`以单位兆显示
![image.png](../../../../assets/sz2bq1c30ov5kna7_unc00d/1668412759111-ef739fe3-2bc3-41a5-8859-a9c4e80bdee8.png)

<a name="BAnsX"></a>

# 磁盘使用情况

`du`
全拼: disk usage

|  命令 |  作用 |
| --- | --- |
| du /usr | 显示使用情况 |
| du -h /usr | --human-readable用恰当的单位 |
| du -h /root --max-depth=1 | 加上层级限制 |
| du -h --max-depth=1 | sort -hr | 降序排列 |
| du -ah /root | sort-hr | head -n 3 | 前三个大文件 |
| du -ah --exclude="*/.*" . | 排除隐藏目录 |
| du -kt 10M ./* | 找出10M以上的文件 |

<a name="el8iA"></a>

## 综合命令 sar

全拼: system activity reporter

    [root@xuegod63 ~]# sar
    Linux 3.10.0-1160.80.1.el7.x86_64 (xuegod63.cn) 	2022年11月14日 	_x86_64_	(4 CPU)

    09时49分56秒       LINUX RESTART

    09时50分02秒     CPU     %user     %nice   %system   %iowait    %steal     %idle
    10时00分01秒     all      0.69      0.12      1.39      0.10      0.00     97.71
    10时10分01秒     all      0.12      0.00      0.25      0.01      0.00     99.63
    10时20分01秒     all      0.12      0.00      0.24      0.00      0.00     99.64
    10时30分01秒     all      0.11      0.00      0.28      0.01      0.00     99.60
    10时40分01秒     all      0.11      0.00      0.24      0.00      0.00     99.65
    10时50分01秒     all      0.12      0.00      0.24      0.01      0.00     99.64
    11时00分01秒     all      0.12      0.00      0.25      0.00      0.00     99.62

`%user`: 用于表示用户模式下消耗的CPU时间的比例;
`%nice`: 通过nice改变了进程调度优先级的进程，在用户模式下消耗的CPU时间的比例;&#x20;
`%system`: 系统模式下消耗的CPU时间的比例;
`%iowait`: CPU等待磁盘I/O导致空闲状态消耗的时间比例;
`%steal`: 利用Xen等操作系统虚拟化技术，等待其它虚拟CPU计算占用的时间比例;
`%idle`: CPU空闲时间比例。

<a name="modlG"></a>

# 定时任务

工具: crontab
全拼: cron table
Cron表达式:
<https://tool.lu/crontab>
`cat /etc/crontab` <a name="zTgOu"></a>

## crontab命令

|  命令 |  作用 |
| --- | --- |
| crontab -u root -r | 删除任务remove |
| crontab -u root time.cron | 把文件添加到某个用户的任务 |
| crontab -u root -l | 列举任务list |
| crontab -u root -e  | 编辑任务edit |

示例脚本:&#x20;
`test.cron` 输出wuya666
`time.cron` 打印时间 <a name="KGhMr"></a>

## 定时任务文件

|  命令 |  作用 |
| --- | --- |
| /etc/crontab | 管理文件 |
| /var/spool/cron/ | 每个用户包括root的crontab任务 |
| /etc/cron.d/ | 存放任何要执行的crontab文件或脚本 |

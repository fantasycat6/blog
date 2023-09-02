---
title: 课时1-9-Linux软件安装
url: https://www.yuque.com/u29002979/ep2zrx/rg0srpt8awh6bd6g_apfedo
---

<a name="ChzHU"></a>

## 课程大纲

1. 软件为什么需要安装
2. 脚本和程序的区别
3. Linux安装软件的几种方式
4. CentOS安装软件案例
5. Linux软件版本管理 <a name="sTB8S"></a>

# Windows软件安装流程

1. 安装检查
2. 释放文件
3. 复制可执行文件
4. DLL动态链接库/安装服务
5. 注册表
6. 开始菜单和快捷方式 <a name="csbUM"></a>

## Windows安装文件

.msi
.exe <a name="ROeDQ"></a>

## Windows可执行程序

.exe

<a name="XNzGp"></a>

# Linux可执行程序

/bin
/sbin
/usr/bin
/usr/sbin <a name="GwsH5"></a>

## 脚本和程序的区别

不需要编译的: Javascript、 Python、 Ruby.
需要编译的: C、C++、Swift、 Kotlin、 Go.

解释型:边解释边执行
编译型:计算机可以直接执行

<a name="zJQgj"></a>

# Linux软件常见安装方式

源码编译(make)、rpm、deb、yum、apt、Docker......

<a name="v68Oc"></a>

## Linux主要派系

|  主要派系 |  Linux发型版 |  主要安装方式 |
| --- | --- | --- |
| Redhat红帽派系 | Redhat、CentOS、 Fedora等 | make、rpm、 yum、dnf |
| Debian派系 | Kali、Ubuntu等 | deb、apt、 dpkg  |
| FreeBSD系 | FreeBSD | make、pkg、 ports |

<a name="qdlUB"></a>

### Redhat系

<a name="CzrmI"></a>

#### 源码安装

下载源代码安装包文件

- 步骤1: tar包解压缩

用途:解压并释放源代码包到指定的目录

- 步骤2/configure配置

用途:设置安装目录、安装模块等选项

- 步骤3:make编译

用途:生成可执行的二进制文件

- 步骤4: make install

用途:复制二进制文件到系统，配置环境

配置并使用软件 <a name="VGVOU"></a>

#### rpm安装

RedHat Package Manager 软件包管理工具 <a name="zFHfU"></a>

##### rpm选项

|  操作 |  命令 |  说明 |
| --- | --- | --- |
| 查询 | rpm -qa
rpm -q 包名 | q: query |
| 安装 | rpm -ivh 包名 | i: install 安装
v: verbose 详细
h: hash 哈希 |
| 升级 | rpm -Uvh 包名 | U:安装或升级最新版 |
| 卸载 | rpm -e 包名 | 需要先卸载依赖其的软件 |

<a name="z8SWP"></a>

#### yum安装

YUM (Yellow dog Updater, Modified)

<a name="JsgZk"></a>

##### yum操作和选项

|  操作 |  命令 |
| --- | --- |
| 列表 | yum list
yum list 包名 |
| 搜索 | yum search 包名 |
| 安装 | yum install 包名 |
| 升级 | yum update 包名 |
| 卸载 | yum remove 包名 |
| 更新所有软件 | yum update |
| 清除缓存 | yum clean all |
| 更新yum缓存 | yum make cache |

|  操作 |  命令 |
| --- | --- |
| -h | 显示帮助信息 |
| -y | 对所有的提问都回答"yes" |
| -c | 指定配置文件 |
| -q | 安静模式 |
| -v | 详细模式 |

<a name="ao8sV"></a>

##### DNF和YUM的区别

DNF (Dandified YUM)

| 区别 | DNF | YUM |
| --- | --- | --- |
| 解析依赖关系 | 使用Libsolv | 使用公开的API |
| API | 有完整的API文档，能很容易地创建新功能 | 没有完整文档，创建新功能困难 |
| 开发语言 | C、C++、Python编写 | 只用Ptyhon编写 |
| 使用范围 | Fedora、RHEL 8、CentOS8、OEL 8、Mageia 6/7 | RHEL 6/7、CentOS 6/7、OEL 6/7 |
| 扩展的支持 | 支持各种扩展 | 只支持基于Python的扩展 |
| 同步元数据 | 占用内存少 | 占用较多内存 |
| 更新 | 包中包含不相关的依赖，则不会更新 | 在没有验证的情况下更新软件包 |
| 存储库不可用 | DNF将跳过它，并继续使用可用的存储库处理事务 | YUM会立即停止 |
| 内核包的保护 | DNF不提供，可以删除内核包 | 不允许你删除运行中的内核 |

<a name="bPNfV"></a>

### Debian系

Deb包安装
apt安装

|  操作 |  命令 |
| --- | --- |
| 搜索 | apt search 包名 |
| 安装 | apt install 包名 |
| 升级 | apt update 包名 |
| 卸载 | apt remove 包名 |

<a name="DKDQ1"></a>

### FreeBSD系

package
ports

|  操作 |  命令 |
| --- | --- |
| 搜索 | pkg search 包名 |
| 安装 | pkg install 包名 |
| 升级 | pkg upgrade 包名 |
| 卸载 | pkg del 包名 |

<a name="UBaPW"></a>

# Linux软件安装方式案例

<a name="YfyzB"></a>

## CentOS启用中文输入法:

<https://blog.csdn.net/qq_30273575/article/details/125097771> <a name="ehWZc"></a>

## CentOS yum安装MySQL:

<https://blog.csdn.net/weixin_44436964/article/details/123845958> <a name="Aup3A"></a>

### 一、卸载MYSQL

<a name="cQsmE"></a>

#### 1.先确认创建的CentOS中是否含有其他软件包

    rpm -qa | grep mysql 查mysql相关软件包
    rpm -e xxx  卸载查询的软件包

问题：出现已另存的警告时，将另存的单独删除，删除语法：&#x20;
`rm-f /etc/my.cnf.rpmsave` <a name="FC0hi"></a>

#### 2.删除相关的文件和目录

    find / -name mysql 查询文件或目录 
    rm -rf xxx 删除相关文件或目录 

<a name="mDAPs"></a>

#### 3.清楚rpm缓存

    yum clean all  清理本地缓存

<a name="EKPR5"></a>

### 二、mysql部署

<a name="GXM3J"></a>

#### 1. mysql安装

    1.下载mysql安装源文件
    wget 'https://dev.mysql.com/get/mysql57-community-release-el7-11.noarch.rpm'
    2.安装mysql的yum源文件
    rpm -Uvh mysql57-community-release-el7-11.noarch.rpm
    3.安装mysql
    yum -y install mysql-community-server
    4.启动mysql服务
    systemctl start mysqld
    5.添加MySQL服务到开机启动
    systemctl enable mysqld

问题：安装第三步时报错密钥不匹配
解决：打开`/etc/yum.repos.d/mysql-community.repo`,更改对应版本的`gpgcheck=0` <a name="AjHCi"></a>

#### 2.修改mysql默认的密码

    1. 查看源码安装的MySQL的密码
    grep 'temporary password' /var/log/mysqld.log
    2. 在Linux下登录mysql服务器
    mysql -uroot -p上一步的临时密码,有特殊字符时需采用复制粘贴的方式
    3. 设置mysql数据密码策略
    set global validate_password_policy=0;
    set global validate_password_length=1;
    4. 修改数据库密码
    set password for root@localhost = password('123456');

<a name="EBUvI"></a>

#### 3.修改mysql远程连接的权限

    1. 切换到mysql库
    use mysql;
    2. 查看主机及用户信息
    select host,user from user;
    3. 赋予任何主机访问数据的权限
    grant all privileges on *.* to 'root'@'%' identified by 'AbCd@123456' with grant option;
    4. 刷新权限使其生效
    flush privileges;

查询3306端口是否开放
`firewall-cmd --query-port=3306/tcp`
\# 开放3306端口
`firewall-cmd --permanent --add-port=3306/tcp`
`firewall-cmd --permanent --add-port=3300-3310/tcp`
\# 移除端口
`firewall-cmd --permanent --remove-port=3306/tcp`
查看防火墙的开放的端口 :
`firewall-cmd --permanent --list-ports`
重启防火墙
`firewall-cmd --reload`
=======================

<a name="b2OC0"></a>

### Linux命令搜索引擎命令搭建

<https://github.com/jaywcjlove/linux-command> <a name="PrCAz"></a>

#### 先安装Docker

    apt install docker.io
    apt install podman-docker

<a name="JuI7z"></a>

#### 通过Docker安装

轻松通过 docker 部署 linux-command 网站。

    docker pull wcjiang/linux-command 
    # Or 
    docker pull ghcr.io/jaywcjlove/linux-command:latest

<!---->

    docker run --name linux-command --rm -d -p 9665:3000 wcjiang/linux-command:latest 
    # Or 
    docker run --name linux-command -itd -p 9665:3000 wcjiang/linux-command:latest 
    # Or 
    docker run --name linux-command -itd -p 9665:3000 ghcr.io/jaywcjlove/linux-command:latest

<a name="qQQET"></a>

#### 在浏览器中访问以下 URL

**http://localhost:9665/**
`http://192.168.31.76:9665`

<a name="xKMMh"></a>

# 软件版本管理

<a name="IHHxG"></a>

## update-alternatives

- 查看:

<!---->

    update- alternatives --display java

- 添加:

<!---->

    alternatives --install /usr/bin/java java /usr/local/jdk-11.0.2/bin/java 3

`/usr/bin/java`: 注册地址，软链
`java`:服务名
`/usr/local/jdk-11.0.2/bin/java`:实际程序路径
`3`:优先级

- 切换:

<!---->

    update-alternatives --config java 

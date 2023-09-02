---
title: 课时1-11-Linux网络管理
url: https://www.yuque.com/u29002979/ep2zrx/ot9vxkilc1d75ugu_ye6ggz
---

<a name="laSCY"></a>

# 课程大纲

1. 网络基本概念
2. 网络配置文件
3. 查看及配置网络
4. 连通性探测
5. 查看网络连接
6. 域名相关
7. 下载传输 <a name="UZI59"></a>

# 物理地址/逻辑地址

- 网卡
- MAC地址(Media Access Control)媒体访问控制

物理地址；厂家分配

- IP (Internet Protocal Address)互联网协议地址

逻辑地址；可变；分私有和公有
192.168.142.132
47.106.11.166 <a name="EnK2X"></a>

## 公有私有

局域网——使用私有 IP地址
互联网——使用公有 IP地址

|  公有IP地址的范围 |  私有IP地址的范围 |
| --- | --- |
| A类的公有IP:
1.0.0.0 - 9.255.255.255
11.0.0.0 - 126.255.255.255 | A类私有IP地址:
10.0.0.0-10.255.255.255 |
| B类的公有IP:
128.0.0.0-172.15.255.255
172.32.0.0-191.255.255.255  | B类私有IP地址:
172.16.0.0-172.31.255.255  |
| C类的公有IP:
192.0.0.0-192.168.255.255
192.168.0.0-233.255.255.255 | C类私有IP地址:
192.168.0.0-192.168.255.255 |

<a name="Te0uP"></a>

## NAT

NAT: Network Address Translation,网络地址转换
![image.png](../../../../assets/ot9vxkilc1d75ugu_ye6ggz/1668397723880-0514e2a8-ab5f-43dd-940e-73f6eae9e0eb.png)

<a name="AkRVV"></a>

## IPv4、IPv6

![image.png](../../../../assets/ot9vxkilc1d75ugu_ye6ggz/1668398175237-5cb6fc6f-3fb3-4e73-8f03-90285b1e061c.png)
<https://tool.520101.com/wangluo/ipjisuan/>

IPv4: 4个8位二进制，2^32=全部约42亿， 实际可用约25亿 <a name="LMduZ"></a>

### 公网IP地址的分配

NIC (Network Information Center)分配
ISP (网络业务提供商)、网络基础设施提供商

全中国一共有多少iP地址?
<https://www.eet-china.com/mp/a95961.html>

IPv6是128位的，一共有2的128次方个 <a name="v70By"></a>

### 动态、静态IP

DCHP (Dynamic Host Configuration Protocol)动态
static静态

<a name="ZR77L"></a>

### 127.0.0.1

环回地址(loop back)
可以ping通代表网卡安装正常 <a name="o1RaU"></a>

## 端口port

作用:区分程序
范围: 0-65535
系统端口，0到1023
用户端口，也称为注册端口，1024-49151
动态端口，也称为私有或临时端口，49152-65535 <a name="Z6NxG"></a>

## 域名Domain Name

作用:替代IP,方便识记
域名如何转换为IP: Domain Name System-DNS
域名:与IP的数量关系:多对一

localhost 域名指向环回地址127.0.0.1

> \--http:// WWW. baidu. com:80 IP Apache
> https: //WWW. baidu. com: 443
> http协议的域名可省80，
> https协议的域名可省443；
> http:// WWW. baidu. com:8080

<a name="uufcp"></a>

### Dns服务器地址

114.114.114.114 国内三大运营商提供
8.8.8.8 谷歌公司提供

例如：
fofa.so 域名被封了，但ip不受影响
改成fofa.info

<a name="nUdCT"></a>

### 子域名

www.baidu.com
map.baidu.com
news.baidu.com

bss.wuya.com 同一个IP 子目录 /wwwroot/bbs
blog.wuya.com 同一个IP 子目录 /wwwroot/blog
talk .wuya.com 同一个IP 子目录 /wwwroot/talk

<a name="e6rtS"></a>

# 网络配置文件

|  文件 |  作用 |
| --- | --- |
| /etc/sysconfig/network-scripts/ifcfg-ens33 | 网卡配置文件 |
| /etc/sysconfig/network-scripts/ifcfg-lo | 环回地址配置文件 |
| /etc/hosts | 主机名与IP的映射 |
| /etc/resolv.conf | DNS配置，由ens33自动覆盖 |

<a name="ZAcJX"></a>

# 查看及配置网络

<a name="VXCMW"></a>

## ifconfig

全拼: network interfaces configuring
位于net-tools工具包
可以动态配置网络参数
其他选项参数: <https://www.linuxcool.com/>

<a name="D7aMr"></a>

## ifconfig和ip

![image.png](../../../../assets/ot9vxkilc1d75ugu_ye6ggz/1668402998435-d63f3f64-51ea-41da-9725-8293a090d92e.png)

<a name="fP7kM"></a>

## ip

位于iproute工具包
添加设备、启动停止网络设备、设置IP、 设置网关......
其他选项参数: <https://www.linuxcool.com/>

<a name="Y9apQ"></a>

# 连通性探测

<a name="xYpLE"></a>

## ping

全拼: Packet Internet Groper,因特网包探索器
ping baidu.com
ping 192.168.142.151 <a name="uZXBt"></a>

## telnet

远程登录
telnet bbs.newsmth.net

探测端口
telnet 192.168.142.132 80
telnet 192.168.142.132 22 <a name="aNbUg"></a>

# 查看网络连接

<a name="Vc71s"></a>

## netstat (ss)

全拼: network statistics

查看程序的网络连接情况:
netstat -ap | grep ssh

查看端口的网络连接情况:
netstat -ap | grep 3306

<a name="NFwvh"></a>

# 域名相关

**nslookup**
`nslookup baidu.com`
A记录: IP地址
CNAME:域名别名
MX:邮件服务器

**dig (domain information groper)**
`dig baidu.com`
`dig www.xtu.edu.cn A +noall + answer`
`dig www.xtu.edu.cn MX + noall + answer`
`dig www.xtu.edu.cn NS + noall + answer`

**host**
`host baidu.com`
`host -t MX www.baidu.com`

    ┌──(root㉿guoyx)-[/home/kali]
    └─# host -t MX www.baidu.com
    www.baidu.com is an alias for www.a.shifen.com.

<a name="yD04Y"></a>

# 下载传输

<a name="uvETu"></a>

## 常规方式

Xshell拖曳——上传
xftp——双向，或者Filezilla、 FlashFTP
sz file name——下载
rz——上传
vmtools拖动——传入
QQ——双向 <a name="jAI0x"></a>

## wget

> wget https://download.redis.io/releases/redis-6.0.9.tar.gz

`wget -O`改名字

> wget -O redis.tar.gz https://download.redis.io/releases/redis-6.0.9.tar.gz

`wget -c `断点续传
`wget -b` 后台下载
`wget -i `filelist.txt 同时下载多个
`tail -f wget-log` 查看下载进度

<a name="SD8bn"></a>

## scp

全拼: Secure Copy
`scp 1.txt root@192.168.142.66:/tmp`
`scp -r folder root@192.168.142.66:/tmp`

<a name="RArG6"></a>

## curl

全拼: Client URL
`curl https://www.baidu.com > page.html`
`curl -X POST -d 'a=1&b= nihao' URL`
`curl -H "Content- Type: application/json" -X POST -d '{" abc":123,"bcd":"nihao"}' URL`

<a name="l6Syi"></a>

# 防火墙Firewall

<a name="CQa2j"></a>

## iptables工具

- 启动防火墙

`systemctl start firewalld`

- 查看已开放的端口

`firewall-cmd --list-ports`

- 开启80端口

`firewall-cmd --zone = public --add-port= 80/tcp --permanent`

- 重启防火墙

`firewall-cmd --reload`

- 停止防火墙

`systemctl stop firewalld.service`

- 禁止防火墙开机启动

`systemctl disable firewalld.service`

- 删除规则

`firewall-cmd --zone=public --remove-port= 80/tcp --permanent`

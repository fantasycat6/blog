# WPA渗透-pyrit：GPU加速_Hash-table

## 1.pyrit工具介绍

pyrit是一款开源且完全免费的软件，任何人都可以检查，复制或修改它。它在各种平台上编译和执行，包括FreeBSD、MacOS X和Linux作为操作系统以及x86、alpha、arm等处理器。

使用pyrit工具最大的优点，在于它可以使用除CPU之外的GPU运算加速生成彩虹表，本身支持抓包获取四步握手过程，无须使用airodump抓包，如果已经通过ariodump抓取数据，也可以使用pyrit进行读取。

## 2.安装pyrit

1.修改更新源

```
vim /etc/apt/sources.list

deb http://mirrors.ustc.edu.cn/debian/ buster main contrib non-free
deb http://mirrors.ustc.edu.cn/debian/ buster-updates main contrib non-free
deb http://mirrors.ustc.edu.cn/debian/ buster-backports main contrib non-free
deb http://mirrors.ustc.edu.cn/debian-security buster/updates main contrib non-free
```

2.更新安装源

`apt-get update && apt-get upgrade`

3.下载pyrit

`apt-get install pyrit`

![image.png](https://image.201068.xyz/assets/4919430750de4c8290143fbca1cb8e75.png)

## 3.安装scapy到指定目录步骤

1、下载scapy：

`wget -v https://github.com/secdev/scapy/archive/v2.3.2.tar.gz`

或者将附件里的scapy-2.3.2.tar.gz拷贝到kali

2、解压后进入目录执行：

```
tar -xzvf tar -xzvf scapy-2.3.2.tar.gz
cd scapy-2.3.2 
python2 setup.py build
```

3.安装

`python2 setup.py install`

![image.png](https://image.201068.xyz/assets/2327d8c42b754d94aca354023bb40144.png)

## 4.渗透wifi

1.分析握手包信息

```
pyrit -r cap包 analyze
-r：pcap格式的数据包捕获源
analyze：分析数据包捕获文件

pyrit -r wpa-1-01.cap analyze
```

![image.png](https://image.201068.xyz/assets/20c48a2d1b754004a62b09bd410b92e9.png)

2.密码字典渗透WiFi

```
pyrit -r 握手包 -i 字典 -b bssid attack_passthrough
-i：输入的文件名
-b：按BSSID筛选AccessPoint
attack_passthrough：用文件中的密码攻击握手

pyrit -r wpa-1-01.cap -i /root/wifi/pwd.txt -b d8:24:bd:79:18:0b attack_passthrough
```

![image.png](https://image.201068.xyz/assets/b3e8a66de47e4b42b7aefa54b1bd8b81.png)

3.hash-table加速渗透wifi

```
pyrit -r 握手包 -i 哈希列表 -b bssid attack_cowpatty
attack_cowpatty：攻击一个来自cowpatty文件的PMK握手

pyrit -r wpa-1-01.cap -i /root/wifi/pwdhash -b d8:24:bd:79:18:0b attack_cowpatty
```

![image.png](https://image.201068.xyz/assets/7ac4842f07af45edb5f292983a01215a.png)
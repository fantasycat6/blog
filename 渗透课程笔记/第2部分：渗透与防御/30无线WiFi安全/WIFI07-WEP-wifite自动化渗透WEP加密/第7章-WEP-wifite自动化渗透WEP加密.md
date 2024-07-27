# WIFI07-WEP-wifite自动化渗透WEP加密

## 1.wifite介绍

wifite是一款自动化wep、wpa以及wps破解工具，不支持windows和osx。wifite的特点是可以同时攻击多个采用wep和wpa加密的网络。wifite只需简单的配置即可自动化运行，期间无需人工干预。 目前支持任何linux发行版、Backtrack 5 R1, BlackBuntu, BackBox, Kali(默认自带), CDLinux等。

wifite 破解wep加密wifi时，会采用很多种攻击方式，比如说chopchop攻击，fake欺骗认证码等等，不一定会采用哪个方式破解。不一定能一次性成功。

## 2.扫描介绍

### 1.扫描无线网络

```
wifite
```

### 2.停止wifi扫描

```
ctrl+c
```

### 3.扫描某个信道

```
wifite -c 1
-c:信道扫描目标
```

### 4.扫描wep加密类型的wifi

```
wifite  -wep
-wep  只针对WEP网络 
```

## 3.破解步骤

注意：学习时，需要提前在AP上连接一个STA，破解成功率比较高

### 1.扫描wep加密类型的wifi

```
wifite  -wep
-wep  只针对WEP网络 
```

### 2.停止wifi扫描

```
ctrl+c
```

### 3.选择要破解的AP

```
输入wifi扫描结果前的序号
 1                cisco-1809     1  WEP   68db    no    1
```

![image-20211125131923614](https://image.201068.xyz/assets/image-20211125131923614.png)

### 4.等待ivs变多后，自动尝试破解

![image-20211125132227530](https://image.201068.xyz/assets/image-20211125132227530.png)

![image-20211127061713174](https://image.201068.xyz/assets/image-20211127061713174.png)

## 4.课堂小结

参考：课后笔记


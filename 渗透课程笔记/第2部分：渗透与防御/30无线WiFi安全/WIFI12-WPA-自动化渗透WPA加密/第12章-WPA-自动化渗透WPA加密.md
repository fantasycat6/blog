# WPA-自动化渗透WPA加密

## 1.开启监听模式

```
airmon-ng start wlan0
```

## 2.指定密码破解

```
wifite --dict /root/wifi/passwd.txt
--dict:指定密码字典
```

## 3.等待扫描到WiFi，停止扫描

```
ctrl+c
```

![image-20211215151002895](https://image.201068.xyz/assets/image-20211215151002895.png)

## 4.选择WiFi序号开始扫描

![image-20211215151021987](https://image.201068.xyz/assets/image-20211215151021987.png)

## 5.指定密码大字典破解

```
wifite --dict /root/wifi/pwd.txt
```


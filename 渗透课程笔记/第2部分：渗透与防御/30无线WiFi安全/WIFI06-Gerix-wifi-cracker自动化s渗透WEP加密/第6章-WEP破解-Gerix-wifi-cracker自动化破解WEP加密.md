# WEP破解-Gerix-wifi-cracker自动化破解WEP加密

## **1.环境准备**

### 1.软件和kali

Kali-Linux-2019.2-vmware-amd64

gerix-wifi-cracker-2

为什么不用2021版本的呢？因为gerix-wifi-cracker-2是基于PyQt4界面工具包开发的软件，2021版本自带的是PyQt5，版本不兼容

### 2.下载软件，下载地址

```
https://github.com/J4r3tt/gerix-wifi-cracker-2
```

### 3.将软件复制到kali，解压

![image-20211118104925897](https://img.gyxnb.top/img/image-20211118104925897.png)



### 4.进入软件目录

```
cd gerix-wifi-cracker-2-master
```

## 2.破解步骤

### 1.启动gerix-wifi-cracker-2-master软件

```
python gerix.py
```

### 2.设置无线网卡位Monitor Mode模式

![image-20211118105038014](https://img.gyxnb.top/img/image-20211118105038014.png)

### 3.重新扫描网络

![image-20211118105100800](https://img.gyxnb.top/img/image-20211118105100800.png)

### 4.选择需要破解的WIFI

![image-20211118105121104](https://img.gyxnb.top/img/image-20211118105121104.png)

### 5.选择顶部【wep】，选择具体的破解方式【General functionalities】

![image-20211118105142221](https://img.gyxnb.top/img/image-20211118105142221.png)

### 6.点击【Start Sniffing and Logging】开始抓包

![image-20211118105204838](https://img.gyxnb.top/img/image-20211118105204838.png)

![image-20211118105218563](https://img.gyxnb.top/img/image-20211118105218563.png)

### 7.连接一个客户端，使其发生ARP通讯

### 8.在客户端发送ping命令加快数据包收集（模拟用户上网数据）

```
ping /t  192.168.1.1
```

### 9.使用python脚本加快收集速度（模拟用户上网数据）

```
import os
import threading
import time

class myThread (threading.Thread):
    def __init__(self):
        threading.Thread.__init__(self)
    def run(self):
        cmd="ping /t 192.168.1.1"
        os.system(cmd)
        time.sleep(0.1)

threads=[]

for i in range(50):
    thread1 = myThread()
    thread1.start()
    threads.append(thread1)


for item in threads:
    item.join()


print ("退出主线程")
```

### 10.等待Date到达5000时，可以开始破解

![image-20211118105254947](https://img.gyxnb.top/img/image-20211118105254947.png)

### 11.选择顶部【Cracking】--点击【Aircrack-ng-Decrypt WEP password】开始破解

![image-20211118122314228](https://img.gyxnb.top/img/image-20211118122314228.png)



### 12.抓包文件存放在： /root/.gerix-wifi-cracker

```
cd /root/.gerix-wifi-cracker
ls
```

### 13.清空抓包结果

```
cd /root/.gerix-wifi-cracker
rm *
```

## 3.课后小结

参考：课后笔记


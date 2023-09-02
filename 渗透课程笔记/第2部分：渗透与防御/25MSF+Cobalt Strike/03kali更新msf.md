登录kali

# 1 打开终端获取root权限

```
获取root权限 
可以在终端 输入 sudo su  
然后输入登录密码获取root权限
```

# 2 开始更新

## 换国内源

首先先添加更新源

进入 etc/apt/   目录

打开 sources.list   需要使用root权限执行

`vim /etc/apt/sources.list`

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1985/1639970340000/777269e6dc9143718ac9080d4650d0c7.png)

```
#中科大源
deb http://mirrors.ustc.edu.cn/kali kali-rolling main non-free contrib 
deb-src http://mirrors.ustc.edu.cn/kali kali-rolling main non-free contrib 

#阿里云kali更新源
deb http://mirrors.aliyun.com/kali kali-rolling main non-free contrib 
deb-src http://mirrors.aliyun.com/kali kali-rolling main non-free contrib

#清华大学源
deb http://mirrors.tuna.tsinghua.edu.cn/kali kali-rolling main contrib non-free
deb-src https://mirrors.tuna.tsinghua.edu.cn/kali kali-rolling main contrib non-free

#浙大源
deb http://mirrors.zju.edu.cn/kali kali-rolling main contrib non-free
deb-src http://mirrors.zju.edu.cn/kali kali-rolling main contrib non-free

#东软大学源
deb http://mirrors.neusoft.edu.cn/kali kali-rolling/main non-free contrib
deb-src http://mirrors.neusoft.edu.cn/kali kali-rolling/main non-free contrib

#网易Kali源 
deb http://mirrors.163.com/debian wheezy main non-free contrib 
deb-src http://mirrors.163.com/debian wheezy main non-free contrib deb
```

​     

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1985/1639970340000/c9eeca42087541a09f20a8078d8064c7.png)

## 更新软件列表

```shell
apt-get update  #更新软件列表
apt-get upgrade  #更新软件
apt-get dist-upgrade  #升级
apt-get clean  #删除缓存包
apt-get autoclean  #删除未安装的deb包
```

## 更新metasploit

`apt-get install metasploit-framework`

# 3 如果更新时显示update无效的错误！

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1985/1639970340000/dea81b359ad14271b35fbc7db0609126.png)

输入下面几个命令修复

```
wget -q -O - https://archive.kali.org/archive-key.asc | apt-key add 
apt-get clean 
apt-get update
```

4 如果报：E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

`apt --fix-broken install`             
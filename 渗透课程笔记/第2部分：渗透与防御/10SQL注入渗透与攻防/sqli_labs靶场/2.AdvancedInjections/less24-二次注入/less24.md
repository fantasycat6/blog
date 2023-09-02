---
title: less24
url: https://www.yuque.com/u29002979/ep2zrx/ni93xt8pwhh5ruwc
---

<a name="Zvqbq"></a>

# 二次注入

```bash
$sql = "insert into users ( username, password) values(\"$username\", \"$pass\")";

$sql = "UPDATE users SET PASSWORD='$pass' where username='$username' and password='$curr_pass' ";
```

> **二次注入**：二次注入是存储型注入。
> 可以理解为构造恶意数据存储在数据库后，恶意数据被读取并进入到了SQL查询语句所导致的注入。
> 恶意数据插入到数据库时被处理的数据又被还原并存储在数据库中，
> 当Web程序调用存储在数据库中的恶意数据并执行SQL查询时，就发生了SQL二次注入。

比如输入了admin' #，网站则会将'和#转义后进行SQL查询，
但是最后存入数据库中的结果仍然是admin' #（并没有转义存储）。

> 简言之就是将脏数据进行简单过滤后开发者就认为该数据可信便存入数据库中，
> 当下一次调用该数据时，该数据就会拼接到其他查询语句中造成注入。

![image.png](../../assets/ni93xt8pwhh5ruwc/1668606367726-3c955835-31b2-4e4c-bbce-4a10e4212514.png) <a name="tu84T"></a>

## 注册

首先注册一个新的账号，然后登录该账号&#x20;
![image.png](../../assets/ni93xt8pwhh5ruwc/1668650181397-1d948aa0-e337-454b-8c7e-f3988e2dae40.png)
然后登录该账号&#x20;
![image.png](../../assets/ni93xt8pwhh5ruwc/1668651240933-a972cf98-6d8b-451b-88d8-1994838d73a2.png)
`**admin'-- +**` <a name="HPMiU"></a>

## 登录修改密码

登录之后，修改密码，
该修改密码功能的语句变为

```bash
UPDATE users SET PASSWORD='$pass' where username='admin'-- +'and password='$curr_pass'
```

那么真正奏效的语句则是

```bash
UPDATE users SET PASSWORD='$pass' WHERE username='admin'
```

这时候我们就是在进行越权改变管理员的密码，
从数据库中抽出我们注册的新账户，用该账户越权修改 管理员的密码 &#x20;
![image.png](../../assets/ni93xt8pwhh5ruwc/1668651533559-bc5112bd-3656-49d1-af60-a80f5a8b4cb0.png)
将密码改为**1234**，

> Password successfully updated

然后用管理员的账户，登录密码1234 &#x20;
![image.png](../../assets/ni93xt8pwhh5ruwc/1668651459102-54e393e7-5449-4f4c-acb4-a55b8fbcd7f8.png)
&#x20;管理员账户登录成功

![](./../../asset/1.png)






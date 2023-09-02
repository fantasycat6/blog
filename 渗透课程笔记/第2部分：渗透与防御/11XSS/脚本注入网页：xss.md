# 案例

## 案例一
http://192.168.31.193:8082/reflect.html 
**POST请求** 
payload:

```html
<script>alert(1)</script>
```



---
## 案例二

http://192.168.31.193:8082/get.html 
get请求 
payload:

```shell
?url=javascript:alert(/wuya/)
```





---

# 定义

 恶意攻击者利用web页面的漏洞，插入一些恶意 代码，当用户访问页面的时候，代码就会执行， 这个时候就达到了攻击的目的。

 除了JavaScript之外，这个脚本也可以是Java、 VBScript、ActiveX、Flash等等 

# 分类 

## 反射型

![反射型](https://img.gyxnb.top/img/反射型xss.png)

包括DOM型 



## 存储型 

![image-20221119181504318](https://img.gyxnb.top/img/image-20221119181504318.png)

利用点:文章、留言板、公告板、评论…… 

演示

 http://192.168.31.193:8082/store.html 

```html
<script>alert(document.cookie)</script>
```

对应数据库的xss表 

攻击 http://192.168.31.193:8082/query.php?id=
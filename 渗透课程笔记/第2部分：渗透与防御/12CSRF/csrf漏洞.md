# 大纲

1. 什么是CSRF漏洞？
2. CSRF案例分析 
3. CSRF漏洞挖掘 
4. CSRF漏洞防御

# CSRF

Cross-Site Request Forgery 

跨站请求伪造



第三方网站利用被攻击网站**生效的cookie**,直接对服务器接口发起请求

# CSRF实现流程

![image-20221121145522952](https://image.201068.xyz/assets/image-20221121145522952.png)

# CSRF案例分析

Gmail CSRF漏洞（设置邮件转发） 

Weibo CSRF漏洞（自动关注账号）



# CSRF漏洞危害 

例如：

- 修改账户信息 
- 利用管理员账号，上传木马文件 
- 传播蠕虫病毒（点击、扩散、点击……） 
- 和其他攻击手段配合，实现攻击，比如XSS、SQL注入

## XSS漏洞危害

- 获取cookie，实现冒充身份的后续操作 
- 刷点击 
-  弹广告 
- 传播蠕虫病

## CSRF与XSS区别

![image-20221121145550382](https://image.201068.xyz/assets/image-20221121145550382.png)



# CSRF payload

- 通过**图片**的img src属性，**自动**加载，发起**GET**请求

```html
<img src="http://192.168.31.193:8087/transfer.php?nameid=1102&amount=1000" width= "0" height="0"
```

- 构建一个**超链接**，用户**点击**以后，发起GET请求

```html
<a href= "http://192.168.31.193:8087/transfer.php?amount=1000&to=jiangang" taget="_blank">小姐姐在线视频聊天！！<a/>
```

- 构建一个**隐藏表单**，用户访问，**自动**提交，发起**POST**请求

  ```
  <form action="http://superbank.com/withdraw" method=POST>
  	<input type="hidden" name="account" value="xiaoming" />
  	<input type="hidden" name="amount" value="1000" />
  	<input type="hidden" name="to" value="jiangang" />
  </form>
  <script> document.forms[0].submit(); </script>
  ```

# CSRF漏洞挖掘

## 确定一个**接口地址**有没有CSRF漏洞

从第三方网站直接调用接口可以成功

## 具体怎么操作

抓取正常通信请求的数据包，再请求一次

## 有没有工具可以使用



### Burp Suite

![image-20221121164549560](https://image.201068.xyz/assets/image-20221121164549560.png)

### CSRF Tester

### Bolt

安装

`git clonehttps://github.com/s0md3v/Bolt` 

检测

http://192.168.31.193:8087/transfer.php有没有csrf漏洞

```python
┌──(root㉿guoyx)-[/home/kali/Bolt]
└─# python3 bolt.py -u http://192.168.31.193:8087/transfer.php



     ⚡ BOLT  ⚡
    
/usr/local/lib/python3.10/dist-packages/fuzzywuzzy/fuzz.py:11: UserWarning: Using slow pure-python SequenceMatcher. Install python-Levenshtein to remove this warning
  warnings.warn('Using slow pure-python SequenceMatcher. Install python-Levenshtein to remove this warning')
 ⚡ Phase: Crawling [1/6]
[~] Parsing http://192.168.31.193:8087/transfer.php      [!] Crawled 1 URL(s) and found 1 form(s).          
 ⚡ Phase: Evaluating [2/6]
[+] Insecure form(s) found
[-] http://192.168.31.193:8087/transfer.php [http://192.168.31.193:8087/login.php]
 ⚡ Phase: Comparing [3/6]
[-] No CSRF protection to test
```

发现有csrf,没有做防护。

### 漏洞扫描服务

https://cloud.tencent.com/product/vss

# CSRF防御

## 防御思路

- 区分一个请求是**来源**于自己的前端页面，还是第三方的网站。
-  让自己的前端页面和伪造的**请求变得不一 样**。

## Referer

Referrer：引用页; 引荐; 来源页面 

作用：**跟踪来源**，比如访问统计、广告效果



检查REFERER :

referer里面是否包含了主机名,IP或域名

### referer的不足

1. 可以任意修改 
2. 可以为空

## Token

在请求中加入一些**随机字段**,

第三方不知道也猜不出来,让第三方网站无法伪造请求



1. 用户使用用户名密码登录，**服务端**下发一个**随机的** token字段给客户端，并且服务端把这个字段保存在 **session**中。
2. **客户端**把这个token保存起来，放到**隐藏字段**。 
3. **用户**在登陆状态下，在之后**访问**的时候，都要**携带这个token字段**。
4. **服务端**从session中拿出token值进行**对比**，如果 一致，说明请求合法。
5. 用户退出，**session销毁，token失效**。



### Token不足

例如还存在xss漏洞，csrf和xss组合，用**xss获取到token**,再利用csrf漏洞。

## 二次验证

- 验证码 
- 短信
- 扫码 
- 人脸识别 
- reCAPTCHA（IP验证）

## 浏览器的保护措施 

#### Referrer Policy

`strict-origin-when-cross-origin`

## 个人用户建议 

1. 不要访问不安全的网站 
2. 不要随意点开别人 发给你的链接

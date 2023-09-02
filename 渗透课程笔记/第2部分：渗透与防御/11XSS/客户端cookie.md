# 现状

每一个请求都是独立的 

# 问题

需要重复鉴别身份 

# 需求1

保持会话 

# 实现

* 服务端给客户端下发标识
- cookie key/value格式的文本: name=wuya,id=99 

# 产生流程

## 浏览器第一次访问

服务器在响应中通过Set-Cookie头字段，下发 Cookie 

## 浏览器保存在本地 

### 硬盘 

有过期时间的Cookie

`C:\Users\15542\AppData\Local\Google\ Chrome\User Data\Default\ `

### 内存 

没有过期时间的临时Cookie，退出浏览器即失效 

## 浏览器随后访问

在请求头中用Cookie字段发给服务器 



# 属性 

## name=value

 一个name/value，就是一个cookie。name/ value这个是必须的，其他的都是可选的。如果 name重复，只取第一个

##  expires

 cookie的过期时间（格林尼治时间），超过这个 时间，cookie就会失效。如果不设置，代表是临 时的cookie，cookie在浏览器关闭的时候就失效 了。

## max-age

与expires作用相同，用来告诉浏览器此cookie 多久过期（单位是秒）。max-age的优先级高于 expires

## domain 

cookie对哪个域名生效。如果没有设置，就设置 为服务器的域名。如果是临时的cookie，就不能 设置domain。

- 比如.baidu.com，百度所有的子站都可以使用。 
- zhidao.baidu.com只能百度知道使用。
-  Cookie具有不可跨域名性。这个是由浏览器保证 的，google服务器不能修改baidu的cookie。 

## path 

除了匹配域名，还可以具体匹配到路径，如果域 名和路径都匹配，那这个cookie就会起作用。 

如果是/，这个服务器所有的路径都可以使用这 个cookie。如果没有设置，那个路径响应，path 就是哪个值 

## secure

只有HTTPS连接，才发送cookie到服务器 

## httponly

告知浏览器不允许通过脚本document.cookie去 更改这个值，同样这个值在document.cookie中 也不可见 

# Cookie特点

- 明文 
- 可修改 比如火狐浏览器 
- 大小受限 

# cookie的用途

- 保持会话 
- 记住密码 
- 跟踪用户行为
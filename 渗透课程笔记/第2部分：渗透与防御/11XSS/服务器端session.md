# Cookie的缺点

 客户端存储量过大

 增加通信成本 

# 解决办法 

把身份信息存储在服务器 

用Cookie给客户端下发一个Session ID 

PHP SESSINO ID 

Java Session ID 

# session校验 

## 开启会话

session_start() cookie/login.php 

把session的字段值保存到以sessionid命名的文件 

## 保存字段 

$_SESSION赋值 cookie/login.php 

## 校验ID 

从服务端的cookie中取出字段 cookie/index.php 

# session销毁 

session_destory() cookie/logout.php 

# 代码演示

http://192.168.31.193:8081

用户名：admin 

密码：123456




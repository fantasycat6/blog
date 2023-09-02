

# Nginx 基础应用实战 04 

## 在公网配置配置HTTPS

### Nginx配置

```
     server {
             listen       443 ssl;
             server_name  aa.abc.com;

             ssl_certificate      /data/cert/server.crt;
             ssl_certificate_key  /data/cert/server.key;

     }
```

### 免费签名

https://freessl.cn

阿里云

腾讯云

### Nginx配置

```
server {
    #SSL 访问端口号为 443
    listen 443 ssl;
 #填写绑定证书的域名
    server_name duozuiyu.com;
 #证书文件名称
    ssl_certificate duozuiyu.com.crt;
 #私钥文件名称
    ssl_certificate_key duozuiyu.com.key;
    location / {
    #网站主页路径。此路径仅供参考，具体请您按照实际目录操作。
        root html;
        index  index.html index.htm;
    }
}

```



编译时报错

```
nginx: [emerg] the "ssl" parameter requires ngx_http_ssl_module in /usr/local/nginx/conf/nginx.conf:98
nginx: configuration file /usr/local/nginx/conf/nginx.conf test failed

```

解决方法：

1. 重新编译 增加ssl模块

```
./configure --with-http_stub_status_module --with-http_ssl_module
```

2. 执行 make

​    make执行完之后 不要执行install

2. 备份
3. 替换文件
4. 启动Nginx
5. 访问https



## java项目的负载均衡

### 反向代理java项目

1.安装jdk

```
yum install java-1.8.0-openjdk
```

2.上传项目

3.让https反向代理到本机Tomcat

```
proxy_pass http://127.0.0.1:8080;
```

4.负载均衡

```
  upstream httpd {
    server 192.168.43.152:80;
    server 192.168.43.153:80;
}
```



## 
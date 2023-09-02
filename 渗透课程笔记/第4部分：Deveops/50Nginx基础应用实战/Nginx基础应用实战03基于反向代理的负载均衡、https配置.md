# Nginx 基础应用实战 03



## 反向代理

`proxy_pass http://baidu.com;`

```
        location /mashibing {
           
	proxy_pass http://mashibing.com/;
        }
```

## 基于反向代理的负载均衡



```

  upstream httpd {
    server 192.168.43.152:80;
    server 192.168.43.153:80;
}
```

##### **weight(权重)**

指定轮询几率，weight和访问比率成正比，用于后端服务器性能不均的情况。

```
upstream httpds {
    server 127.0.0.1:8050       weight=10 down;
    server 127.0.0.1:8060       weight=1;
     server 127.0.0.1:8060      weight=1 backup;
}
```

- down：表示当前的server暂时不参与负载 
- weight：默认为1.weight越大，负载的权重就越大。 
- backup： 其它所有的非backup机器down或者忙的时候，请求backup机器。

## 代理服务的安全问题

## 在公网配置HTTPS

### Nginx配置

```
     server {
             listen       443 ssl;
             server_name  aa.abc.com;

             ssl_certificate      /data/cert/server.crt;
             ssl_certificate_key  /data/cert/server.key;

     }
```

## 免费签名

https://freessl.cn

阿里云
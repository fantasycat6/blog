

# Nginx 基础应用实战 04 

# 动静分离

### 配置反向代理

```

        location / {
            proxy_pass http://127.0.0.1:8080;
            root   html;
            index  index.html index.htm;
        }

```



### 增加每一个location

```
        location /css {
         
            root   /usr/local/nginx/static;
            index  index.html index.htm;
        }
      location /images {
         
            root   /usr/local/nginx/static;
            index  index.html index.htm;
        }

      location /js {
         
            root   /usr/local/nginx/static;
            index  index.html index.htm;
        }
```



### 使用一个location

使用正则

**location 前缀**

------

没有前缀         匹配以指定模式开头的location

------

=              精准匹配，不是以指定模式开头

------

~              正则匹配，区分大小写

------

~*              正则匹配，不区分大小写

------

^~              非正则匹配，匹配以指定模式开头的location

------

 

**location匹配顺序**

- 多个正则location直接按书写顺序匹配，成功后就不会继续往后面匹配

- 普通（非正则）location会一直往下，直到找到匹配度最高的（最大前缀匹配）

- 当普通location与正则location同时存在，如果正则匹配成功,则不会再执行普通匹配 

- 所有类型location存在时，“=”匹配  >  “^~”匹配  >  正则匹配  >  普通（最大前缀匹配）

 

       location ~*/(css|images|js) {
         
            root   /usr/local/nginx/static;
            index  index.html index.htm;
        }


### alias与root

        location /css {
         
            alias   /usr/local/nginx/static/css;
            index  index.html index.htm;
        }
root用来设置根目录，而alias在接受请求的时候在路径上不会加上location。



1）alias指定的目录是准确的，即location匹配访问的path目录下的文件直接是在alias目录下查找的；

2）root指定的目录是location匹配访问的path目录的上一级目录,这个path目录一定要是真实存在root指定目录下的；

3）使用alias标签的目录块中不能使用rewrite的break（具体原因不明）；另外，alias指定的目录后面必须要加上"/"符号！！

4）alias虚拟目录配置中，location匹配的path目录如果后面不带"/"，那么访问的url地址中这个path目录后面加不加"/"不影响访问，访问时它会自动加上"/"；

 但是如果location匹配的path目录后面加上"/"，那么访问的url地址中这个path目录必须要加上"/"，访问时它不会自动加上"/"。如果不加上"/"，访问就会失败！

5）root目录配置中，location匹配的path目录后面带不带"/"，都不会影响访问。



## Url重写

# rewrite语法格式及参数语法:



```bash
rewrite是实现URL重写的关键指令，根据regex (正则表达式)部分内容，
重定向到replacement，结尾是flag标记。


rewrite    <regex>    <replacement>    [flag];
关键字      正则        替代内容         flag标记

关键字：其中关键字error_log不能改变
正则：perl兼容正则表达式语句进行规则匹配
替代内容：将正则匹配的内容替换成replacement
flag标记：rewrite支持的flag标记

rewrite参数的标签段位置：
server,location,if

flag标记说明：
last  #本条规则匹配完成后，继续向下匹配新的location URI规则
break  #本条规则匹配完成即终止，不再匹配后面的任何规则
redirect  #返回302临时重定向，浏览器地址会显示跳转后的URL地址
permanent  #返回301永久重定向，浏览器地址栏会显示跳转后的URL地址
```



`rewrite   ^/account/login.html$     /account/login     last;`

```
rewrite   ^/account/(.+).html$     /account/list?pageNum=$1     last;
```




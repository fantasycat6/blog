

# Nginx 基础应用实战 06



## 构建一个PHP的站点

使用套件

lmnp

https://oneinstack.com

### 安装完成后

![image-20210521191847266](https://img.gyxnb.top/img/image-20210521190719162.png)



### 搭建bbs

https://www.discuz.net/

### 搭建博客

https://wordpress.com

https://cn.wordpress.org/

### CMS系统

http://www.dedecms.com/



## 构建Lua站点

## Openresty Nginx + Lua 

Nginx是一个主进程配合多个工作进程的工作模式，每个进程由单个线程来处理多个连接。

在生产环境中，我们往往会把cpu内核直接绑定到工作进程上，从而提升性能。

### 安装

#### 预编译安装

# CentOS

你可以在你的 CentOS 系统中添加 `openresty` 仓库，这样就可以便于未来安装或更新我们的软件包（通过 `yum check-update` 命令）。 运行下面的命令就可以添加我们的仓库（对于 CentOS 8 或以上版本，应将下面的 `yum` 都替换成 `dnf`）：

```bash
# add the yum repo:
wget https://openresty.org/package/centos/openresty.repo
sudo mv openresty.repo /etc/yum.repos.d/

# update the yum index:
sudo yum check-update
```

然后就可以像下面这样安装软件包，比如 `openresty`：

```bash
sudo yum install -y openresty
```

如果你想安装命令行工具 `resty`，那么可以像下面这样安装 `openresty-resty` 包：

```bash
sudo yum install -y openresty-resty
```

命令行工具 `opm` 在 `openresty-opm` 包里，而 `restydoc` 工具在 `openresty-doc` 包里头。

列出所有 `openresty` 仓库里头的软件包：

```bash
sudo yum --disablerepo="*" --enablerepo="openresty" list available
```

参考 [OpenResty RPM 包](http://openresty.org/cn/rpm-packages.html)页面获取这些包更多的细节。

对于 CentOS 8 及更新版本，我们只需要将上面的 `yum` 命令都替换成 `dnf` 即可。

#### 源码编译安装

#### 下载

http://openresty.org/cn/download.html

`./configure`

然后在进入 `openresty-VERSION/ `目录, 然后输入以下命令配置:

 `./configure`

默认, `--prefix=/usr/local/openresty` 程序会被安装到`/usr/local/openresty`目录。

依赖 `gcc openssl-devel pcre-devel zlib-devel`

安装：`yum install gcc openssl-devel pcre-devel zlib-devel postgresql-devel`

 

您可以指定各种选项，比如

 ```
./configure --prefix=/opt/openresty \

            --with-luajit \

            --without-http_redis2_module \

            --with-http_iconv_module \

            --with-http_postgres_module
 ```





试着使用 `./configure --help` 查看更多的选项。

`make && make install`

#### 服务命令

##### 启动

`systemctl start openresty.service`

##### 停止

`systemctl stop openresty.service`

 重新加载配置文件

`systemctl reload openresty.service`





### 启动成功后的欢迎页面

##### 注意

如遇启动失败，先检查一下是否之前装过nginx 端口有没有冲突

![image-20210611184024696](https://img.gyxnb.top/img/image-20210611184024696.png)

##### 查看已安装模块和版本号

`Nginx -V`

### 测试lua脚本

```nginx
在Nginx.conf 中写入
   location /lua {

        default_type text/html;
        content_by_lua '
           ngx.say("<p>Hello, World!</p>")
         ';
      }
```





### lua-nginx-module

#### 创建配置文件lua.conf

```nginx
   server {
        listen       80;
        server_name  localhost;

   location /lua {

        default_type text/html;

        content_by_lua_file conf/lua/hello.lua;

         }
}
```



#### 在Nginx.conf下引入lua配置

`include       lua.conf;`

#### 创建外部lua脚本

`conf/lua/hello.lua`

内容：

`ngx.say("<p>Hello, World!</p>")`





## lua读取nginx数据的常用方法

### ngx.var

#### 获取Nginx uri中的单一变量

 ```nginx
     location /nginx_var {

          default_type text/html;

         content_by_lua_block {

             ngx.say(ngx.var.arg_a)

         }
     }
 ```

### ngx.req.get_uri_args

#### 获取Nginx uri中的所有变量

```lua
local uri_args = ngx.req.get_uri_args()  

for k, v in pairs(uri_args) do  

    if type(v) == "table" then  

        ngx.say(k, " : ", table.concat(v, ", "), "<br/>")  

    else  

        ngx.say(k, ": ", v, "<br/>")  

    end  
end
```





## lua文件热部署

```
lua_code_cache off;
```

关闭缓存后 重启生效

配置在 `http`->`server`节点下

只对`content_by_lua_file`生效

#### 获取Nginx请求头信息

```lua
local headers = ngx.req.get_headers()                         

ngx.say("Host : ", headers["Host"], "<br/>")  

ngx.say("user-agent : ", headers["user-agent"], "<br/>")  

ngx.say("user-agent : ", headers.user_agent, "<br/>")

for k,v in pairs(headers) do  

    if type(v) == "table" then  

        ngx.say(k, " : ", table.concat(v, ","), "<br/>")  

    else  

        ngx.say(k, " : ", v, "<br/>")  

    end  

end  
```





#### 获取post请求参数

```lua
ngx.req.read_body()  

ngx.say("post args begin", "<br/>")  

local post_args = ngx.req.get_post_args()  

for k, v in pairs(post_args) do  

    if type(v) == "table" then  

        ngx.say(k, " : ", table.concat(v, ", "), "<br/>")  

    else  

        ngx.say(k, ": ", v, "<br/>")  

    end  
end
```

#### http协议版本

```lua
ngx.say("ngx.req.http_version : ", ngx.req.http_version(), "<br/>")
```

#### 请求方法

```lua
ngx.say("ngx.req.get_method : ", ngx.req.get_method(), "<br/>")  
```

#### 原始的请求头内容  

```lua
ngx.say("ngx.req.raw_header : ",  ngx.req.raw_header(), "<br/>")  
```



#### body内容体  

ngx.say("ngx.req.get_body_data() : ", ngx.req.get_body_data(), "<br/>")
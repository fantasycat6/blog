# Nginx 基础应用实战 01



## 课程大纲

1. Nginx基础
   1. 版本区别与安装
   2. 基础知识
      1. Nginx安装部署
      2. http协议基础
      3. 域名与dns
   3. 核心功能与应用场景
      1. 网站静态资源访问
      2. 虚拟主机
      3. 反向代理服务
      4. 负载均衡
      5. rewrite
      6. 软防火墙
      7. Tengine的扩展模块
   4. 实战：构建一个可供大家访问的静态网站
2. 高级使用
   1. 核心配置与调优
   2. 深入http1/2
   3. Squid
   4. 缓存服务
   5. 日志管理
   6. 高可用 keepalived
   7. 监控管理 zabbix prometheus
   8. kubernetes集群化管理
   9. lua语言基础
   10. openresty扩展模块
   11. Nginx二次开发
   12. 实战：构建高性能、高可用、高并发的亿级流量网关系统

## 版本区别

常用版本分为四大阵营

- Nginx开源版

http://nginx.org/

- Nginx plus 商业版

https://www.nginx.com

- openresty

http://openresty.org/cn/

- Tengine

http://tengine.taobao.org/



## 课前准备

### 虚拟机中标准安装CentOS7.6

CentOS6.x升级到CentOS7.x的注意事项视频

1. 1、虚拟机中标准安装CentOS7.6步骤
2. 2、XShell远程连接CentOS7.6
3. 3、CentOS7.6模板机封装步骤
4. 4、VMware虚拟机链接克隆与完全克隆
5. 5、VMware虚拟机创建快照和还原快照
6. 6、CentOS7.6编译安装Redis-4.0.6例子
7. 7、CentOS7.x与CentOS6.x本例中用到几个区别
8. 8、CentOS7.6系统优化之SELinux永久关闭
9. 9、CentOS7.6 yum安装软件以及Redis配置文件简介
10. 10、CentOS7.6创建Redis.service服务实现开机自启动

链接: https://pan.baidu.com/s/1_M0ADqa8LeHrJJTCwTDUpA 提取码: yhfd



docker

## Nginx安装

### 下载

https://nginx.org/en/download.html

传到虚拟机中并解压缩



### 编译安装

`./configure --prefix=/usr/local/nginx`

`make`

`make install`

### 如果出现警告或报错

提示：

```
./configure: error: the HTTP rewrite module requires the PCRE library.
You can either disable the module by using --without-http_rewrite_module
option, or install the PCRE library into the system, or build the PCRE library
statically from the source with nginx by using --with-pcre=<path> option.

```

安装perl库

`yum install -y pcre pcre-devel`



提示：

```
./configure: error: the HTTP gzip module requires the zlib library.
You can either disable the module by using --without-http_gzip_module
option, or install the zlib library into the system, or build the zlib library
statically from the source with nginx by using --with-zlib=<path> option.

```

安装zlib库

`yum install -y zlib zlib-devel`



### 启动Nginx

进入安装好的目录`/usr/local/nginx/sbin`

```
./nginx 启动 
./nginx -s stop 快速停止
./nginx -s quit 优雅关闭，在退出前完成已经接受的连接请求
./nginx -s reload 重新加载配置
```



### 关于防火墙

#### 关闭防火墙

`systemctl stop firewalld.service`

#### 禁止防火墙开机启动

`systemctl disable firewalld.service`

#### 放行端口

`firewall-cmd --zone=public --add-port=80/tcp --permanent`

#### 重启防火墙

`firewall-cmd --reload`

### 安装成系统服务

创建服务脚本

`vi /usr/lib/systemd/system/nginx.service`

服务脚本内容

```
[Unit]
Description=nginx -  web server
After=network.target remote-fs.target nss-lookup.target
  
[Service]
Type=forking
PIDFile=/usr/local/nginx/logs/nginx.pid
ExecStartPre=/usr/local/nginx/sbin/nginx -t -c /usr/local/nginx/conf/nginx.conf
ExecStart=/usr/local/nginx/sbin/nginx -c /usr/local/nginx/conf/nginx.conf
ExecReload=/usr/local/nginx/sbin/nginx -s reload
ExecStop=/usr/local/nginx/sbin/nginx -s stop
ExecQuit=/usr/local/nginx/sbin/nginx -s quit
PrivateTmp=true
  
[Install]
WantedBy=multi-user.target
```

重新加载系统服务

`systemctl daemon-reload`



启动服务

`systemctl start nginx.service`

#### 开机启动

`systemctl enable nginx.service`
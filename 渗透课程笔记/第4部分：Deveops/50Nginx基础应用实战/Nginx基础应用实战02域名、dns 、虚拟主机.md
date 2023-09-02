# Nginx 基础应用实战 02



## 域名、dns与http协议

mashibing.com

## server 相关配置



` listen       80;`  监听端口
`server_name www.mashibing.com mashibing.com; ` 域名可以有多个，用空格隔开

`charset koi8-r;` 编码集

access_log  logs/host.access.log  main; 日志配置

`location ` URI匹配规则

`index index.html index.htm index.jsp;` 默认页
`root /data/www/ha97;` 主目录

### 虚拟主机

虚拟主机是一种特殊的软硬件技术，它可以将网络上的每一台计算机分成多个虚拟主机，每个虚拟主机可以独立对外提供www服务，这样就可以实现一台主机对外提供多个web服务，每个虚拟主机之间是独立的，互不影响的

通过nginx可以实现虚拟主机的配置，nginx支持三种类型的虚拟主机配置

- 基于ip的虚拟主机， （一块主机绑定多个ip地址）
- 基于域名的虚拟主机（servername）
- 基于端口的虚拟主机（同一ip不同的端口）

```
http{
	server{
		#表示一个虚拟主机
	}
}

```



### 重新加载配置与排查错误

`systemctl reload nginx.service` 重新加载配置

`systemctl status nginx.service -l` 查看错误详情



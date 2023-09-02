# xsser

## 主要特性

同时使用GET和POST方法注入。 

包括各种过滤器和绕过技术。 

可以与命令行和GUI一起使用。 

将提供攻击的详细统计数据。

 

## 查看参数

```
xsser -h
```

参考 

https://www.freebuf.com/sectool/173228.html

## 检查接口

```
xsser -u "http://192.168.31.193:8084/vulnerabilities/" -g "xss_r/?name=XSS" --cookie="security=low; PHPSESSID=9j7j5aml5k3nqj5st6grtfaiqa" -s -v --reverse-check
```

注意：替换成DVWA最新的cookie

## 基于搜索引擎语法检测

```
xsser –De "google" -d "search.php?q=" 
```

## 图形化界面

```
xsser --gtk
```

# XSStrike

## 整体介绍

- 生成payload 
- 爬虫功能 
- 探测WAF 

## 安装使用 

```bash
git clone https://github.com/s0md3v/XSStrike
```

python 3.6 以上 



## 帮助

```
python3 xsstrike.py -h
```



## GET 

```
python3 xsstrike.py -u 'http://192.168.70.130/vul/xss/xss_reflected_get.php?message=321&submit=submit' 
```

## POST

```
python3 xsstrike.py -u "http://192.168.31.193:8082/reflect.php" --data 'name=1' 
```

## 爬虫

```
python3 xsstrike.py -u "http://192.168.31.193:8082/get.html?url=1" 
```

## 参考

https://www.freebuf.com/sectool/173228.html

https://blog.csdn.net/gao646467783/article/details/113249158




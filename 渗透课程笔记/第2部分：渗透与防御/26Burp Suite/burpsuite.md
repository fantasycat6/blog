# Burp Suite基本介绍

## Burp历史版本

https://portswigger.net/burp/releases

## 主要功能

- 目标：测试网站安全性 
- 手段：抓HTTP包、改HTTP包；自动请求、过滤响应 
- 场景：SQL注入、文件上传、XSS、CSRF、FUZZ、重放 攻击、密码爆破、爬取数据、漏洞扫描……

## 版本区别

- 企业版 Enterprise Edition 
- 社区版 Community Edition 
- 专业版 Professional （$399/year)

## 运行平台

- Jar（推荐） 
- Linux 
- MacOS（ARM、Intel） 
- Window

## 参考资料

### 本地文档

问号按钮

### 在线文档

https://portswigger.net/support 

https://portswigger.net/burp/documentation/desktop

### 视频学习和练习平台

https://portswigger.net/web-security

### 问答社区

https://forum.portswigger.net/

# Burp Suite配置

## Burp jar包

### Burp jar包

推荐2021+，jar包版本 

https://portswigger.net/burp/releases

### JRE环境

1. JDK类型：推荐解压版（zip） 
2. JDK版本：推荐JDK11 （配合Burp 2021）

https://repo.huaweicloud.com/java/jdk/

#### JDK11环境变量配置

| 变量      | 值                                   |
| --------- | ------------------------------------ |
| JAVA_HOME | JDK解压的根路径，比如 D:\jdk-11.0.11 |
| PATH      | %JAVA_HOME%\bin                      |

### 激活和汉化包

#### 激活软件下载地址： 

https://github.com/h3110w0r1d-y/BurpLoaderKeygen/releases 

#### 汉化包地址： 

https://github.com/h3110w0r1d-y/BurpLoaderKeygen/releases/download/2.0/BurpLoaderKeygenCn.jar

## Burp Suite启动激活

### 命令行方式启动

**burp_start.bat**，内容： 

```
@echo off 
cmd /k "java -jar BurpLoaderKeygen.jar"
```

### VBS启动

```
set ws=WScript.CreateObject("WScript.Shell") 
ws.Run "burp_start.bat",0
```

## Burp Suite配置

### 汉化说明

如果执行了上面的英文破解程序，需要先**反向激活**，让激活失效，再**删除**英文破解程序产生的**config.cfg**文件。

接着使用中文的破解程序激活。

**burp_cn_start.bat** 

```
@echo off 
cmd /k "java -jar BurpLoaderKeygenCn.jar"
```

**VBS启动**

```
set ws=WScript.CreateObject("WScript.Shell") 
ws.Run "burp_cn_start.bat",0
```

# Burp Suite模块

## Burp Suite界面布局

### 参考手册目录全文

https://portswigger.net/burp/documentation/contents

### 界面总览

![image-20221219180736217](https://img.gyxnb.top/img/image-20221219180736217.png)

### 旧版对比

![image-20221219180831190](https://img.gyxnb.top/img/image-20221219180831190.png)

### 菜单栏

#### Burp

![image-20221219181021718](https://img.gyxnb.top/img/image-20221219181021718.png)

1. 搜索内容 
2. 配置库 
3. 用户选项 
4. Infiltrator 
5. Clickbandit 
6. Collaborator clien

#### Project

![image-20221219181129597](https://img.gyxnb.top/img/image-20221219181129597.png)

1. 工程配置 
2. 重命名 
3. 保存备份 
4. 导入配置 
5. 导入遗留状态文件

#### Intruder

![image-20221219181216302](https://img.gyxnb.top/img/image-20221219181216302.png)

1. 发起攻击 
2. 打开工作空间 
3. 扫描预定义的插入点
4.  被动扫描 主动扫描
5.  发送到Repeater
6.  保存、加载、复制配置
7.  打开新标签时的操作
8.  自动标记payload位置
9.  配置预定义字典
10.  关闭攻击结果时的偏好

#### Repeater

![image-20221219181443476](https://img.gyxnb.top/img/image-20221219181443476.png)

1. 更新 Content-Length 
2. 解压压缩的数据 
3. 跟随重定向跳转
4.  重定向的cookie处理
5.  跨域跳转
6.  HTTP1 行结尾
7.  HTTP2 连接重用
8.  剥离 HTTP2 连接头
9.  允许 HTTP2 ALPN 覆盖

https://portswigger.net/burp/documentation/desktop/tools/repeater/options

#### Window

![image-20221219181619180](https://img.gyxnb.top/img/image-20221219181619180.png)

剥离窗口

#### Help

![image-20221219181646974](https://img.gyxnb.top/img/image-20221219181646974.png)

1. 离线文档
2.  上手用BP做渗透测试
3.  支持中心（在线）
4.  更新记录 
5. 上报bug 运行诊断 
6. 内置浏览器健康检查
7.  许可证 
8. 检查更新
9.  下载其他安装器 
10. 删除BP

## 模块总体概括

### 官方介绍

https://portswigger.net/burp/documentation/desktop/tools

### Dashbord仪表盘

- 扫描 
- 任务 Tasks 
- 事件日志 Event Log 
- 漏洞问题 Issue activity

https://portswigger.net/burp/documentation/desktop/dashboard

### Target 目标模块

- 生成站点地图（sitemap） 
- 设置扫描域（target scope） 
- 生成安全分析

### Proxy 代理模块

拦截浏览器的HTTP数据包（包括请求和响应）

![image-20221219182424329](https://img.gyxnb.top/img/image-20221219182424329.png)

### Intruder渗透模块

对拦截到的请求（地址），设置攻击载荷 （payload），利用**字典**进行渗透测试 

比如：目录扫描、密码暴力破解、压力测试、FUZZ等等

### Repeater重放模块

1. 分析每一步具体的请求和响应内容 
2. 修改请求和响应内容 
3. 重发请求内容

### Sequencer 序列器模块

用来评估Token、Session等关键字段 

是否可以伪造（是否固定、是否可预测）

![image-20221219182713921](https://img.gyxnb.top/img/image-20221219182713921.png)

### Decoder 解码器模块

对请求数据进行编码、解码

### Comparer比较器模块

对两次请求的结果进行对比

### Extender 扩展模块

对插件进行管理

# Burp Proxy模块

## 网络代理

![image-20221219183410409](https://img.gyxnb.top/img/image-20221219183410409.png)

## 网络代理的作用

- 突破IP限制 
- 隐藏IP 
- 加速访问
- ......

## Burp代理的作用

拦截HTTP(S)请求，并对请求和响应进行处理和利用

## 与Fiddler、WireShark的区别

| 对比项 | Burp         | Fiddler      | WireShark        |
| ------ | ------------ | ------------ | ---------------- |
| 平台   | 多平台       | Windows      | 多平台           |
| 定位   | 渗透测试套件 | Web调试工具  | 网络封包分析工具 |
| 功能   | 渗透测试     | 调试HTTP请求 | 分析数据         |

## 浏览器代理设置

![image-20221219183719656](https://img.gyxnb.top/img/image-20221219183719656.png)



- Chrome扩展插件Crx：https://crxdl.com
- 下载Proxy SwitchySharp

## Burp Suite代理设置

### Intercept

| 操作            | 描述                           |
| --------------- | ------------------------------ |
| Forward         | 放行本次拦截的包，发送到服务器 |
| Drop            | 丢弃本次拦截的包               |
| on/off          | 拦截开关                       |
| Action          | 对数据的操作                   |
| Open in Browser | 打开内置浏览器                 |

### Options选项

| 操作                      | 描述         |
| ------------------------- | ------------ |
| Proxy Listeners           | 监听器       |
| Intercept Client Requests | 请求拦截规则 |
| Intercept Server Response | 响应拦截规则 |
| Response Modification     | 响应结果修改 |
| Match and Replace         | 匹配和替换   |
| TLS Pass Through          | TLS穿透      |
| Miscellaneous             | 杂项         |

## Burp Suite拦截HTTPS

### 网站的证书的作用

1. 操作系统安装根证书，里面有CA的公钥 
2. CA颁发的证书，包含机构的公钥，并且用CA的公钥对机构公钥摘要加签 
3. 浏览器利用CA的公钥对摘要进行验签，确定机构公钥合法 
4. 浏览器用机构的公钥与服务器协商会话密钥 
5. 浏览器与服务器用会话密钥通信

![image-20221219184300307](https://img.gyxnb.top/img/image-20221219184300307.png)

![image-20221219184308582](https://img.gyxnb.top/img/image-20221219184308582.png)

### 导出证书

![image-20221219184327303](https://img.gyxnb.top/img/image-20221219184327303.png)

# Burp Target模块

## Burp渗透测试流程

![image-20221219184447840](https://img.gyxnb.top/img/image-20221219184447840.png)

## Target模块的作用

### 与HTTP History的区别

1. HTTP History按**时间**顺序记录 
2. Target按**主机**或者**域名**分类记录

![image-20221219184545443](https://img.gyxnb.top/img/image-20221219184545443.png)

### Target模块的作用

1. 把握网站的整体情况 
2. 对一次工作的域进行分析 
3. 分析网站存在的攻击面

### 攻击面

对一个软件系统可以采取的攻击方法集合，一个软件 的攻击面越大安全风险就越大。 

包括：字段、协议、接口、服务、硬件的攻击点。

## Target设置作用域

### 同一个域

| 域1                     | 域2                                                          | 同域 | 原因   |
| ----------------------- | ------------------------------------------------------------ | ---- | ------ |
| http://www.wuya.com/    | http://www.wuya.com/index.html  http://www.wuya.com/admin?a=1 | YES  | -      |
| http://www.wuya.com/    | https://www.wuya.com/                                        | NO   | 协议   |
| http://www.wuya.com/    | http://www.wuya.cn/                                          | NO   | 主域名 |
| http://www.wuya.com/    | http://blog.wuya.com/                                        | NO   | 子域名 |
| http://www.wuya.com:80/ | http://www.wuya.com:7298/                                    | NO   | 端口   |

- 协议、域名、端口必须相同 
- 目录、文件、参数可以不同

### 限定域的范围

例如： 

只拦截：https://www.wuya.com/ 

不拦截：https://www.wuya.com/blog

### 使用场景

1. 限定Sitemap和HTTP history记录哪些域的内容 
2. 限定Spider抓取哪些域的内容 
3. 限定Scanner扫描哪些域的安全漏洞

## 站点地图Sitemap

### 站点地图记录类型

1. 自动（爬行） 
2. 手动（浏览器访问）

## 对结果进行操作

### 右键菜单

![image-20221219191216277](https://img.gyxnb.top/img/image-20221219191216277.png)

### Referer字段

作用：告诉服务器当前请求是从哪个页面链接过来的

 应用场景： 

1. 来源统计 
2. 防盗链

# Burp 扫描功能

## 参考资料

https://portswigger.net/burp/documentation/scanner 

https://portswigger.net/burp/documentation/desktop/scanning

 模块总体介绍： 

https://portswigger.net/burp/vulnerability-scanner 

扫描功能的使用： 

https://portswigger.net/burp/documentation/desktop/getting-started/running-your-first-scan 

收录的漏洞 

https://portswigger.net/kb/issues

## 漏洞扫描整体介绍

### 漏洞扫描与工具

AWVS、Appscan、Nessus、Openvas、Goby、 Xray、ZAP……

### 新版BP

![image-20221219191758077](https://img.gyxnb.top/img/image-20221219191758077.png)

爬行 Crwal 

审计 Audit

### 核心内容

| 内容                                           | 描述                                               |
| ---------------------------------------------- | -------------------------------------------------- |
| Scan（**主动**扫描）                           | 给定地址，爬取内容，检测漏洞                       |
| Live task（**被动**扫描）                      | 对经过Proxy、Repeater、Intruder的请 求进行漏洞检测 |
| live passive **crawl** from proxy(all traffic) | 来自Proxy的被动流量抓取                            |
| live **audit** from proxy(all traffic)         | 流量的实时**审计**                                 |

### 扫描类型

- Actively Scan：主动扫描 = Crawl and audit 
- Passively Scan：被动扫描 = Live audit

### 主动扫描

- 方式：爬取所有链接，检测漏洞 

- 特点：发送大量请求 

- 使用场合：开发、测试环境 

- 针对漏洞： 

  客户端的漏洞，如XSS 、HTTP头注入、操作重定向。

  服务端的漏洞，如SQL注入、命令行注入、文件遍历。

### 被动扫描

1. 方式：只检测经过BP代理服务器的地址，不爬取

2. 特点：发送有限请求

3.  使用场合：生产环境

4.  针对漏洞： 

   - 提交的密码为未加密的明文。

   - 不安全的cookie的属性，例如缺少HttpOnly和安全标志。

   - cookie的范围缺失。 

   - 跨域脚本包含和站点引用泄露。 

   - 表单值自动填充，尤其是密码。 

   - SSL保护的内容缓存。 

   - 目录列表。 

   - 提交密码后应答延迟。 

   - session令牌的不安全传输。 

   - 敏感信息泄露，例如内部IP地址、电子邮件地址、堆枝跟踪等信息泄露。 

   - 不安全的ViewState 的配置。 

   - 错误或不规范的Content-Type指令。

## 使用BP漏扫功能

### 主动扫描的类型

![image-20221220083555554](https://img.gyxnb.top/img/image-20221220083555554.png)

Crawl 爬行（建立站点地图） 

Audit 审计（扫描漏洞）



Scan Configuration：爬行和审计的设置

 Application login：账号密码

 Resouce pool：线程池设置

### 爬行配置

| 内容                          | 翻译         | 作用                                               |
| ----------------------------- | ------------ | -------------------------------------------------- |
| Crwal Optimization            | 爬行的优化   | 最大链接深度；更快还是更完整                       |
| Crwal Limits                  | 爬行最大限制 | 最大时间；最多链接；最大请求数                     |
| Login Functions               | 登录注册     | 登录操作：自动注册；用无效的用户名主动触发登录失败 |
| Handling Application          | 错误处理     | 爬行过程中的错误处理，比如超 时                    |
| Miscellaneous [ˌmɪsəˈleɪniəs] | 杂项         | 杂项                                               |

### 审计配置

| 内容                                     | 翻译                | 作用                                                         |
| ---------------------------------------- | ------------------- | ------------------------------------------------------------ |
| Audit Optimization                       | 审计优化            | 扫描的速度和精确度                                           |
| Issues Reported                          | 问题报告            | 报告哪些漏洞：根据扫描类型或者漏洞类型 来过滤，默认全选      |
| Handling Application Errors During Audit | 审计过程出错 的处理 | 比如连接失败和传输超时默认：如果一个插 入点连续失败两次，就跳过，不再发送请求 （接口挂了） 如果连续两个插入点失败，跳过其他的插入 点（网站挂了） |
| Insertion Point Types                    | 插入点的类型        | URL参数值、Body里面的参数值、Cookie值、 参数名字、HTTP请求头、Body完整内容、 URL文件名、URL目录 |
| Modifying Parameter Locations            | 插入点位置          | 替换，交叉检测                                               |

### 审计配置

| 内容                                   | 翻译           | 作用                                                |
| -------------------------------------- | -------------- | --------------------------------------------------- |
| Ignored insertion Point                | 忽略的插入点   |                                                     |
| Frequentcly Occurring Insertion Points | 插入点相同时   | 当大量的插入点结果没有区别的 时候，更加高效地扫描。 |
| Misc Insertion Point Options           | 杂项           | 一个插入点的最大请求数量                            |
| Java Script Analysis                   | JavaScript审计 |                                                     |

### 主动扫描的类型

Scan：输入URL或者URL右键 

Live Task：从其他模块获取到流量 



Live Task： 

Audit 不会爬行 

passive crawl 会爬行

## 生成扫描报告

### 扫描报告

![image-20221220084534787](https://img.gyxnb.top/img/image-20221220084534787.png)

右键导出

https://portswigger.net/burp/samplereport/burpscannersamplereport

# Burp Repeater

## 参考资料

https://portswigger.net/burp/documentation/desktop/tools/repeater

## Repeater模块作用

### 用途

1. 发起HTTP请求，分析响应 
2. 重放请求

## Repeater使用方法

### 内容来源

1. 从其他模块发送（Ctrl +R ） 
2. 手动填入

# Burp Intrude

## 参考资料

https://portswigger.net/burp/documentation/desktop/tools/intruder

## Intruder模块作用与原理

### 原理

http://xxx.wuya.com/bbs/index.php?name=wuyanzu&motto=go 

对请求参数进行修改，分析响应内容，获得特征数据 

本质： 

1. 自动化发起HTTP请求 
2. 基于现成字典或者生成字典

### 用途

1. 猜测用户名、密码等 
2. 寻找参数、目录等 
3. 枚举商品ID、验证码等
4. 模糊测试（FUZZ）
5. .......

可替代工具： 

wfuzz（全部功能）、dirb（目录扫描）、hydra（暴 破）……

## Intruder实现暴力破解

### 流程

1. 从其他模块发送或者手动填写 
2. 选择攻击模式 Attack type 
3. 选择攻击字段 Positions 
4. 设置payload 
5. 其他设置（线程池等） 
6. 发起攻击 
7. 查看结果

### 攻击模式

- Sniper 狙击手 
- Battering ram 攻城锤 
- Pitchfork 草叉 
- Cluster bomb 榴霰[xiàn]弹

### payload type

| 类别                   | 名称                  | 描述                                                         |
| ---------------------- | --------------------- | ------------------------------------------------------------ |
| Simple list            | 简单字典              | 添加、粘贴或者从文件读取字典，或者使用预定义的字典           |
| Runtime file           | 运行时文件            | 运行时，Burp Intruder将读取文件的每一行作为一个 Payload      |
| Custom iterator        | 自定义迭代器          | 这个是占位填充的一种方式，最多8位                            |
| Character substitution | 字符替换              | 把字典里面相应的字符进行替换                                 |
| Case modification      | 大小写修改            | 要不要保持原样的，要不要全部大写的，要不要全小写的， 要不要驼峰命名的 |
| Recrusvive grep        | 递归查找              | 用来提取相应数据的比如拿到PHPSESSIONID，拿到TOKEN 等等，可以通过格式匹配抓取到对应的字段值。 |
| Illegal unicode        | 非法Unicode 编码      | 用于绕过正则表达式的过滤验证                                 |
| Character blocks       | 字符块                | 比如生成100A，200个+号，300个数字1等等                       |
| numbers                | 数字组合              |                                                              |
| dates                  | 日期组合              |                                                              |
| Brute forcer           | 暴力破解              | 暴力枚举，最后一位先固定，然后一个个改                       |
| Null payloads          | 空payload             | 不需要设置payload                                            |
| Character frobber      | 字符frobber           | 依次修改指定字符串在每个字符位置的值，每次都是在原字 符上递增一个该字符的ASCII码。 |
| Bit flipper            | Bit翻转               | 对预设的Payload原始值，按照比特位，依次进行修改              |
| Username generator     | 用户名生成器          | 主要用于用户名和email帐号的自动生成                          |
| ECB block shuffler     | ECB加密块洗牌         | 基于ECB加密模式的Payload生成器                               |
| Extension-generated    | Burp Payload 生成插件 | 基于Burp插件来生成Payload值，需要安装插件                    |
| Copy other payload     | Payload复制           | 是将其他位置的参数复制到Payload位置上（比如密码要输 入两遍） |

https://portswigger.net/burp/documentation/desktop/tools/intruder/payloads/types

## Intruder其他攻击模式

### Battering ram 攻城锤

所有字段的值相同，来自同一个字典

### Pitchfork 草叉

从多个字典提取值，赋给多个字段，按顺序一一对应 

例如： 

- 100个用户名 
- 50个密码 
- 最终请求次数：50次

### Cluster bomb 榴霰弹

所有字典全部交叉验证 

例如： 

- 100个用户名 
- 50个密码 
- 最终请求次数：5000次

## Intruder标记结果

### Grep Match

![image-20221220091129176](https://img.gyxnb.top/img/image-20221220091129176.png)

## Intruder获得CSRF Token

### Grep Extract

![image-20221220091307639](https://img.gyxnb.top/img/image-20221220091307639.png)
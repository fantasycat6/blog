#          JavaScript基础第一天

贾成豪 哈尔滨 QQ：122787987

# 一、JavaScript简介

![img](https://img.gyxnb.top/img001/clip_image002.jpg)![img](https://img.gyxnb.top/img001/clip_image004.jpg)

JavaScript（简称“JS”） 是一种具有[函数](https://baike.baidu.com/item/函数/301912)优先的[轻量级](https://baike.baidu.com/item/轻量级/22359343)，解释型或即时编译型的[编程语言](https://baike.baidu.com/item/编程语言/9845131)。虽然它是作为开发Web页面的[脚本语言](https://baike.baidu.com/item/脚本语言/1379708)而出名的，但是它也被用到了很多非浏览器环境中，JavaScript 基于原型[编程](https://baike.baidu.com/item/编程/139828)、多范式的动态脚本语言，并且支持[面向对象](https://baike.baidu.com/item/面向对象/2262089)、命令式和声明式（如[函数式编程](https://baike.baidu.com/item/函数式编程/4035031)）风格。 [1] 

JavaScript在1995年由[Netscape](https://baike.baidu.com/item/Netscape)公司的[Brendan Eich](https://baike.baidu.com/item/Brendan Eich)，在[网景导航者](https://baike.baidu.com/item/网景导航者/10404300)浏览器上首次设计实现而成。因为Netscape与[Sun](https://baike.baidu.com/item/Sun/69463)合作，Netscape管理层希望它外观看起来像[Java](https://baike.baidu.com/item/Java/85979)，因此取名为JavaScript。但实际上它的语法风格与[Self](https://baike.baidu.com/item/Self/4959923)及[Scheme](https://baike.baidu.com/item/Scheme)较为接近。

总结：

1. JavaScript前端人简称JS。是一门编程语言。
2. JavaScript属于脚本语言。脚本语言特征：可以嵌套在网页中，给网页添加一些动态效果。
3. JavaScript在1995年由[Netscape](https://baike.baidu.com/item/Netscape)公司的[Brendan Eich](https://baike.baidu.com/item/Brendan Eich)。

## 1.1JavaScript用途

概述：我们已经知道，JavaScript属于一门脚本语言。脚本语言有一个很大特征：可以给网页添加一些动态效果。

![img](https://img.gyxnb.top/img001/clip_image006.jpg)   ![img](https://img.gyxnb.top/img001/clip_image008.jpg)

![img](https://img.gyxnb.top/img001/clip_image010.jpg)

 

- 比如：后期课程中我们会学习node平台，开发服务器。利用的也是JS

- 比如：后期课程中我们会学习React、Vue框架。他们底层也是通过JS实现的。


## 1.2JavaScript组成

问题：你知道前端分为几层吗？

| HTML（结构层）       | 利用语义化标签搭建网页             |
| -------------------- | ---------------------------------- |
| CSS（样式层）        | 利用样式进行美化网页、进行网页布局 |
| JavaScript（行为层） | 可以给网页添加动态效果             |

问题：JavaScript是由哪几部分组成的呀？

![img](https://img.gyxnb.top/img001/clip_image012.jpg)

答：JavaScript是由三部分组成。ECMAScript、DOM、BOM。

1.  ECMAScript：它是欧洲计算机协会，大概每年六月中旬定制语法规范。

2.  DOM：英文全称：document object model ，中文全称：文档对象模型。

3. BOM：英文全称：browser object model，中文全称：浏览器对象模型。


## 1.3JavaScript书写规范

概述：我们已经知道JS属于脚本语言。它需要嵌套在网页中才可以运行的。

我们需要通过双闭合标签script，将JS语法嵌套在网页中运行。

而且，script标签可以放在网页的任意地方，而且，可以同时有多个script标签。

<!DOCTYPE html>
```
<html lang="en">

<head>

   <meta charset="UTF-8">

    <title>Document</title>

</head>

<body>

 

</body>

</html>

<script type="text/javascript">
  

   alert("你好，我是JS呀");

</script>

<script type="text/javascript">


  alert("hello word");

</script>
```

- JS语法，务必通过双闭合标签script，嵌套在网页内部执行。

-  script标签可以放在程序任意地方，但是一般会放在程序最下方。

-  script标签内部，只能放JS语法。标签、样式别再script标签内部书写。

-  script标签有一个type属性，属性值为text/javascript。代表的是书写JS语法。


# 二、内置函数

内置函数：内置，可以理解为浏览器自带的。函数，你可以理解为是某一个功能。

## 2.1alert-警告框

![img](https://img.gyxnb.top/img001/clip_image014.jpg)

概述：alert是JS当中内置函数，它主要的作用是，就是在浏览器正上方弹出一个警告框。

![img](https://img.gyxnb.top/img001/clip_image016.jpg)

```
<script type="text/javascript">


    //内置函数-alert警告框使用

   alert("床前明月光,疑是地上霜");

   alert('举头望明月,低头思故乡');

</script>
```

- JS语法，务必放在script标签内部书写。而且，script标签内部，别书写标签、别书写样式。

- script标签有一个type属性，属性值为text/javascript

- 在JS当中单行注释：两个冲左侧反斜杠。

- 警告框使用：需要由关键字alert开头，后面紧随小括号。

- 小括号里面传递的参数，即为警告框显示内容。

- 传递参数一般情况下需要加上双引号、单引号。别一个是双的、一个是单的。

- 在每一行程序结束末尾，加上一个分号。这个分号代表的是，这行语句结束了。


## 2.2prompt-提示框

![img](https://img.gyxnb.top/img001/clip_image018.jpg)

概述：prompt也是JS当中内置函数，它主要的作用是，可以在浏览器的正上方，弹出一个提示框。

![img](https://img.gyxnb.top/img001/clip_image020.jpg)

```
<script type="text/javascript">

   //内置函数---prompt提示框

   prompt("姑娘你的芳龄?");

   prompt('大兄弟期末考试,考了几分呀');

</script>
```

- prompt书写语法，和上面的alert是一模一样的。

- 是以关键字prompt开头，后面紧随小括号。

- 小括号里面可以传递参数，这个参数即为提示框提示的文字。

- 传递参数，一般情况下需要外层加上一对双引号、单引号。别一个是双、一个是单。

- 在程序结尾处，别忘记加上一个分号。代表这行语句结束了。


## 2.3控制台使用*

![img](https://img.gyxnb.top/img001/clip_image022.jpg)![img](https://img.gyxnb.top/img001/clip_image024.jpg)

概述：在JS当中，我们可以通过console对象的log方法在控制台中输出一些内容。

控制台的快捷键：ctr + shift + i

语法格式：

console.log(参数)；

![img](https://img.gyxnb.top/img001/clip_image026.jpg)

![img](https://img.gyxnb.top/img001/clip_image028.jpg)

![img](https://img.gyxnb.top/img001/clip_image030.jpg)

```
<script type="text/javascript">


   //控制台的使用

   console.log("我是控制台中打印的数据");

   console.log("我是大帅哥","我是贾成豪");

</script>
```

- console.log可以在控制台中打印一些数据。

- 如果同时打印多个数据，多个数据之间，用逗号隔开。

- 当程序出现错误的时候（红色），可以在控制台中查看。

- 控制台中可以进行一些数学运算。可以获取到运算的结果。


# 三、字面量  

概述：在JS世界当中，我们书写的数据是不能瞎写的。这是由于JS中的数据是有数据类型划分的。

JS的数据类型一共有六种：五个基本数据类型、一个引用类型。

五个基本数据类型：

| 数据类型              | 数值                      |
| --------------------- | ------------------------- |
| String（字符串类型）  | “我是大帅哥” “我是大美女” |
| Number(数字类型)      | 100、200、3.14、-99       |
| Boolean（布尔类型）   | true、false               |
| Undefined(未定义类型) | undefined                 |
| Null（空对象类型）    | null                      |

一个引用类型：

| 数据类型         | 数值                           |
| ---------------- | ------------------------------ |
| Object(引用类型) | 函数、数组、正则、DOM、BOM等等 |

注意：以后我们在编程的时候。书写的数据务必是这六中数据类型当中的数值。

如果不是，程序就会报错。

字面量：字面量，说白了就是某一个类型数据的一个固定数值。

当你看到这个固定的数值的时候，我们就知道他是属于那种类型的数据。

## 3.1数字类型字面量

概述：在JS当中，数字类型的字面量使用频率相对挺高的。其实，常用的数字类型的字面量，无非就是两个。

整数和小数（浮点数）

### 3.1.1整数字面量

概述：在JS当中整数字面量，即为十进制的数字。逢10进一。整数的数字区分正负之分。

![img](https://img.gyxnb.top/img001/clip_image032.jpg)

```
<script type="text/javascript">


  //十进制的数字（整数）

  console.log(100);

  console.log(-99);

  console.log(12306);

</script>
```

- 在JS当中，十进制的数字，使用非常多。

- 整数是有正负之分的。

- 数字在控制台中打印的时候，是蓝色的。


### 3.1.2浮点数

概述：浮点数，即为小数。数字当中带有小数点的。浮点数也有正负之分。

![img](https://img.gyxnb.top/img001/clip_image034.jpg)

  console.log(3.1415926);

  console.log(-6.6);

  console.log(4.8)

  //如果小数是在0~1之间的小数，可以使用0

  console.log(.123);

- 小数即为浮点数。数字当中带有小数点的。

- 小数也有正负之分

- 0~1之间的小数可以省略零

```
<script type="text/javascript">


  //小数注意事项

  console.log(0.1 + 0.2);

  console.log(0.5 + 0.3);

  console.log(0.3 + 0.3);

</script>
```

- l 小数在进行计算的时候：比如0.1 + 0.2这个比较特殊。

- l 由于0.1和0.2在进行计算的时候，计算机底层转换为二进制数据进行计算。没办法整除（后面保留17位小数）

- l 由于遵守IEEE754浮点数算数标准。


### 3.1.3科学计数法

概述：科学计数法，也是表示数字一种形式。代表的是某一个数字与10的N次幂的乘积。

![img](https://img.gyxnb.top/img001/clip_image036.jpg)

console.log(6e2);相当于6 * 10 ^2

console.log(3.14E2);相当于3.14 * 10^2

- l 科学计算法，也是表达数字一种形式

- l 代表的是某一个数字与10的N次幂的乘机。

- l 科学计数法中的英文单词e可以是大写的，当然也可以是小写的。


### 3.1.4特殊值

#### 3.1.4.1Infinity

![img](https://img.gyxnb.top/img001/clip_image038.jpg)

 

概述：在JS当中，数字其实是有范围的。-2^53~2^53,如果开发中书写数字超出这个范围，

如果超出数字范围，可以利用特殊值Infinity进行表示。Infinity这个数字类型的特殊值，也有正负之分。

![img](https://img.gyxnb.top/img001/clip_image040.jpg)

```


<script type="text/javascript">


  //数字类型特殊值---Infinity

  console.log(Infinity);

  console.log(-Infinity);

  console.log(6e123456789);//Infinity

</script>
```

- l 在控制台中打印的数字，切记是蓝色的。

- l 数字类型的特殊值Infinity（无穷大），也有正负之分。（代表这个数字超出JS数字范围）

- l Infinity（无穷大）的首个英文字母，是大写的。


#### 3.1.4.2NaN

概述：NaN，英文全称【Not A Number】，它是Number（数字类型）中的一个特殊值。

这个数值，一般是在数学计算不出结果的时候回出现的。

比如：在数学当中，数字零不能作为分母的。如果出现这种现象，别的语言可能崩掉。

但是在JS当中，不会出现崩掉现象，而是给你返回一个数字类型特殊值NaN。

![img](https://img.gyxnb.top/img001/clip_image042.jpg)

  console.log(0/0);//NaN

  console.log(12/0);//Infinity

- l 在数学当中，零是不能作为分母的。在别的语言当中，零作为分母，程序可能会崩掉

- l 红色部分：如果分子、分母同时为零。认为分母零（零），但是计算不出结果，只能返回一个数字类型特殊值NaN

- l 蓝色部分：如果分子（不为零），分母为零。认为分母零（趋近于零的这样的一个数字），只能返回一个数字类型特殊值Infinity。


## 3.2字符串类型的字面量

概述：字符串（String）类型数据外层需要加上双引号、单引号。别一个是双、一个是单。

字符串：可以当中是人说的话而已。

字符串：字符串是由字符组成的。而字符串中的字符，可以是汉字、英文字母、数字、任意特殊符号都可以。

![img](https://img.gyxnb.top/img001/clip_image044.jpg)

```
<script type="text/javascript">


  //字符串类型的字面量

  console.log("我是大诗人李白");

  console.log("订火车票12306");

  console.log("我是阿拉伯人说的是@#￥%……&*WERTYU123132");

  console.log("12345687");

  console.log("");

  console.log("  么么哒")

</script>
```

- l 字符串的数据外层务必加上双引号、单引号。

- l 字符串在控制台中打印的时候是黑色的。

- l 数字类型的字面量在控制台中打印的时候是蓝色。

- l 数据外层如果加上双引号、单引号。即为字符串类型的数据。

- l 空格也可以作为字符串的字符。

- l 如果字符串中一个字符都没有，称之为空字符串。


# 四、变量

## 4.1变量基本使用

![img](https://img.gyxnb.top/img001/clip_image046.jpg)

概述：变量（variable），它是计算机语言中一个术语。变量这个术语起源于数学。

变量，你可以理解为是一个容器，这个容器可以装在任意类型的字面量数值、或者装载数学计算完结果。

我们可以通过访问变量名字、获取到变量存储的结果。

变量在使用的时候,分为三步：声明、赋值、使用。

1. 声明：我们在使用变量之前，务必需要通过关键字var进行声明一次。

   var 变量名字;//代表声明一个变量

2. 赋值：可以将任意类型字面量数值、数学计算完结果。赋值给变量

   变量名字 = 任意类型字面量数值

3. 使用：通过访问变量名字，获取到变量存储结果。

   //在控制台中打印

   console.log(变量名字)


 

```
<script type="text/javascript">


 //变量基本使用

 //第一步:声明,在使用变量之前，务必、一定、切记需要通过关键字var进行声明一次。

 var age;

 //第二步:赋值

 age = 123;

 //第三步：使用

 console.log(age);

 console.log(age);

</script>
```

- l 在使用变量之前，务必需要通过关键字var，进行声明一次。（声明）

- l 在声明变量以后，可以将右侧任意类型的字面量通过赋值运算符（一个等号）赋值给左侧的变量。（赋值）

- l 通过访问变量名字，可以获取到变量存储的结果。（使用）


![img](https://img.gyxnb.top/img001/clip_image048.jpg)

## 4.2变量使用注意事项

![img](https://img.gyxnb.top/img001/clip_image050.jpg)

  var hobby;

  console.log(hobby);

- l 一个变量，仅仅是声明了，但是没有赋值。默认初始值为未定义类型的特殊值undefined。


![img](https://img.gyxnb.top/img001/clip_image052.jpg)

```


<script type="text/javascript">


  //变量使用：分为三部分，声明、赋值、使用

  //第一步：需要通过关键字var进行声明一次变量；

  var hobby;

  //赋值：第一次赋值

  hobby = "我爱你塞北的雪";

  //使用

  console.log(hobby);

  //赋值：第二次赋值

  hobby = 123;

  //使用

  console.log(hobby);

  //赋值：第三次赋值

  hobby = "啊呀呦";

  //使用

  console.log(hobby);

</script>
```

l 一个变量在声明一次以后，可以进行多次赋值。后者赋值的数据会层叠前者赋值的数据。

```


<script type="text/javascript">


 console.log(age);

</script>
```

- l 上面写法是错误的，因为使用变量之前，务必需要通过关键字var进行声明。


![img](https://img.gyxnb.top/img001/clip_image054.jpg)

```


<script type="text/javascript">


  //注意事项

  var age;

  age = 100;

  console.log(age);

  console.log("age");

</script>
```

- l 变量名字外层不需要加上双引号。

- l 如果访问变量的时候，变量外层有双引号。它就不是变量（获取不到变量存储结果）。因为他是字符串了，不是变量了。


## 4.3其他声明方式

![img](https://img.gyxnb.top/img001/clip_image056.jpg)

```


<script type="text/javascript">


  //常用方式1

  var hobby = "吃饭睡觉打豆豆";

    hobby = 12306;

  console.log(hobby);

  //常用方式2

  var name = "曹操",age = 100, sex = "男";

  console.log(name,age,sex);

</script>
```

- l 我们可以将第一步（声明）和第二步进行合并。

- l 一个关键字var可以同时声明多个变量，多个变量之间，需要用逗号隔开。


## 4.4命名标识符规范

概述：从今天开始，我们需要知道一件事情。就是给变量、函数起名字的时候。务必眼遵守下面规则。

规则：

1. \1.    可以是数字、英文字母、下划线、美元符号

2. \2.    不能以数字开头

3. \3.    不能是关键字、保留字


 var 2b;

 var @__@;

 var var;

 var class；

1. l 第一个错误:是以数字开头。

2. l 第二个错误:出现的特殊符号@。

3. l 第三个错误:出现关键字var。

4. l 第四个错误:出现保留字class。


 

## 4.5变量声明提升*

概述:各大浏览器的厂商都有属于自己的解析器。在翻译代码的时候，会将变量的声明部分，提升到当前的作用域的最上方。

解析器：各大浏览器厂商都有属于自己的解析器。说白了，就是将你的代码翻译给浏览器，让浏览器知道你写的是什么。

作用域：书写代码的范围。

![img](https://img.gyxnb.top/img001/clip_image058.jpg)   

![img](https://img.gyxnb.top/img001/clip_image060.jpg)            

```


<script type="text/javascript">


 console.log(age);

 //声明部分：需要用关键字var进行声明变量一次

 var age ;

 //赋值：将右侧任意类型的字面量、或者是数学计算完的结果。赋值给左侧变量

 age = 100;

 //使用变量：通过访问变量名字、获取到变量存储的数据

 console.log(age);

/*************************相当于下面写法*********************/

 var age;

 console.log(age);//undefined

 age = 100;

 console.log(age);//100

</script>
```

1. l 一个变量，如果只是声明了。没有赋值，默认初始值为undefined

2. l 当程序中出现变量，解析器做的第一件事情。将变量的声明部分，提升到当前作用域最上方。（赋值部分不会提升）


# 五、数据类型的判断

概述：在JS当中，我们可以利用关键字typeof，它主要的作用是可以检测任意类型的字面量或者变量存储的数据为什么类型的数值。

![img](https://img.gyxnb.top/img001/clip_image062.jpg)

```


<script type="text/javascript">


  <script type="text/javascript">


  //typeof:用来检测数据的类型用的

  //检测字面量的数据类型

  console.log(typeof "我爱你塞北的大雪呀");

  console.log(typeof 123);

  console.log(typeof 3.14);

  console.log(typeof Infinity);

  console.log(typeof NaN);

  console.log(typeof true);

  console.log(typeof undefined);

  //null属于Null类型的，不是Object

  console.log(typeof null);

  //检测变量存储的数据的类型

  var age = 666;

    age = "我是祖国的老花骨朵";

  console.log(typeof age);

</script>
```

- l typeof关键字可以检测数据的类型。

- l 使用的时候，关键字typeof + 空格+检测数据即可。


# 六、数据类型的转换

概述：我们今天学习了两种数据类型的数值。字符串类型、数字类型。

1. \1.    将数字类型的数据转换为字符串类型的数据

2. \2.    将字符串类型的数据转换为数字类型的数据


## 6.1数字转换为字符串

概述：在JS当中，我们可以通过连字符（+），将数字类型的数据转换为字符串。

切记：在JS当中这个+真的比较特殊。

1. l 如果语句当中没有出现字符串，这个加号（+），就是数学的加法。（可以进行数学的加法运算）

2. l 如果语句当中出现了字符串，这个加号（+），就不是数学的加法了。是所谓连字符。可以将数据从左到右变为字符串。


![img](https://img.gyxnb.top/img001/clip_image064.jpg)

```


<script type="text/javascript">


  //语句当中没有出现字符串，加号即为数学的加法（进行数学的加法运算）

  console.log(66 + 123);

  console.log(3.14 + 2.99);

  //语句当出现字符串，加号，所谓连字符，可以将数据从左到右拼接为一个字符串

  console.log("张三" + "李四");

  console.log("习大大" + 180);

  console.log("123" + 66);

</script>
```

- l 不要拿生活的角度加号。

- l 语句当中没有出现字符串，这个加号即为加法。可以进行数学运算。

- l 语句当中出现了字符串，这个加号（连字符）。将数据从左到右拼接为一个整体字符串。


![img](https://img.gyxnb.top/img001/clip_image066.jpg)

```


<script type="text/javascript">


  //经典面试题

  var num = 123;

  var num1 = "666";

  console.log(num + num1); 

</script>
```

- l 因为num1是字符串类型数据，当前这个加号连字符（将数据从左到右转换为字符串）


![img](https://img.gyxnb.top/img001/clip_image068.jpg)

```


<script type="text/javascript">


 //老师：想在控制台中打印一句话，我是小明我今年18岁了

  var age = 18;

  console.log("我是小明我今年age岁了");

  console.log("我是小明我今年"+age+"岁了");

</script>
```

- l 第一种写法：age不是变量，它只是字符串中的三个字符。不能变量存储的数据。

- l 第二种写法：age是变量，而且加号也是连字符，可以将数据从左到右转换为字符串。


总结：以后再遇见加号：先问问自己是加法、还是连字符。

## 6.2字符串转换为数字

![img](https://img.gyxnb.top/img001/clip_image070.jpg)![img](https://img.gyxnb.top/img001/clip_image072.jpg)

![img](https://img.gyxnb.top/img001/clip_image074.jpg)

概述：在JS当中，我们可以通过内置函数parseInt和parseFloat将字符串转换为数字。 

1. \1.    内置函数parseInt，可以将字符串中的数字形式字符串转换为数字。（整数部分）

2. \2.    内置函数parseFloat，可以将字符串中的数字形式的字符转换为数字。（精确到小数部分）。


![img](https://img.gyxnb.top/img001/clip_image076.jpg)

```


<script type="text/javascript">


 //将字符串转换为数字

 //parseInt:可以将字符串中的数字形式的字符转换为数字（整数部分）

 console.log(parseInt("12306"));

 console.log(parseInt("3.14"));

 console.log(parseInt("666我很喜欢你_$ABC么么哒123"));

 console.log(parseInt("贾成豪18岁"));

</script>
```

- l 内置函数parseInt，它主要的作用是可以将字符串中的数字形式字符，转换为数字（整数部分）

- l 在进行转换的时候，从左到右进行转换，如果是数字形式字符，转换为数字。遇见了非数字形式字符，后面数据就不在进行转换。


![img](https://img.gyxnb.top/img001/clip_image078.jpg)

 console.log(parseFloat("3.14"));

 console.log(parseFloat("6.789么么哒123"));

 console.log(parseFloat("大帅哥张杰18"));

- l parseFloat的使用方式和parseInt是一模一样的。只不过精确度，精确到小数部分。


# 七、提示框

概述：提示框prompt，可以在浏览器正上方弹出一个提示框。用户是可以输入数据。

我们可以获取到用户输入进来的数据，利用这些用户输入进来的数据，进行编程。

![img](https://img.gyxnb.top/img001/clip_image080.jpg)

```


<script type="text/javascript">


 //提示框

 var age = prompt("帅哥,你今年多大了呀");

 console.log(age);

 console.log(typeof age);

</script>
```

- l 用户在提示框中输入的进来的数据，我们可以用变量进行存储。

- l 用户输入进来的数据都是字符串类型的数据。


# 八、数学运算符

概述：在JS语言当中，也有数学运算符（数学操作符）。

其实数学运算符即为：加（+）、减（-）、乘（*）、除（/）、去余数（%）

口诀：先算乘除、后算加减。如果有小括号先算小括号里面的。

![img](https://img.gyxnb.top/img001/clip_image082.jpg)

```


<script type="text/javascript">


  //数学运算符

  console.log(6 + 6 + 3);

  console.log(100 - 20 + 10);

  console.log(66 * 11);

  console.log(24/12);

  //去余数

  console.log(6 % 3);

  console.log(3 % 4);

</script>
```



# 九、数学对象

![img](https://img.gyxnb.top/img001/clip_image084.jpg)

![img](https://img.gyxnb.top/img001/clip_image086.jpg)

![img](https://img.gyxnb.top/img001/clip_image088.jpg)

![img](https://img.gyxnb.top/img001/clip_image090.jpg)

概述：在JS语言当中，给我们提供了一个内置的数学对象（Math），这个对象拥有很多的属性和方法提供给我们使用。

对象：在JS当中，我们经常将引用类型的数据称之为对象。

属性和方法：今天任务是知道怎么使用即可。

![img](https://img.gyxnb.top/img001/clip_image092.jpg)

```


<script type="text/javascript">


  //Math对象的基本使用

  console.log(typeof Math);

  console.log(Math);

  //数学对象的属性的使用

  console.log(Math.PI);

  //数学对象方法使用

  //获取数字绝对值

  console.log(Math.abs(-99999));

  //获取某一个数字N次幂

  console.log(Math.pow(2,3))

  //随机一个0~2之间的小数

  console.log(Math.random());

</script>
```

- l Math数学对象，提供很多数学方法。

- l Math对象的属性后面不需要加上小括号。

- l Math对象的方法后面紧随小括号。

- l Math数学对象的方法中，如果传递多个参数，需要用逗号隔开。


 


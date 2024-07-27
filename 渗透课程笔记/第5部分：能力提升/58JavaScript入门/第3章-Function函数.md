#         JavaScript基础第五天 

# 一、数组

![img](https://image.201068.xyz/assets/clip_image002-16900394289221.jpg)

概述:在很多的编程语言当中都有数组存在。数组你可以理解为是一个大容器，这个容器可以存储很多的任意类型数值。存储的数据都是有序的数据。在JS这门语言当中数组利用中括号进行表示。

<script type="text/javascript">

  //在JS当中用中括号代表数组

  console.log([]);

  //数组在JS当中属于引用类型数据

  console.log(typeof []);

  //数组可以存储很多任意类型数据

  console.log([1,true,NaN,"吃饭",null,function(){}]);

  //数组在使用的时候为了方便，

  //可以将数组赋值给变量进行存储，通过访问变量名字就可以操作数组

  var arr = ["吃饭","睡觉","打豆豆",1,NaN,false];

  console.log(arr);

</script>

l 数组利用中括号进行表示，而且是引用类型数据。

l 数组里面存储的数据我们经常叫做‘元素’，多个元素之间利用逗号隔开。

l 以后再使用数组的时候，最好把数组赋值给变量使用。这样操作比较方便。

## 1.1数组基本使用

概述:在JS当中数组（引用类型数据）可以存储很多任意类型数据且有序存储。当然也可以读取、修改、添加数据。

<script type="text/javascript">

 //数组:可以存储任意类型的元素

 var arr = ["吃饭","睡觉","打豆豆",true,NaN];

 //读取数据:可以利用枚举法获取数组里面元素

 console.log(arr[0]);

 console.log(arr[1]);

 console.log(arr[4]);

 console.log(arr[99]);

</script>

l 数组里面元素可以通过枚举法获取到。

l 枚举法：数组后面紧随一个中括号，中括号里面放置的是获取元素对应的索引值||下角标。

l 元素的索引值是从数字零开始的。

l 数组枚举元素的时候，下角标越界程序不会报错，默认返回的是undefined

<script type="text/javascript">

 //数组:可以存储任意类型的元素

 var arr = ["吃饭","睡觉","打豆豆",true,NaN];

 //读取数据:可以利用枚举法获取数组里面元素

 console.log(arr[0]);

 console.log(arr[1]);

 console.log(arr[4]);

 console.log(arr[99]);

 //修改已有的数据

 arr[1] = "学习";

 arr[4] = '小帅哥';

 //给数组添加新的数据

 arr[5] = false;

 arr[999] = '么么哒';

 console.log(arr);

</script>

l 数组：可以修改已有的元素数值、添加新的元素。

# 二、数组常用属性与方法

概述:官方给我们提供了很多的数组的属性与方法，可以用来操作数组。

## 2.1length属性

![img](https://image.201068.xyz/assets/clip_image004-16900394289232.jpg)

概述:数组拥有length属性，它主要的作用是可以获取到数组元素个数。

<script type="text/javascript">

 //声明一个数组

 var arr = ["吃饭","睡觉","打豆豆",true,[1,2,3]];

 //length属性:获取当前数组的元素总个数

 console.log(arr.length);

 console.log(arr[0]);

 console.log(arr[3]);

 console.log(arr[4][1]);

</script>

l 数组length属性，主要的作用是可以获取到元素的总个数。

l 数组里面元素可以是任意类型数值，出现数组嵌套数组情况（二维数组）

<script type="text/javascript">

  //数组的length属性：经常结合循环语句遍历数组里面元素

  var arr = ["张三","李四","王五","贾六","曹操","张飞"];

  for(var i = 0 ; i < arr.length;i++){

​     console.log(arr[i]);

  }

</script>

l 数组的length属性经常结合循环语句进行遍历数组里面元素。

## 2.2push与pop*****

![img](https://image.201068.xyz/assets/clip_image006-16900394289233.jpg)![img](https://image.201068.xyz/assets/clip_image008-16900394289234.jpg)

概述:他们两者都是数组方法。它主要的作用分别是：

l push:可以向数组尾处添加一个或者多个元素

l pop:可以在数组的尾处移除一个元素

<script type="text/javascript">

 //数组

 var arr = ["小鸡","三饼","四条","白板"];

 //push:可以在数组的尾处添加一个或者多个元素

 arr.push("曹操");

 arr.push("刘备",NaN,"习大大");

 console.log(arr);

 //数组

 var arr1 = ['手机','电视','彩电','洗衣机'];

 //pop:可以在数组的尾处移除一个元素

 arr1.pop();

 arr1.pop();

 console.log(arr1);

</script>

## 2.3unshift与shift方法*****

概述：他们两者也是数组的方法，主要的作用分别是：

l unshift：可以向数组头部添加一个或者是多个元素

l shift:可以向数组的头部移除一个元素

<script type="text/javascript">

 //数组

 var arr = ["小猫",'小狗','大鹅','小鸡'];

 //unshift:可以向数组的头部添加一个或者多个元素

 arr.unshift("乌龟");

 arr.unshift('大叔',"清水");

 console.log(arr);

 //数组

 var arr1 = [1,2,3,4,5,6];

 //shift:可以向数组的头部删除一项元素

 arr1.shift();

 arr1.shift();

 console.log(arr1);

</script>

## 2.4join与reverse方法

![img](https://image.201068.xyz/assets/clip_image010-16900394289237.jpg)![img](https://image.201068.xyz/assets/clip_image012-16900394289235.jpg)

概述：他们两者也属于数组方法，他们的作用分别是：

l join：主要的作用是可以通过某一个字符将数组拼接转换为字符串。

l reverse:可以把当前的数组的元素进行倒置。

<script type="text/javascript">

 //数组

 var arr = [1,2,3,4,5,6];

 //join:可以通过某一个字符将数组转化为字符串

 var str = arr.join("*");

 var str1 = arr.join('');

 console.log(str,str1);

 

 //数组

 var arr = ['北京',"上海",'深圳','广州'];

 arr.reverse();

 arr.reverse();

 console.log(arr);

</script>

l 数组的join方法：可以通过某一个字符串将数组转换为一个字符串。【对起始数组没有任何影响】

l 数组的reverse方法：可以将当前的数组的元素进行倒置。

## 2.5indexOf与includes方法

indexOf:索引值

includes: 包含

概述:他们两者也是数组的方法。他们两者作用分别是：

l indexOf:它可以获取数组当中某一个元素的索引值【下脚标】

l includes:它主要的作用是检测某一个元素是不是当前这个数组的。如果是【返回布尔值真】，否则【返回布尔值假的】

<script type="text/javascript">

 //数组

 var arr = ['吃饭','睡觉','打豆豆','烫头'];

 //indexOf:这个方法主要的作用是可以获取到某一个元素的索引值

 console.log(arr.indexOf("吃饭"));

 console.log(arr.indexOf('打豆豆'));

 console.log(arr.indexOf('么么哒'));

 //includes:这个方法主要的作用是检测数据是不是当前数组的

 console.log(arr.includes("吃饭"));

 console.log(arr.includes('贾称号'));

</script>

## 2.6slice与splice方法

slice||splice:切割、分割

概述:他们两者也是数组方法，他们主要的作用是：

l slice：从起始数组当中切割出一个新的子数组

l splice:可以对数组进行切割、插入、替换。

arr.slice(起始索引值，结束的索引值); 包含起始的索引值元素，但是不包含结束索引值元素

<script type="text/javascript">

 //数组

 var arr = ['张飞','刘备','关羽','马超','黄忠','曹操'];

 //slice:主要的作用是切割某一个数组并且返回一个新的数组

 //这个方法传参至少一个参数【都是数组的索引值】

 var newArr = arr.slice(2);

 var newArr1= arr.slice(1,3);

 console.log(newArr1);

 console.log(arr);

</script>

l slice方法：数组通过这个方法可以切割出一个新的数组【slice对于起始数组没有任何影响】

l slice方法：传递参数至少一个、最多两个参数。【起始索引值、结束索引值）

 <script type="text/javascript">

   //数组

   var arr = [55,33,21,88,57,48,29];

   //splice:可以对于当前数组进行切割、插入、替换元素操作

   //切割:第一个参数切割起始位置索引值

   //传递一个

   var newArr = arr.splice(2);

   // console.log(newArr);

   //传递两个参数:第一个参数代表的是切割起始位置、第二个参数切割长度

   var newArr = arr.splice(2,2);

   console.log(newArr);

 </script>

l splice:可以对于起始数组进行切割，返回一个新数组【对于起始数组是由影响的】

l 第一个参数：切割的起始位置索引值，第二个参数：切割元素的长度

 <script type="text/javascript">

   //数组

   var arr = [55,33,21,88,57,48,29];

   //splice:可以对于当前数组进行切割、插入、替换元素操

   //插入：代表从索引值为2的地方切割出零个元素，插入进一个元素么么哒

   var newArr = arr.splice(2,0,"么么哒");

   console.log(arr);

   //替换:代表从起始数组索引值2切割出两个元素，使用马老师、贾老师进行替换。

   var newArr = arr.splice(2,2,"马老师",'贾老师');

   console.log(newArr);

   console.log(arr);

 </script>

# 三、数组的实战练习

## 3.1实战练习1

问题:请你设计一个程序，需要声明一个函数rev(arr,n)。

比如：【1,2,3,4,5】 1  当前rev函数返回一个数组  【5,1,2,3,4】

   【1,2,3,4,5】 2  当前rev函数返回一个数组 【4,5,1,2,3】

   【1,2,3,4,5】 3  当前rev函数返回一个数组  【3,4,5,1,2】

<script type="text/javascript">

  //声明一个函数

  function rev (arr,n){

   //循环语句----->进行N次的尾删头增

   for(var i = 0 ; i < n;i++){

​       //将数组的尾处元素删除

​       var result = arr.pop();

​       //将数组尾巴删除掉元素添加到数组头部

​       arr.unshift(result);

   }

   //返回结果

   return arr;

  }

  //调用函数

  var newResult = rev([1,2,3,4,5],2);

  var newResult1 = rev([33,22,11],1);

  console.log(newResult);

  console.log(newResult1);

</script>

l 数组的pop方法：可以将数组尾处一项元素移除。【这个方法可以将移除掉元素返回】

l 数组的unshift方法：可以在数组头部添加元素【一个||多个】

## 3.2实战练习2

问题：请你设计一个程序，需要你封装一个函数Max(arr),需要将数组中最大的数值返回。

比如：【1,2,3,4,9,6】     返回结果  9

完整代码：

<script type="text/javascript">

  //声明一个函数

  function Max (arr){

   //用来记录数组当中最大数值

   var note = arr[0];

   for(var i = 0 ; i < arr.length;i++){

​        if(arr[i] > note){

​          note = arr[i];

​        }

   }

   return note;

  }

  //调用函数

  var result = Max([22,44,1,6]);

  var result1 = Max([-1,99,22,45,88,2]);

  console.log(result);

  console.log(result1)

</script>

## 3.3实战练习3

问题：请你编写一个程序，需要封装一个函数uniq(arr),这个函数功能是可以将数组中重复元素去除。

比如: [1,2,2,3,4,4,5,6]   返回结果  【1,2,3,4,5,6】

代码如下：

<script type="text/javascript">

 //indexOf方法:获取到数组当中某一个元素索引值【数组当中没有这个元素:-1】

 function uniq (arr){

   //声明一个空的数组：将来装载没有重复元素的数组

   var result = [];

   //循环遍历实参这个数组，看看这个数组里面元素在空数组有没有出现

   for(var i = 0 ; i <arr.length;i++){

​        if(result.indexOf(arr[i])==-1){

​            //将result数组当中添加没有重复元素

​            result.push(arr[i]);

​        }

   }

   return result;

 }

 //调用函数

 var result1 = uniq([1,2,2,2,3,4,4,4,4,5,6]);

 var result2 = uniq([22,22,4,66,66,8,9]);

 console.log(result2);

 console.log(result1);

</script>

# 四、数据类型相等判断*****

概述：基本类型数据：数字、字符串、布尔、未定义类型、空对象

   引用类型数据【Object】：函数、数组

注意：我们在书写代码的时候，代码存储计算机内存当中。计算机内存中分：五大区域。

常用区域：堆空间、栈空间。

 

 

 

 

 

基本数据类型：依据的是数值是否一样。

<script type="text/javascript">

 //基本数据类型数值相等判断

 var a = 100;

 var b = 100;

 console.log(a==b);

</script>

![img](https://image.201068.xyz/assets/clip_image014-16900394289236.jpg)

l 这两个数值100，存储于内存当中栈空间。

l 而且a与b这两个变量，存储的就是‘房间’中主人公100

<script type="text/javascript">

  var a = [];

  var b = [];

  console.log(a==b);

</script>

![img](https://image.201068.xyz/assets/clip_image016-16900394289238.jpg)

l 引用类型数据存储于内存当中堆空间。

l 而当前变量a与变量b，存储不是房间里面‘主人公’，存储的是‘门牌号’，由于‘门牌号’不同，因此这两个数据不相等。

门牌号：即为内存中地址



#          JavaScript基础第六天 

# 一、字符串属性与方法

概述：官网也给字符串提供很多的属性与方法，用来进行字符串的操作。

## 1.1length

概述：字符串拥有length属性，它主要的作用是可以获取到字符串中字符的个数。

<script type="text/javascript">

 //length属性：主要的作用是可以获取到字符串总字符的个数

 var str = "我爱你我的祖国";

 console.log(str.length);

</script>

l 字符串的length属性，主要的作用是可以获取到字符个数。

l length属性也经常结合循环语句一起使用，遍历字符串中每一个字符

<script type="text/javascript">

  //length属性：经常结合循环语句一起使用，用来遍历字符

  var str = "我买火车票就去12306";

  for(var i = 0 ; i< str.length;i++){

​    console.log(str[i]);

  }

</script>

## 1.2indexOf与lastIndexOf

概述：他们两者是字符串的方法，主要的作用是分别是：

l indexOf:获取到第一个匹配到的字符的索引值。

l lastIndexOf:获取到的最后一个匹配到的字符的索引值。

<script type="text/javascript">

  //indexOf:获取到一个匹配到的字符串的 索引值

  var str = "我爱你我的祖国";

  console.log(str.indexOf("我"));

  console.log(str.indexOf('么么'));

  console.log(str.lastIndexOf('我'));

</script>

l 如果字符在字符串中没有出现，返回的是数字-1

## 1.3toLowerCase与toUpperCase

概述：他们两者也是字符串方法，他们两者主要的作用是分别是：

l toLowerCase：将字符串中英文字符变为小写

l toUpperCase:将字符串中英文字符变为大写

<script type="text/javascript">

 var str = "我喜欢英文aBcD";

 var newStr = str.toUpperCase();

 var newStr1 = str.toLowerCase();

 console.log(newStr);

 console.log(newStr1);

 console.log(str);

</script>

l 他们两者属于字符串方法：是将字符串英文字符变为大小写。【都是返回一个新的字符串，对于起始字符串没有影响】

## 1.4search与split

![img](https://image.201068.xyz/assets/clip_image002-169003946808617.jpg)![img](https://image.201068.xyz/assets/clip_image004-169003946808618.jpg)

概述：他们两者是字符串方法，他们主要的作用是：

l search:它的作用是可以获取到某一个字符的索引值。

l split:它的作用是可以将字符串通过某一个字符切割为数组。

<script type="text/javascript">

  var str = "我是祖国的老祖花骨朵";

  //search:获取到某一个字符的索引值

  console.log(str.search("祖"));

</script>

<script type="text/javascript">

   var str = "我今天买了一个华为手机花了我5888";

   //split:可以将字符串通过某一个字符分割为一个数组

   var arr = str.split("华");

   var arr1 = str.split("");

   console.log(arr1);

</script>

l search:主要的作用是可以获取到某一个字符的索引值。

l split:可以将字符串通过某一个字符将字符串切割为一个数组。

## 1.5substring与substr方法

概述:他们两者也是字符串方法，他们主要的作用是：

l substring:它是字符串方法，主要的作用是在父串当中切割出一个子串 

str.substring(起始索引值，结束索引值)  包含起始索引值、不包含结束索引值

l substr:它也是字符串方法，它主要的作用也是从父串当中切割出一个子串

str.substr(起始索引值，切割长度)

<script type="text/javascript">

 var str = "我们在学习JS基础语法,将来学习DOM，我们就可以做很多可以看见效果了";

 //substring:可以切割出一个新的字符串，对于起始字符串没有影响

 var newStr = str.substring(5);

 console.log(newStr);

 var newStr1 = str.substring(5,8);

 console.log(newStr1);

</script>

## 1.6replace与match方法

![img](https://image.201068.xyz/assets/clip_image006-169003946808619.jpg)![img](https://image.201068.xyz/assets/clip_image008-169003946808620.jpg)

概述:他们两者也是字符串方法，主要的作用分别是：

l replace:可以替换某一个字符串中复合条件的字符进行替换。

l match:可以进行将某一个字符串中符合条件的第一个字符匹配出来，返回的是一个数组。

<script type="text/javascript">

 var str = "我今天买了一个华为手机,花了我5688元";

 //replace:可以将某一个字符串中符合条件的字符进行替换

 var newStr = str.replace("华为","vivo");

 console.log(newStr);

 console.log(str);

</script>

<script type="text/javascript">

 var str = "我喜欢中国,因为中国好吃的东西很多";

 //match:可以将某一个字符串中第一个符合条件的字符匹配出来，返回一个数组

  var arr = str.match("中国");

  console.log(arr);

</script>

# 二、字符串的实战练习

## 2.1实战练习1

问题:请你设计一个程序，需要声明一个函数rev(str),这个函数功能如下：

比如：rev(“我爱你北京天安门”)  功能：返回一个结果是一个字符串 门安...爱我

解决方案1：

<script type="text/javascript">

  //问题:封装一个函数，函数功能是可以将实参传递进来的字符进行倒置返回。

  function rev (str){

​    //累加器

​    var result = '';

   for(var i = str.length -1; i >=0;i--){

​        result += str[i];

   }

   return result;

  }

  //调用函数

  var newStr = rev("我爱你北京天安门");

  console.log(newStr);

</script>

解决方案2：

<script type="text/javascript">

  function rev (str){

   //split:可以将字符串切割为数组

   var arr = str.split("");

   //reverse:可以将数组元素进行倒置

   arr.reverse();

   //join:可以将数组转换为字符串

   var result = arr.join('');

   //返回结果

   return result;   

  }

  //调用函数

  var newStr = rev("我爱你北京天安门");

  console.log(newStr);

</script>

![img](https://image.201068.xyz/assets/clip_image010-169003946808621.jpg)

## 2.2实战练习2

问题:请你设计一个程序，封装一个函数changeString(str),功能是将字符串中英文进行大小写转换返回结果。

比如:’ILikeBeiJing’   返回结果：大小变为小写，小写变为大写返回。

代码如下：

<script type="text/javascript">

  //将英文字母大小写进行转换

  function changeString (str){

   //无非将大写变为小写

   //小写变为大写

   //累加器

   var result = '';

   for(var index = 0 ; index < str.length;index++){

​       //想获取到全部大写英文字母

​       if(str[index] < 'a'){

​           //进入这个条件语句：一定是大写英文字母

​            result += str[index].toLowerCase();

​       }else{

​           //进入这个条件语句：一定是小写英文字母

​            result += str[index].toUpperCase();

​       }

   }

​    return result;

  }

  //调用函数

 var newStr = changeString("ILikeBeiJing");

 var newStr1 = changeString('Tom');

 console.log(newStr);

 console.log(newStr1);

</script>

## 2.3实战练习3

问题:请你编写一个程序，需要你设计一个函数fun（str），这个函数功能是将每一个英文单词的首个字母变为大写。

![img](https://image.201068.xyz/assets/clip_image012-169003946808622.jpg)

比如:fun(“i like beijing”);    返回结果 :I Like Beijing 

<script type="text/javascript">

  //函数功能:将每一个字符串的首个英文字母变为大写返回。（英文单词之间有空格的）

  function fun (str){

   //获取到实参中每一个英文单词

   var arr = str.split(" ");

   console.log(arr);

   //累加器

   var result = "";

   //循环遍历数组：获取到每一个英文单词

   for(var i = 0 ; i < arr.length ;i++){

​     result += arr[i][0].toUpperCase() + arr[i].substr(1) +" ";

   }

   return result;

  }

  //调用函数

  var newStr = fun("welcome to beijing");

  console.log(newStr);

</script>

# 三、JSON数据格式*

概述：JSON【JavaScript Object Nonation】 JS对象一种标记法。

在JS当中是有JSON数据格式，JSON数据格式是由一个大的花括号表，JSON数据格式在JS当中是引用类型数据。JSON数据格式作用如下：

l 前端工程师可以和后台工程师进行数据交换

l JSON数据格式可以通过KV对存储数据、读取、修改、添加数据。

语法格式：

{

  “name”: “小明”，

  “age”:12

}

l JSON数据格式经常用存储、读取、修改、新增数据操作。

l JSON数据格式是通过K V对进行存储数据。

l JSON数据格式K务必需要加上双引号。

## 3.1存储数据

<script type="text/javascript">

 //JSON数据格式：大花括号表示

 console.log({});

 //JSON数据格式：引用类型数据

 console.log(typeof {});

 //JSON数据格式   存储数据

 var info = {

​     "name":"孙悟空",

​     "age": 12,

​     "marray":true,

​     "hobby":["吃饭","睡觉","打豆豆"]

 }

 console.log(info);

</script>

l JSON数据格式常用功能即为存储数据

l JSON存储数据的时候K-V键值对存储（K：务必加上双引号）

l JSON存储的时候右侧V可以是任意类型数值。

## 3.2读取数据

概述:JSON数据格式可以通过点语法||枚举法读取数据。

 //JSON数据格式   读取数据

 //点语法读取数据

 console.log(info.age);

 console.log(info.marray);

 console.log(info.hobby);

 //通过枚举法读取数据

 console.log(info["name"]);

 console.log(info['age']);

## 3.3修改已有数据

概述：我们也可以通过点语法||枚举法修改JSON数据格式里面的V；

 //点语法进行修改

 info.name = "猪八戒";

 info['age'] = 88;

 console.log(info);

## 3.4添加新的KV键值对

 //JSON数据格式 添加KV键值对

 info.sex = "男";

 info['color'] = "黄色";

 console.log(info);

l 点语法||枚举法在没有当前这个K的时候，给JSON数据格式在添加新的KV

l 点语法||枚举法在有K情况，在修改JSON中KV

 
#           DOM第一天

 

# 一、DOM认知

问题:JavaScript是由几部分组成的呀？

l ECMAScript：简称【ES】，它是欧洲计算机协会，大概每年的六月中旬定制语法规范。

l DOM：全称【document object model】即为文档对象模型

l BOM：全称【browser object model】即为浏览器对象模型

## 1.1节点树

概述:节点即为标签。节点之间这种关系，我们称之为‘节点树’。因为很想一颗大树扎根。

DOM【document object model】:文档对象模型，你可以理解为是整个节点树最外层‘根元素’。

DOM其实就是JS语言中内置引用类型document对象，DOM对象经常用来操作节点（标签）

比如：操作节点样式、属性、文本等等。

![img](https://image.201068.xyz/assets/clip_image002-16900389555941.jpg)

<script type="text/javascript">

 //DOM:其实就是内置document对象，引用类型数据

 console.log(document);

 console.log(typeof document);

</script>

## 1.2DOM属性

概述:DOM【document object model】：它在JS当中，是引用类型数据，官方给我们提供很多属性、方法进行操作。

<script type="text/javascript">

 //DOM:常用属性

 //documentElement:获取到节点树的html标签

 console.log(document.documentElement);

 //head:获取到节点树的head标签

 console.log(document.head);

 //title:获取到节点title标签的文本

 console.log(document.title);

 //body:获取到节点body

 console.log(document.body);

</script>

l DOM官方给我们提供很多属性、方法。用来操作节点树上面节点。

## 1.3DOM方法

概述:DOM对象，官方也给我们提供很多方法用来操作节点树上的标签。

l getElementById:它是DOM对象方法，可以通过标签ID选择器，在JS当中获取标签。

<script type="text/javascript">

  //getElementById方法:可以获取到节点树上任意节点

  //【需要给标签添加id属性，通过id选择器获取】

  var element = document.getElementById("box");

  var eleCur = document.getElementById("cur");

  var eleLi = document.getElementById("me");

  console.log(element);

  console.log(eleCur);

  console.log(eleLi);

  console.log(typeof element);

</script>

l getElementById方法：可以通过标签ID选择器获取对应节点。

l 一般我们将script标签放在程序最底部。

l 不管节点（标签）在网页中嵌套关系如何复杂。都可以通过这个方法获取到。

l 注意：标签（节点）在JS当中属于引用类型数据。

#            DOM第二天

# 一、事件对象

![img](https://image.201068.xyz/assets/clip_image002-16900389774263.jpg)

概述:任意节点树上的节点（标签），都可以绑定一个或者多个事件。当用户触发事件的时候，系统会自动给事件处理函数传递实参，而这个参数即为事件对象（事件对象给我们传递很多信息）。

<script type="text/javascript">

 //获取节点

 var div = document.querySelector("div");

 div.onclick = function(event){

   //对于高级浏览器：谷歌、IE8以上的浏览器---->event

   //对于低级浏览器：IE8以下的，事件对象作为BOM对象属性

   var e = event||window.event;

   console.log(e);

 }

</script>

l 当事件处理函数执行的时候，系统会自动注入实参，我们用形参接受【事件对象】

l 在不同浏览器中事件对象是有兼容问题。使用短路语句进行兼容。

## 1.1获取鼠标位置

概述：当用户触发事件的时候，系统会自动给事件处理函数注入实参【事件处理函数】，

它给我们提供很多信息，可以获取鼠标位置。

### 1.1.1screenX||screenY

概述：他们两者是事件对象属性，主要可以获取鼠标位置。获取鼠标位置零零点在电脑屏幕左上角。

![img](https://image.201068.xyz/assets/clip_image004-16900389774264.jpg)

<script type="text/javascript">

  //获取节点

  var inn = document.querySelector('.inner');

  //鼠标在整个网页当中移动

  document.onmousemove = function(event){

​     //短路语法进行兼容

​     var e = event||window.event;

​     inn.innerHTML = "screenX:"+ e.screenX + "screenY"+e.screenY;

  }

</script>

### 1.1.2pageX||pageY

概述：他们两者也是事件对象属性，主要作用也是获取鼠标位置。是网页主题部分左上角为零零点。

![img](https://image.201068.xyz/assets/clip_image006-16900389774265.jpg)

<script type="text/javascript">

  //获取节点

  var inn = document.querySelector('.inner');

  //鼠标在整个网页当中移动

  document.onmousemove = function(event){

​     //短路语法进行兼容

​     var e = event||window.event;

​     inn.innerHTML = "screenX:"+ e.screenX + "screenY"+e.screenY+"<br/>";

​     inn.innerHTML += "pageX:"+e.pageX +"pageY:"+e.pageY;

  }

</script>

### 1.1.3clientX||clinetY

概述:他们两者也是事件对象属性，主要作用是获取鼠标位置。但是他的零零点是按照可视区域左上角为零零点。

![img](https://image.201068.xyz/assets/clip_image008-16900389774266.jpg)

### 1.1.4offsetX||offsetY

概述：他们两者也是事件对象属性，他们两者主要的作用也是获取鼠标位置。

获取数据类似pageX||pageY。但是这个获取数据零零点，会收到子元素坐标体系影响。

![img](https://image.201068.xyz/assets/clip_image010-16900389774267.jpg)

<script type="text/javascript">

  //获取节点

  var inn = document.querySelector('.inner');

  //鼠标在整个网页当中移动

  document.onmousemove = function(event){

​     //短路语法进行兼容

​     var e = event||window.event;

​     inn.innerHTML = "screenX:"+ e.screenX + "screenY"+e.screenY+"<br/>";

​     inn.innerHTML += "pageX:"+e.pageX +"pageY:"+e.pageY+"<br/>";

​     inn.innerHTML +="clientX"+e.clientX +"clinetY"+e.clientY+"<br/ >";

​     inn.innerHTML +="offsetX"+e.offsetX +"offsetY"+e.offsetY;

  }

</script>

## 1.2原生JS实现拖拽效果

![img](https://image.201068.xyz/assets/clip_image012-16900389774278.jpg)

概述:在前端领域当中拖拽是一个非常常见效果。拖拽三板斧鼠标按下=>鼠标移动=>鼠标抬起。

<script type="text/javascript">

 //移除事情

 var div = document.querySelector('.cur');

 //鼠标按下

 div.onmousedown = function(event){

   //短路语法兼容事件对象

   var e = event||window.event;

   //获取鼠标距离元素左侧顶部数据

   var startX = e.offsetX;

   var startY = e.offsetY;

   //鼠标在整个网页中移动

   document.onmousemove = function(event1){

​     //短路语法兼容事件对象

​     var e1 = event1||window.event;

​     //元素进行拖拽

​     div.style.left = e1.clientX - startX +"px";

​     div.style.top = e1.clientY - startY +"px";

   }

 }

 //鼠标抬起事情----将鼠标移动事件移除

 document.onmouseup =function(){

​    document.onmousemove = null;

 }

</script>

l 可以将元素事件移除：就是给这个元素绑定多次事件。让后者覆盖前者。

## 1.3淘宝放大镜

<script type="text/javascript">

  //获取节点

  var slider = document.querySelector('.slider');

  var small = document.querySelector('.small');

  //鼠标按下

  slider.onmousedown = function(event){

​    //短路语法进行兼容

​    var e = event||window.event;

​    var startX = e.offsetX;

​    var startY = e.offsetY;

​    //鼠标移动

​    document.onmousemove = function(event){

​      var e1 = event||window.event;

​      //计算出元素left数值

​      var l = e1.clientX - startX ;

​      var t = e1.clientY - startY;

​      //因为滑块只能在父盒子中进行移动----进行条件约束

​      if(l <= 0) l = 0;

​      if(l >=300) l = 300;

​      if(t <=0) t = 0;

​      if(t >=200) t = 200;

​      slider.style.left = l +"px";

​      slider.style.top = t +'px';

​      //修改小图背景图定位

​      small.style.backgroundPosition="-" + l +"px -" + t +"px";

​    }

  }

  //鼠标抬起

  document.onmouseup = function(){

​      //将鼠标移动的事件移除

​      document.onmousemove = null;

  }

</script>

# 二、BOM

问题:JavaScript这门脚本语言是由几部分组成的呀？

l ECMAScript【简称ES】：它是欧洲计算机协会，大概每年6月中旬定制语法规范。

l DOM【document object model】：文档对象模型。相当于是整个节点树的‘根节点’。

l BOM【browser object model】：浏览器对象模型。每一个浏览器厂商给程序员提供一个内置对象，可以获取浏览器一些信息。

## 2.1初次认知BOM

概述:BOM【browser object model】浏览器对象模型，每一个浏览器厂商都有属于自己特定BOM对象，

给我们提供一些获取浏览器信息的属性、方法。其实BOM即为每一个浏览器内置window对象。

<script type="text/javascript">

  //BOM对象：即为内置window对象

  console.log(window);

  console.log(typeof window);

  //获取地址栏信息

  console.log(window.location.href);

  //获取电脑屏幕一些信息

  console.log(window.screen.width);

  console.log(window.screen.height);

  //获取浏览器信息（用的是哪个浏览器、版本号多少）

  console.log(window.navigator.userAgent)

</script>

l BOM即为浏览器内置window对象

l BOM对象：获取地址栏信息、屏幕信息、浏览器内核信息等等

l 作为BOM对象属性、方法可以省略window

l BOM对象是引用类型数据

## 2.2定时器

概述：BOM对象给我们提供很多属性与方法，其中最为重要的一个方法即为定时器。定时器你可以理解为

每隔一段时间执行一次回调函数。

语法格式：

setInterval(callBack,time);

l 定时器是BOM对象方法，因此可以省略window

l 第一个参数【回调函数：当一个函数执行的时候，传递实参是另外一个函数声明部分】必有的。

l 第二个参数【时间：毫秒】 1S = 1000ms

<script type="text/javascript">

 //定时器是BOM对象一个方法：因此可以省略window

 setInterval(function(){

​    //书写任意代码

​    console.log('我是定时器么么哒');

 },1000);

</script>

### 2.2.1异步语句

概述:在JS这门语言当中，如果某一个语句很耗时间【称之为异步语句】。

异步语句有一个很大特征：先执行异步语句后面代码，回首在执行异步语句。

<script type="text/javascript">

 //定时器是BOM对象一个方法：因此可以省略window

 //开启定时器

 var timer = setInterval(function(){

​    //书写任意代码

​    console.log('我是定时器么么哒');

 },1000);

 //定时器语句后面代码

 console.log('我是定时器后面代码呀');

 //清除定时器方法

 clearInterval(timer);

</script>

l 定时器是异步语句：先执行异步语句后面代码，回首在执行异步。

l clearInterval也是BOM对象提供一个方法：清除定时器。

### 2.2.2运动套路

概述：在前端领域中经常会出现元素运动效果。实现原理无非：定时器 + 改变定位元素left、top套路。

<script type="text/javascript">

   //获取节点

   var div = document.querySelector('div');

   //信号量

   var l = 0;

   var t = 0;

   //开启定时器

   setInterval(function(){

​     l+=10;

​     t+=5;

​     if(l >=300) l = 300;

​     //修改节点left、top

​     div.style.left = l+"px";

​     div.style.top = t +"px";

   },100);

</script>

l 前端当中运动套路：定时器+定位元素修改left、top即可。

### 2.2.3浩克游戏

游戏素材网站：http://www.aigei.com/

<script type="text/javascript">

  //获取节点

  var div = document.querySelector('div');

  //信号量

  var step = 0;

  var l = 0;

  //控制小人是否行走

  var isMove = false;

  //开启定时器

  setInterval(function(){

​      if(isMove) return;

​     step++;

​     l+=10;

​     if(step > 3) step = 0;

​     //改变背景图定位

​     div.style.backgroundPosition = - step * 32 +"px -96px";

​     //修改left

​     div.style.left = l +"px";

  },100);

  //绑定单机事件

  div.onclick = function(){

​     //将右侧数值赋值给左侧变量【置反思想】

​     isMove = !isMove;

  }

</script>

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 
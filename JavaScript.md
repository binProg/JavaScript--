

# JavaScript

## 1. 概述

1. JS是运行在客户端浏览器里的脚本语言
2. JS 是弱类型；Java是强类型。
   - 弱类型，变量类型可变。强类型变量类型不可变

## 2. JS与HTML的混合使用

- 第一种：将JS代码写入html的<head></head>标签中。

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
      <script type="text/javascript">
          //alert 是javaScript语言提供的一个警告框函数
          //它可以接收任意类型的参数，这个参数就是警告框的提示信息
          alert("hello javaScript!")
      </script>
  </head>
  <body>
  
  </body>
  </html>
  ```

- 第二种：使用script标签单独引入js代码。

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
      <!--
          现在使用script标签引入外部的js 文件来执行
              src属性专门用来引入js文件路径（可以是相对路径，也可以是绝对路径
          script标签可以用来定义js代码，也可以用来引入js文件
          但是
          ——只能两个功能二选一使用，不能同时使用两个功能。
       -->
      <script type="text/javascript" src="1.js"></script>
  </head>
  <body>
  </body>
  </html>
  ```

## 3. 变量

> 变量：可以存放某些值的内存的命名。

  3.1.  **JS的变量类型**

  - 数值类型：number 
  - 字符串类型：string
  - 对象类型：object
  - 布尔类型：boolean
  - 函数类型：function

 3.2.  **JS里特殊的值**：

 - underfined：  未定义，所有js变量未赋予初始值的时候，默认值都是undefined
- null：        空值
- NAN ：      全程Not a number。非数字、非数值。

*示例*：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script type="text/javascript">
        var i;
        alert(i)//undefined
        i=12;
        alert(i)//12

        var a=12;
        var b="abc"
        alert(a*b)//NAN
    </script>
</head>
<body>

</body>
</html>
```



3.3. **JS中的定义变量格式**：

```javascript
var 变量名；
var 变量名=值；
```



## 4. 关系（比较）运算：

​	等于：			== (等于是简单的做*字面值*的比较)

​	全等于：		===(除了字面值的比较，还要比较两个变量的数值类型)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script type="text/javascript">
        var a="12";
        var b=12;
        alert(a==b);//true
        alert(a===b);//false
    </script>
</head>
<body>

</body>
</html>
```

## 5. 逻辑运算：

​	在JS 语言中，所有的变量都可以作为一个boolean类型的变量去使用。

​       ==0、null、undefined、""（空串）都认为是false==

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script type="text/javascript">
        /*在JS 语言中，所有的变量都可以作为一个boolean类型的变量去使用。

       0、null、undefined、""（空串）都认为是false
*/
        var a=0;
        if(a){
            alert("0为真");
        }else{
            alert("0为假");//this
        }

        a=null;
        if(a){
            alert("null为真");
        }else{
            alert("null为假");//this
        }

        a=undefined;
        if(a){
            alert("undefined为真");
        }else{
            alert("undefined为假");//this
        }

        a=""
        if(a){
            alert("空串为真");
        }else{
            alert("空串为假");//this
        }
    </script>
</head>
<body>
</body>
</html>
```



> 1. && 且运算。
>
>    有两种情况：
>
>    （1）当表达式为全真的时候。返回最后一个表达式的值。
>
>    （2）当表示式中，有一个为假的时候。返回第一个为假的表达式的值。
>
> 2. || 或运算。
>
>    （1）当表达式全为假时，返回最后一个表达式的值。
>
>    （2）只要有一个表达式为真，就返回第一个为真的表示式的值。

​	==并且 **&& 与运算** 和 **|| 或运算** 有短路。短路就是说，当这个&&或||运算		有了结果之后，后面的表达式**不再执行**。==

```javascript
        /* &&:
        （1）当表达式全真，last ture。
        （2）当有一个表达式为假，first false。
         */
        var a="abc";
        var b=true;
        var c=false;
        var d=null;

        alert(a&&b);//true
        alert(b&&a);//abc
        alert(a&&c);//false
        alert(c&&a);//false
        alert(c&&d);//false
        alert(a&&d&&c);//null
```



## 6.数组 ==重点！！！==

 - 数组定义方式：

   ​		格式：

   ​			```var 数组名 =[]；//空数组```

   ​			```var 数组名=[1,'abc',true];//定义数组同时赋值元素```

   ==JavaScript语言中，只要通过数组下标进行赋值，那么最大的下标就会自动对数组进行扩容操作。==

   ```javascript
           var arr=[];//定义一个空数组
           alert(arr.length);//0
   
           arr[0]=12;
           alert(arr[0]);//12
           alert(arr.length);//1
   
           arr[2]=9;
           alert(arr[2]);//9
           alert(arr.length);//3
   
           alert(arr[1]);//undefined
   
           //数组的遍历
           for (var i=0;i<arr.length;i++){
               alert(arr[i]);
           }
   ```

## 7.函数：

​	函数的第一种定义方式：

​		```function 函数名(){函数体}```

```javascript
//定义一个无参函数
function f1() {
    alert("无参函数f1被调用了");
}
//调用函数
f1();

//定义一个有参函数
function f2(a,b){
    alert("有参函数f2被调用了，a=>"+a+", b=>"+b);
}

f2(12,"hello");

//定义一个有返回值的函数
function f3(num1,num2){
    var result = num1 + num2;
    return result;
}

alert(f3(100,9));
```

​	函数的第二种定义方式：

​		```var 函数名= function(形参列表){函数体}```

```javascript
var f1=function(){
            alert("No arguments function");
        }

        f1()

        var f2=function (a,b) {
            alert("function with arguments, a="+a+", b="+b);
        }

        f2(2,6);

        var f3=function (num1,num2) {
            var result=num1+num2;
            return result;
        }

        alert(f3(100,99));
```

==JS函数中不允许**重载**==

```javascript
function f(){
    alert("无参函数");
}

function f(a,b){
    alert("有参函数");
}

f();//有参函数
```

```javascript
function f(a,b) {
    alert("有参函数");
}

function f() {
    alert("无参函数");
}

f(2,6);//无参函数
```

	> 函数的arguments 隐形参数（只在function函数内）：
	>
	> 就是在function函数中不需要定义，但却可以直接用来获取所有参数的变量，我们管它叫**隐形参数**。
	>
	> 隐形参数和 Java中的可变长参数一样。
	>
	> public void fun(Object ..args);
	>
	> 可变长参数其实是一个数组。
	>
	> 那么，JS中的隐形参数也可跟 Java的可变长参数一样。操作类似数组。

```javascript
//需求: 要求编写一个函数，用于计算所有参数相加的和并返回。
function sum(num1,num2){
    var result=0;
    for(var i=0;i<arguments.length;i++){
        result+=arguments[i];
    }
    return result
}

alert("所有参数相加的和为： "+sum(1,2,3,4,5,6,7,8,9));//45
alert("所有参数相加的和为：（含非数值型参数）"+sum(1,2,3,4,"abc",5,6,7,8));//10abc56789
```

## 8.JS 中自定义对象

1. **Object形式**的自定义对象

   对象的定义：

   ​	```var 变量名 = new object();  //对象实例（空对象```

   ​	```变量名.属性名 = 值;   //定义一个属性```

   ​	```变量名.函数名 = function(){}   //定义一个函数```

   对象的访问：

   ​	```变量名.属性名 / 函数名(); ```

   ```javascript
    var obj = new Object();
           obj.name = "IU";
           obj.age = 23;
           obj.fun = function () {
               alert("姓名："+obj.name+", age:"+obj.age);
           }
           // 对象的访问：
           //      对象.属性名
           //      对象.函数()
           alert(obj.name);
           alert(obj.age);
           obj.fun();
   ```

2. **{}花括号形式**的自定义对象

   ```
   var 变量名 = {}; // 空对象
   var 变量名 = {
   	属性名:值，
   	属性名:值，
   	函数名:function(){}
   };
   ```

   ```javascript
    var obj={
               name:"刘德华",
               age: 66,
               fun: function () {
                   alert("name: "+this.name+", age: "+this.age);
               }
           };
           alert(obj.name);
           obj.fun();
   ```

## 9. JS中的事件

​	事件：PC输入设备与页面进行交互的响应。

​	9.1. **常用的事件**：

  - onload  加载完成事件；	*页面加载完成后，常用于做页面 js代码初始化操作*
  - onclick 单击事件；         常用于按钮的点击响应操作
  - onblur  失去焦点事件；    常用于输入框失去焦点后验证其输入内容是否合法。
  - onchange  内容发生改变事件；  常用于下拉列表和输入框内容发生改变后操作
  - onsubmit  表单提交事件；  常用于表单提交前，验证所有表单项是否合法。

​       9.2.  **事件的注册又分为：<u>静态注册</u>和<u>动态注册</u>**

​		（1）事件的注册（绑定）？

​	       其实就是告诉了浏览器，当事件响应后要执行哪些操作代码，叫事件注册       或事件绑定。

​		（2）静态注册事件：通过html标签的事件属性直接赋予事件响应后的代码，这种方式叫 静态注册。

​		（3）动态注册事件：是指先通过js代码得到标签的dom对象，然后再通过```dom对象.事件名 = function(){}``` 这种形式赋予事件响应后的代码，叫动态注册。

==动态注册的基本步骤：==

  1. 获取标签对象；
  2. 标点对象.事件名=function(){}

		9.2.1. onload事件**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script type="text/javascript">
        //onload事件方法
        function onloadFun(){
            alert("静态注册onload事件，所有代码");
        }

        //onload事件动态注册，是 固定 写法
        window.onload=function () {
            alert("onload动态注册事件");
        }
    </script>
</head>
<!--静态注册onload事件，
        onload事件是浏览器解析万页面后就会自动触发的事件

<body onload='alert("静态注册onload事件")'>

<body onload="onloadFun();">
-->
<body>
</body>
</html>
```



​	9.2.2. onclick事件**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script type="text/javascript">
        function onclickFun(){
            alert("onclick静态注册事件");
        }

        //动态注册onclick事件
        window.onload=function () {
            /*
            * 动态注册的步骤：
            *   1.获取对象标签
            *   2.标签对象.事件名=function(){}
            * */
            //获取对象标签
            var btnObj = document.getElementById("btn02");
            //通过 标签对象.事件名 = function(){} 进行事件的动态注册
            btnObj.onclick=function () {
                alert("动态注册onclick事件")
            }
        }
    </script>
</head>
<body>
<button onclick="onclickFun()">按钮1</button>
<button id="btn02">按钮2</button>
</body>
</html>
```

​       9.2.3. **onblur事件**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script type="text/javascript">
        //静态注册失去焦点事件
        function onblurFun() {
            //console是控制台对象，是由javaScript语言提供的，专门用来向浏览器控制台打印输出，用于测试使用。
            //log()是打印方法
            console.log("静态注册失去焦点事件");
        }

        //动态注册失去焦点事件
        window.onload=function(){
            //1. 获取标签对象
            var pwd=document.getElementById("pwd");
            //2. 通过 标签对象.事件名=function(){}来注册事件
            pwd.onblur=function () {
                console.log("动态注册失去焦点事件");
            }
        }
    </script>
</head>
<body>
    用户名：<input type="text" onblur="onblurFun();"><br/>
    密码:  <input id="pwd" type="text"><br/>
</body>

</html>
```

​	9.2.4. **onchange事件**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script type="text/javascript">
        //静态注册onchange事件
        function onchangeFun(){
            alert("奶茶味道发生改变");
        }

        //动态注册onchange事件
        window.onload=function () {
            //1. 获取标签对象
            var selObj = document.getElementById("sel01");
            //2. 通过标签对象.事件名=function(){}注册事件
            selObj.onchange=function () {
                alert("喜欢的水果发生改变");
            }
        }
    </script>
</head>
<body>
    <!--静态注册onchange事件-->
    请选择你最喜欢的奶茶味道：
    <select onchange="onchangeFun();">
        <option>--奶茶味道--</option>
        <option>原味</option>
        <option>焦糖味</option>
        <option>芝士味</option>
    </select>

    <br/>
    <!--动态注册内容改变事件-->
    请选择你最喜欢的水果：
    <select id="sel01">
        <option>--水果--</option>
        <option>西瓜</option>
        <option>耙耙柑</option>
        <option>柠檬</option>
    </select>
</body>
</html>
```

​	9.2.5. **onsubmit事件**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script type="text/javascript">
        //静态注册onsubmit事件
        function onsubmitFun() {
            //onsubmib事件要验证所有表单项是否合法，如果发现一个不合法就阻止表单提交
            alert("静态注册表单提交事件---发现不合法");

            return false;
        }

        //动态注册onsubmit事件
        window.onload=function () {
            //1. 获取标签对象
            var formObj = document.getElementById("form01");
            //2. 通过 标签对象.事件名=function(){}
            formObj.onsubmit=function () {
                alert("动态注册表单提交事件---发现不合法");

                return true;
            }
        }

    </script>
</head>
<body>
    <!-- return False; 可以阻止表单提交-->
    <form action="http://localhost:8080" method="get" onsubmit="return onsubmitFun();">
        <input type="submit" value="静态注册"/>
    </form>

    <br/>
    <form action="http://localhost:8080" method="get" id="form01">
        <input type="submit" value="动态注册"/>
    </form>
</body>
</html>
```
## 10. DOM模型

	> DOM全称：Document Object Model 文档对象模型
	>
	> 即，把文档中的标签、属性、文本、转化为对象来管理。

​	10.1. Document 对象（==重点==）

![Document对象](C:\Users\BINJ\Pictures\Document文档树.png "Documment文档树内存结构")

​	10.1.1.  Document 对象的理解：

  - Document 它管理了多有HTML文档内容
  - document 它是一种树结构的文档，有层级关系
  - 它让我们把所有标签都对象化
  - 我们可以通过document访问所有的标签对象

		10.1.2.  对象化：

			举例：有一个人，年龄：18，性别：女，名字：张某某。我们需要将这个人的信息对象化。（Java是面向对象的编程）

```java
class Person{
    private int age;
    private String sex;
    private String name;
}
```

​		那么，标签的对象化：

```html
<body>
	<div id="div01">div01</div>
</body>
```

​		模拟对象化，相当于：

```java
class Dom{
    private String id; //id属性
    private String tagName; //标签名
    private Dom parentNode; //父节点
    private List<Dom> children; //孩子节点
    private String innerHTML; //起始标签和结束标签中间的内容
}
```

10.2 Document对象中的方法介绍（**重点**)

​	```document.getElementById(elementId)```:    通过标签中的id属性查找标签dom对象，elementId是标签的id属性。

​	```document.getElementsByName(elementName)```:    通过标签的name属性查找标签dom对象，elementName是标签的name属性值。

​	```document.getElementsByTagName(tagname)```:    通过标签名查找dom对象，tagname是标签名。

​	```document.createElement(tagName)```:    通过给定的标签名，创建一个标签对象，tagName是要创建的标签名。

​	例子：用DOM对象方法验证 用户名输入是否有效。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script type="text/javascript">
        /*
        * 需求：当用户点击了 校验 按钮，要获取输入框中的内容，并查看是否合法。
        * 验证的规则是：必须由字母、数字、下划线组成，长度为5-12位。
        * */
        function onclickFun(){
            //1. 当我们要操作一个标签时，一定要首先获得这个标签对象
            var unameObj = document.getElementById("username");
            //2. 获取输入框中的文本内容
            var unameText = unameObj.value;//value是可变的
            //alert(unameText);
            //3. 对获取的文本内容进行校验
            pattern = /^\w{5,12}$/;
            /*
            * test()方法用于测试某个字符串，是否匹配规则
            * 匹配，返回true；否则，返回false.
            * */
            if(pattern.test(unameText)){
                alert("用户名合法！")
            }else{
                alert("用户名非法！")
            }
        }
    </script>
</head>
<body>
    用户名： <input type="text" id="username" value="hello"/>
    <button onclick="onclickFun();">校验</button>
</body>
</html>
```

**注**：

​	优先使用顺序：id$\gt$name$\gt$tagName 。

## 11. 节点的常用属性和方法

	> 节点就是 标签对象

​	*方法*:

  - getElementsByTagName()方法
  - appendChild(oChildNod)方法，可以添加一个子节点，oChildNode是要添加的孩子节点。

​        属性：

      - childNodes属性：获取当前节点的所有子节点
      - firstChild属性：获取当前节点的第一个子节点
      - lastChild属性：获取当前节点的最后一个子节点
      - parentNode属性：获取当前节点的父节点
      - nextSibling属性：获取当前节点的下一个节点
      - previousSibling属性：获取当前节点的上一个节点
      - className属性：用于获取或设置标签的class属性值
              - innerHTML属性：表示获取/设置起始标签和结束标签之间的内容
      - innerText属性：表示获取/设置起始标签和结束标签之间的文本


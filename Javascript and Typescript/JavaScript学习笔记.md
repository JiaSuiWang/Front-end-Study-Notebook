

## JavaScript Can Change HTML Styles (CSS)

Scripts can be placed in the `<body>`, or in the `<head>` section of an HTML page, or in both.

```javascript
<p id="demo">JavaScript can change HTML content.</p>

<button type="button" onclick="document.getElementById('demo').innerHTML = 'Hello JavaScript!'">Click Me!</button>
```



```javascript
<script>
function myFunction() {
  document.getElementById("demo").innerHTML = "Paragraph changed.";
}
</script>

<body>
    <p id="demo">A Paragraph</p>
	<button type="button" onclick="myFunction()">Try it</button>
</body>
```

myFunction()这里有括号，意味着这里调用了函数！为什么赋值给了onclick呢



## javascript最常见的打印方式是改变HTML元素的innerHTML 属性

**Changing the innerHTML property of an HTML element** is a common way to display data in HTML.

```javascript
<body>

<h1>My First Web Page</h1>
<p>My First Paragraph</p>

<p id="demo"></p>

<script>
document.getElementById("demo").innerHTML = 5 + 6;
</script>

</body>
```



# Javascript语法要注意的点

#### 0.Javascript在创建对象，类，变量，函数的时候，都需要有关键字进行声明！！！

​	处于python和java之间：跟python一样都是动态语言，但是需要关键字声明；java需要指定变量类型，但是需要有关键字声明

#### 1.Javascript每个语句结束都需要写分号！

```javascript
var person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"}; 
```

​	**分号不是必须的，但是非常推荐**

​		Ending statements with semicolon is **not required**, **but highly recommended.**

​	**如果代码太长要分行的话**在一个operate后面分比较好：

​		If a JavaScript statement does not fit on one line, the best place to break it is after an operator:

#### 2.Javascript的函数，需要有关键字function，需要有大括号

```javascript
function name(parameter1, parameter2, parameter3) {
  // code to be executed
}
```

#### 3.Javascript用//和/* content */来注释, html用<!-- content -->来注释

#### 4.Javascript大小写敏感，申明变量只能是var，不能是Var

#### 5.变量名用Lower Camel Case规则** 驼峰式，比如lastName

#### 6.可以在一行声明多个变量，用逗号隔开

7.JavaScript Types are **Dynamic**(跟python一样是动态语言，destroy and allocate)



## Javascript变量类型

| **number**    | 包括整数和浮点数                                             |
| ------------- | ------------------------------------------------------------ |
| **string**    | The `length` property returns the length of a string         |
| **object**    | objects are written with curly braces `{}`, Object properties are written as name:value pairs, separated by commas. 例如var person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"}; 注意虽然都用大括号，但是它跟函数不一样，函数最后不需要分号，但是object的定义需要分号。 The `typeof` operator returns "object" for **objects, arrays, and null**. |
| **undefined** | var car;  // Value is undefined, type is undefined                                                                             car = undefined;  // Value is undefined, type is undefined |
| **null**      | typeof null        // object                   You can consider it a bug in JavaScript that `typeof null` is an object. It should be `null`. |
| **boolean**   |                                                              |

1.将number类型和string类型相加的时候，JavaScript会将number视为string

2.用typeof函数来查看数据类型，例如typeof(true)

3.The `typeof` operator returns "object" for objects, **arrays**, and **null**.

对于array和null,typeof都返回object, Arrays are a special type of objects.

```javascript
typeof {name:'John', age:34} // Returns "object"
typeof [1,2,3,4]             // Returns "object" (not "array", see note below)
typeof null                  // Returns "object"
```





 

## **Javascript关键字**

| **var**   | **JavaScript uses the `var` keyword to declare variables. keywords are used to identify actions to be performed. The `var` keyword tells the browser to create variables:** |
| --------- | :----------------------------------------------------------- |
| **const** | **(2015 ES6) `const` keyword to define a variable that cannot be reassigned                                注意1.在声明的时候必须赋值 2.在block scope内定义，与let性质一样 3.不能接受redeclare 4.cannot change constant primitive values, but we can change the properties of constant objects.** |
| **let**   | **(2015 ES6) `let` keyword to define a variable with restricted scope，called Block Scope variable** |
|           |                                                              |



## **let 关键字来定义变量**

**1.对于已经存在的变量再次声明（redeclare）是可以的**

```javascript
var lastName = "Harry";
var lastName; //这里lastName还是依然是Harry

var lastName = "Harry";
var lastName = "Potter"; //这里lastName变为Potter
```

**2.带来的问题：在区块范围内重新声明变量会改变区块外的值:**

```javascript
var x = 10;
//here x = 10
{
var x = 2;
//here x = 2 
}
//here x = 2
```

**3.用let定义变量的好处是：在区块范围内重新声明的变量，不会影响到区块范围外面的变量**

**意义：避免使用全局变量，每次在块里面都用let声明，万无一失**

**Redeclaring a variable inside a block will not redeclare the variable outside the block**

```javascript
var x = 10;
//here x = 10
{
let x = 2;
//here x = 2
}
//here x = 10
```

**4.用var和let声明的全局变量有何区别**

**In HTML, the global scope is the window object.**

**Global variables defined with the `var` keyword belong to the window object**

**Global variables defined with the `let` keyword do not belong to the window object**

```javascript
var carName = "Volvo";
// code here can use window.carName
```

**5.用let来declare变量在大多数情况下是非法的 https://www.w3schools.com/js/js_let.asp**

**Redeclaring a `var` variable with `let`, in the same scope, or in the same block, is not allowed:**

**Redeclaring a `let` variable with `var`, in the same scope, or in the same block, is not allowed:**

**Redeclaring a `let` variable with `let`, in the same scope, or in the same block, is not allowed:**

**Redeclaring a variable with `let`, in another scope, or in another block, is allowed:**



## 避免使用全局变量

Do NOT create global variables unless you intend to.

Your global variables (or functions) can overwrite window variables (or functions).
Any function, including the window object, can overwrite your global variables and functions.

所有的函数都能重写全局变量和函数





## Event

HTML allows **event handler attributes**, with JavaScript code, to be added to HTML elements.同时对event进行检测和响应

```javascript
<element event="some JavaScript">
```

1.How to **detect** the event

2.How to **react** the event

​	JavaScript can **"react"** on these events.



## 常见的event

| Event attribute | Description                      |
| :-------------- | :------------------------------- |
| onclick         | The user clicks an HTML element  |
| onchange        | An HTML element has been changed |

```javascript
<!DOCTYPE html>
<html>
<body>

<p id="demo" onclick="displayDate()">this is a paragraph</p>

<script>
function displayDate(){
	document.getElementById("demo").innerHTML = Date();
}
</script>

</body>
</html>
```



## 条件语句

```javascript
if (condition1) {
    statement1;
} else if (condition2) {
    statement2;
} else {
    statement3;
}
```



## switch语句

```javascript
switch(expression) {
  case x:
    // code block
    break;
  case y:
    // code block
    break;
  default:
    // code block
}
```



## try and catch, throw

The `try` statement lets you test a block of code for errors.

The `catch` statement lets you handle the error.

The `throw` statement lets you create custom errors.

The `finally` statement lets you execute code, after try and catch, regardless of the result.

```javascript
try {
  Block of code to try  //这里放想要测试的代码
}
catch(err) {
  Block of code to handle errors  //这里放捕获异常之后想要处理的代码
}
```

如果try里面的代码块执行异常，JavaScript会产生一个**Error Object**, 包括**name** and **message**两个属性。

（throw an exception = throw an error）

6种error name

| Error Name     | Description                                  |
| :------------- | :------------------------------------------- |
| EvalError      | An error has occurred in the eval() function |
| RangeError     | A number "out of range" has occurred         |
| ReferenceError | An illegal reference has occurred            |
| SyntaxError    | A syntax error has occurred                  |
| TypeError      | A type error has occurred                    |
| URIError       | An error in encodeURI() has occurred         |

```javascript
<script>
try {
  adddlert("Welcome guest!");
}
catch(err) {
  document.getElementById("demo").innerHTML = err.message;
}
</script>
```



但是exception也可以自己定义，exception 可以是 `String`, a `Number`, a `Boolean` or an `Obje`

定义的方式就是用throw关键字， throw是跟try和catch一起搭配使用的，用来产生一个定制的错误的messages

```javascript
<script>
function myFunction() {
  var message, x;
  message = document.getElementById("p01");
  message.innerHTML = "";
  x = document.getElementById("demo").value;
  try {
    if(x == "") throw "empty";
    if(isNaN(x)) throw "not a number";
    x = Number(x);
    if(x < 5) throw "too low";
    if(x > 10) throw "too high";
  }
  catch(err) {
    message.innerHTML = "Input is " + err;
  }
  finally {
    document.getElementById("demo").value = "";
  }
}
</script>
```



The `finally` statement lets you execute code, after try and catch, regardless of the result:



## Hoist 

区分点1 Declarations 和Initializations 

区分点2 var声明变量和let，const声明变量

1.Hoisting 是JavaScript的特性，将参数的Declarations自动的提到函数块的最前面

​	但是这种声明只针对由var声明的变量，不针对由var和const声明的变量

2.只将Declarations 提前，不会将Initializations 提前









## Strict Model

1.它是一种声明，写法是一行语句,作用是阻止你使用undeclared variables.

```javascript
"use strict";
```

2.一定要在script or a function的开头声明！！！

3.作用域是函数块，如果再函数外面声明，作用域就是全局

4.为什么这个很重要：因为Javascript会自动创建全局变量，万一是因为不小心打错了变量名，在strict model的保护下，他会抛出一个异常，而不是说自动声明一个全局变量！！！

#### 	Automatically Global https://www.w3schools.com/js/js_scope.asp

​	如果你给一个没有被声明(declare)的变量赋值，那么他就会自动的成为一个全局变量(即使这个赋值过程发生在函数里面，也会自动成为一个全局变量)！！

5.除了防止使用未声明的变量以外，还有一些作用是：不允许delete参数，函数之类的 https://www.w3schools.com/js/js_strict.asp





# this

**1.对于函数而言**	

​	对于定义在对象里的method，this指的是**拥有这个method的对象**

```javascript
<script>
var person = {
  firstName: "John",
  lastName : "Doe",
  id     : 5566,
  fullName : function() {
    return this.firstName + " " + this.lastName;//this 指的是拥有这个function的对象，也就是person
  }
};
</script>
```

​	对于普通的函数

​		**如果没有在strict model下，this指的是整个的global object，也就是object Window**

​		如果在strict model下，this指的是undefined

2.对于单独的this而言，指的就是整个的global object，也就是object Window

3.对于event而言，this指的是接收这个事件的对象

```javascript
<button onclick="this.style.display='none'">Click to Remove Me!</button>
```

4.如果有了call和apply函数就另当别论了



# Arrow Function

先导课：**函数的定义与赋值**

```javascript
<script>
function hello(){
    return "hello world！"
}
var test = hello
document.getElementById("demo").innerHTML = typeof(test)  //此处会打印function
</script>
```

写法二:**函数定义的另一种写法**

```javascript
<script>
//这里如果不写var关键字的话，就会自动将test变为一个全局的变量，这个变量是function类型
var test = function(){  
    return "hello world!"
}
document.getElementById("demo").innerHTML = typeof(test)  //此处会打印function
</script>
```

写法三：**箭头函数**

```javascript
<script>
test = () =>{
    return "hello world!"
}
//如果只有一句statement，还能写成
test = () => "Hello world"
document.getElementById("demo").innerHTML = typeof(test)  //此处会打印function
</script>
```

1. 写法

   function_name = () 代表着这是一个函数，取代了function关键字

   =>后面写的是函数的具体内容

2. 如果由传入参数的话，写入在括号里面就可以

   如果传入参数只有一个的话，可以省略小括号

   ```javascript
   hello = val => "Hello " + val;
   ```

   如果函数的内容只有一个statement的话，可以省略大括号和return

   ```javascript
   hello = () => "Hello World!";
   ```

3.箭头函数与普通函数不仅仅是语法上面的不同，还有this也不一样

With a regular function `this` represents the object that *calls* the function:

如果一个函数是一个普通定义的函数，那么在该函数里面，this代表着调用这个函数的对象

th an arrow function `this` represents the *owner* of the function:

如果一个函数是一个箭头函数，那么在这个函数里面，不管谁调用的它，this都代表着这个类的对象





# class

1.class的语法：

​	用关键字class进行声明，

​	后面接类名和大括号，

​	一定要有constructor()函数->对应python的`__init__` 函数，但是不需要加self，当创建对象的时候会被自动调用！！！

```javascript
class ClassName{
    constructor(a, b){
        this.a = a
        this.b = b
    }
    method1(){
        
    }
    method2(){
        
    }
}

var className = new ClassName(a,b) //一定要有var声明关键字
```

2.class与object的不同

```javascript
var person = {
  firstName: "John",
  lastName : "Doe",
  id       : 5566,
  fullName : function() {
    return this.firstName + " " + this.lastName;
  }
};
```

1.object这样写，关键字用var声明而不是class

2.如果要访问object的参数，不需要实例化，直接用object_name.object_property

3.class需要实例化

相同点：都有this这个用法



# JSON

一个JSON例子：

```javascript
{"employees":[
  { "firstName":"John", "lastName":"Doe" },
  { "firstName":"Anna", "lastName":"Smith" },
  { "firstName":"Peter", "lastName":"Jones" }
]}
```

- Data is in name/value pairs 

- Data is separated by commas

- Curly braces hold objects

- Square brackets hold arrays

  

一个object例子：

```javascript
var person = { name: "John", age: 31, city: "New York" };
```
















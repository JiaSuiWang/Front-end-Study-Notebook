# Javascript相关知识实时渲染！！！

1. **HTML** to define the **content**， **structure**, of web pages

2. **CSS** to specify the **layout** of web pages

3. **JavaScript** to program the **behavior** of web pages




<style>
https://www.cnblogs.com/dreamingbaobei/p/5062901.html

### html + css + javascript的关系

- HTML（超文本标记语言 **H**yper **T**ext **M**arkup **L**anguage），HTML 是用来描述网页的一种语言 
  - **H**yper **T**ext 超文本：指“含有指向其他资源链接”内容的文本，超文本中有很多HyperLink（超链接）可以连接到其他资源
- CSS(层叠样式表 *C*ascading *S*tyle *S*heets),样式定义如何显示 HTML 元素，语法为：selector {property：value} (选择符 {属性：值})
- JavaScript是一种脚本语言，其源代码在发往客户端运行之前不需经过编译，而是将文本格式的字符代码发送给**浏览器**由浏览器解释运行
  - 什么是脚本（script）：脚本就是**一系列指令**，演员看了指令就知道自己该表演什么，说什么台词；计算机看了指令就知道自己该做什么事情。所以 script 其实就是短小的、用来**让计算机自动化完成一系列工作的程序**。通常是**解释运行**的——也就是说，计算机里有一个程序能一句一句地把脚本里的内容转换成CPU能理解的指令，而且它每次只解释一句，CPU跑完了才解释下一句。

```javascript
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Title</title>
  <style> 
    h1 {
      text-align: center;
    }
  </style>
</head>
<body>

<h1>Hello </h1>
<script>  #这里是JavaScript
  console.debug('Hello World');
</script>
</body>
</html>
```

html里面可以写入css和js

html：静态网页

JavaScript：动态网页（动画+数据请求）

CSS



### Javascript 是动态类型语言

**为什么python慢**：https://www.jiqizhixin.com/articles/2018-08-14-11

动态类型语言是指在运行期间才去做数据类型检查的语言。 在用动态语言编程时，不用给变量指定数据类型，第一次赋值给变量时，在内部将数据类型记录下来。 JavaScript、Ruby、Python是典型的动态类型语言



在**静态类型语言**中，定义变量时必须声明类型。C, C++, Java, C#, Go都是这种语言。

在**动态类型语言**中，类型的概念依旧存在，但是这个变量的类型是动态变化的。

```
a = 1

a = "foo"
```

在上面这个例子中，Python创建第二个变量的时候用了同样的名字，但是变量类型是str（字符型），这样就**对先前在内存中给a分配的空间进行了释放和再分配。**

静态类型语言的这种设计并不是为了麻烦大家——它们是按照CPU的运行方式设计的。如果**最终需要将所有内容都转化为简单的二进制操作，那就必须将对象和类型转换为低级数据结构**。

Python自动完成了这个过程，我们看不见，也没必要看见。

不必声明类型不是使Python变慢的原因。Python语言的设计使我们几乎可以创建任何动态变量。我们可以在运行时替换对象中的方法，也可以胡乱地把低级系统调用赋给一个值。几乎怎么修改都可以。





## What is HTML?

- HTML stands for Hyper Text Markup Language
- HTML is the standard markup language for creating Web pages
- HTML describes the **structure** of a Web page
- HTML consists of a series of elements
- HTML elements tell the browser how to display the content
- HTML elements label pieces of content such as "this is a heading", "this is a paragraph", "this is a link", etc.

## What is an HTML Element?

An HTML element is defined by a start tag, some content, and an end tag

**Note:** Some HTML elements have no content (like the <br> element). These elements are called empty elements. Empty elements do not have an end tag!

## The <!DOCTYPE> Declaration

The `<!DOCTYPE>` declaration for HTML5 is:<!DOCTYPE html>

作用：**help browsers to display web pages correctly.**

只能出现一次（但是不声明好像也没有什么问题）



# 常见的HTML元素

**Note:** The content inside the <body> section (the white area above) will be displayed in a browser. The content inside the <title> element will be shown in the browser's title bar or in the page's tab.



## Empty HTML Elements

HTML elements with no content are called empty elements.

The `<br>` tag defines a line break, and is an empty element without a closing tag:

- **The `<html>` element is the root element of an HTML page**



## HTML的结构

## HEAD

- The `<head>` element contains **meta information about the HTML page**

  - The HTML `<head>` element is a container for the following elements: `<title>`, `<style>`, `<meta>`, `<link>`, `<script>`, and `<base>`.

    - **Meta Information**  源信息的作用：are used by **browsers** (how to display content or reload page), by **search engines** (keywords), and **other web services**.

    - ### **meta信息和style定义的区别**

      - style里面的properties和values都是css里里面规定好的元素
      - meta的name是定义好的，它的值包括application-name，author，description，generator， keywords，viewport，但是对应的content都是自己写的
      - ![image-20210408214954241](C:\Users\Jiasui Wang\AppData\Roaming\Typora\typora-user-images\image-20210408214954241.png)

    - **Define the character set used:**

      <meta charset="UTF-8">

      **Define keywords for search engines:** ！！！title和keywords都是为了让搜索引擎更好的对,页面排序！！！

      <meta name="keywords" content="HTML, CSS, JavaScript">

      **Define a description of your web page:**

      <meta name="description" content="Free Web tutorials">

      **Define the author of a page:**

      <meta name="author" content="John Doe">

      **Refresh document every 30 seconds:**

      <meta http-equiv="refresh" content="30">

      **Setting the viewport to make your website look good on all devices:**

      <meta name="viewport" content="width=device-width, initial-scale=1.0">

- The `<title>` element specifies a title for the HTML page (which is shown in the browser's title bar or in the page's tab)

  ## BODY

- The `<body>` element defines the document's body, and is **a container for all the visible contents, such as headings, paragraphs, images, hyperlinks, tables, lists, etc.**

  - headings：HTML headings are defined with the `<h1>` to `<h6>` tags.
  - paragraphs：The `<p>` element defines a paragraph
  - images： HTML images are defined with the `<img>` tag.
  - hyperlinks：HTML links are defined with the `<a>` tag:
    - The link's destination is specified in the `href` attribute. Attributes are used to provide additional information about HTML elements.
  - tables
  - lists



## The HTML Style Attribute

#### Attribute写法一律用**name="value"**，用双引号把value括起来，多个attribute放在一起用空格分开



## Style

**本质上是一个CSS定义的一种方式**

Setting the style of an HTML element, can be done with the `style` attribute.

The HTML `style` attribute has the following syntax:

**<*tagname* style="*property*:*value;*">**

三点需要注意：

1.形式上面用的tag是style <style>

2.还是需要大括号的

3.里面的元素写法是property:value， property是css里面的

4.注意句尾的分号！！！





常见的element以及他包含的attributes:

| html         | <html **lang** = 'en-US'> to declare the language and country of the Web page. This is meant to assist search engines and browsers. |
| ------------ | ------------------------------------------------------------ |
| **a**        | **The `<a>` tag defines a hyperlink**    <a **href** = 'www.aaa.com'>  href 代表hypertext reference |
| **image**    | <image src = '/image/aaa.jpg' width = '500' height = '600' alt = 'this is a gril standing under the tree'> The required `alt` attribute for the `<img>` tag specifies an alternate text for an image |
| **style**    | background-color定义背景的颜色， color定义字体的颜色，font-family定义字体，font-size定义字体大小，text-align定义对齐方式 设置color的三种方式：1.rgb(255, 99, 71) 2.#ff6347 3.hsl(9, 100%, 64%) |
| **link**     | The `<link>` tag is most often used to link to external style sheets， 用于声明该文档与外部资源的关系                                                                                                                                             <link rel="stylesheet" href="mystyle.css">                                                                          rel代表relationship，值=stylesheet代表外部资源是一个css文件，href代表hyper reference |
| **base**     | 用于声明初始的url的位置，在相对路径中只需要写相对路径即可，有两个参数1.href 写路径 2.target写显示路径的方式 |
| **title**    | 1.title tag，放在head里面，用于定义页面的title，对搜索引擎有用 |
|              | 2.title attribute,是一个全局的attribute，在任何标签下都能用，用于提示文字 |
| **ul 与 li** | 创建一个无序的list                                           |
| **ol 与 li** | 创建一个有序的list                                           |
| **br**       | 分段                                                         |
| type         | 如果是放在button的tag里面，用于声明按钮的类型，它的值有三种：button（普通的用于点击的按钮），submmit（提交数据的按钮）和reset（重置按钮） |
|              |                                                              |



# Using CSS

Cascading Style Sheets (CSS) is used to format the **layout** of a webpage.

With CSS, you can control the **color, font, the size of text, the spacing between elements**, **how elements are positioned and laid out, what background images or background colors are to be used, different displays for different devices and screen sizes, and much more!**



CSS can be added to HTML documents in 3 ways:

- **Inline** - by using the `style` **attribute** inside HTML elements

  ```javascript
  <h1 style="color:blue;">A Blue Heading</h1>
  ```

- **Internal** - by using a `<style>` **element** in the `<head>` section

  ```javascript
  <style>
  body {background-color: powderblue;}
  h1   {color: blue;}
  p    {color: red;}
  </style>
  ```

- **External** - by using a `<link>` **element** to link to an **external** CSS file

  ```javascript
  <head>
    <link rel="stylesheet" href="styles.css">
  </head>
  ```

  



# div element

#### div element is a block-level element

​	A block-level element always starts on a new line.

​	A block-level element always takes up the full width available (stretches out to the left and right as far as it can).

​	A block level element has a top and a bottom margin, whereas an inline element does not.



#### The `<div>` element has no required attributes, but `style`, `class` and `id` are common.

class：class和组件的关系是多对多的关系

##### The Syntax For Class

To create a class： write a period (.) character, followed by a class name. Then, define the CSS properties within curly braces {}:

一个class设计出来可以被多个组件使用

一个组件可以用多个class



如果多个class存在冲突：在**<style>中后声明的样式**是最终效果，而与 class="" 中式样的顺序无关



id：id和组件的关系是一对一的关系

The syntax for id is: write a hash character (#), followed by an id name. Then, define the CSS properties within curly braces {}.

一个id设计出来只能被一个组件使用

一个组件只能使用一个id







# 写法总结

### style inline

**<*tagname* style="*property*:*value;*">** **如果有多个，直接在style里面加**

三点需要注意：

1.形式上面用的tag是style <style>

2.还是需要大括号的

3.里面的元素写法是property:value， property是css里面的

4.注意句尾的分号！！！



### style internal -> 需要告知具体的部件

**如果有多个，在style里面分段写**

![CSS selector](https://www.w3schools.com/css/selector.gif)

<style>
body {background-color: powderblue;}
h1   {color: blue;}
p    {color: red;}
</style>



### class -> 只要继承它，就是就按里面的来写

To create a class; write a period (.) character, followed by a class name. Then, define the CSS properties within curly braces {}

<style>
.city {  
    background-color: tomato;  
    color: white;  
    padding: 10px;
}
</style>


### meta

**如果有多个，分段写**

#<meta charset="UTF-8">

#<meta name="keywords" content="HTML, CSS, JavaScript">

#<meta name="description" content="Free Web tutorials">



### 一个element里面有多个tag

用空格隔开

```javascript
<p id="demo" onclick="displayDate()">The time is?</p>
```


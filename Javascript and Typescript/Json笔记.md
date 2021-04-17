# Json

## **增**

```javascript
 * request: {
    dataList:[
      {
        id: "007",
        speed: 6.5,
        latitude: 40.741895,
        longitude: -73.989308,
        elevation: 50,
        fuel: 89,
        damage: 0,
        nectar: 20,
        honey: 8,
      },
      ...
    ]
 * },
     
 * response: {
 *  status: 0,
 *  msg: 'ok',
 *  data: {}
 * }


```

## **删**

```javascript
 * request: {
    delIdList:[
      { id: "007" },
      { id: "008" },
      ...
    ]
 * },
     
 * response: {
 *  status: 0,
 *  msg: 'ok',
 *  data: {}
 * }
```

## **改**

```javascript
request: {
    updateList:[
      {
        id: "007",
        speed: 6.5, //速度
        latitude: 40.741895, //纬度
        longitude: -73.989308, //经度
        elevation: 50, //海拔
        fuel: 89, //燃料 %
        damage: 0, // 损耗 %
        nectar: 20, //g 采蜜
        honey: 8, //g 蜂蜜
      },
      ...
    ]
 * },
 
 * response: {
 *  status: 0,
 *  msg: 'ok',
 *  data: {}
 * }   
```

## **查**

```javascript
* request: {},
    
 * response: {
 *  status: 0,
 *  msg: 'ok',
 *  data: [
     {
        id: "007",
        speed: 6.5, //速度
        latitude: 40.741895, //纬度
        longitude: -73.989308, //经度
        elevation: 50, //海拔
        fuel: 89, //燃料 %
        damage: 0, // 损耗 %
        nectar: 20, //g 采蜜
        honey: 8, //g 蜂蜜
     },
     ...
 *  ]
 * }

```

## **w3school例子**

```javascript
{
"employees":[
  {"firstName":"John", "lastName":"Doe"},
  {"firstName":"Anna", "lastName":"Smith"},
  {"firstName":"Peter", "lastName":"Jones"}
]
}
```

```javascript
{
"employee":{ "name":"John", "age":30, "city":"New York" }
}
```

## 其他例子：

```javascript
{"menu": {
  "id": "file",
  "value": "File",
  "popup": {
    "menuitem": [
      {"value": "New", "onclick": "CreateNewDoc()"},
      {"value": "Open", "onclick": "OpenDoc()"},
      {"value": "Close", "onclick": "CloseDoc()"}
    ]
  }
}}
```



# 满足以下格式的文本叫做JSON文本

**关于JSON的常识**

1. JSON是一种格式和语法（syntax ）
2. 



- Data is in name/value pairs  数据格式都是key/value一对的格式
  - JSON的key能且仅能是字符串（必须要由双引号括起来）
  - Jason的value可以是以下的类型
    - a string，**对于是string类型的value，一定要由双引号括起来**
    - a number
    - **an object (JSON object)**
    - **an array**
    - a boolean
    - null
- Data is separated by commas 数据之间由逗号分隔
- Curly braces hold objects  **Jason对象一定有大括号进行括起来**
- Square brackets hold arrays 方括号包着数组





# Json格式和object格式的对比

1.JSON的语法object语法的子集！

2.虽然他们都是key:value的形式，但是

​	JSON的key必须是字符串，而且必须由双引号括起来；object的key可以是字符串，可以是数字，也可以是标志符

​	object的value类型不仅仅是JSON那些，还能是function, date，undefine类型



# JSON与XML的对比

XML is much more difficult to parse than JSON.
JSON is parsed into a ready-to-use JavaScript object.





# JSON的作用

- **与后端交换数据**

  ​	1. 后端传来的数据永远是string类型

   2. string写的格式是JSON的格式时，就能把这个string解析为一个JavaScript的object

      ```
      var str = '{"name":"Jiasui", "age":"22"}'
      var obj = JSON.parse(str)
      ```

      



# AJAX request

- **AJAX表示Asynchronous JavaScript And XML.**

  ​	解释：这里的XML具有误导性，**实际上AJAX应用更多的用JSON来传输数据而不是XML**

- **AJAX 的作用是从前端访问后端**

  - 从后端读取数据到前端
  - 从前端发送数据到后端
  - 更新页面（无需重新加载）

- **AJAX的组成部分**

  - 1.浏览器内置的**XMLHttpRequest**对象，用于从后端请求数据
  - 2.JS and HTML DOM，用于显示和使用数据

- **AJAX的工作流程**

  ​	1.事件发生

  ​    2.XMLHttpRequest对象被JS创建

  ​    3.XMLHttpRequest发送请求到后端

  ​    4.后端处理请求，并发送响应到前端

  ​    5.JS读取请求，并进行相关动作





遗留问题：从后端请求数据

https://www.w3schools.com/js/js_json_parse.asp



# DOM

#### **DOM是什么**

- DOM代表着Document **Object Model** （文档对象模型）
- 当页面加载完成的时候，浏览器会创建这个**HTML**页面的**D**ocument **O**bject **M**odel（文档对象模型），如下所示，这一整个模型就是一个**HTML DOM**
  - HEML DOM是一个树状模型
  - 这棵树是一个objects组成的树

![DOM HTML tree](https://www.w3schools.com/js/pic_htmltree.gif)

#### **DOM有什么用**

- HTML DOM是HTML的一个程序接口（programming interface），它将HTML element定义为对象，同时定义了这个对象的属性（**properties**），方法（**methods**）和事件（**events**）
- The HTML DOM is a standard **object** model and **programming interface** for HTML. It defines:
  - The HTML elements as **objects**
  - The **properties** of all HTML elements
  - The **methods** to access all HTML elements
  - The **events** for all HTML elements
-  **The HTML DOM is a standard for how to get, change, add, or delete HTML elements.**

一.**修改元素**

1. 对html element进行添加，删除和修改
2. 对css进行修改
3. 对attribute进行修改

**二.修改事件**

​	1.对现有event进行响应

​	2.创建新的event



#### HTML DOM定义的常见的属性和方法

https://www.w3schools.com/js/js_htmldom_document.asp

| 属性（properties）                    | 方法（methods）                                              |
| :------------------------------------ | :----------------------------------------------------------- |
| **innerHTML**：用于获取html元素的内容 | **getElementById**(id):用于获取id名为特定名字的元素 document.getElementById("demo").innerHTML = "Hello world" |
| *attribute*                           | **getElementsByTagName(*name*)**                             |
| *style.*property                      | **getElementsByClassName(*name*)**                           |
|                                       | **setAttribute(attribute, value)**                           |
|                                       |                                                              |

**document是所有objects的根object**，想要访问其他element的话，要通过document来进行访问





# event

有一种特殊的attribute叫event attribute，他能监听发生在html element上的事件，To assign events to HTML elements you can use event attributes.

对事件进行响应的方式就是将要执行的动作用JavaScript code写在事件后面

常见的事件

- **When a user clicks the mouse**
- **When a web page has loaded**
- When an image has been loaded
- When the mouse moves over an element
- **When an input field is changed**
- When an HTML form is submitted
- When a user strokes a key







```javascript
document.getElementById("myBtn").onclick = displayDate;
```


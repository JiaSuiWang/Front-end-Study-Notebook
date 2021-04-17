## React工程整理

## **项目设计的流程**

1.配置环境

2.设置项目架构

​	技术栈，前端组件设计，API设计

3.完成前端

​	3.1完成前端页面：功能性（每个页面的组件）+ 美观性（CSS渲染）

​	3.2完成前端组件之间的通信

​	3.3完成前端API ： 利用axios(封装好的ajax请求)处理http请求

4.完成后端

​	4.1后端连接文件系统（数据库或者JSON文件）

​	4.2完成后端API（node.js. spring boot, KOA）

5.完成前后端连调



## 前端工具：Inspect（F12）

- Element （选择Select an element to inspect it）查看元素

  - 将鼠标放到页面上的组件之后就能看到对应的html代码
  - 同时在页面右侧有
    - Styles **//可以添加样式来调试CSS，对颜色可以直接取色**
    - Computed
    - Layout
    - Event Listeners
    - DOM Breakpoints
    - Properties
    - Accessibility

- Console 网页打印，Bug提示

- Network 查看前后端通信

- Application 

  - **Local Storage**：浏览器关闭以后信息还在
  - **Session Storage**：浏览器关闭之后信息没有，session表示单次前后端会话
  - **Cookies**：只能存4K
  - 会存哪些信息：1.登陆凭证 2.用户信息（最好存在后端里面，不然有危险）
  - 相当于是前端缓存，里面信息存储的方式都是key-value形式

  

## 常见提示错误

解决方式：1.经验 2：直接复制错误信息直接查

w3cschool：https://www.w3schools.com/js/js_errors.asp

更详细的信息：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Errors

| Error Name     | Description                                  |
| :------------- | :------------------------------------------- |
| EvalError      | An error has occurred in the eval() function |
| RangeError     | A number "out of range" has occurred         |
| ReferenceError | An illegal reference has occurred            |
| SyntaxError    | A syntax error has occurred                  |
| TypeError      | A type error has occurred                    |
| URIError       | An error in encodeURI() has occurred         |



## 常见网络错误状态码 

HTTP status messages ： https://www.w3schools.com/tags/ref_httpmessages.asp

- 200 请求成功
- 400 有可能是请求方式错误 put, get, post之类的
- 403 请求参数报错
- 404 没有找到后端接口
- 500 后端报错了，直接找后端





## 工作量和完成时间

##### 前端工作量：

1.完成页面的部件设计（功能性） 

2.完成部件的渲染（美观） 

3.根据功能完成响应函数和组件通信

​	3.1保持搜索后的元素继续观察

​	3.2随机变动的值

​	3.3唯一的ID生成

​	3.4websocket长连接

4.前端API设计



##### 后端工作量

1.理解代码：现有的node.js的后端框架设计

2.用spring boot写的后端代码



##### 其他工作量：

1.学习**D3**库

2.学习完**JavaScript**剩下的部分

3.系统学习**React**

4.系统学习**Typescript**



## 项目框架怎么搭建：

用官网脚手架



## 怎么运行一个react项目：

1.执行命令**npm install**

- **作用**：将package.json文件里面所有列举的依赖都下载下来，并且自动创建一个node_modules文件夹，将依赖下载到里面去
- **原理**：根据package.json文件里面Scripts部分的描述，去找到项目对应的操作方式
- package.json文件，里面列举了项目需要的依赖包
- package.json文件不需要自己写，里面的内容由1.react脚手架完成 2.每当npm install一个新的依赖的时候会自动写入到该文件里面

2.执行命令npm start来将项目跑起来



## **代码结构**和命名规范：

### 重要！！一个完整的项目包括以下模块

- REACT-TYPESCRIPT

  - node_modules

    - 各种依赖包的依赖包

  - public

    - 里面什么都有，**重要的就是index.html，和favicon.ico，其他都可以删掉**
    - index.html **//这个里面声明了id为root的element**

  - ### src **//最重要，编程就在这里面编**

    - **components**  **//用于写子组件**
      - 子组件1
        - index.tsx
        - index.module.css
      - 子组件2
        - index.tsx
        - index.module.css
    - **interface** **//用于写全局的接口，防止繁琐的export**
    - styles(views)
    - **App.tsx**  **//默认的父组件**
    - App.css
    - **index.tsx** **//对默认的父组件也就是App.tsx进行展示**
    - index.css

  - .gitignore  //git 提交配置文件

  - package-lock.json 

  - package.json

  - tsconfig.json //用来编译这个项目的根文件和编译选项

  - yarn.lock /依赖包下载锁定文件



##### index.tsx, App.tsx, index.html之间的调用



**index.tsx**

1.引入父组件 App.tsx，并在ReactDOM.render里面进行显示

2.React.StrictMode是严格的声明，比如table下面不能有div

3.在最后用了index.html文件里面id为root的组件

```typescript
import App from './App';
import React from 'react';
import ReactDOM from 'react-dom';
ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById('root')
);
```



 **App.tsx**

```typescript
const App: FC = () => {
    return (
        <div>
			<子组件1/>
        	<子组件2/>
       	 	<子组件3/>
        </div>
    )
}
export default App;
```

 

**index.html**

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>React App</title>
  </head>
    
  <body>
    <div id="root"></div>
  </body>
</html>
```



## 子组件的规范

**强烈建议：建立一个Test子组件，其他组件的编写先在Test组件里面完成**

**对每一个子组件都应该建立一个单独的文件夹**

- 文件夹的命名按照子组件的名字来命名，首字母大写的驼峰命名法
- 文件夹下有两个文件：index.tsx和index.module.css
  - react的ts文件后缀名都是tsx，命名为index.tsx的好处的是
    - 1.默认就是这样命名
    - 2.当别的包需要使用这个的时候，路径不需要指定到文件名，只需要指定到子组件文件夹的路径即可
  - index.module.css，这样命名的原因是，import './index.css'可能会导致**全局样式的样式冲突**问题（当有两个css文件有同一个名字的class的时候，系统不知道用哪一个），为了避免冲突，所以使用module.css，这样对于每一个css文件的class都会生成一个随机字符串放在class名字的后面



### index.tsx页面的结构

1.import所需要的依赖 （特殊的依赖，先不引入，而是quick fixed依赖）

2.可选：所需要的常量定义

3.子组件的function定义

​	3.1 用useState的方式定义常量

​	3.2 定义API(事件处理函数)

​	3.3 用useEffect的方式定义监听函数

​	3.4 写返回的





### index.tsx的语法格式和规范

### 

逻辑：react

实现：Typescript



#### 1.写TS的FC函数

TS函数写法：

```typescript
const Query: FC<IProps> = ({ setBeesList, beesList }): JSX.Element => {return()}
const Represent: FC<IProps> = ({beesList}):JSX.Element=>{return()}
const Statistics: FC = (): JSX.Element => {return()}
const ChildComponent : FC<IProps> = ({name, age, handleChild}):JSX.Element =>{return()}
const App: FC = () => {return()}
```

```typescript
//核心
const ElementName: FC = () => {return()}  
//传入参数，在函数后面用<>声明传入类型，在()里面写入解构好的参数
const ElementName: FC<Type> = (destructure) => {return()} 
//声明返回值类型，在括号后面标注返回值的类型
const ElementName: FC<Type> = (destructure):JSX.Element => {return()} 
```



#### 2.写html上的组件

用原生的html组件就行

注意：HTML和JS/TS是两码事

​	对于**页面的整个设计**，增加一个按钮，设计一个表单，都是HTML的事情

​	涉及到**页面的操作**，响应函数，才是JS/TS的事情！！！

阅读https://ant.design/components/overview-cn/

或者https://www.w3schools.com/tags/default.asp、





#### 3.写逻辑

##### 1.分析页面结构：

- **components**  
  - **Query**
    - index.tsx
    - index.module.css
    - **SubQuery**
      - index.tsx
      - index.module.css
  - **Represent**
    - index.tsx
    - index.module.css

##### 2.分析页面上的组件：

**Query**

<img src="C:\Users\Jiasui Wang\AppData\Roaming\Typora\typora-user-images\image-20210413093004837.png" alt="image-20210413093004837" style="zoom:33%;" />

**SubQuery**

<img src="C:\Users\Jiasui Wang\AppData\Roaming\Typora\typora-user-images\image-20210413092949438.png" alt="image-20210413092949438" style="zoom:33%;" />

**Represent**

![image-20210413093030661](C:\Users\Jiasui Wang\AppData\Roaming\Typora\typora-user-images\image-20210413093030661.png)



##### 3.想要实现的功能：

1.在Query页面点击add按钮时，会弹出子表单SubQuery的内容

2.子表单可以输入新增数据的信息，

​	点击OK可以将数据展示到Represent页面

​	点击Cancel会关闭子表单



##### 4.每个功能对应的数据流向

> 1.在Query页面点击add按钮时，会弹出子表单SubQuery的内容

1.Query页面的add按钮上需要绑定一个点击event，这个事件触发的结果是弹出SubQuery页面内容



> 2.子表单可以输入新增数据的信息

```
<input type="text" value={233} /> 
```

每一个表单都有一些属性

type属性，代表input的类型

value是这个input显示的值

​    点击OK可以将数据展示到Represent页面

​	点击Cancel会关闭子表单



##### 5.最终目的

明确每个组件有**哪些依赖**要import

每个组件有**哪些变量/接口**要声明

每个组件的**Hook函数**都有哪些

​	**函数的输入参数都是**哪些

​	返回值是什么



最终逻辑!

//1.要在form里面显示值“value = {params.speed}”，就需要定义变量params（一个对象）

//2.要想定义param这个对象，就需要定义它的规范也就是接口 

  //接口名称第一个I

  //显示都用string类型

//3.经过以上两步，就可以给每一个表单加上一个value的attribute，来与对象params的里面的值分别绑定

//4.为了让表单里的数可以编辑，要绑定onChange事件，注意不是onClick事件

  //逻辑,主动作用：通过event handler来更新params的值，由于params是用useState定义，所以会触发视图更新

  //逻辑,被动作用：又由于value attribute已经和params绑定在一起,所以显示也会更新！

//5.那么onChange的event handler如何写呢，我们的目的是更新对应表单的值所以

  //1.要知道更改谁，所以需要找到绑定在这个表单上面的变量，所以要传入它的名字，这是函数的第一个参数

  //2.要知道更改后的值是什么，用event.target.value来获取，所以需要获得event是什么，这是第二个参数

  //因此写成 onChange={(ev) => {handleChange(ev, 'speed')}}，这里我们用handleChange来帮我们调用setParams来更改

//6.那么handleChange函数又怎么写呢

  //1.首先它是一个箭头函数，其次这个函数的功能就是调用setParams

  //2.其次他的传入参数比较复杂，

​    //1.event,在Typescrip里面，所有的变量都应该有类型，它是ChangeEvent<HTMLInputElement>，鼠标放在ev上就能显示

​    //2.key，是一个string类型

  //3.setParams函数用到了解构的方法，

​    //1.只修改键为[key]的值，并用event.target.value为其赋予了修改后的值

​    //2.其他保持不变，语法为...params

//7.最后写click的event handler,也就是handleOK

  //因为subQuery的父组件已经有handleAdd方法了，所以思路就是把它引进来

  //1.在父组件中使用子组件SubQery时，应该将handleAdd，引入， <SubQuery handleAdd={handleAdd}/>

  //2.在子组件里面，应该有一个参数去接受它，这里应该定义一个接口!

​    //1.接口定义IProps，里面只有一个函数，普通函数的类型都是 handleAdd:()=>void;

​    //2.更改component的传入参数，

​      //需要在FC后面用尖括号写上传入的类型<接口名称>，

​      //以及在圆括号里面将接口进行解构，解构的内容记得用圆括号！！！

​      //const SubQuery:FC = () =>{} 到const SubQuery:FC<IProps> = ({handleAdd}) =>{}



### index.css页面的结构



### index.css页面的语法格式和规范





#### 



## 子组件之间的通讯：

两种方式：

1.将子组件中的函数，变量传递到另一个子组件中，在另一个子组件中操作

2.将两个子组件的变量都传递到父组件中，在父组件中操作：状态提升






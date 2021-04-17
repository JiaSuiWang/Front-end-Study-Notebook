# React笔记-Javascript版本的

## **react示例**

```javascript
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



## **什么是react**

React is a **JavaScript library** for building user interfaces.



## React原理

React creates a **VIRTUAL DOM** in memory. 

**没有直接对browser DOM进行操作，而是先创建一个虚拟的DOM,最后把修改放到browser DOM**

Instead of manipulating the browser's DOM directly, React creates a virtual DOM in memory, where it does all the necessary manipulating, before making the changes in the browser DOM.





## React uses ES6

**ES6 = ECMAScript 6 =  ECMAScript 2015**， 用来标准化JavaScript（standardize JavaScript）

ES6重要特征

- Classes
- Arrow Functions
- Variables (let, const, var)



### **class**

##### 声明

lower camel case, upper camel case

curly braces

semicolon分号

1.所有的类都包含constructor函数，它会在实例被创建的时候自动调用

2.class里面声明的参数用this来表示

3.类的实例需要用new关键字

```javascript
class Car {
  constructor(name) {
    this.brand = name;
  }
  present() {
    return 'I have a ' + this.brand;
  }
}

mycar = new Car("Ford");
```

##### 继承

1.用关键字 `extends` 

2.子类会自动继承父类的所有method

3.**super（）函数**

​	**一定要在子类的constructor()函数中调用super()函数**，它的功能是

​		**1.自动调用父类的构建函数** 

​		**2.得到父类所有的properties and methods**



### Arrow箭头函数

##### 1.写法

```javascript
hello = function(){} //普通函数
hello = () =>{} //箭头函数
```



##### 2.this

箭头函数与普通函数不仅仅是语法上面的不同，还有this也不一样



With a regular function `this` represents the object that *calls* the function:

如果一个函数是一个普通定义的函数，那么在该函数里面，this代表着调用这个函数的对象



with an arrow function `this` represents the *owner* of the function:

**如果一个函数是一个箭头函数，那么在这个函数里面，不管谁调用的它，this都代表着这个类的对象**





### var, let, 和 const

##### **var跟let的区别：**

`var` has a *function* scope, not a *block* scope.

​	If you use `var` inside of a block, i.e. a for loop, **the variable is still available outside of that block**.

`let` has a *block* scope.

​	If you use `let` inside of a block, i.e. a for loop, **the variable is only available inside of that loop.**



## React Render HTML

1.react的作用就是在一个网页中渲染HTML

​	render the HTML to the DOM，因为此前都是在虚拟的DOM里面做的，所以这个函数的只用就是把虚拟的HTML tag render到真实的DOM里面

2.**这种渲染通过ReactDOM.render()函数实现**（React renders HTML to the web page by using a function called `ReactDOM.render()`.）



**ReactDOM.render()**

​	1.两个输入参数：HTML code, HTML element

​	2.函数的作用就是将给定的的**HEML code**在给定的**HTML element**进行展示

```javascript
ReactDOM.render(<p>Hello</p>, document.getElementById('root'));
```

​	





## lifecycle生命周期

生命周期主要讲的就是前端页面从**生成Mounting**-**更新Updating**-**销毁Unmounting**等几个阶段的过程，**框架一般会提供该过程的回调和可用参数**



**Mounting**有两个大的阶段：

1.**initial the component**/ component is initialed

2.**render the component/HTML /elements  in DOM** 

​	render the HTML to the DOM，因为此前都是在虚拟的DOM里面做的，所以这个函数的只用就是把虚拟的HTML tag render到真实的DOM里面





#### **Mounting**：

Mounting means **putting elements into the DOM**

Mounting又可以分为以下几个阶段：

**When the component is initiated** (before anything else):  **constructor()**

​	1. natural place to set the `state` object based on the initial props

​	2.calling the `super(props)` will 

​			initiate the parent's constructor method

​			**inherit methods** from its parent

**Right before rendering** the element(s) in the DOM:   **getDerivedStateFromProps()**

**Render the element** in DOM : **render()**

**After the component is rendered** in the DOM： **componentDidMount()**



#### **Updating**：

A component is updated whenever there is a change in the component's **`state`** or **`props`**.



**first method that is called** when a component gets updated : **getDerivedStateFromProps**()

​	 natural place to set the `state` object based on the initial props

**whether React should continue with the rendering** or not. : **shouldComponentUpdate**()

​	return a Boolean value

**re-render** the HTML to the DOM : **render()**

**check what the values were** *before* the update ：**getSnapshotBeforeUpdate()**

**after the component is updated** in the DOM ：**componentDidUpdate**



#### Unmounting

when a component is removed from the DOM

只有一个函数

when the component **is about to be removed** from the DOM **componentWillUnmount（）**





## JSX

### JSX是什么

JSX 代表 JavaScript XML.

JSX 是基于ES6的JavaScript的扩展（并不是官方的，而是react自己搞得），它会被翻译为JavaScript at runtime

1. **语法上**：**JSX允许你在Javascript代码里面写HTML** JSX which allows you to **write HTML tags inside the JavaScript code**,and place them in DOM

2. **作用上**，**JSX可以把HTML tag转化为react元素 **JSX converts **HTML tags into react elements**.

   ```javascript
   const myelement = <h1>I Love JSX!</h1>;
   //没必要用createElement函数或者appendChild函数
   const myelement = React.createElement('h1', {}, 'I do not use JSX!');
   ```

```typescript
如果我们不写=的话，() => {}是一个reference，
	可以在event handler里面直接这样写，例如onClick = {() => {handleOK()}}，
    或者在接口声明的时候handleAdd: () => void;


Statistics = () => {} 
const Statistics = () => {}
const Statistics:FC = () => {}  // FC是Function Component的缩写，用于声明该变量是component的类型
const Statistics:FC = ():JSX.Element => {}

如果加参数:
const Statistics:FC<IProps> = ({setBeesList, beesList}):JSX.Element => {}

```



### JSX的语法

JSX可以用于插入一个很大的HTML代码块，**语法是，将这些代码块包裹在括号（）里面**

如果是只有一行可以不加括号

```jsx
const myelement = (
  <ul>
    <li>Apples</li>
    <li>Bananas</li>
    <li>Cherries</li>
  </ul>
);
```

**注意两点：**

​	1.HTML代码必须包裹在一个顶层的元素里面，比如<div>或者<fragment>

​	2.HTML一定要正确结尾 Close empty elements with `/>`

```javascript
const myelement = <input type="text" />;
```





# 花括号在这！！！花括号在这！！！在JavaScript里面写HTML语言的时候（JSX）,要打印（渲染）变量的话就要用{}包起来

## JSX中的表达式

With JSX you can write expressions **inside curly braces `{ }`**.

**variable, or property都可以写在里面**

```javascript
const myelement = <h1>React is {5 + 5} times better with JSX</h1>;
```







# React component 

components的作用跟函数一样，只不过它返回的是HTML elements.（通过一个 render() function）

Component 可以用两种方式创建，根据创建方式的不同把components分为两类：Class components 和 Function components

**component 的最大作用就是增加代码复用**



#### **Class components**

1.**components的命名要首字母大写**

2.**必须extends React.Component**

3.里面必须包含`render()` method用来返回HTML元素

**创建：**

```javascript
class Car extends React.Component {
  render() {
    return <h2>Hi, I am a Car!</h2>;
  }
}
```

**使用：**

使用跟普通的HTML元素相同的语法就可以：  `<Car />`

```javascript
ReactDOM.render(<Car />, document.getElementById('root'));
```



##### 第一种使用property的方法： Constructor的state

在创建的时候被调用，用于初始化component's properties.

component properties 被保存在叫做 `state`的对象（object）里面

**注意要在constructor的函数里面调用super（）方法，以及 extends React.Component**

```javascript
class Car extends React.Component {
  constructor() {
    super();
    this.state = {color: "red"};
  }
  render() {
    return <h2>I am a {this.state.color} Car!</h2>;
  }
}
```



##### 第二种使用property的方法：Props

1.在使用components的时候，就像定义attribute一样，传入参数！

2.传入以后，就可以在render里面直接调用了

```javascript
class Car extends React.Component {
  render() {
    return <h2>I am a {this.props.color} Car!</h2>;
  }
}

ReactDOM.render(<Car color="red"/>, document.getElementById('root'));
```





# state和props两种方式对比：

1.使用state，一定有constructor函数，因为state在里面被定义

2.使用props的时候constructor函数可选，但是如果要constructor函数，那一定要把props当参数传进去

3.

props是“隐形的”，参数传入以后会被component自动接受为props对象，用的时候直接用this.props.参数名

state是显形的，需要自己在constructor函数里面定义和赋值







##### component复用：

为了增加代码复用，在不同的文件调用components：

```javascript
export default Car;.
```



##### Class components的模板:使用state

```javascript
class ComponentName extends React.Component{   //1.名字大写 ，2.extends React.Component
    constructor(){  //3.用constructor方法
        super();   //4.一定要用super()函数
        this.state = {key1: "value1"}; //5.把类的properties放在state这个对象里面
    }
    
    render(){   //6.render函数用于返回HTML element
        return (
        	//HTML Element
        )
    }
}
export default ComponentName;
```

##### Class components的模板:使用props

```javascript
class ComponentName extends React.Component{   //1.名字大写 ，2.extends React.Component
    constructor(props){  //3.用constructor方法,一定要传入props
        super(props);   //4.一定要用super()函数
    }
    
    render(){   //5.render函数用于返回HTML element
        return (
        	//HTML Element
        )
    }
}
export default ComponentName;
```



##### Class components的模板:同时使用state和props

因为要使用state定义properties,就需要用constructor函数

因为选择用了constructor函数，就必须传入props参数

```javascript
class ComponentName extends React.Component{   //1.名字大写 ，2.extends React.Component
    constructor(props){  //3.用constructor方法
        super(props);   //4.一定要用super()函数
        this.state = { //5.把类的properties放在state这个对象里面
            key1: "value1",
            key2: "value2"
            key3: "value3"
        }; 
    }
    
    render(){   //6.render函数用于返回HTML element
        return (
        	//HTML Element
        )
    }
}
export default ComponentName;
```



#### Function components

**1.命名一定要首字母大写**

2.跟创建函数的格式一样，只不过返回的是HTML Element

```javascript
function Car() {
  return <h2>Hi, I am also a Car!</h2>;
}
```

使用方式也是  `<Car />`



## Function Component的模板

```typescript
1.const ComponentName = () => {} //先写一个箭头函数
2.const ComponentName:FC = () => {} //然后他的类型是Function Component
3.const ComponentName:FC<IProp> = ({beeList, setBeeList}) =>{} //然后它的输入参数是什么，解构一下Destructure

4.const ComponentName:FC<Iprops> = ({beeList, setBeeList}) =>{  //它会return一个什么
    return(
        <div>
        	content
        </div>
    )
}

//开始看接口定义了
//首先，如果有输入参数，那么一定会有一个输入参数的接口，接口本质是一种变量类型，就像int和string
const interface{
    beeList: IBeeProps[];
    setBeeList:React.Dispatch<React.SetStateAction<IBeeProps[]>>
}
5.const ComponentName:FC<Iprops> = ({beeList, setBeeList}) => { 
    
}

//其次，内部参数用useState初始化的时候需要定义接口
interface Iprops {
    beeList: IBeeProps[];
    setBeeList:React.Dispatch<React.SetStateAction<IBeeProps[]>>
}

interface Iparams {
    fuel: string;
    damage: string;
}
 
6.const ComponentName:FC<Iprops> = ({beeList, setBeeList}) => { 
    const [params, setParams] = useState<Iparams>({
        fuel:"1",
        damage:"2"
    })
    
}
```







# Class和Function的两种写法对比

**分别对应react里面的两种写法：class和hook**

class写法需要用rende() function来返回HTML element

hook写法直接用return就返回



class写法定义properties的方法就是使用state或者props

function(hook)的写法就是，使用useState定义变量，使用effectState来定义监听事件！





## props

##### **定义：**

1.propos是传递给component的参数

2.**传递方式是通过HTML的attribute传入**

3.component会接收参数as a `props` object:



##### **示例：**

```javascript
const myelement = <Car brand="Ford" />;
```



##### **功能**：

**props可以作为参数的在不同的component里面传递**

```javascript
class Car extends React.Component {
  render() {
    return <h2>I am a {this.props.brand}!</h2>;  /////////////////在这里被接受了
  }
}

class Garage extends React.Component {
  render() {
    return (
      <div>
      <h1>Who lives in my garage?</h1>
      <Car brand="Ford" />      //////////////////////////////在这里传入了参数
      </div>
    );
  }
}

ReactDOM.render(<Garage />, document.getElementById('root'));
```





##### 语法：

**如果component有一个constructor函数，那么在super()里面一定要加props**

```jsx
class Car extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return <h2>I am a {this.props.model}!</h2>;
  }
}

ReactDOM.render(<Car model="Mustang"/>, document.getElementById('root'));
```



**在使用component的时候，如果需要传递参数且参数是一个变量，那么就需要把这个变量放到一个花括号里面**

```javascript
class Car extends React.Component {
  render() {
    return <h2>I am a {this.props.brand.model}!</h2>;
  }
}

class Garage extends React.Component {
  render() {
    const carinfo = {name: "Ford", model: "Mustang"};
    return (
      <div>
      <h1>Who lives in my garage?</h1>
      <Car brand={carinfo} />
      </div>
    );
  }
}

ReactDOM.render(<Garage />, document.getElementById('root'));
```



## State

React有一个**内置的（built-in）object叫做state**，它用来存**放属于该component的propertyies**

**注意两点：**

1.要使用state一定要在constructor的方法里面初始化它！

2.如果要修改State里面的参数的话，必须用**this.setState()**方法来实现

**每次当State里面的参数改变，react都会重新渲染组件！！！**

Always use the `setState()` method to change the state object, it will ensure that the component knows its been updated and **calls the render() method** (and **all the other lifecycle methods**).







# React Event

### 写法有三点要注意：

1.**React的event命名**都是第一个字母小写的驼峰命名，而不是HTML里面的

2.event的**event handlers要写在花括号里面**, 而不是双引号里面

3.**event handlers传递的是reference（地址），而不是函数调用**

```javascript
//React里面的写法 1.onClick驼峰 2.event handler写在花括号里面 3.传递的是处理函数的reference
<button onClick={shoot}>Take the Shot!</button>

<button onclick="myFunction()">Click me</button> 
```



### 永远用Arrow Function

with an arrow function `this` represents the *owner* of the function:

**箭头函数的this永远代表着定义这个函数的类**



### event handlers可以访问event object

Event handlers have access to the React event that triggered the function.



**注意！！event handler函数可以自动获取触发函数的event！！**

```javascript
class Football extends React.Component {
  shoot = (a, b) => {
    alert(b.type);
    /*
    'b' represents the React event that triggered the function,
    in this case the 'click' event
    */
  }
  render() {
    return (
      <button onClick={(ev) => this.shoot("Goal", ev)}>Take the shot!</button>
		//ev是这个箭头函数的传入参数，它调用了shoot函数并将这个参数继续传递给了它
		//这个传入到响应函数的参数ev，是响应函数自动获取的，代表着触发该响应函数的事件，也就是click event
    );
  }
}

ReactDOM.render(<Football />, document.getElementById('root'));
```

<button onClick={(ev) => this.shoot("Goal", ev)}>Take the shot!</button>

**这个传入到响应函数的参数ev，是响应函数自动获取的，代表着触发该响应函数的事件，也就是click event**











# React Form 表单

1.获取表单的值直接用 **event.target.value来访问**！！！很重要！！！













# 总结：在哪些情况下我们需要用花括号

1.写**JSX**时，HTML tag里面使用变量

2.写**components**时，在components声明里面用于解构参数

3.写**components**时，返回html element时候，在里面使用变量

4.使用**components**时，给它参数的时候

5.在**react event**里面event handler需要





**1.定义的时候**（return：在JavaScript里面使用html）

```javascript
const myelement = <h1>React is {5 + 5} times better with JSX</h1>;
```

**2.返回的时候**（return：在JavaScript里面使用html）

```javascript
class Car extends React.Component {
  render() {
    return <h2>I am a {this.props.brand.model}!</h2>;
  }
}

  render() {
    return (
      <div>
        <h1>My {this.state.brand}</h1>   //在JavaScript里面使用html
        <p>
          It is a {this.state.color}
          {this.state.model}
          from {this.state.year}.
        </p>
      </div>
    );
```

**3.向component传递参数的时候**

```javascript
const carinfo = {name: "Ford", model: "Mustang"};
<Car brand={carinfo} />
```



**4.写react event的时候**

```javascript
<button onClick={shoot}>Take the Shot!</button>
```



**5.定义函数，接受参数，解构的时候需要！**

```typescript
//调用component
<Query 
    setBeesList={setBeesList} 
    // 这个不用看，只是为展示一下添加之后，表格内容
    beesList={beesLists}
/>

//接受参数的接口定义
interface IProps {
    setBeesList: React.Dispatch<React.SetStateAction<IBeesProps[]>>;
    beesList: IBeesProps[]
}

//component定义
const Query: FC<IProps> = ({ setBeesList, beesList }): JSX.Element => {}
```




# 学习Hook

为何使用react：入门比较难，但是之后就会发现很简单，因为提供了很多的语法糖

**what** : 

**Hooks are functions that let you “hook into” React state and lifecycle features from function components.** 

1.Hooks 是一个函数

2.Hook让你在function components里“钩入” React state 及lifecycle等特性



**why**存在：

- Hooks allow you to reuse stateful logic without changing your component hierarchy.**Hook 使你在无需修改组件结构的情况下复用状态逻辑**
- Hooks let you split one component into smaller functions based on what pieces are related (such as setting up a subscription or fetching data)**Hook 将组件中相互关联的部分拆分成更小的函数（比如设置订阅或请求数据**
- Hooks let you use more of React’s features without classes.**Hook 使你在非 class 的情况下可以使用更多的 React 特性**



**相比于class的component的写法，使用hook的function component的写法的有优点**：	摘抄自ahook：

​	对比而言，React Hooks 的主要特性之一就是可以**在组件之间共享可复用的状态逻辑**，方便了开发者将**业务逻辑**和 **UI 视图**进行解耦，从而**状态**与 UI 的界限会越来越清晰







**Hook定义**：

**Hooks are functions that let you “hook into” React state and lifecycle features from function components.** 

1.Hooks 是一个函数

2.Hook让你在function components里“钩入” React state 及lifecycle等特性





## Hook的重要规则：

Hook 就是 JavaScript 函数，但是使用它们会有两个额外的规则：

- 只能在**函数最外层**调用 Hook。不要在循环、条件判断或者子函数中调用。
- 只能在 **React 的函数组件**中调用 Hook。不要在其他 JavaScript 函数中调用。（还有一个地方可以调用 Hook —— 就是自定义的 Hook 中，我们稍后会学习到。）



# State Hook写法

**State Hook的意义就是，每当用State Hook定义的变量的值改变的时候，都能让react来重新渲染组件，把最新的值传给他**

`useState` is a *Hook*，他是一个方法（函数）

`useState` returns a pair: the *current* state value and a function that lets you update it. 

```typescript
const [age, setAge] = useState(42);
const [fruit, setFruit] = useState('banana');
const [todos, setTodos] = useState([{ text: 'Learn Hooks' }]);
```



## **如何调用 `useState` 的 Hook**：

### 1.**引入 **

import {useState} from ‘react’;

### 2.**声明变量**

```typescript
 const [count, setCount] = useState(0);
```

上面这一行语句作了以下的事情：

使用useState**方法**声明了一个叫state的变量，这个变量的类型是number型，它的初始值是0，这个方法返回了当前state，以及更新该state的函数

#### 1.定义变量

定义了一个叫做名为count的**state变量**，**它不会随着函数的退出后而消失，而是会被React保留**

#### 2.传参

给useState一个**唯一的参数**，也就是**初始state**

##### 传参**注意两点**：

1.这里给定参数的时候，可以在useState关键字后面**标识出变量是什么类型**的,例如

```typescript
 const [count, setCount] = useState<number>(0);
```

2.这里的**参数类型可以是很复杂**的类型，比如对象：

```typescript
interface IParamsProps {
    fuel: string;
    damage: string;
}

//好的编程习惯就是，在 = 后面进行换行
//对象的初始化应该也是一个对象，所以这里用到了花括号
const [params, setParams] = useState<IParamsProps>({
        fuel: '1',
        damage: '2'
    })
```

```typescript
interface IBeesProps {
    id: number;
    speed: number;
    latitude: number;
    longitude: number;
    elevation: number;
    fuel: number;
    damage: number;
    nectar: number;
    honey: number;
    tansformationRate: number;
}
//IBeesProps[]代表着数据类型是，object的一个数组，也就是说数组里面的每一个元素都是IBeesProps类型
const [beesLists, setBeesList] = useState<IBeesProps[]>([]);
```

##### 传参的语法解释

```typescript
const [count, setCount] = useState<number>(0);
```

为何这里要用要用**方括号**括起来呢：这种语法是JS里面的**数组解构** **destructure**

也就是说，**将useState方法的返回值分别赋给count和setCount**

```typescript
const foo = ['one', 'two', 'three'];
const [red, yellow, green] = foo;
```

#### 3.useState的返回值

useState的返回值是**当前的state**和**更新state的函数**，需要去成对地获取他们



### 3.如何去使用它

##### 读取：

如何读取它的值，直接使用{count}就行，注意读取的时候，需要用一个花括号括起来

```typescript
<p>You clicked {count} times</p>
```

##### 修改：

把修改后的值当作参数直接传到setCount函数里面去就行！

```typescript
<button onClick={() => setCount(count + 1)}>    Click me
  </button>
```



4.同时使用读取和修改写出来的例子

```typescript
const Test: FC = (): JSX.Element => {
  // Declare a new state variable, which we'll call "count"
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>   //这里读取了！！！
      <button onClick={() => setCount(count + 1)}>  //这里修改了！！！
        Click me
      </button>
    </div>
  );
}
```



# Effect Hook写法

**Effect Hook是什么**：The *Effect Hook* lets you perform **side effects** in **function components**

相当于class lifecycle methods中的componentDidMount`, `componentDidUpdate`, and `componentWillUnmount

**哪些场合会用**：

Data fetching, setting up a subscription, and manually changing the DOM



**为什么要有Effect Hook**

in many cases we want to perform the **same side effect** regardless of whether the component just **mounted, or if it has been updated.(happen after every render)**

为了避免重复代码，为了复用状态逻辑（reuse stateful logic）



**What does `useEffect` do?** 

**在每个render()之后自动执行**

By using this Hook, you tell React that your component needs to do something **after render**.



**useEffect语法**

**useEffect(function)**

React will call the function you passed later **after every render**

```typescript
function Example() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `You clicked ${count} times`;
  });
}
```















# Ahook

**ahooks是什么**：

基于 React Hooks 的工具库，致力提供常用且高质量的 Hooks。

**目的**：

将与业务无关的逻辑进行抽象，封装一套通用场景的纯逻辑的 Hooks 工具方法



前提：

1.大部分逻辑是重复且可被复用的，如对数据请求的逻辑处理，对防抖节流的逻辑处理等，**同样的代码经常会在同一个或不同的项目中被重复的编写** 

2.Hooks 虽然解决了 Class 组件的 this 、 LifeCycle 等学习成本过高的问题，但是也引入了诸如闭包、依赖地狱、不能在条件语句中使用的约定等等新的问题



Hook优点

可以**在组件之间共享可复用的状态逻辑**，方便了开发者将业务逻辑和 UI 视图进行解耦，从而状态与 UI 的界限会越来越清晰





**Ahook结构**

ahooks 基于 UI、SideEffect、LifeCycle、State、DOM 等分类提供了常用的 Hooks

![image.png](https://ucc.alicdn.com/pic/developer-ecology/4c4ae5ea583742479fe9e3ccb297cf29.png)
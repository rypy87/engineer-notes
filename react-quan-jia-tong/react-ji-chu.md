# React基础

### 简介

React由 Facebook 的软件工程师 Jordan Walke 创建，他发布了一个名为“FaxJS”的 React 早期原型。用来架设 Instagram 的网站。2013 年 5 月在 JSConf US 宣布开放源代码。

#### 基础概念

React是一个声明式，高效且灵活的用于构建 Web应用交互界面的 JavaScript 库。

React采用组将模式构建复杂的UI界面。

React使用 Facebook自主研发的一套语法糖--JSX。

React可用作开发具有 Next.js 等框架的单页、手机或服务器渲染应用程序的基础。

React只专注状态管理和将状态渲染到 DOM，因此创建 React 应用程序通常需要使用额外的工具库来进行路由实现，以及某些客户端功能。

React于 2015 年 2 月发布React Native，支持使用 React 进行原生 Android、iOS 和 UWP 开发。

#### 官网

```
https://zh-hans.reactjs.org/
```

#### 近期版本历史

2022.3.29 18.0.0

2020.10.20 17.0.0

2017.9.26 16.0.0

#### 最新版本

18.2.0

#### 优缺点

**优点**

**1.声明式设计** −React采用声明范式，可以轻松描述应用。

**2.高效** −React通过对DOM的模拟，最大限度地减少与DOM的交互。

**3.灵活** −React可以与已知的库或框架很好地配合，兼容性很好。

**4.JSX** − JSX （Javascript xml）是 JavaScript 语法的扩展。React 专属语法 ，建议使用。

**5.组件** − 通过 React 构建组件，一切皆组件，代码组件化更简单。

**6.单向响应的数据流** − React 实现了单向响应的数据流，有效减少重复率。

**缺点**

React 并不是一个完整的框架，因此不适合做一个完整的项目构建，它只实现了 MVC 模式中的 V(View)层。如果构建大型项目需要一套完整的框架，基本都需要加上 ReactRouter 和 Flux 才能写大型应用。

### 安装

#### CDN方式

```
<script crossorigin src="https://unpkg.com/react@18/umd/react.production.min.js"></script><script crossorigin src="https://unpkg.com/react-dom@18/umd/react-dom.production.min.js"></script>
```

#### 脚手架方式

**react脚手架安装**

```
npm i create-react-app [-g]
```

**创建项目**

```
npx create-react-app 项目名npm init react-app   项目名 
```

选择模板创建

```
--template [template-name]
```

**脚手架目录**

```
-demo    -node_modules           // 依赖包    -public                 // 打包之后public文件夹不会进行压缩        favicon.ico         // 偏爱图标        index.html          // 单页面应用的html文件,主页面        logo192.png         // logo图        logo512.png         // logo图        manifest.json       // 应用加壳的配置文件        robots.txt          // 爬虫协议文件    -src        App.css             // App组件的样式        App.js              // App组件        App.test.js         // App测试文件        index.css           // 入口样式        index.js            // 入口文件        logo.svg            // logo图        reportWebVitals.js  // 页面性能分析文件（需要web-vitals库的支持）        setupTests.js       //  组件单元测试的文件（需要jest-dom库的支持）    .gitgnore               // 忽略文件，不需要上传到git的文件    package-lock.json       // 锁定项目的依赖包及版本号    package.json            // 项目信息    READMO.md               // 说明文件
```

**清空文件**

只留下index.html、App.js和index.js

去掉index.html中的引入

```
    <link rel="manifest" href="%PUBLIC_URL%/manifest.json" />
```

**修改脚手架项目端口号**

**package.json**

```
{  "scripts": {    "start": "set port=5000 && react-scripts start"  }}
```

### JSX语法

#### 注释语法

快捷键 ctrl+/

```
{/* 注释内容 */}
```

#### 输出表达式

**基本语法**

```
{变量/对象属性/函数调用}
```

注：如果复合数据类型，多层级数据会报错，需要结合JSON.stringfy()

**案例**

```
function App() {  let a=30;  const user={username:"admin"};  function f(){  	return '我是函数';}  return (    <div>      {/* 数据绑定 */}        <p>年龄{a}</p>        <p>{f()}</p>        <p>{user.username}</p>        <p>{JSON.stringify(user)}</p>    </div>  );}
```

**标签属性语法**

```
<标签 属性名={变量}></标签>
```

**案例**

```
function App() {  let a=30;  let imgSrc=`https://t7.baidu.com/it/u=1595072465,3644073269&fm=193&f=GIF`;  return (    <div>      {/* 属性绑定 */}      <img src={imgSrc} aa={a}></img>    </div>  );}
```

**三目表达式语法**

```
{三目表达式}
```

**案例**

```
function App() {  let a=30;  return (    <div>      {/* 条件渲染 */}        <p>年龄{a>18?'已成年':'未成年'}</p>    </div>  );}
```

**列表语法**

```
{	可遍历引用.map(()=>{return <标签 key={}>元素</标签>})}
```

**案例**

```
function App() {  const arr=[1,2,34,5,6,7,8];  return (    <div>      <ul>        {              arr.map((item,index)=>{          return <p key={index}>数组元素:{item},{index}</p>        })}      </ul>    </div>  );}
```

**标签的类样式**

```
<标签 className="类名"></标签>
```

**案例**

```
function App() {    function f1(){      let user={username:"admin",pwd:123456}      return Object.values(user);	}  return (    <div>       {f1().map(((item,index)=>{          return <p key={index} className='a'>{item}</p>        }))}    </div>  );}
```

**标签的行内样式**

```
<标签 style={{行内样式}}></标签>
```

**案例**

```
function App() {  return (    <div>   		<p style={{color:"red"}}>我要测试行内样式</p>    </div>  );}
```

#### jsx规则

1、在JSX语法中，当遇到了<>就会按照html语法来解析，当遇到了{}就会按照js语法来解析。

2、return返回值最外层只能有一个根标签。

3、JSX标签可以相互进行嵌套，注意代码的缩进和换行，增强代码的可读性。

4、通过JSX语法将数据渲染到页面中也有虚拟DOM。

**vscode自动jsx补全**

```
点击左下角——>设置——>搜索emmet——>点击在settings.json中编辑——>添加如下代码"emmet.includeLanguages": {    "javascript": "javascriptreact"}
```

### 事件

#### 事件的绑定

**语法**

**箭头函数方式**

```
<button on事件名={()=>this.fn1()}></button>
```

**bind方式**

```
<button on事件名={this.fn1.bind()}></button>
```

**案例**

```
function f(){  console.log("我被点击了");}      {/* 箭头函数方式 */}      <button onClick={()=>f()}>按钮</button>      {/* bind方式 */}      <button onClick={f.bind()}>按钮2</button>
```

#### 事件传参

**语法**

**箭头函数方式**

```
<button on事件名={()=>this.fn1(...参数)}></button>
```

**bind方式**

```
<button on事件名={this.fn1.bind(event,...参数)}></button>
```

**案例**

```
function ff(a){  console.log(a);}      <button onClick={()=>ff('admin')}>按钮3</button>      <button onClick={ff.bind(Event,"adddd")}>按钮4</button>
```

#### 事件对象

**语法**

**箭头函数方式**

```
<button on事件名={(event)=>this.fn1([...参数,]event[,...参数])}></button>
```

**bind方式**

```
<button on事件名={this.fn1.bind(event,...参数)}></button>
```

**案例**

```
function fff(a,event){  console.log(a);  console.log(event);}      <button onClick={()=>fff("aaaaa",Event)}>按钮5</button>      <button onClick={fff.bind(Event,"adddd")}>按钮6</button>
```

#### 事件应用

**阻止默认行为**

```
function ffff(event){  event.preventDefault();  console.log("我被点击");}<div className="dBox" onContextMenu={(event)=>ffff(event)}>我是点击</div>
```

**阻止事件传播**

```
function f1(){  console.log("我被点击1");}function f2(event){  event.stopPropagation();  console.log("我被点击2");}      <div className="dBoxb" onClick={()=>f1()}>        <div className="dBox" onClick={(event)=>f2(event)}></div>      </div>
```

#### 事件捕获

**语法**

```
on事件名称Capture={}
```

**案例**

```
function f1(){  console.log("我被点击1");}function f2(event){  console.log("我被点击2");}      <div className="dBoxb" onClickCapture={()=>f1()}>        <div className="dBox" onClickCapture={()=>f2()}></div>      </div>
```

### 状态机（state）

#### 状态机定义

状态机定义在类中

**构造方法定义**

```
  constructor(){    super()    this.state = {}  }
```

**变量定义**

```
state = {}
```

**案例**

```
import {Component}from "react";class page extends Component{    //state的定义有两种方式    //直接定义    // state={    //     username:"admin",    //     pwd:123456    // }    //在构造函数中定义状态机    constructor(){        super();        this.state={//先声明，在帮给当前类            username:"admin",            user:{u1:"aaa"},            arr:[1,2,4,5,6,8,9]        }    }    render(){        let {username,user,arr}=this.state;        return(            <div>                {this.state.username}                {this.state.pwd}                {                    arr.map(item=>{                        return <p>{item}</p>                    })                }            </div>          )      }}export default page;    
```

#### 状态机使用

**修改状态机语法**

```
setState({}[,()=>{}])
```

参数1，需要修改键名和值

参数2：回调函数，由于setState是异步的，所以参数二相当于then方法。

注意事项

1、如果定义的数据不在state中，则数据发生变化的时候，不会驱动页面重新渲染。

2、只能使用setState()来修改状态机的值。setState是异步的

3、一定不要在render中调用setState()，因为setState()会引起页面的重新渲染，如果在render中调用会陷入死循环。

4、在开发模式下 \<React.StrictMode>会被执行，导致render函数执行两便去掉就好。

5、state中数据支持解构赋值。

6、state中操作数组/对象，需要先取数组/对象，修改数组/对象，再存放回去

**案例**

状态机的定义修改案例

```
import {Component}from "react";class page extends Component{    constructor(){        super();        this.state={//先声明，在帮给当前类            username:"admin"        }    }    changeUserName(){       //this.setState({username:"admin1",pwd:123123});       //this.a=60;    }    a=30;    render(){        let {username,user,arr}=this.state;        return(            <div>                我是子组件                <button onClick={()=>this.changeUserName()}>按钮</button>                {this.state.username}                {this.state.pwd}                <p>{username}</p>            </div>          )      }}export default page;    
```

操作数组

```
import {Component}from "react";class page extends Component{    constructor(){        super();        this.state={            arr:[1,2,4,5,6,8,9]        }    }    changeUserName(){       //this.setState({arr:[1,2,100,5,6,8,9]})       this.state.arr.splice(2,1,100)       this.setState({arr:this.state.arr})    }    render(){        let {arr}=this.state;        return(            <div>                我是组件                <button onClick={()=>this.changeUserName()}>按钮</button>                {                    arr.map(item=>{                        return <p>{item}</p>                    })                }            </div>          )      }}export default page;
```

操作对象

```
import {Component}from "react";class page extends Component{    constructor(){        super();        this.state={            user:{u1:"aaa"}        }    }    changeUserName(){       this.setState({user:{u1:"bbbb"}})    }    render(){        let {user}=this.state;        return(            <div>                我是组件                <button onClick={()=>this.changeUserName()}>按钮</button>                <p>{user.u1}</p>            </div>          )      }}export default page;
```

### form表单

#### 表单控件分类

**受控表单**

通过表单控件的value属性，给表单控件赋予仓库的默认值，这种表单控件称为受控表单控件。

**特点**

就地反馈，如：验证 禁用按钮，如：提交 执行特定的输入格式，如：手机号、身份证号、银行卡号

**非受控表单**

没有通过表单控件的value属性，给表单控件赋予仓库的默认值，这种表单控件称为非受控表单控件。

\####

**案例**

```
    state={        username:"admin"    }    changeText(event){        this.setState({username:"aaaaa"})    }    
```

#### 受控表单和非受控表单对比

#### 综合案例

输入框，密码框，单选框，下拉框，多选框，文本框，是否同意协议。

姓名，密码，性别，职业，爱好，自我介绍，

```
import {Component}from "react";class Page extends Component{    state={        username:"admin"    }    changeText(event){        // this.setState({username:"aaaaa"})        // console.log(event.target.value);        //console.log(event.target.value);        //单选框event.target.checked/event.target.value       // console.log(event.target.value);       //复选框event.target.checked/event.target.value       //下拉框event.target.value       //文本框event.target.value       console.log(event.target.value);    }    render(){        return(            <div>                用户名<input type="text" value={this.state.username} onChange={(event)=>this.changeText(event)}/><br></br>                密&emsp;码<input type="password" onChange={(event)=>this.changeText(event)}/><br></br>                性&emsp;别                <input type="radio" name="sex" id="" onChange={(event)=>this.changeText(event)}/>男                <input type="radio" name="sex" id="" />女<br></br>                爱&emsp;好                <input type="checkbox" name="" id=""  onChange={(event)=>this.changeText(event)}/>读                <input type="checkbox" name="" id="" />写                <input type="checkbox" name="" id="" />背<br></br>                城&emsp;市                <select name="" id="" onChange={(event)=>this.changeText(event)}>                    <option value="0">广东省</option>                    <option value="1">河南省</option>                    <option value="2">湖南省</option>                    <option value="3">湖北省</option>                    <option value="4">台湾省</option>                </select><br></br>                简介                <textarea name="" id="" cols="30" rows="10"  onChange={(event)=>this.changeText(event)}></textarea>                            </div>        )              }}export default Page
```

### 组件

组件分为两种函数组件和类组件。

#### 组件定义

建议将组件定义到components文件夹中。

**函数组件**

**语法**

```
function 函数名(){  return <div>内容</div>}export default 函数名
```

**案例**

```
function child1(){    return <div>        <p>我是函数组件</p>        我是函数组件    </div>    // return (    //     <div>    //     </div>        // )}export default child1;
```

**类组件**

**语法**

```
import React,{Component} from "react"class 类名 extends Component {  render(){    return <div>内容</div>  }}export default 类名
```

**案例**

```
import { Component } from 'react';class Child2 extends Component {    render() {        return <div>            我是类组件            </div>    }}export default Child2;
```

**定义的注意事项**

1、组件名首字母必须大写。 2、组件最外层只能有一个根标签。

#### 组件的使用

```
<组件名></组件名>
```

**使用注意事项**

1、使用之前直接进行引入。 2、组件区分大写，直接使用即可。

**两种组件的区别**

1、子组件接收父组件的传值方式不一样，函数定义使用props接收，类定义使用this.props接收。 2、函数定义没有生命周期，类定义有生命周期。 3、类定义有状态机state，函数定义没有状态机state。

4、在类定义中默认还要初始化一下，而函数定义不需要初始化。就加载速率来说，函数定义的要比类定义快一点。

5、新版本中使用函数速度会快一些，旧版本推荐使用类

#### 组件的通信

**props**

**父子组件传值**

**父组件**

**语法**

```
<组件名 键名={键值} ></组件名>
```

**子组件**

**语法**

```
this.props
```

**案例**

**父组件**

```
import {Component}from "react";import Child from "./Child";class Page extends Component{    username="admin";    pwd=123123;    state={        u1:"admin"    }    render(){        return <div>            <Child username={this.username} pwd={this.pwd} ss={this.state}></Child>        </div>    }}export default Page;
```

**子组件**

```
import {Component} from "react";class Child extends Component{    render(){        console.log(this.props);        return <div>            我是子组件            {this.props.username}           {JSON.stringify(this.props)}        </div>    }}   export default Child
```

**批量传值（父子孙传值）**

**父组件**

**语法**

```
<组件名 键名={键值} ></组件名>
```

**子组件**

**语法**

```
<子组件子组件 {...this.props}></子组件子组件>
```

**孙子组件**

**语法**

```
this.props
```

**案例**

**父组件**

```
import {Component}from "react";import Child from "./Child";class Page extends Component{    username="admin";    pwd=123123;    state={        u1:"admin"    }    render(){        return <div>            <Child username={this.username} pwd={this.pwd} ss={this.state}></Child>        </div>    }}export default Page;
```

**子组件**

```
import {Component} from "react";import Childchild from "./Childchild";class Child extends Component{    render(){        // console.log(this.props);        return <div>            我是子组件            {/* {this.props.username}           {JSON.stringify(this.props)} */}           <Childchild {...this.props}></Childchild>        </div>    }}   export default Child
```

**子子组件**

```
import {Component} from "react";class Childchild extends Component{    render(){        return <div>            我是子组件的子组件            {JSON.stringify(this.props)}        </div>    }}export default Childchild
```

**组件的虚拟DOM**

**语法**

**父组件**

```
<组件名><标签>内容</标签></组件名>
```

**子组件**

```
this.props.children
```

可以获取父组件，通过子组件的标签节点获取子组件标签节点下的内容，并将其转换数组。

**案例**

**父组件**

```
import {Component}from "react";import Child from "./Child";class Page extends Component{    render(){        return <div>            <Child>                <b>我是憨憨</b>                <b>我是喜喜</b>            </Child>        </div>    }}export default Page;
```

**子组件**

```
import {Component} from "react";class Child extends Component{    render(){       console.log(this.props);        return <div>            我是子组件           {this.props.children[0]}        </div>    }}   export default Child
```

**子父组件传值**

注：采用传递修改方法的方式进行修改传递。

**父组件**

```
<组件名 方法名={(event)=>this.父组件的方法(event)}></组件名>
```

**子组件**

```
this.props.方法名
```

**案例**

**父组件**

```
import {Component}from "react";import Child from "./Child";import "./index.css";class Page extends Component{    state={        username:"admin"    }    chageUsername(aa){        this.setState({username:aa});    }    render(){        return <div className="divp">            我是父组件            <p>{this.state.username}</p>            <Child changU={(ee)=>this.chageUsername(ee)}></Child>            </div>    }}export default Page;
```

子组件

```
import {Component} from "react";import "./index.css";class Child extends Component{    render(){        return <div className="divc">            我是子组件          <button onClick={()=>this.props.changU("憨憨")}>按钮</button>           </div>    }}   export default Child
```

**构造方法中的props使用**

在构造方法中使用props，需要先将props传递给component父类构造方法，才能在子类中继承使用。

**语法**

```
constructor(props){    super(props)    console.log(this.props);}
```

**props和state区别**

state状态机，存放当前组件数据，需要通过setState()进行修改。

props是用来传值的，props的数据在子组件中是只读的，如果需要传值可以使用调用修改函数方式传值。

### 组件

#### 组件生命周期

**完整版**

![react完整版生命周期](file:///E:/%E6%8E%88%E8%AF%BE%E5%86%85%E5%AE%B9/%E4%B8%AD%E5%85%AC/VUE%E8%AF%BE%E7%A8%8B/%E7%AC%94%E8%AE%B0/2022%E5%B9%BF%E5%B7%9EWeb%E5%85%A8%E6%A0%88%E9%9D%A2%E6%8E%88%E5%B0%B1%E4%B8%9A%E7%8F%AD10%E7%8F%AD/img/react%E5%AE%8C%E6%95%B4%E7%89%88%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F.png?lastModify=1664353384)

**Mounting(挂载)**

constructor() 组件构造函数，初始化数据

getDerivedStateFromProps() 在渲染之前，修改state中的数据。 ①、一定要在前面加上static，声明为静态的，不然会被react忽略同时还报错 ②、一定要保证在constructor中定义了state ③、一定要加上return，如果return空对象则表示什么都不修改，如果return键值对则会修改成当前这个键值对的样子

render() 渲染DOM的方法，加载并渲染所有的DOM元素 componentDidMount() 组件挂载完毕调用，一般情况下在这里开启定时器、开启倒计时、做数据交互

**Updating(更新)**

getDerivedStateFromProps() 在挂载完成后，再次渲染前再次被调用， 根据 shouldComponentUpdate() 的返回值，判断 React 组件的输出是否受当前 state 或 props 更改的影响。可以影响的常见方法包括New props、setState()、forceUpdate()。 shouldComponentUpdate(nextProps,nextState) ，当 props 或 state 发生变化时，会被调用，其主要功能判断要不要更新，可以控制值变换而决定是否更新。 1、return true 要更新，就会走render进行局部更新 2、return false 不要更新，就不会走render也不会进行局部更新

render() 重新渲染DOM元素

getSnapshotBeforeUpdate() ，在最近一次渲染输出（提交到 DOM 节点）之前调用。

componentDidUpdate() ，在更新完毕后调用

**Unmounting(卸载)**

componentWillUnmount(): 在组件卸载及销毁之前直接调用。一般情况下在这里关闭定时器、关闭倒计时

**常用版**

![react常用生命周期](file:///E:/%E6%8E%88%E8%AF%BE%E5%86%85%E5%AE%B9/%E4%B8%AD%E5%85%AC/VUE%E8%AF%BE%E7%A8%8B/%E7%AC%94%E8%AE%B0/2022%E5%B9%BF%E5%B7%9EWeb%E5%85%A8%E6%A0%88%E9%9D%A2%E6%8E%88%E5%B0%B1%E4%B8%9A%E7%8F%AD10%E7%8F%AD/img/react%E5%B8%B8%E7%94%A8%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F.png?lastModify=1664353384)

**父子组件的生命周期执行顺序**

单组件执行顺序

**没有更新正常版执行顺序**

我是构造=>我是渲染=>我是挂载完成=>我是卸载前

**更新正常版执行顺序**

我是构造=>我是渲染=>我是挂载完成=>我是渲染=>我是更新完成=>我是卸载前

**没有更新完整版执行顺序**

我是构造=>我是被调用getDerivedStateFromProps=>我是渲染=>我是挂载完成=>我是卸载前

**更新正常版执行顺序**

**当判断更新方法返回false的时候**

我是构造=>我是被调用getDerivedStateFromProps=>我是渲染=>我是挂载完成=>我是被调用getDerivedStateFromProps=>我是判断你要不要更新=>我是卸载前

**当判断更新方法返回true的时候**

我是构造=>我是被调用getDerivedStateFromProps=>我是渲染=>我是挂载完成=>我是被调用getDerivedStateFromProps=>我是判断你要不要更新=>我是渲染=>最后一次更新结果=>我是更新完成=>我是卸载前

父子组件执行顺序

我是构造=>我是被调用=>我是渲染=>我是构造儿=>我是被调用儿=>我是挂载完成儿=>我是挂载完成=>我是被调用getDerivedStateFromProps=>我是判断你要不要更新=>我是渲染=>我是被调用儿getDerivedStateFromProps=>我是判断你要不要更新儿=>最后一次更新结果儿=>最后一次更新结果=>我是更新完成儿/我是卸载前儿=>我是更新完成

**案例**

父组件

```
import  { Component } from 'react'import Child from "./Child";export default class Page extends Component {  constructor(){    super()    this.state={      username:"admin",      flag:true    }    console.log("我是构造");  }  static getDerivedStateFromProps(a,newState){    console.log(a);    console.log(newState);//是最新的state值    console.log("我是被调用");      //return {username:"addffsddf"};    return null;  }  shouldComponentUpdate(c,newValue){    console.log(c);    console.log(newValue);//是最新的state值    console.log("我是判断你要不要更新");    return true;  }getSnapshotBeforeUpdate(){  console.log("最后一次更新结果");  return null;}  componentDidMount(){    console.log("我是挂载完成");  }  componentDidUpdate(){    console.log("我是更新完成");  }  componentWillUnmount(){    console.log("我是卸载前");  }    changeUsername(){    this.setState({      flag:false    })  }  render() {    console.log("我是渲染");    console.log(this.state);    return (      <div>        <button onClick={()=>this.changeUsername()}>按钮</button>        用户名:{this.state.username}        {this.state.flag?<Child username={this.state.username}></Child>:null}        </div>    )  }}
```

子组件

```
import React, { Component } from 'react'export default class Child extends Component {    constructor(){        super()        console.log("我是构造儿");        this.state={                    }      }      static getDerivedStateFromProps(newProps,newState){        console.log(newProps);//是最新的Props值        // console.log(newState);//是最新的state值        console.log("我是被调用儿");          return {username:"addffsddf"};//return null;      }      shouldComponentUpdate(newProps,newValue){        console.log(newProps);//是最新的Props值        // console.log(newValue);//是最新的state值        console.log("我是判断你要不要更新儿");        return true;      }    getSnapshotBeforeUpdate(){      console.log("最后一次更新结果儿");      return null;    }          componentDidMount(){        console.log("我是挂载完成儿");      }      componentDidUpdate(){        console.log("我是更新完成儿");      }      componentWillUnmount(){        console.log("我是卸载前儿");      }  render() {    let {username}=this.props;    return (      <div>        Child        {username}        </div>    )  }}
```

#### 组件优化

**空标签组件（Fragment）**

使用场景：假设在父组件中的ul标签中使用子组件，那么现在的嵌套是ul套div套li，这是一个不合理的嵌套。我们希望ul标签内直接套li标签；我们可以将子组件最外层的div删掉，只写一个空标签来解决，但是官方不建议这样，官方给我们提供了fragment组件来解决，fragment组件就是一个空标签。

**案例**

**父组件**

```
import  { Component } from 'react'import Child from './Child';export default class Page extends Component {  render() {    return (      <div>        <ul>            <Child></Child>        </ul>      </div>    )  }}
```

**子组件**

```
import { Component, Fragment } from 'react'export default class Child extends Component {    constructor(){        super();        this.state={            arr:["外卖","电影","音乐"]        }    }  render() {    let {arr}=this.state;    return (      <Fragment>        {            arr.map((item,index)=><li key={index}>{item}</li>)        }      </Fragment>    )  }}
```

**组件销毁优化（componentWillUnmount）**

使用场景：子组件中有一个定时器，在子组件销毁的时候，定时器会一直存储在内存中，我们希望在子组件将要销毁的时候定时也也需要清空。

**案例**

**子组件**

```
import { Component } from 'react'export default class Child extends Component {  constructor(){    super();    this.state={        time:new Date().toLocaleString()    }  }componentDidMount(){    this.dingshiqi=setInterval(()=>{        this.setState({time:            new Date().toLocaleString()        })    },1000);    console.log(this);}  componentWillUnmount(){    clearInterval(this.dingshiqi);    console.log("我销毁");    console.log(this);  }    render() {     let {time}=this.state;    return (      <div>        <div>time:{time}</div>      </div>    )  }}
```

**父组件**

```
import  { Component } from 'react'import Child from './Child';export default class Page extends Component {    constructor(){        super();        this.state={            flag:true        }    }    chageFlag(){        this.setState({flag:false})    }  render() {    let {flag}=this.state;    return (      <div>        Page        <button onClick={()=>{this.chageFlag()}}>按钮</button>        {flag?<Child></Child>:null}    </div>    )  }}
```

**更新判定优化（shouldComponentUpdate）**

使用场景：假设父组件有很多很多数据，子组件只依赖部分数据，现在效果就是只要其父组件中的任何一个数据发生变化了都会引起子组件的重新渲染。我们希望只有当子组件依赖的数据发生变化了才会引起子组件的重新渲染。

**案例**

**父组件**

```
import { Component } from 'react'import Child from './Child';export default class Page extends Component {    constructor(){        super();        this.state={            username:"admin"        }    }    changeUsername(){        this.setState({username:"aaaaa"});    }  render() {    let {username}=this.state;    return (      <div>        Page        <button onClick={()=>this.changeUsername()}>按钮</button>        <p>{username}</p>            <Child username={username}></Child>        </div>    )  }}
```

**子组件**

```
import { Component } from 'react'export default class Child extends Component {    shouldComponentUpdate(newProps,newState){        console.log(newProps);        return false;    }  render() {    let {username}=this.props;    return (      <div>        Child        {username}    </div>    )  }}
```

**纯组件（pureComponent）**

使用场景：假设父组件有很多很多数据，子组件只依赖了其中的一个，现在效果就是只要其父组件中的任何一个数据发生变化了都会引起子组件的重新渲染。我们希望只有当子组件依赖的数据发生变化了才会引起子组件的重新渲染。

注：以浅层对比 prop 和 state 的方式来实现了shouldComponentUpdate()函数，主要针对类组件

**案例**

**父组件**

```
import  { Component } from 'react'import Child from './Child';export default class Page extends Component {    constructor(){        super();        this.state={            username:"admin",            pwd:123456        }    }    changPwd(){        this.setState({pwd:"123123"});    }    changUsername(){        this.setState({username:"aaaaaaa"});    }  render() {    let {username,pwd}=this.state;    return (      <div>        Page        <button onClick={()=>this.changPwd()}>按钮</button>        <button onClick={()=>this.changUsername()}>按钮2</button>        <p>{username},{pwd}</p>        <Child username={username}></Child>        </div>    )  }}
```

**子组件**

```
import React, { PureComponent } from 'react'export default class Child extends PureComponent {  render() {    let {username}=this.props;    console.log("我是子组件");    return (      <div>        Child        <p>{username}</p>      </div>    )  }}
```

**React.Memo方法**

使用场景：假设父组件有很多很多数据，子组件只依赖了其中的一个，现在效果就是只要其父组件中的任何一个数据发生变化了都会引起子组件的重新渲染。我们希望只有当子组件依赖的数据发生变化了才会引起子组件的重新渲染。

注：以浅层对比 prop 和 state 的方式来实现了shouldComponentUpdate()函数，主要针对函数组件

**案例**

**父组件**

```
import  { Component } from 'react'import Child from './Child';export default class Page extends Component {    constructor(){        super();        this.state={            username:"admin",            pwd:123456        }    }    changPwd(){        this.setState({pwd:"123123"});    }    changUsername(){        this.setState({username:"aaaaaaa"});    }  render() {    let {username,pwd}=this.state;    return (      <div>        Page        <button onClick={()=>this.changPwd()}>按钮</button>        <button onClick={()=>this.changUsername()}>按钮2</button>        <p>{username},{pwd}</p>        <Child username={username}></Child>        </div>    )  }}
```

**子组件**

```
import React from 'react'function Child(props) {  let {username}=props;    console.log("我是子组件");    return (      <div>        Child        <p>{username}</p>      </div>    )}export default React.memo(Child);
```

**语境方法context**

使用场景：假设父组件有一些数据，子组件不需要使用，但是子子组件需要使用，我们传统的方式是父组件传给子组件，子组件再传给子子组件，如果组件嵌套比较多的话就不太合理了。我们可以借助React.context()来解决。

**案例**

**父组件**

```
import { Component,createContext } from 'react'import Child from './Child';export const {Provider,Consumer} =createContext();//Provider 传递数据//Consumer 接收数据export default class Page extends Component {    constructor(){        super();        this.state={            username:"admin"        }    }  render() {    let {username}=this.state    return (      <div>        Page        {username}        <Provider value={{username:username}}>           <Child></Child>         </Provider>      </div>    )  }}
```

子组件

```
import React, { Component } from 'react'import ChildChild from './ChildChild'export default class Child extends Component {  render() {    return (      <div>        Child        <ChildChild></ChildChild>        </div>    )  }}
```

子子组件

```
import React, { Component } from 'react'import {Consumer} from "./Page";export default class ChildChild extends Component {  render() {    return (      <div>        ChildChild        <Consumer>            {(e)=>{                let {username}=e;                   return <div>                    <p>{JSON.stringify(e)}</p>                    <p>{username}</p>                </div>            }}        </Consumer>        </div>    )  }}
```

#### 错误边界处理函数（componentDidCatch）

使用场景：假设父组件内有很多页面，但是其中一个子组件的错误会引起整套页面的崩塌，我们希望当子组件出现错误的时候仅仅是子组件自己不渲染不会影响到其他页面的内容。

componentDidCatch函数，当页面发生错误的时候被触发。

**案例**

父组件

```
import React, { Component } from 'react'import Child from './Child'export default class Page extends Component {    constructor(){        super();        this.state={            flag:true        }    }    componentDidCatch(){        console.log("我打印不？");        this.setState({flag:false});    }  render() {    let {flag}=this.state;    return (      <div>        {flag?<Child></Child>:null}      </div>    )  }}
```

**子组件**

```
import React, { Component } from 'react'export default class Child extends Component {  render() {    // console.log(a);    // let a=30;    return (      <div>        Child    </div>    )  }}
```

#### 高阶组件

HOC(Higher­order component)是一种React 的进阶使用方法，主要还是为了便于组件的复用，并非官方方法。HOC本身并不是 React API, 它就是一个方法，一个接收一个组件作为参数，返回一个增强的组件的方法。

注：高阶组件有且只有一个参数。

**案例**

```
import  { Component } from 'react'import Child1 from './Child1';import Child2 from './Child2';import f from "./index";  let C1=f(Child1);  let C2=f(Child2);  export default class Page extends Component {    render() {      return (        <div>         <C1></C1>         <C2></C2>      </div>              )    }  }
```

**高阶组件的模块化**

**index.js**

```
import { Component } from 'react'export default function f(C){    return class H extends Component{      constructor(){        super();        this.state={          str:`我是一个子组件`        }      }        render(){          return (<div>            <C str={this.state.str}></C>          </div>)        }      }    }
```

### 过渡动画

#### 下载

```
npm i react-transition-group
```

#### 引入

```
import {CSSTransition,TransitionGroup} from "react-transition-group"
```

#### 使用

**关键配置项**

```
unmountOnExit	必填，退出时实现卸载该组件in				必填，该元素受哪个状态所影响timeout			必填，过渡动画的持续时间classNames		必填，指过渡动画的类名（两组四个）onEnter			元素进入前的回调函数onEntering		元素进入中的回调函数onEntered		元素进入后的回调函数onExit			元素离开前的回调函数onExiting		元素离开中的回调函数onExited		元素离开后的回调函数
```

**案例**

**样式文件**

```
/* 进入 */.fade-enter{  opacity: 0;}.fade-enter-active{  opacity: 1;  transition: all 1s;}/* 离开 */.fade-exit{  opacity: 1;}.fade-exit-active{  opacity: 0;  transition: all 1s;}
```

**jsx文件**

**单元素过渡动画**

```
        <button onClick={()=>this.setState({flag:!flag})}>{msg}</button>        <CSSTransition unmountOnExit in={flag} timeout={500} classNames="fade" onEntered={()=>this.setState({msg:"隐藏"})} onExited={()=>this.setState({msg:"显示"})}>            <div className='boxDiv'></div>        </CSSTransition>
```

**列表过渡动画**

```
<ul>        <TransitionGroup>        {                arr.map((item,index)=>{                    return <CSSTransition unmountOnExit in={flag} timeout={1000} classNames="fade" key={index}>                        <li>                            <p>{item}</p>                            <button onClick={()=>this.delArr(index)}>删除</button>                        </li>                    </CSSTransition>                })            }        </TransitionGroup>            </ul>   
```

### 路由

#### 下载

```
npm i react-router-dom@latest
```

最新版本 6.4.0 2022.04

#### 路由模式

**注**：在react中使用路由的时候，一定要先设置路由模式，不然路由是无效的。

**引入**

index.js

```
import {BrowserRouter,HashRouter} from "react-router-dom"
```

BrowserRouter 不带#，相当于vue-router中的history路由模式 HashRouter 带#，相当于vue-router中的hash路由模式

**绑定使用使用**

index.js

```
root.render(  <BrowserRouter>    <App />  </BrowserRouter>);
```

#### 路由出口

**app.js**

```
import {Routes} from "react-router-dom"function App() {  return (    <div>      <Routes></Routes>    </div>  );}
```

#### 路由规则定义

**语法**

```
<Routes><Route path="/路由" element={<组件></组件>}></Route></Routes>
```

app.js

```
import {Routes,Route} from "react-router-dom";import Page from "./components/01_react生命周期/Page";function App() {  return (    <div>      <Routes>        {/* 路由规则 */}		<Route path="/index" element={<Index></Index>}></Route>      </Routes>    </div>  );}
```

#### 路由重定向

**语法**

```
import {Routes,Route,Navigate} from "react-router-dom"<Routes>	<Route path="*" element={<Navigate to="/路由"></Navigate>}></Route></Routes>
```

**应用**

**资源不存在(404)处理**

```
import {Routes,Route,Navigate} from "react-router-dom"<Routes> 	<Route path="/not" element={<Not></Not>}></Route>	<Route path="*" element={<Navigate to="/not"></Navigate>}></Route></Routes>
```

#### 路由嵌套

**语法**

**一级路由**

```
<Routes>	<Route path="/路由/*" element={<Index></Index>}></Route></Routes>
```

**二级路由**

```
 <Routes>        <Route path="home" element={<Home></Home>}></Route></Routes>        
```

**使用**

**app.jsx**

```
<Routes>	<Route path="/index/*" element={<Index></Index>}></Route></Routes>
```

**index.jsx**

```
import {Routes,Route,Navigate} from "react-router-dom"    <div>      <Routes>          <Routes>              <Route path='c1' element={<Child></Child>}></Route>              <Route path='c2' element={<Child1></Child1>}></Route>          </Routes>    </div>
```

#### 路由导航

**导航组件**

**语法**

**Link组件**

```
import {Link,NavLink} from "react-router-dom"<div>    <Link to="/路由">文字</Link>    <NavLink to="/路由" className={({isActive})=>isActive?'样式':undefined}>文字</NavLink></div>
```

**NavLink组件**

```
import {Link,NavLink} from "react-router-dom"<div>    <NavLink to="/路由" className={({isActive})=>isActive?'样式':undefined}>文字</NavLink>    <NavLink to="/路由" style={({isActive})=>isActive?{background:"orange"}:undefined}>文字</NavLink></div>
```

**注：**Link组件没有提供className和style，如果想要实现激活高亮的话就需要使用NavLink组件，NavLink组件默认会调用active样式

**案例**

**样式**

```
.footBox{  width: 100vw;  position: fixed;  left: 0;  bottom: 0;  display: flex;}.footBox .aaa{  color: white;  background-color: orange;}
```

**index.js**

```
import React, { Component } from 'react'import { Route, Routes, Link,NavLink} from 'react-router-dom'import Home from "./Home";import Fima from "./Fima";import Mine from "./Mine";import Msg from "./Msg";import "./index.css";export default class index extends Component {    render() {        return (<div>            <p><Link to="/index/home">首页</Link></p>            <p><NavLink to="/index/fima" style={({isActive})=>isActive?{background:"green"}:null}>理财</NavLink></p>            <p><NavLink to="/index/msg" className={({isActive})=>isActive?'aaa':null}>消息</NavLink></p>            <p><NavLink to="/index/mine">我的</NavLink></p>            <Routes>                <Route path='home' element={<Home></Home>}></Route>                <Route path='fima' element={<Fima></Fima>}></Route>                <Route path='mine' element={<Mine></Mine>}></Route>                <Route path='msg' element={<Msg></Msg>}></Route>            </Routes>        </div>        )    }}
```

**编程式导航**

**语法**

```
import {useNavigate} from "react-router-dom"const Navigate = useNavigate()Navigate("/路由");//追加一条新的历史记录Navigate("/路由",{replace:true})// 用新的历史记录替换掉当前历史记录Navigate(num),根据正负数，回退/前进指定历史记录
```

**案例**

```
import React from 'react';import {useNavigate} from "react-router-dom";export default function Home() {    let Navigate=useNavigate();  return (    <div>home        <button onClick={()=>Navigate(-2)}>按钮</button>    </div>  )}
```

#### 路由参数

**search传参**

**语法**

**传递**

```
<Link key={item.id} to={"/路由?键名=键值&&键名=键值}>
```

**接收**

**方式一**

```
import {useLocation} from "react-router-dom"const {search} = useLocation()
```

**方式二**

```
import {useSearchParams} from "react-router-dom"const [searchParams,setSearchParams] = useSearchParams()
```

**案例**

```
import React from 'react'import { useLocation }from "react-router-dom";export default function Child() { let {search}=useLocation();console.log(new URLSearchParams(search).get("username"));  return (    <div>Child</div>  )}
```

**案例2**

```
import React from 'react'import {useSearchParams} from "react-router-dom";export default function Child() {  let [searchParams,setSearchParams]=useSearchParams();  console.log(searchParams.get("username"));  return (    <div>Child</div>  )}
```

**state传参**

**语法**

**传递**

```
<Link key={item.id} to="/路由" state={{键名:键值}}>
```

**接收**

```
import {useLocation} from 'react-router-dom'const {state} = useLocation()console.log(state);
```

**案例**

```
import React from 'react'import { useLocation }from "react-router-dom";export default function Child() {  let {state}=useLocation();  console.log(state.usera);  return (    <div>Child</div>  )}
```

**动态路由传参**

**语法**

**路由规则**

```
<Route path="/路由/:变量名" element={<PlayingDetail></PlayingDetail>}></Route>
```

**传递**

```
<Link to={"/路由/"+值>
```

**接收**

```
import React from 'react'import { useParams }from "react-router-dom";export default function Child() {  let param=useParams();  console.log(param);  return (    <div>Child</div>  )}
```

#### 路由懒加载

**语法**

**引入 方式懒加载**

```
const 变量 = React.lazy(()=>import("引入路径"))
```

**React.Suspense方式**

此方式需要将路由出口进行包裹

```
<React.Suspense fallback={<div>正在加载中。。。</div>}>	<Routes>		所有路由规则	</Routes></React.Suspense>
```

### 过滤器

#### 创建过滤器

**filterPrice.js**

```
export default function 函数名(){  	过滤器语法  return ;}
```

#### 使用过滤器

```
<p>价格：{过滤器函数名(传递值)}</p>
```

**案例**

1、创建过滤器并导出

```
export default function dateFilter(date){    return new Date(date).toLocaleString().replaceAll("/","-");}
```

2、在需要使用的组件中

```
import dateFilter from "./filter";<p>当前时间：{dateFilter(dateTime)}</p>
```

### react公共组件的使用

**back.jsx**

```
import React from 'react'import {useNavigate}from "react-router-dom";export default function back() {  let Navigate=useNavigate();  return (    <div>      <button onClick={()=>Navigate(-1)}>返回</button>    </div>  )}
```

**组件**

```
import React, { Component } from 'react'import { Route,Routes } from 'react-router-dom';import Back  from "./Back";import ChildA from "./ChildA";import ChildB from "./ChildB";import ChildC from './ChildC';export default class Page extends Component {  state={    flag:false  }  changFlag(){    this.setState({flag:true})  }  render() {    let {flag}=this.state;    return (      <div>        {flag?<Back></Back>:null}        <Routes>        <Route path="a" element={<ChildA></ChildA>}></Route>        <Route path="b" element={<ChildB changeFlag={()=>this.changFlag()}></ChildB>}></Route>        <Route path="c" element={<ChildC changeFlag={()=>this.changFlag()}></ChildC>}></Route>        </Routes>        </div>    )  }}
```

### React UI库

#### antd

antd 是基于 Ant Design 设计体系的 React UI 组件库。

**特点**

* 🌈 提炼自企业级中后台产品的交互语言和视觉风格。
* 📦 开箱即用的高质量 React 组件。
* 🛡 使用 TypeScript 开发，提供完整的类型定义文件。
* ⚙️ 全链路开发和设计工具体系。
* 🌍 数十个国际化语言支持。
* 🎨 深入每个细节的主题定制能力。

**官方**

```
https://ant.design/index-cn
```

**下载**

**cdn方式**

```
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/antd/4.22.1/antd.css" /><script src="https://cdnjs.cloudflare.com/ajax/libs/antd/4.22.1/antd.js"></script>
```

**npm方式**

```
npm i antd
```

**引入方式**

**全局引入**

**index.js**

```
import "antd/dist/antd.css"
```

**组件使用**

```
import React, { Component } from 'react'import {Button} from "antd";import {CaretRightOutlined,AliwangwangOutlined} from "@ant-design/icons"; export default class Page extends Component {  render() {    return (      <div>        <Button type="primary" >按钮</Button>        <Button type="danger" >按钮</Button>        <Button type="danger"  ghost>按钮</Button>        <Button>按钮</Button>        <CaretRightOutlined style={{color:"blue"}} />        <AliwangwangOutlined style={{color:"pink"}}/>        <p>Page</p>        </div>    )  }}
```

**按需引入**

**组件内**

```
import React, { Component } from 'react'import {Button} from "antd";import {CaretRightOutlined,AliwangwangOutlined} from "@ant-design/icons"; import "antd/es/button/style/index.css"export default class Page extends Component {  render() {    return (      <div>        <Button type="primary" >按钮</Button>        <Button type="danger" >按钮</Button>        <Button type="danger"  ghost>按钮</Button>        <Button>按钮</Button>        <CaretRightOutlined style={{color:"blue"}} />        <AliwangwangOutlined style={{color:"pink"}}/>        <p>Page</p>        </div>    )  }}
```

**babel-plugin-import插件方式引入（推荐）**

**下载**

```
npm i babel-plugin-import
```

**使用**

1、在 src 下创建.babelrc文件，内容如下：

```
{ "presets": [ "react-app" ], "plugins": [ 	["import", { "libraryName": "antd", "style": "css" }]  ] }
```

2、通过命令暴露 webpack.config.js配置文件

```
npm run eject   y				// 可能会报错，因为本地仓库的代码和你现在的代码不是同一个版本git add .						// 将当前文件夹所有文件更新到本地仓库git commit -m "123"				// 给本地仓库的文件添加描述信息npm run eject	y
```

3、修改config/webpack.config.js

```
修改babelrc:true
```

4、修改 package.json

```
删除"babel": {"presets": ["react-app"]}
```

5、重启项目

```
npm start
```

6、使用即可

```
import React, { Component } from 'react'import {Button} from "antd";import {CaretRightOutlined,AliwangwangOutlined} from "@ant-design/icons"; export default class Page extends Component {  render() {    return (      <div>        <Button type="primary" >按钮</Button>        <Button type="danger" >按钮</Button>        <Button type="danger"  ghost>按钮</Button>        <Button>按钮</Button>        <CaretRightOutlined style={{color:"blue"}} />        <AliwangwangOutlined style={{color:"pink"}}/>        <p>Page</p>        </div>    )  }}
```

### 数据交互

#### 配置代理

**方式一**

**配置package.json代理**

1、package.json添加键值对

```
 "proxy": "http://localhost:3000"
```

2、重启项目

```
npm start
```

3、使用

```
import axios from "axios";let { data } = await axios.get("/api/getbanner")
```

**方式二**

**插件库方式**

1、安装依赖

```
npm i http-proxy-middleware
```

2、创建setupProxy.js文件

在src下创建【setupProxy.js】文件，内容如下：

```
const proxy = require("http-proxy-middleware")module.exports = (app)=>{  app.use("/api",proxy.createProxyMiddleware({    target:"http://localhost:3000",    changeOrigin:true,    pathRewrite:{      "^/api":"http://localhost:3000"    }  }))}
```

3、使用

```
let {data}=await axios.get("/aaa/api/getbanner");// 注意：如果使用这种方式配置代理的话，在开发环境下请求地址前面需要加上/aaa，生产环境就不需要加/aaa了.
```

#### axios使用

**get方式**

```
let {data}=await axios.get("/aaa/api/getbanner");
```

**post方式**

```
let {data:dd}=await axios.post("/aaa/api/login",{phone:"12312311231",password:123123});
```

**封装的使用**

http.js

```
import axios from "axios";export let baseURL="";if(process.env.NODE_ENV==="development"){    baseURL="http://localhost:3000";}//请求拦截器axios.interceptors.request.use(req=>req);//响应拦截器axios.interceptors.response.use(res=>res);export const getDatabyAxios=(url,{params,data},method="get")=>axios({    url,    method,    params,    data,    timeout:3000,    headers:{    }});
```

api.js

```
import {getDatabyAxios} from "./http";export const getBanner=()=>getDatabyAxios("/aaa/api/getbanner",{params:undefined});
```

## React基础

### 简介

React由 Facebook 的软件工程师 Jordan Walke 创建，他发布了一个名为“FaxJS”的 React 早期原型。用来架设 Instagram 的网站。2013 年 5 月在 JSConf US 宣布开放源代码。

#### 基础概念

React是一个声明式，高效且灵活的用于构建 Web应用交互界面的 JavaScript 库。

React采用组将模式构建复杂的UI界面。

React使用 Facebook自主研发的一套语法糖--JSX。

React可用作开发具有 Next.js 等框架的单页、手机或服务器渲染应用程序的基础。

React只专注状态管理和将状态渲染到 DOM，因此创建 React 应用程序通常需要使用额外的工具库来进行路由实现，以及某些客户端功能。

React于 2015 年 2 月发布React Native，支持使用 React 进行原生 Android、iOS 和 UWP 开发。

#### 官网

```
https://zh-hans.reactjs.org/
```

#### 近期版本历史

2022.3.29 18.0.0

2020.10.20 17.0.0

2017.9.26 16.0.0

#### 最新版本

18.2.0

#### 优缺点

**优点**

**1.声明式设计** −React采用声明范式，可以轻松描述应用。

**2.高效** −React通过对DOM的模拟，最大限度地减少与DOM的交互。

**3.灵活** −React可以与已知的库或框架很好地配合，兼容性很好。

**4.JSX** − JSX （Javascript xml）是 JavaScript 语法的扩展。React 专属语法 ，建议使用。

**5.组件** − 通过 React 构建组件，一切皆组件，代码组件化更简单。

**6.单向响应的数据流** − React 实现了单向响应的数据流，有效减少重复率。

**缺点**

React 并不是一个完整的框架，因此不适合做一个完整的项目构建，它只实现了 MVC 模式中的 V(View)层。如果构建大型项目需要一套完整的框架，基本都需要加上 ReactRouter 和 Flux 才能写大型应用。

### 安装

#### CDN方式

```
<script crossorigin src="https://unpkg.com/react@18/umd/react.production.min.js"></script><script crossorigin src="https://unpkg.com/react-dom@18/umd/react-dom.production.min.js"></script>
```

#### 脚手架方式

**react脚手架安装**

```
npm i create-react-app [-g]
```

**创建项目**

```
npx create-react-app 项目名npm init react-app   项目名 
```

选择模板创建

```
--template [template-name]
```

**脚手架目录**

```
-demo    -node_modules           // 依赖包    -public                 // 打包之后public文件夹不会进行压缩        favicon.ico         // 偏爱图标        index.html          // 单页面应用的html文件,主页面        logo192.png         // logo图        logo512.png         // logo图        manifest.json       // 应用加壳的配置文件        robots.txt          // 爬虫协议文件    -src        App.css             // App组件的样式        App.js              // App组件        App.test.js         // App测试文件        index.css           // 入口样式        index.js            // 入口文件        logo.svg            // logo图        reportWebVitals.js  // 页面性能分析文件（需要web-vitals库的支持）        setupTests.js       //  组件单元测试的文件（需要jest-dom库的支持）    .gitgnore               // 忽略文件，不需要上传到git的文件    package-lock.json       // 锁定项目的依赖包及版本号    package.json            // 项目信息    READMO.md               // 说明文件
```

**清空文件**

只留下index.html、App.js和index.js

去掉index.html中的引入

```
    <link rel="manifest" href="%PUBLIC_URL%/manifest.json" />
```

**修改脚手架项目端口号**

**package.json**

```
{  "scripts": {    "start": "set port=5000 && react-scripts start"  }}
```

### JSX语法

#### 注释语法

快捷键 ctrl+/

```
{/* 注释内容 */}
```

#### 输出表达式

**基本语法**

```
{变量/对象属性/函数调用}
```

注：如果复合数据类型，多层级数据会报错，需要结合JSON.stringfy()

**案例**

```
function App() {  let a=30;  const user={username:"admin"};  function f(){  	return '我是函数';}  return (    <div>      {/* 数据绑定 */}        <p>年龄{a}</p>        <p>{f()}</p>        <p>{user.username}</p>        <p>{JSON.stringify(user)}</p>    </div>  );}
```

**标签属性语法**

```
<标签 属性名={变量}></标签>
```

**案例**

```
function App() {  let a=30;  let imgSrc=`https://t7.baidu.com/it/u=1595072465,3644073269&fm=193&f=GIF`;  return (    <div>      {/* 属性绑定 */}      <img src={imgSrc} aa={a}></img>    </div>  );}
```

**三目表达式语法**

```
{三目表达式}
```

**案例**

```
function App() {  let a=30;  return (    <div>      {/* 条件渲染 */}        <p>年龄{a>18?'已成年':'未成年'}</p>    </div>  );}
```

**列表语法**

```
{	可遍历引用.map(()=>{return <标签 key={}>元素</标签>})}
```

**案例**

```
function App() {  const arr=[1,2,34,5,6,7,8];  return (    <div>      <ul>        {              arr.map((item,index)=>{          return <p key={index}>数组元素:{item},{index}</p>        })}      </ul>    </div>  );}
```

**标签的类样式**

```
<标签 className="类名"></标签>
```

**案例**

```
function App() {    function f1(){      let user={username:"admin",pwd:123456}      return Object.values(user);	}  return (    <div>       {f1().map(((item,index)=>{          return <p key={index} className='a'>{item}</p>        }))}    </div>  );}
```

**标签的行内样式**

```
<标签 style={{行内样式}}></标签>
```

**案例**

```
function App() {  return (    <div>   		<p style={{color:"red"}}>我要测试行内样式</p>    </div>  );}
```

#### jsx规则

```
1、在JSX语法中，当遇到了<>就会按照html语法来解析，当遇到了{}就会按照js语法来解析。2、return的最外层只能有一个根标签。3、JSX标签可以相互进行嵌套，注意代码的缩进和换行，增强代码的可读性。4、通过JSX语法将数据渲染到页面中也有虚拟DOM。
```

**vscode自动jsx补全**

```
点击左下角——>设置——>搜索emmet——>点击在settings.json中编辑——>添加如下代码"emmet.includeLanguages": {    "javascript": "javascriptreact"}
```

### 事件

#### 事件的绑定

**语法**

**箭头函数方式**

```
<button on事件名={()=>this.fn1()}></button>
```

**bind方式**

```
<button on事件名={this.fn1.bind()}></button>
```

**案例**

```
function f(){  console.log("我被点击了");}      {/* 箭头函数方式 */}      <button onClick={()=>f()}>按钮</button>      {/* bind方式 */}      <button onClick={f.bind()}>按钮2</button>
```

#### 事件传参

**语法**

**箭头函数方式**

```
<button on事件名={()=>this.fn1(...参数)}></button>
```

**bind方式**

```
<button on事件名={this.fn1.bind(event,...参数)}></button>
```

**案例**

```
function ff(a){  console.log(a);}      <button onClick={()=>ff('admin')}>按钮3</button>      <button onClick={ff.bind(Event,"adddd")}>按钮4</button>
```

#### 事件对象

**语法**

**箭头函数方式**

```
<button on事件名={(event)=>this.fn1([...参数,]event[,...参数])}></button>
```

**bind方式**

```
<button on事件名={this.fn1.bind(event,...参数)}></button>
```

**案例**

```
function fff(a,event){  console.log(a);  console.log(event);}      <button onClick={()=>fff("aaaaa",Event)}>按钮5</button>      <button onClick={fff.bind(Event,"adddd")}>按钮6</button>
```

#### 事件应用

**阻止默认行为**

```
function ffff(event){  event.preventDefault();  console.log("我被点击");}<div className="dBox" onContextMenu={(event)=>ffff(event)}>我是点击</div>
```

**阻止事件传播**

```
function f1(){  console.log("我被点击1");}function f2(event){  event.stopPropagation();  console.log("我被点击2");}      <div className="dBoxb" onClick={()=>f1()}>        <div className="dBox" onClick={(event)=>f2(event)}></div>      </div>
```

#### 事件捕获

**语法**

```
on事件名称Capture={}
```

**案例**

```
function f1(){  console.log("我被点击1");}function f2(event){  console.log("我被点击2");}      <div className="dBoxb" onClickCapture={()=>f1()}>        <div className="dBox" onClickCapture={()=>f2()}></div>      </div>
```

### 状态机（state）

#### 状态机定义

状态机定义在类中

**构造方法定义**

```
  constructor(){    super()    this.state = {}  }
```

**变量定义**

```
state = {}
```

**案例**

```
import {Component}from "react";class page extends Component{    //state的定义有两种方式    //直接定义    // state={    //     username:"admin",    //     pwd:123456    // }    //在构造函数中定义状态机    constructor(){        super();        this.state={//先声明，在帮给当前类            username:"admin",            user:{u1:"aaa"},            arr:[1,2,4,5,6,8,9]        }    }    render(){        let {username,user,arr}=this.state;        return(            <div>                {this.state.username}                {this.state.pwd}                {                    arr.map(item=>{                        return <p>{item}</p>                    })                }            </div>          )      }}export default page;    
```

#### 状态机使用

**修改状态机语法**

```
setState({}[,()=>{}])
```

参数1，需要修改键名和值

参数2：回调函数，由于setState是异步的，所以参数二相当于then方法。

注意事项

1、如果定义的数据不在state中，则数据发生变化的时候，不会驱动页面重新渲染。

2、只能使用setState()来修改状态机的值。setState是异步的

3、一定不要在render中调用setState()，因为setState()会引起页面的重新渲染，如果在render中调用会陷入死循环。

4、在开发模式下 \<React.StrictMode>会被执行，导致render函数执行两便去掉就好。

5、state中数据支持解构赋值。

6、state中操作数组/对象，需要先取数组/对象，修改数组/对象，再存放回去

**案例**

状态机的定义修改案例

```
import {Component}from "react";class page extends Component{    constructor(){        super();        this.state={//先声明，在帮给当前类            username:"admin"        }    }    changeUserName(){       //this.setState({username:"admin1",pwd:123123});       //this.a=60;    }    a=30;    render(){        let {username,user,arr}=this.state;        return(            <div>                我是子组件                <button onClick={()=>this.changeUserName()}>按钮</button>                {this.state.username}                {this.state.pwd}                <p>{username}</p>            </div>          )      }}export default page;    
```

操作数组

```
import {Component}from "react";class page extends Component{    constructor(){        super();        this.state={            arr:[1,2,4,5,6,8,9]        }    }    changeUserName(){       //this.setState({arr:[1,2,100,5,6,8,9]})       this.state.arr.splice(2,1,100)       this.setState({arr:this.state.arr})    }    render(){        let {arr}=this.state;        return(            <div>                我是组件                <button onClick={()=>this.changeUserName()}>按钮</button>                {                    arr.map(item=>{                        return <p>{item}</p>                    })                }            </div>          )      }}export default page;
```

操作对象

```
import {Component}from "react";class page extends Component{    constructor(){        super();        this.state={            user:{u1:"aaa"}        }    }    changeUserName(){       this.setState({user:{u1:"bbbb"}})    }    render(){        let {user}=this.state;        return(            <div>                我是组件                <button onClick={()=>this.changeUserName()}>按钮</button>                <p>{user.u1}</p>            </div>          )      }}export default page;
```

### form表单

#### 表单控件分类

**受控表单**

通过表单控件的value属性，给表单控件赋予仓库的默认值，这种表单控件称为受控表单控件。

**特点**

就地反馈，如：验证 禁用按钮，如：提交 执行特定的输入格式，如：手机号、身份证号、银行卡号

**非受控表单**

没有通过表单控件的value属性，给表单控件赋予仓库的默认值，这种表单控件称为非受控表单控件。

\####

**案例**

```
    state={        username:"admin"    }    changeText(event){        this.setState({username:"aaaaa"})    }    
```

#### 受控表单和非受控表单对比

#### 综合案例

输入框，密码框，单选框，下拉框，多选框，文本框，是否同意协议。

姓名，密码，性别，职业，爱好，自我介绍，

```
import {Component}from "react";class Page extends Component{    state={        username:"admin"    }    changeText(event){        // this.setState({username:"aaaaa"})        // console.log(event.target.value);        //console.log(event.target.value);        //单选框event.target.checked/event.target.value       // console.log(event.target.value);       //复选框event.target.checked/event.target.value       //下拉框event.target.value       //文本框event.target.value       console.log(event.target.value);    }    render(){        return(            <div>                用户名<input type="text" value={this.state.username} onChange={(event)=>this.changeText(event)}/><br></br>                密&emsp;码<input type="password" onChange={(event)=>this.changeText(event)}/><br></br>                性&emsp;别                <input type="radio" name="sex" id="" onChange={(event)=>this.changeText(event)}/>男                <input type="radio" name="sex" id="" />女<br></br>                爱&emsp;好                <input type="checkbox" name="" id=""  onChange={(event)=>this.changeText(event)}/>读                <input type="checkbox" name="" id="" />写                <input type="checkbox" name="" id="" />背<br></br>                城&emsp;市                <select name="" id="" onChange={(event)=>this.changeText(event)}>                    <option value="0">广东省</option>                    <option value="1">河南省</option>                    <option value="2">湖南省</option>                    <option value="3">湖北省</option>                    <option value="4">台湾省</option>                </select><br></br>                简介                <textarea name="" id="" cols="30" rows="10"  onChange={(event)=>this.changeText(event)}></textarea>                            </div>        )              }}export default Page
```

### 组件

组件分为两种函数组件和类组件。

#### 组件定义

建议将组件定义到components文件夹中。

**函数组件**

**语法**

```
function 函数名(){  return <div>内容</div>}export default 函数名
```

**案例**

```
function child1(){    return <div>        <p>我是函数组件</p>        我是函数组件    </div>    // return (    //     <div>    //     </div>        // )}export default child1;
```

**类组件**

**语法**

```
import React,{Component} from "react"class 类名 extends Component {  render(){    return <div>内容</div>  }}export default 类名
```

**案例**

```
import { Component } from 'react';class Child2 extends Component {    render() {        return <div>            我是类组件            </div>    }}export default Child2;
```

**定义的注意事项**

1、组件名首字母必须大写。 2、组件最外层只能有一个根标签。

#### 组件的使用

```
<组件名></组件名>
```

**使用注意事项**

1、使用之前直接进行引入。 2、组件区分大写，直接使用即可。

**两种组件的区别**

1、子组件接收父组件的传值方式不一样，函数定义使用props接收，类定义使用this.props接收。 2、函数定义没有生命周期，类定义有生命周期。 3、类定义有状态机state，函数定义没有状态机state。

4、在类定义中默认还要初始化一下，而函数定义不需要初始化。就加载速率来说，函数定义的要比类定义快一点。

5、新版本中使用函数速度会快一些，旧版本推荐使用类

#### 组件的通信

**props**

**父子组件传值**

**父组件**

**语法**

```
<组件名 键名={键值} ></组件名>
```

**子组件**

**语法**

```
this.props
```

**案例**

**父组件**

```
import {Component}from "react";import Child from "./Child";class Page extends Component{    username="admin";    pwd=123123;    state={        u1:"admin"    }    render(){        return <div>            <Child username={this.username} pwd={this.pwd} ss={this.state}></Child>        </div>    }}export default Page;
```

**子组件**

```
import {Component} from "react";class Child extends Component{    render(){        console.log(this.props);        return <div>            我是子组件            {this.props.username}           {JSON.stringify(this.props)}        </div>    }}   export default Child
```

**批量传值（父子孙传值）**

**父组件**

**语法**

```
<组件名 键名={键值} ></组件名>
```

**子组件**

**语法**

```
<子组件子组件 {...this.props}></子组件子组件>
```

**孙子组件**

**语法**

```
this.props
```

**案例**

**父组件**

```
import {Component}from "react";import Child from "./Child";class Page extends Component{    username="admin";    pwd=123123;    state={        u1:"admin"    }    render(){        return <div>            <Child username={this.username} pwd={this.pwd} ss={this.state}></Child>        </div>    }}export default Page;
```

**子组件**

```
import {Component} from "react";import Childchild from "./Childchild";class Child extends Component{    render(){        // console.log(this.props);        return <div>            我是子组件            {/* {this.props.username}           {JSON.stringify(this.props)} */}           <Childchild {...this.props}></Childchild>        </div>    }}   export default Child
```

**子子组件**

```
import {Component} from "react";class Childchild extends Component{    render(){        return <div>            我是子组件的子组件            {JSON.stringify(this.props)}        </div>    }}export default Childchild
```

**组件的虚拟DOM**

**语法**

**父组件**

```
<组件名><标签>内容</标签></组件名>
```

**子组件**

```
this.props.children
```

可以获取父组件，通过子组件的标签节点获取子组件标签节点下的内容，并将其转换数组。

**案例**

**父组件**

```
import {Component}from "react";import Child from "./Child";class Page extends Component{    render(){        return <div>            <Child>                <b>我是憨憨</b>                <b>我是喜喜</b>            </Child>        </div>    }}export default Page;
```

**子组件**

```
import {Component} from "react";class Child extends Component{    render(){       console.log(this.props);        return <div>            我是子组件           {this.props.children[0]}        </div>    }}   export default Child
```

**子父组件传值**

注：采用传递修改方法的方式进行修改传递。

**父组件**

```
<组件名 方法名={(event)=>this.父组件的方法(event)}></组件名>
```

**子组件**

```
this.props.方法名
```

**案例**

**父组件**

```
import {Component}from "react";import Child from "./Child";import "./index.css";class Page extends Component{    state={        username:"admin"    }    chageUsername(aa){        this.setState({username:aa});    }    render(){        return <div className="divp">            我是父组件            <p>{this.state.username}</p>            <Child changU={(ee)=>this.chageUsername(ee)}></Child>            </div>    }}export default Page;
```

子组件

```
import {Component} from "react";import "./index.css";class Child extends Component{    render(){        return <div className="divc">            我是子组件          <button onClick={()=>this.props.changU("憨憨")}>按钮</button>           </div>    }}   export default Child
```

**构造方法中的props使用**

在构造方法中使用props，需要先将props传递给component父类构造方法，才能在子类中继承使用。

**语法**

```
constructor(props){    super(props)    console.log(this.props);}
```

**props和state区别**

state状态机，存放当前组件数据，需要通过setState()进行修改。

props是用来传值的，props的数据在子组件中是只读的，如果需要传值可以使用调用修改函数方式传值。

### 组件

#### 组件生命周期

**完整版**

![react完整版生命周期](file:///E:/%E6%8E%88%E8%AF%BE%E5%86%85%E5%AE%B9/%E4%B8%AD%E5%85%AC/VUE%E8%AF%BE%E7%A8%8B/%E7%AC%94%E8%AE%B0/2022%E5%B9%BF%E5%B7%9EWeb%E5%85%A8%E6%A0%88%E9%9D%A2%E6%8E%88%E5%B0%B1%E4%B8%9A%E7%8F%AD10%E7%8F%AD/img/react%E5%AE%8C%E6%95%B4%E7%89%88%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F.png?lastModify=1664353384)

**Mounting(挂载)**

constructor() 组件构造函数，初始化数据

getDerivedStateFromProps() 在渲染之前，修改state中的数据。 ①、一定要在前面加上static，声明为静态的，不然会被react忽略同时还报错 ②、一定要保证在constructor中定义了state ③、一定要加上return，如果return空对象则表示什么都不修改，如果return键值对则会修改成当前这个键值对的样子

render() 渲染DOM的方法，加载并渲染所有的DOM元素 componentDidMount() 组件挂载完毕调用，一般情况下在这里开启定时器、开启倒计时、做数据交互

**Updating(更新)**

getDerivedStateFromProps() 在挂载完成后，再次渲染前再次被调用， 根据 shouldComponentUpdate() 的返回值，判断 React 组件的输出是否受当前 state 或 props 更改的影响。可以影响的常见方法包括New props、setState()、forceUpdate()。 shouldComponentUpdate(nextProps,nextState) ，当 props 或 state 发生变化时，会被调用，其主要功能判断要不要更新，可以控制值变换而决定是否更新。 1、return true 要更新，就会走render进行局部更新 2、return false 不要更新，就不会走render也不会进行局部更新

render() 重新渲染DOM元素

getSnapshotBeforeUpdate() ，在最近一次渲染输出（提交到 DOM 节点）之前调用。

componentDidUpdate() ，在更新完毕后调用

**Unmounting(卸载)**

componentWillUnmount(): 在组件卸载及销毁之前直接调用。一般情况下在这里关闭定时器、关闭倒计时

**常用版**

![react常用生命周期](file:///E:/%E6%8E%88%E8%AF%BE%E5%86%85%E5%AE%B9/%E4%B8%AD%E5%85%AC/VUE%E8%AF%BE%E7%A8%8B/%E7%AC%94%E8%AE%B0/2022%E5%B9%BF%E5%B7%9EWeb%E5%85%A8%E6%A0%88%E9%9D%A2%E6%8E%88%E5%B0%B1%E4%B8%9A%E7%8F%AD10%E7%8F%AD/img/react%E5%B8%B8%E7%94%A8%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F.png?lastModify=1664353384)

**父子组件的生命周期执行顺序**

单组件执行顺序

**没有更新正常版执行顺序**

我是构造=>我是渲染=>我是挂载完成=>我是卸载前

**更新正常版执行顺序**

我是构造=>我是渲染=>我是挂载完成=>我是渲染=>我是更新完成=>我是卸载前

**没有更新完整版执行顺序**

我是构造=>我是被调用getDerivedStateFromProps=>我是渲染=>我是挂载完成=>我是卸载前

**更新正常版执行顺序**

**当判断更新方法返回false的时候**

我是构造=>我是被调用getDerivedStateFromProps=>我是渲染=>我是挂载完成=>我是被调用getDerivedStateFromProps=>我是判断你要不要更新=>我是卸载前

**当判断更新方法返回true的时候**

我是构造=>我是被调用getDerivedStateFromProps=>我是渲染=>我是挂载完成=>我是被调用getDerivedStateFromProps=>我是判断你要不要更新=>我是渲染=>最后一次更新结果=>我是更新完成=>我是卸载前

父子组件执行顺序

我是构造=>我是被调用=>我是渲染=>我是构造儿=>我是被调用儿=>我是挂载完成儿=>我是挂载完成=>我是被调用getDerivedStateFromProps=>我是判断你要不要更新=>我是渲染=>我是被调用儿getDerivedStateFromProps=>我是判断你要不要更新儿=>最后一次更新结果儿=>最后一次更新结果=>我是更新完成儿/我是卸载前儿=>我是更新完成

**案例**

父组件

```
import  { Component } from 'react'import Child from "./Child";export default class Page extends Component {  constructor(){    super()    this.state={      username:"admin",      flag:true    }    console.log("我是构造");  }  static getDerivedStateFromProps(a,newState){    console.log(a);    console.log(newState);//是最新的state值    console.log("我是被调用");      //return {username:"addffsddf"};    return null;  }  shouldComponentUpdate(c,newValue){    console.log(c);    console.log(newValue);//是最新的state值    console.log("我是判断你要不要更新");    return true;  }getSnapshotBeforeUpdate(){  console.log("最后一次更新结果");  return null;}  componentDidMount(){    console.log("我是挂载完成");  }  componentDidUpdate(){    console.log("我是更新完成");  }  componentWillUnmount(){    console.log("我是卸载前");  }    changeUsername(){    this.setState({      flag:false    })  }  render() {    console.log("我是渲染");    console.log(this.state);    return (      <div>        <button onClick={()=>this.changeUsername()}>按钮</button>        用户名:{this.state.username}        {this.state.flag?<Child username={this.state.username}></Child>:null}        </div>    )  }}
```

子组件

```
import React, { Component } from 'react'export default class Child extends Component {    constructor(){        super()        console.log("我是构造儿");        this.state={                    }      }      static getDerivedStateFromProps(newProps,newState){        console.log(newProps);//是最新的Props值        // console.log(newState);//是最新的state值        console.log("我是被调用儿");          return {username:"addffsddf"};//return null;      }      shouldComponentUpdate(newProps,newValue){        console.log(newProps);//是最新的Props值        // console.log(newValue);//是最新的state值        console.log("我是判断你要不要更新儿");        return true;      }    getSnapshotBeforeUpdate(){      console.log("最后一次更新结果儿");      return null;    }          componentDidMount(){        console.log("我是挂载完成儿");      }      componentDidUpdate(){        console.log("我是更新完成儿");      }      componentWillUnmount(){        console.log("我是卸载前儿");      }  render() {    let {username}=this.props;    return (      <div>        Child        {username}        </div>    )  }}
```

#### 组件优化

**空标签组件（Fragment）**

使用场景：假设在父组件中的ul标签中使用子组件，那么现在的嵌套是ul套div套li，这是一个不合理的嵌套。我们希望ul标签内直接套li标签；我们可以将子组件最外层的div删掉，只写一个空标签来解决，但是官方不建议这样，官方给我们提供了fragment组件来解决，fragment组件就是一个空标签。

**案例**

**父组件**

```
import  { Component } from 'react'import Child from './Child';export default class Page extends Component {  render() {    return (      <div>        <ul>            <Child></Child>        </ul>      </div>    )  }}
```

**子组件**

```
import { Component, Fragment } from 'react'export default class Child extends Component {    constructor(){        super();        this.state={            arr:["外卖","电影","音乐"]        }    }  render() {    let {arr}=this.state;    return (      <Fragment>        {            arr.map((item,index)=><li key={index}>{item}</li>)        }      </Fragment>    )  }}
```

**组件销毁优化（componentWillUnmount）**

使用场景：子组件中有一个定时器，在子组件销毁的时候，定时器会一直存储在内存中，我们希望在子组件将要销毁的时候定时也也需要清空。

**案例**

**子组件**

```
import { Component } from 'react'export default class Child extends Component {  constructor(){    super();    this.state={        time:new Date().toLocaleString()    }  }componentDidMount(){    this.dingshiqi=setInterval(()=>{        this.setState({time:            new Date().toLocaleString()        })    },1000);    console.log(this);}  componentWillUnmount(){    clearInterval(this.dingshiqi);    console.log("我销毁");    console.log(this);  }    render() {     let {time}=this.state;    return (      <div>        <div>time:{time}</div>      </div>    )  }}
```

**父组件**

```
import  { Component } from 'react'import Child from './Child';export default class Page extends Component {    constructor(){        super();        this.state={            flag:true        }    }    chageFlag(){        this.setState({flag:false})    }  render() {    let {flag}=this.state;    return (      <div>        Page        <button onClick={()=>{this.chageFlag()}}>按钮</button>        {flag?<Child></Child>:null}    </div>    )  }}
```

**更新判定优化（shouldComponentUpdate）**

使用场景：假设父组件有很多很多数据，子组件只依赖部分数据，现在效果就是只要其父组件中的任何一个数据发生变化了都会引起子组件的重新渲染。我们希望只有当子组件依赖的数据发生变化了才会引起子组件的重新渲染。

**案例**

**父组件**

```
import { Component } from 'react'import Child from './Child';export default class Page extends Component {    constructor(){        super();        this.state={            username:"admin"        }    }    changeUsername(){        this.setState({username:"aaaaa"});    }  render() {    let {username}=this.state;    return (      <div>        Page        <button onClick={()=>this.changeUsername()}>按钮</button>        <p>{username}</p>            <Child username={username}></Child>        </div>    )  }}
```

**子组件**

```
import { Component } from 'react'export default class Child extends Component {    shouldComponentUpdate(newProps,newState){        console.log(newProps);        return false;    }  render() {    let {username}=this.props;    return (      <div>        Child        {username}    </div>    )  }}
```

**纯组件（pureComponent）**

使用场景：假设父组件有很多很多数据，子组件只依赖了其中的一个，现在效果就是只要其父组件中的任何一个数据发生变化了都会引起子组件的重新渲染。我们希望只有当子组件依赖的数据发生变化了才会引起子组件的重新渲染。

注：以浅层对比 prop 和 state 的方式来实现了shouldComponentUpdate()函数，主要针对类组件

**案例**

**父组件**

```
import  { Component } from 'react'import Child from './Child';export default class Page extends Component {    constructor(){        super();        this.state={            username:"admin",            pwd:123456        }    }    changPwd(){        this.setState({pwd:"123123"});    }    changUsername(){        this.setState({username:"aaaaaaa"});    }  render() {    let {username,pwd}=this.state;    return (      <div>        Page        <button onClick={()=>this.changPwd()}>按钮</button>        <button onClick={()=>this.changUsername()}>按钮2</button>        <p>{username},{pwd}</p>        <Child username={username}></Child>        </div>    )  }}
```

**子组件**

```
import React, { PureComponent } from 'react'export default class Child extends PureComponent {  render() {    let {username}=this.props;    console.log("我是子组件");    return (      <div>        Child        <p>{username}</p>      </div>    )  }}
```

**React.Memo方法**

使用场景：假设父组件有很多很多数据，子组件只依赖了其中的一个，现在效果就是只要其父组件中的任何一个数据发生变化了都会引起子组件的重新渲染。我们希望只有当子组件依赖的数据发生变化了才会引起子组件的重新渲染。

注：以浅层对比 prop 和 state 的方式来实现了shouldComponentUpdate()函数，主要针对函数组件

**案例**

**父组件**

```
import  { Component } from 'react'import Child from './Child';export default class Page extends Component {    constructor(){        super();        this.state={            username:"admin",            pwd:123456        }    }    changPwd(){        this.setState({pwd:"123123"});    }    changUsername(){        this.setState({username:"aaaaaaa"});    }  render() {    let {username,pwd}=this.state;    return (      <div>        Page        <button onClick={()=>this.changPwd()}>按钮</button>        <button onClick={()=>this.changUsername()}>按钮2</button>        <p>{username},{pwd}</p>        <Child username={username}></Child>        </div>    )  }}
```

**子组件**

```
import React from 'react'function Child(props) {  let {username}=props;    console.log("我是子组件");    return (      <div>        Child        <p>{username}</p>      </div>    )}export default React.memo(Child);
```

**语境方法context**

使用场景：假设父组件有一些数据，子组件不需要使用，但是子子组件需要使用，我们传统的方式是父组件传给子组件，子组件再传给子子组件，如果组件嵌套比较多的话就不太合理了。我们可以借助React.context()来解决。

**案例**

**父组件**

```
import { Component,createContext } from 'react'import Child from './Child';export const {Provider,Consumer} =createContext();//Provider 传递数据//Consumer 接收数据export default class Page extends Component {    constructor(){        super();        this.state={            username:"admin"        }    }  render() {    let {username}=this.state    return (      <div>        Page        {username}        <Provider value={{username:username}}>           <Child></Child>         </Provider>      </div>    )  }}
```

子组件

```
import React, { Component } from 'react'import ChildChild from './ChildChild'export default class Child extends Component {  render() {    return (      <div>        Child        <ChildChild></ChildChild>        </div>    )  }}
```

子子组件

```
import React, { Component } from 'react'import {Consumer} from "./Page";export default class ChildChild extends Component {  render() {    return (      <div>        ChildChild        <Consumer>            {(e)=>{                let {username}=e;                   return <div>                    <p>{JSON.stringify(e)}</p>                    <p>{username}</p>                </div>            }}        </Consumer>        </div>    )  }}
```

#### 错误边界处理函数（componentDidCatch）

使用场景：假设父组件内有很多页面，但是其中一个子组件的错误会引起整套页面的崩塌，我们希望当子组件出现错误的时候仅仅是子组件自己不渲染不会影响到其他页面的内容。

componentDidCatch函数，当页面发生错误的时候被触发。

**案例**

父组件

```
import React, { Component } from 'react'import Child from './Child'export default class Page extends Component {    constructor(){        super();        this.state={            flag:true        }    }    componentDidCatch(){        console.log("我打印不？");        this.setState({flag:false});    }  render() {    let {flag}=this.state;    return (      <div>        {flag?<Child></Child>:null}      </div>    )  }}
```

**子组件**

```
import React, { Component } from 'react'export default class Child extends Component {  render() {    // console.log(a);    // let a=30;    return (      <div>        Child    </div>    )  }}
```

#### 高阶组件

HOC(Higher­order component)是一种React 的进阶使用方法，主要还是为了便于组件的复用，并非官方方法。HOC本身并不是 React API, 它就是一个方法，一个接收一个组件作为参数，返回一个增强的组件的方法。

注：高阶组件有且只有一个参数。

**案例**

```
import  { Component } from 'react'import Child1 from './Child1';import Child2 from './Child2';import f from "./index";  let C1=f(Child1);  let C2=f(Child2);  export default class Page extends Component {    render() {      return (        <div>         <C1></C1>         <C2></C2>      </div>              )    }  }
```

**高阶组件的模块化**

**index.js**

```
import { Component } from 'react'export default function f(C){    return class H extends Component{      constructor(){        super();        this.state={          str:`我是一个子组件`        }      }        render(){          return (<div>            <C str={this.state.str}></C>          </div>)        }      }    }
```

### 过渡动画

#### 下载

```
npm i react-transition-group
```

#### 引入

```
import {CSSTransition,TransitionGroup} from "react-transition-group"
```

#### 使用

**关键配置项**

```
unmountOnExit	必填，退出时实现卸载该组件in				必填，该元素受哪个状态所影响timeout			必填，过渡动画的持续时间classNames		必填，指过渡动画的类名（两组四个）onEnter			元素进入前的回调函数onEntering		元素进入中的回调函数onEntered		元素进入后的回调函数onExit			元素离开前的回调函数onExiting		元素离开中的回调函数onExited		元素离开后的回调函数
```

**案例**

**样式文件**

```
/* 进入 */.fade-enter{  opacity: 0;}.fade-enter-active{  opacity: 1;  transition: all 1s;}/* 离开 */.fade-exit{  opacity: 1;}.fade-exit-active{  opacity: 0;  transition: all 1s;}
```

**jsx文件**

**单元素过渡动画**

```
        <button onClick={()=>this.setState({flag:!flag})}>{msg}</button>        <CSSTransition unmountOnExit in={flag} timeout={500} classNames="fade" onEntered={()=>this.setState({msg:"隐藏"})} onExited={()=>this.setState({msg:"显示"})}>            <div className='boxDiv'></div>        </CSSTransition>
```

**列表过渡动画**

```
<ul>        <TransitionGroup>        {                arr.map((item,index)=>{                    return <CSSTransition unmountOnExit in={flag} timeout={1000} classNames="fade" key={index}>                        <li>                            <p>{item}</p>                            <button onClick={()=>this.delArr(index)}>删除</button>                        </li>                    </CSSTransition>                })            }        </TransitionGroup>            </ul>   
```

### 路由

#### 下载

```
npm i react-router-dom@latest
```

最新版本 6.4.0 2022.04

#### 路由模式

**注**：在react中使用路由的时候，一定要先设置路由模式，不然路由是无效的。

**引入**

index.js

```
import {BrowserRouter,HashRouter} from "react-router-dom"
```

BrowserRouter 不带#，相当于vue-router中的history路由模式 HashRouter 带#，相当于vue-router中的hash路由模式

**绑定使用使用**

index.js

```
root.render(  <BrowserRouter>    <App />  </BrowserRouter>);
```

#### 路由出口

**app.js**

```
import {Routes} from "react-router-dom"function App() {  return (    <div>      <Routes></Routes>    </div>  );}
```

#### 路由规则定义

**语法**

```
<Routes><Route path="/路由" element={<组件></组件>}></Route></Routes>
```

app.js

```
import {Routes,Route} from "react-router-dom";import Page from "./components/01_react生命周期/Page";function App() {  return (    <div>      <Routes>        {/* 路由规则 */}		<Route path="/index" element={<Index></Index>}></Route>      </Routes>    </div>  );}
```

#### 路由重定向

**语法**

```
import {Routes,Route,Navigate} from "react-router-dom"<Routes>	<Route path="*" element={<Navigate to="/路由"></Navigate>}></Route></Routes>
```

**应用**

**资源不存在(404)处理**

```
import {Routes,Route,Navigate} from "react-router-dom"<Routes> 	<Route path="/not" element={<Not></Not>}></Route>	<Route path="*" element={<Navigate to="/not"></Navigate>}></Route></Routes>
```

#### 路由嵌套

**语法**

**一级路由**

```
<Routes>	<Route path="/路由/*" element={<Index></Index>}></Route></Routes>
```

**二级路由**

```
 <Routes>        <Route path="home" element={<Home></Home>}></Route></Routes>        
```

**使用**

**app.jsx**

```
<Routes>	<Route path="/index/*" element={<Index></Index>}></Route></Routes>
```

**index.jsx**

```
import {Routes,Route,Navigate} from "react-router-dom"    <div>      <Routes>          <Routes>              <Route path='c1' element={<Child></Child>}></Route>              <Route path='c2' element={<Child1></Child1>}></Route>          </Routes>    </div>
```

#### 路由导航

**导航组件**

**语法**

**Link组件**

```
import {Link,NavLink} from "react-router-dom"<div>    <Link to="/路由">文字</Link>    <NavLink to="/路由" className={({isActive})=>isActive?'样式':undefined}>文字</NavLink></div>
```

**NavLink组件**

```
import {Link,NavLink} from "react-router-dom"<div>    <NavLink to="/路由" className={({isActive})=>isActive?'样式':undefined}>文字</NavLink>    <NavLink to="/路由" style={({isActive})=>isActive?{background:"orange"}:undefined}>文字</NavLink></div>
```

**注：**Link组件没有提供className和style，如果想要实现激活高亮的话就需要使用NavLink组件，NavLink组件默认会调用active样式

**案例**

**样式**

```
.footBox{  width: 100vw;  position: fixed;  left: 0;  bottom: 0;  display: flex;}.footBox .aaa{  color: white;  background-color: orange;}
```

**index.js**

```
import React, { Component } from 'react'import { Route, Routes, Link,NavLink} from 'react-router-dom'import Home from "./Home";import Fima from "./Fima";import Mine from "./Mine";import Msg from "./Msg";import "./index.css";export default class index extends Component {    render() {        return (<div>            <p><Link to="/index/home">首页</Link></p>            <p><NavLink to="/index/fima" style={({isActive})=>isActive?{background:"green"}:null}>理财</NavLink></p>            <p><NavLink to="/index/msg" className={({isActive})=>isActive?'aaa':null}>消息</NavLink></p>            <p><NavLink to="/index/mine">我的</NavLink></p>            <Routes>                <Route path='home' element={<Home></Home>}></Route>                <Route path='fima' element={<Fima></Fima>}></Route>                <Route path='mine' element={<Mine></Mine>}></Route>                <Route path='msg' element={<Msg></Msg>}></Route>            </Routes>        </div>        )    }}
```

**编程式导航**

**语法**

```
import {useNavigate} from "react-router-dom"const Navigate = useNavigate()Navigate("/路由");//追加一条新的历史记录Navigate("/路由",{replace:true})// 用新的历史记录替换掉当前历史记录Navigate(num),根据正负数，回退/前进指定历史记录
```

**案例**

```
import React from 'react';import {useNavigate} from "react-router-dom";export default function Home() {    let Navigate=useNavigate();  return (    <div>home        <button onClick={()=>Navigate(-2)}>按钮</button>    </div>  )}
```

#### 路由参数

**search传参**

**语法**

**传递**

```
<Link key={item.id} to={"/路由?键名=键值&&键名=键值}>
```

**接收**

**方式一**

```
import {useLocation} from "react-router-dom"const {search} = useLocation()
```

**方式二**

```
import {useSearchParams} from "react-router-dom"const [searchParams,setSearchParams] = useSearchParams()
```

**案例**

```
import React from 'react'import { useLocation }from "react-router-dom";export default function Child() { let {search}=useLocation();console.log(new URLSearchParams(search).get("username"));  return (    <div>Child</div>  )}
```

**案例2**

```
import React from 'react'import {useSearchParams} from "react-router-dom";export default function Child() {  let [searchParams,setSearchParams]=useSearchParams();  console.log(searchParams.get("username"));  return (    <div>Child</div>  )}
```

**state传参**

**语法**

**传递**

```
<Link key={item.id} to="/路由" state={{键名:键值}}>
```

**接收**

```
import {useLocation} from 'react-router-dom'const {state} = useLocation()console.log(state);
```

**案例**

```
import React from 'react'import { useLocation }from "react-router-dom";export default function Child() {  let {state}=useLocation();  console.log(state.usera);  return (    <div>Child</div>  )}
```

**动态路由传参**

**语法**

**路由规则**

```
<Route path="/路由/:变量名" element={<PlayingDetail></PlayingDetail>}></Route>
```

**传递**

```
<Link to={"/路由/"+值>
```

**接收**

```
import React from 'react'import { useParams }from "react-router-dom";export default function Child() {  let param=useParams();  console.log(param);  return (    <div>Child</div>  )}
```

#### 路由懒加载

**语法**

**引入 方式懒加载**

```
const 变量 = React.lazy(()=>import("引入路径"))
```

**React.Suspense方式**

此方式需要将路由出口进行包裹

```
<React.Suspense fallback={<div>正在加载中。。。</div>}>	<Routes>		所有路由规则	</Routes></React.Suspense>
```

### 过滤器

#### 创建过滤器

**filterPrice.js**

```
export default function 函数名(){  	过滤器语法  return ;}
```

#### 使用过滤器

```
<p>价格：{过滤器函数名(传递值)}</p>
```

**案例**

1、创建过滤器并导出

```
export default function dateFilter(date){    return new Date(date).toLocaleString().replaceAll("/","-");}
```

2、在需要使用的组件中

```
import dateFilter from "./filter";<p>当前时间：{dateFilter(dateTime)}</p>
```

### react公共组件的使用

**back.jsx**

```
import React from 'react'import {useNavigate}from "react-router-dom";export default function back() {  let Navigate=useNavigate();  return (    <div>      <button onClick={()=>Navigate(-1)}>返回</button>    </div>  )}
```

**组件**

```
import React, { Component } from 'react'import { Route,Routes } from 'react-router-dom';import Back  from "./Back";import ChildA from "./ChildA";import ChildB from "./ChildB";import ChildC from './ChildC';export default class Page extends Component {  state={    flag:false  }  changFlag(){    this.setState({flag:true})  }  render() {    let {flag}=this.state;    return (      <div>        {flag?<Back></Back>:null}        <Routes>        <Route path="a" element={<ChildA></ChildA>}></Route>        <Route path="b" element={<ChildB changeFlag={()=>this.changFlag()}></ChildB>}></Route>        <Route path="c" element={<ChildC changeFlag={()=>this.changFlag()}></ChildC>}></Route>        </Routes>        </div>    )  }}
```

### React UI库

#### antd

antd 是基于 Ant Design 设计体系的 React UI 组件库。

**特点**

* 🌈 提炼自企业级中后台产品的交互语言和视觉风格。
* 📦 开箱即用的高质量 React 组件。
* 🛡 使用 TypeScript 开发，提供完整的类型定义文件。
* ⚙️ 全链路开发和设计工具体系。
* 🌍 数十个国际化语言支持。
* 🎨 深入每个细节的主题定制能力。

**官方**

```
https://ant.design/index-cn
```

**下载**

**cdn方式**

```
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/antd/4.22.1/antd.css" /><script src="https://cdnjs.cloudflare.com/ajax/libs/antd/4.22.1/antd.js"></script>
```

**npm方式**

```
npm i antd
```

**引入方式**

**全局引入**

**index.js**

```
import "antd/dist/antd.css"
```

**组件使用**

```
import React, { Component } from 'react'import {Button} from "antd";import {CaretRightOutlined,AliwangwangOutlined} from "@ant-design/icons"; export default class Page extends Component {  render() {    return (      <div>        <Button type="primary" >按钮</Button>        <Button type="danger" >按钮</Button>        <Button type="danger"  ghost>按钮</Button>        <Button>按钮</Button>        <CaretRightOutlined style={{color:"blue"}} />        <AliwangwangOutlined style={{color:"pink"}}/>        <p>Page</p>        </div>    )  }}
```

**按需引入**

**组件内**

```
import React, { Component } from 'react'import {Button} from "antd";import {CaretRightOutlined,AliwangwangOutlined} from "@ant-design/icons"; import "antd/es/button/style/index.css"export default class Page extends Component {  render() {    return (      <div>        <Button type="primary" >按钮</Button>        <Button type="danger" >按钮</Button>        <Button type="danger"  ghost>按钮</Button>        <Button>按钮</Button>        <CaretRightOutlined style={{color:"blue"}} />        <AliwangwangOutlined style={{color:"pink"}}/>        <p>Page</p>        </div>    )  }}
```

**babel-plugin-import插件方式引入（推荐）**

**下载**

```
npm i babel-plugin-import
```

**使用**

1、在 src 下创建.babelrc文件，内容如下：

```
{ "presets": [ "react-app" ], "plugins": [ 	["import", { "libraryName": "antd", "style": "css" }]  ] }
```

2、通过命令暴露 webpack.config.js配置文件

```
npm run eject   y				// 可能会报错，因为本地仓库的代码和你现在的代码不是同一个版本git add .						// 将当前文件夹所有文件更新到本地仓库git commit -m "123"				// 给本地仓库的文件添加描述信息npm run eject	y
```

3、修改config/webpack.config.js

```
修改babelrc:true
```

4、修改 package.json

```
删除"babel": {"presets": ["react-app"]}
```

5、重启项目

```
npm start
```

6、使用即可

```
import React, { Component } from 'react'import {Button} from "antd";import {CaretRightOutlined,AliwangwangOutlined} from "@ant-design/icons"; export default class Page extends Component {  render() {    return (      <div>        <Button type="primary" >按钮</Button>        <Button type="danger" >按钮</Button>        <Button type="danger"  ghost>按钮</Button>        <Button>按钮</Button>        <CaretRightOutlined style={{color:"blue"}} />        <AliwangwangOutlined style={{color:"pink"}}/>        <p>Page</p>        </div>    )  }}
```

### 数据交互

#### 配置代理

**方式一**

**配置package.json代理**

1、package.json添加键值对

```
 "proxy": "http://localhost:3000"
```

2、重启项目

```
npm start
```

3、使用

```
import axios from "axios";let { data } = await axios.get("/api/getbanner")
```

**方式二**

**插件库方式**

1、安装依赖

```
npm i http-proxy-middleware
```

2、创建setupProxy.js文件

在src下创建【setupProxy.js】文件，内容如下：

```
const proxy = require("http-proxy-middleware")module.exports = (app)=>{  app.use("/api",proxy.createProxyMiddleware({    target:"http://localhost:3000",    changeOrigin:true,    pathRewrite:{      "^/api":"http://localhost:3000"    }  }))}
```

3、使用

```
let {data}=await axios.get("/aaa/api/getbanner");// 注意：如果使用这种方式配置代理的话，在开发环境下请求地址前面需要加上/aaa，生产环境就不需要加/aaa了.
```

#### axios使用

**get方式**

```
let {data}=await axios.get("/aaa/api/getbanner");
```

**post方式**

```
let {data:dd}=await axios.post("/aaa/api/login",{phone:"12312311231",password:123123});
```

**封装的使用**

http.js

```
import axios from "axios";export let baseURL="";if(process.env.NODE_ENV==="development"){    baseURL="http://localhost:3000";}//请求拦截器axios.interceptors.request.use(req=>req);//响应拦截器axios.interceptors.response.use(res=>res);export const getDatabyAxios=(url,{params,data},method="get")=>axios({    url,    method,    params,    data,    timeout:3000,    headers:{    }});
```

api.js

```
import {getDatabyAxios} from "./http";export const getBanner=()=>getDatabyAxios("/aaa/api/getbanner",{params:undefined});
```

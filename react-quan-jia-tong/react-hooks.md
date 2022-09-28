# React HOOKS

### 简介

Hook 是 React 16.8 的新增特性。它可以让你在不编写 class 的情况下使用 state 以及其他的 React 特性。

#### 解决的问题

1.用于在函数组件中引入状态管理和生命周期方法;

2.取代高阶组件和render props来实现抽象和可重用性;

3.完全脱离"类",便可写出一个全功能的组件。

### 常用的钩子

```
useState()      为函数提供状态机stateuseEffect()     为函数提供生命周期useReducer()    函数使用actionuseContext()    共享状态机钩子
```

### 函数的使用

#### useState

为函数提供状态机state

**基本语法**

```
let [变量名,设置变量的方法]=useState(默认值);
```

**案例**

```
import React from 'react'import { useState } from 'react';export default function Page() {let [username,setUsername]=useState("admin");const [pwd]=useState(123123123);const [user,setUser]=useState({username:"addd",pwd:"ddddd"});  return (    <div>            用户名{username}<br></br>        mima{pwd}        <p>{user.username}</p>        <button onClick={()=>setUsername("aaaaaaa")}>修改值</button>        <button onClick={()=>setUser({username:"xxxxxx",pwd:"aaaaaa"})}>值</button>        <p>{user.pwd}</p>    </div>  )}
```

#### useEffect

为函数提供生命周期

```
    //挂载的时候被调用componentDidMount+componentDidUpdate     useEffect(()=>{         console.log("我来了");     })    // 挂载的时候被调用componentDidMount     useEffect(()=>{         console.log("我又来了");     },[]);    //挂载的时候被调用componentDidMount+componentDidUpdate(只监听数组中存在变量的更新)    useEffect(()=>{        console.log("我再来了");    },[username]);  //将要销毁生命周期componentWillUnMount  useEffect(()=>{    return ()=>{      console.log("我什么时候执行");    }  },[]);
```

#### useReducer

为函数使用action

**基本语法**

```
    const [state,dispatch]=useReducer(storeRoules,initState);
```

**store/index.js**

```
//[state]export let initState={     username:"admin",    pwd:123123}const Types={    type1:"changeUsername",    type2:"changePwd"}//[mutation]export function storeRoules(state=initState,action){    switch(action.type){        case Types.type1:            state.username=action.username            return {...state}        case Types.type2:            state.pwd=action.pwd            return {...state}        default :            return state    }}[action]export const actions={    changUsername:username=>({type:Types.type1,username}),    changPwd:pwd=>({type:Types.type2,pwd})}[getter]export const getters={    getUsername:state=>state.username,    getPwd:state=>state.pwd}
```

**组件的使用**

```
import React,{useReducer} from 'react';import {storeRoules,initState,actions,getters} from "../../store/index";export default function Page() {    const [state,dispatch]=useReducer(storeRoules,initState);  return (    <div>        <button onClick={()=>{dispatch(actions.changUsername("sssss"))}}>修改</button>        用户名：{state.username}        密码：{getters.getPwd(state)}          </div>  )}
```

#### useContext

共享状态机钩子

**父组件**

```
import React ,{useState}from 'react'import Child from "./Child";export let  myConnext=React.createContext();export default function Page() {    let [username,setUsername]=useState("admin");    let [pwd,SetPwd]=useState(123123);    return (    <div>        用户名{username}        <myConnext.Provider value={{username,pwd}}>            <Child></Child>        </myConnext.Provider>        </div>  )}
```

**子组件**

```
import React from 'react'import Childchild from "./Childchild";export default function Child() {  return (    <div>        <Childchild></Childchild>    </div>  )}
```

**子子组件**

```
import React,{useContext} from 'react'import {myConnext}from "./Page";export default function Childchild() {    let state=useContext(myConnext);  return (    <div>        子子页面        用户名{state.username}    </div>  )}
```

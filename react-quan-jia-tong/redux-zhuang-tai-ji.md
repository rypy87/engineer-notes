# Redux状态机

#### 基本概念

Redux 是 JavaScript 应用的状态容器，提供可预测的状态管理。

#### 三大原则

**1、单一数据源**

整个应用的 state 被储存在一棵 object tree 中，并且这个 object tree 只存在于唯一一个 store 中。

**2、State 是只读的**

唯一改变 state 的方法就是触发 action，action 是一个用于描述已发生事件的普通对象。

**3、只能使用纯函数来执行修改**

为了描述 action 如何改变 state tree ，你需要编写 reducers函数。

#### 官网

```
https://redux.js.org/https://cn.redux.js.org/
```

#### 安装

```
npm i redux
```

#### 使用

创建store文件夹index.js文件

**基本语法**

**定义语法**

```
1、引入import { createStore } from 'redux'2、定义规则function 规则函数名(state = [], action) {  switch (action.type) {    case '操作类型名':      return 匹配后操作内容    default:      return state  }}3、创建仓库对象let store = createStore(规则函数名[,state的初始值])4、修改触发方法store.dispatch({  type: '操作类型名',  text: '对应传值'});console.log(store);console.log(store.getState());​export default store;
```

**获取语法**

```
store.getState()
```

**修改数据语法**

```
store.dispatch({  type: '操作类型名',  键名: 键值});
```

**监听语法**

```
store.subscribe(callback)
```

**案例**

**定义组件**

```
//1、引入import {createStore} from "redux";//2、定义规则function StateRules(state={},action){    //switch中每条语句结束使用return，return必须要有值，否则getState获取的就是undefined    switch(action.type){        case "changeUsername":            return {...state,...action.text};        case "changePwd":            return {...state,pwd:action.aaaaa};            default :            return state;    }}const state={username:"admin",pwd:123456};//3、创建容器实例const store=createStore(StateRules);​//4、触发动作// store.dispatch({//     type:"changeUsername",//     text:"aaaaa"// })​export default store
```

**组件中使用**

```
import React, { Component } from 'react'import store from  "../../store/index";export default class Page extends Component {    constructor(){        super();    }      changeUsername(value){        store.dispatch({            type:"changeUsername",            text:{username:value,pwd:"sssssss"}        });        this.setState({});        console.log(store.getState());    }    changeUserPwd(pwd){        store.dispatch({            type:"changePwd",            aaaaa:pwd        })        console.log(store.getState());    }  render() {    let {username}=store.getState();    return (      <div>        {username}        <input type="text" onBlur={(e)=>this.changeUsername(e.target.value)}/>        <button onClick={()=>this.changeUserPwd("ssssss")}>修改用户名</button>        Page    </div>    )  }}
```

### react-redux库

将状态机仓库进行组件化处理，将所需页面迭代为子组件。

#### 分类

React-Redux 将所有组件分成两大类：UI 组件（presentational component）和容器组件（container component）。

UI组件：一般用来展示数据，数据一般从父组件传过来，一般是函数定义。也叫木偶型组件。

容器型组件：一般用来处理逻辑业务的，数据一般从仓库过来，一般是类定义的。

**UI 组件**

负责 UI 的呈现，不带有任何业务逻辑

没有状态（即不使用this.state这个变量）

所有数据都由参数（this.props）提供

不使用任何 Redux 的 API

**容器组件**

负责管理数据和业务逻辑，不负责 UI 的呈现

带有内部状态

使用 Redux 的 API

**注意事项**

数组的方法如果不改变存储，插件不会监听更新。

#### 安装

```
npm i react-redux
```

#### 使用

**1、使用Provider将App和store进行绑定**

**index.js**

```
import { Provider } from "react-redux";import store from "./store/index.js";root.render(  <Provider store={store}>    <App />  </Provider>);
```

**2、将类组件变成容器型组件**

**Page.jsx**

```
import {connect}from "react-redux";class Page extends Component {	...	...	...}export default connect()(Page)
```

**3、将仓库的state绑定到类组件**

**Page.jsx**

```
let mapState=(state)=>{  return {    addFlag:state.addFlag,    userlist:state.userlist  }}export default connect(mapState)(Page)
```

**4、将触发行为进行封装并绑定仓库**

**Page.jsx**

```
let mapActions=(dispatch)=>{  return{    addUserAction(newUser){      dispatch({type:"addType",obj:newUser});    },    upUser(){      // store.dispatch()    },    delUser(){      // store.dispatch()    },    addUserView(){      dispatch({type:"FlagType",flag:true});    },    cancelAddUser(){      dispatch({type:"FlagType",flag:false});    }  }}export default connect(mapState,mapActions)(Page)
```

**5、组件的类中使用**

**Page.jsx**

```
 class Page extends Component {  render() {    let {addFlag}=this.props;    return (      <div>        <List {...this.props}></List>        {addFlag?<Add addUser={(user)=>this.addUser(user)} {...this.props} ></Add>:null}      </div>    )  }}
```

**6、修改状态层的state返回值**

**store/index.js**

```
function stroeRules(state={},action){    switch(action.type){        case "Type1":            return {...state,username:action.username};        case "Type2":            return {...state,pwd:action.pwd};        default :             return state;            }}
```

### store的优化

#### action优化

作用：用来统一管理所有的action

**store/index.js**

```
export const actions={    addUserAction:(newUser)=>{        return {type:Types.Type1,obj:newUser}    },    delUserAction:(id)=>{        return {type:Types.Type3,id:id}    },    changeAddFlagAction:(flag)=>{        return {type:Types.Type4,flag}    }}
```

**Page.jsx**

```
import {action} from "../../store/index";const mapActions=(dispatch)=>{    return {        addUserAction(newUser){           dispatch(action.addUserAction(newUser))        },        delUserAction(id){            dispatch(action.delUserAction(id))        },        addUserViewAction(){            dispatch(action.changeAddFlagAction(true))        },        cancelAddViewAction(){            dispatch(action.changeAddFlagAction(false))        }    }}
```

#### type优化

作用：统一管理所有的type

**store/index.js**

```
const Types={    Type1:"addType",    Type2:"upType",    Type3:"delType",    Type4:"FlagType"}function storeRules(state={},action){    switch(action.type){        case Types.Type1:            let {userlist}=state;            let newUser={                id:((userlist[userlist.length-1]?.id)??0)+1,                username:action.obj.username,                pwd:action.obj.pwd,                isadmin:"0"            }            return {...state,userlist:[...userlist,newUser]};        case Types.Type2:            return state.filter(item=>{                if(item.id===action.id){                    item={...action};                }                return true;            })        case Types.Type3:            return {...state,userlist:state.userlist.filter(item=>(item.id!==action.id))};        case Types.Type4:            return {...state,addFlag:action.flag}           default :            return state        }}export const actiona={    addUserAction:(newUser)=>{        return {type:Types.Type1,obj:newUser}    },    delUserAction:(id)=>{        return {type:Types.Type3,id:id}    },    changeAddFlagAction:(flag)=>{        return {type:Types.Type4,flag}    }}
```

#### dispatch优化

bindActionCreators方法，用来整合导出所有的actions上面的方法进行dispatch。

**Page.jsx**

代码区

```
import {bindActionCreators} from "redux";const mapActions=(dispatch)=>{    return {     ...bindActionCreators(actiona,dispatch)    }}
```

渲染区

```
 class Page extends Component {  render() {    let {addFlag}=this.props;    return (      <div>        <List {...this.props}></List>        {addFlag?<Add addUser={(user)=>this.addUser(user)} {...this.props} ></Add>:null}      </div>    )  }}
```

#### store模块化

作用：reducer进行拆分，按照各自的模块进行管理，方便了我们对项目未来的管理和修改。

**store/modules/user.js**

```
//1、初始化数据      相当于statelet initState={    msg:"",    code:0,    addFlag:false,    userlist:[        {            id:1,            username:"admin",            pwd:"123123",            isadmin:"1"        }    ]};//2、封装规则名const Types={    Type1:"addType",    Type2:"upType",    Type3:"delType",    Type4:"FlagType",    Type5:"loginType"}//3、绑定规则和数据 设置更改数据setter   相当于Mutationasync function storeRules(state=initState,action){    switch(action.type){        case Types.Type1:            let {userlist}=state;            let newUser={                id:((userlist[userlist.length-1]?.id)??0)+1,                username:action.obj.username,                pwd:action.obj.pwd,                isadmin:"0"            }            return {...state,userlist:[...userlist,newUser]};        case Types.Type2:            return state.filter(item=>{                if(item.id===action.id){                    item={...action};                }                return true;            })        case Types.Type3:            return {...state,userlist:state.userlist.filter(item=>(item.id!==action.id))};        case Types.Type4:            return {...state,addFlag:action.flag}        default :            return state        }}//4、设置动作   相当于Actionexport const actions={    addUserAction:(newUser)=>{        return {type:Types.Type1,obj:newUser}    },    delUserAction:(id)=>{        return {type:Types.Type3,id:id}    },    changeAddFlagAction:(flag)=>{        return {type:Types.Type4,flag}    }}//5，抛出设置export default storeRules;
```

**store/index.js**

```
import { createStore,combineReducers} from 'redux';import user from "./modules/user";const rootReducers=combineReducers({    user});const store=createStore(rootReducers)export default store;
```

**Page.jsx**

```
import {actions as actss} from "../../store/modconst mapState=(state)=>{    return {        addFlag:state.user.addFlag,        userlist:state.user.userlist    }}const mapActions=(dispatch)=>{    return {     ...bindActionCreators(actss,dispatch)    }}
```

### redux开发调试工具

#### redux-devtools

**下载**

**谷歌浏览器**

下载：百度搜索码云——>在码云搜索 分叉桶-前端 / redux-devtools-extension——>下载压缩包，在README.md文件中点击last releases，会打开一个网址[https://github.com/zalmoxisus/redux-devtools-extension/releases](https://github.com/zalmoxisus/redux-devtools-extension/releases)——>下载firefox.zip

安装：点击右上角三个点——>更多工具——>扩展程序——>点击右上角打开开发者模式——>将刚才的压缩包拖进来

**使用**

**下载包使用**

```
const store = createStore(    rootReducers, /* preloadedState, */    window.__REDUX_DEVTOOLS_EXTENSION__ && window.__REDUX_DEVTOOLS_EXTENSION__()   );
```

**NPM使用**

①安装

```
npm i @redux-devtools/extension
```

②使用

**store/index.js**

```
// 在store/index.js中import {composeWithDevTools} from "redux-devtools-extension"let store = createStore(rootReducer,composeWithDevTools(/* 中间件 */))
```

### 状态导出(selectors)

导出状态层的state

**状态层**

```
export const getters={    getUserName:(state)=>{        return state.user.list[0].username;    },    getPwd:(state)=>{        return state.user.list[0].pwd;    }}
```

**组件中**

```
import {actions,getters} from "../../store/modules/user";const mapState=(state)=>{    return {       username:getters.getUserName(state),       pwd:getters.getPwd(state)    }}
```

### redux的中间件

![redux 中间件](file:///E:/%E6%8E%88%E8%AF%BE%E5%86%85%E5%AE%B9/%E4%B8%AD%E5%85%AC/VUE%E8%AF%BE%E7%A8%8B/%E7%AC%94%E8%AE%B0/2022%E5%B9%BF%E5%B7%9EWeb%E5%85%A8%E6%A0%88%E9%9D%A2%E6%8E%88%E5%B0%B1%E4%B8%9A%E7%8F%AD10%E7%8F%AD/img/redux%20%E4%B8%AD%E9%97%B4%E4%BB%B6.png?lastModify=1664353496)

#### 自定义中间件

**基本语法**

**完整版**

```
let myMiddleware = (store)=>{	return (next)=>{		return (action)=>{			...			...			...		}	}}
```

**简写版**

```
let myMiddleware = store => next => action =>{	...	...	...}
```

**案例**

**store/index.js**

```
import {applyMiddleware, bindActionCreators,createStore} from "redux";import {composeWithDevTools}from "@redux-devtools/extension";//自定义中间件const logger=(store)=>{    return (next)=>{        return (action)=>{            console.log("我执行了没");            next(action);            }    }}//redux的中间是在   rules=>中间件=>actionsconst Errors=store=>next=>action=>{    try{        next(action);    }catch(e){        console.log("我出错了！"+e.message);    }}const store=createStore(storeRules,composeWithDevTools(applyMiddleware(logger,Errors)));export default store;
```

#### 第三方中间件

**redux-logger**

作用：用来打印，而且打印出来的内容比较详细，里面包含了改变之前的值和改变之后的值还有本次触发的哪个action。

**安装**

```
npm i redux-logger
```

**引入**

```
import reduxLogger from "redux-logger"
```

**使用**

```
let store = createStore(rootReducer,composeWithDevTools(applyMiddleware(reduxLogger)))
```

**redux-thunk**

用来处理异步，用来请求的。因为redux是单向数据流不支持异步请求。

**安装**

```
npm i redux-thunk
```

**引入**

```
import thunk from "redux-thunk"
```

**使用**

```
let store = createStore(rootReducer,composeWithDevTools(applyMiddleware(thunk)))
```

**案例**

**store/index.js**

```
const actions={  ...  ...  ...    getBannerList(){        //thunk本身提供的参数        return async (dispatch,getState)=>{            let {data}=await axios.get("http://localhost:3000/api/getbanner");            // console.log(data);            dispatch(actions.changeBannerList(data.list));        }    }}
```

**reselect**

reselect 是 redux 的一个中间件，它通过计算获得新的 state，然后传递到 Redux Store。其主要作用是进行计算，使得计算的状态被缓存，从而根据传入的 state 判断是否需要调用计算函数，而不用在组件每次更新的时候都进行调用，从而更加高效。

**安装**

```
npm i reselect
```

**引入**

```
import { createSelector } from "reselect"
```

**使用**

**store/index.js**

```
const getpageSum=(state)=>{    // console.log("我被调用过2");    return state.pageSum;}const getUss=state=>state.usss;const getUsernamec=createSelector([getUsername,getUss],(getUsername,getUss)=>{    console.log("我被调用过1");    return getUsername+getUss+"aaaadddd";});const getpageSumC=createSelector(getpageSum,(getpageSum)=>{    console.log("我被调用了");    return 1*getpageSum;});export const mapState=(state)=>{    return {        username:getUsername(state),        pageSum:getpageSum(state),        getpageSumC:getpageSumC(state),        bannerList:state.bannerList,        getUsernamec:getUsernamec(state)    }}
```

### 项目中redux目录结构设计

#### 按照功能划分

![按照功能划分](file:///E:/%E6%8E%88%E8%AF%BE%E5%86%85%E5%AE%B9/%E4%B8%AD%E5%85%AC/VUE%E8%AF%BE%E7%A8%8B/%E7%AC%94%E8%AE%B0/2022%E5%B9%BF%E5%B7%9EWeb%E5%85%A8%E6%A0%88%E9%9D%A2%E6%8E%88%E5%B0%B1%E4%B8%9A%E7%8F%AD10%E7%8F%AD/img/%E6%8C%89%E7%85%A7%E5%8A%9F%E8%83%BD%E5%88%92%E5%88%86.png?lastModify=1664353496)

#### 按照类型划分

![按照类型划分](file:///E:/%E6%8E%88%E8%AF%BE%E5%86%85%E5%AE%B9/%E4%B8%AD%E5%85%AC/VUE%E8%AF%BE%E7%A8%8B/%E7%AC%94%E8%AE%B0/2022%E5%B9%BF%E5%B7%9EWeb%E5%85%A8%E6%A0%88%E9%9D%A2%E6%8E%88%E5%B0%B1%E4%B8%9A%E7%8F%AD10%E7%8F%AD/img/%E6%8C%89%E7%85%A7%E7%B1%BB%E5%9E%8B%E5%88%92%E5%88%86.png?lastModify=1664353496)

**duck模式【推荐】**

```
-src	-containers							  // 业务组件-路由组件		-组件文件夹						  // 组件文件夹			组件.jsx						// 组件的主页面			-components					 // 子组件1文件夹				-子组件1				   // 子组件1文件夹					子组件1.jsx		   // 子组件1的页面					子组件1.css		   // 子组件1的样式				-add					 // 子组件2文件夹					子组件2.jsx		   // 子组件2的页面					子组件2.css		   // 子组件2的样式	-store								 // 仓库		index.js						 // 创建并导出仓库，整合所有的reducer		-modules						 // 模块			组件1.js					    // 组件的state、TYPES、reducer、actions、selectors			组件2.js						// role的state、TYPES、reducer、actions、selectors		-middleware						 // 中间件			logger.js					 // logger中间件			error.js					 // error中间件
```

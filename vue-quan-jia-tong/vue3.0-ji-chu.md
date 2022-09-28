# Vue3.0基础

### 简介

Vue3.0，在2020年9月份发布，在2022年npm正式默认推送vue3，目前版本 3.2.37

VUE2.0采用Options API的函数式API。

VUE3.0采用Composition API的组件式API，相对更灵活，更清晰。

Vue3支持vue2的大多数特性

**性能提升**

* 项目打包体积更小
* 初次渲染更快, 更新渲染更快
* 需要的运行内存更小
* 使用Proxy代替Object.defineProperty实现数据响应式
* 重写虚拟DOM的实现和Tree-Shaking
* 更好的支持Typescript

### 官网

```
英文官网：https://vuejs.org/中文官网：https://staging-cn.vuejs.org/
```

### 安装

#### CDN方式

```
<script src="https://unpkg.com/vue@3.2.37/dist/vue.global.js"></script>
```

#### npm方式

```
npm i vue
```

#### 脚手架方式

**webpack方式**

全局安装脚手架

```
npm i @vue/cli -g
```

创建项目

```
vue create 项目名称
```

选择vue3版本的项目创建

```
Default (Vue 3) ([Vue 3] babel, eslint)
```

启动项目

```
npm run serve
```

默认监听端口号8080

```
http://loclhost:8080
```

**Vite方式(推荐使用)**

vite是vuejs官方发布的一种构建工具

vite不是依赖于webpack

vite的底层依赖于浏览器对ES模块的语法支持来进行构建项目，所以构建项目速度非常快

**创建项目**

**方式一**

```
npm init vite 项目名称 [-- --template vue]
```

**方式二**

```
npm create vite 项目名称 [-- --template vue]
```

提示是否需要vite

```
是否安装vite插件          y               // 这一步只有第一次使用vite的时候才会提示需要安装的框架             vue选择语法                 vue
```

下载node\_modules依赖包

```
npm i 或者 npm install
```

启动项目

```
npm run dev
```

默认监听端口号5173

```
http://localhost:5173
```

#### 案例

**CDN**

```
<!DOCTYPE html><html lang="en"><head>    <meta charset="UTF-8">    <meta http-equiv="X-UA-Compatible" content="IE=edge">    <meta name="viewport" content="width=device-width, initial-scale=1.0">    <title>Document</title>    <script src="./vue.global.js"></script></head><body>    <div id="app">        {{username}}        {{pwd}}    </div>    <script>       const divVUE= Vue.createApp({            data(){                return {                    username:"admin",                    pwd:123123                }            },            methods: {},            computed: {},            components: {}        }).mount("#app");        // divVUE.mount("#app");    </script></body></html>
```

### 基本语法

#### VUE实例

**基本语法**

```
Vue.createApp({    data(){      return{        键名:键值      }    }   }).mount("#app")
```

**案例**

```
<template>   {{username}}   {{pwd}}</template><script>export default {    name:"Page",    data(){        return {            username:"admin",            pwd:123123        }    }}</script>
```

#### 新增特性

**fragment模板碎片**

vue2中组件的tempalte标签最外层只能有一个根标签 vue3中组件的tempalte标签最外层可以有多个标签

注：使用多标签需要修改插件

```
针对于vsCode编辑器要将Vetur插件禁用，下载Vue Language Features (Volar)插件
```

**案例**

```
<template>   {{username}}   {{pwd}}</template>
```

**setup方法**

setup 标签关键词和setup函数不能共存,使用了setup标签关键词不能使用export default.

setup 方法在组件创建完成之前自动调用，不能在其内部使用this访问组件内容。

当使用了setup标签关键词，相当于把整个标签都放到了setup函数中

在setup中定义的变量和方法，一定要return,否则不会绑定给data和methods

**语法**

**script标签使用**

```
<script setup>
```

**组件的使用**

```
export default{  setup(){}}
```

**案例**

```
<template>    <div>        {{username}}    </div></template><script>export default {    setup(){        let username="admin";        const changeUsername=()=>{            console.log("sssss");        }        return {username,changeUsername}    }};</script>
```

**Vue3.0的生命周期**

![vue-smzq3](file:///E:/%E6%8E%88%E8%AF%BE%E5%86%85%E5%AE%B9/%E4%B8%AD%E5%85%AC/VUE%E8%AF%BE%E7%A8%8B/%E7%AC%94%E8%AE%B0/2022%E5%B9%BF%E5%B7%9EWeb%E5%85%A8%E6%A0%88%E9%9D%A2%E6%8E%88%E5%B0%B1%E4%B8%9A%E7%8F%AD10%E7%8F%AD/img/vue-smzq3.png?lastModify=1664353223)

VUE3.0，包含8个生命周期钩子函数，beforeCreate(组件实例刚刚被创建)、created(组件实例创建完成)、beforeMount(模板编译/挂载前)、mounted(模板编译/挂载完成)、beforeUpdate(组件更新前)、updated(组件更新完成)、beforeUnmount(组件销毁前)、unmounted(组件销毁完成)。

**案例**

```
<template>    <div>        我是Page        {{username}}        <button @click="changeUsername()">按钮</button>    </div></template><script>export default {    name: 'ProjectNodePage',    data() {        return {            username:"admin"        };    },    methods:{        changeUsername(){            this.username="sssss";        }    },    beforeCreate() {        console.log("创建前");    },    created() {        console.log("创建后");    },    beforeMount() {        console.log("挂载前");    },    mounted() {        console.log("挂载后");    },    beforeUpdate() {        console.log("修改前");    },    updated() {        console.log("修改后");    },    beforeUnmount() {        console.log("销毁前");    },    unmounted() {        console.log("销毁后");    }};</script>
```

**setup函数中的生命周期**

setup函数本身替代了beforeCreate和created生命周期，因此在setup函数中不能使用beforeCreate和created生命周期，其它生命周期在每个生命周期前增加了on。

```
beforeCreate                            /created                                 /beforeMount                             onBeforeMountmounted                                 onMountedbeforeUpdate                            onBeforeUpdateupdated                                 onUpdatedbeforeUnmount                           onBeforeunmountunmounted                               onUmmounted
```

**案例**

```
<template>    <div>        我是Page        {{ username }}        <button @click="changeUsername()">按钮</button>    </div></template><script setup>import { onBeforeMount, onMounted, onBeforeUpdate, onUpdated, onBeforeUnmount, onUnmounted, toRefs, reactive } from "vue";onBeforeMount(() => {    console.log("挂载前");})onMounted(() => {    console.log("挂载后");})onBeforeUpdate(() => {    console.log("修改前");})onUpdated(() => {    console.log("修改后");})onBeforeUnmount(() => {    console.log("销毁前");})onUnmounted(() => {    console.log("销毁后");})let { username } = toRefs(reactive({ username: "admin" }))const changeUsername = () => {    username.value = "ddddddd";}</script>
```

**响应式API （setup模式）**

**reactive函数**

返回对象的响应式副本，将ref对象模式转换为基础对象。

响应式转换是“深层”的——它影响所有嵌套 property。在基于ES6 Proxy 的实现中，返回的 proxy 是不等于原始对象的。建议只使用响应式 proxy，避免依赖原始对象。

可以解包ref函数，也可以赋值自动解包

**案例**

```
import {ref,reactive} from "vue";let num=ref(100);let {num:num1}=reactive({num})//num1=100let user=ref({username:"admin",pwd:"12312312"});let {value:{username}}=reactive(user);//username=adminlet {user:{username}}=reactive({user});//username=admin
```

**案例2**

浅拷贝

```
import {ref,reactive} from "vue";let user=ref({username:"admin",pwd:"12312312"});let newUser=reactive(user.value);//aaaaaaauser.value.username="aaaaaaa";
```

**REFS API**

**ref函数**

接收一个值。并将值转换为ref对象，对象有且只有一个value属性，指向默认值

基本类型和复合类型及泛型

```
声明关键词 变量=ref(默认值);
```

当时复合类型的时候，自动调用reactive。

**案例**

```
let username=ref("admin");let user=ref({username:"adminnn"})
```

**toRef函数**

可以用来为源响应式对象上的某个 property 新创建一个 ref。然后，ref 可以被传递，它会保持对其源 property 的响应式连接。

**案例**

```
let user=reactive({username:"admin",pwd:"123123"});let newUser=toRef(user,"pwd");let user=ref({username:"admin",pwd:"123123"})let newUser=toRef(user.value,"pwd");
```

**toRefs**

将原对象的键值对进行一一转换为ref对象

**案例**

```
let user=reactive({username:"admin",pwd:"123123"});let newUser=toRefs(user)
```

**isRef函数**

判断参数是否是ref对象,返回值是布尔类型

**案例**

```
let user=reactive({username:"admin",pwd:"123123"});let user=ref({username:"admin",pwd:"123123"})
```

**unref函数**

如果参数是一个ref，则返回内部值，否则返回参数本身。是isRef(val) 的语法糖

**案例**

```
let user=ref({username:"admin",pwd:"123123"})let a=30;console.log(unref(a));
```

**setup模式下函数的定义**

**案例**

```
<template>{{username}}{{pwd}}<!-- <button @click="changeUsername">修改1</button><button @click="changeUser">修改2</button>{{user.username}}{{user.pwd}}{{user1.username}}{{user1.pwd}} --></template><script setup>import {ref,reactive,toRefs}from "vue";let {username,pwd}=toRefs(reactive({username:'admin212',pwd:123123123123}))const changeUsername=()=>{    username.value="aaaaaaa";}const changeUser=()=>{    user.username="sdddddd"}</script>
```

**组件注册**

**兼容VUE2语法**

```
<template>  <v-a></v-a></template>​<script>import vA from "./components/a.vue"export default {  components:{    vA  }}</script>
```

**Vue3本身语法**

```
<template>    <Child></Child>    <v-child></v-child>    <vChild></vChild>    <v-Child></v-Child>    <childc></childc></template><script setup>import Child from "./Child.vue";import vChild from "./vChild.vue";import childc from "./childc.vue";</script>
```

**组件通信**

**provide/inject方式**

provide和inject方式，是Vue中提供的一对API，可以实现父组件向子组件传递数据，只要是存在关系，无论几代，都可以实现传递值。

**案例**

**父组件**

```
<template>    我是父组件    {{user.username}}    <button @click="changeUsername">修改</button>    <Child></Child>    <Child1></Child1></template><script setup>import Child from "./Child.vue";import Child1 from "./Child1.vue";import {reactive,provide}from "vue";// let {username,pwd}=reactive({username:"admin",pwd:"123123123"});let user=reactive({username:"admin",pwd:"123123123"})// provide("user",{username,pwd});provide("user",user);const changeUsername=()=>{    user.username="sssssss"}</script>
```

**子组件**

```
<template>我是子组件{{username}}<button @click="changeUU">按钮</button><childchild></childchild></template><script setup>import childchild from "./childchild.vue";import {inject}from "vue";let {username,pwd}=inject("user");// let {user}=inject("user");const changeUU=()=>{    user.username="xxxxxx";}</script>
```

**计算属性(computed)**

Vue3支持Vue2的计算属性

**新增语法**

```
import {computed}from "vue";const 变量=computed(()=>{    return 返回内容; });
```

**案例**

```
<template>我是组件{{jiayun}}</template><script setup>import {computed,ref}from "vue";let num=ref(1);const jiayun=computed(()=>{    let sum=0;    for(let i=num.value;i<=100;i++){        sum+=i;    }    return sum; });</script>
```

**侦听器（watch）**

Vue3支持Vue2的侦听器

**新增语法**

```
    watch(变量名,(newValue,oldValue)=>{    }[,{deep:true}]);
```

**使用规则**

```
当监听基本数据类型的时候newValue新值，oldValue旧值当监听复合数据类型的时候newValue=oldValue都是新值。
```

**案例**

```
<template><button @click="changeUsername">修改</button>{{username}}<button @click="changeUser">修改</button>{{user.pwd}}</template><script setup>    import{ref,watch,reactive} from "vue";    let username=ref("admin");    let user=reactive({username:"admin123",pwd:123123});    const changeUsername=()=>{        username.value="aaaaaa";    }    const changeUser=()=>{        user.pwd="asxdffg";    }    watch(变量名,(newValue,oldValue)=>{    }[,{deep:true}]);    watch(username,(newValue,oldValue)=>{        console.log("我在监听");        console.log(newValue);        console.log(oldValue);    },{deep:true});    watch(user,(newObj)=>{        console.log("我在对象");        console.log(newObj);    },{deep:true});</script>
```

**h渲染函数**

在vue3中提供了h渲染函数，但是这个渲染函数需要我们手动引入，系统不会自动将其注入到render函数中

**基本语法**

```
import {h} from "vue";h(标签,{行内样式},字符串内容)h(组件名)
```

**案例**

```
import { createApp,h } from 'vue'import App from './App.vue'const app = createApp({  render(){    return h(App)  }})app.mount("#app")
```

**瞬移组件**

将组件内的内容，挂载到当前根组件之外。

**案例**

```
<!-- to后面接的是要瞬移的位置：.class或者#id或者标签名 --><teleport to="#a">     <div>喜喜</div>    <div>哈哈</div></teleport> 
```

**index.html**

```
<div id="a"></div>
```

**函数组件**

在vue3中提供了函数定义组件，函数定义组件没有响应状态和生命周期，一般情况下我们只是在函数定义组件中渲染一些简单的数据。

**注：**函数组件的定义语法，一定要返回h函数，才会是组件。

**基本语法**

```
const 变量=([形参])=>{    return h(标签,{样式},内容)}
```

**案例**

```
<template>    我是页面内容    <myChild username="admin"></myChild></template><script setup>import {h} from "vue";const myChild=(props)=>{    // return h("div",{style:{color:"red"}},"憨憨sdfsdfs")    return h("div",{style:{color:"red"}},`<h1>${props.username}</h1>`)}</script>
```

**v-if和v-for**

当v-for和v-if作用于同一标签的时候，在vue3中，v-if的优先级会高于v-for,导致无法获取循环数据，建议采用v-show或计算属性来替代；在vue2中，v-for具有比v-if更高的优先级，说简单点就是：当渲染很多数据的时候会先使用v-for将所有数据渲染出俩，然后在使用v-if砍掉不符合条件的。

**案例**

```
<template>    <table>        <tr>            <th>用户ID</th>            <th>用户名</th>            <th>密码</th>            <th>权限</th>        </tr>         <tr v-for="item of ulist" :key="item.id" v-if="(item.id)>3">            <td>{{item.id}}</td>            <td>{{item.username}}</td>            <td>{{item.pwd}}</td>            <td>{{item.isadmin}}</td>        </tr>    </table></template><script setup>import {reactive} from "vue";import {userlist} from "./index.js";let ulist=reactive(userlist.list)console.log(ulist);</script>
```

**全局变量**

全局变量,只能使用在vue挂载的渲染区。

**基本语法**

```
引用.config.globalProperties.变量=值
```

**案例**

```
const app=createApp(App);app.config.globalProperties.user={username:"addd",pwd:123123};app.config.globalProperties.username="admin";app.mount("#app");
```

### 移除特性

#### 过滤器

在vue3中移除了filter过滤器，官方建议我们使用computed或者methods来解决。

**案例**

```
<template>{{dateFormat(12313243234)}}{{newDateFormat(12313243234)}}{{dateN(123464565464)}}</template><script setup>import {computed,ref}from "vue";let newDateFormat=computed(()=>date=>new Date(date).toLocaleString().replaceAll("/","-"));let dateFormat=computed(()=>{   return (date)=>{    return new Date(date).toLocaleString().replaceAll("/","-")   }});const dateN=date=>new Date(date).toLocaleString().replaceAll("/","-");</script>
```

#### vm.$set

在vue3中移除了vm.$set，我们可以直接操作对象或数组。

#### vm.$on

在vue3中移除了$on方法，可以使用 @事件名 v-on

vm.$emit 事件触发 ，没有被移除。

#### vm.$destory

unmount()可以使用

### 路由

#### 基本使用

**下载**

```
npm i vue-router
```

**引入**

```
import {createRouter} from "vue-router";
```

**规则定义**

```
import {createWebHashHistory} from "vue-router";const router=createRouter({    history:createWebHashHistory(),    routes:[        {            path:"/",            component:()=>import("../components/08_路由的使用/Page.vue")        },        {            path:"/a",            component:()=>import("../components/08_路由的使用/Page1.vue")        },{            path:"/:pathMatch(.*)",            redirect:"/a"        }    ]    //createWebHistory(),不带#    //createWebHashHistory(),带#});export default router;
```

**使用**

```
import router from "./router/index";const app=createApp(App);app.use(router);app.mount("#app");
```

**设置出口**

```
<router-view></router-view>
```

#### 路由嵌套

**案例**

**router/index.js**

```
import {createRouter,createWebHashHistory} from "vue-router";const router=createRouter({    routes:[{        "path":"/",        "component":()=>import("../components/03_路由的嵌套/Page.vue")    },{        name:"index",        "path":"/index",        "component":()=>import("../components/03_路由的嵌套/index/List.vue"),         children:[             {                 path:"add",                 component:()=>import("../components/03_路由的嵌套/index/Add.vue")             },             {                 path:"/index/edit",                 component:()=>import("../components/03_路由的嵌套/index/Edit.vue")             },{                  path:"/index/:pathMatch(.*)*",                  redirect:"/index"             }        ]    }],    history:createWebHashHistory()})export default router;
```

设置路由出口

**index.vue**

```
<router-view></router-view>
```

#### 路由导航

**编程式导航**

```
import {useRoute,useRouter}from "vue-router";let route=useRoute();//路由元信息let router=useRouter();//路由对象
```

**常用方法**

```
router.go(num) 正数前进负数后退router.back() 后退一条router.forward() 前进1条push()replace()
```

**标签导航**

```
<router-link :to="..."> <router-link :to="..." replace> 
```

#### 路由传参

**问号传参**

**传递方式**

```
router.push("/index?username=aaaaa")router.push({path:"/index",query:{username:"bbbbbbb"}})router.push({name:"index",params:{username:"bbbbbbb"}})
```

**接收方**

```
route.query.usernameroute.params
```

**动态路由传参**

**路由规则**

```
{        name:"index",        "path":"/index/:pwd",        "component":()=>import("../components/05_路由的传参/index/List.vue")}        
```

**传递方**

```
router.push("/index/23234234234");
```

**接收方**

```
route.params
```

#### 路由守卫

**全局**

beforeEach()全局前置守卫

beforeResolve()全局解析守卫

afferEach()全局后置钩子

**路由**

beforeEnter()路由独享守卫

**组件**

beforeRouteEnter()组件进入守卫

beforeRouteUpdate()组件更新守卫

beforeRouteLeave()组件离开守卫

**导航解析流程**

导航被触发。 在失活的组件里调用 beforeRouteLeave 守卫。 调用全局的 beforeEach 守卫。 在重用的组件里调用 beforeRouteUpdate 守卫(2.2+)。 在路由配置里调用 beforeEnter。 解析异步路由组件。 在被激活的组件里调用 beforeRouteEnter。 调用全局的 beforeResolve 守卫(2.5+)。 导航被确认。 调用全局的 afterEach 钩子。 触发 DOM 更新。 调用 beforeRouteEnter 守卫中传给 next 的回调函数，创建好的组件实例会作为回调函数的参数传入。

### vuex

#### 使用步骤

1、下载

```
npm i vuex
```

2、引入

**store/index.js**

```
import {createStore} from "vuex"​
```

3、配置仓库信息

**store/index.js**

```
export const state = {}export const mutations = {}export const actions = {}export const getters = {}
```

4、创建仓库

**store/index.js**

```
const store = createStore({  state,  mutations,  actions,  getters,  modules:{  }})
```

5、导出仓库

**store/index.js**

```
export default store
```

6、引入并挂载

**main.js**

```
import { createApp } from 'vue'import App from './App.vue'import router from "./router/index";import store from "./store/index";createApp(App).use(router).use(store).mount('#app');
```

7、使用

**组件.vue**

```
import {useStore,mapActions} from "vuex";import {ref,computed} from "vue";let store=useStore();let num=ref(1);const user=computed(()=>{    return store.getters.getUser;});const changeUser=()=>{    store.commit("changeUser",{username:"cccccc",pwd:"ddddddd"});    store.dispatch("asyncChangeUser",{username:"bbbbbb",pwd:"ddddddd"})}
```

### element-plus组件库的使用

#### 下载安装

```
npm i element-plus
```

#### 完整导入

* 将element-plus组件库中提供的所有组件全部导入我们自己的vue3的项目中
*   缺点: 导致项目最终构建出来的文件体积过大, 性能不好

    > main.js

    ```
    // 导入element-plus核心文件import Element from 'element-plus';// 导入element-plus的样式文件import 'element-plus/dist/index.css';// 全局注册组件库const app=Vue.createApp(App);app.use(Element);
    ```

#### 按需导入(vite)

1.  安装一个开发依赖

    ```
    npm i unplugin-vue-components
    ```
2.  在项目配置文件中添加配置项

    > vite.config.js

    ```
    import { defineConfig } from 'vite'import vue from '@vitejs/plugin-vue'import Components from 'unplugin-vue-components/vite'import { ElementPlusResolver } from 'unplugin-vue-components/resolvers'// https://vitejs.dev/config/export default defineConfig({  plugins: [    vue(),    Components({      resolvers: [ElementPlusResolver()],    }),  ]})
    ```
3.  重启开发服务器

    ```
    npm run dev
    ```

#### 按需导入(vue-cli)

*   安装插件

    ```
    npm install unplugin-vue-components
    ```
*   修改项目配置文件(`webpack`进行配置)

    > vue.config.js

    ```
    const Components = require('unplugin-vue-components/webpack')const { ElementPlusResolver } = require('unplugin-vue-components/resolvers')module.exports={    // webpack的配置节点    configureWebpack:{        plugins: [            Components({              resolvers: [ElementPlusResolver()],            }),          ]    }}
    ```
*   重启开发服务器

    ```
    npm run serve
    ```

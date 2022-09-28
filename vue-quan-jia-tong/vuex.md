# VueX

### 简介

#### 概念

Vuex 是一个专为 Vue.js 应用程序开发的状态管理模式。它采用集中式存储管理应用的所有组件的状态，并以相应的规则保证状态以一种可预测的方式发生变化。

#### 作用

存储数据，数据的仓库。对共享数据的管理（增删改查）

#### 官网

```
https://v3.vuex.vuejs.org/zh
```

### 组成

* state，驱动应用的数据源；（数据仓库）
* view，以声明方式将 state 映射到视图；
*   actions，响应在 view上的用户输入导致的状态变化。

    ![vuex单向数据流](file:///E:/%E6%8E%88%E8%AF%BE%E5%86%85%E5%AE%B9/%E4%B8%AD%E5%85%AC/VUE%E8%AF%BE%E7%A8%8B/%E7%AC%94%E8%AE%B0/2022%E5%B9%BF%E5%B7%9EWeb%E5%85%A8%E6%A0%88%E9%9D%A2%E6%8E%88%E5%B0%B1%E4%B8%9A%E7%8F%AD10%E7%8F%AD/img/vuex%E5%8D%95%E5%90%91%E6%95%B0%E6%8D%AE%E6%B5%81.png?lastModify=1664353297)

### vuex使用

#### 安装

```
npm i vuex@3
```

#### 引入

```
import Vuex from "vuex"
```

#### 挂载

```
Vue.use(vuex);
```

#### 实例化仓库

```
let store = new Vuex.Store({option})
```

#### 绑定实例到vue实例

```
new Vue({  store:store,  render: h => h(App)}).$mount('#app')
```

**案例**

```
import Vue from 'vue'import App from './App.vue'import router from "./router"import vuex from "vuex";Vue.use(vuex);let store=new vuex.Store({});new Vue({  router,  store,  render: h => h(App),}).$mount('#app')
```

#### 数据仓库的创建

**state**

数据仓库，存放数据，存放状态。

**定义语法**

```
const store=new vuex.Store({    state: {      键名:键值    }});
```

**使用语法**

**对象模式**

```
$store.state.键名
```

**辅助函数模式**

```
import {mapState} from "vuex";computed:{    ...mapState(["键名"])    ...mapState({//        变量名:"键名"    })}
```

**注：**如果采用模块化的数据仓库，则必须使用对象的模式进行子仓库的使用

**案例**

```
  state: {    username:"admin",    pwd:"123456",    isadmin:1  }computed:{    ...mapState(["username"]),    ...mapState({        "uu":"username"    })},
```

#### 数据的修改

**mutations**

修改数据仓库的值，通过commit方法触发驱动数据修改数据，同步方法，此方法修改的值，当前页有效

![数据的修改](file:///E:/%E6%8E%88%E8%AF%BE%E5%86%85%E5%AE%B9/%E4%B8%AD%E5%85%AC/VUE%E8%AF%BE%E7%A8%8B/%E7%AC%94%E8%AE%B0/2022%E5%B9%BF%E5%B7%9EWeb%E5%85%A8%E6%A0%88%E9%9D%A2%E6%8E%88%E5%B0%B1%E4%B8%9A%E7%8F%AD10%E7%8F%AD/img/%E6%95%B0%E6%8D%AE%E7%9A%84%E4%BF%AE%E6%94%B9.png?lastModify=1664353297)

**定义语法**

```
let store = new Vuex.Store({  mutations:{    方法名(state,[参数值]){      state.属性名 = 参数值/值    }  }})
```

**使用语法**

**对象模式**

```
$store.commit('方法名',[值])
```

**辅助函数模式**

```
import {mapState} from "vuex";computed:{    ...mapMutations(["方法名"])    ...mapMutations({//        变量名:"方法名"    })}
```

**案例**

```
  mutations: {    changeUsername(state){      state.username="admin123123";    },    changeUsername1(state,newu){        state.username=newu;    }  }import {mapMutations} from "vuex";  computed:{    ...mapMutations(["changeUsername"]),    ...mapMutations({        "uu":"changeUsername1"    })}
```

**actions**

处理异步操作的数据获取，并通过mutations对仓库的state的键值对进行修改，主要用来处理异步。当前页有效

**定义语法**

```
let store = new Vuex.Store({  actions:{   async方法名(state,[参数值]){      异步操作      state.commit()    }  }})
```

**使用语法**

**对象模式**

```
$store.dispatch('方法名',[值])
```

**辅助函数模式**

```
import {mapActions} from "vuex";methods: {        ...mapActions([方法名]),        ...mapActions({        变量名:方法名        })    }
```

**案例**

```
<button @click="$store.dispatch('asyncChagePws')">异步</button>import {mapActions} from "vuex";  methods: {        ...mapActions(["asyncChagePws","asyncChagePwps"]),        ...mapActions({            cpw:"asyncChagePws",            cpp:"asyncChagePwps"        })    }actions:{    asyncChagePws(state){      setTimeout(() => {          state.commit("changeUsername1","ssssssss");      }, 2000);    },        asyncChagePwps(state,newPP){      setTimeout(() => {          state.commit("changeUsername1",newPP);      }, 2000);    }  }
```

#### 数据的批量导出

**getters**

用来批量导出数据，可以将现有数据加工处理并导出。

**定义语法**

```
let store = new Vuex.Store({  getters:{    方法名(state){    	数据的加工      	return state.属性名    }  }})
```

**使用语法**

**对象模式**

```
$store.getters.方法名
```

**辅助函数模式**

```
import {mapGetters} from "vuex";computed:{        ...mapGetters([键名]),        ...mapGetters({        变量名:键名    })
```

**案例**

```
getters:{    getUsername(state){      return `姓名：${state.username}`;    }}import {mapGetters} from 'vuex'computed:{    ...mapGetters(["getUsername"])}
```

**vueX流程**

state=>mutations=>actions=>getters

### Vuex模块化

vueX本身是数据仓库，当前后端交互的时候用来临时存储后端api接口对应的Dom，因此需要根据功能页面的视图数据进行模块化，即前端数据的组件化。

视图数据文件modules/data.js

```
const state = {}const mutations = {}const actions = {}const getters = {}export default{  state,  mutations,  actions,  getters,  // 开启命名空间  namespaced: true}
```

整合文件index.js

```
import Vue from "vue"import Vuex from "vuex"Vue.use(Vuex)​import {state,mutations,getters,actions} from "./全局文件.js"​// 引入模块import food from "./modules/模块化文件"​// 创建仓库const store = new Vuex.Store({  state,  mutations,  actions,  getters,  modules: {    food:food  }})​// 导出仓库export default store
```

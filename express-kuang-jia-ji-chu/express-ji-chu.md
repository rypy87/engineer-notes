# Express基础

## 一、简介

Express 是一个简洁、灵活的 node.js Web应用框架。

Express，提供一系列强大特性API，可以方便、快速的创建 Web 网站的服务器或 API 接口的服务器。

官网：

英语官网：http://expressjs.com/       （4.17.3）
中文官网：https://expressjs.com/zh-cn/ （4.17.1）

## 二、Express基本使用

### **创建web服务器**

#### 步骤

(1)创建package.json配置文件

```
npm init [-y]
```

(2)下载Express插件

```
npm i express
```

(3)引入express模块

(3)创建web服务器应用实例

(4)使用listen方法开启一个3000端口

```

```

### 应用对象(Application)

创建Express实例后，生成该插件的引用实例。

#### 应用对象的常用方法

##### 引用.get()

响应浏览器的GET请求。

###### 语法

```
app.get(‘路由', (req,res)=>{ 处理函数 })
```

###### 参数

参数1：客户端请求的URL地址（必须以/开头）
参数2：请求对应的处理函数

​	req：请求对象（包含了请求相关的属性与方法）
​	res：响应对象（包含了与响应相关的属性与方法）

##### 引用.post()

响应浏览器的POST请求方式

###### 语法

```
app.post(‘路由', (req,res)=>{ 处理函数 })
```

###### 参数

参数1：客户端请求的URL地址（必须以/开头）
参数2：请求对应的处理函数

​	req：请求对象（包含了请求相关的属性与方法）
​	res：响应对象（包含了与响应相关的属性与方法）

#### 案例：

##### 服务器端代码

```

```

##### 浏览器端代码

```
   
```

### 响应对象(response)

负责服务器端响应浏览器请求的对象。

浏览器相关信息参数常用对照表：https://tool.oschina.net/commons

#### 响应对象常用方法

##### 引用.send()

结束响应并向浏览器端发送数据内容，自动解析中文字。

###### 语法：

```
res.send( 字符串/json格式对象 )
```

##### 引用.sendFile()

结束响应并，将文件类型的资源返回给浏览器。

###### 语法

```
res.sendFile( 文件绝对路径 )
```

##### 引用.status()

设置响应的状态码。

###### 语法

```
res.status(状态码)
```

##### 引用.type()

设置响应内容的类型。

###### 语法

```
res.status(资源类型)
```

#### 案例：

```

```

### 请求对象(request)

服务器端获取浏览器端的参数对象。

#### 常用属性

##### req.query

获取浏览器端GET请求方式，发送的参数。

**案例**

```

```

##### req.params

动态路由(冒号传参)，以动态路由的形式传递参数。

**案例：**

```

```

##### req.body

获取浏览器端POST请求方式，发送的参数，需要结合相关中间件一起使用。

## 三、项目工具

### nodemon

在编写调试 Node.js 项目的时候，如果修改了项目的代码，则需要频繁的重新启动项目，nodemon工具，它能够监听项目文件的变动，当代码被修改后，nodemon 会自动帮我们重启项目，极大方便了开发和调试。

**安装命令**

```
npm i nodemon -g
```

### Rest Client

接口调试工具，基于VScode的接口测试的工具。

**使用步骤**

(1)安装REST Client插件

![REST Client插件](E:\授课内容\中公\node课程\笔记\img\REST Client插件.png)

(2)创建后缀名为 .http 文件，书写REST接口调试语法 

![REST Client插件语法](E:\授课内容\中公\node课程\笔记\img\REST Client插件语法.png)

**案例：**文件语法

```

```

## 四、Express路由

广义上来讲，路由就是映射关系。不同的访问地址对应不同的路由，每一次互联网请求都对应一个请求处理的函数。

### 路由组成

Express 的路由分 3 部分组成，分别是请求类型、请求路由名字、处理函数

#### 基本语法：

```
引用.METHOD(path, callback [, callback ...])
```

**语法和参数解释**

METHOD：请求方式的响应方法，如get，post，put等 。
PATH：请求路由的名字 
callback：回调函数，当请求方式和路由匹配后，用于响应该请求所执行的算法。

### 路由匹配流程

(1)当一个请求发送到服务器端后，首先进行请求方式和响应方法的匹配，再进行路由的匹配，当都匹配成功，则会通过回调函数，执行相应算法，响应浏览器所需内容。
(2)路由匹配顺序是从上到下依次匹配，匹配第一个满足条件的路由。

![路由匹配流程](E:\授课内容\中公\node课程\笔记\img\路由匹配流程.png)

Express支持Http请求方式的方法

![Express支持Htpp请求方式](E:\授课内容\中公\node课程\笔记\img\Express支持Htpp请求方式.png)

**案例**

```

```

### 子路由

项目的开发过程中，为了方便路由层的管理，可以将路由以功能需求进行模块化分类管理，这个过程称为路由的模块化，模块化的单个路由文件称为子路由。

#### 语法：

```
let router=express.Router(); 
```

##### 子路由的创建步骤

(1)创建子路由模块文件
(2)使用express.Router() 方法创建子路由实例对象
(3)给子路由挂载对应的响应方法
(4)使用module.exports将子路由实例对象抛出
(5)使用 app.use() 方法挂载子路由模块

####  应用对象.use() 

将子路由/中间件挂载到指定路由上。

```
app.use([path,] callback [, callback...])
```

#### 案例：

##### 子路由文件1

```

```

##### 子路由文件2

```

```

##### 主路由文件

```

```

## 五、中间件

### **概念**

中间件（Middleware ），指业务流程的中间处理环节。也是特殊的路由，通常指在处理请求过程中，需要对响应数据进行多次加工处理时，采用中间件加工模式。

![中间件](E:\授课内容\中公\node课程\笔记\img\中间件.png)

### **好处**

更有效的实现业务逻辑，提升开发效率，生成高品质的响应资源。

### 中间件执行流程：

当一个请求到达Express的服务器后，可以通过连续调用多个中间件，对这次请求进行预处理。但是必须要有一个最终的匹配路由进行响应给客户端结果。

![中间件执行过程](E:\授课内容\中公\node课程\笔记\img\中间件执行过程.png)

### 中间件的使用

#### 语法

```
app.use([前缀,]中间件函数)
//中间函数
([arg,]req,res,next)=>{
          //next，移交响应控制权。当中间件处理完毕以后要进行下一个处理环节，但作为特殊的路由的时候next可以省略。
}
```

#### 案例

##### 三个参数的中间件

```

```

##### 四个参数的中间件

```

```

##### 特殊的路由

```

```

### 中间件的前缀

在某些情况下有些请求是不需要经过中间件处理的，因此可以给中间件加上特定路由前缀，达到按规则过滤响应。

```

```

### 使用中间件注意事项： 

(1)必须在路由之前注册中间件，错误中间件除外
(2)对于客户端的请求，可以连续使用多个中间件进行处理
(3)中间件的业务执行完之后， next() 函数一定要执行
(4)连续使用多个中间件时，多个中间件之间，共享req和res对象

### 中间件分类

#### 应用级别中间件：

绑定在主路由的中间件，叫做应用级中间件。

#### 路由级中间件

路由级中间件和应用级中间件类似，只不过是它绑定对象为express.Router()。

#### 错误中间件：

错误级别中间件是用来捕获整个项目中发生的异常/错误，从而防止项目异常崩溃的问题，主要有404错误和逻辑错误。错误级别中间件的处理函数中，必须有 4 个形参，形参顺序从前到后，分别是 err, req, res, next。

**案例：处理404错误**

当请求没有匹配到响应路由时，则会匹配此中间件，把它称为404中间件，也叫404资源不存在响应。

```

```

**案例：处理服务器运行时错误**

在代码运行时，服务器可能会出现代码运行时错误，这类错误是由服务器运行时产生，这类错误叫服务器运行时错误。

```

```

**注：**错误级别的中间件，必须在应用级中间件的最后面，防止漏掉捕获！

#### 内置中间件：

Express框架API自带的一些常用中间件，被称作内置中间件。

##### static

负责在 Express 应用中提托管静态资源的中间件

###### 语法

```
引用.static(静态资源路径)
```

**注：**当托管静态资源时，如果静态资源的根目录下存在index.html，则默认会将index.html绑定给首页路由“ / ”，且静态资源的根目录不会出现的访问URL中。

**案例**

```
//express.static(静态资源路径),部署项目中的静态资源，静态资源服务器。
//静态资源服务器默认会将当前路径下的index.html绑定给首页路由，将文件/文件夹的名字自动转换为路由
app.use(express.static(path.join(__dirname,"public")));//将public文件夹下所有的文件部署为静态资源。
```

##### json

将request请求对象有效内容解析为json格式数据

###### 语法

```
引用.json()
```

##### urlencoded

将request请求对象传入的post请求方式的urlencoded格式数据解析，并进行解码操作。

```
引用.urlencoded({extended:false}) 
```

**案例：**

```
//处理Post请求参数的中间件
app.use(express.urlencoded({extended:true}));

//更好的处理JSON格式的数据
app.use(express.json());
```

#### 自定义中间件（第三方中间件）：

非 Express 框架内置的，而是由第三方开发出来的中间件，叫做第三方中间件。
本质上第三方中间件是npm上开源的模块包。所以可以通过npm下载工具获取第三方中间件。

## 六、常用第三方中间件

### 处理cookie中间件

#### cookie的概念 

cookie是服务器向客户端发送的一小份数据，并将数据存放在客户端。用户记录客户与服务器交互的一些信息。为下一次访问提供良好的服务。

#### cookie的特点

(1)不设置有效时间，浏览器关闭即销毁。
(2)大小限制（4KB）
(3)存储在客户端
(4)单个域名下数量最多不能超过50个cookie
(5)cookie是键值对的形式，值只能是字符串
(6)一般情况下不同浏览器和不同项目之间cookie不共享，但同一项目cookie共享。

#### cookie实现原理

![cookie创建过程](E:\授课内容\中公\node课程\笔记\img\cookie创建过程.png)

(1)客户端发送一个请求到服务器
(2)服务器发送一个响应到客户端，其中包含Set-Cookie的头部，cookie就是通过该字段传递给客户端，并自动保存。

![Set-Cookie键值对](E:\授课内容\中公\node课程\笔记\img\Set-Cookie键值对.png)

![图形化查看cookie](E:\授课内容\中公\node课程\笔记\img\图形化查看cookie.png)

（3）当本地存储了cookie以后，下次访问相同服务器地址，cookie内容会自动携带。

![请求中携带的cookie](E:\授课内容\中公\node课程\笔记\img\请求中携带的cookie.png)

#### cookie的使用

##### 安装

```
npm i cookie-parser
```

##### 插件的绑定

```
const cookieParser = require("cookie-parser");
app.use(cookieParser([密匙]));//以中间件的形式绑定插件
```

##### cookie的设置语法

```
res.cookie(key,value[,option])
```

**参数：**

option:

​	expires：过期时间（秒）,设置失效的时间点

​	maxAge：最大失效时间（毫秒)，设置多少毫秒后失效

​	signed： 表示是否签名（加密）,设为 true 会对当前cookie 签名加密，需要用res.signedCookies 获取,且需要在绑定中间件的时候设置密匙。未签名加密则用res.cookies获取。

##### 获取cookie

```
res.cookies//未签名cookie获取
res.signedCookies//获取签名cookie
```

##### 服务器端代码案例

```

```

### 处理Session中间件

#### session的概念

session是另一种记录用户信息的机制，不同于cookie的是，session保存在客户端浏览器中，当浏览器打开创建当前session，浏览器关闭自动销毁。

![session实例图](E:\授课内容\中公\node课程\笔记\img\session实例图.png)

#### session特点

(1)session临时存储在浏览器运行时。
(2)依赖cookie存储，存放SessionID，通过客户端的SessionID标识符区分session，判别是否为相同Session。
(3)可以存储任意类型。
(4)session没有大小限。

#### session应用场景：

cookie能做的sessioin都能做，且可以实现访问次数。 

#### session实现原理

(1)客户端发送一个请求到服务器
(2)服务器发送一个响应到客户端，其中包含Set-Cookie的头部(同时包含sessionID标识信息，服务器也会开启此用户的session数据区)
(3)客户端保存sessionID标识的cookie，之后向服务器发送请求时，http请求中会包含一个Cookie的头部 
(4)服务器根据客户端传过来的sessionID标识进行处理，然后返回响应数据。

![session创建过程](E:\授课内容\中公\node课程\笔记\img\session创建过程.png)

![session交互过程](E:\授课内容\中公\node课程\笔记\img\session交互过程.png)

#### session的使用

##### 安装

```
npm i cookie-session
```

##### 插件的绑定

```
const cookieSession = require("cookie-session");
app.use(cookieSession({
    name:"sessionText",
    keys:["aaa","bbb","ccc"],
    maxAge:1000 * 60 * 3,
}));//以中间件的形式绑定插件
```

**参数：**

name：设置的Cookie的名称，默认为express:sess。
keys：是个数组，用于签名和验证Cookie值的键列表。设置Cookie时始终使用签名keys[0]，验证时使用其它密钥。
secret：通过设置的 secret 字符串，来计算 hash 值并放在 cookie 中，使产生的 signedCookie 防篡改，如果没有设置keys，将使用secret作为单一密钥。
maxAge：设置有效时间，为毫秒数
expires：设置cookie的过期日期，是一个Date对象，默认在会话结束时过期。 

##### 存储session的语法

```
req.session.变量名=值
```

##### 获取session

```
req.session.变量名
```

##### 服务器端代码案例

```

```

### 表单数据处理中间件

该中间件可以处理from表单提交的一切数据，包括上传文件功能，即把本地的文件上传到服务器。

#### 安装

```
npm i formidable@latest
```

#### 使用步骤

(1)客户端创建form表单
(2)表单的提交方式必须为POST
(3)设置数据传输格式 enctype="multipart/form-data“
(4)服务器端借助formidable模块接收文件
(5)服务器再对接收过来的文件进行处理
(6)服务器处理完毕以后响应客户端结果

#### 案例

##### 浏览器端代码

```
 
```

##### 服务器端代码

```

```

### 表单数据验证中间件

验证表单数据格式合法性的中间件。

#### 安装

```
npm i validator
```

#### 案例

```

```

### 表单校验码中间件

服务器端生成表单校验码的中间件。

#### 安装

```
npm i svg-captcha
```

#### 案例

```

```

### 跨域中间件

#### 跨域概念

当使用Ajax请求url时，如果协议、域名、端口三者之间任意一个与当前页面url不同即为跨域。

#### 跨域种类

![跨域种类](E:\授课内容\中公\node课程\笔记\img\跨域种类.png)

#### 跨域错误信息

![跨域报错](E:\授课内容\中公\node课程\笔记\img\跨域报错.png)

#### 解决跨域方案

##### CORS跨域资源共享方案

###### 概念

CORS （Cross-Origin Resource Sharing，跨域资源共享）由一系列 HTTP 响应头组成，这些 HTTP 响应头决定服务器是否阻止前端Ajax代码跨域获取资源。CORS是在服务器端进行配置。

![跨域过程解析](E:\授课内容\中公\node课程\笔记\img\跨域过程解析.png)

###### 服务器端配置cors

**Access-Control-Allow-Origin**

设置接口的请求地址。默认*

**语法：**

```
 res.header('Access-Control-Allow-Origin', '*');
```

**Access-Control-Allow-Methods**

设置接收的请求方式，默认只有GET和POST

**语法：**

```
res.header('Access-Control-Allow-Methods', '*');
```

###### CORS中间件

**使用步骤**

1、下载cors中间件

```
 npm i cors 
```

2、引入中间件

```
const cors = require('cors');
```

3、绑定中间件

```
app.use(cors());
```

##### JSONP解决跨域

JSONP，即JSON + padding，把服务端传过来的json数据 padding（填充）在html页面标签中。JSPNP模式只能发送get请求。

```
<button id="btn1">按钮</button>
    <script>
        function jsonp() {
            let script = document.createElement('script');
            script.type = 'text/javascript';
            // 传参并指定回调执行函数为backFn
            script.src = 'http://localhost:1234/?uid=100&callback=callbackFn';
            document.head.appendChild(script);
        }
        // 回调执行函数
        function callbackFn(res) {
            alert(JSON.stringify(res));
        }
        document.getElementById('btn1').addEventListener('click',()=>{
            jsonp();
        });
</script>
```

### 时间格式化中间件

根据参数格式生成相应的时间字符串。

#### 安装

```
npm i time-stamp
```

#### 服务器端代码

```
const tm=require("time-stamp");
console.log(tm("YYYYMMDDHHmmssms"));
```

### 唯一字符串生成中间件

根据特定编码格式生成唯一字符串。

#### 安装

```
npm i uuid
```

#### 服务器端代码（服务器端使用）

```
const {v4:uuid}=require("uuid");
console.log(uuid());
```

### 模板引擎中间件(EJS)

EJS是一套简单的模板语言。它是服务器端转义语言，是由标签和 JavaScript 语法语法组成。

#### 安装

```
npm  i ejs 
```

#### 服务器端使用步骤

(1)下载  ejs 
(2)在项目中设置ejs模板引擎 

```
app.set("view engine",“ejs"); 
```

(3)在项目根目录下创建views文件夹 ，也可以通过set方法设置根目录

```
app.set(‘views’,“./view”); 
```

(4)在views文件夹下创建模板文件，注意必须以 .ejs为后缀名

#### EJS服务器端渲染语法

```
res.render( '模板名称' ,[ data ])
```

**参数：**

(1)参数1为模板名称不需要添加后缀，会自动寻找对应名称的.ejs文件  
(2)参数2为可选参数，向模板中传递的数据，必须是一个JSON格式对象

#### EJS页面标签语法

##### 输出变量语法：

```
<%=变量名 %>
<%-变量名 %>
```

##### 分支语法：

```
<% if( 条件 ){%>
	条件代码
<% }else{ %>   
	条件代码
 <% } %>
```

##### 循环语法：

```
<% for(let i=0;i<数组.length;i++){ %>  
	循环代码
<% }%>
```

##### 包含文件语法：

```
<%- include('公共文件路径')  %>
```

#### 服务器端代码

```

```

#### 页面代码

```

```

## 七、Express脚手架

express-generator（又称为脚手架工具） 可以快速创建一个应用的骨架。

### 脚手架安装步骤

1、安装全局express-generator工具

```sh
 npm i express-generator -g
```

2、使用脚手架初始化项目

```sh
express --view=ejs 项目名
```

	--view=ejs : 你的项目使用ejs模板引擎

3、进入目录, 安装所有需要的模块

```
cd 项目包名 
npm i
```

4、启动项目

```
npm  start   
完整的命令叫 ： npm run start
注意：start是一个特殊的名字。所以只这个start可以省略run。
```

注：上面的命令是在package.json文件内配置的script属性。

5、浏览器访问 http://localhost:3000

### 目录和文件介绍

app.js : 入口文件

views: 模板文件夹

routes:子路由存放文件夹

public:静态资源存放文件夹

bin/www：启动的文件

package.json：项目的配置文件

## 八、KOA脚手架

Koa 是一个新的 web 框架，由 Express 幕后的原班人马打造， 致力于成为 web 应用和 API 开发领域中的一个更小、更富有表现力、更健壮的基石。 通过利用 async 函数，Koa 帮你丢弃回调函数，并有力地增强错误处理。 Koa 并没有捆绑任何中间件， 而是提供了一套优雅的方法，帮助您快速而愉快地编写服务端应用程序。

### 脚手架安装步骤

1、安装全局koa-generator工具

```js
npm i koa-generator -g 
```

2、使用脚手架初始化项目

 ```
koa2  项目包名 
 ```

说明：如果需要ejs模板, 在koa2 后 加 -e参数：

```
koa2 -e --ejs  项目包名 
```

3、进入目录, 安装所有需要的模块

```
cd 项目包名 
npm i
```

4、启动项目

```
npm start
```

5、浏览器访问 http://localhost:3000

### 目录及文件介绍

(1)bin/www：启动文件
(2)app.js：入口文件
(3)public：静态资源文件夹
(4)routes：模块化路由文件夹
(5)views：模板文件夹
(6)package.json：项目配置文件

### koa与express区别：

(1)koa 把 express 中内置的 router、view 等功能都移除了，使得框架本身更轻量化。
(2)Koa使用了Promise配合异步函数, 来组合各种中间件使用, 做到真正的异步代码同步化使用。

## 前后端数据交互总结

| 请求方法 | 编码格式                            | 前端要传输的数据格式                                    | 后端如何获取                          | 应用场景 |
| -------- | ----------------------------------- | ------------------------------------------------------- | ------------------------------------- | -------- |
| GET      | url地址后面（querystring）          | url?key1=value1&key2=value2                             | 不需要中间件:req.query                | 获取数据 |
| POST     | applicaion/x-www-form-urlencoded    | form-data: key1=value1&key2=value2                      | express.urlencoded( { extend:true } ) | 提交数据 |
| POST     | applicaion/json（只能通过ajax）     | request-payload:  '{ "key1":"value1","key2":"value2" }' | express.json()                        |          |
| POST     | mutilpart/form-data（可以使用表单） | 文件流                                                  |                                       | 文件上传 |
| DELETE   | 同post                              |                                                         |                                       | 删除数据 |
| PUT      | 同post                              |                                                         |                                       | 更新数据 |


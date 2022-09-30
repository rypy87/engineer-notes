# webpack

### 简介

#### 概念

webpack，是一个现代 JavaScript 应用程序的静态模块打包工具(module bundler)。当 webpack 处理应用程序时，它会在内部构建一个依赖图(dependency graph)，此依赖图对应映射到项目所需的每个模块，并生成一个或多个 bundle。

#### 官网

英文网站：[https://webpack.js.org/](https://webpack.js.org/)

中文网站：[https://webpack.docschina.org/](https://webpack.docschina.org/)

#### 最新版本

5.74.0

#### 功能

Webpack不仅仅具备编译、压缩、合并功能，同时还具备模块化开发和组件式开发的优点，目前流行的很多前端框架的脚手架都是基于webpack，如vue2.0、reactjs等。

#### 优点

1.可以完成依赖管理、动态打包、代码分离、按需加载、代码压缩、静态资源压缩、缓存等配置；

2.扩展性强，插件机制完善，开发者可自定义插件、loader；

3.社区相对庞大，更新速度快，轮子丰富；

4.webpack 通过依赖关系图可以获取非代码资源，如 images 或 web 字体等。并会把它们作为依赖提供给应用程序。

5.每个模块都可以明确表述它自身的依赖，在打包时可根据依赖进行打包，避免打包未使用的模块。

#### 目的

* 分离开发环境、生产环境配置；
* 模块化开发；
* sourceMap 定位警告和错误；
* 动态生成引入 bundle.js 的 HTML5 文件；
* 实时编译；
* 封装编译、打包命令。

#### 安装

安装工程的webpack

```
npm i  webpack -D
```

安装全局webpack运行环境

```
npm i webpack-cli -g
```

### 基本配置概念

#### 基本语法格式

```
module.exports = {    entry:入口,    output:{        出口    },    module: {         rules: [             加载器规则         ]    },    plugins:[        插件    ],    mode:模式}
```

#### 入口(Entry)

入口（Entry），工程的入口文件，通过配置 entry 属性，来指定一个入口起点或多个入口起点。默认起点路径为 ./src/index.js。

webpack中入口的形式分为两种，单入口形式和对象入口形式

**单入口形式：**

**语法**

```
entry: string | Array<string>
```

**字符串**

```
module.exports={    entry:"./index.js"}
```

**数组**

数组的形式可以合并入口文件。

```
module.exports={    entry:["./index.js","./index1.js"]}
```

**对象入口形式**

对象入口形式，可配置多入口，可配置出口文件名/基于dist文件夹的相对路径，灵活可扩展，可以按环境构建分离，比如手机端、浏览器端等。

**语法**

```
entry:{    [entryChunkName:string]: string|Array<string>    [entryChunkPath/entryChunkName:string]: string|Array<string>    }，
```

**案例**

```
module.exports={    entry:{        //"../../../../aa":"./index.js"        "b":["./index.js"],        "c":["./index.js"]    }}
```

#### 出口(output)

出口(Output),配置Webpack打包后的资源bundles输出到路径及输出文件的名字。默认输出路径是./dist/main.js。

**注：**

即使可以存在多个入口起点，但只指定一个输出配置。

生产环境下用过contenthash 值来区分版本和变动，从而可以达到清缓存的效果。

**配置参数**

● filename: 配置输出文件名，可添加相对路径配置，可使用占位符，常用占位符有以下5种形式：&#x20;

1）name:模块在入口时配置的输出文件名，默认值是main.js。注：此模式只能在对象中使用。&#x20;

2）id: 内部模块标识符(ID序列号)&#x20;

3）hash: 模块标识符的hash值，跟工程内容相关，注：它只能输出一个入口文件&#x20;

4）chunkhash: chunk内容的hash值，注：可以根据对象的输入文件个数生成多个文件&#x20;

5）contenthash：使用文件内容的 md4-hash。 ● path: 文件的输出路径，必须是绝对地址，支持跨盘符。

● clean：设置编译前是否清楚目录

**案例1**

```
module.exports={    entry:"./index.js",    output:{        filename:"../../aa.js"//设置出口文件的相对于dist的相对路径和文件名/文件名    }}
```

**案例2**

```
module.exports={    entry:"./index.js",    output:{        filename:"./aa.js",//设置出口文件的相对于dist的相对路径和文件名/文件名        path:"E://a"//设置出口文件的路径，其参数是绝对路径,但不能直接接盘符，可以接文件夹，如果文件夹不存在，会自动创建.    }}
```

**案例3**

```
module.exports={    entry:"./index.js",    output:{        filename:"[chunkhash].js"//设置出口文件的相对于dist的相对路径和文件名/文件名    }}
```

#### 加载器(Loader)

webpack5本身只能加载Javascript文件和json文件，Loader可以让webpack处理不同类型的模块。

配置loader必须的属性有两个： test 属性，用于标识出应该被对应的 loader 进行转换的某个或某些文件。 use 属性，表示进行转换时，应该使用哪个 loader。 注：上面两个属性需要定义到module.rules下。且加载顺序是从右到左（或从下到上），执行。

#### 插件(Plugins)

插件（Plugins）在webpack打包过程中可以用于执行范围更广的任务，比如代码分割、静态资源处理、环境变量的注入，清除打包目录、复制静态文件、抽取css文件等。webpack自身也是用插件系统构建起来的。

#### 模式(Mode)

webpack5中增加了模式的概念，通过设置模块(mode)参数可以启用相应的模式优化，参数值为development(开发模式)，production(产品模式，默认值)或者none(空模式)。

#### 解析器（resolve）

**常用配置属性**

**alias**

配置解析器别名，简化模块引入代码量。

**extensions**

配置解析后缀，方便引入模块时不带文件后缀

**symlinks**

配置npm link是否生效，禁用可以提升编译速度

**案例**

```
module.exports = {  resolve: {    extensions: ['.js','.jsx','.vue','.ts','.tsx','.json','.d.ts'],    alias: {      '@': './',    },    symlinks: false,  }}
```

#### 优化器（optimization）

optimization 用于自定义 webpack 的内置优化配置，一般用于生产模式提升性能，

**常用配置属性**

**minimize**

设置是否压缩bundle。

**minimizer**

配置压缩工具插件，如，css-minimizer-webpack-plugin，TerserPlugin、OptimizeCSSAssetsPlugin等。

**splitChunks**

拆分bundle。

**runtimeChunk**

设置是否将所有生成 chunk 之间共享的运行时文件拆分出来。

**案例**

```
module.exports = {  optimization: {    minimizer: [      new CssMinimizerPlugin(),    ],    splitChunks: {      chunks: 'all',      // 重复打包问题      cacheGroups:{        vendors:{           //node_modules里的代码          test: /[\\/]node_modules[\\/]/,          chunks: "all",          //chunks name          name: 'vendors',           //优先级          priority: 10,           enforce: true         }      }    },  },}
```

### webpack基本使用

在构建项目的过程中两种模式，即开发模式和产品模式，两种模式下的都拥有独立的webpack配置，通常开发模式（webapck.dev.js）,产品模式（webpack.prod.js），两种模式的配置会带来一个很严重的问题，配置信息冗余，因此，在遵循不重复原则，两者配置相同部分采用通用文件配置（webpack.common.js）。

#### 配置通用配置插件

**安装**

```
npm i webpack-merge -D
```

**案例**

**webpack.common.js**

```
module.exports = {} 
```

**webpack.dev.js**

```
const { merge } = require('webpack-merge')const common = require('./webpack.common')module.exports = merge(common, {}) 
```

**webpack.prod.js**

```
const { merge } = require('webpack-merge')const common = require('./webpack.common')module.exports = merge(common, {}) 
```

#### 配置入口信息

**webpack.common.js**

```
module.exports = {  entry: {    index: './src/index.js',  },}
```

#### 配置出口信息和模式

**webpack.dev.js**

```
const { merge } = require('webpack-merge');const common = require('./webpack.common');const path = require("path");module.exports = merge(common, {  output: {    filename: '[name].bundle.js',    path: path.resolve(__dirname,"dist"),    clean: true  },  mode: 'development',})
```

**webpack.prod.js**

```
const { merge } = require('webpack-merge');const common = require('./webpack.common');const path = require("path");module.exports = merge(common, {  output: {    filename: '[name].[contenthash].bundle.js',    path: path.resolve(__dirname,"dist"),    clean: true  },  mode: 'production',})
```

#### 配置追踪错误和异常

使用source-map追踪 error 和 warning，将编译后的代码映射回原始源代码。

```
module.exports =  merge(common, {  mode: 'development',  devtool: 'eval-cheap-module-source-map'})
```

注：建议只有在开发环境下开启source-map，编译调试。

#### 配置运行命令

通过 cross-env 配置环境变量，区分开发模式和产品模式的运行命令。

**安装**

```
npm i cross-env -D
```

**配置package.json**

```
{    "scripts": {        "dev": "cross-env NODE_ENV=development webpack serve --open --config config/webpack.dev.js",        "build": "cross-env NODE_ENV=production webpack --config config/webpack.prod.js"      },}
```

**运行命令**

**本地构建**

```
npm run dev
```

**生产打包**

```
npm run build
```

### webpack高级使用

#### 自动打包js和JSON文件

webpack4.0开始，可以不需要配置webpack.config.js文件，直接可以打包js文件和Json文件。只需要按默认入口路径./src/index.js，配置好入口即可。默认出口路径是dist/main.js

**打包js文件**

**index.js**

```
let user={    username:"admin",    pwd:"123456"};module.exports=user;
```

**打包JSON文件**

**user.json**

```
{  "username":"rypy"}
```

**index.js**

```
const userData=require("../json/user.json");module.exports={    userData}
```

#### 打包HTML文件

**html-webpack-plugin插件**

1、自动生成一个压缩后的HTML5的页面，并自动引入打包后的js文件

2、可以讲模板为h4的页面转换为html5的页面

3、可以处理ejs页面的打包和压缩

**安装**

```
npm i html-webpack-plugin -D
```

**参数配置**

● title 设置浏览器title标签的名字，默认是 Webpack App。

● filename 就是输出html文件的文件名，默认是index.html

● template 指定你生成的文件所依赖哪一个html文件模板，模板类型可以是html、ejs等。但是要注意的是，如果想使用自定义的模板文件的时候，你需要安装对应的loader，默认值：支持ejs和html。

● inject :{Boolean|String} true 默认值，script标签位于html文件的 head 标签中 body ：script标签位于html文件的 body 底部 head ：script标签位于html文件的 head中 false ：不插入生成的js文件

● minify {Boolean|Object} 使用minify会对生成的html文件进行压缩。如果当前模式是production，默认值是true,否则是false。html-webpack-plugin内部集成了html-minifier,因此，还可以对minify进行配置。

**常用minify属性**

**案例**

```
module.exports={    plugins:[        new hwp({            title:"我是title",//设置自动生成HTML文档标题，默认值是Webpack App            filename:"aaa.html",//设置生成的文件名,需要带后缀，默认值是index.html            template:"./index2.html",//设置HTMl模板,当有模板存在的时候，title属性自动失效。            inject:true,//设置script标签的引入位置，默认是head,取值是head,body,true,false            //设置是否压缩HTML文件，可以指定某些压缩条件进行部分压缩。           //minify:false           minify:{                collapseWhitespace:true,                useShortDoctype:true,                removeComments:true           }        })    ],    mode:"production"}
```

#### 打包css到js文件中

css-loader加载器是负责解析css样式文件。

style-loader加载器是负责将css样式以内部样式表的形式嵌入到js代码中。

**安装**

```
npm i style-loader css-loader -D
```

**案例**

```
const hwp=require("html-webpack-plugin");module.exports={    entry:"./css/index.css",    module:{        rules:[{            test:/\.css$/i,//设置加载器可以加载的文件后缀名，通常使用正则表达式            use:["style-loader","css-loader"]        }]    },    plugins:[        new hwp()    ],    mode:"production"}
```

#### 从js中抽离css文件

MiniCssExtractPlugin，可以将打包后的css文件以link的形式引入html页面中。合并多个css文件输出一个css。

**安装**

```
npm i mini-css-extract-plugin -D
```

**案例**

```
const miniCss=require("mini-css-extract-plugin");const hwp=require("html-webpack-plugin");module.exports={    entry:["./css/index.css","./css/index1.css"],    plugins:[        new hwp(),        new miniCss({            filename:"./aaa/index.css"//设置生成的css文件名/相对路径，注：如果设置了文件名则html中不会自动引入。        })    ],    module:{        rules:[{            test:/\.css$/i,            use:[miniCss.loader,"css-loader"]        }]    },    mode:"production"}
```

#### 压缩css文件

css-minimizer-webpack-plugin插件，压缩css,合并相同页面效果/页面元素样式的功能。

**安装**

```
npm i css-minimizer-webpack-plugin  -D
```

**案例**

```
const minim=require("css-minimizer-webpack-plugin");const minic=require("mini-css-extract-plugin");module.exports={    entry:"./css/index.css",    module:{        rules:[{            test:/\.css$/i,            use:[minic.loader,"css-loader"]        }]    },    plugins:[        new minic(),        new minim()    ],    mode:"production"}
```

#### 打包less样式文件

less-loader加载器，可以将less样式文件，编译合并到css样式文件中。

**安装**

```
npm i less less-loader -D
```

**案例**

```
const minin=require("css-minimizer-webpack-plugin");const minic=require("mini-css-extract-plugin");module.exports={    entry:["./less/index.less","./css/index.css"],    module:{        rules:[{            //   /\.less|\.css$/i            test:/\.(less|css)$/i,            use:[minic.loader,"css-loader","less-loader"]        }]    },    plugins:[        new minic(),        new minin(),    ],    mode:"production"}
```

#### 打包样式中的图片

新版的webpack5中打包图片采用asset module(资源模块)，它是是一种模块类型，它允许使用资源文件（字体，图标等）而无需配置额外 loader。

**type配置参数：**

**案例**

```
const hwp=require("html-webpack-plugin");module.exports={    entry:"./css/index.css",    module:{        rules:[            {                test:/\.(jpg|jpeg|png|gif|bmp|webp)$/i,                type:"asset/inline"            },{                test:/\.css$/i,                use:["style-loader","css-loader"]            }        ]    },    plugins:[        new hwp()    ],    mode:"production"}
```

#### 将下载的插件打包压缩到js文件中

webpack支持可以将node下载的插件打包集成新的压缩文件中。比如可以将jquery插件模块，打包集成。

**安装**

```
npm i jquery -D
```

**案例**

**index.js**

```
$("#btn").on("click",()=>{    alert("弹窗");});
```

**webpack.config.js**

```
const hwp=require("html-webpack-plugin");const webpack=require("webpack");//注：使用webpack内置插件，需要将webpack引入。module.exports={    entry:"./index.js",    plugins:[        new hwp({            template:"./index.html"        }),        //使用webpack的内置插件，将下载的插件在打包的过程中自动打包到项目中        new webpack.ProvidePlugin({            $:"jquery"        })    ],    mode:"production"}
```

#### Web Server的使用

**插件安装**

```
npm i webpack-dev-server -g
```

webpack-dev-server ，默认开启压缩模式 conpress: true，每个静态文件文件开启gzip压缩。

**插件的应用**

**热更新**

webpack-dev-server，默认可以开启开发模式的服务器，可以将当前目录下的index.html自动设置为首页。 新版的webpack-dev-server，自动可以热更新入口文件的内容。 页面的热更新操作，指使用代码更改页面样式可以试试看到效果，即动态特效实时生效。

**案例**

```
const hwp=require("html-webpack-plugin");module.exports={    devServer:{        host:"127.0.0.2",        port:"1222",        open:true    },    plugins:[        new hwp({            template:"./index.html"        })    ],    mode:'production'}
```

**反向代理**

webpack-dev-server，插件可以将远程服务器的数据，代理到本地服务器，从而解决跨域的问题。

**首页路由的方向代理**

```
module.exports={    devServer:{        host:"192.168.1.74",        port:'1235',        open:true,        proxy:{            '/':{                target:"http://www.icbc.com.cn",                changeOrigin:true,                secure:false            }        }    },    mode:"production"}
```

**将本地路由代理到指定路由**

```
module.exports={    devServer:{        host:"127.0.0.6",        port:"1236",        open:true,        proxy:{            "/guonei":{                target:"http://news.baidu.com/",                changeOrigin:true,                secure:false            },            "/world":{                target:'https://news.sina.com.cn/',                changeOrigin:true,                secure:false            },            "/nba":{                target:"https://sports.qq.com/",                changeOrigin:true,                secure:false            }        }    },    mode:"production"}
```

**自定义本地路由访问所需路由**

```
module.exports={    devServer:{        host:"192.168.1.74",        port:"1237",        open:true,        proxy:{            '/a':{                target:'http://www.baidu.com',                changeOrigin:true,                secure:false,                pathRewrite:{"/a":""}            },            '/b':{                target:'http://www.sina.com.cn',                changeOrigin:true,                secure:false,                pathRewrite:{"/b":""}            },             '/c':{                target:'http://www.qq.com',                changeOrigin:true,                secure:false,                pathRewrite:{"/c":""}            }        }    },    mode:"production"}
```

**指定开放服务器的路由**

```
module.exports={    devServer:{        host:'127.0.0.1',        port:"1238",        open:true,        proxy:[{            context:['/guonei',"/ent","/sports"],            target:"http://news.baidu.com",            changeOrigin:true,            secure:false        }]    },    mode:"production"}
```

### webpack进阶使用

### webpack优化使用

### 自定义加载器

#### 自定义插件

### webpack打包原理

### 补充概念

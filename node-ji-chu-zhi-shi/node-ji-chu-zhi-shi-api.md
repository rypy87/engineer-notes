# Node基础

### Node简介

#### 基本概念

Node.js 是一个基于 Chrome V8 引擎的解析器和运行环境。

Node.js本身带有一个内置的REPL来解析JavaScript代码，且内置了增强JavaScript编程的模块。

Node.js可以使用在任意操作系统上，可以开发与系统硬件交互的应用程序，主要应用于服务端开发，用来操作文件和创建http服务及进程操作。

#### 官方网址

**英文：**[https://nodejs.org/en/](https://nodejs.org/en/)

**中文：**[https://nodejs.org/zh-cn/](https://nodejs.org/zh-cn/)

**中文官方论坛cnodejs：**[https://cnodejs.org/](https://cnodejs.org/)

#### Node特点

1.单线程

2.非阻塞I/O机制

3.事件驱动(事件环机制)

### 第一个Node程序

文件

```
console.log("hello world!")
```

运行指令

```
node 文件名[.js]
```

### 命令行和CMD

#### 命令

完整的命令是由单词或词组的全称/简写构成。

#### 使用命令步骤：

打开cmd(命令提示行)->输入命令 ->回车执行命令

#### 打开cmd方法：

(1)windows + R -> cmd 回车 (2)打开任意文件夹 -> 在地址栏输入cmd -> 回车 (3)运行/搜索->输入cmd->回车

#### cmd操作技巧：

(1)tab键 快速补全文件或目录名称 (2)上下箭头 ↑↓ 快速定位最近执行的命令 (3)Esc键取消本次命令

#### 常用命令

**清屏**

**语法：**

```
cls
```

**列出当前目录下所有文件**

**语法：**

```
dir
```

**进入指定目录**

**语法：**

```
cd 路径(目录)
```

**返回上一层目录/根目录**

**语法：**

```
cd..  /  cd /
```

**切换盘符**

**语法：**

```
盘符:
```

**创建文件夹**

**语法：**

```
md /mkdir 文件夹名
```

**删除文件夹**

**语法：**

```
rd / rmdir 文件夹名
```

**删除文件**

**语法：**

```
del 文件名
```

### 环境变量

环境变量就是访问文件或文件夹的另一种快速通道，在系统在中配置环境变量，可以快速访问文件或文件夹。

### 文件系统(File system)

#### 进制

**概念**

进制描述的是进位计数规则。对于任何一种进制称为X进制，就表示每一位置上的数运算时都是逢X进一位。 十进制是逢十进一，十六进制是逢十六进一，二进制就是逢二进一，以此类推，x进制就是逢x进位。

**常见进制**

二进制、八进制、十进制、十六进制...

**进制转换原理**

**二进制：**二进制由1和0组成，逢2进1，计算机在底层运算中都把数据转换成了二进制。

**十进制：**十进制是由0-9组成，逢10进1。

#### 计算机存储原理

计算机中最小的单位是位bit比特。存储文件的的最小的单位是 B 字节 1B = 8bit。计算机中文件以十六进制存储：计算机中常用十六进制表示2进制，这样位数就不需要那么长。由0-F组成。

**进制换算方式：**

```
1B = 8 Bit1Kb = 1024B1MB= 1024KB1GB = 1024MB1TB  = 1024GB1PB = 1024TB1EB = 1024PB1ZB = 1024EB1TB = 1024ZB
```

#### ascii码

ascii是最通用的信息交换标准。

![ascii码](file:///E:/%E6%8E%88%E8%AF%BE%E5%86%85%E5%AE%B9/%E4%B8%AD%E5%85%AC/node%E8%AF%BE%E7%A8%8B/%E7%AC%94%E8%AE%B0/img/ascii%E7%A0%81.png?lastModify=1647087559)

**注：**目前utf-8是国际通用标准，规定3个字节的长度表示一个中文。

#### 文件概念

一篇文章、一段视频、一个可执行程序、一个网页，都可以存储在计算机的硬盘中，并赋予一个名字，它就被称为文件。

#### Node文件系统(File system)模块

Node文件系统，File system模块，简称FS模块。模块提供了两套风格的API，一套是采用回调函数(callback)风格API，一套是采用Promise对象风格API。每种风格的API都包含两种方式的API，异步方式和同步方式。例如，读文件的方法，异步方式，引用.readFile()，同步方式，引用.readFileSync()。写文件的方法，异步方式，引用.writeFile()，同步方式，引用.writeFileSync()。在开发过程中，建议使用异步方式，可以避免程序阻塞。

**引入方式：**

```
const fs = require(‘fs’).promises 或 require(‘fs/promises’);//Promise对象风格，支持V14及以上版本const fs = require(‘fs’);//回调函数风格
```

#### 文件操作流程：

**文件操作步骤：**

1、引入fs文件模块

2、打开文件

3、将内容写入文件

4、关闭文件

**打开文件操作：**

**语法：**

```
fs.open(path[, flags[, mode]], callback)fs.openSync(path[, flags[, mode]])
```

**参数：**

path：文件路径 flags：设置打开文件的模式(访问模式)。默认值 r mode ：设置文件权限模式（权限和粘滞位）。默认值: 0o666。 callback： err:错误信息 fd:文件句柄

打开文件模式

| **模式** | **描述**                                            |
| ------ | ------------------------------------------------- |
| a      | 打开文件用于追加。 如果文件不存在，则创建该文件。                         |
| ax     | 打开文件用于追加。 如果文件不存在，则创建该文件，如果路径存在，则失败。              |
| a+     | 打开文件用于读取和追加。 如果文件不存在，则创建该文件。                      |
| ax+    | 打开文件用于读取和追加。 如果文件不存在，则创建该文件，如果路径存在，则失败            |
| as     | 打开文件用于追加（在同步模式中）。 如果文件不存在，则创建该文件。                 |
| as+    | 打开文件用于读取和追加（在同步模式中）。 如果文件不存在，则创建该文件。              |
| r      | 打开文件用于读取。 如果文件不存在，则会发生异常。                         |
| r+     | 打开文件用于读取和写入。 如果文件不存在，则会发生异常。                      |
| rs+    | 打开文件用于读取和写入（在同步模式中）。 指示操作系统绕过本地的文件系统缓存。           |
| w      | 打开文件用于写入。 如果文件不存在则创建文件，如果文件存在则截断文件。               |
| wx     | 打开文件用于写入。 如果文件不存在则创建文件，如果文件存在则截断文件，如果路径存在，则失败。    |
| w+     | 打开文件用于读取和写入。 如果文件不存在则创建文件，如果文件存在则截断文件。            |
| wx+    | 打开文件用于读取和写入。 如果文件不存在则创建文件，如果文件存在则截断文件，如果路径存在，则失败。 |

**写入操作：**

将内容写入文件

**语法：**

```
fs.write(fd, string[, position[, encoding]], callback)fs.writeSync(fd, string[, position[, encoding]])
```

**参数：**

fd\<integer>，文件句柄 string \<string> | \<Object>，写入内容 position \<integer>，在文件中写入内容的位置。 encoding \<string> 编码格式，默认值: 'utf8' callback \<Function> err \<Error>，错误信息 written \<integer>，指定写入内容的字节 string \<string> ，写入内容

**关闭操作**

**语法：**

```
fs.close(fd[, callback])fs.closeSync(fd)
```

**参数：**

fd\<integer>，文件句柄 callback \<Function> err \<Error>，错误信息

**案例：**

```
const fs=require("fs");fs.open("./1.txt","w",(err,fd)=>{    fs.write(fd,"今天天气很好！西安加油！",20,(err,writes,str)=>{        console.log(str);    });    fs.close(fd,err=>{if(err)console.log(err);});});
```

#### 常用文件操作方法

采用Promise对象风格API。

**引入：**

```
const fs=require("fs/promises");
```

**获取文件基本属性信息**

获取文件基本信息，查看文件状态功能，同时可以对文件进行判断是文件还是目录。

**语法**

```
fs.stat(path[, options])fs.statSync(path[, options])
```

**参数**

● path \<string> | \<Buffer> | \<URL> 文件路径。

● options \<Object>

■ bigint \<boolean> 返回的 fs.Stats 对象中的数值是否应为 bigint 型。默认值: false。

● Returns: \<Promise> 返回路径的Stat类信息，封装在Promise对象中。

**常用方法**

● 引用.isFile() 判断当前路径是否是文件

● 引用.isDirectory()判断当前路径是否是文件夹

**案例**

```
const fs=require("fs/promises");async function f(){    let stat=await fs.stat("./1.txt",{bigint:true});    console.log(stat.isFile());    console.log(stat);}f(); 
```

**写文件**

**语法**

```
fs.writeFile(file,data[, options]);fs.writeFileSync(file,data[, options]);
```

**参数**

● file \<string> | \<Buffer> | \<URL> | \<integer> 文件名或文件描述符。 ● data \<string> | \<Buffer> | \<TypedArray> | \<DataView> 需要写入文件的内容 ● options \<Object> | \<string> 可选参数 ■ encoding \<string> | \<null> 编码格式，默认值:’utf8’。 ■ mode \<integer> 设置文件模式（权限和粘滞位）。默认值: 0o666。 ■ flag \<string> 文件系统标志。默认值: 'w'。即默认写入为覆盖写入 ■ signal \<AbortSignal> 允许程序终止此方法，此属性只有异步操作可以支持 ● Returns: \<Promise> 成功返回undefined。

**案例**

```
const fs=require('fs/promises');async function f(){    try{        await fs.writeFile("./2.txt","我是Promise写入",{flag:"a"});    }catch(err){        if(err.message.includes("no such file or directory")){            console.log("文件或文件夹不存在");        }    }finally{        console.log("我的块是永久执行");    }    console.log("dddd");}f();
```

**拼接文件**

**语法**

```
fs. appendFile(file,data[, options]);fs. appendFileSync(file,data[, options]);
```

**参数**

● path \<string> | \<Buffer> | \<URL> | \<number> 文件名或文件描述符。 ● data \<string> | \<Buffer> 需要写入文件的内容 ● options \<Object> | \<string> 可选参数 ■ encoding \<string> | \<null> 编码格式，默认值:’utf8’。 ■ mode \<integer> 设置文件模式（权限和粘滞位）。默认值: 0o666。 ■ flag \<string> 文件系统标志。默认值: 'w'。即默认写入为覆盖写入 ● Returns: \<Promise> 成功返回undefined。

**案例**

```
const fs=require('fs/promises');async function f(){    let str=await fs.appendFile("./a/3.txt",",憨憨");    console.log(str);}f();
```

**读文件**

用于异步读取文件的全部内容，并将全部内容的存储在缓存区后，再传递输出给用户。

**语法**

```
fs.readFile(path[, options]);fs.readFileSync(path[, options]);
```

**参数**

● path \<string> | \<Buffer> | \<URL> | \<integer> 文件名或文件描述符。 ● options \<Object> | \<string> 可选参数 ■ encoding \<string> | \<null> 编码格式，默认值: null。注：目前只有两个读方法的编码格式未空。 ■ flag \<string> 文件系统标志。默认值: 'r’。 ■ signal \<AbortSignal> 允许程序终止此方法，此属性只有异步操作可以支持 ● Returns: \<Promise> 成功会读取的文件内容，若未设置编码格式，默认是Buffer类型。

**案例**

```
const fs=require("fs/promises");async function f(){    let str=await fs.readFile("./1.txt","utf-8");    console.log(typeof str);}   f();
```

**移动重命名文件/文件夹**

**语法**

```
fs.rename(oldPath, newPath)；fs.renameSync(oldPath, newPath)；
```

**参数**

● oldPath \<string> | \<Buffer> | \<URL> 旧文件路径及文件名。 ● newPath \<string> | \<Buffer> | \<URL> 新文件路径及文件名。 ● Returns: \<Promise> 返回值为Promise对象。执行成功返回undefined。

**注：**如果新路径地址不同，则实现剪切功能，如果新文件路径下存在该文件，则会被覆盖，不支持跨盘符操作。

**案例**

```
 let str=await fs.rename("./aaa","D://1.txt");
```

**删除文件**

**语法**

```
fs.unlink(path)fs.unlinkSync(path)
```

**参数**

● path \<string> | \<Buffer> | \<URL>文件名。 ● Returns: \<Promise> 返回值为Promise对象。执行成功返回undefined。

**案例：**

```
let str=await fs.unlink("./aaa");
```

**创建文件夹**

**语法**

```
fs.mkdir(path[, options]);fs.mkdirSync(path[, options]);
```

**参数**

● path \<string> | \<Buffer> | \<URL> 要创建的文件夹完整路径名称 ● options \<Object> | \<integer> ■ recursive \<boolean> 指定是否创建父文件夹。默认值: false。 ■ mode \<integer> 设置文件模式（权限和粘滞位）。默认值: 0o777。注：Windows 上不支持。 ● Returns: \<Promise> 返回值为Promise对象。执行成功返回undefined。

**案例**

```
let str=await fs.mkdir('./a/b/c',{recursive:true});
```

**删除目录**

**语法**

```
fs.rmdir(path[, options])fs.rmdirSync(path[, options])fs.rm(path[, options])//递归删除推荐使用fs.rmSync(path[, options])//递归删除推荐使用
```

**参数**

● path \<string> | \<Buffer> | \<URL>要删除的文件夹完整路径 ● options \<Object> ■ maxRetries \<integer>表示出现异常后重试的次数， 如果遇到EBUSY, EMFILE, ENFILE, ENOTEMPTY, 或者 EPERM 错误,则 Node.js将会在每次尝试时以 retryDelay设置的毫秒线性回退等待重试该操作。此选项代表重试的次数。如果 recursive选项不为true，则忽略此选项。默认值: 0. ■ recursive \<boolean> 如果为 true，则执行递归的目录删除。在递归模式中，如果 path 不存在则不报告错误，并且在失败时重试操作。默认值: false. ■ retryDelay\<integer>出现异常后重试之间等待毫秒数，单位是ms。如果recursive选项不为true，则忽略此选项。默认值: 100ms。 ● Returns: \<Promise> 返回值为Promise对象。执行成功返回undefined。

**案例**

```
let str=await fs.rmdir("./a");let str=await fs.rm("./a",{recursive:true});
```

**读取文件夹内容**

**语法**

```
fs.readdir(path[, options]);fs.readdirSync(path[, options])；
```

**参数**

● path \<string> | \<Buffer> | \<URL> 要读取的文件夹的完整路径 ● options \<string> | \<Object> ■ encoding \<string> 编码格式。默认值: 'utf8'。 ■ withFileTypes \<boolean> 设置files 文件名数组中是否包含fs.Dirent对象。 默认值: false。 ● Returns: \<Promise> 返回值为Promise对象。执行成功，以数组的形式获取目录中的文件/文件夹名。

**案例**

```
let str=await fs.readdir("../../",{withFileTypes:true});
```

### 全局变量

#### node全局对象：

```
global
```

#### 跨平台全局对象：

```
globalThis
```

#### 获取目录名

获取当前正在执行脚本的目录名，以绝对路径输出：

```
_ _dirname
```

#### 获取文件名

当前正在执行脚本的文件名，以绝对路径输出：

```
_ _filename
```

### 模块系统

#### 模块化简介：

在Node.js中，一个js文件就称之为一个模块（Module）。

#### 模块化好处

(1)提高代码的可复用性

(2)提高代码的可维护性

(3)可以实现按需加载

(4)避免函数名和变量名的冲突。

#### 模块的分类

模块分为三类：内置模块、自定义模块、第三方模块。

#### 内置模块

指的是node官方提供的模块，供开发者使用。

**使用步骤**

(1)从nodejs官网中寻找自己想要的模块。

(2)在自己js文件中引入模块。

(3)根据业务使用模块中的一些方法。

**语法：**

```
require( 模块名称 );
```

**常用内置模块**

**URL模块**

用于处理与解析 URL，获取给定url的每一部分。

**引入**

```
import url from 'url';const url = require('url');
```

注：Node中内置的URL模块不需要引入，直接实例化就可以使用。

**语法**

```
new URL(input[, base]);
```

input：要解析的绝对或相对的 URL。

base：如果 input 不是绝对路径，则为要解析的基础地址。

**URL形式及含义**

```
协议：//子域名.域名.顶级域名:端口号/目录/文件名.文件后缀?参数=值#标识
```

**案例：**

```
let urlStr=`http://www.baidu.com:8080/a/b/c/index.html?username=admin&pwd=123456#href`;let url=new URL(urlStr);console.log(url.searchParams.get("username"));
```

**querystring模块(\*)**

用于解析和格式化 URL 查询字符串的实用工具。

**常用方法**

**parse**:将URL格式的字符串序列化为Object类型的对象，且自带转码功能。

```
引用.parse(str[, sep[, eq[, options]]])
```

**参数：**

str,URL类型的参数字符串

sep,设置拆分对象键值对的字符，默认值&

eq，设置拆分键名和键值的字符，默认值是=

options，设置编码的格式类型。

**案例:**

```
let urlData=`username=admin&pwd=123456`;console.log(qs.parse(urlData,"&","d"));
```

**stringify**

将一个Object类型的对象序列化一个URL格式的字符串，且自带编码功能。

```
引用.stringify(obj[, sep[, eq[, options]]])
```

**参数：**

sep，设置拼接对象键值对的字符，默认值&

eq，设置拼接键名和键值的字符，默认值是=

options，设置解码码的格式类型。

**案例：**

```
let user={username:'我是憨憨',pwd:123456}let str=qs.stringify(user);//console.log(qs.stringify(user,"@","$"));console.log(qs.parse(str));
```

**path模块**

提供了一些实用工具，用于处理文件和目录的路径，经常和fs模块结合使用。

**常用方法**

**basename**

获取路径中最后的一部分

```
引用.basename(path[, ext])
```

**参数：**

path：必选参数，路径地址

ext：可选参数，是否忽略扩展名

**案例：**

```
console.log(path.basename(__filename));console.log(path.basename(__dirname));
```

**extname**

获取path路径的扩展名

```
引用.extname(path)
```

**参数：**

path：必选参数，路径地址

**案例：**

```
console.log(path.extname(__filename));console.log(path.extname(__dirname));
```

**join**

将所有给定的path片段连接到一起，使新的路径更加规范化。

```
引用.join([...paths])
```

**参数：**

paths，一组路径列表参数

**案例：**

```
console.log(path.join(__dirname,"../../a","b","../index.html"));console.log(path.join(__dirname,__filename));
```

**parse**

以对象的形式返回当前路径的盘符，完整路径，文件/文件夹的全称(带文件后缀)，文件的后缀，文件的名字（不带后缀）。

```
引用.parse(path))
```

**参数：**

path必选参数，完整的路径地址

**案例：**

```
console.log(path.parse(__filename));
```

#### 自定义模块

自定义模块，指的是开发者将特定的功能/算法封装到js模块文件中，其包含一些公共函数或其它数据，每一个js文件都可以称为一个模块。

**使用步骤：**

1、定义模块：将功能/算法进行模块文件的封装。

2、抛出模块：使用module.exports/exports将模块进行抛出。

**语法**

```
//暴露抛出语法：使用module对象的exports属性module.exports=属性名/方法名//隐式抛出语法：使用 exports 对象    exports.属性 = 属性名;    exports.方法 = 函数名/函数体;使用module对象的exports属性    module.exports.属性 = 属性名;    module.exports.方法 = 函数名/函数体;    module.exports = {键：函数名/属性名};
```

3、引入模块：使用require()方法，将模块化的文件引入，该方法读取一个文件并加载，且返回文件使用module.exports/exports抛出的名字。

**注：**必须以相对路径引入自定义模块，根据实际情况 以 ./ 或 ../ 开头。

**语法**

```
const 变量名 = require('相对路径');
```

module.exports与exports区别：

(1)exports是module.exports的引用。

(2)module.exports是实体抛出功能方法。

(3)当两个关键词混用的时候会造成暴露混乱导致未达到抛出效果。

**案例：**

定义模块

```
//定义模块//定义模块，可以是变量，对象，函数/方法，类，类的实例let username="admin";let user={username,pwd:123456};function getPwd() {    return "sddfsdf";}//抛出模块//暴露抛出// module.exports=username;//隐式抛出//变量形式抛出// module.exports.aa=user;//对象形式抛出(推荐)module.exports={    uu:username,    user,    pp:getPwd}//exports只能以变量的形式抛出// exports.aaa={//     username,//     user// }// exports.bbb={//     getPwd// }// exports.cccc={// }// module.exports={//     aaa:{username,user},//     bbb:{getPwd}// }
```

引入模块

```
//暴露抛出的引入 //原理//a=require("./2")=module.exports=username=值// const a=require("./2");// console.log(a);//变量抛出的引入// const a=require("./2");// const {aa}=require("./2");// console.log(aa);//对象抛出的引入const a=require("./2");const {uu:u}=require('./2');//(推荐使用)let uu="sss";console.log(u);console.log(uu);console.log(a);
```

**第三方模块：**

由第三方开源出来的模块，使用前需要npm工具从npm社区下载。

**使用步骤：**

(1)新建js文件并命名

(2)生成package.json配置文件

```
npm init
```

(3)下载所需插件

```
npm i trim
```

(4)引入trim。并去除字符串中的空格

```
const trim=require("trim");let str=`     aaa      `;console.log(trim(str));
```

### npm与包

#### npm

npm(Node Package Manager)，是Node内置的包管理器，安装node环境后，自动安装了npm命令行工具，可以使用npm命令下载（安装），卸载，更新，查看第三方模块。

npm社区，全球最大的JavaScript开源生态系统库，该社区提供了数以亿个包模块，这些包模块实现了不同的功能。提供给需要使用的人进行下载并使用。

**使用场景**

1、从npm服务器下载其他人编写的第三方包或命令行程序到本地,供本地项目使用。

2、将自己编写的包或或命令行程序，发布到npm服务器供其他人使用。

**网址：**

[https://www.npmjs.com/](https://www.npmjs.com/)

[https://www.npmjs.cn/](https://www.npmjs.cn/)

**常用命令**

**查看NPM版本号**

```
npm -v / -version
```

**初始package.json配置文件命令**

```
npm init [-y]
```

注：-y代表自动生成package.json。当前项目文件夹名必须没有中文、特殊符号、空格

**安装命令**

npm安装插件模式分为两种，全局安装模式和项目安装模式。

**全局安装模式**

```
npm i / add / install 插件名字 -g / --global
```

全局安装的插件默认存放在 C:\Users\计算机名\AppData\Roaming\npm\node\_modules，一般将命令行工具和需要全局使用的插件安装为全局模式。

**项目安装模式**

项目安装模式，又分为两种模式，产品模式插件(默认安装)和开发模式插件

**产品模式插件(默认安装)**

项目部署运行过程中需要用到的插件，则安装为产品模式，安装记录会存放在package.json文件的dependencies属性下。

默认安装

```
npm i/in/ins/inst/insta/instal/isnt/ista/istal/install/add 插件名字[ 插件名字 插件名字]
```

参数安装

```
npm i / add / install 插件名字 [-P / --save -prod]
```

**开发模式插件**

项目开发过程中需要用到的插件，且项目部署后不需要使用，则安装为开发模式。安装记录会存放在package.json文件的devDependencies属性下。

```
npm i / add / install 插件名字 -D / --save -dev
```

注：如果将开发模式的插件依赖，重新安装为产品模式的插件依赖，则必须要携带参数-P。

**全部安装插件**

全部安装插件会根据package.json文件的记录安装全部的插件（开发模式和产品模式）

```
npm i / add / install
```

一般安装插件都会从NPM社区下载最新稳定版，也可指定版本下载相应插件。

**安装指定版本插件**

```
npm i / add / install 插件的名字@版本号npm  i / install / add  别名@npm:插件的名字@版本号
```

**卸载插件**

```
npm uninstall / rm / remove / r / un / unlink 插件的名字 [-g]
```

**npm命令版本号的书写格式**

```
“foo” : “1.0.0 - 2.9999.9999“  //区间最新版本, "bar" : ">=1.0.2 <2.1.2“  //区间最新版本, "baz" : ">1.0.2 <=2.3.4“ //区间最新版本, “boo” : “2.0.1“ //指定版本, “qux” : “<1.0.0 || >=2.3.1 <2.4.5 || >=2.5.2 <3.0.0“ //满足条件的最新版本, “til” : “~1.2”  //大约匹配前两位的最新版本, “elf” : “~1.2.3“ //大约匹配的最新版本,”one”:“^4.1.2“ //固定版本, “two” : “2.x“   //固定一位的最新版本, “thr” : “3.3.x“ //固定两位的最新版本, “lat” : “latest“ //最新版本
```

**注：**新版的NPM版本更遵循语义化版本规则，需要node-semver语义版本器支持

**淘宝镜像(CNPM)**

淘宝在国内免费为开发者提供了一个服务器，专门把国外官方服务器上的包同步到国内的服务器，供国内开发者使用。极大的提高了下载包的速度。cnpm是一个功能和npm一模一样的命令工具，同样可以完成包的管理工作，同步频率目前为5分钟一次以保证尽量与官方服务同步。

**网址：**

```
https://npmmirror.com/
```

**配置方法：**

**1、全局cnpm：**

```
npm i cnpm -g
```

**2、修改下载源地址：**

```
npm i -g cnpm --registry=https://registry.npmmirror.com
```

**注：**推荐使用方法2，同时会在 C盘/users/用户名 下生成一个 .npmrc文件。

**Facebook(yarn)**

yarn 是 Facebook 2017 年推出的和 npm 功能类似的包管理工具。

```
npm i yarn -g
```

#### 包

模块的高级包装形式就是包，与核心模块类似，就是将一些预先设计好的功能或API封装到一个文件夹，以目录形式存储，存放在“node\_modules”文件夹中，提供给其他开发者使用。

**注：**包中最终指向还是一个模块。且模块必须遵循CommonJS规范。

**包描述文件(package.json)：**

包描述文件(package.json)，用于表达非代码相关的信息，它是一个JSON格式的文件，位于包的根目录下，是包重要的组成部分。NPM命令下载的所有插件行为，都与包描述文件的字段息息相关。

**文件包含信息：**

(1)项目的名称、版本号、描述

(2)项目中使用的第三方模块包（包括开发模式模块包和产品模式模块包）

**创建命令：**

```
npm init [-y]
```

**属性说明**

| **属性名**         | **描述**                   |
| --------------- | ------------------------ |
| name            | 项目的名字                    |
| version         | 项目的版本号                   |
| description     | 项目的描述                    |
| main            | 项目模块加载的主入口文件             |
| scripts         | 项目的启动命令                  |
| keywords        | 项目的关键词                   |
| author          | 项目的作者                    |
| license         | license证书说明(证书协议)默认值，ISC |
| dependencies    | 产品模式第三方依赖                |
| devDependencies | 开发模式第三方依赖                |

**main的三种加载机制：**

(1)根据目录下的package.json 的文件，寻找 main 属性指定的文件名，作为 require() 加载的入口。 (2)如果目录里没有 package.json 文件，或者 main 入口不存在或无法解析，则 Node.js 将会加载目录下的 index.js 文件（所以默认目录中的默认入口为index.js）。 (3)如果以上两步都加载失败，则 Node 会在终端打印错误消息，报告模块缺失：Error: Cannot find module 'xxx'。

**包的分类：**

**项目包：**

使用npm命令安装到项目的node\_modules 目录中的包，称为项目包。

**项目包分为两类：**

(1)开发依赖包：被记录到 devDependencies 节点中的包，只在开发期间使用。

(2)产品依赖包：被记录到 dependencies 节点中的包，项目全过程。

**全局包：**

一般安装为全局的插件包，称为全局包，通常指(工具类的包)称为全局包。

**安装命令**

```
npm i 插件名  -g
```

**应用场景**

(1)需要当作可执行程序进行使用

(2)官方API要求

注：全局包会被安装到 C:\Users\计算机名\AppData\Roaming\npm\node\_modules 目录下。

**包加载机制**

**模块的分类**

在Node中，模块分为两类：一类是Node提供的模块，称为核心模块；另一类是用户编写的模块，称为文件模块。

**核心模块(内置模块)**

核心模块由Node官方API内置模块，加载优先级最高。在Node进程启动时，部分核心模块就被直接加载进内存中，所以这部分核心模块引入时，文件定位和编译执行这两个步骤可以省略掉，并且在路径分析中优先判断，所以它的加载速度是最快的。

**文件模块**

文件模块则是在运行时动态加载，需要完整的路径分析、文件定位、编译执行过程，速度比核心模块慢。文件模块分为两类自定义模块和第三方模块。

**自定义模块**

自定义模块，在引入的时候，必须指定以./或../开头的路径标识符，否则node 会把它当作内置模块或第三方模块进行加载。如果省略了文件的扩展名，则Node.js会按顺序分别尝试加载以下的文件： (1)文件名.js 扩展名进行加载 (2)文件名.json 扩展名进行加载 (3)加载失败，终端报错 Error: Cannot find module 'xxx'

**第三方模块**

如果引入的模块标识符不是内置模块，也不是自定义模块，则Node.js会尝试从当前文件夹下查找node\_modules 文件夹中加载第三方模块，如果当前文件夹下没有node\_modules文件夹，则移动到再上一层父目录中，进行查找加载，直到查找到当前项目文件的盘符根目录。如果没有则加载失败，终端报错 Error: Cannot find module ‘xxx’ 。

**模块加载机制：**

![模块加载机制](file:///E:/%E6%8E%88%E8%AF%BE%E5%86%85%E5%AE%B9/%E4%B8%AD%E5%85%AC/node%E8%AF%BE%E7%A8%8B/%E7%AC%94%E8%AE%B0/img/%E6%A8%A1%E5%9D%97%E5%8A%A0%E8%BD%BD%E6%9C%BA%E5%88%B6.png?lastModify=1647087559)

**第三方模块查找的流程**

![node\_module包加载机制](file:///E:/%E6%8E%88%E8%AF%BE%E5%86%85%E5%AE%B9/%E4%B8%AD%E5%85%AC/node%E8%AF%BE%E7%A8%8B/%E7%AC%94%E8%AE%B0/img/node\_module%E5%8C%85%E5%8A%A0%E8%BD%BD%E6%9C%BA%E5%88%B6.png?lastModify=1647087559)

### 服务器与客户端

#### 基本概念

**交互模式：**

B/S：指基于 浏览器（Browser） 和 服务器（Server） 这种交互形式

C/S：指基于 客户端（Client） 和 服务器（Server） 这种交互形式

**服务器：**

在互联网交互过程中，负责存放和对外提供资源的网络终端，叫做服务器。与个人终端相比，服务器要求的配置和性能更高。

**客户终端：**

在互联网交互过程中，负责获取资源的终端，叫做客户终端，简称客户端。客户终端可以有很多表现形式，如：个人电脑、手机、平板等等。客户端可以通过浏览器很方便地从服务器端获取资源。

**静态资源与动态资源：**

静态资源：服务器端只需要读取并直接发送给客户端、不需要进一步处理的资源。

动态资源：服务器端没有现成的资源，需要服务器端动态生成的资源。

#### 互联网通信模型

请求 -> 处理 -> 响应

请求：由客户端发起请求； 处理：由服务器端处理请求； 响应：服务器端把处理的结果，通过网络发送给客户端；

![互联网通信模型](file:///E:/%E6%8E%88%E8%AF%BE%E5%86%85%E5%AE%B9/%E4%B8%AD%E5%85%AC/node%E8%AF%BE%E7%A8%8B/%E7%AC%94%E8%AE%B0/img/%E4%BA%92%E8%81%94%E7%BD%91%E9%80%9A%E4%BF%A1%E6%A8%A1%E5%9E%8B.png?lastModify=1647087559)

基于互联网通信模型，交互过程中，互联网会话的 4 个步骤 ●建立连接：客户端的浏览器向服务端发出建立连接的请求，服务端给出响应就可以建立连接了。 ●发送请求：客户端按照协议的要求通过连接向服务端发送自己的请求。 ●给出响应：服务端按照客户端的要求给出应答，把结果（HTML 文件）返回给客户端。 ●关闭连接：客户端接到应答后关闭连接

#### Web应用架构

![Web应用框架](file:///E:/%E6%8E%88%E8%AF%BE%E5%86%85%E5%AE%B9/%E4%B8%AD%E5%85%AC/node%E8%AF%BE%E7%A8%8B/%E7%AC%94%E8%AE%B0/img/Web%E5%BA%94%E7%94%A8%E6%A1%86%E6%9E%B6.png?lastModify=1647087559)

Client - 客户终端，客户终端可以通过 HTTP 协议向服务器请求数据。

Server - 服务端，一般指 Web 服务器，可以接收客户终端请求，并向客户端发送响应数据。

Business - 业务层， 通过 Web 服务器处理应用程序，如与数据库交互，逻辑运算，调用外部程序等。

Data - 数据层，一般由数据库组成。

#### URL地址组成

URL（全称是UniformResourceLocator）又称统一资源定位符，根据一个URL能够在全球互联网上确定一个唯一的资源存放位置。浏览器只有通过URL地址，才能正确定位资源的存放位置，从而成功访问到对应的资源。它包含的信息有，文件的位置，文件的类型，及浏览器的处理方式。

**组成**

```
通信协议：//子域名.域名.顶级域名:端口号/目录/文件名.文件后缀?参数=值
```

**通信协议**

通信协议，指互联网交互过程中，需要遵守已定的通信协议，从完成互联交互。如：http 、https、ftp、DNS、Telnet、smtp、TCP/IP等都是协议。

**域名**

互联网上服务器是通过IP来进行定位，但为了方便记忆会用域名来表示，域名和IP是通过DNS来解析的。

**端口号**

计算机中每一个端口号对应一个正在开启的服务。同一台计算机中同一个端口号不能被多个应用使用。

**常用默认端口号**

(1)http的默认端口为80

(2)https的默认端口为443，默认端口号是可以省略的

(3)mysql默认端口号3306

**路由**

资源在服务器上相应的位置（不一定是具体路径，可能需要结合代码实现资源相应）

**参数**

获取资源所需要的参数，可以是必备参数也可以是可选参数

**标识**

用来标识是否有关联资源，比如父子资源。

#### 域名与ip

**IP：**

IP用于区分互联网上每个终端的唯一标识。

**格式**

```
X.X.X.X
```

**注：**X的取值是0\~255之间。

**域名：**

IP的字符别名，为了方便记忆而产生。通过DNS来进行IP与域名的解析。

**DNS服务器：**

DNS（Domain Name System）服务是和 HTTP 协议一样位于应用层的协议。它提供域名到 IP 地址之间的解析服务。

**DNS解析过程**

![DNS解析过程](file:///E:/%E6%8E%88%E8%AF%BE%E5%86%85%E5%AE%B9/%E4%B8%AD%E5%85%AC/node%E8%AF%BE%E7%A8%8B/%E7%AC%94%E8%AE%B0/img/DNS%E8%A7%A3%E6%9E%90%E8%BF%87%E7%A8%8B.png?lastModify=1647087559)

#### 互联网传输协议

**协议概念**

协议（ Protocol）是指双方为了完成一个目标结果所必须遵守的规则和约定。

**http协议**

HTTP(Hyper Text Transfer Protocol)< 超文本传输协议> 的缩写. 是用于从WWW 服务器传输超文本(内容)到本地浏览器的传输协议。它规定了客户端与服务器之间进行页面内容传输时，所必须遵守的传输格式。HTTP 是一个应用层协议, 由请求和响应构成, 是一个标准的客户端和服务器模型。通常基于TCP连接方式。

**http与https的区别**

相同点：http协议和https，都是超文本传输协议，

不同点：

1）http的参数信息是明文传输，而https的参数信息是加密传输， 2）https则是具有安全性的ssl加密传输协议。 3）端口号不同http是80，https是443

#### 请求/响应交互模型：

HTTP 协议采用了请求/响应的交互模型。即客户终端主动发起请求，再由服务器端处理请求，并把内容响应给客户终端。

**请求消息(请求报文)：**

**描述：**

由客户终端发起，在客户终端向服务器端发送请求时生成。

**组成：**

HTTP请求消息由请求行（request line）、请求头部（ header ） 、空行 和 请求体 4 个部分组成。

![请求报文](file:///E:/%E6%8E%88%E8%AF%BE%E5%86%85%E5%AE%B9/%E4%B8%AD%E5%85%AC/node%E8%AF%BE%E7%A8%8B/%E7%AC%94%E8%AE%B0/img/%E8%AF%B7%E6%B1%82%E6%8A%A5%E6%96%87.png?lastModify=1647087559)

**请求行**

请求行由请求方式、URL 和 HTTP 协议版本 3 个部分组成。

**请求头部**

请求头部用来描述客户端的基本信息，从而把客户端相关的信息告知服务器。

**表现形式：**请求头部由多行键/值对组成，每行的键和值之间用英文的冒号分隔。

**常见请求头字段:**

(1)Host要请求的服务器域名

(2)User-Agent产生请求的浏览器类型

(3)Cookie产生请求所携带的cookie

**空行**

用来隔开请求头部与请求体。

**请求体**

请求体中存放的，是要通过 POST 方式提交到服务器的数据。注意：只有 POST 请求才有请求体，GET 请求没有请求体。

**响应消息(相应报文)：**

**描述：**

根据客户端的请求信息做出的资源结果响应时生成。

**组成：**

HTTP响应消息由状态行、响应头部、空行 和 响应体 4 个部分组成。

![相应报文](file:///E:/%E6%8E%88%E8%AF%BE%E5%86%85%E5%AE%B9/%E4%B8%AD%E5%85%AC/node%E8%AF%BE%E7%A8%8B/%E7%AC%94%E8%AE%B0/img/%E7%9B%B8%E5%BA%94%E6%8A%A5%E6%96%87.png?lastModify=1647087559)

**状态行：**

状态行由 HTTP 协议版本、状态码和状态码的描述文本 3 个部分组成。

**相应头部:**

响应头部用来描述服务器的基本信息。

**表现形式：**请求头部由多行键/值对组成，每行的键和值之间用英文的冒号分隔。

**常见请求头字段:**

(1)Server：服务器类别

(2)Content-type：告诉浏览器采用何种方式对响应体进行处理

**空行：**

用来隔开请求头部与请求体。

**响应体:**

响应体中存放的，是服务器响应给客户端的资源内容。。

**请求方式：**

HTTP 请求方式，属于 HTTP 协议中的一部分，用来表明要对服务器上的资源执行的操作。

最常用的请求方式是 GET 和 POST。

**http中常见的请求方法：**

| **请求方法** | **描述**                                  |
| -------- | --------------------------------------- |
| GET      | 发送请求,获得服务器上的资源，请求体中不会包含请求数据，请求数据放在协议头中  |
| POST     | 向服务器提交资源（例如提交表单或上传文件）。数据被包含在请求体中提交给服务器。 |
| PUT      | 向服务器提交资源，并使用提交的新资源，替换掉服务器对应的旧资源。        |
| DELETE   | 请求服务器删除指定的资源。使用表格展示                     |

**状态码**

HTTP 响应状态码（HTTP Status Code），也属于 HTTP 协议的一部分，用来标识响应的状态。

**作用**

响应状态码会随着响应消息一起被发送至客户端浏览器，浏览器根据服务器返回的响应状态码，判断服务器端的响应结果。

**格式**

HTTP状态码由三个十进制数字组成，第一个十进制数字定义了状态码的类型，后两个数字用来对状态码进行细分。HTTP 状态码共分为 5 种类型。

**常见状态码：**

| **状态码** | **描述**                                         |
| ------- | ---------------------------------------------- |
| 1\*\*   | 信息，服务器收到请求，需要请求者继续执行操作（实际开发中很少遇到 1\*\* 类型的状态码） |
| 2\*\*   | 成功，操作被成功接收并处理                                  |
| 3\*\*   | 重定向，需要进一步的操作以完成请求                              |
| 4\*\*   | 客户端错误，请求包含语法错误或无法完成请求                          |
| 5\*\*   | 服务器错误，服务器在处理请求的过程中发生了错误                        |

### Node创建服务器

#### 引入模块

```
const http = require("http")；
```

#### 创建服务器

```
引用.createServer((req,res)=>{}).listen(端口号);
```

listen(端口, IP地址, 启动成功的回调函数)，设置端口号，IP地址方法，常用端口号范围在1\~65535。

#### 设置响应头

设置响应报文头，包括状态码，状态消息，Content-Type属性等。

```
响应引用.writeHead(statusCode[, statusMessage][, headers])
```

#### 结束响应

结束响应并向客户端发送内容方法。

```
响应引用.end([data[, encoding]][, callback])
```

#### 获取请求的方法

```
请求引用.method
```

#### 请求的路由及参数

```
请求引用.url
```

#### 原生路由的的响应

根据不同的路由跳转到不同的页面

```
const http=require("http");const fs=require("fs/promises");const path=require("path");const umodel=require("./model/UserModel");​http.createServer(async (req,res)=>{    if(req.url!=="/favicon.ico"){        let {pathname,searchParams}=new URL(req.url,"http://localhost:80");        switch(pathname){            //静态资源路由            case "/":                res.writeHead(200,'200',{"content-Type":"text/html;charset=utf8"});                res.end(await fs.readFile(path.join(__dirname,"./public/index.html")));                break;            case "/css/index.css":                res.writeHead(200,'200',{"content-Type":"text/css;charset=utf8"});                 res.end(await fs.readFile(path.join(__dirname,"./public/css/index.css")));                break;            case "/js/index.js":                res.writeHead(200,'200',{"content-Type":"text/javascript;charset=utf8"});                 res.end(await fs.readFile(path.join(__dirname,"./public/js/index.js")));                break;            case "/js/jquery.min.js":                    res.writeHead(200,'200',{"content-Type":"text/javascript;charset=utf8"});                 res.end(await fs.readFile(path.join(__dirname,"./public/js/jquery.min.js")));                break;            case "/html/userlist.html":                res.writeHead(200,'200',{"content-Type":"text/html;charset=utf8"});                 res.end(await fs.readFile(path.join(__dirname,"./public/html/userlist.html")));                break;                 //业务路由            case "/login":                res.end(JSON.stringify(await umodel.login({username:searchParams.get("username"),pwd:searchParams.get('pwd')})));                break;        }    }}).listen(1413,"192.168.1.63",()=>{    console.log("服务器已启动1413");});
```


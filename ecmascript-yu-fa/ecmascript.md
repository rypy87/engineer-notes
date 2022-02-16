# ECMASCript

## ECMAScript简介

### 概念

我们俗称的ECMAScript(简称ES),指的就是ECMAScript 6.0(ES6)，是 JavaScript 语言的下一代标准，在 2015 年 6 月正式发布。它的目标，是使得 JavaScript 语言可以用来编写复杂的大型应用程序，成为企业级开发语言。

**ECMAScript与JavaScript的关系是**

前者是后者的规则，后者是前者的一种实现。

### 版本发展史

| **年份** | **版本**               |
| -------- | ---------------------- |
| 1997     | ECMAScript  1.0        |
| 1998     | ECMAScript  2.0        |
| 1999     | ECMAScript  3.0        |
| 2009/12  | ECMAScript  5.0        |
| 2015/06  | ECMAScript  2015(ES6)  |
| 2016/06  | ECMAScript  2016(ES7)  |
| 2017/06  | ECMAScript  2017(ES8)  |
| 2018/06  | ECMAScript  2018(ES9)  |
| 2019/06  | ECMAScript  2019(ES10) |
| 2020/06  | ECMAScript  2020(ES11) |
| 2021/06  | ECMAScript  2021(ES12) |

## 变量与常量的声明

### let

声明变量的关键字。

#### 语法：

```
let 变量名[=赋值]
```

#### 特点

(1) 块级作用域。

```
{
	let b=30;
	console.log(b);//30
}
console.log(b);//b is not defined
```

(2) 不存在变量提升：暂时性死区(Temporal Dead Zone，TDZ)：本质，只要一进入当前作用域，所要使用的变量就已经存在了，但是不可获取，只有等到声明变量的那一行代码出现，才可以获取和使用该变量。

```
{
	console.log("b的死区开始");
	console.log(b);//Cannot access 'b' before initialization
	console.log("b的死区结束");
	let b=30;
}
```

(3) 同一作用域，不能重复声明同一变量。

```
{
    let b=20;
    let b=30;//Identifier 'b' has already been declared
    console.log(b);
}  
```

### const

声明常量，ES6中默认公约使用大写形式定义常量名。

#### 语法：

```
const 变量名=赋值；
```

#### 特点：

(1) 块级作用域。

(2) 不存在变量提升：暂时性死区(Temporal Dead Zone，TDZ)：本质，只要一进入当前作用域，所要使用的变量就已经存在了，但是不可获取，只有等到声明变量的那一行代码出现，才可以获取和使用该变量。

(3) 同一作用域，不能重复声明同一变量。

(4)声明变量的同时需要立即初始化。

```
const a=20;
```

(5) 当数据类型为数值、字符串、布尔值、类型时，其值是不可改变的，但是为对象或数组的时候，其值是可以改变，因为声明的变量相当于指向的那个内存地址。

```
const a=20;
console.log(a);//20
a=30;// Assignment to constant variable.
console.log(a);
```

```
const a=[1,3,5,6,8];
console.log(a);//[1,3,5,6,8]
a[3]=10;
console.log(a);//[1,3,5,10,8];
```

### 使用场景

#### 循环输出

```
for(var i=0;i<5;i++){}
console.log(i);//5
for(let i=0;i<5;i++){}
console.log(i);//i is not defined
```

#### 按钮事件

```
<button>按钮1</button>
<button>按钮2</button>
<button>按钮3</button>
<script>
    let btns=document.getElementsByTagName("button");
    for(let i=0;i<btns.length;i++){
        btns[i].onclick=function(){
            console.log(i+1);
        }
    }
</script>
```

## Symbol数据类型

**JavaScript基本数据类型**

undefined、null、布尔值（Boolean）、字符串（String）、数值（Number）。

### 概念：

Symbol是第六种基本数据类型，使用Symbol函数来生成一个symbol数据，每一个Symbol是都是独一无二的。

### 语法：

```
let 变量=Symbol(["注解"]);
```

### 应用场景

#### 私有属性和方法

```
function Person(){
            let a=Symbol();
            let b=Symbol();
            this[a]=20;
            this.name="rypy";
            this.aa=function(){
                this[b]();
                console.log("aaaa,"+this[a]);
            }
            this[b]=function(){
                console.log("我是私有方法");
            }
        }
        let p=new Person();
        console.log(p.name);
        p.aa();
```

## 字符串扩展

### 模板字符串

#### 语法：

```
`字符串1 ${输出表达式} 字符串2`
```

#### 输出表达式：

1.变量

2.JavaScript表达式（三目运算符）

3.获取对象的属性

4.调用函数

#### 案例

```
let str1=`<h1 style="color:red;">我的名字："${user.username}",
                    我的年龄：${user.age>18?"已成年":"未成年"},${f()}</h1>`;
        console.log(str1);
        document.getElementById("divs").innerHTML=str1
        function f(){
            return "我是函数的返回值";
        }
```

### 其它新增方法

#### startsWith

判断字符串是否以参数字符串开始，返回值是布尔类型。

##### 语法：

```
字符串.startsWith(参数字符)
```

```
let str="我是字符串，憨憨！";
console.log(str.startsWith("我是"));
```

#### endsWith

判断字符串是否以参数字符串结束，返回值是布尔类型。

##### 语法：

```
字符串.endsWith(参数字符)
```

```
console.log(str.endsWith("！"));
```

#### repeat

重复拼接字符串参数次数，返回值是新的字符串。

##### 语法：

```
字符串.repeat(重复次数)
```

```
console.log(str.repeat(4));
```

#### padStart

将字符串前置补全

##### 语法：

```
字符串.padStart(目标长度，填充的字符)
```

```
console.log(str.padStart(20,"abc"));
```

#### padEnd

将字符串后置补全

##### 语法：

```
字符串.padEnd(目标长度，填充的字符)
```

```
console.log(str.padEnd(20,"abc"));
```

#### replaceAll

查找并全部替换

##### 语法：

```
字符串. replaceAll(目标字符，替换字符)
```

```
console.log(str.replaceAll("憨","mll"));
```

















## 数组的扩展

**新增方法**

Array.of(元素序列)：创建一个数组，解决 new Array的缺陷，即将类数组序列转化为真正的数组

**语法：**

```
console.log(Array.of(1,3));
```

Array.from(类数组)：将类数组转换为真正的数组，返回值是一个新数组。

**语法：**

```
    <button>按钮1</button>
    <button>按钮2</button>
    <button>按钮3</button>
    <script>
    	let btns=document.getElementsByTagName("button");
        console.log(btns);//类似数组（伪数组）
        console.log(Array.from(btns));
    </script>    
```

引用.filter(callback),循环遍历数组，根据回调函数中返回值的布尔类型，过滤当前数组元素，并生成新的数组。

**语法：**

```
        console.log(persons.filter(function(item){return item.salary>55000;}));
```

引用.includes(参数)：查询数组中是否含有参数元素，返回值是布尔类型。注：此方法只支持基本数据类型

**语法：**

```
        // let arr=[1,2,4,7,8,9];
        // console.log(arr.includes(8));
```

引用.flat(Infinity),将多维数组降维，返回值是一个一维数组。

**语法：**

```
        let arr=[1,2,4,[2,3,5,67,8,[3,3,5,7,8,9]]];
        console.log(arr.flat(Infinity));   
```

## 对象的扩展

对象（object）是 JavaScript 最重要的数据类型。ES6 对其进行了重大升级，包括（数据类型本身的升级和Object对象的方法）。

### 类型本身特性

**属性简写：**

键名的“”可以省略。

当变量名和对象中的属性名相同时，属性值可以省略。

**语法：**

```
let newObj={username:"admin",pwd:123456};
let username="admin";
let age=20;
let newUser={username,age};
```

**对象中函数简写：**对象中可以直接定义普通函数，一定程度降低了代码量，简写形式的函数中的this和function声明函数的this指向是相同的。

**语法：**

```
        // let newObj1={
        //     bb(){console.log("我是新对象中的函数");}
        // } 
        // newObj1.bb();
```

**属性名表达式：**表达式可以使对象的属性/方法，更加灵活的运算，即中括号的用法(中括号中写表达式)。

**语法：**

```
let 变量名=变量值；
{   [变量名/表达式]:对象变量值  ,  [变量名/表达式](){}  }
```

**调用：**

```
(1)对象.变量值
(2)对象[变量名]
```

**案例：**

```
		// let str="hello";
        // let i=0;
        // let obj={
        //     [`${str}user${++i}`]:"amdin",
        //     [`${str}${i+1}`](){console.log("我是函数");}
        // }
        // console.log(obj);
        // obj.hello2();
        // obj[`${str}${i+1}`]();
```



### 新增方法

Object.assign(参数1,...参数n),将参数2...参数n,合并给参数1， 并生成新的对象，新对象与参数1一致。当键名相同的时候，会进行同名覆盖操作。基本数据类型深拷贝，复合数据类型浅拷贝。

**语法：**

```
        // let obj=Object.assign(user1,user2,user3);
        // user2.username.aa="sssss";
        // console.log(obj);
        // console.log(user1);
```

Object.keys(引用)，将对象中的键名以一维数组的形式返回。

**语法：**

```
        let user={username:"amdin",pwd:"123123"};
        // console.log(Object.keys(user));
```

Object.values(引用)，将对象中的值以一维数组的形式返回。

**语法：**

```
console.log(Object.values(user));
```

Object.entries(引用)，将对象中的键值对以二维数组的形式返回。 键值对是一个一维数组。

**语法：**

```
console.log(Object.entries(user));
```

**JSON对象**

JSON.stringify(引用)，将对象/数组转换为JSON格式的字符串。

**语法：**

```
console.log(typeof JSON.stringify(user));
```

JSON.parse(引用)，将JSON格式的字符串转换为对象/数组。

**语法：**

```
let str=JSON.stringify(user);
console.log(typeof JSON.parse(str));
```

## 数据结构

### set数据结构

自带去重功能。类数组,可以存储任意数据类型。

**语法：**

```
new Set(数组/类数组)
```

**常用方法**

add：set数据结构中添加元素数据，返回set数据结构本身

**语法：**

```
		// s.add("aaaa");
        // s.add({username:"aa"});
        // s.add(true);
        // s.add(function(){console.log("ssss");})
        // s.add(function aa(){console.log("ssssaaa");});
        // console.log(s);
```

delete：删除set数据结构中的某个元素数据，返回布尔类型，表示删除是否成功，仅支持基本数据类型。

**语法：**

```
        // s.delete("aaaa");
        // s.delete(function aa(){console.log("ssssaaa");});
        // s.delete({username:"aa"});
```

has：判断某个元素数据是否存在于set数据结构中，返回布尔类型，表示数据结构中是否含有该元素，仅支持基本数据类型。

**语法：**

```
        // console.log(s.has(true));
        // console.log(s.has({username:"aa"}));
```

clear：清空set数据结构中的数据，无返回值。

**语法：**

```
s.clear();
```

forEach(callback),循环遍历Set数据结构

**语法：**

```
		// s.forEach(function(item){
        //     if(typeof item==="function"){
        //         item();
        //     }else{
        //         console.log(item);
        //     }
        // });
```

**常用属性**

size:获取set数据结构的长度

**语法：**

```
console.log(s.size);
```

### Map数据结构

类对象，键名和键值可以是任意类型，且键名不重复的键值对集合体。

**语法：**

```
new Map([[key,value],[key,value]]);
```

**常用方法**

set：向map数据结构中添加键值对数据

**语法：**

```
		m.set("aaaa","ssssss");
        m.set(true,{username:"aaaaa"});
        m.set(123,"ddddd");
        m.set(undefined,function aa(){console.log("ddddd");});
        m.set(function (){console.log("ddddd");},"xaaaaa");
        console.log(m);
```

get：获取map数据结构中参数键名的数据，只支持键名为基本数据类型。

**语法：**

```
        //console.log(m.get(undefined));  
        //m.get(undefined)();
        //console.log(m.get(function (){console.log("ddddd");}));
```

delete：删除map数据结构中的参数键名的数据，只支持键名为基本数据类型。

**语法：**

```
m.delete(undefined);
```

has：判断参数键名是否存在于map数据结构中,返回布尔类型，只支持基本数据类型。

**语法：**

```
        //console.log(m.has(undefined));    
        //console.log(m.has(function (){console.log("ddddd");})); 
```

clear：清空map数据结构中的数据

**语法：**

```
        //m.clear();
        //console.log(m);
```

forEach(callback),循环遍历Map数据结构

**语法：**

```
        m.forEach(function(value,key){
            console.log(value);
        });  
```

**常用属性**

size:获取Map数据结构的长度

**语法：**

```
        console.log(m.size);
```

## 常用运算符

### ...运算符

...运算符，分为两类，rest 剩余参数运算符、spread 扩展运算符。

#### rest剩余参数运算符

用于获取函数的多余或所有参数,将以“，”隔开的参数转换为数组。通常使用在形参中，将剩余实参序列转换为数组。

**语法：**

```
        // function f(b,...a){
        //     console.log(a);
        // }
        // f(1,2,4,6,7);
```

注：必须出现在形参的最后 

#### spread扩展运算符：

用于打散数据，将一个数组/对象，转为用“，”的参数序列，可以理解为rest 参数运算符逆运算，通常使用在实参的传递中，用来打散数据。

**语法：**

```
        // function f(a,b,c,d,r){
        //     console.log(a);
        //     console.log(r);
        // }    
        // let arr=[1,2,5,7,8,9,0,3,5];
        // f(...arr);
```

#### 作用：

1、展开数组/对象,复制数组/对象，对于基本数据类型深拷贝。

```
        // let arr=[1,2,5,7,8,9,0,3,5];
        // let newArr=[...arr];
        // arr[5]=30;
        // console.log(newArr);
        // let user={username:"admin",pwd:124};
        // let newUser={...user};
        // user.pwd="aaaaaaaa";
        // console.log(newUser);
```

2、合并数组/对象，注：键名相同的值，会被覆盖。

```
        // let user1={username:"admin",pwd:124};
        // let user2={username:"aaaaa"};
        // let user={...user1,...user2};
        // console.log(user);
```

3、将伪数组（类数组）转换为真正的数组

```
    <button>1</button>
    <button>2</button>
    <button>3</button>
    <script>
        let btns=document.getElementsByTagName("button");
        console.log([...btns]);
   </script>     
```

4、将数组转换为特殊对象，键名是原数组的下标，键值是原数组的对象。

```
        let arr=[1,2,4,5,7,8];
        console.log({...arr}['1']);
```

注：扩展运算符对数组和对象操作时，对数值是深拷贝，如果里面有嵌套对象和数组，其存储的为地址，会改变原内容。

### 可选操作符

可选操作符，当不确定数据是否含有键名对应值的时候，可以采用可选操作符，进行输出，，好处不会对不存在键名报错，会将不存在键名的值以undefined的形式输出。

**案例：**

```
        // let users={user1:{username:"admin"},user2:{username:"admin2"}};
        // console.log(users.user1.pwd);//undefined
        // console.log(users?.user1?.pwd?.pwd1);//undefined
```

### 空值合并运算符

空值合并运算符,处理显示undefined和null数据类型，可以将数据类型显示为""。

**案例：**

```
        // let a=null;
        // console.log(a??"");//""
```

## 解构赋值

### 概念

ES6 允许按照一定模式（即规则），从数组和对象中提取值，对变量进行赋值，这被称为解构赋值（Destructuring）。解构赋值是对赋值运算符的扩展。

### 数组的解构

**语法：**

```
        //形式1：let [变量名,变量名,变量名,变量名]=[值,值,值,值];
        //形式2：let 变量名,变量名,变量名,变量名;
```

#### 解构的形式

**1）完全解构**

```
        // let [a,b,c]=[1,2,3]; 
```

**2）不完全解构（值比变量多）** 

```
        // let [,,a]=[1,2,3];
```

**3）解构失败（变量比值多）**

```
        // let [a,b,c]=[1,2];
```

**4）缺省方式**

```
        // let [a,b]=[undefined,2];
       // let [a,b]=[null,];
```

**5）嵌套解构**

```
        // let [,,[,,[a]]]=[1,2,[4,6,[7,8]]];
```

#### 默认值

**1、默认值**

```
 let [a=1,b]=[];
```

**2、默认值+解构**

```
let [a=1,b]=[3,4];
```

**3、默认值+解构中的undefined**

```
let [a=1,b]=[undefined];
```

**4、默认值+解构中的null**

```
let [a=1,b]=[null];
```

#### 应用场景

数组值的交换

```
        let a=1;
        let b=2;
        let c=3;
       [a,b,c]=[b,a,a];
```

### 对象的解构

**语法：**

```
//语法1：
        //let {键名:变量名,键名:变量名,键名:变量名}={键名:值,键名:值,键名:值};
//语法2：
        //let {变量名,变量名,变量名}={键名:值,键名:值,键名:值};
```

#### 解构形式

**1）完全解构**

```
let user={username:"admin",pwd:"123456"};
let {username,pwd}=user;
```

**2）不完全解构（值比变量多）**

```
let {pwd}=user;
```

**3）解构失败（变量比值多）**

```
let {a}=user;
```

**4）复合型解构**

```
let {sex:{b}}={sex:{a:"a",b:"vv"}};
```

#### 默认值

**1、默认值**

```
        //let {a:a=1}={};
        // let {a=1}={};
```

**2、默认值+解构**

```
let {a=1}={a:3};
```

**3、默认值+解构中的undefined**

```
let {a=1}={a:undefined};
```

**4、默认值+解构中的null**

```
let {a=1}={a:null};
```

#### 应用场景

1、JSON格式数据的解构

2、对象的解构赋值，使用在形参的默认值

```
// function f(){
        //     return {username:"admin",pwd:"123456"};
        // }
        // let {pwd}=f();
```

3、对象的解构赋值，使用在函数返回值的解构

```
        function f({username,pwd}){
            console.log(username);
        };
        f({username:"admin"});
```

## 函数的扩展

### 箭头函数

#### 函数的定义：

函数就是将一段具有独立功能的代码块整合到一个整体并命名，在需要的位置调用这个名称即可完成对应的需求，从而更有效的实现代码重用。

#### 回调函数概念：

以参数的形式，将一个函数传递给另一个函数。

#### 箭头函数概念：

ES6 允许使用“箭头”（=>）定义函数。简化回调函数和普通函数的写法。箭头函数必须先执行后调。

**语法：**

```
let b=()=>{console.log("我是箭头函数的匿名函数！");};
```

##### 箭头函数的参数：

(1)无参数

```
let a=()=>{};
```

(2)一个参数：变量名=参数=>{函数体}，即，可以将（）省略。

```
let b=a=>{console.log(a);}
```

(3)多个参数 ：变量名=(参数1，参数2)=>{函数体}

```
let c=(m,n)=>{}
```

(4)剩余参数

```
let a=(...a)=>console.log(a);
```

##### 箭头函数的返回值：

1、完整写法的返回值形式 

```
let b=(m,n)=>{console.log(`我是${m}`);};
```

2、只有一行代码，{}可以省略

```
let a=m=>console.log(`我是${m}`);
```

3、只有一行代码的返回值， return可以省略

```
let a=m=>++m;
```

4、返回对象

```
let b=()=>({username:"admin",pwd:123});
```

##### 箭头函数使用注意事项：

箭头函数不作为构造函数使用：

```
// let a=()=>{}//报错
// let aa=new a();
```

#### 箭头函数中的this指向：

箭头函数中，this不会指向当前环境，而是指向定义时所在的环境。

##### 特例语法：

(1)箭头函数直接调用打印this

```
		// let a=function(){
        //     console.log(this);//window
        // };
        // let b=()=>{
        //     console.log(this);//window
        // };
```

(2)绑定给事件的this

```
    <button id="btn1">按钮1</button>
    <button id="btn2">按钮2</button>
    <script>
        // document.getElementById("btn1").onclick=function(){
        //     console.log(this);//btn
        // }
        // document.getElementById("btn2").onclick=()=>{
        //     console.log(this);//window
        // }
    </script>    
```

(3)使用call尝试改变箭头函数的this指向 

```
        // let a=function(){
        //     console.log(this);//document
        // };
        // let b=()=>{
        //     console.log(this);//window
        // };
        // a.call(document);
        // b.call(document);
```

(4)在构造函数中包一个箭头函数尝试打印this指向

```
        //情况一
        // function f(){
        //     this.a=function(){
        //         return function(){
        //             console.log(this);//Window
        //         }
        //     }
        // }
        // let ff=new f();
        //     ff.a()();
        //情况二
        // function f(){
        //     this.a=function(){
        //         return ()=>{
        //             console.log(this);//a
        //         }
        //     }
        // }
        // let ff=new f();
        //     ff.a()();
        //情况三
        // function f(){
        //     this.a=()=>{
        //         return ()=>{
        //             console.log(this);//a
        //         }
        //     }
        // }
        // let ff=new f();
        //     ff.a()();
        //情况四
        function f(){
            this.a=()=>{
                return function(){
                    console.log(this);//Window
                }
            }
        }
        let ff=new f();
            ff.a()();     
```

### 函数的默认值：

**语法：**

```
// function f(username="aa",pwd="bb"){
//     console.log(username,pwd);
// }
// // f("admin","123123");
// f(null,undefined);
```

注：函数默认值如果需要生效必须在调用的时候，设置实参为undefined

## Promise与异步

### 同步与异步

#### 同步

主任务在执行多任务队列时，由上到下，由左到右依次执行。且下一个任务需要等待上一个任务执行结束后得到执行结果，再继续执行，即阻塞模式。

**同步案例**

index.html

```
console.log(1)
console.log(2)
alert(3)
console.log(4)
function sum(){
    return 1+1
}
let result = sum()
console.log( result );
```

#### 异步

主任务在执行多任务队列时，不需要等待上一个任务的执行结果，就可以执行下一个任务，当上一个任务执行完成后，会以状态、通知和回调来通知调用者。即非阻塞模式。

**异步案例**

定时器

```
function fn(){
   console.log( 44 );
   setTimeout( function(){
        let sum = 2+4
        console.log( sum,'2秒钟以后' );
   },2000 )
   console.log(33);
}
let s = fn(  )
console.log( s,'我是undefined' );
```

### 回调函数

在使用JavaScript时，为了实现某些逻辑经常会写出层层嵌套的回调函数，如果嵌套过多，会极大影响代码可读性和逻辑，这种情况被称为回调地狱（或回调）。

**目的**:异步代码同步化操作。

### promise对象

Promise对象，异步编程的一种解决方案。也称之为一个容器，里面保存着某个未来才会结束的事件（异步操作）的结果。在语法上，其从它可以获取异步操作的消息。

#### 语法

```
new Promise( (resolve,reject)=>{
        resolve()/reject();
} );
Promise.方法名()
```

**案例**

```
new Promise((resolve,reject)=>{
    /**
     * 异步操作的代码
    */
});
```

#### 状态

pending（进行中）、fulfilled（已成功）和 rejected（已失败）

#### 特点

1）对象的状态不受外界影响。
2）一旦状态改变，就不会再变。
3）Promise的状态不可逆。

#### 常用方法

**Promise.resolve()**

设置成功结果，可以将Promise对象的状态切换为成功状态。

```
// function f(){
//     return new Promise((resolve,reject)=>{
//         setTimeout(resolve,5000,"我是成功的结果");
//     });
// }
```

**Promise.reject()**

设置失败结果，可以将Promise对象的状态切换为失败状态。

```
// function f(){
//     return new Promise((resolve,reject)=>{
//         // console.log(age);
//         // let age=20;
//         //throw new Error("我是创建的错误");
//         setTimeout(reject,3000,"我是失败的结果");
//     });
// }
```

##### Promise.then(参数1callback，参数2callback)

then方法接受两个回调函数作为参数。

第一个回调函数是Promise对象的状态变为resolved时调用，获取成功状态的值。

第二个回调函数是Promise对象的状态变为rejected时调用,获取失败状态的值/代码运行时错误/获取自定义错误（注：不推荐使用此方法获取）。其中，第二个回调函数可以省略。

###### 语法

```
promise对象.then( (结果)=>{
   //代码块
}， [(失败)=>{
   //代码块
}]);
```

###### 案例

```
// f().then(data=>{
//     //console.log(data);
// },err=>console.log(err.message));
```

##### Promise.catch()

获取失败状态的值/代码运行时错误/获取自定义错误（推荐使用）

###### 语法

```
promise对象.catch( (异常)=>{
   //代码块
});
```

###### 案例

```
//f().then(data=>console.log(data)).catch(err=>{if(err)console.log(err.message)});
```

**Promise.finally(callback)**

永久执行的方法。

**案例：**

```
// f().then(data=>console.log(data))
//     .catch(err=>{
//         if(err)console.log(err)
//     }).finally(()=>{
//         console.log("我执行了");
//     });
```

##### Promise.all([p1,p2,p3,....pn])

同时执行多个 Promise 实例，并生成一个新的 Promise 实例。

###### 语法

```
Promise.all( [ pro1,pro2,... ] );
```

**注**
1）参数实例中必须全部都是fulfilled时，Promise.all()的状态才是fulfilled，否则状态就是rejected；
2）参数实例中如果使用catch捕获的错误或者异常，则不会触发Promise.all()的catch方法。

###### 案例

```
let p1=Promise.resolve("我时成功1");
let p2=Promise.resolve("我是成功2");
// let p3=Promise.reject("我是失败状态1");
// let p4=Promise.reject("我是失败状态2");
// let p5=new Promise((resolve,reject)=>{
//     setTimeout(reject,5000,"我是失败1")
// });
// let p6=new Promise((resolve,reject)=>{
//     setTimeout(reject,1000,"我是失败2")
// });
// Promise.all([p1,p2,p5,p6]).then(data=>{
//     console.log(data);
// }).catch(err=>{
//     if(err)console.log(err);
// });
```

#### 链式操作

then的回调函数中还可以有返回值，可以是promise对象（也可以是其它数据），都可以使用链式操作再进行调用下一个then函数进行接收结果。

##### 案例

```
new Promise(resolve=>{
    resolve("我是成功！");
}).then(data=>{
    //console.log(data);
    return data+"123";
}).then(data1=>{
    // console.log(data1);
    return data1+"ddddd";
}).then(data2=>{
    console.log(data2);
});
```

**注：**jQuery对象就是一个典型的链式操作对象。

## async函数

ES2017 标准将原有的async 函数，进行了升级，它是一个关键字，被async修饰的函数称为async函数。
async修饰的函数，默认会将返回值封装为一个Promise对象。

### 语法

```
async function name( ){
	let res1 = await 异步1
	let res2 = await 异步2
}
```

**注:**async函数只能获取成功状态的值。async可以单独出现，但await必须要在async函数中使用否则报错。

### 案例

```
function f(ms){
    return new Promise(resolve=>{
        setTimeout(resolve,ms,`我是异步${ms}`);
    });
}
async function ff(){
    let aa=await f(3000);
    console.log(aa);
    let bb=await f(5000);
    console.log(bb);
}
ff();
```

## class类

### 面向对象概述：

面向对象是一种以对象为中心的编程思想。面向对象是相对于面向过程来讲的，面向对象把相关的数据和方法组织为一个整体来看待。

### 面向过程和面向对象：

面向过程和面向对象，都是一种编程思想。两者解决问题的思维方式不同。

#### 面向过程：

面向过程思想强调的是步骤，当碰见问题时，思考的是“我该怎么做”，分析出解决问题所需要的步骤，一步步的去实现。

#### 面向对象：

面向对象思想强调的是结果，当碰见问题，思考的是“我该让谁来做”。这个“谁”就是对象。找合适的对象做合适的事情。而对象如何去做(采用什么样的步骤)就不需关心，最终把问题解决掉即可

### 面向对象编程：

面向对象编程其本质是以，建立模型体现出来的抽象思维过程和面向对象的一些方法。模型是用来反映现实世界中事物特征。方法就是模型所需要的行为动作。
在面向对象编程中，最常见的表现就是基于类(Class)来表现的，每一个对象实例都有具体的类，即对象的类型。

**面向对象特点：**封装，继承，多态，抽象。

### 类和对象： 

在面向对象编程过程中，有两个重要组成部分：类 和 对象。
类和对象的关系：用类去创建一个对象。

#### 类的概念：

类是对一系列具有相同特征和行为的事物的统称，是一个抽象的概念，不是真实存在的事物。类是由特征和行为组成的。特征即是属性、行为即是方法。

#### 对象的概念：

对象是类创建出来的真实存在的事物。

注：开发中，先有类，再有对象。

### 创建类： 

定义类名要满足标识符命名规则，同时遵循大驼峰命名习惯。

**语法：**

```
class Fruit{}
```

**实例化：**

```
let f=new Fruit();
```

### constructor

构造函数/构造器，初始化对象。在创建一个对象时默认被调用，不需要手动调用，同时可以定义形参。

**语法：**

```
    constructor(){
        console.log("我是水果构造");
    }
```

### 类的属性和方法： 

#### 实例属性和实例方法

表示当前对象的属性或方法。

**特点：**

实例属性/实例方法，通过当前的对象访问。如果是每个对象分别独立调用的, 则实例的属性和方法属于对应的对象。

**语法：**

```
    sweet="我很甜";
    eating(){
        console.log("我能吃！");
    }
```

**调用语法**

```
let f=new Fruit();
console.log(f.sweet);
f.eating();
```

#### 静态属性和静态方法

静态属性和方法指的是 class 本身的，即class.propName，而不是定义在实例对象（this）上的属性。

**特点：**

需要通过关键字 static 来进行修饰

**语法：**

```
static water="我有水分";
static drinking(){
        console.log("我可以榨汁！");
    }
```

**调用语法**

```
console.log(Fruit.water);
Fruit.drinking();
```

### 类的继承： 

面向对象的继承指的是多个类之间的所属关系，即子类默认继承父类所有的特性，体现了对属性和方法的复用性的提升。继承中的父类和子类：被继承的类称为父类，而继承父类的类称为子类。

#### 继承的优点：

(1)提高了代码的复用性。
(2)减少了代码量。

**语法：**

```
class 子类 extends 父类{}
```

注：如果子类中有constructor构造函数，那么必须在构造函数的第1行执行super()

#### super的使用

```
class Fruit{
    sweet="我很甜";
    static water="我有水分";
    constructor(){
        console.log("我是水果构造");
    }
    a(){
        return this.sweet;
    }
    eating(){
        console.log("我能吃！");
    }
    static drinking(){
        console.log("我可以榨汁！");
    }
}
class Apple extends Fruit{
    sweet="我苹果是酸的";
    static water="我是干的";
    constructor(){//子类的构造方法多态，必须要先调用父类的构造方法。
        super();//调用父类的构造方法
        console.log("我是Apple构造");
    }

    eating(){
        Fruit.drinking();
        super.eating();
        console.log("我是烂的"+Fruit.water);
    }
    static drinking(){
        super.drinking();
        console.log("我硬的"+super.water);
    }
}
```

## ES6模块化

在es6中模块功能主要由两个命令构成：export和import。export命令用于规定模块的对外接口，import命令用于输入其他模块提供的功能。

### 步骤

(1)使用规范暴露数据 

(2)使用规范引入模块

(3)设置script标签的属性 type="module"

### 关键词

#### import

##### 语法：

```
import { 变量 } 文件
import { 变量 as  新变量名 } 文件
```

案例

```
import "../jquery.min.js";
//import {getUser,a,bb as cc,getUsername} from "./index2.js";
import aa from "./index2.js";//export default引入模式。
```

#### export

##### 语法

```
export default 数据
export 定义关键词 变量名=值;
export function 方法名(){}
export {变量名,方法名}
```

##### 案例

```
// export function getUser(){
//     return {username:"admin",pwd:123456};
// }
// export let a=20;

// let b=20;
// function getUsername(){
//     return {username:"admin2"};
// }
// let c=40;
// //集成抛出方法/属性
// export{
//     b as bb,
//     getUsername
// }
//注：export关键词可以使用多次，最终会把所有的抛出汇总使用
export default 30;//export default有且只能使用一次。后面直接抛出数据。
```

### 浏览器引入

```
    <script src="./index.js" type="module"></script>
```

## iterator迭代器

### ES6中的四种数据结构：

数组（Array）、对象（Object），Map、Set

### 概念

iterator是 ES6 引入的一种新的遍历机制，它提供了一个统一的接口，它的作用是使各种数据结构可被便捷的访问，它是通过Symbol.iterator 的方法来实现。

### for…of：

for...of 是 ES6 新引入的循环，用于替代 for..in 和 forEach() 

#### 支持遍历的数据类型：

(1)Array
(2)arguments 
(3)Set数据结构
(4)Map数据结构
(5)String 
(6)NodeList对象 
(7)HTMLCollection 对象
(8)TypedArray

注：for...of不能遍历对象。

### iterator迭代过程： 

1、通过 Symbol.iterator 创建一个迭代器，指向当前数据结构的起始位置
2、通过 next 方法进行向下迭代指向下一个位置， next 方法会返回当前位置的对象，对象包含了 value 和 done 两个属性， value 是当前属性的值， done 用于判断是否遍历结束，当done的值为true时代表结束

#### 遍历过程流程图：

![图片1](E:/授课内容/中公/node课程/标准化笔记/2021长沙Web全栈面授就业班88班/img/图片1.png)

```
let arr=[1,2,5,7,3,6,89,0,8];
let p=arr[Symbol.iterator]();
// p.next();
// p.next();
// p.next();
// p.next();
// p.next();
// p.next();
// p.next();
// p.next();
// p.next();
// p.next();
// p.next();
// console.log(p.next());
p.next()
p.next()
p.next()
for(let item of p){
    console.log(item);
}
```

## ES新特性

#### ES6的新特性

class类，module模块化，箭头函数，函数参数默认值，promise对象，模板字符串，变量的解构赋值，对象的简写，let和const关键词

#### ES7的新特性

数组includes()方法

#### ES8的新特性

async/await、字符串的padStart()和字符串的padEnd()

#### ES9的新特性

...运算符

#### ES10的新特性

数组的flat()方法

#### ES11的新特性

globalThis，可选操作符，空值合并运算符

#### ES12的新特性

字符串的 replaceAll（），顶层await运算符

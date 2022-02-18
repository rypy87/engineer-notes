# ECMASCript

## ECMAScript简介

### 概念

我们俗称的ECMAScript(简称ES),指的就是ECMAScript 6.0(ES6)，是 JavaScript 语言的下一代标准，在 2015 年 6 月正式发布。它的目标，是使得 JavaScript 语言可以用来编写复杂的大型应用程序，成为企业级开发语言。

**ECMAScript与JavaScript的关系是**

前者是后者的规则，后者是前者的一种实现。

### 版本发展史

| **年份**  | **版本**                |
| ------- | --------------------- |
| 1997    | ECMAScript 1.0        |
| 1998    | ECMAScript 2.0        |
| 1999    | ECMAScript 3.0        |
| 2009/12 | ECMAScript 5.0        |
| 2015/06 | ECMAScript 2015(ES6)  |
| 2016/06 | ECMAScript 2016(ES7)  |
| 2017/06 | ECMAScript 2017(ES8)  |
| 2018/06 | ECMAScript 2018(ES9)  |
| 2019/06 | ECMAScript 2019(ES10) |
| 2020/06 | ECMAScript 2020(ES11) |
| 2021/06 | ECMAScript 2021(ES12) |

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

## 数据结构

### set数据结构

自带去重功能。类数组,可以存储任意数据类型。

**语法：**

```
new Set(数组/类数组)
```

#### 常用方法

##### add

set数据结构中添加元素数据，返回set数据结构本身

**语法：**

```
s.add("aaaa");
s.add({username:"aa"});
s.add(true);
s.add(function(){console.log("ssss");})
s.add(function aa(){console.log("ssssaaa");});
console.log(s);
```

##### delete

删除set数据结构中的某个元素数据，返回布尔类型，表示删除是否成功，仅支持基本数据类型。

**语法：**

```
s.delete("aaaa");
s.delete(function aa(){console.log("ssssaaa");});
s.delete({username:"aa"});
```

##### has

判断某个元素数据是否存在于set数据结构中，返回布尔类型，表示数据结构中是否含有该元素，仅支持基本数据类型。

**语法：**

```
console.log(s.has(true));
console.log(s.has({username:"aa"}));
```

##### clear

清空set数据结构中的数据，无返回值。

**语法：**

```
s.clear();
```

##### forEach

循环遍历Set数据结构

**语法：**

```
s.forEach(function(item){
    if(typeof item==="function"){
    	item();
    }else{
    	console.log(item);
    }
});
```

#### 常用属性

##### size

获取set数据结构的长度

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

#### 常用方法

##### set

向map数据结构中添加键值对数据

**语法：**

```
m.set("aaaa","ssssss");
m.set(true,{username:"aaaaa"});
m.set(123,"ddddd");
m.set(undefined,function aa(){console.log("ddddd");});
m.set(function (){console.log("ddddd");},"xaaaaa");
console.log(m);
```

##### get

获取map数据结构中参数键名的数据，只支持键名为基本数据类型。

**语法：**

```
console.log(m.get(undefined));  
m.get(undefined)();
console.log(m.get(function (){console.log("ddddd");}));
```

##### delete

删除map数据结构中的参数键名的数据，只支持键名为基本数据类型。

**语法：**

```
m.delete(undefined);
```

##### has

判断参数键名是否存在于map数据结构中,返回布尔类型，只支持基本数据类型。

**语法：**

```
console.log(m.has(undefined));    
console.log(m.has(function (){console.log("ddddd");})); 
```

##### clear

清空map数据结构中的数据

**语法：**

```
m.clear();
console.log(m);
```

##### forEach

循环遍历Map数据结构

**语法：**

```
m.forEach(function(value,key){
	console.log(value);
});  
```

#### 常用属性

##### size

获取Map数据结构的长度

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
(1)function fun(...values) {} 
(2)function fun(a,b,...values) {}
```

```
function f(b,...a){
	console.log(a);
}
f(1,2,4,6,7);
```

注：必须出现在形参的最后 

#### spread扩展运算符：

用于打散数据，将一个数组/对象，转为用“，”的参数序列，可以理解为rest 参数运算符逆运算，通常使用在实参的传递中，用来打散数据。

**语法：**

```
(1) ...[ ]  
(2)...{} 
```

```
function f(a,b,c,d,r){
    console.log(a);
    console.log(r);
}    
let arr=[1,2,5,7,8,9,0,3,5];
f(...arr);
```

#### 作用：

1、展开数组/对象,复制数组/对象，对于基本数据类型深拷贝。

```
let arr=[1,2,5,7,8,9,0,3,5];
let newArr=[...arr];
arr[5]=30;
console.log(newArr);
let user={username:"admin",pwd:124};
let newUser={...user};
user.pwd="aaaaaaaa";
console.log(newUser);
```

2、合并数组/对象，注：键名相同的值，会被覆盖。

```
let user1={username:"admin",pwd:124};
let user2={username:"aaaaa"};
let user={...user1,...user2};
console.log(user);
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

**语法：**

```
引用?.属性名/数组下标/函数/下标
```

**案例：**

```
        // let users={user1:{username:"admin"},user2:{username:"admin2"}};
        // console.log(users.user1.pwd);//undefined
        // console.log(users?.user1?.pwd?.pwd1);//undefined
```

### 空值合并运算符

空值合并运算符，用来解决变量不为undefiend和null，与逻辑运算符相比好处在于其如果为真则返回变量的值。

**语法：**

```
引用??为真返回值
```

**案例：**

```
let a=null;
console.log(a??"");//""
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

**语法：**

```
字符串.startsWith(参数字符)
```

```
let str="我是字符串，憨憨！";
console.log(str.startsWith("我是"));
```

#### endsWith

判断字符串是否以参数字符串结束，返回值是布尔类型。

**语法：**

```
字符串.endsWith(参数字符)
```

```
console.log(str.endsWith("！"));
```

#### repeat

重复拼接字符串参数次数，返回值是新的字符串。

**语法：**

```
字符串.repeat(重复次数)
```

```
console.log(str.repeat(4));
```

#### padStart

将字符串前置补全

**语法：**

```
字符串.padStart(目标长度，填充的字符)
```

```
console.log(str.padStart(20,"abc"));
```

#### padEnd

将字符串后置补全

**语法：**

```
字符串.padEnd(目标长度，填充的字符)
```

```
console.log(str.padEnd(20,"abc"));
```

#### replaceAll

查找并全部替换

**语法：**

```
字符串. replaceAll(目标字符，替换字符)
```

```
console.log(str.replaceAll("憨","mll"));
```

## 数组的扩展

#### 新增方法

##### Array.of

创建一个数组，解决 new Array的缺陷，即将类数组序列转化为真正的数组。

**语法：**

```
Array.of(元素序列)
```

```
console.log(Array.of(1,3));
```

##### Array.from

将类数组转换为真正的数组，返回值是一个新数组。

**语法：**

```
Array.from(类数组)
```

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

##### filter

循环遍历数组，根据回调函数中返回值的布尔类型，过滤当前数组元素，并生成新的数组。

**语法：**

```
引用.filter(callback)
```

```
console.log(persons.filter(function(item){return item.salary>55000;}));
```

##### includes

查询数组中是否含有参数元素，返回值是布尔类型。

**注：**此方法只支持基本数据类型

**语法：**

```
引用.includes(参数)
```

```
let arr=[1,2,4,7,8,9];
console.log(arr.includes(8));
```

##### flat

将多维数组降维。

引用. flat([depth])， depth取值是数字，默认值是1， Infinity直接降维1维，

**语法：**

```
引用.flat([depth])
```

注：depth取值是数字，默认值是1， Infinity直接降维1维。

```
let arr=[1,2,4,[2,3,5,67,8,[3,3,5,7,8,9]]];
console.log(arr.flat(Infinity));   
```

## 对象的扩展

对象（object）是 JavaScript 最重要的数据类型。ES6 对其进行了重大升级，包括（数据类型本身的升级和Object对象的方法）。

### 类型本身特性

#### 属性简写

键名的“”可以省略。

当变量名和对象中的属性名相同时，属性值可以省略。

**语法：**

```
{ 变量名1,变量名2 }
```

```
let newObj={username:"admin",pwd:123456};
let username="admin";
let age=20;
let newUser={username,age};
```

#### 对象中函数简写

对象中可以直接定义普通函数，一定程度降低了代码量，简写形式的函数中的this和function声明函数的this指向是相同的。

**语法：**

```
{  函数名(){} }
```

```
let newObj1={
	bb(){console.log("我是新对象中的函数");}
} 
newObj1.bb();
```

#### 属性名表达式

表达式可以使对象的属性/方法，更加灵活的运算，即中括号的用法(中括号中写表达式)。

**语法：**

```
let 变量名=变量值；
{[变量名/表达式]:对象变量值,[变量名/表达式](){}}
```

**调用：**

```
(1)对象.变量值
(2)对象[变量名]
```

**案例：**

```
let str="hello";
let i=0;
let obj={
    [`${str}user${++i}`]:"amdin",
    [`${str}${i+1}`](){console.log("我是函数");}
}
console.log(obj);
obj.hello2();
obj[`${str}${i+1}`]();
```

### 新增方法

#### assign

将参数2...参数n,合并给参数1，并生成新的对象，新对象与参数1一致。当键名相同的时候，会进行同名覆盖操作。基本数据类型深拷贝，复合数据类型浅拷贝。

**语法：**

```
Object.assign(参数1,...参数n)
```

```
let obj=Object.assign(user1,user2,user3);
user2.username.aa="sssss";
console.log(obj);
console.log(user1);
```

#### keys

将对象中的键名以一维数组的形式返回。

**语法：**

```
Object.keys(引用)
```

```
let user={username:"amdin",pwd:"123123"};
console.log(Object.keys(user));
```

#### values

将对象中的值以一维数组的形式返回。

**语法：**

```
Object.values(引用)
```

```
console.log(Object.values(user));
```

#### entries

将对象中的键值对以二维数组的形式返回。 键值对是一个一维数组。

**语法：**

```
Object.entries(引用)
```

```
console.log(Object.entries(user));
```

#### fromEntries

将数组格式的键值对/Map数据结构转换为对象，返回值是个对象。

**语法：**

```
Object.fromEntries( [[key,value], [key,value]] )
```

```
console.log(Object.fromEntries([["name","admin"],["pwd","123"]]));
```

### JSON对象

#### stringify

将对象/数组转换为JSON格式的字符串。

**语法：**

```
JSON.stringify(对象/数组)
```

```
console.log(typeof JSON.stringify(user));
```

#### parse

将JSON格式的字符串转换为对象/数组。

**语法：**

```
JSON.parse(JSON格式的字符串)
```

```
let str=JSON.stringify(user);
console.log(typeof JSON.parse(str));
```


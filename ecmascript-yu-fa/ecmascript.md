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

# MySQL数据库

## 一、数据库简介

### 概念

数据库（database，DB）是指，按照数据结构来组织、存储和管理数据的仓库。

### 数据库管理系统：

数据库管理系统（Database Management System，简称DBMS）：用来对数据进行管理的软件，它是数据库系统的核心组成部分。

#### 主要功能：

数据定义、数据操纵、数据库运行管理、数据库的建立和维护功能、数据通信。

\*\*常见的数据模型有：\*\*网状、关系、层次、面向对象。

![数据库管理系统](E:%5C%E6%8E%88%E8%AF%BE%E5%86%85%E5%AE%B9%5C%E4%B8%AD%E5%85%AC%5Cnode%E8%AF%BE%E7%A8%8B%5C%E7%AC%94%E8%AE%B0%5Cimg%5C%E6%95%B0%E6%8D%AE%E5%BA%93%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F.png)

### 常见的数据库管理软件（DBMS）

#### Oracle

Oracle Database，又称Oracle RDBMS、Oracle。是甲骨文公司的一款关系数据库管理系统。 特性：处理速度快，非常快，安全级别高，支持快闪以及完美的恢复（即硬件坏了，也可以恢复到故障发前一秒），可以做到30s内故障转移，网格控制，和数据仓库方面也非常强大。

#### MySQL

MySQL是一个小型关系型数据库管理系统，被广泛地应用在中小型企业级应用。也是甲骨文公司的一款产品。 \*\*特性：\*\*开放源码、高度非过程化、面向集合的操作方式、以一种语法结构提供多种使用方式。

#### OceanBase

OceanBase是由蚂蚁集团完全自主研发的企业级分布式关系数据库，创建于2010年。

\*\*特性：\*\*数据的强一致、高可用、高性能、在线扩展、高度兼容SQL标准和主流关系数据库、低成本。

\*\*应用企业：\*\*中国工商银行、南京银行、西安银行、网商银行、苏州银行、GCash 、DANA Wallet、常熟农商行、Easypaisa、中国人民保险、中华保险、招商证券、上投摩根、蚂蚁集团、浙江移动、山东移动、中国石化、数字江西。

#### MS SQLServer

SQLserver数据库是微软公司发布的一款RMDBS数据库，也就是关系型数据库系统。 \*\*特性：\*\*图形化用户界面、客户服务器体系结构、丰富的编程接口工具、与Windows NT完成集成、具有很好的伸缩性，

#### DB2

DB2是一系列混合数据管理产品，提供完整的 AI 支持的能力，旨在帮助您管理本地、私有云和公共云环境中的结构化和非结构化数据。目前隶属于IBM公司 \*\*特性：\*\*无限的扩展能力、应用透明、持续的高可用性。

### 数据库存储数据的方式：

取决于数据库的类型(数据模型不同)，并按照一定的规则进行存储。

#### 1、根据数据类型分类：

![数据库数据类型分类](E:%5C%E6%8E%88%E8%AF%BE%E5%86%85%E5%AE%B9%5C%E4%B8%AD%E5%85%AC%5Cnode%E8%AF%BE%E7%A8%8B%5C%E7%AC%94%E8%AE%B0%5Cimg%5C%E6%95%B0%E6%8D%AE%E5%BA%93%E6%95%B0%E6%8D%AE%E7%B1%BB%E5%9E%8B%E5%88%86%E7%B1%BB.png)

#### 2、根据特定属性分类

与 Excel 中数据的组织结构比较类似。每个 Excel 中，数据的组织结构分别为工作簿、工作表、数据行、列这 4 大部分组成 。

| **学生编号** | **姓名** | **年龄** | **性别** | **省份** | **学历** | **老师编号** |
| -------- | ------ | ------ | ------ | ------ | ------ | -------- |
| 2019001  | 小黄     | 19     | 男      | 北京     | 本科     | 10003    |
| 2019002  | 王明     | 18     | 男      | 天津     | 专科     | 10001    |
| 2019003  | 大江     | 19     | 女      | 河北     | 本科     | 10006    |

| **老师编号** | **姓名** | **性别** | **年龄** |
| -------- | ------ | ------ | ------ |
| 10001    | 彭老师    | 男      | 32     |
| 10003    | 张老师    | 女      | 25     |
| 10006    | 李老师    | 男      | 28     |

## 二、Mysql数据库的安装

安装步骤详见安装文档

mysql 官网：https://www.mysql.com/ mysql下载地址 https://dev.mysql.com/downloads/mysql/

**查看Mysql服务**

![MySQL服务](E:%5C%E6%8E%88%E8%AF%BE%E5%86%85%E5%AE%B9%5C%E4%B8%AD%E5%85%AC%5Cnode%E8%AF%BE%E7%A8%8B%5C%E7%AC%94%E8%AE%B0%5Cimg%5CMySQL%E6%9C%8D%E5%8A%A1.png)

命令行登录Mysql

```
mysql -u root -p
```

查看本地数据库命令

```
show database
```

## 三、数据库可视化工具

操作数据库最古老的方式为cmd。这种方式操作相对比较繁琐、命令无法保存。数据库可视化工具可以使开发者更高效的操作数据库。常用的数据库可视化工具Navicat,功能相对比较强大，支持数据库比较多。

安装步骤见安装文档。

### Navicat工具的使用

#### 建立数据库连接

1.点击连接选项卡。

2.创建对应数据库模型连接。

3.填写相关信息，如连接名、主机域名/主机IP地址、数据库端口号、数据库登录用户名、数据库密码。

4.点击测试连接按钮，出现测试成功后，点击确定按钮。

#### 查看本地数据库

1.鼠标左键点击左侧菜单栏的新建的数据库连接，打开连接。

2.找到需要查看的数据库双击，打开对应数据库。

#### 数据库的创建

1.右键点击连接，选择新建数据库。

2.填写数据库名、选择填写字符集(默认也可)，点击确定按钮，创建数据库成功。

#### 数据库表的创建

**学生信息表**

![学生信息表](E:%5C%E6%8E%88%E8%AF%BE%E5%86%85%E5%AE%B9%5C%E4%B8%AD%E5%85%AC%5Cnode%E8%AF%BE%E7%A8%8B%5C%E7%AC%94%E8%AE%B0%5Cimg%5C%E5%AD%A6%E7%94%9F%E4%BF%A1%E6%81%AF%E8%A1%A8.png)

1.打开数据库，点击表格选项卡，点击新建表表选项卡。

2.添加字段名，字段类型，字段约束等其它字段信息。

3.点击保存按钮，输入表名，点击确定按钮，完成创建。

#### 数据库表的备份与还原

**备份**

数据库备份是指将数据库进行备份以防数据丢失。

**基本步骤**

1.右键点击左侧栏需要备份的表格名字。

2.选择转储SQL文件。

3.选择对应的转储模式(结构和数据/仅结构)。

4.选择保存路径，填写文件名，点击保存按钮，备份成功。

**还原**

把备份好的数据库信息通过软件恢复到备份的状态。

**基本步骤**

1.右键点击左侧栏需要将表还原的数据库名中表的选项卡。

2.选择运行SQL文件。

3.选择文件栏，找到对应SQL文件的路径，点击开始按钮，还原完成。

#### 数据库表的增删改查操作

**查询数据**

双击表名打开数据库表，即可查询到该表的数据内容，但数据过多的时候，由于当前页只能显示1000条数据，可以按下菜单栏的箭头切换页码。

**添加数据**

在查询模式下，点击下菜单栏的"+"按钮，可以添加数据，添加好后，点击‘’√“按钮，确认，点击”X‘，取消。

**修改数据**

在查询模式下，点击单元格即可进行修改，修改后，点击‘’√“按钮，确认，点击”X‘，取消。

**删除数据**

在查询模式下，点击下菜单栏的"—"按钮，可以删除数据，删除好后，点击‘’√“按钮，确认，点击”X‘，取消。

## 四、数据库表结构

### 数据表的组成：

1.表名 2.列信息(字段名) 3.字段数据类型 4.字段约束信息

### 数据库表的相关概念

#### 表

一般情况下，每个项目都对应独立的数据库。不同的数据，存储到数据库的不同表中。

#### 行

表中的行，代表每一条具体的数据。

#### 字段(列)

表示具有同一特征的数据，且满足相应的字段约束。

#### 表与表的联系

有些表之间会以某个字段产生关系，即表与表的联系。

### mysql常见数据类型

#### 数值型

| **名字** | **类型**                                                        |
| ------ | ------------------------------------------------------------- |
| 位置整型   | **bit(M)**                                                    |
| 极小整型   | **tinyint(M)**                                                |
| 短整型    | **smallint(M)**                                               |
| 中整型    | **mediumint(M)**                                              |
| 整型     | **int(M)**、**integer(M)**                                     |
| 长整型    | **bigint(M)**                                                 |
| 单精度浮点型 | **float(M,D)**                                                |
| 双精度浮点型 | **double(M,D)**                                               |
| 高精度浮点型 | **numeric(M,D)**、**decimal(M,D)**、**dec(M,D)**、**fixed(M,D)** |
| 布尔类型   | **bool**、**boolean**                                          |

#### 字符串型

| 类型               | **说明**  |
| ---------------- | ------- |
| **char(M)**      | 定长字符    |
| **varchar(M)**   | 变长字符    |
| **binary(M)**    | 定长二进制字节 |
| **varbinary(M)** | 变长二进制字节 |
| **tinyblob**     | 二进制字符串  |
| **blob(M)**      | 二进制字符串  |
| **mediumblob**   | 二进制字符串  |
| **longblob**     | 二进制字符串  |
| **tinytext**     | 字符串     |
| **text(M)**      | 字符串     |
| **mediumtext**   | 字符串     |
| **longtext**     | 字符串     |

#### 日期时间类型

| **类型**             | **占用字节** |
| ------------------ | -------- |
| **datetime(fsp)**  | 8        |
| **Date**           | 3        |
| **timestamp(fsp)** | 4        |
| **year**           | 1        |
| **time(fsp)**      | 3        |

#### 枚举类型

| **类型**                   | **描述**                                          |
| ------------------------ | ----------------------------------------------- |
| **ENUM(‘v1’, ‘v1’……..)** | 一个ENUM列最多可以包含65535个不同元素。单个ENUM元素长度255，且索引是从1开始。 |
| **SET(‘v1’, ‘v1’……..)**  | 一个SET列最多可以包含64个不同元素。单个SET元素长度255，且索引是从1开始。      |

#### JSON类型

JSON类型的数据可以是NULL或者是JSON格式的数据，其它格式会报错。且默认值只可以设置为NULL。

### mysql常用的约束

auto\_increment——自动增加，不能定义表级约束 not null——非空，不能定义表级约束 default——默认值，不能定义表级约束，注：在Mysql8.0.13之后的版本默认值，可以是文字、常量或表达式。 unique——唯一。 check——限制列的取值范围，使用方式CHECK(条件) primary key——主键，即非空唯一。 CURRENT\_TIMESTAMP ——自动获取当前数据库的默认时间，注区分东八区。 foreign key——外键,使用方式，\[FOREIGN KEY] \[(列名)] REFERENCES 外表名 (外表列名) \[删除修改是否联动] UUID() ——自动生成十六进制的ID，此ＩＤ不会重复。

## 五、SQL结构化查询语言

### SQL语言基本概念

SQL（英文全称：Structured Query Language）是结构化查询语言，专门操作数据库和处理数据的编程语言。

#### SQL语句特点：

(1)SQL 是一门数据库编程语言 (2)SQL 语言在MySQL、Oracle、SQL Server等关系型数据库中是通用的。 (3)SQL语言不区分大小写，官方建议关键字使用大写，自己定义的变量用小写

#### 作用：

(1)可以对数据库进行增删改查操作 (2)可以对数据库中的表进行增删改查操作 (3)可以对数据库中的数据进行增删改查操作

#### SQL的关键词：

(1)主句select、insert 、update 、delete\
(2)子句where、and 和 or 、order by 、group by 、limit、join...on

### 数据库用户操作命令

#### 命令行登录Mysql的命令

```
mysql -u root -p
```

#### 修改指定用户密码的命令

```
ALTER USER 用户名@数据库服务器地址 IDENTIFIED WITH mysql_native_password BY 新密码;
```

### 结构化查询语言分类

通常分为两类DDL（Data Definition Language）数据定义语言和DML（Data Manipulation Language）数据操作语言。

#### 数据定义语言(DDL)

DDL（Data Definition Language）数据定义语言-用于定义和管理 SQL 数据库中的所有对象的语言，对数据库中的某些对象(如，database,table)进行管理。

常用关键字：create、alter、drop、truncate、comment、grant、revoke等

#### 数据操作语言(DML)

DML（Data Manipulation Language）数据操作语言-数据库的基本操作，SQL中处理数据等操作统称为数据操纵语言,

常用关键字：select、update、delete、insert等

### DDL数据库定义语法

#### 查看本地数据库命令

```
show databases;
```

#### 创建数据库

```
create database [ IF NOT EXISTS ] 数据库名 
[
CHARACTER SET utf8//默认数据库编码格式
| COLLATE utf8_general_ci //默认数据库排序规则
| [DEFAULT] ENCRYPTION [=] {'Y' | 'N'}//是否加密，默认是加密，此属性是在MySQL 8.0.16启用。
];
```

\*\*注：\*\*如果使用IF NOT EXISTS创建数据库，即使此表已经存在，也会执行成功。

#### 删除数据库

```
drop database  [IF EXISTS] 数据库名;
```

\*\*注：\*\*IF EXISTS，用于防止数据库不存在时产生错误。

#### 查看当前使用数据库

```
select database();
```

#### 切换到指定数据库

```
use 数据库的名字
```

#### 查看当前数据库中的所有表

```
show tables;
```

#### 创建表

```
create table [IF NOT EXISTS] 表名(
	字段名 字段类型 字段约束[,
	字段名 字段类型 字段约束,
	字段名 字段类型 字段约束],
	FOREIGN KEY (本表的字段名)] REFERENCES 外表名 (外表字段名)[,
	FOREIGN KEY (本表的字段名)] REFERENCES 外表名 (外表字段名)
	]
);
```

注：

1.如果使用IF NOT EXISTS创建数据表，即使此表已经存在，也会执行成功。

2.约束可以是多个，采用空格隔开即可。

3.外键必须放在创建字段的最后面

#### 删除表

```
delete table 表名;
```

#### 修改表结构

```
//查看表结构
desc 表名;
//修改表结构
alter table 表名 change 原列名 新列名 数据类型 [完整性约束];
alter table 表名 modify  原列名 数据类型  [完整性约束];
//添加表结构
alter table 表名 add [column] 列名 数据类型 not NULL default '123456' ;
//删除表结构
alter table 表名 drop [column] 列名;
```

### DML数据库操作语法

#### 添加数据语法

INSERT INTO 语句用于向数据表中插入新的数据。列和值要一一对应，多个列和多个值之间，使用英文的逗号进行分隔。

```
INSERT [INTO] table_name VALUES/value ( 值1,值2,... )
INSERT [INTO] table_name ( 列1,列2,... ) VALUES ( 值1,值2,... )
insert [into] table_name ( 列1,列2,... ) VALUES ( 值1,值2,... ), ( 值1,值2,... )
```

#### 删除数据语法

从指定的表中，根据WHERE条件，删除对应的数据，删除是不可逆的。

```
DELETE FROM 表名 [WHERE 列名=值]
```

#### 更新数据语法

用UPDATE指定要更新的表，用SET指定字段对应的新值，用WHERE指定更新的条件

```
UPDATE 表名 SET 列名=新值 [WHERE 列名=值]
```

#### 查询数据语法

查询所需数据，其返回结果被称为结果集。

```
SELECT * FROM 表名
SELECT 列名1[,列名2...] FROM 表名
```

语法1，从FROM指定的表中，查询所有的数据，\*代表所有列。 语法2，从FROM指定的表中，查询指定列（字段）的数据。

#### 去重查询语法

```
select distinct 列名 from 表名;
```

#### 子语句操作语法

**where语句**

WHERE 子句用于限定查询数据结果。常用在 SELECT、UPDATE、DELETE 语句中。where子语句中可以使用运算符。

**语法：**

```
主语句  where  子语句
```

**常用操作符：**

| **操作符**         | **说明**       |
| --------------- | ------------ |
| =               | 等于           |
| <>，!=           | 不等于          |
| >               | 大小于登录于       |
| <               | 小于           |
| >=              | 大于等于         |
| <=              | 小于等于         |
| between…and     | 特定范围之间       |
| like / like ‘%’ | 搜索特定模式       |
| or              | 只要满足任意一个条件即可 |
| and             | 同时满足多个条件     |
| in              | 多条件判断        |

**ORDER BY：**

用于按照某个字段进行排序，如果某列的值相同，还可以按照多列进行排序，默认为升序（ASC），降序使用（DESC）。

**语法**

```
主语句  ORDER BY 字段名1 [ASC | DESC], [ 字段名2 ASC | DESC ]
```

**常用函数：**

(1)count 函数用于返回查询结果的总数据条数

```
select count(*) from 表名;
```

(2)avg 求平均数

```
select avg(*) from 表名;
```

(3)sum求和

```
select sum(*) from 表名;
```

(4)max最大值

```
select max(*) from 表名;
```

(5)min 最小值

```
select min(*) from 表名;
```

(6)concat 合并列

```
select concat(字段名,字段名,字段名) from 表名;
```

(7)MD5加密函数(8.0版本)

```
select MD5(字段名) from 表名;
```

(8)sha加密函数(8.0版本)

```
select sha(字段名) from 表名;
```

(9)sha2(字符串，长度224，256，384，512，0)加密函数(8.0版本)

```
select sha2(字段名,长度) from 表名;
```

注：使用函数查结果，通常字段名是函数本身，可以使用As关键词设置别名，As也可设置表的别名。

#### limit语法

LIMIT语法，实现按序查找数据和分页功能，start 代表从第几行开始，默认从0行，size代表取几条

**语法：**

```
主语句  LIMIT [start,size]/[size]
```

#### 分页原理

```
select * from 表名 LIMIT [start,size]/[size]
```

注：LIMIT通常和ORDER BY一起配合使用来进行记录的分页显示，且limit属于MySQL扩展SQL92后的语法，其他数据库不通用。

#### 表的连接查询

每一个数据库表中，都是存放同一类型的数据，如学生表中只存储学生，教师表中只存储教师。

表连接分为内连接和外连接。区别在于，内连接仅选出两张表中互相匹配的记录，而外连接会选出其他不匹配的记录。通常用的是内连接。 外连接又分为左连接和右连接。 左连接：包含所有的左边表中的记录甚至是右边表中没有和它匹配的记录 右连接：包含所有的右边表中的记录甚至是左边表中没有和它匹配的记录

**语法：**

```
SELECT * FROM 表1 JOIN 表2 ON 条件
- JOIN ON
- LEFT JOIN 
- RIGHT JOIN
```

#### select完整语法

```
SELECT 
    字段名[ 表名.字段名 | 表别名.字段名 | 字段名 AS 字段别名 ] [...]
FROM table_name[as table_alias]
    [JOIN table_name2 ON 条件]-- 联合查询
    [WHERE....]-- 指定结果须满足的条件
    [GROUP BY....]-- 指定结果按照那几个字段来分组
    [ORDER BY....]-- 指定查询一个记录按一个或者多个排序
    [LIMIT 0,3]-- 指定查询记录‘0’为起始位置，‘3’为末尾位置
```

\*\*注：\*\*MySQL8.0支持DDL原子化操作，即批量操作。

## 六、Node操作Mysql

当数据库创建完成以后，需要服务器端开发者将数据库和服务器端应用进行关联，才能对数据进行操作。

### 登录注册过程分析：

#### 登录

请求将登录表单中的数据传递到服务器（Express），然后Express通过条件判断，匹配数据库中是否存在该数据，完全匹配采用查询语句（SELECT）。

#### 注册

请求将注册表单中的数据传递到服务器（Express），然后Express根据程序的规则约束判定用户名的存在性，符合条件会把数据添加到数据库中，采用添加语句（INSERT \[INTO]）。

### Node中操作数据库流程:

![Node操作数据库流程](E:%5C%E6%8E%88%E8%AF%BE%E5%86%85%E5%AE%B9%5C%E4%B8%AD%E5%85%AC%5Cnode%E8%AF%BE%E7%A8%8B%5C%E7%AC%94%E8%AE%B0%5Cimg%5CNode%E6%93%8D%E4%BD%9C%E6%95%B0%E6%8D%AE%E5%BA%93%E6%B5%81%E7%A8%8B.png)

### Node中操作数据库步骤

#### (1)下载所需第三方插件mysql模块

```
npm i mysql
```

#### (2)书写连接数据库代码

**1、引入插件**

```
const mysql=require(mysql);
```

**2、配置数据库连接信息，并建立连接**

**对象的形式配置**

```
let db=mysql.createConnection({
				host:'主机名',
				user:'用户名',
				password:'密码'
				port:'端口号',
				database:'要操作哪个数据库'
})
```

**字符串的形式配置**

```
let db=mysql.createConnection({
	mysql:"user:pass@host/db?debug=true&charset=BIG5_CHINESE_CI&timezone=-0700"
});
//mysql://user:pass@host/db?debug=true&charset=BIG5_CHINESE_CI&timezone=-0700
```

\*\*参数说明：\*\*数据库驱动的名字://用户名:密码!@数据库地址:数据库端口号/数据库的名字?是否支持debug打印&编码格式&连接失败抛错时间

**3、连接数据库，此步骤可以省略，若省略了，则数据库连接不上不会报错。**

```
db.connect(err=>if(err)console.log("数据库连接错误！"));
```

#### (3)执行SQL语句操作数据库

```
db.query(sqlstr,(err,results)=>{});
```

#### (4)关闭数据库

```
db. end([err=>if(err)console.log(“数据库关闭错误！")]);
db.destroy();
```

### Query语句执行增删改查

#### 执行增加语句

```
//完整版sql执行模式，此模式会造成sql注入式攻击
// db_conn.query(`insert users(username) value('adminss')`,(err,result)=>{
//     if(err)console.log(err);
//     if(result.affectedRows>0){
//         console.log("添加成功");
//     }else{
//         console.log("添加失败！");
//     }
// });
//占位符sql传参模式，占位符关键词 ? ,注：占位符，与参数之间必须一一对应
// db_conn.query(`insert users(username,pwd) value(?,?)`,['admin222',"sdfsdfxcvsdf"],(err,result)=>{
//     if(err){
//         if(err.message.includes("Duplicate entry")){
//             console.log("用户已存在！");
//         }else{
//             console.log(err);
//         }
//     }else{
//         if(result.affectedRows>0){
//             console.log("添加成功");
//         }else{
//             console.log("添加失败！");
//         }
//     }
// });
```

#### 执行修改语句

```
db_conn.query(`update users set pwd=? where username=?`,["zzzzz","admins"],(err,result)=>{
    if(err)console.log(err);
    else{
        if(result.affectedRows>0){
            console.log("修改成功！");
        }else{
            console.log('修改失败！');
        }
    }
});
```

#### 执行删除语句

```
db_conn.query(`delete from users where username=?`,["admins"],(err,result)=>{
    if(err)console.log(err);
    else{
        if(result.affectedRows>0){
            console.log("删除成功！");
        }else{
            console.log("删除失败！");
        }
    }
});
```

#### 执行查询语句

```
db_conn.query(`select * from users where username=? and pwd=?`,['admin','1234567'],(err,reslut)=>{
    if(err){
        console.log(err);
    }else{
        if(reslut.length>0){
            console.log("登录成功！");
        }else{
            console.log("登录失败，用户名或密码不正确!");
        }
    }
});
```

## 七、模块化封装数据库

1、新建数据库文件db.js

2、新建数据库参数配置文件db\_config.js

```
module.exports={
    host:"127.0.0.1",
    port:"3306",
    user:"root",
    password:"123456",
    database:"test2"
}
```

2、书写封装代码

```
const mysql=require("mysql");
const db_config=require("./db_config");
async function getDataBySQL(sql,data){
    const db_conn=mysql.createConnection(db_config);
    db_conn.connect(err=>{
        if(err)console.log("连接数据库失败，请联系数据库管理员！");
    });
    let resultData=await new Promise(resolve=>{
        db_conn.query(sql,data,(err,result)=>{
            if(err)resolve([err,null]);
            else resolve([null,result]);
        });
    });
    db_conn.end(err=>{
        if(err){
            console.log("关闭数据库失败，请联系数据库管理员！");
        }
    });
    return resultData;
}
module.exports={
    getDataBySQL
}
```

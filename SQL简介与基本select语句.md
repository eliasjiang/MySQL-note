# SQL简介与基本SELECT语句

## SQL概述

SQL（Structured Query Language）,是已使用关系模型的数据库应用语言。

### SQL分类

**DDL(Data Definition Languages,数据定义语言)**：定义不同数据库、表、视图、索引等数据对象，并进行创建、删除、修改等操作

**DML(Data Manipulation Language,数据操作语言)**：用于添加、删除、更新、查询数据记录

**DCL(Data Control Language,数据控制语言)**：用于定义数据库、表、字段、用户的访问权限和安全级别



## SQL语言规则与规范

### 基本规则

- SQL 可以写在一行或者多行。为了提高可读性，各子句分行写，必要时使用缩进
- 每条命令以 ; 或 \g 或 \G 结束
- 关键字不能被缩写也不能分行
- 关于标点符号
  - 必须保证所有的()、单引号、双引号是成对结束的
  - 必须使用英文状态下的半角输入方式
  - 字符串型和日期时间类型的数据可以使用单引号（' '）表示
  - 列的别名，尽量使用双引号（" "），而且不建议省略as

### 大小写规范

- **MySQL 在 Windows 环境下是大小写不敏感的**
- **MySQL 在 Linux 环境下是大小写敏感的**
  - 数据库名、表名、表的别名、变量名是严格区分大小写的
  - 关键字、函数名、列名(或字段名)、列的别名(字段的别名) 是忽略大小写的。
- **推荐采用统一的书写规范：**
  - 数据库名、表名、表别名、字段名、字段别名等都小写
  - SQL 关键字、函数名、绑定变量等都大写

## 基本SELECT语句

### SELECT ... FROM

语法：

```sql
SELECT   标识选择哪些列
FROM     标识从哪个表中选择
```

选择全部列：

```sql
SELECT *
FROM   departments;
```

选择特定列

```sql
SELECT department_id, location_id
FROM   departments;
```

### 列的别名

- 重命名一个列
- 便于计算
- 紧跟列名，也可以**在列名和别名之间加入关键字AS，别名使用双引号**，以便在别名中包含空格或特殊的字符并区分大小写。
- AS 可以省略
- 建议别名简短，见名知意



```sql
SELECT last_name AS name, commission_pct comm
FROM   employees;
```



### 去除重复行

```sql
SELECT DISTINCT department_id 
FROM employees;
```

![image-20220519154416422](E:\我的数据库\我的坚果云\发布文章\数据库笔记\image-20220519154416422.png)



### 空值与空值运算

所有运算符或列值遇到null值，运算的结果都为null



### 显示表结构

使用DESCRIBE 或 DESC 命令，表示表结构。

```mysql
DESCRIBE employees; 
DESC employees;
```


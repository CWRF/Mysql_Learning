#首先在#Ubuntu 安装mysql环境（离线压缩包方式)
<https://my.oschina.net/WWWW23223/blog/614608>
#开始的知识点
##基础
###登陆
终端输入：
```
mysql -u root -p
```
###查看系统有哪些数据库
```
SHOW DATABASES;
```
###创建数据库
```
CREATE DATABASE 数据库名;
```
###删除数据库
```
DROP DATABASE 数据库名;
```
##MySQL存储引擎
###查询MySQL存储引擎
存储引擎是MySQL的特点，它决定了MySQL数据库中的表可以用不同的方式存储
```
SHOW ENGINES;
```
可以查看MySQL数据库支持的存储引擎类型，还可以使用
```
SHOW VARIABLES LIKE 'have%';
```
查询默认的存储引擎
```
SHOW VARIABLES LIKE 'storage_engine';
```
###InnoDB存储引擎
MySQL存储引擎的一种，优势在于提供了良好的事务管理、崩溃修复和并发控制的能力，缺点在于读写效率差，占用数据空间较大。
##创建表
###语法
表名不能是SQL语言的关键字
```
CREATE TABLE 表名（属性名 数据类型 [完整性约束条件],
                  属性名 数据类型 [完整性约束条件],
                  .
                  .
                  .
                  属性名 数据类型
                  ）
```
###设置表的主键
主键是表的特殊字段。每个记录的主键值都不同，就像人的身份证号一样。主键可以是单一字段也可以是多个字段的组合
####单字段主键
属性名 数据类型 PRIMARY KEY

例如：设置stu_id作为主键
```
CREATE TABLE example1(stu_id INT PRIMARY KEY,stu_name VARCHAR(20),stu_sex BOOLEAN);
```
####多字段主键
PRIMARY KEY（属性名 1，属性名 2，···，属性名 n）

例如：设置stu_id和course_id两个字段作为主键，stu_id和course_id两者组合可以确定一个记录
```
CREATE TABLE example2(stu_id INT,course_id INT,grade FLOAT,PRIMARY KEY(stu_id,course_id));
```
####设置表的外键
如果字段sno是表A的属性，且依赖于表B 的主键，那么，称表B为父表，表A为子表，sno是表A的外键。

外键一定要关联父表的主键，且数据类型要一致；外键可以为空。

父表删除某条信息，子表中与之对应的信息也必须有相应的改变。
```
CONSTRAINT 外键别名 FOREIGN KEY(属性1.1,属性1.2,···,属性1.n) 
REFERENCES 表名(属性2.1,属性2.2,···,属性2.n)
```
例如：
```
CREATE TABLE example3(id INT PRIMARY KEY,stu_id INT,course_id INT,CONSTRAINT c_fk FOREIGN KEY(stu_id,course_id) REFERENCES example2(stu_id,course_id));
```
运行之后，example2表的主键：stu_id,course_id；外键：c_fk。外键依赖于父表的example2的主键stu_id,course_id

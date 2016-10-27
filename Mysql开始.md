#在Ubuntu安装mysql环境（离线压缩包方式)
<https://my.oschina.net/WWWW23223/blog/614608>
#在OS X安装mysql环境
<http://www.jianshu.com/p/fd3aae701db9>
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

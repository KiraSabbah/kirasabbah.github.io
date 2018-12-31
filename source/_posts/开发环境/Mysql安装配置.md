---
title: Mysql安装配置
pp: 开发环境
category:
  - 开发环境
tags:
  - 开发环境
  - mysql
abbrlink: fdfb491a
date: 2018-12-31 10:07:40
---



## Windows MySql安装配置（压缩包解压配置）

1. [MySql官网](https://dev.mysql.com/downloads/mysql/)下载对应版本的MySQL

2. 解压缩至指定目录，例如解压至`D:\mysql`

3. 新版MySql目录下没有data文件，先新建data文件夹，然后执行初始化命令，cd至mysql的`bin`目录，执行：

   ```
   mysqld --initialize-insecure --user=mysql
   ```

4. 在根目录下新建my.ini文件，在my.ini中添加如下字段

   ```
   [mysqld]
   port=3306
   character_set_server=utf8
   lower_case_table_names=2
   basedir=D:\\mysql
   datadir=D:\\mysql\\data
   sql_mode=NO_ENGINE_SUBSTITUTION,STRICT_TRANS_TABLES
   ```

   其中**port**为端口，默认3306；**basedir**为安装目录；**datadir**为数据库目录；**lower_case_table_names**为大小写设置（1大小写不敏感，2大小写敏感）

5. 命令行安装mysql服务，以管理员身份运行cmd，cd至mysql的bin目录，输入命令安装`mysqld --install mysql`,执行成功后即安装成功。

   - 启动服务`net start mysql`
   - 停止服务`net stop mysql`
   - 删除服务`mysqld --remove mysql`



### PS

1. [修改root密码的四种方法](http://www.jb51.net/article/39454.htm)
2. 常用命令
   - 列出MySql支持的所有字符集：`SHOW CHARACTER SET`
   - 当前MySql字符集设置：`SHOW VARIABLES LIKE 'character_set_%'`
   - 显示某数据库字符集设置：`SHOW CREATE DATABASE [数据库名]`
   - 显示某表字符集设置：`SHOW CREATE TABLE [表名]`
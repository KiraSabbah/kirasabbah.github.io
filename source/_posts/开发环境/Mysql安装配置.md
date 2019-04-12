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



Mysql的安装配置

> 本文环境
>
> 操作系统：Windows 10 64位
>
> Mysql版本：MySQL Community Server 8.0.15

本文只是简单的安装，详细安装以及高级配置请参考[官方文档](https://dev.mysql.com/doc/)。

<!-- more -->

## Windows MySql安装配置（压缩包解压配置）

英文好的可以直接参考[官方安装教程](https://dev.mysql.com/doc/refman/8.0/en/windows-install-archive.html)。以下是简单安装配置

1. [MySql官网](https://dev.mysql.com/downloads/mysql/)下载对应版本的MySQL

2. 解压缩至指定目录，例如解压至`D:\mysql-8.0.15-winx64`

3. 新版MySql目录下没有data文件夹(初始数据库)，执行初始化命令，cd至mysql的`bin`目录，执行：

   ```shell
   mysqld --initialize-insecure --console
   ```

   注意如果linux下需加`  --user=mysql`来指定数据库目录文件归mysql用户所有

4. 在根目录下新建my.ini文件，在my.ini中添加如下配置

   ```ini
   [mysqld]
   #端口，默认3306
   port=3306
   #表名大小写模式，Windows默认1；macOS上默认2；Linux上不支持2强制该值为0
   #0指定大小写存储区分大小写。1以小写存储不区分大小写。2指定大小写存储以小写比较
   lower_case_table_names=1
   #mysql根目录
   basedir=D:/mysql-8.0.15-winx64
   #数据库目录
   datadir=D:/mysql-8.0.15-winx64/data
   ```

5. 启动/停止mysql，cd至mysql的bin目录下，执行以下命令启动/停止：

   ```shell
   #启动命令
   mysqld --console
   
   #停止命令 ctrl+c或以下
   mysqladmin -u root shutdown
   ```

6. 如果需要也可以将mysql安装为windows服务，方便启动停止以及自动启动等。cd至mysql的bin目录下，执行以下命令（任选一）安装mysql服务（以管理员身份运行cmd）

   ```shell
   #安装服务，默认服务名为MySql
   mysqld --install
   #安装服务，指定服务名为localmysql
   mysqld --install localmysql
   #更多请访问官方文档
   ```

   服务安装完后可以使用如下命令

   - 启动服务`net start localmysql`
   - 停止服务`net stop localmysql`
   - 删除服务`mysqld --remove localmysql`

7. 由于上面第3步初始化数据库时使用的`--initialize-insecure`参数，创建的root用户的密码是空的。以下是更改root密码步骤：

   a. root无密码连接到服务器：

   ```shell
   mysql -u root --skip-password
   ```

   b. 设置密码

   ```mysql
   ALTER USER 'root'@'localhost' IDENTIFIED BY 'root-password';
   ```

   c. 使用密码登录

   ```shell
   mysql -u root -p
   ```

   


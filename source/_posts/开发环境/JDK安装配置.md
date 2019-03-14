---
title: JDK安装配置
pp: 开发环境
category:
  - 开发环境
tags:
  - 开发环境
  - JDK
abbrlink: f58f11ab
date: 2018-12-31 10:01:13
---



JDK的安装配置。由于Oracle在JDK8之后商用开始收费，所以这里记录了Oracle JDK和Oracle在[GPL License](https://openjdk.java.net/legal/gplv2+ce.html)协议下的OpenJDK的安装配置。两种版本的配置类似。

> 本文环境
>
> 操作系统：Windows 10 64位

<!-- more -->



### windows JDK 安装配置

#### Oracle JDK 安装配置

1. 下载jdk：[各版本下载地址](https://www.oracle.com/technetwork/java/javase/archive-139210.html)
2. 安装jdk至目录（自定义目录）：`C:\Program Files\Java\jdk1.8.0_181`
3. 配置环境变量
   * 在系统变量中**新增**变量`JAVA_HOME`，值为：`C:\Program Files\Java\jdk1.8.0_181`
   * 在系统变量中**新增**变量`CLASSPATH`，值为：`.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;`，注意开头的 "." 不能省略
   * 在系统变量`Path`中**添加**两个值:`%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin; `，";" 为值的分割符，注意这里是添加，不是替换，若原Path中的值不是 ";" 结尾，需加上“;”分隔
4. 安装验证：cmd窗口输入命令 `javac -version`，若输出配置的JDK版本信息即安装配置成功



#### Oracle OpenJDK安装配置

1. 下载JDK：[目前最新版本为11](http://jdk.java.net/11/)，其他版本可查看[jdk.java.net](http://jdk.java.net)
2. 将下载的Builds（这里下载的是openjdk-11.0.2_windows-x64_bin.zip）解压至目录，例如：`C:\Program Files\Java\jdk-11.0.2`
3. 配置环境变量：
   * 在系统变量中**新增**变量`JAVA_HOME`，值为：`C:\Program Files\Java\jdk-11.0.2`
   * 在系统变量`Path`中添加值:`%JAVA_HOME%\bin`
4. 安装验证：cmd窗口输入命令`javac -version`或`java -verison`，即可查看相应信息





### Linux JDK 安装配置（tar.gz解压安装）

1. 下载jdk（tar.gz）：[各版本下载地址](https://www.oracle.com/technetwork/java/javase/archive-139210.html)

2. 解压安装：解压jdk至某目录，这里解压至`/usr/lib/java`

3. 配置环境变量，这里直接配置在全局变量中，编辑`/etc/profile`，在末尾添加：

   ```
   export JAVA_HOME=/usr/lib/java/jdk1.8.0_121
   export JRE_HOME=${JAVA_HOME}/jre
   export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib
   export PATH=${JAVA_HOME}/bin:$PATH 
   ```

4. 输入：`source /etc/profile`，使配置生效

5. 安装验证：输入命令 `javac -version`，若输出配置的JDK版本信息即安装配置成功

   

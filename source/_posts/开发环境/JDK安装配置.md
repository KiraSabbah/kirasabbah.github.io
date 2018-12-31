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



### windows JDK 安装配置

1. 下载jdk：[各版本下载地址][1]
2. 安装jdk至目录（自定义目录）：`C:\Program Files\Java\jdk1.8.0_181`
3. 配置环境变量
   * 在系统变量中**新增**变量`JAVA_HOME`，值为：`C:\Program Files\Java\jdk1.8.0_181`
   * 在系统变量中**新增**变量`CLASSPATH`，值为：`.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;`，注意开头的 "." 不能省略
   * 在系统变量`Path`中**添加**两个值:`%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin; `，";" 为值的分割符，注意这里是添加，不是替换，若原Path中的值不是 ";" 结尾，需加上“;”分隔
4. 安装验证：输入命令 `javac -version`，若输出配置的JDK版本信息即安装配置成功



### Linux JDK 安装配置（tar.gz解压安装）

1. 下载jdk（tar.gz）：[各版本下载地址][1]

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



[1]: https://www.oracle.com/technetwork/java/javase/archive-139210.html
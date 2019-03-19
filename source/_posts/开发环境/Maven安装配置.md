---
title: Maven安装配置
pp: 开发环境
category:
  - 开发环境
tags:
  - 开发环境
  - Maven
abbrlink: 440a507c
date: 2018-12-31 10:03:49
---



Maven的安装配置。

> 本文环境
>
> 操作系统：Windows 10 64位

<!-- more -->

### Windows Maven 安装配置
1. [Maven官网][1]下载对应版本，例如`apache-maven-3.6.0-bin.zip`
2. 解压至某个目录，例如`D:/maven`
3. 配置环境变量（**不是必须**）
   - **新增**环境变量：`MAVEN_HOME`，值为安装根目录`D:\maven`
   - path中**新增**：`%MAVEN_HOME%\bin`;
4. 建议修改本机maven仓库：`D:/maven/confing/settings.xml`中找到**localRepository**，默认是注释的，取消注销根据需要修改，例如改为`<localRepository>D:/maven_repository</localRepository>`
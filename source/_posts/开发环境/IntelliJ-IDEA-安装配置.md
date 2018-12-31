---
title: IntelliJ IDEA 安装配置
pp: 开发环境
category:
  - 开发环境
tags:
  - 开发环境
  - IDEA
abbrlink: 53b6713c
date: 2018-12-31 10:06:56
---



### 下载安装

1. 下载：[官方下载地址](https://www.jetbrains.com/idea/download/ )
2. 安装：根据提示需要安装
3. 修改配置：主要对`{安装目录}/bin/`下的`idea.exe.vmoptions`和`idea.properties`文件进行配置修改
4. 运行：首次运行会进入运行向导，根据提示进行即可



### 默认配置修改推荐

1. 最好指定一个默认Project路径：`Setting->Appearance & Behavior-> System Setting`下的`Default directory`
2. Maven改为自己安装的，并使用安装中配置的本地仓库
3. 文件编码修改`Setting->Editor->File Encodings`，都改为`UTF-8`
4. Maven相关配置
5. 快捷键修改，可以直接使用eclipse的快捷键方案，**不建议**修改默认快捷键，用用就习惯了，这里只修改一个代码提示
   - 提示`Main menu->code->Completion->Basic`：默认是`ctrl+空格`，改成`alt+/`。但是`alt+/`已经被同目录下的`Cyclic Expand Word`占用，去掉或改掉`Cyclic Expand Word`的快捷键。





### 推荐@[judasn](https://github.com/judasn)的详细[IDEA教程](https://github.com/judasn/IntelliJ-IDEA-Tutorial)
---
title: Node.js安装配置
pp: 开发环境
category:
  - 开发环境
tags:
  - 开发环境
  - nodejs
abbrlink: e0a75e6f
date: 2018-12-31 10:07:22
---

Node.js的安装配置。

> 本文环境
>
> 操作系统：Windows 10 64位

<!-- more -->

1. [下载](https://nodejs.org/en/download/)，建议下载LTS版本
2. 安装程序，建议勾选**Add to PATH**，新版本中已经默认勾选
3. 安装验证：`node -v`查看安装的nodejs版本号，`node config ls`查看配置信息
4. 修改全局安装路径，默认是安装至C盘用户目录下的，改为默认保存至nodejs的安装目录（这里为D:\nodejs）。执行命令`npm config set prefix "D:\nodejs"`。*nodejs会自动寻找该路径下的node_modules文件夹为实际存放全局模块的路径，这也是为啥叫prefix不叫global的原因；以后安装的全局模块都会被放到D:\nodejs\node_modules下，跟默认内置的npm模块在一个文件夹中*
5. 修改cache路径：`npm config set cache "D:\nodejs\node_cache"`
6. 上面**第4和第5点**的配置修改后会在C盘用户目录下生成.npmrc文件，即配置信息，若上述方法修改后无效果，可以直接修改`D:\nodejs\node_modules\npm\npmrc`中的内容
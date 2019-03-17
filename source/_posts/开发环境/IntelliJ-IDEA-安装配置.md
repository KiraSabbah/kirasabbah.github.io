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



主流的针对Java的IDE应该就是[Eclipse](https://www.eclipse.org/)和[Intellij IDEA](https://www.jetbrains.com/idea/)了。从接触java开始就一直使用的eclipse，已经用的很顺手，各种快捷键也习惯了。人总是要尝试新事物，所以开始转而使用idea。用了两个月idea，各种智能各种快捷，真香~~~这里记录下安装以及简单配置。

> 本文环境
>
> 操作系统：Windows 10 64位
>
> Intellij IDEA：2018.3.3 Ultimate Edition
>
> JDK：Oracle OpenJDK 11

<!-- more -->

### 下载安装

1. 下载：[官方下载地址](https://www.jetbrains.com/idea/download/ )
2. 安装：根据提示需要安装
3. 修改配置（最好在第一次启动前）：主要对`{安装目录}/bin/`下的`idea.exe.vmoptions`和`idea.properties`文件进行配置修改
4. 运行：首次运行会进入运行向导，根据提示进行即可



### 默认配置修改推荐

1. 指定一个默认Project路径：`Setting->Appearance & Behavior-> System Setting`下的`Default directory`
2. Maven配置：Maven改为自己安装的，并使用安装中配置的本地仓库（setting->Appearance&Behavior->Path Variables中还有一个MAVEN_REPOSITORY最好也改掉，暂时还不知道干什么的:sweat_smile:）
3. 文件编码：修改`Setting->Editor->File Encodings`，都改为`UTF-8`
4. 悬停显示文档：`Setting->Editor->General`勾选`Show quick documentation on mouse move`默认延迟500毫秒
5. 自动import：`Setting->Editor->General->Auto Import`勾选`Add unambiguous imports on the fly` 下面一行的自动优化(去掉没使用的import)也可以勾选上。自动import是指使用一个类的时候自动import，如果多个则选择
6. 代码折叠：一行代码的方法默认是折叠的，如果不习惯可以改为不折叠`Setting->Editor->General->Code Folding`去掉勾选`One-line methods` 
7. 大小写不敏感提示：idea默认情况下是适配首个字母的大小写的，改为大小写不敏感。`Setting->Editor->General->Code Completion`去掉勾选`Match case`
8. 版本控制父目录提示：idea默认情况下的版本控制提示只提示在通过颜色当前变动的文件，父文件夹是没有提示的，当项目大改动分散时就不是很方便，改为父级也有相应的颜色提示。`Setting->Version Control`勾选上`Show directories with changed descendants`

### 快捷键修改

`Setting Keymap`进行快捷键修改，可以直接使用eclipse的快键键方案，但是**不推荐**对快键键进行修改，用用就习惯了，习惯了就真香了:joy:

### 推荐@[judasn](https://github.com/judasn)的详细[IDEA教程](https://github.com/judasn/IntelliJ-IDEA-Tutorial)
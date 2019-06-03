---
title: IDEA代码热更新
pp: 开发环境
category:
  - 开发环境
tags:
  - 开发环境
  - IDEA
abbrlink: 4af858b7
date: 2019-01-12 16:17:23
---

Intellij IDEA代码的热更新。在写项目时，idea默认是不会自动热更新代码的，要看效果需要重新编译启动。很多人的方案是将idea改为自动编译，然后更新代码，但是这种方案会导致项目不断的重新加载，稍微一点改动甚至换个行就会触发，导致资源浪费电脑卡顿。所以这里使用另一个方案，只有手动触发才重新加载代码，并且是在Debug模式下。

<!-- more -->

### JAVA Web项目Tomcat部署热更新

1. 打开`Project Structure`,设置`Artifacts`添加`war exploded`，如图所示，名字自定义

   {% asset_img tomcat-1-1.png %}

   添加后如下图：

   {% asset_img tomcat-1-2.png %}

2. 打开`Run/Debug Configurations`，配置部署信息，这里没有tomcat的话先添加，添加后设置`Deployment`,添加上一步设置的`Artifacts`

   {% asset_img tomcat-2-1.png %}

   添加完成后如下图：

   {% asset_img tomcat-2-2.png %}

3. 部署设置里面，将`On 'Update' action`（当执行更新动作时）设置成如图所示,，注意这里如果不是`war exploded`方式的`Artifacts`，是没有如图所示的选项的（Archive方式看名字就知道不能热更新）。下面的`On frame deactivation`（当失去焦点时）也可根据需要设置

   {% asset_img tomcat-3-1.png %}

4. 设置好后，run模式下java文件不会更新，debug模式下java和静态资源文件都会更新。至于怎么触发`Update`,默认快捷键是`Ctrl+F10`,或者可以手动点击 update按钮

5. 如果是使用构建工具的构建的，一般上面的1,2步骤是不需要操作的



### Spring Boot/Spring Cloud项目热更新

设置方法与上面类似，选择对应的`Artifacts`,修改更新操作默认方式，Debug启动即可



> 本文环境
>
> 操作系统：Windows 10 64位
>
> Intellij IDEA：2018.3.3 Ultimate Edition
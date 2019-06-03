---
title: Docker简单安装配置
pp: 开发环境
category:
  - 开发环境
tags:
  - 开发环境
  - Docker
abbrlink: 7dd83663
date: 2019-06-03 22:31:14
---

[Docker](https://www.docker.com)，一个开源容器引擎，简直神器，反正用了之后就再也戒不掉了，安装使用也很简单，[官网文档](https://docs.docker.com)有很详细的教程。Docker分**CE**（Community Edition，社区免费版）和**EE**（Enterprise Edition，企业版）版本。本文记录下**Docker CE**的安装以及简单配置。

<!-- more -->

### CentOS 下安装 Docker CE

[官方安装文档](https://docs.docker.com/install/linux/docker-ce/centos/)已经说的很详细了，这里只列出关键步骤：

1. 卸载老的版本

   ```shell
   $ sudo yum remove docker \
                     docker-client \
                     docker-client-latest \
                     docker-common \
                     docker-latest \
                     docker-latest-logrotate \
                     docker-logrotate \
                     docker-engine
   ```

2. 安装所需的包

   ```shell
   $ sudo yum install -y yum-utils \
     device-mapper-persistent-data \
     lvm2
   ```

3. 设置仓库

   ```shell
   $ sudo yum-config-manager \
       --add-repo \
       https://download.docker.com/linux/centos/docker-ce.repo
   ```

4. 安装Docker CE

   ```shell
   $ sudo yum install docker-ce docker-ce-cli containerd.io
   ```

5. 启动

   ```shell
   $ sudo systemctl start docker
   ```

Docker已经可以使用。



### Window10 安装Docker CE

Docker CE在Window中安装条件比较多，官方安装文档](https://docs.docker.com/docker-for-windows/install/)有详细的说明。Windows下Docker的运行依靠虚拟机，Win10中可直接使用Hyper-V，没启用的话安装过程会提示开启。

[下载](https://hub.docker.com/editions/community/docker-ce-desktop-windows)安装没什么好说的，由于Docker依靠Hyper-V，默认虚拟机文件是存在C盘，这里将虚拟机路径改至其他目录，例如`D:\Hyper-V`。

1. 在D盘新建`Hyper-V`文件夹

2. 打开Hyper-V管理器，点击如图Hyper-V设置：

   {% asset_img hv.png %}

3. 根据需要将图中的虚拟机和虚拟磁盘更改目录：

   {% asset_img hvset.png %}

4. 如果Docker没启动的话，直接启动即可，已经启动了重新启动即可，启动后虚拟机文件即存储在指定目录：

   可以在Hyper-V中查看：

   {% asset_img hvshow1.png %}

   {% asset_img hvshow2.png %}

   也可在Docker的Setting中查看：

   {% asset_img dockersetting.png %}
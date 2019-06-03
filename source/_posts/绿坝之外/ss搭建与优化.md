---
title: ss搭建与优化
pp: 绿坝之外
category:
  - 绿坝之外
tags:
  - Shadowsocks
  - 科学上网
abbrlink: 1918433b
date: 2019-01-01 21:45:06
---

shadowsocks服务端安装配置。

<!-- more -->

### VPS

首先准备VPS，如果还没有，看这里[VPS推荐以及一些基本配置](https://blog.kira.ink/posts/ae129a0b.html)。



### Shadowsocks搭建

如果VPS不是OpenVZ虚拟方式，推荐用Docker来安装部署，简直方便，看这里[Docker搭建SS以及v2ray](https://blog.kira.ink/posts/7dd83663.html)。

OpenVZ虚拟方式下，Shadowsocks服务器端的搭建课可以参考官方的或者省事直接使用[teddysun](https://github.com/teddysun/shadowsocks_install)的一键安装脚本。脚本安装过程中会有一步一步的配置信息，如果不懂就把他搞懂，实在搞不懂，默认就行。

```shell
wget https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks.sh
chmod +x shadowsocks.sh
./shadowsocks.sh 2>&1 | tee shadowsocks.log
```

安装完之后会输出配置信息以及`Enjoy it!`，至此，梯子已经搭建完成，已可以使用。



### 使用

下载各客户端的Shadowsocks输入服务器的配置信息即可使用，[安卓下载](https://github.com/shadowsocks/shadowsocks-android/releases)，[Windows下载](https://github.com/shadowsocks/shadowsocks-windows/releases)。IOS的自己找下吧（无IOS设备:joy:）



### 优化加速

常见加速的方案，**BBR**、**Kcptun**等。这里如果你的VPS虚拟方式不是*OpenVZ*的，直接BBR吧。

如果是*OpenVZ*方式的那可以通过**UML**、**LKL**等方式使用BBK，相当于在你的主机中再虚拟个主机，不过这需要Tun/Tap的支持，有的VPS厂商不开放。

这里如果一定要使用的**BBR**的话，推荐[tcp-nanqinlang](https://github.com/tcp-nanqinlang/wiki/wiki/lkl-rinetd)的OpenVZ 魔改 BBR - lkl-rinetd 一键脚本，无需Tun/Tap，只要64位系统都可以安装。以下是CentOS 7的单网卡脚本（更多脚本访问[tcp-nanqinlang wiki](https://github.com/tcp-nanqinlang/wiki)）：

``` shell
# CentOS 7 单网卡
wget https://github.com/tcp-nanqinlang/lkl-rinetd/releases/download/1.1.0/tcp_nanqinlang-rinetd-centos.sh
bash tcp_nanqinlang-rinetd-centos.sh
```



>  本文VPS环境：
>
> 操作系统：CentOS 7 64-BIT
>
> 虚拟方式：OpenVZ
---
title: ss搭建与优化
pp: 绿坝之外
category:
  - 绿坝之外
tags:
  - Shadowsocks
  - 翻墙
abbrlink: 1918433b
date: 2019-01-01 21:45:06
---



> 本文VPS环境：
>
> 操作系统：CentOS 7 64-BIT
>
> 虚拟方式：OpenVZ



### VPS

首先需要有一台国外的VPS，关于选择哪个服务商，选择什么国家地区机房，网上各种评测很多，更具需求自行选择。比较常见的就是[vultr](https://www.vultr.com/)和[Bandwagon(搬瓦工)](https://bwh8.net/)了。

选择好服务商和线路之后就是购买了，如果是纯用来搭梯子，一般最便宜的就足够了。购买好之后可以对VPS进行网速、配置、硬盘性能等进行测试。可以网上搜一些脚本，下面是[SunsetLast](https://github.com/SunsetLast/TestYourVPS)测试脚本的使用

```shell
wget https://raw.githubusercontent.com/oooldking/script/master/superbench.sh
chmod +x superbench.sh
./superbench.sh
```



### Shadowsocks搭建

Shadowsocks服务器端的搭建直接使用[teddysun](https://github.com/teddysun/shadowsocks_install)的一键安装脚本。脚本安装过程中会有一步一步的配置信息，如果不懂就把他搞懂，实在搞不懂，默认就行。

```shell
wget https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks.sh
chmod +x shadowsocks.sh
./shadowsocks.sh 2>&1 | tee shadowsocks.log
```

安装完之后会输出配置信息以及`Enjoy it!`，至此，梯子已经搭建完成，已可以使用。



### 使用

下载各客户端的Shadowsocks输入服务器的配置信息即可使用，[安卓下载](https://github.com/shadowsocks/shadowsocks-android/releases)，[Windows下载](https://github.com/shadowsocks/shadowsocks-windows/releases)。IOS的自己找下吧（穷，无IOS设备:joy:）



### 优化加速

优化加速的方案很多，**BBR**、**Kcptun**、**V2Ray**等。这里如果你的VPS虚拟方式不是*OpenVZ*的，直接BBR吧。

如果是*OpenVZ*方式的那可以通过**UML**、**LKL**等方式使用BBK，相当于在你的主机中再虚拟个主机，不过这需要Tun/Tap的支持，有的VPS厂商不开放。

这里如果一定要使用的**BBR**的话，推荐[tcp-nanqinlang](https://github.com/tcp-nanqinlang/wiki/wiki/lkl-rinetd)的OpenVZ 魔改 BBR - lkl-rinetd 一键脚本，无需Tun/Tap，只要64位系统都可以安装。以下是CentOS 7的单网卡脚本（更多脚本访问[tcp-nanqinlang wiki](https://github.com/tcp-nanqinlang/wiki)）：

``` shell
# CentOS 7 单网卡
wget https://github.com/tcp-nanqinlang/lkl-rinetd/releases/download/1.1.0/tcp_nanqinlang-rinetd-centos.sh
bash tcp_nanqinlang-rinetd-centos.sh
```

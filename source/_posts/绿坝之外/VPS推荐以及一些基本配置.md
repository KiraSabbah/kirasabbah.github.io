---
title: VPS推荐以及一些基本配置
pp: 绿坝之外
category:
  - 绿坝之外
tags:
  - VPS
  - 科学上网
abbrlink: ae129a0b
date: 2019-06-02 22:44:03
---

购买国外VPS一般用来科学上网，所以一个稳定可靠的VPS至关重要，本文推荐我一直在使用的VPS以及一些基本配置

<!-- more -->

### 国外VPS推荐

这里只说下我使用过的几个VPS，其他VPS选择评测可以到[国外主机评测](https://www.zhujiceping.com)看看。选择的时候尽量不要选择openvz的虚拟主机，会有很多限制，关键是不能使用docker，没有docker，那折腾起来真的费劲。

- [Bandwagon(搬瓦工)](https://bwh8.net/)，以前一直使用，但是现在便宜的越来越难买到了。
- [HostMyBytes](http://www.hostmybytes.com)，很便宜，很稳定，网络还快，2.5美元一年，但是不久前被[AlphAracks](https://www.alpharacks.com)收购了，我的那台速度就慢慢下来了，但是依旧便宜。
- [Vultr][vultrlink]，这里重点推荐，机房多，地点多，而且按小时付费，IP被封或者想换机房直接销毁再部署一台，很方便，另外使用我的[Vultr推广链接][vultrlink]注册新用户充值任意金额可赠送50美元。

以上几个官网可能会被墙，可能无法访问，如果没有梯子，可以看这里的[ss免费账号](https://github.com/Alvin9999/new-pac/wiki/ss%E5%85%8D%E8%B4%B9%E8%B4%A6%E5%8F%B7)

### Vultr的一些基本配置

##### 服务器部署

根据自己的需要选择部署一台服务器，如果是用来科学上网，选择一个地点，最便宜的方案就行了，不用担心流量不够用，就算真的不够用，销毁了再建一个就是了。这里选择的方案是：

> Server Location: Tokyo
>
> Server Type: CentOS 7 x64
>
> Server Size: 25GB SSD / 1CPU / 1024MB Memory / 1TB Bandwidth （$5/每月）

选择好后等待安装完成，安装完成后会有一个IP，Ping下这个IP，延迟再可接受范围内即可。我经反复的创建部署，终于分配到一个延迟120ms的IP。有人说Tokyo的IP都不行，到了晚上丢包严重，但是我这个IP用到今天一直很稳定很快。反正不行就销毁重来。延迟只是反映了在当前网络环境下的情况，可以在网上搜下VPS测试的脚本，全方面测试下VPS。

##### 修改ssh端口

这个最好改下，防止暴力扫描。

1. 编辑 **/etc/ssh/sshd_config** 文件，找到注释的``#Port 22``，在下面一行添加``Port 22222``，这个表示ssh端口使用*22222*，ssh端口是支持多端口的，如果取消上面``#Port 22``注释，则表示*22*端口和*22222*端口同时可用。这个端口自己定义，不要使用1-1024，最好5000以后。
2. 使用命令``systemctl restart sshd.service``重启ssh服务
3. 防火墙添加允许端口：
   - ``firewall-cmd --zone=public --add-port=22222/tcp --permanent``，永久开放22222端口；
   - ``firewall-cmd --reload``，重新加载防火墙；
   - ``firewall-cmd --zone=public --list-ports``，查看当前开放的端口

注意以上是在Vultr的初始化默认CentOS 7环境下，其他环境略有差别。

##### 修改root密码/禁用root账户

这个不一定要改，要改的话网上搜下把。



至此一台VPS就准备好了，可以在上面做一些科学的事情了。



[vultrlink]: https://www.vultr.com/?ref=8096009-4F
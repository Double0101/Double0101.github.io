---
layout: post
title: VPS中搭建shadowsocks教程
date: 2017-08-05
categories: blog
tags: [搭建,shadowsocks]
description: 一条龙服务，从头到尾搭建ss教程

---


刚刚放暑假，为了暑假同学想从国外下Minecraft的脚本，放在自己的服务器上，然后正好我之前又有在包VPN（天行vpn），介于暑假时间比较长，我就直接买了一个季度的，我们两个人一起用，结果谁知，才刚刚包完一个季度没多久，国家就出台政策，封完了大部分的vpn，我的天，白白包了这么久。

其实像GreenVPN也被封了，但是人家至少比较有良心，给用户退费，可是天行真的太坑了，什么反应都没有，问客服也没回应。只好不了了之。

处于下策，为了翻墙，我只能选择更贵的VPS，来给自己搭一个shadowsocks，不过听说shadowsocks的作者被约谈了，不知道真的假的，github上

「搭建shadowsocks」

自己搭建shadowsocks有很多好处，比如自己一个人用一条线比较快，相比于VPN，ss不容易被封接下来进入正题，我们开始搭建shadowsocks。

首先你得有一台VPS，其实国外的VPS的提供商很多，我选择的是[digtialocean](https://m.do.co/c/35263bfe06ce)(可以通过该链接注册)这是官方提供的链接，绝对没啥问题，现在注册还可以获赠10美金，就相当于给你免费试用两个月，还是很划算的，不过需要用paypal或者国际信用卡支付，我选择的是纽约的线路，感觉用着还可以，日常用用没啥问题，我选择的是512MB／20GB／CentOS这个配置，5美金一个月。其他还有很多供应商，比如vultr和BandwagonHost，都是可以的。

创建好实例之后我们进入我们的VPS，如果经常要进其实可以用SSH，然后我们进入服务器，这里我用到了别人写的[一键安装包](https://shadowsocks.be/11.html)

```
wget --no-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks-all.sh
chmod +x shadowsocks-all.sh
./shadowsocks-all.sh 2>&1 | tee shadowsocks-all.log
```

然后你就跟着提示一步一步往下走就可以，安装完成后要是有什么不满意，可以直接修改/etc/目录下的配置文件shadowsocks.json。

这个时候你就可以通过你电脑上的shadowsocks来科学上网了，
我的是Mac，所以我选择了[ShadowsocksX-NG](https://github.com/shadowsocks/ShadowsocksX-NG)，如果你是windows就可以使用这个[shadowsocks-windows](https://github.com/shadowsocks/shadowsocks-windows)这两个软件好像作者说不更新了，不知道还能用多久。我想来配置ss的人应该或多或少都有一些技术，这些对你们来说应该不是很困难。

连上了ss后你会发现你可以翻墙了，速度还可以吧，可以用，比VPN快多了，但是我还想再快一点，嗯，这个时候你可以装一个[锐速](https://www.zhangchaoquan.com/index.php/linux/serverspeeder.html)链接里面很详细。安装完成之后你会发现，诶，你的ss快了不少，很流畅了已经。

其实还可以更快，你可以开启BBR加速算法，让你的代理更加流畅
以下是安装的方法，十分简单：

用root身份登录vps，输入如下命令：
```
wget –no-check-certificate https://github.com/teddysun/across/raw/master/bbr.sh
chmod +x bbr.sh
./bbr.sh
```

安装后重启

之后你就可以愉快的上网了










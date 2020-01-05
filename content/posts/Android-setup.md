---
title: 安卓 9.0 刷机跳过开机验证
tags: ["刷机"]
author: gravel
date: 2020-01-01 00:01:41 
---

昨天跨年夜给自己的老破旧刷机，双清之前忘记退出 Google 账号，导致无法正常跳过开机向导。这里简单记录一下解决方案。

<!--more-->

根据以往的经验：

1. 拔掉 sim 卡，关闭 wifi 功能，然后发现 Android9.0 似乎不能这么操作了。此条作废。 

2. 使用另外一个手机，科学上网，开热点。然后本机连接热点。不知道为什么也不行。推测热点没法直接转发科学上网的流量。此条作废。
3. 同上，使用另外的手机科学上网，不过使用了另外的网络转发软件 netshare ，这个软件可以做到转发科学上网的流量，不过需要在连接热点的时候设置代理，很奇怪的是，我的手机竟然设置不了手动代理。此条放弃，不过我感觉这种方式应该是可行的。
4. 电脑开代理，分享热点，也不行。

Google 了好久，看到有提到安卓开机向导是由 `/system/build.prop` 中的参数控制的。应该是可以通过修改这个文件的参数，解决这个问题。

1. 进入 recovery ，我的是TWRP

2. 进入mount选项，挂载上system

3. 进入 命令行操作

4. ```
   cd /
   vi /system/build.prop
   ```

5. 然后在这个文件中添加

```
ro.setupwizard.mode=DISABLED
```

然后重启系统，搞定

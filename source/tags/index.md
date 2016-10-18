---
title: Xcode 这个吃空间的怪物
date: 2016-10-14 17:35:22
---

相信有不少朋友和我一样硬盘的空间不大，特别是SSD的朋友

下面我们就来看看如何清除`Xcode`中可以删除的空间

1. 首先进入`/Users/yourusername/Library/Developer/Xcode`目录,其中记得修改`yourusername`为你自己的用户名
2. 进入`iOS DeviceSupport`目录
3. 这个目录底下就是可以删除的东西通常都比较大，可以节省很大的空间
4. 这里面其实就是你用xcode给别人的机器第一次装应用的时候要等很长时间的原因，xcode会找对应的device的版本号往里安装一些东西，可根据不需要的删除也可全删除，再次安装应用的时候如没找到对应的版本号，xcode还是会重新安装的，所以不必担心误删

最后上传一个截图

![](https://lizhaobomb.github.io/source/tags/xcode.png)
---
layout: post
title: Jarvis OJ RE classical crackme
date: 2021-04-13 18:18:32 +0900
category: RE
---
# Jarvis OJ RE classical crackme 

​		下载程序后，拖入exeinfope，如图所示。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image064.png" alt="image064" style="zoom:67%;" />

​		打开craceme.exe，随意输入一串数字测试，显示注册失败的字样。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image065.png" alt="image065" style="zoom: 50%;" />

​		接下来将crackme.exe放入.NET Reflector，搜索“注册”。可以看到首先取得用户输入的字符串，之后将字符串base64编码后赋给str2，再将str2与str3进行比较，如果相同则注册成功，那么str3的值显然就是注册码，题目提示flag就是注册码，因此我们将str3的内容进行base64解码。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image066.png" alt="image066" style="zoom: 50%;" />

​		解码后flag如图2所示，提交后成功。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image067.png" alt="image067" style="zoom: 67%;" />
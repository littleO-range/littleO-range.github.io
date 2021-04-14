---
layout: post
title: Jarvis OJ RE Android Normal
date: 2021-04-14
category: RE
---

# Android Normal

用模拟器打开apk文件，还是一个输入key的题。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image119.png" alt="image119" style="zoom: 50%;" />

反编译看java源码。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image120.png" alt="image120" style="zoom: 67%;" />

可以看到与正确的key有关的函数是stringFromJNI，再hello-libs中，所以我们查看so文件。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image121.png" alt="image121" style="zoom: 67%;" />

选择Java_com_didictf_hellolibs_MainActivity_stringFromJNI，反编译后，发现有一个字符串像是flag，到这里其实在前面补上“DDCT”再拼接这个字符串，就是正确的flag（因为DDCTF系列基本都是相同的开头以及一个邮箱的形式）。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image122.png" alt="image122" style="zoom: 67%;" />

不过还是再继续找一下，这里估计flag也不用计算了，应该就在内存里，这里直接查看这个文件的二进制形式，找到flag，如图所示。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image123.png" alt="image123" style="zoom: 67%;" />
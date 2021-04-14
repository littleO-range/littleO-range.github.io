---
layout: post
title: Jarvis OJ RE 爬楼梯
date: 2021-04-14
category: RE
---

# 爬楼梯

Apk文件，先用模拟器打开查看，如图所示。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image092.png" alt="image092" style="zoom: 50%;" />

每点击一下“爬一层楼”的按钮，“已爬的楼层”数量会增加一，“爬到了，看FLAG”的按钮无法点击。

将apk文件改为rar文件，然后解压，将解压后文件夹内的classes.dex文件反汇编为java源码。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image093.png" alt="image093" style="zoom:67%;" />

 接下来查看源码中MainActivity部分。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image094.png" alt="image094" style="zoom:67%;" />

分析源码可知，setClickable的参数决定了查看flag的按钮能否点击，当已爬楼层大于等于要爬楼层时，setClickable的参数为true，而小于时，为false，因此我们可以设法在小于情况下将其参数改为true，这样不用爬楼层就可以查看flag了。

接下来，利用apktoolbox反编译apk文件。 

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image095.png" alt="image095" style="zoom: 50%;" />

首先把反编译后的文件夹中的unknown文件夹删掉，否则之后回编译apk会出现问题。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image096.png" alt="image096" style="zoom:67%;" />

然后打开smali文件夹，找到MainActivity.smali文件，打开后，查找字符串setClickable。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image097.png" alt="image097" style="zoom: 50%;" />

共找到两处。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image098.png" alt="image098" style="zoom:67%;" />

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image099.png" alt="image099" style="zoom:67%;" />

对比找到的两个部分，不难推测出这里的v3和v5是传给setClickable的参数，因此我们需要修改代码第202行中v5的值与代码第111行中v3的0x1相同即可。
搜索v5，其值为0x0，将其修改为0x1，如图所示。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image100.png" alt="image100" style="zoom:67%;" />

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image101.png" alt="image101" style="zoom:67%;" />

修改完成后，保存文件，然后将文件夹回编译apk，用模拟器运行后，点击“爬到了，看FLAG”即可得到flag。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image102.png" alt="image102" style="zoom: 50%;" />
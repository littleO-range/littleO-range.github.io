---
layout: post
title: Jarvis OJ RE DD-Hello
date: 2021-04-13
category: RE
---

# DD-Hello

首先将文件拖入exeinfope中，文件类型不太了解，于是查了一下资料，Mach -O是通用二进制文件，因此尝试将此文件放入IDA64中，发现可以反汇编，因此接下来查看几个函数。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image083.png" alt="image083" style="zoom:67%;" />

首先有两个非常简单的函数start()和dummy()，函数本身没什么用，但后面计算flag会用到。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image084.png" alt="image084" style="zoom:67%;" />

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image085.png" alt="image085" style="zoom:67%;" />

 接下来查看函数sub_100000CE0，猜测此函数最后输出就是flag，而最后输出只用到变量v2和1000001040处的数组以及此函数中的for循环。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image086.png" alt="image086" style="zoom:67%;" />

因此这里先看变量v2，可以看到这里的第一个减法的两个操作数应该是指针指向了两个函数的地址，然后这两个地址做减法，之后转换成整数，再右移两位，最后与数组中的第一个数据做异或运算。
 因此这里需要找到两个函数的地址以及数组的内容。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image087.png" alt="image087" style="zoom:67%;" />

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image088.png" alt="image088" style="zoom:67%;" />

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image089.png" alt="image089" style="zoom:67%;" />

 数据获取完成后，利用python编写获得flag的算法，运行后得到flag。

```python
#DD-hello.py
s=0x100000CB0
d=0x100000C90
a=[0x41,0x10,0x11,0x11,0x1b,0x0a,0x64,0x67,0x6a,0x68,0x62,0x68,0x6e,0x67,
 0x68,0x6b,0x62,0x3d,0x65,0x6a,0x6a,0x3d,0x68,0x04,0x05,0x08,0x03,0x02,
   0x02,0x55,0x08,0x5d,0x61,0x55,0x0a,0x5f,0x0d,0x5d,0x61,0x32,0x17,0x1d,
   0x19,0x1f,0x18,0x20,0x04,0x02,0x12,0x16,0x1e,0x54,0x20,0x13,0x14]
x=((s-d)>>2)^a[0]
for i in range(0,55):
	a[i]=a[i]-2
	a[i]=a[i]^x
	x=x+1
for i in range(1,55): #反汇编代码中从byte_100001040[1]开始输出
	print(chr(a[i]),end="")
print("")

```

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image090.png" alt="image090" style="zoom:67%;" />
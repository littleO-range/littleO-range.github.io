---
layout: post
title: Jarvis OJ RE Android Easy
date: 2021-04-14
category: RE
---

# Android Easy

首先用模拟器打开apk文件，根据提示随意输入123456，提示密码错误。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image104.png" alt="image104" style="zoom: 33%;" />

因此反编译java源码，查看FlagActivity部分，关键部分如图所示。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image105.png" alt="image105" style="zoom: 67%;" />

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image106.png" alt="image106" style="zoom: 67%;" />

分析源码可知，首先定义了两个数组p和q，然后新建一个数组a1，长度与数组p相同，且其中每个元素的值都是p和q对应的值异或，之后定义一个值b为数组a1的第一个值，然后是一个for循环，数组a2就是随后的flag。

读懂源代码后利用python写一个相同的算法计算出flag即可。

```python
p = [ -40, -62, 107, 66, -126, 103, -56, 77, 122, -107, 
      -24, -127, 72, -63, -98, 64, -24, -5, -49, -26, 
      79, -70, -26, -81, 120, 25, 111, -100, -23, -9, 
      122, -35, 66, -50, -116, 3, -72, 102, -45, -85, 
      0, 126, -34, 62, 83, -34, 48, -111, 61, -9, 
      -51, 114, 20, 81, -126, -18, 27, -115, -76, -116, 
      -48, -118, -10, -102, -106, 113, -104, 98, -109, 74, 
      48, 47, -100, -88, 121, 22, -63, -32, -20, -41, 
      -27, -20, -118, 100, -76, 70, -49, -39, -27, -106, 
      -13, -108, 115, -87, -1, -22, -53, 21, -100, 124, 
      -95, -40, 62, -69, 29, 56, -53, 85, -48, 25, 
      37, -78, 11, -110, -24, -120, -82, 6, -94, -101 ]
q = [-57, -90, 53, -71, -117, 98, 62, 98, 101, -96, 
      36, 110, 77, -83, -121, 2, -48, 94, -106, -56, 
      -49, -80, -1, 83, 75, 66, -44, 74, 2, -36, 
      -42, -103, 6, -115, -40, 69, -107, 85, -78, -49, 
      54, 78, -26, 15, 98, -70, 8, -90, 94, -61, 
      -84, 64, 112, 51, -29, -34, 126, -21, -126, -71, 
      -31, -24, -60, -2, -81, 66, -84, 85, -91, 10, 
      84, 70, -8, -63, 26, 126, -76, -104, -123, -71, 
      -126, -62, -23, 11, -39, 70, 14, 59, -101, -39, 
      -124, 91, -109, 102, -49, 21, 105, 0, 37, -128, 
      -57, 117, 110, -115, -86, 56, 25, -46, -55, 7, 
      -125, 109, 76, 104, -15, 82, -53, 18, -28, -24 ]
aOB1=[]
for i in range(0,len(p)):
	aOB1.append(p[i]^q[i])
b=aOB1[0]
flag_len=int(0)
while(aOB1[b+flag_len]!=0):
	flag_len=flag_len+1
j=int(0)
flag=""
while(j<flag_len):
	flag=flag+chr(aOB1[b+j])
	j=j+1
print(flag)

```

运行后可以得到flag。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image107.png" alt="image107" style="zoom: 80%;" />
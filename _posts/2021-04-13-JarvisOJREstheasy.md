---
layout: post
title: Jarvis OJ RE stheasy
date: 2021-04-13
category: RE
---

# stheasy

 首先将文件拖入exeinfope。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image076.png" alt="image076" style="zoom:67%;" />

之后可以直接将文件拖入IDA，找到main函数，然后反汇编查看。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image077.png" alt="image077" style="zoom:67%;" />

 可以看到有一个对用户输入的字符串进行处理的关键函数sub_8048630，那么接下来反汇编该函数。 

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image078.png" alt="image078" style="zoom:67%;" />

可以看到，正确flag的长度为29，每个字符是通过对数组8049B15中的数据进行运算，在将运算结果对应到8049AE0数组中得到的，因此我们找到这两个数组的内容。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image080.png" alt="image080" style="zoom:67%;" />

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image079.png" alt="image079" style="zoom:67%;" />

之后利用python编写一段程序，计算出flag。

```python
#stheasy.py
a=[0x48,0x5D,0x8D,0x24,0x84,0x27,0x99,0x9F,0x54,0x18,0x1E,0x69,
0x7E,0x33,0x15,
0x72,0x8D,0x33,0x24,0x63,0x21,0x54,0x0C,0x78,0x78,0x78,0x78,
0x78,0x1B]
b="lk2j9Gh}AgfY4ds-a6QW1#k5ER_T[cvLbV7nOm3ZeX{CMt8SZo]U"
flag=""
for i in range(0,29):
	flag=flag+b[int(a[i]/3-2)]
print(flag)
```

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image081.png" alt="image081" style="zoom:67%;" />


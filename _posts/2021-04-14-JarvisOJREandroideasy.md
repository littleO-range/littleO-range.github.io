---
layout: post
title: Jarvis OJ RE androideasy
date: 2021-04-14
category: RE
---

# androideasy

使用模拟器打开apk文件，如图所示。随意输入123456，提示flag错误。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image110.png" alt="image110" style="zoom: 50%;" />

查看源码中的MainActivity部分。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image111.png" alt="image111" style="zoom: 67%;" />

忽略掉循环中的验证部分，可以分析出flag就是数组s中的每一个值与0x17异或得到。因此直接利用python写出flag的算法。

```python
#androideasy.py
s=[113, 123, 118, 112, 108, 94, 99, 72, 38, 68,
   72, 87, 89, 72, 36, 118,100,78, 72, 87, 121, 
   83, 101, 39, 62, 94, 62, 38, 107, 115, 106]
flag=""
for i in range(0,len(s)):
	flag=flag+chr(int(s[i])^0x17)
print(flag)
```

运行后得出flag。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image112.png" alt="image112"  />
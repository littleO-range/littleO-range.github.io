---
layout: post
title: Jarvis OJ RE Findpass
date: 2021-04-14
category: RE
---

# Findpass

将apk文件用模拟器打开，随意输入key后提示错误。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image114.png" alt="image114" style="zoom: 33%;" />

接下来反编译此文件，查看java源代码，MainActivity部分如图所示。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image115.png" alt="image115" style="zoom: 67%;" />

可以看到这里arrayOfChar2是从src.jpg中获取的，然后前面还有一个字符串str，因为一直用的jd-gui看的源码，不知道这个str具体是哪一个字符串，后来发现jeb可以看到字符串是fkey，于是找到它的值，如图所示。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image116.png" alt="image116" style="zoom: 67%;" />

再查看源代码查看key值的计算方法，用python写一个类似的。

```python
#findpass.py
c1="Tr43Fla92Ch4n93"
src=open('src.jpg','rb')
src.seek(0,0)
c2=[]
for i in range(1024):
	c=src.read(1)
	c2.append(ord(c))
flag=""
for i in range(len(c1)):
	if c2[ord(c1[i])]<128 :
		tep=c2[ord(c1[i])]%10
	else:
		tep=(-(c2[ord(c1[i])]%128))%10
	if i%2==0:
		flag=flag+chr(ord(c1[i])-tep)
	else:
		flag=flag+chr(ord(c1[i])+tep)
print(flag)
```


运行后得到flag，注意提交格式为flag{}。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image117.png" alt="image117" style="zoom: 100%;" />
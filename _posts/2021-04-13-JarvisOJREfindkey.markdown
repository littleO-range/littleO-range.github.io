---
layout: post
title: Jarvis OJ RE Findkey
date: 2021-04-13
category: RE
---
# Findkey
本题为pyc文件，因此放到linux系统下，利用uncomple反编译成py文件。

打开findkey.py，如图2.2.4所示。

分析之后发现，此代码首先判断用户输入的字符串长度是否为17，不是17直接判错，如果是17，则将字符串逆序，之后对字符串的每个字符进行一个计算后与lookup中的某个值进行比较。举例说明比较方法，取flag[0]的ascii码，然后与pwda[0]的值相加，得到的结果与255做按位与运算，将得到的结果与lookup[(0+pwdb[0])]的值进行比较。

了解比较方法后，我们可以利用lookup数组，编写逆向算法来得出flag。先取i的值为0~16，然后取lookup[(i+pwdb[i])]这17个值，然后逐个减去pwda[i]与255按位与运算后的值（ascii码），再将ascii码转换为对应字符，得到长度为17的字符串，再对其逆序，就得到flag。
修改findkey.py如图2.2.5所示。

 运行文件，得到flag。
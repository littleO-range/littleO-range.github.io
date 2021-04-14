---
layout: post
title: Jarvis OJ RE smali
date: 2021-04-14
category: RE
---

# smali

由于对smali语言不熟悉，所以这题将smli文件做了两个转换，查看java源代码，首先用apktoolbox里面的smali.jar将smali源码（这里是Crackme.smali）转换为dex文件（这里是out.dex），然后再将dex文件转换为java源码就可以了。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image125.png" alt="image125" style="zoom: 67%;" />

接下来利用jd-gui打开源码，如图所示。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image126.png" alt="image126" style="zoom: 67%;" />

分析代码逻辑，大致是定义str2字符串为密钥，传给GetFlag函数的字符串就是需要解密的flag，解密前首先对两个字符串base64解码，解密方式是ECB模式下不填充的AES。

 接下来利用python写一个相同算法就可以了，运行后得到flag。

```python
#smali
import base64
from Crypto.Cipher import AES
key=base64.b64decode('cGhyYWNrICBjdGYgMjAxNg==')
flag=base64.b64decode('sSNnx1UKbYrA1+MOrdtDTA==')
cipher=AES.new(key,AES.MODE_ECB)
flag=cipher.decrypt(flag)
print(flag)
```

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_images/image127.png" alt="image127" style="zoom: 80%;" />
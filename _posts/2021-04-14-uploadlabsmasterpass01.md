---
layout: post
title: upload-labs-master-pass01
date: 2021-04-14
category: web
---

# upload-labs-master-pass01

打开第一关，选择pass01.php上传，跳出提示，发现只能上传jpg、png和gif类型的文件。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_upload_ima/image102.png" alt="image102" style="zoom:67%;" />

因此先修改pass01.php后缀为jpg，然后打开burp抓包然后修改文件后缀。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_upload_ima/image103.png" alt="image103" style="zoom:67%;" />

修改后如下图所示。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_upload_ima/image104.png" alt="image104" style="zoom:67%;" />

改包后，把包发送出去，文件上传成功。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_upload_ima/image105.png" alt="image105" style="zoom:67%;" />

接下来查看上传的文件。

<img src="https://github.com/littleO-range/littleO-range.github.io/raw/master/_upload_ima/image106.png" alt="image106" style="zoom:67%;" />
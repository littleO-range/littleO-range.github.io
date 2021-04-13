---
layout: post
title: Happy Birthday to My First Blog!
date: 2021-04-13
category: other
---
# Happy Birthday to My First Blog!
> 简单记录一下创建这个blog过程中的一些关键部分来纪念此blog的生日

### 1.上传/更新github仓库内文件

​		首先在D盘打开git bash，需要先将原仓库克隆到本地，此后D盘有了一个与仓库同名的文件夹。

```bash
littleO@DESKTOP-HCE8CCS MINGW64 /d
$ git config --global user.name "littleO-range"
$ git config --global user.email "08183046@cumt.edu.cn"
$ ssh-agent bash
$ ssh-add ~/.ssh/991104 #存ssh密钥的文件，默认为id_rsa，这里我改为991104
$ git clone git@github.com:littleO-range/littleO-range.github.io.git
```

​		之后修改文件夹内的文件，或者将需要上传的文件放到文件夹内，接下来再将本地文件夹上传到github上。

```bash
littleO@DESKTOP-HCE8CCS MINGW64 /d/littleO-range.github.io (master)
$ git add 文件名 #上传该文件
$ git add . #上传文件夹内全部文件
$ git commit -m "1"  #给此次修改一个备注
$ git push -u origin master
```

### 2.建立/删除与github仓库的远程连接

```bash
littleO@DESKTOP-HCE8CCS MINGW64 /d
$  git remote add origin 仓库地址 #建立
littleO@DESKTOP-HCE8CCS MINGW64 /d
$  git remote rm origin #删除
```


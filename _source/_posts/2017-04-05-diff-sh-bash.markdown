---
layout: post
title:  "bash与sh的区别"
date:   2017-04-05 15:14:26 +0800
categories: jekyll update
---
对于脚本文件split_str.sh
```
#!/bin/bash
str="hello,world,i,like,you,babalala"
arr=(${str//,/ })
for i in ${arr[@]}
do
    echo $i
done
```
sh split_str.sh运行时会出现Bad substitution的错误，而改成bash split_str.sh时没有问题。

于是顺手查了下 /bin/sh 与 /bin/bash 的区别，用 : 截取字符串不是POSIX 标准的。
区别
sh 一般设成 bash 的软链 (symlink)
```
ls -l /bin/sh  
lrwxrwxrwx 1 root root 4 Sep 14 04:45 /bin/sh -> dash  
```
在一般的 linux 系统当中（例外如 FreeBSD,OpenBSD 等），使用 sh 调用执行脚本相当于打开了bash 的 POSIX 标准模式
也就是说 /bin/sh 相当于 /bin/bash --posix
所以，它们之间的各种差异都是来自 POSIX 标准模式 和 bash 的差异，比如 用 : 截取字符串，不能用 let ， 遇错中断 等等，在使用时需要注意。
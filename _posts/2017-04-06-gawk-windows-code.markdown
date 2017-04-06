---
layout: post
title:  "awk处理windows编码文件时最后一个字段的问题"
date:   2017-04-06 16:31:26 +0800
categories: code
---
采用awk来处理文本文件，希望对其中的字段进行重新组合，以便于后续的处理。但是采用
```
awk -F'#' '{ print $1,$2,$3}’时正确显示
```
而换成
```
awk -F'#' '{ print $3,$2,$1}'时无法显示最后一个字段
```
在查阅了awk的语法后没有发现任何问题。
后来定位到是文件本身的问题。
也就是说我处理的文件的编码问题，该文件在windows上被打开编辑过，所以它的回车换行是windows的，必须转换成linux的，
^M就是元凶，
```
2:0xFD3515E21CA80E761EB9AD5D793BDB9F0D8F030F2DB39FD1200A7E^M$
2:0xFD3515E21CA80E761EB9AD5D793BDB9F0D8F030F2DB39FD1200A7E^M$
2:0xFD3515E21CA80E761EB9AD5D793BDB9F0D8F030F2DB39FD1200A7E^M$
2:0xFD3515E21CA80E761EB9AD5D793BDB9F0D8F030F2DB39FD1200A7E^M$
3:0xFdd515E21CA80E761EB9AD5D793BDB9F0D8F030F2DB39FD1200A7E^M$
```
转换的方法是
cat source.txt | tr -d "^M" > source2.txt
^M在shell中的输入方式为ctrl + v,然后松开v按m即可，

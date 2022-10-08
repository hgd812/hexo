title: 批处理.bat文件 一键实现 Git push
author: dong
tags: []
categories: []
date: 2022-10-06 23:56:00
---

每次push代码到仓库都需要敲那么几行代码，十分的不方便，新建一个==.bat文件==，写入如下内容，直接运行，便可实现一键push到仓库。
运行时直接将=git commit -m 后的内容=输入到Message提示后边即可。

```
set /p a=Message:
git add .
git commit -m "%a%"
git push
```

两种一键实现方法：

1. 在=Terminal=键入.bat文件名称，回车运行
2. =直接双击= .bat文件运行

来源引用

> [批处理.bat文件 一键实现 Git push](https://blog.csdn.net/qq_45613277/article/details/107067421)

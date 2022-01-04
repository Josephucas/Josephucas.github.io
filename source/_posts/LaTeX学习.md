---
title: LaTeX学习
date: 2022-01-04 19:19:58
categories:
tags:
description:
top:
---

<p align="right">latex基本使用技巧</p> 

[TOC]



<!-- more -->

## 几种编译器的区别

​	可选的编译器有 pdfLaTeX （默认）、XeLaTeX、LuaLaTeX。一般来说，pdfLaTeX 就够用了，但有些时候你可能需要其他类型的编译器。

​	通常情况下，西文文档使用`pdflatex`，中文文档使用`xelatex` 配合中文基础文档类（`ctex*`）。现在几乎很少使用 `latex` 进行编译了，没必要兜个大圈子。

​	只讲实用性。 `latex` 现在用得很少。 `pdflatex` 在我投稿英文期刊时用。 `xelatex` 在我处理中文文档时用。

- LaTeX 只支持 .eps 和 .ps 图片格式，所以如果你项目中的所有图片都是 .eps 格式，那么推荐你使用这个编译器。
- pdfLaTeX 支持 .png, .jpgg, .pdf 图片格式。它会把 .eps 文件转换为 .pdf 文件，这个过程会加长编译所需的时间。（在 Overleaf 中，pdfLaTeX 也许不能很好的支持 `pstricks`）
- XeLaTeX 和 LuaLaTeX 都支持 UTF-8、Truetype、OpenType。如果你要在文档中输入非拉丁字符，那么我们推荐你配合 `polyglossia` 包来使用这两个编译器。它们支持 .png, .jpg, .pdf, .eps 图片格式。
- XeLaTeX 支持 `pstricks`，但是 LuaLaTeX 不支持
- 你可以在基于 LuaLaTeX 的文档中直接使用 Lua 代码

> [[翻译] [Overleaf] 选择 LaTeX 编译器](https://blog.csdn.net/xovee/article/details/106302599)
>
> [xelatex、pdftex、latex 有什么编译上的差别吗？](https://wenda.latexstudio.net/q-1509.html)

## latex字体问题

\textit \textbf等字体命令并不变成斜体和加粗，但并不报错

编译器XeLaTex改为PdfLaTex就好了




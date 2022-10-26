---
title: rust语言圣经学习
abbrlink: 18543
date: 2022-02-15 10:10:03
categories:
tags:
description:
top:
---

---
title: VRF算法学习
abbrlink: 25666
date: 2022-01-07 15:57:26
categories:
tags:
description:
top:

---

<p align="right">RUST教程笔记</p> 

* 

<!-- more -->

避免从入门到放弃

* 避免试一试的心态，需要认真对待
  * 要提前做好会遇到困难的准备，因为如上面所说，学习 Rust 不仅仅是在学习一门编程语言
  * 不要抱着试一试的心态去试一试，否则是浪费时间和消耗学习的激情，作为连续六年全世界最受喜欢的语言，Rust 不仅仅是值得试一试 :)
* 深入学习一本好书或教程
  * [rust语言圣经](https://github.com/sunface/rust-course)
* [千万别从链表或图开始练手](https://course.rs/print.html#千万别从链表或图开始练手)
* [仔细阅读编译错误](https://course.rs/print.html#仔细阅读编译错误)
* [不要强制自己使用其它编程语言的最佳实践来写 Rust](https://course.rs/print.html#不要强制自己使用其它编程语言的最佳实践来写-rust)

[在 Linux 或 MacOS 上安装 `rustup`](https://course.rs/print.html#在-linux-或-macos-上安装-rustup)

打开终端并输入下面命令：

```console
$ curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh
```

这个命令将下载一个脚本并开始安装 `rustup` 工具，此工具将安装 Rust 的最新稳定版本。可能会提示你输入管理员密码。

如果安装成功，将出现下面这行：

```text
Rust is installed now. Great!
```

OK，这样就已经完成 Rust 安装啦。

[在 Windows 上安装 `rustup`](https://course.rs/print.html#在-windows-上安装-rustup)

## [Cargo.toml 和 Cargo.lock](https://course.rs/print.html#cargotoml-和-cargolock)

`Cargo.toml` 和 `Cargo.lock` 是 `cargo` 的核心文件，它的所有活动均基于此二者。

- `Cargo.toml` 是 `cargo` 特有的**项目数据描述文件**。它存储了项目的所有元配置信息，如果 Rust 开发者希望 Rust 项目能够按照期望的方式进行构建、测试和运行，那么，必须按照合理的方式构建 `Cargo.toml`。
- `Cargo.lock` 文件是 `cargo` 工具根据同一项目的 `toml` 文件生成的**项目依赖详细清单**，因此我们一般不用修改它，只需要对着 `Cargo.toml` 文件撸就行了。

> 什么情况下该把 `Cargo.lock` 上传到 git 仓库里？很简单，当你的项目是一个可运行的程序时，就上传 `Cargo.lock`，如果是一个依赖库项目，那么请把它添加到 `.gitignore` 中

```rust
fn greet_world() {
     let southern_germany = "Grüß Gott!";
     let chinese = "世界，你好";
     let english = "World, hello";
     let regions = [southern_germany, chinese, english];
     for region in regions.iter() {
             println!("{}", &region);
     }
 }
 
 fn main() {
     greet_world();
 }

```

其次，关注下 `println` 后面的 `!`，如果你有 Ruby 编程经验，那么你可能会认为这是解构操作符，但是在 Rust 中，这是 `宏` 操作符，你目前可以认为宏是一种特殊类型函数。

对于 `println` 来说，我们没有使用其它语言惯用的 `%s`、`%d` 来做输出占位符，而是使用 `{}`，因为 Rust 在底层帮我们做了大量工作，会自动识别输出数据的类型，例如当前例子，会识别为 `String` 类型。

最后，和其它语言不同，Rust 的集合类型不能直接进行循环，需要变成迭代器（这里是通过 `.iter()` 方法），才能用于迭代循环。在目前来看，你会觉得这一点好像挺麻烦，不急，以后就知道这么做的好处所在。

> 实际上这段代码可以简写，在 2021 edition 及以后，支持直接写 `for region in regions`，原因会在迭代器章节的开头提到，是因为 for 隐式地将 regions 转换成迭代器。

string和&str的区别

==区分`&str`和`String`两个类型是非常有必要的 。`&str`只读、无所有权，适合切片、字面量等不可变的情形；`String`可变、持所有权，适合字符串字段类型存储等情形。==

作者：PTLin
链接：https://zhuanlan.zhihu.com/p/384496181
来源：知乎
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。



## String是什么？

简单来讲，String可以看作由三个变量所组成的结构体，第一个变量为指向一块堆上连续内存的指针，第二个变量为这块内存里已经使用的总大小*len*，第三个变量为这块的总长度*capacity。*

String在new的时候从堆里申请内存，在drop的时候释放内存。由于String实现了Drop trait所以String不能为其实现Copy trait。

String内部的指向的连续内存可以看作为u8的数组，String的使用接口确保了内部存储的确实为合法的UTF-8编码的字节。

## &str是什么？

&str是对String的一种借用形式，被称为字符串切片。

对String进行deref可以得到&str，而deref内部创建&str的函数`from_utf8_unchecked(v: &[u8]) -> &str`其内部的原理仅仅是调用了`transmute`函数对&[u8]的数据进行了重新解释，`transmute`类似CPP中的`reinterpret_cast`，所以下文把&str和&[u8]视为一个结构完全相同的类型。

对于普通的引用其大小为一个usize，内容为被引用变量的地址，但&[T]并不是这样的引用。就如同C语言里字符串在结尾处需要放置一个`'\0'`当做指示字符串结束的哨兵一样，&[T]也需要某种方式携带被指向的连续内存的长度的元数据，所以&[T]有着两个usize的大小，第一个usize是指向内存的指针，第二个usize为被指向内存总共有多长。

str是字符串切片，&str是字符串切片引用

String是字符串，`String`就是三个玩意组成的：指向缓冲区的堆分配指针，容量，长度。类似于动态数组

&String是字符串引用

关系就是对String取地址&得到&String，对String切片得到str，对str取地址得到&str





在这里你会发现为何在前面强调这一点。字符串切片是一个用途广泛的输入型参数，不仅适用于实际的字符串切片引用，还适用于String引用。所以再强调一遍：如果你需要将一个字符串传递给你的函数，那么请使用字符串切片&str。





## [通过例子学 Rust 中文版](https://rustwiki.org/zh-CN/rust-by-example/index.html)

## [Rust 程序设计语言](https://kaisery.github.io/trpl-zh-cn/title-page.html#rust-程序设计语言)

## [Rust 编码规范 V 0.2](https://rust-coding-guidelines.github.io/rust-coding-guidelines-zh/overview.html)

## [Rust语言圣经(Rust教程 Rust Course)](https://course.rs/)

## [通过大量的链表学习Rust](https://weathfold.gitbooks.io/rust-too-many-lists-zhcn/content/)

## [rust Primer](https://hardocs.com/d/rustprimer/index.html)

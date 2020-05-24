---
title: Rust学习笔记1
tags:
  - 编程语言
categories:
  - Rust
toc: true
img: ''
author: djkloop
top: 'false'
cover: 'false'
date: 2020-05-24 12:37:51
updated: 2020-05-24 13:23:43
---

> 万丈高楼，HelloWorld起...

## 前言
Rust 语言是一种高效、可靠的通用高级语言。其高效不仅限于开发效率，它的执行效率也是令人称赞的，是一种少有的兼顾开发效率和执行效率的语言。

这个系列是跟着b站的**up主令狐冲**的视频一路跟下去的...如果有想学习的可以点击下面的链接
[b站地址](https://www.bilibili.com/video/BV1xJ411B79h)

## 安装

[官网地址](https://www.rust-lang.org/zh-CN/learn/get-started)
  
```bash
  # 安装（官方）
  curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh 

  # 安装是否成功
  rustc --version

  # 控制台显示以下内容就算安装成功
  # rustc 1.42.0 (b8cedc004 2020-03-09)


```
 **注意事项**，国内是需要梯子的，这里可以配置国内的清华大学的源（参考下面的文章或者百度谷歌一下）
 [https://lug.ustc.edu.cn/wiki/mirrors/help/rust-crates](https://lug.ustc.edu.cn/wiki/mirrors/help/rust-crates)

## 编程环境和软件

 我个人使用的是 macos + vscode， 其它的我没有试过但是应该都大同小异。

## HelloWorld

```bash
  carogo new HelloWorld
```

```rs
fn main() {
    print!("Hello World!")
}
```
然后在vscode里面右键运行<code>Run Code</code>就能看到结果了
---
title: Rust学习笔记3
tags:
  - 编程语言
categories:
  - Rust
toc: true
img: ''
author: djkloop
top: 'false'
cover: 'false'
date: 2020-05-24 02:54:48
updated: 2020-05-25 01:06:14
---

> 万丈高楼，HelloWorld起…

## 前言
> https://kaisery.github.io/trpl-zh-cn/ch04-00-understanding-ownership.html

所有权（系统）是 Rust 最为与众不同的特性，它让 Rust 无需垃圾回收（garbage collector）即可保障内存安全。因此，理解 Rust 中所有权如何工作是十分重要的。本章，我们将讲到所有权以及相关功能：借用、slice 以及 Rust 如何在内存中布局数据。
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
updated: 2020-06-10 01:14:03
---

> 万丈高楼，HelloWorld起…

## 前言
> https://kaisery.github.io/trpl-zh-cn/ch04-00-understanding-ownership.html

所有权（系统）是 Rust 最为与众不同的特性，它让 Rust 无需垃圾回收（garbage collector）即可保障内存安全。因此，理解 Rust 中所有权如何工作是十分重要的。本章，我们将讲到所有权以及相关功能：借用、slice 以及 Rust 如何在内存中布局数据。

```rs
// 1. rust通过所有权机制来管理内存，编译器在编译就会根据所有权规则对内存的使用进行检测
// 2. 堆和栈
//  2.1 在编译时栈中的所有数据都必须占用已知且固定的大小
//  2.2 在编译时大小未知或大小可能变化的数据，要改为存储在堆上
// 3. 作用域
// 4. String内存回收
// 5. 移动
// 6. clone
// 7. 栈上数据拷贝
// 8. 函数和作用域

fn main() {
  let x: i32 = 1;
  {
    let y: i32 = 1;
    println!("y = {}", y);
    println!("x - x = {}", x);
  }

  {
    let mut s1 = String::from("Hello");
    s1.push_str(" World");
    println!("s1 = {}", s1); // String类型离开作用域时，会调用drop方法

    // 移动
    let s2 = String::from("test");
    // let s3 = s2  会报错，s2离开的时候内存会被释放掉，所以不能这样直接赋值，也就是不能再使用s2
    // 这里可以使用深拷贝来解决s2不能使用的问题
    let s3 = s2.clone();
    println!("s2 = {}", s2);
    println!("s2 = {}", s3);
  }

  // copy 栈上的数据拷贝，就是拷贝的数据。
  let a = 1;
  let b = a;
  println!("a = {}, b = {}", a, b);
  // 常用的copy trait有
  // 所有的整型
  // 浮点型
  // 布尔值
  // 字符类型 char
  // 元组
}
```
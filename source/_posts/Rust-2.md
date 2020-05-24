---
title: Rust学习笔记2
tags:
  - 编程语言
categories:
  - Rust
toc: true
img: ''
author: djkloop
top: 'false'
cover: 'false'
date: 2020-05-24 01:24:42
updated: 2020-05-24 14:54:46
---

> 万丈高楼，HelloWorld起...

## 前言
上一篇讲完了Rust的一些概念和安装还有HelloWorld，这一篇跟着视频里面学习变量等相关的代码。

## 变量

```rs
const MAX_POIONT: u32 = 10000;
fn main() {
    // 1. 变量定义
    // 定义变量用let，如果变量没有使用mut，那么变量是不可变的。
    let a = 1;
    println!("a = {}", a);

    let mut b: u32 = 2;
    println!("b1 = {}", b);
    b = 4;
    println!("b2 = {}", b);

    // 2. 隐藏性
    // 这个变量可以重复定义...真他娘的是个神奇的语言
    // 如果后面继续有使用这个变量的话，会使用这一行的变量，
    // 有点覆盖的意思...
    let b: f32 = 1.1;
    println!("b = {}", b);

    // 3. 常量
    println!("MAX_POINT = {}", MAX_POIONT);
}
```

## 数据类型
```rs
fn main() {
    // bool
    let is_true: bool = true;
    println!("is_true = {}", is_true);
    let is_false: bool = false;
    println!("is_false = {}", is_false);
    // rust自带类型推导
    let is_bool = true;
    println!("is_bool = {}", is_bool);

    // char 在rust里面，char是32位的
    let char_a = "a";
    println!("char_a = {}", char_a);
    let char_b = "你";
    println!("char_b = {}", char_b);

    // i8, i16, 132, i64, u8, u16, u32, u64, f32, f64
    let i8_c: i8 = -111;
    println!("i8_c = {}", i8_c);
    let f32_d = 0.00000008;
    println!("f32_b = {}", f32_d);

    // 自适应类型 isize, usize
    println!("max = {}", usize::max_value());

    // 数组 [Type; size]
    let arr: [u32; 5] = [1, 2, 3, 4, 5];
    println!("arr[0] = {}", arr[0]);
    let arr1: [u32; 3] = [1, 2, 3];
    show(arr1);

    // 元组
    let tup: (i32, f32, char) = (-3, 3.2, '你');
    println!("{}", tup.0);
    // 自带类型推导
    let tup = (-3, 3.2, '你');
    println!("------------------");
    println!("{}", tup.0);
    println!("{}", tup.1);
    println!("{}", tup.2);
    println!("------------------");

    // 有点类似js的解构赋值
    let (x, y, z) = tup;
    println!("------------------");
    println!("{}", x);
    println!("{}", y);
    println!("{}", z);
    println!("------------------");
}

fn show(arr1: [u32; 3]) {
    println!("------------------");
    for i in &arr1 {
        println!("{}", i);
    }
    println!("------------------");
}
```
## 函数

```rs
// 不传参数
fn other_fun() {
    println!("This is a function");
}

// 传参数(参数必须要带类型)
fn other_fun1(a: i32, b: u32) {
    println!("a = {}, b = {}", a, b);
}

// 返回带类型的
fn other_fun2(a: i32, b: i32) -> i32 {
    let result = a + b;
    return result;
}

// 返回带类型的 可以不写return但是不能写冒号
fn other_fun3(a: i32, b: i32) -> i32 {
    // let result = a + b;
    // result 这样也可以哦~
    a + b
}

fn main() {
    //
    other_fun();
    //
    let a = -1;
    let b = 2;
    other_fun1(a, b);
    //
    let c = 9;
    let r = other_fun2(a, c);
    println!("r1 = {}", r);
    //
    let r = other_fun3(a, c);
    println!("r2 = {}", r);
    // let y = 1; // 语句， 没有返回值
    let y = {
        let x = 1;
        x + 1
    };
    println!("y = {}", y);

    println!("Hello, world!");
}

```

## 注释
```rs
fn main() {
  // 双斜杠
}
```

## 控制流
```rs
fn main() {
    // if
    let y = 0;
    if y == 1 {
        println!("y = 1");
    }

    // if - else
    if y == 1 {
        println!("y = 1")
    } else {
        println!("y != 1")
    }

    // if - else - if - else
    if y == 1 {
        println!("y = 1")
    } else if y == 0 {
        println!("y == 0")
    } else if y == 3 {
        println!("y == 3")
    } else {
        println!("other")
    }

    let condition = true;
    // if - else 里面的所有类型都应该一致
    // let x = if condition { 5 } else { "6" }; error
    let x = if condition { 5 } else { 6 };
    println!("x = {}", x);

    // loop
    let mut counter = 0;
    loop {
        println!("in loop");
        if counter == 3 {
            break;
        };
        counter += 1;
    }

    let result = loop {
        counter += 1;
        if counter == 6 {
            break counter * 3;
        }
    };
    println!("result = {}", result);

    // while
    let mut i = 0;
    while i != 10 {
        i += 1;
    }
    println!("i = {}", i);

    // for
    let arr = [1, 2, 3, 4];
    // for i in arr.iter() {
    for i in &arr {
        println!("element = {}", i);
    }
}
```
---
title: test-code
tags:
  - JavaScript
categories:
  - 前端开发
toc: false
img: ''
author: djkloop
top: 'false'
cover: 'false'
date: 2020-05-19 03:58:51
updated: 2020-05-21 11:59:31
---

## 前言

React Native 之前使用时，用过 Socket.io，但是一直连接不上，表示连接超时什么的。

今天再次试了一些，既然连接上了，献上关键代码。

## 前端

React Native上，socket版本必须要限制，固定为 <code>2.1.1</code>, 如果直接安装新版本会不行的。 

> "socket.io-client": "2.1.1"

```js
 const a = '12';
 const b = "13";

 let aaa = "aa";
 aaa = 999;
 if(aaa === 999) {
   console.log("你说的太对了!")
 }
```

<!-- more -->
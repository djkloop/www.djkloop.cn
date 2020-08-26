---
title: Golang goroutine
tags:
  - 编程语言
categories:
  - Golang
toc: true
img: ''
author: djkloop
top: 'false'
cover: 'false'
date: 2020-08-26 10:48:13
updated: 2020-08-26 23:17:14
---

> 万丈高楼, HelloWorld起

```go

package main

import (
	"fmt"
	"time"
)

func main() {
	var a [10]int
	for i := 0; i < 10; i++ {
		go func(n int) {
			for {
				a[n]++
			}
		}(i)
	}
	time.Sleep(time.Millisecond)
	fmt.Println(a)
}
```
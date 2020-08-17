---
title: Golang Struct
tags:
  - 编程语言
categories:
  - Golang
toc: true
img: ''
author: djkloop
top: 'false'
cover: 'false'
date: 2020-08-18 12:04:37
updated: 2020-08-18 00:27:21
---

> 万丈高楼, HelloWorld起

```c
package main

import (
	"fmt"
)

type treeNode struct {
	value       int
	left, right *treeNode
}

func (node treeNode) print() {
	fmt.Println(node.value)
}

func (node *treeNode) setValue(value int) {
	node.value = value
}

func (node *treeNode) traverse() {
	if node == nil {
		return
	}
	node.left.traverse()
	node.print()
	node.right.traverse()
}

func createNode(value int) *treeNode {
	return &treeNode{value: value}
}

func main() {
	var root treeNode
	fmt.Println(root)

	root = treeNode{
		value: 3,
	}

	root.left = &treeNode{
		value: 3,
	}

	root.right = &treeNode{
		5, nil, nil,
	}
	root.right.left = new(treeNode)
	root.left.right = createNode(10)
	root.left.right.setValue(9)

	root.traverse()
}


```
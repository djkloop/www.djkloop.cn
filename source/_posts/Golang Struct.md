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
updated: 2020-08-22 15:26:04
---

> 万丈高楼, HelloWorld起

```c
package main

import (
	"fmt"

	"go_reset/tree"
)

type myTreeNode struct {
	*tree.Node
}

func (myNode *myTreeNode) postOrder() {
	if myNode == nil || myNode.Node == nil {
		return
	}

	left := myTreeNode{myNode.Left}
	left.postOrder()

	right := myTreeNode{myNode.Right}
	right.postOrder()

	myNode.Print()
}

func (myNode *myTreeNode) Traverse() {
	fmt.Println("This method ois shadowed.")
}

func main() {
	root := myTreeNode{&tree.Node{Value: 3}}

	root.Left = &tree.Node{
		Value: 3,
	}

	root.Right = &tree.Node{
		Value: 5,
	}
	root.Right.Left = new(tree.Node)
	root.Left.Right = tree.CreateNode(10)
	root.Left.Right.SetValue(9)

	fmt.Print("In-order traversal: ")
	root.Traverse()

	fmt.Print("My own post-order traversal: ")
	root.postOrder()
}
```
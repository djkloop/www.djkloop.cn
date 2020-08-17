---
title: Golang Map
tags:
  - 编程语言
categories:
  - Golang
toc: true
img: ''
author: djkloop
top: 'false'
cover: 'false'
date: 2020-08-17 11:14:40
updated: 2020-08-17 23:54:55
---

> 万丈高楼, HelloWorld起

```golang
package main

import (
	"fmt"
)

func main() {
	m := map[string]string{
		"name":     "a",
		"language": "golang",
		"site":     "ok",
		"quality":  "good",
	}

	m2 := make(map[string]int)

	var m3 map[string]int

	fmt.Println(m, m2, m3)

	/// 不会保证顺序
	for k, v := range m {
		fmt.Println(k, v)
	}

	fmt.Println("Getting values")

	if cName, ok := m["name"]; ok {
		fmt.Println(cName)
	} else {
		fmt.Println("not error key")
	}

	if notName, ok := m["fu"]; ok {
		fmt.Println(notName)
	} else {
		fmt.Println("key dose not exist")
	}

	fmt.Println("Deleting values")
	delete(m, "name")
	name, ok := m["name"]
	fmt.Println(name, ok)

}
```

```golang
package main

import (
	"fmt"
)

func lengthOfNonRepeatingSubStr(s string) int {
	lastOccurred := make(map[rune]int)
	start := 0
	maxLength := 0

	for i, ch := range []rune(s) {

		if lastI, ok := lastOccurred[ch]; ok && lastOccurred[ch] >= start {
			start = lastI + 1
		}
		if i-start+1 > maxLength {
			maxLength = i - start + 1
		}
		lastOccurred[ch] = i

	}
	return maxLength
}

func main() {
	fmt.Println(lengthOfNonRepeatingSubStr("111222333"))
	fmt.Println(lengthOfNonRepeatingSubStr("abcabcaa"))
	fmt.Println(lengthOfNonRepeatingSubStr("bbbbbbbb"))
	fmt.Println(lengthOfNonRepeatingSubStr("pwwkewa"))
	fmt.Println(lengthOfNonRepeatingSubStr("对啊对啊"))
}

```
```golang
package main

import (
	"fmt"
	"unicode/utf8"
)

func main() {
	s := "你说的对!" // UTF-8
	for _, b := range []byte(s) {
		fmt.Printf("%X ", b)
	}
	fmt.Println()
	for i, ch := range s {
		fmt.Printf("(%d %X)", i, ch)
	}
	fmt.Println()
	fmt.Println("Run Count: ", utf8.RuneCountInString(s))

	bytes := []byte(s)
	for len(bytes) > 0 {
		ch, size := utf8.DecodeRune(bytes)
		bytes = bytes[size:]
		fmt.Printf("%c ", ch)
	}
	fmt.Println()

	for i, ch := range []rune(s) {
		fmt.Printf("(%d %c) ", i, ch)
	}
	fmt.Println()
}

```
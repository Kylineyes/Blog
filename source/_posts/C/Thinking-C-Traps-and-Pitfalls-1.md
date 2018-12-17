---
title: C Traps and Pitfalls 练习摘记(1)
date: 2018-12-15 23:25:29
categories: C
tags: 
    - C
toc: true
thumbnail: /images/C/C-Note-thumbnail.png
banner: /images/C/C-Note-banner.png
---

# 语法“陷阱”

__练习 2-1：__ C语言运行初始化列表中出现多余的逗号，例如

```c
int days[] = { 31, 28, 31, 30, 31, 30,
	31, 31, 30, 31, 30, 31,};
```

为什么这种特性是有用的？

__答案：__ 我们可以看出，初始化列表每一个元素后面都跟着一个逗号，这种语法上的相似性，为自动化的程序设计工具提供了方便。亦即当代码是由工具自己编写产生的时候，就不需要花费心思去特别的判定结尾了。

---

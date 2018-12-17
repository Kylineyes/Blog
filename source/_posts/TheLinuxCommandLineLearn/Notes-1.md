---
title: 快乐的 Linux 命令行 个人笔记(1)
date: 2018-7-30 03:34:11
categories: Linux
tags: 
    - Shell
    - Linux
toc: true
thumbnail: /images/TheLinuxCommandLineLearn/TheLinuxCommandLineLearn-thumbnail.png
banner: /images/TheLinuxCommandLineLearn/TheLinuxCommandLineLearn-banner.png
---

# 背景

此书网站：[The Linux Command Line](http://linuxcommand.org/tlcl.php) ，它是免费的。
此书中文版：[快乐的 Linux 命令行](https://billie66.github.io/TLCL/)
我是跟着中英对照版进行学习，安装了 Ubuntu Server 17.10 的虚拟机作为学习环境，本系列的相当一部分内容都是从原书摘抄修改。

本文对应章节：
[什么是 shell](http://billie66.github.io/TLCL/book/chap02.html)


# 什么是Shell

shell 就是一个程序，它接受从键盘输入的命令， 然后把命令传递给操作系统去执行。几乎所有的 Linux 发行版都提供一个名为 bash 的 来自 GNU 项目的 shell 程序。“bash” 是 “Bourne Again SHell” 的首字母缩写， 所指的是这样一个事实，bash 是最初 Unix 上由 Steve Bourne 写成 shell 程序 sh 的增强版。

# 终端仿真器

有了 shell 不够，我们需要一个名为终端仿真器的程序来于 shell 沟通。一般它被简单的称为 terminal，但 KDE 使用的是konsole，GNOME 使用 gnome-terminal，但是它们的目的都是相同的，让我们能够访问 shell。

# Shell提示符 

当 Shell 准备好去接收输入时，他会显示一行提示，提示可能会因为不同的环境会有不同的模样，但是通常的，提示会包括 你的用户名@主机名，紧接着当前工作目录和一个美元符号。
如果提示符的最后一个字符是“\#”, 而不是“\$”, 那么这个终端会话就有超级用户权限。 这意味着，我们或者是以 root 用户的身份登录，或者是我们选择的终端仿真器提供超级用户（管理员）权限。

# 命令历史

如果按下 `上箭头` 按键，我们会看到刚才输入的命令重新出现在提示符。 这叫命令历史。许多 Linux 发行版默认保存最后输入的500个命令。 按下 `下箭头` 按键，先前输入的命令就消失了。
我们可以利用上下箭头加快我们输入的效率，这里的上下箭头出现的内容其实是之前输入过的命令，而同时，`左右箭头` 按键可以帮助我们定位到命令行的期望位置。

# 简单命令

## date

显示当前日期。

```bash
Tue Jul 31 02:49:03 CST 2018
```

## cal

以日历形式显示当前日期，当前日高亮标出。

```bash
     July 2018
Su Mo Tu We Th Fr Sa
 1  2  3  4  5  6  7
 8  9 10 11 12 13 14
15 16 17 18 19 20 21
22 23 24 25 26 27 28
29 30 31
```

## df

查看磁盘剩余空间的数量。

## free

显示空闲内存的数量。

## exit

结束终端对话。

# 幕后控制台

即使终端仿真器没有运行，在后台仍然有几个终端会话运行着。它们叫做虚拟终端 或者是虚拟控制台。在大多数 Linux 发行版中，这些终端会话都可以通过按下 Ctrl-Alt-F1 到 Ctrl-Alt-F6 访问。当一个会话被访问的时候， 它会显示登录提示框，我们需要输入用户名和密码。要从一个虚拟控制台转换到另一个， 按下 Alt 和 F1-F6(中的一个)。返回图形桌面，按下 Alt-F7。


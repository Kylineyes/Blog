---
title: 快乐的 Linux 命令行 个人笔记(2)
date: 2018-7-31 03:32:10
categories: Linux
tags: 
    - Shell
    - Linux
toc: true
thumbnail: /images/TheLinuxCommandLineLearn/TheLinuxCommandLineLearn-thumbnail.png
banner: /images/TheLinuxCommandLineLearn/TheLinuxCommandLineLearn-banner.png
---

本文对应章节：
[文件系统中跳转](http://billie66.github.io/TLCL/book/chap03.html)

# 理解文件系统树

类似于 Windows，一个“类 Unix” 的操作系统，比如说 Linux，以分层目录结构来组织所有文件。 这就意味着所有文件组成了一棵树型目录（有时候在其它系统中叫做文件夹）， 这个目录树可能包含文件和其它的目录。文件系统中的第一级目录称为根目录。 根目录包含文件和子目录，子目录包含更多的文件和子目录，依此类推。

注意(类 Unix 系统)不像 Windows ，每个存储设备都有一个独自的文件系统。类 Unix 操作系统， 比如 Linux，总是只有一个单一的文件系统树，不管有多少个磁盘或者存储设备连接到计算机上。 根据负责维护系统安全的系统管理员的兴致，存储设备连接到（或着更精确些，是挂载到）目录树的各个节点上。

![图1: 由图形化文件管理器显示的文件系统树](\images\TheLinuxCommandLineLearn\Notes-3-1.png)

大多数人都可能熟悉如图1所示描述文件系统树的图形文件管理器。注 通常这是一棵倒置的树，也就是说，树根在最上面，而各个枝干在下面展开。然而，命令行没有这样的图片，所以我们需要把文件系统树想象成别的样子。

把文件系统想象成一个迷宫形状，就像一棵倒立的大树，我们站在迷宫的中间位置。 在任意时刻，我们处于一个目录里面，我们能看到这个目录包含的所有文件， 以及通往上面目录（父目录）的路径，和下面的各个子目录。我们所在的目录则称为 当前工作目录。我们使用 pwd（print working directory(的缩写)）命令，来显示当前工作目录。

当我们首次登录系统（或者启动终端仿真器会话）后，当前工作目录是我们的家目录。 每个用户都有他自己的家目录，__当用户以普通用户的身份操控系统时，家目录是唯一允许用户写入文件的地方。__

# ls

列出一个目录包含的文件及子目录。
默认的使用方法只列出当前目录下的内容，但是实际上 ls 可以列出任一目录的内容。如果你的终端支持色彩，你会发现 ls 用不同的颜色来区分文件的类型，这对我们寻找指定文件很有帮助。

# cd

更改工作目录。

输入 cd, 然后输入你想要去的工作目录的路径名。路径名就是沿着目录树的分支 到达想要的目录期间所经过的路线。路径名可通过两种方式来指定，一种是绝对路径， 另一种是相对路径。

## 绝对路径

绝对路径开始于根目录，紧跟着目录树的一个个分支，一直到达所期望的目录或文件。

## 相对路径

绝对路径从根目录开始，直到它的目的地，而相对路径开始于工作目录。 为了做到这个（用相对路径表示）， 我们在文件系统树中用一对特殊符号来表示相对位置。 这对特殊符号是 “.” (点) 和 “..” (点点)。

符号 “.” 指的是工作目录（或者可以看作当前目录），”..” 指的是工作目录的父目录。

在几乎所有的情况下，可以省略”./”。它是隐含的，例外的情况，包括但不仅包括运行当前目录下一个可执行文件。

cd 快捷键

| 快捷键 | 运行结果 |
| --- | --- |
| cd | 更改工作目录到你的家目录。 |
| cd - | 更改工作目录到先前的工作目录。 |
| cd ~user_name | 更改工作目录到用户家目录。例如, cd ~bob 会更改工作目录到用户“bob”的家目录。 |

# 关于文件名的重要规则

1. 以 “.” 字符开头的文件名是隐藏文件。这仅表示，ls 命令不能列出它们， 用 ls -a 命令就可以了。当你创建帐号后，几个配置帐号的隐藏文件被放置在 你的家目录下。稍后，我们会仔细研究一些隐藏文件，来定制你的系统环境。 另外，一些应用程序也会把它们的配置文件以隐藏文件的形式放在你的家目录下面。
2. 文件名和命令名是大小写敏感的。文件名 “File1” 和 “file1” 是指两个不同的文件名。
3. Linux 没有“文件扩展名”的概念，不像其它一些系统。可以用你喜欢的任何名字 来给文件起名。文件内容或用途由其它方法来决定。虽然类 Unix 的操作系统， 不用文件扩展名来决定文件的内容或用途，但是有些应用程序会。
4. 虽然 Linux 支持长文件名，文件名可能包含空格，标点符号，但标点符号仅限 使用 “.”，“－”，下划线。最重要的是，不要在文件名中使用空格。如果你想表示词与词之间的空格，用下划线字符来代替。过些时候，你会感激自己这样做。

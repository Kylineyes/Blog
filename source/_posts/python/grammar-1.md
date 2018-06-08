---
title: Python3 学习之路(1) 初识
date: 2018年6月7日 22:36:33
categories: Python
tags: 
    - Python
toc: true
thumbnail: /images/python/Python-thumbnail.png
banner: /images/python/Python-banner.png
---

# Python 简介

Python 是一种解释型[^1]、交互性、面向对象[^2]语言。

Python 由 Guido van Rossum 在 1989 年圣诞节期间编写。

## Python 设计之禅(The Zen of Python)

*   Beautiful is better than ugly.
    美丽胜于丑陋
*   Explicit is better than implicit.
    显式胜过隐式
*   Simple is better than complex.
    简单优于复杂
*   Complex is better than complicated.
    复杂好于超复杂
*   Flat is better than nested.
    单一胜过于嵌套
*   Sparse is better than dense.
    间隔胜于紧凑
*   Readability counts.
    可读性很重要
*   Special cases aren’t special enough to break the rules.
    特殊的情况并不足以特殊到打破规则
*   Although practicality beats purity.
    尽管实用性打击代码的纯洁
*   Errors should never pass silently.
    错误绝不应该被默默地放过
*   Unless explicitly silenced.
    除非你有意为之
*   In the face of ambiguity, refuse the temptation to guess. 
    面对含糊不清的地方，忍住去猜想的冲动 
*   There should be one – and preferably only one – obvious way to do it. 
    这里应该有一种（最好只有一种）明确的方法来了解它 
*   Although that way may not be obvious at first unless you’re Dutch 
    除非你是Dutch, 在一开始它可能并不是那么明显 
*   Now is better than never. 
    现在开始做总比最远不做的好 
*   Although never is often better than right now. 
    不加思考就做还不如不做 
*   If the implementation is hard to explain, it is a bad idea. 
    如果某个实现很难解释清楚，那一定是个糟糕的想法 
*   If the implementation is easy to explain, it may be a good idea. 
    如果某个实现很好解释，这也许是个好的想法。 
*   Namespaces are one honking great idea – let’s do more of those! 
    命名空间是个绝妙的想法，我们应该多用，多多益善！

## Python 应用范围

* 网络应用，包括网站、后台服务
* 许多日常需要的小工具，包括系统管理员需要的脚本任务
* 深度学习
* 人工智能

# Windows10 下安装配置

到 [Python 官方网站](https://www.python.org/) 下载对应版本，现在我的版本是 __Python V3.6.5 for windows__。

安装过程没有什么好说的，但是可以选择自动配置PATH，不然需要在后面手动进行配置。


| 变量名 | 描述 |
|:---:|:---:|
| PATH | 系统维护的可用的命令行解释器和其他程序的信息，应添加"(Python安装目录)\\Scripts\\" 和 "(Python安装目录)\\" |
| PYTHONPATH | PYTHONPATH是Python搜索路径，默认我们import的模块都会从PYTHONPATH里面寻找。 |
| PYTHONSTARTUP | Python启动后，先寻找PYTHONSTARTUP环境变量，然后执行此变量指定的文件中的代码。 |
| PYTHONCASEOK | 加入PYTHONCASEOK的环境变量, 就会使python导入模块的时候不区分大小写. |
| PYTHONHOME | 另一种模块搜索路径。它通常内嵌于的PYTHONSTARTUP或PYTHONPATH目录中，使得两个模块库更容易切换。 |

__安装完__，启动命令提示符，在任意目录下输入 `python` ，进入Python的交互式解释器，显示Python的版本，此时说明安装成功。

接下来，python的语法，我将用 [IntelliJ IDEA](https://www.jetbrains.com/idea/)，加 Python 的拓展插件来实践。

# Python解释器

当我们编写Python代码时，我们得到的是一个包含Python代码的以.py为扩展名的文本文件。要运行代码，就需要Python解释器去执行.py文件。

由于整个Python语言从规范到解释器都是开源的，所以理论上，只要水平够高，任何人都可以编写Python解释器来执行Python代码（当然难度很大）。事实上，确实存在多种Python解释器。

- CPython
当我们从Python官方网站下载并安装好Python 3.x后，我们就直接获得了一个官方版本的解释器：CPython。这个解释器是用C语言开发的，所以叫CPython。在命令行下运行python就是启动CPython解释器。
CPython是使用最广的Python解释器。教程的所有代码也都在CPython下执行。
- IPython
IPython是基于CPython之上的一个交互式解释器，也就是说，IPython只是在交互方式上有所增强，但是执行Python代码的功能和CPython是完全一样的。好比很多国产浏览器虽然外观不同，但内核其实都是调用了IE。
CPython用>>>作为提示符，而IPython用In [序号]:作为提示符。
- PyPy
PyPy是另一个Python解释器，它的目标是执行速度。PyPy采用JIT技术，对Python代码进行动态编译（注意不是解释），所以可以显著提高Python代码的执行速度。
绝大部分Python代码都可以在PyPy下运行，但是PyPy和CPython有一些是不同的，这就导致相同的Python代码在两种解释器下执行可能会有不同的结果。如果你的代码要放到PyPy下执行，就需要了解PyPy和CPython的不同点。
- Jython
Jython是运行在Java平台上的Python解释器，可以直接把Python代码编译成Java字节码执行。
- IronPython
IronPython和Jython类似，只不过IronPython是运行在微软.Net平台上的Python解释器，可以直接把Python代码编译成.Net的字节码。

>小结
Python的解释器很多，但使用最广泛的还是CPython。如果要和Java或.Net平台交互，最好的办法不是用Jython或IronPython，而是通过网络调用来交互，确保各程序之间的独立性。
本教程的所有代码只确保在CPython 3.x版本下运行。请务必在本地安装CPython（也就是从Python官方网站下载的安装程序）。

---

# 引用

1. http://www.runoob.com/python/python-intro.html
2. http://www.runoob.com/python/python-install.html
3. https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/00143161198846783e33de56d4041058c3dfc7e44ee1203000
4. https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/001431608990315a01b575e2ab041168ff0df194698afac000


[^1]:运行效率较低，不适合运算密集型的部分。
[^2]:当然可以只编写面向过程的部分。
---
title: Python3 学习之路(2) 基础语法
date: 2018-6-8 01:27:17
categories: Python
tags: 
    - Python
toc: true
thumbnail: /images/python/Python-thumbnail.png
banner: /images/python/Python-banner.png
---

# 你好，世界

在工程下新建 __main.py__ 文件，向文件写入

```python
print("你好，世界")
```
如果你的文件是UTF-8编码存储的，那么这个文件可以立即运行，如果不是，会报一个 SyntaxError 错误，我建议的解决方法是将存储的文件编码改成UTF-8 without BOM。

同时，我还建议在文件头加入一行`#coding=utf-8`，这样Python会以UTF-8编码解析此文件。而之前没有加入本行也能运行的原因是因为：Python3.X 源码文件默认使用UTF-8编码，所以可以正常解析中文，无需指定UTF-8编码。

# 命令提示符/终端下调用脚本

在命令提示符/终端下，进入之前工程写好的 __main.py__ 文件的目录，输入 `python main.py`，便可执行，我们称这种方式为脚本编程。

# 标识符

在 Python 里，标识符由字母、数字、下划线组成。

在 Python 中，所有标识符可以包括英文、数字以及下划线(\_)，但不能以数字开头。

Python 中的标识符是区分大小写的。

以下划线开头的标识符是有特殊意义的。以单下划线开头 \_foo 的代表不能直接访问的类属性，需通过类提供的接口进行访问，不能用 from xxx import * 而导入；

- 以双下划线开头的 \_\_foo 代表类的私有成员
- 以双下划线开头和结尾的 \_\_foo\_\_ 代表 Python 里特殊方法专用的标识，如 \_\_init\_\_() 代表类的构造函数。

# 保留字符

下面的列表显示了在Python中的保留字。这些保留字不能用作常数或变数，或任何其他标识符名称。

所有 Python 的关键字只包含小写字母。

||||
|:-:|:-:|:-:|
| and | exec | not |
| assert | finally | or |
| break | for | pass |
| class | from | print |
| continue | global | raise |
| def | if | return |
| del | import | try |
| elif | in | while |
| else | is | with |
| except | lambda | yield |

# 行和缩进

Python的代码不使用大括号 {} 来控制逻辑、作用范围，而是适用行首的空白缩进来控制。
行首的空白缩进可以适用 Tab 或者空格来控制，每一个逻辑、作用范围的递进，需要保证相同的缩进量，譬如，一直缩进为4个空格的程序，进入一个判定，但是接下来的缩进量变成了5个空格，则会中断程序的运行。
缩进量在一开始就需要定下，然后之后要严格执行，一般建议4个空格作为单位缩进量，并且不要混用 Tab。

## 多行的语句

Python不使用像 C/C++ 一样强制要求分号作为一个语句的结束，在python中一般以新行作为语句的结束符。

但是我们可以使用斜杠（ \\）将一行的语句分为多行显示，

```python
total = a + \
        b + \
        c
```
语句中包含 [], {} 或 () 括号就不需要使用多行连接符。

```python
days =  ['Monday',  'Tuesday',  'Wednesday',  
			'Thursday',  'Friday']
```
Python 也可以同一行显示多条语句，方法是用分号 ; 分开，但极不建议这样做。

```python
print 'hello';print 'World';
```
# 引号

Python 可以使用引号( ' )、双引号( " )、三引号( ''' 或 """ ) 来表示字符串，引号的开始与结束必须的相同类型的。

其中三引号可以由多行组成，编写多行文本的快捷语法，常用于文档字符串，在文件的特定地点，被当做注释。

```python
word =  'word' 
sentence =  "这是一个句子。" 
paragraph =  """这是一个段落。
包含了多个语句"""
```
# 注释

python中单行注释采用 # 开头。
注释可以在语句或表达式行末：

```python
answer =  "42"  # 这是一个注释
```
python 中多行注释使用三个单引号(''')或三个双引号(""")。

# 转义字符

\\可以转义很多字符，比如\\n表示换行，\\t表示制表符，字符\\本身也要转义，所以\\\\表示的字符就是\\

如果字符串里面有很多字符都需要转义，就需要加很多\\，为了简化，Python还允许用r''表示''内部的字符串默认不转义。

---

# 引用

1. http://www.runoob.com/python/python-basic-syntax.html
2. https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/001431658624177ea4f8fcb06bc4d0e8aab2fd7aa65dd95000


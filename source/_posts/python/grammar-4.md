---
title: Python3 学习之路(4) 字符串
date: 2018-6-10 16:19:34
categories: Python
tags: 
    - Python
toc: true
thumbnail: /images/python/Python-thumbnail.png
banner: /images/python/Python-banner.png
---

# 字符串

在Python3中，字符串在内存中的存储格式均是Unicode。且其实不存在单个字符，单个字符也被视为字符串。

## 编码与解码

对于许多编程语言来说，字符串的各类编码是一个很让人难以处理的问题，在Python中，用了很好的封装方式，字符串的编码与解码不再是令人头疼的问题。

### encode() 

python使用encode()方法来进行字符串的编码。这个方法将一个字符串编码成指定编码格式，返回值是bytes类型。

```python
bytes_string = '中文'.encode('utf-8')
```
如果你对含有超出ASCII编码外的字符（比如说，中文）的字符串编码为ASCII，则Python会报错，解决方法是告知Python如何进行处理。

```python
bytes_string = '中文CN'.encode('ascii',errors='ignore')
```
这里我将encode()中errors参数的值设置为'ignore'，即对错误的字节进行忽略，返回值为ASCII编码的bytes，意为CN。

### decode()

python使用decode()方法来进行字符串的编码。这个方法将一个bytes根据指定编码格式进行解码，返回值是一个字符串。

```python
string = b'\xe4\xb8\xad\xe6\x96\x87'.decode('utf-8')
```
如果进行上面的encode()实验，很容易知道这里的__b'\xe4\xb8\xad\xe6\x96\x87'__是UTF-8编码格式下的'中文'，这里相当于上面的逆过程。

同样的，如果bytes里有含有超出指定编码外的字符，Python也会报错，解决方法也是同样告知如何进行处理。

## 转义字符表

| 转义字符 | 描述 |
| --- | --- |
| \(在行尾时) | 续行符 |
| \\ | 反斜杠符号 |
| \\\' | 单引号 |
| \\\" | 双引号 |
| \\a | 响铃 |
| \\b | 退格(Backspace) |
| \\e | 转义 |
| \\000 | 空 |
| \\n | 换行 |
| \\v | 纵向制表符 |
| \\t | 横向制表符 |
| \\r | 回车 |
| \\f | 换页 |
| \\oyy | 八进制数，yy代表的字符，例如：\o12代表换行 |
| \\xyy | 十六进制数，yy代表的字符，例如：\x0a代表换行 |
| \\other | 其它的字符以普通格式输出 |

## 字符串运算符

下表实例变量a值为字符串 "Hello"，b变量值为 "Python"：

| 操作符 | 描述 | 实例 |
|:--:|:--:|:--:|
| + | 字符串连接 | a + b 输出结果： HelloPython |
| * | 重复输出字符串 | a*2 输出结果：HelloHello |
| [] | 通过索引获取字符串中字符 | a[1] 输出结果 **e** |
| [ : ] | 截取字符串中的一部分 | a[1:4] 输出结果 **ell** |
| in | 成员运算符 - 如果字符串中包含给定的字符返回 True | **'H' in a** 输出结果 True |
| not in | 成员运算符 - 如果字符串中不包含给定的字符返回 True | **'M' not in a** 输出结果 True |


## 格式化字符串

Python支持格式化字符串的输出，语法与C语言的printf()函数基本相同。

python字符串格式化符号:

| 符号 | 描述 |
|:--:|:--:|
| %c | 格式化字符及其ASCII码 |
| %s | 格式化字符串 |
| %d | 格式化整数 |
| %u | 格式化无符号整型 |
| %o | 格式化无符号八进制数 |
| %x | 格式化无符号十六进制数 |
| %X | 格式化无符号十六进制数（大写） |
| %f | 格式化浮点数字，可指定小数点后的精度 |
| %e | 用科学计数法格式化浮点数 |
| %E | 作用同%e，用科学计数法格式化浮点数 |
| %g | %f和%e的简写 |
| %G | %f 和 %E 的简写 |
| %p | 用十六进制数格式化变量的地址 |

格式化操作符辅助指令:

| 符号 | 功能 |
|:--:|:--:|
| * | 定义宽度或者小数点精度 |
| - | 用做左对齐 |
| + | 在正数前面显示加号( + ) |
| # | 在八进制数前面显示零('0')，在十六进制前面显示'0x'或者'0X'(取决于用的是'x'还是'X') |
| 0 | 显示的数字前面填充'0'而不是默认的空格 |
| % | '%%'输出一个单一的'%' |
| m.n | m 是显示的最小总宽度,n 是小数点后的位数(如果可用的话) |

样例如下：

```python
print('%c' % 'a') #输出一个字符，如果不是字符会报错 
print('%x' % 16) #16进制下的16，没有前缀表明进制 
print('%04d' % 20) #输出占位4格的数字，未满4位前补0 
print('%+-4d' % 20) #左对齐的，在正数前面补'+'号的占位4格的数字 
print('%10.6f' % 12.98765) #占位10格(包括'.')，小数点后至少6位的数字
```
### format

Python2.6开始支持使用format()函数来格式化字符串。

```python
print('{0:4d}-{1:02d}-{2:d}'.format(1926,8,17)) #输出 1926-08-17
```


## 字符串内建函数

### capitalize()

将字符串的第一个字符转换为大写

```python
str1 = 'hello world' 
print(str1.capitalize()) # 返回 Hello world
str2 = '123hello world' 
print(str2.capitalize()) # 返回 123hello world
```

### center(width, fillchar)

返回一个指定的宽度width居中的字符串，fillchar为填充的字符，默认为空格。

### count(str, beg= 0,end=len(string))

返回 str 在字符串里面出现的次数，如果beg或者end指定则返回指定范围内str出现的次数。

```python
str = 'where which why who when' 
print(str.count('wh')) #返回5
```
### startswith/endswith(suffix, beg=0, end=len(string))

检查字符串是否以suffix开始/结束，如果beg或者end指定则检查指定的范围内是否以suffix开始/结束，如果是，返回True，否则返回False。

### expandtabs(tabsize=8)

把字符串 string 中的 tab 符号转为空格，tab 符号默认的空格数是 8 。

### find(str, beg=0 end=len(string))

检测str是否包含在字符串中，如果指定范围beg和end，则检查是否包含在指定范围内，如果包含返回开始的索引值，否则返回-1。

### index(str, beg=0, end=len(string))

跟find()方法一样，只不过如果str不在字符串中会报一个异常。

### isalnum()

如果字符串至少有一个字符并且所有字符都是字母或数字则返回True，否则返回False。

### isalpha()

如果字符串至少有一个字符并且所有字符都是字母则返回True，否则返回False。

### isdigit() isdecimal() isnumeric()

如果字符串只包含数字则返回True，否则返回False。

这三个在细节上有很多不同的地方，具体请参照引用3的博文，这里只给出结论。

- isdigit()
True: Unicode数字，byte数字（单字节），全角数字（双字节），罗马数字（英文）
False: 汉字数字、罗马数字
Error: 无
- isdecimal()
True: Unicode数字，全角数字（双字节）
False: 罗马数字（英文），汉字数字，罗马数字
Error: byte数字（单字节）
- isnumeric()
True: Unicode数字，全角数字（双字节），罗马数字（英文），汉字数字、罗马数字
False: 无
Error: byte数字（单字节）

### isspace()

如果字符串中只包含空白，则返回True，否则返回False。

### join(seq)

以指定字符串作为分隔符，传入的参数，迭代器seq中的所有变量的字符串表示合并为一个字符串返回。

```python
seq = '-' 
print(seq.join( ('A','B','C') )) #返回A-B-C
```
### len(string)

返回字符串长度。

### ljust(width[, fillchar])

返回一个原字符串左对齐，并使用fillchar填充至长度width的新字符串，fillchar默认为空格。

### lower()

转换字符串中所有大写字符为小写。

### replace(old, new [, max])

把将目标字符串中的old子串替换成new子串,如果max指定，则替换不超过max次。

### split(str=" ", num=string.count(str))

num=string.count(str)) 以str为分隔符截取字符串，如果num有指定值，则仅截取num个子字符串。
这个的默认.split()意即按空格截取字符串。

### splitlines(keepends=False)

返回字符串的行数，按照换行符切割目标字符串。
如果没设定keepends=True，则会将换行符从返回的字符串组中移除。

---

# 引用

1. http://www.runoob.com/python3/python3-string.html
2. https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/001431664106267f12e9bef7ee14cf6a8776a479bdec9b9000
3. https://www.cnblogs.com/jebeljebel/p/4006433.html


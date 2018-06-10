---
title: Python3 学习之路(3) 变量
date: 2018-6-8 02:17:36
categories: Python
tags: 
    - Python
toc: true
thumbnail: /images/python/Python-thumbnail.png
banner: /images/python/Python-banner.png
---

# 变量简述

Python 中的变量赋值不需要类型声明。
每个变量在内存中创建，都包括变量的标识，名称和数据这些信息。
每个变量在使用前都必须赋值，变量赋值以后该变量才会被创建。
等号（=）用来给变量赋值。
等号（=）运算符左边是一个变量名,等号（=）运算符右边是存储在变量中的值。

```python
answer = 42 #之前看到过的简单的变量赋值
```
# 标准数据类型

## 数字(Number)

### 长整型(int)

在Python3中，只有一种int代表长整型，可以参照上述进行赋值和计算。在超过类似 C/C++ 中的 int 变量时，自动的转换成一个精度无限的long类型。同时，python提供16进制0x写法，和8进制的0o写法。

### 浮点数(float)

浮点数也就是小数，之所以称为浮点数，是因为按照科学记数法表示时，一个浮点数的小数点位置是可变的，比如，1.23x109和12.3x108是完全相等的。浮点数可以使用平时的小数写法，也支持科学计数写法。

### 布尔值(bool)

布尔值和布尔代数的表示完全一致，一个布尔值只有True、False两种值，要么是True，要么是False，注意其大小写。
布尔值可以参与数字的运算，此时True代表1，False代表0。

布尔值可以用and、or和not运算，分别对于与，或，非。

### 复数(complex)

复数的赋值可以使用两种方法。

```python
s = 3 + 1j
d = complex(3,2)
```
### 数值计算

python 支持 加法、减法、乘法、除法、地板除法、取余、乘方的数值计算。在混合计算时，Python会隐式的把整型转换成为浮点数。

```python
5/2 #除法 返回一个浮点数 2.5
5//2 #地板除法 返回一个整数 2，向0取整
5%2 #取余 返回一个整数/浮点数，取决于两个操作数是否有浮点数
2**5 #乘方
```
## 字符串(String)

字符串是以单引号\'或双引号\"括起来的任意文本，比如\'abc\'，\"xyz\"等等。请注意，\'\'或\"\"本身只是一种表示方式，不是字符串的一部分，因此，字符串\'abc\'只有a，b，c这3个字符。
字符串可以用截取的语法，格式为：变量[头下标:尾下标]

```python
print(str[0:-1])  # 输出第一个到倒数第二个的所有字符  
print(str[0])  # 输出字符串第一个字符  
print(str[2:5])  # 输出从第三个开始到第五个的字符  
print(str[2:])  # 输出从第三个开始的后的所有字符  
print(str * 2)  # 输出字符串两次  
print(str + "TEST")  # 连接字符串
```
注意，python里面的字符串(甚至包括其他引用类型)，是以值比较相等的，而不是像java等语言比较内存地址。故两个内存地址不同，但内容相同的字符串做相等判定，答案是True。

## 列表(List)

列表可以完成大多数集合类的数据结构实现。列表中元素的类型可以不相同，它支持数字，字符串甚至可以包含列表（所谓嵌套）。
列表是写在方括号之间、用逗号分隔开的元素列表，列表中的元素是可以改变的。
和字符串一样，列表同样可以被索引和截取，列表被截取后返回一个包含所需元素的新列表。

## 元组(Tuple)

元组与列表类似，不同之处在于元组的元素不能修改。元组写在小括号里，元素之间用逗号隔开。
tuple的元素不可改变，但它可以包含可变的对象，比如list列表。
构造包含 0 个或 1 个元素的元组比较特殊，所以有一些额外的语法规则：

```python
tup1 = ()  # 空元组
tup2 = (20,)  # 一个元素，需要在元素后添加逗号
```
string、list和tuple都属于sequence（序列）。

## 集合(Set)

集合是一个无序不重复元素的序列，其基本功能是进行成员关系测试和删除重复元素。
可以使用大括号 { } 或者 set() 函数创建集合。
但是创建一个空集合必须用 set() 而不是 { }，因为 { } 是用来创建一个空字典。

```python
a = set('abracadabra') 
b = set('alacazam') 
print(a) 
print(a - b)  # a和b的差集  
print(a | b)  # a和b的并集  
print(a & b)  # a和b的交集  
print(a ^ b)  # a和b中不同时存在的元素
```
## 字典(Dictionary)

字典当中的元素是通过键来存取的，而不是通过偏移存取，这是字典与序列不同的地方。

字典是一种映射类型，字典用"{ }"标识，它是一个无序的键(key) : 值(value)对集合。
键(key)必须使用不可变类型，在同一个字典中，键(key)必须是唯一的。
字典可以通过中括号中加key的方法来获得value，也可以调用.keys() 或 .value() 方法来获得其中的所有键与值。

## 空值(None)

空值是一个特殊的值，用None表示，空值不能代表0，0也不能代表空值。

# 相关函数

## del var

删除一些对象的引用，你可以使用del删除一个或多个的对象引用，如果要多个，用逗号隔开。

```python
del var1,var2,var3
```

## int(x[,base])

```python
age = int(10.9) # 将x转换为int型变量，向0取整
status = int('10',2) # 构造2进制下的10，即十进制下的2，注意'10'是字符串
```
## float(x)

```python
weight = float(50) # 将x转换float型变量
```

## complex(real[,imag])

```python
a = complex(1) # 构造复数 1 + 0j
b = complex(-1,5) # 构造复数 -1 ＋５ｊ
```
## str(x)

将x转换为字符串。

## repr(x)

将对象转化为供解释器读取的形式，返回一个字符串。

## eval(expression[, globals[, locals]])

执行一个字符串表达式，并返回表达式的值。

| 参数 | 含义 |
|---|---|
| expression | 表达式 |
| globals | 变量作用域，全局命名空间，如果被提供，则必须是一个字典对象。 |
| locals | 变量作用域，局部命名空间，如果被提供，可以是任何映射对象。 |

```python
eval('2 + 2') # 返回一个值为4的int类型
n = 4
eval('n ** 2') # 返回一个值为16的int类型
eval('"hello," + str(0)') # 返回一个值为'hello,0'的string类型
```
## tuple(s)

将s转换为元组。

## list(s)

将s转换为列表。

## dict(d)

将d转换为字典。

```python
sex = dict(boy='1',girl='0') #传入关键字
week = dict([('Mon', 0), ('Tues', 1), ('Wed', 2), 
             ('Thur', 3), ('Fri', 4), ('Sat', 5), ('Sun', 6)]) 
				#可迭代对象方式来构造字典
```
## frozenset([iterable])

将iterable转换为冻结的集合，冻结后集合不能再添加或删除任何元素。
iterable为可迭代的对象，比如列表、字典、元组等等。
注意，冻结的集合中任意一个元素不能是列表，但是可以直接冻结列表(这里应该看作均为不可变的元素)。

```python
tup = (3, 5.0, "test", (2, 2), ([2,3],[3,3])) 
	#元素分别为int、float、string、tuple、带有list的tuple
list = [321,"test",((2,2),(3,3))] 
	#元素分别为int、string、带有tuple的tuple
frozenset(tup) 
	# 非法操作，冻结的集合中含有带list的元素
frozenset(list) 
	# 合法操作，冻结的中不含有带list的元素
```
## chr(x) ord(c)

chr(x) 将整数x以ASCII码表转换成字符。
ord(c) 将字符c以ASCII码表转换成整数。

## hex(x) oct(x)

hex(x) 将整数x转换成16进制，以字符串的格式返回。
oct(x) 将整数x转换成8进制，以字符串的格式返回。

## id(x)

返回变量x的内存地址。

## type(var)

查询变量所指的对象类型。

## isinstance(var, type)

判定查询变量所指的对象类型是不是type，若是则返回True，否则返回False。

```python
n = 3
if isinstance(n, int) :
   print("n's type is int)
```
type()与isinstance()的区别在面向对象时可以区分出来。
若有A类，且B类继承了A类。
则，type()认为A与B是两种不同的数据类型。
而，isinstance()认为B类的对象也是一种A类的对象，他们同属于一种数据类型。

---

# 引用

1. http://www.runoob.com/python3/python3-data-type.html
2. https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/001431658624177ea4f8fcb06bc4d0e8aab2fd7aa65dd95000
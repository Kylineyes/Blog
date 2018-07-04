---
title: Python3 学习之路(5) 列表、元组与字典
date: 2018-6-11 00:02:38
categories: Python
tags: 
    - Python
toc: true
thumbnail: /images/python/Python-thumbnail.png
banner: /images/python/Python-banner.png
---

# 列表

可以理解为列表为可变的数组，不过Python中的列表较之灵活许多。

## 访问改动

使用下标索引来访问并改动列表中的值，同样你也可以使用方括号的形式截取字符，访问并改动，超出范围则会报错。

### index(obj)

返回目标列表中obj出现的位置，如果没有则抛出异常。

## 增减

### append(obj)

向目标列表的最后添加一个元素。

### extend(seq)

向目标列表的最后添加如干个元素，seq要是一个可迭代的参数。

### insert(index,obj)

向目标列表指定位置插入一个元素。

### del
可以使用 del 语句来删除列表的的元素，可以删除整个列表，也可以通过下标索引来删除列表中的某个或某些元素。

```python
list = ['A','B','C','D','E','F']

del list[0] # 删除一个元素 
print(list) # 输出['B', 'C', 'D', 'E', 'F'] 
del list[1:3] # 删除一些元素 
print(list) # 输出['B', 'E', 'F'] 
del list # 删除整个列表
```
### remove(obj)

移除目标列表的指定元素，找不到则抛出异常。

### pop([index=-1])

移除列表中的一个元素（默认最后一个元素），并且返回该元素的值，没有值可以返回则抛出异常。

## 操作符

列表的操作与字符串运算符的种类和效果基本相同，此处不表，请参照之前的文章。

## 其他函数

### len(list)

返回列表元素个数。

### clear()

清除目标列表的所有元素。

### max(list) min(list)

返回列表元素的最大/小值，如果列表中的元素不是一种类型或者没有重载小于号，会报错。
当列表中元素均是一种类型，可以通过此类型的默认排序获得结果。

```python
list = [[1,2],[4,4],[4,2,2]]
print(max(list)) # 输出[4,4] 即先比较第一个数，再比较第二个数
```
### sort(cmp=None, key=None, reverse=False)

对原列表进行排序，不返回值。

- cmp 可选参数, 如果指定了该参数会使用该参数的方法进行排序。
- key 主要是用来进行比较的元素，只有一个参数，具体的函数的参数就是取自于可迭代对象中，指定可迭代对象中的一个元素来进行排序。
- reverse 排序规则，reverse = True 降序， reverse = False 升序（默认）。

sort还可以搭配类中重载小于号的方式来使用，此处按下不表。

# 元组

可以理解为元组为不可变的数组，目的是为了代码的安全性。

## 访问

使用下标索引来访问元组中的值。

## 改动

元组中的元素值是不允许修改的，但我们可以对元组进行连接组合。

## 删除

元组中的元素值是不允许删除的，但我们可以使用del语句来删除整个元组。

## 操作符

元组的操作与字符串运算符的种类和效果基本相同，此处不表，请参照之前的文章。

## 其他函数

元组同列表一样拥有len()、min()、max()等函数。

# 字典

字典同其他主流编程语言的map一样，是一种key-\>value的容器，查询速度很快。
要注意的是，key要是唯一的且不可变，但value不一定。如果重复对一个key进行改动，则会把旧的抛弃，更新为新的。

## 访问

使用下标索引(key)来访问字典中的值。没有会报错。

## 改动

使用下标索引(key)来更新元组中的值。

## 删除

有三种方法可以不同程度上的删除字典。

### del dict[]

删除字典里的一对key-\>value的元素。

### clear()

删除字典里面的所有元素。

### del dict

删除整个字典。dsadsadsadsa

## 其他函数

### len(dict)

计算字典元素个数，即键的总数。

### str(dict)

输出字典，以可打印的字符串表示。

### fromkeys()

创建一个新字典，以序列seq中元素做字典的键，val为字典所有键对应的初始值。

### get(key, default=None)

返回指定键的值，如果值不在字典中返回default值。

### items()

以列表返回可遍历的(键, 值) 元组数组。

### setdefault(key, default=None)

和get()类似, 但如果键不存在于字典中，将会添加键并将值设为default。

### pop(key[,default])
删除字典给定键 key 所对应的值，返回值为被删除的值。key值必须给出。 否则，返回default值。

### keys()/values()

以列表返回一个字典所有的键/值。

---

# 引用

1. http://www.runoob.com/python3/python3-list.html
2. http://www.runoob.com/python3/python3-tuple.html
3. http://www.runoob.com/python3/python3-dictionary.html
4. https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/0014316724772904521142196b74a3f8abf93d8e97c6ee6000
5. https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/00143167793538255adf33371774853a0ef943280573f4d000
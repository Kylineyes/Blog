---
title: Effective C++ 摘记(1)
date: 2018-10-7 03:12:56
categories: C++
tags: 
    - C++
toc: true
thumbnail: /images/Cplusplus/Cplusplus-thumbnail.png
banner: /images/Cplusplus/Cplusplus-banner.png
---

# 条款02 尽量以const, enum, inline 替换#define

当我们进行 #define 的时候，代码在预处理器的时候就已经被替换了，于是记号名称有可能没有进入记号表(Symbol table)内，于是你应用此常量但获得一个编译错误信息的时候，错误信息可能只会提及到被替换后的值。这时的错误跟踪会十分浪费时间，故此时，我们应该用一个常量来替换宏。

>定义常量指针时，因此有必要将指针声明为const，但是同时你应该也要保证指针指向之物不变，此时应该用两个const限定。如
`const char* const authorName = "Scott Meyers"`
但是同时，string对象比 char*-based指针更加合适，故应该使用
`const std::string authorName("Scott Meyers")`

其次，在class类内声明一个静态成员常量，例如：

```cpp
class Tuple {
private:
    static const int GroupSize = 5;
    int value[GroupSize];
}
```

然而你所看到的是GroupSize的声明式而非定义式。通常C++要求你要用的所有东西提供一个定义式，但如果它是个class专属常量又是static且为整数类型(int/char/bool)，则需要特殊处理。
只要你不取他的地址，你可以声明并使用它们而无须提供定义式。但是若你**一定要取某个class成员常量的地址或者编译器坚持要看到一个定义式（通常发生在较老的编译器上）**，就需要提供一个这样的式子：

```cpp
const int Tuple::GroupSize;
```

这个式子应该放在实现文件而非头文件，由于class常量在声明时已经获得了初值，因此定义时不可以再设初值。

但是有些老旧的编译器不允许static成员在其声明式获得初值，或者所谓"in-class 初值设定"也只能对整数常量进行。此时我们可以在实现文件中定义其初值。

```cpp
const int Tuple::GroupSize = 5;
```

但是此时我们想要像上面Tuple类中value数组利用GroupSize的值进行分配内存初始化的操作是非法的。因为此时GroupSize值是不明确的，此时要使用“the enum hack”的补偿做法。其理论基础是:**一个属于枚举类型("enumerated type")的数值可权充整数类型被使用**。


```cpp
class Tuple {
private:
    enum { GroupSize = 5 };
    int value[GroupSize];
}
```
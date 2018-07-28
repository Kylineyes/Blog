---
title: TensorFlow上手(1) 环境配置
date: 2018-7-26 16:01:32
categories: TensorFlow
tags: 
    - Python
    - TensorFlow
toc: true
thumbnail: /images/TensorFlow/TensorFlow-thumbnail.png
banner: /images/TensorFlow/TensorFlow-banner.png
---

# TensorFlow 简介

TensorFlow 最初由Google大脑小组（隶属于Google机器智能研究机构）的研究员和工程师们开发出来，用于机器学习和深度神经网络方面的研究，但这个系统的通用性使其也可广泛用于其他计算领域。
Tensor的意思是张量，代表N维数组；Flow的意思是流，代表基于数据流图的计算。把N维数字从流图的一端流动到另一端的过程，就是人工智能神经网络进行分析和处理的过程。

# 配置环境

本文章是在 Windows 10 (1803) 下进行的配置，以 Python 语言作为工作语言。

## 下载 Anaconda

Anaconda指的是一个开源的Python发行版本，其包含了conda、Python等180多个科学包及其依赖项，方便我们后面的配置。

[官网](https://www.anaconda.com/)上，当下最新的版本 Anaconda 5.2 For Windows，可使用 Python 3.6。

下载并安装完成后我们要进行配置。

## 配置 Anaconda

安装完 Anaconda 后，将 `(安装目录)\Anaconda3\Scripts` 加入系统环境变量 `Path` 中，网上相关教程多，这里按下不表，然后我们的操作都要在命令行下进行。

以管理员权限打开命令行，输入 `conda -V` 或 `conda --version` 显示当前安装的版本，我这里是 4.5.8 ，若无错误则说明上述变量加入无误，接下来输入`conda upgrade --all` 把所有工具包进行升级，避免后续出现问题。

接下来要给 Python 建立一个独立的环境，输入 `activate` ，发现命令行前多出了 (base) ， 这是 Anaconda 自带的环境。此时若输入 `python` 就可以进入 Anaconda 自带的 Python 环境，这个环境是与你之前有无安装 Python 无关的，同时此时输入 `python -V` 就可以查看此时 python 的版本。

接下来创建一个自己的虚拟环境，我们输入以下代码

```bash
conda create -n tfLearn python=3
```

创建一个名称为 tfLearn 的虚拟环境，使用的 python 版本是 python3，你也可以细化到 `python=3.x.x`。
我们可以使用

```bash
conda env list
```

列出所有环境的名称和所在位置。

此时我们用下列语句切换至我们的 tfLearn 环境。

```bash
activate tfLearn
```

此时命令行前的 (base) 改变成了 (tfLearn) ，表明切换成功，下一步我们进行 python 的配置。

## 配置 python

进入 tfLearn 环境后，我们使用下列安装 tensorFlow。

```bash
pip install tensorflow-gpu==1.9.0
```

注意此处指定了 tensorflow 是以 gpu 方式安装的，且版本为 1.9.0 ，这是为了与后面的 CUDA 配套的。

如果此时你不是以管理员权限进行的安装的话，在此处安装结尾可能会出现报错。

## 安装 CUDA 和 cuDNN

[NVIDIA官网中CUDA下载](https://developer.nvidia.com/cuda-toolkit-archive)
请选择 CUDA 9.0，这是配套的。

[NVIDIA官网中cuDNN下载](https://developer.nvidia.com/rdp/cudnn-download)
请选择 cuDNN v7.1.4 for CUDA 9.0，解压后放置于CUDA v9.0的根目录下（文件夹刚好是对应的）。

## 测试环境

tfLearn 环境下，进入 python 环境，输入

```python3
import tensorflow as tf
```

经过一小段等待，没有报错信息输出，说明安装成功，我们的测试环境就搭建好了。

## 安装jupyter notebook

在 Anaconda 页面中，在 Home选项卡下，将 `Applications on` 切换到 tfLearn 环境，下面会出现一些工具可以安装，我们找到 `jupyter notebook` 点击 `install` ，完成后点击 `Launch`，浏览器会默认打开 `http://localhost:8888` 这是 jupyter notebook的工作环境，也是我们之后要实践的主要场地。

# Anaconda 意义

Anaconda 是一个多环境的配置工具，他解决我们在工作中不同工具版本的共存问题。
他实现这个解决方法的方式十分简单，我们的新建的一个个工作环境都在 `Anaconda3\envs` 下，点开我们的 tfLearn 文件夹，里面就是一个完备的 python 环境。

---

#引用

1. https://www.jianshu.com/p/eaee1fadc1e9


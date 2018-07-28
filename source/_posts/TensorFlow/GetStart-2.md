---
title: TensorFlow上手(2) 第一个程序
date: 2018年7月28日 03:01:32
categories: TensorFlow
tags: 
    - Python
    - TensorFlow
toc: true
thumbnail: /images/TensorFlow/TensorFlow-thumbnail.png
banner: /images/TensorFlow/TensorFlow-banner.png
---

# 基本使用

以下是来自 `TensorFlow 中文社区`的对 TensorFlow 工作流程的解释：
使用 TensorFlow, 你必须明白 TensorFlow:

*   使用图 (graph) 来表示计算任务。
*   在被称之为 `会话 (Session)` 的上下文 (context) 中执行图。
*   使用 tensor 表示数据。
*   通过 `变量 (Variable)` 维护状态。
*   使用 feed 和 fetch 可以为任意的操作(arbitrary operation) 赋值或者从其中获取数据。

有点拗口，但可以将其理解为工厂中，原料由tensor提供，工艺流程由图设计，一些机器可以维护现场状态或数据，由变量提供，而 feed 和 fetch 是人工的工具。

## Jupyter 打开

在浏览器中，打开 Jupyter 工作环境，新建一个文件（新建过程请查阅 _引用3_），开始我们的 tf 之旅。

## 构建图

构建图的第一步, 是创建源 op (source op)。源 op 不需要任何输入, 例如 `常量 (Constant)`。 源 op 的输出被传递给其它 op 做运算。

```python
import tensorflow as tf
# 创建一个常量 op，值为 2
v1 = tf.constant(2)
# 创建一个常量 op，值为 3
v2 = tf.constant(3)
# 创建一个乘法 op，
# 把 'v1' 和 'v2' 作为输入
# 返回值 'res' 代表乘法的结果
res = tf.multiply(v1,v2)
```

默认图现在有三个节点，两个 `constant() op`，和一个`mul() op`。 为了真正进行相乘运算，并得到乘法的结果，你必须在会话里启动这个图。

## 在一个会话中启动图

构造阶段完成后，才能启动图。启动图的第一步是创建一个 `Session` 对象，如果无任何创建参数，会话构造器将启动默认图。

```python
# 调用sess的 run() 方法来执行乘法 op, 传入 'res' 作为该方法的参数。
# 整个执行过程是自动化的, 会话负责传递 op 所需的全部输入. op 通常是并发执行的。
# 函数调用 run(res) 触发了图中三个 op (两个常量 op 和一个乘法 op) 的执行。
result = sess.run(res)
print result
# ==> 6
# 任务完成, 关闭会话.
sess.close()
```

`Session` 对象在使用完后需要关闭以释放资源。除了显式调用 close 外，也可以使用 with 代码块来自动完成关闭动作。

```python
with tf.Session() as sess:
    print(sess.run(res))
```

>在实现上，TensorFlow 将图形定义转换成分布式执行的操作，以充分利用可用的计算资源(如 CPU 或 GPU)。一般你不需要显式指定使用 CPU 还是 GPU，TensorFlow 能自动检测。如果检测到 GPU，TensorFlow 会尽可能地利用找到的第一个 GPU 来执行操作。
如果机器上有超过一个可用的 GPU，除第一个外的其它 GPU 默认是不参与计算的。为了让 TensorFlow 使用这些 GPU，你必须将 op 明确指派给它们执行。
设备用字符串进行标识，目前支持的设备包括：
* `"/cpu:0"`：机器的 CPU。
* `"/gpu:0"`：机器的第一个 GPU，如果有的话。
* `"/gpu:1"`：机器的第二个 GPU，以此类推。
`with...Device` 语句用来指派特定的 CPU 或 GPU 执行操作：
```python
with tf.Session() as sess:
  with tf.device("/gpu:1"):
    matrix1 = tf.constant([[3., 3.]])
    matrix2 = tf.constant([[2.],[2.]])
    product = tf.matmul(matrix1, matrix2)
    ...

```

## Fetch

Fetch 可以帮助我们从 Session 中取回多个结果，在之前的例子中，我们只取回了一个 res 的结果，下个例子中，我们用 Fetch 来一次性获得多个结果。

```
import tensorflow as tf
v1 = tf.constant(2)
v2 = tf.constant(3)
res1 = tf.multiply(v1,v2)
res2 = tf.add(v1,v2)

with tf.Session() as sess:
    res = sess.run([res1, res2])
    print(res)
# ==> [6, 5]
```

## Feed

上面的例子在计算图的时候用到了 tensor，都是以常量或变量的形式存储的，而同时 TensorFlow 还提供了 Feed 机制，来为临时替换图中任意操作的 tensor。

Feed 使用一个 tensor 值临时替换一个操作的输出结果。你可以提供 feed 数据作为 run() 调用的参数。Feed 只在调用它的方法内有效，方法结束，feed 就会消失。
在使用 Feed 之前，我们要进行标记，标记的方法是使用 tf.placeholder() 为这些操作创建占位符。

```python
v1 = tf.placeholder(tf.float32)
v2 = tf.placeholder(tf.float32)
output = tf.multiply(input1, input2)

with tf.Session() as sess:
  print(sess.run(output, feed_dict={input1:[7.0], input2:[2.0]}))
# ==> [14.]
```


---

#引用

1. https://www.jianshu.com/p/eaee1fadc1e9
2. http://www.tensorfly.cn/tfdoc/get_started/basic_usage.html
3. https://blog.csdn.net/red_stone1/article/details/72858962
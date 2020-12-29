# Summary

* [Introduction](README.md)
* [MachineLearning](machinelearning.md)
  * [无监督学习](machinelearning/wu-jian-du-xue-xi.md)
  * [Model and Cost Function](machinelearning/model-and-cost-function.md)
  * [Linear Algebra](machinelearning/parameter-learning.md)
  * [Multivariate Linear Regression](machinelearning/multivariate-linear-regression.md)
* [开发环境](develope-environment.md)
* [附录](fu-lu.md)
  * [Numpy教程](fu-lu/numpyjiao-cheng.md)
    * [NumPy - 简介](fu-lu/ts-numpy-tut-zh-master/0.md)
    * [NumPy - 环境](fu-lu/ts-numpy-tut-zh-master/1.md)
    * [NumPy - Ndarray 对象](fu-lu/ts-numpy-tut-zh-master/2.md)
    * [NumPy - 数据类型](fu-lu/ts-numpy-tut-zh-master/3.md)
    * [NumPy - 数组属性](fu-lu/ts-numpy-tut-zh-master/4.md)
    * [NumPy - 数组创建例程](fu-lu/ts-numpy-tut-zh-master/5.md)
    * [NumPy - 来自现有数据的数组](fu-lu/ts-numpy-tut-zh-master/6.md)
    * [NumPy - 来自数值范围的数组](fu-lu/ts-numpy-tut-zh-master/7.md)
    * [NumPy - 切片和索引](fu-lu/ts-numpy-tut-zh-master/8.md)
    * [NumPy - 高级索引](fu-lu/ts-numpy-tut-zh-master/9.md)
    * [NumPy - 广播](fu-lu/ts-numpy-tut-zh-master/10.md)
    * [NumPy - 数组上的迭代](fu-lu/ts-numpy-tut-zh-master/11.md)
    * [NumPy - 数组操作](fu-lu/ts-numpy-tut-zh-master/12.md)
    * [NumPy - 位操作](fu-lu/ts-numpy-tut-zh-master/13.md)
    * [NumPy - 字符串函数](fu-lu/ts-numpy-tut-zh-master/14.md)
    * [NumPy - 算数函数](fu-lu/ts-numpy-tut-zh-master/15.md)
    * [NumPy - 算数运算](fu-lu/ts-numpy-tut-zh-master/16.md)
    * [NumPy - 统计函数](fu-lu/ts-numpy-tut-zh-master/17.md)
    * [NumPy - 排序、搜索和计数函数](fu-lu/ts-numpy-tut-zh-master/18.md)
    * [NumPy - 字节交换](fu-lu/ts-numpy-tut-zh-master/19.md)
    * [NumPy - 副本和视图](fu-lu/ts-numpy-tut-zh-master/20.md)
    * [NumPy - 矩阵库](fu-lu/ts-numpy-tut-zh-master/21.md)
    * [NumPy - 线性代数](fu-lu/ts-numpy-tut-zh-master/22.md)
    * [NumPy - Matplotlib](fu-lu/ts-numpy-tut-zh-master/23.md)
    * [NumPy - 使用 Matplotlib 绘制直方图](fu-lu/ts-numpy-tut-zh-master/24.md)
    * [NumPy - IO](fu-lu/ts-numpy-tut-zh-master/25.md)
    * [NumPy - 实用资源](fu-lu/ts-numpy-tut-zh-master/26.md)
  * [Octave](fu-lu/octave.md)
    * [Matrix & Victor](fu-lu/octave/matrix-and-victor.md)
  * Scrapy
    * [run](fu-lu/scrapy/run.md)
* ROS
  * [Installation](ros/installation.md)
安装流程 https://index.ros.org/doc/ros2/Installation/Foxy/

MAC 安装中遇到的问题：

```
python3 -m pip install pygraphviz pydot
```
安装编译报错，架构不支持。需要设置一个环境变量。

```
export ARCHFLAGS="-arch x86_64
```

`ros2 run demo_nodes_cpp talker` 执行发生 python 错误时，看一下 `/usr/local/bin/python3` 是否存在，不存在想办法添加一个链接。不要修改成 `/usr/bin/python3`。否则会发生一些 python 执行错误。
```
Fatal Python error: _PyInterpreterState_Get(): no current thread state
Python runtime state: unknown
```

### 常用指令记录

设置环境变量
```
. ~/ros2_foxy/ros2-osx/setup.bash
```

https://index.ros.org/doc/ros2/
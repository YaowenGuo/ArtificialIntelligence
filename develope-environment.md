入门机器学习需要一些编程语言基础来实践，如果只是做理论有些不着实际，通过实际的操作验证理论能够帮助理解其中的运行机制和加强记忆。目前使用最广泛的语言是python，并不是其他语言不能够用于机器学习，而是其他语言缺少一些机器学习方面的库。有了这些苦，一两句代码就能解决的问题，没有这方面的库，如果自己编写可能会花上很多时间，并且这些库可能跟机器学习方面的内容并不相关，自己动手编写这些库分散了学习AI的注意力，也会浪费不少的时间。

除了能够使用python编程之外，一些模块在机器学习中经常用到，例如 Numpy用于处理矩阵运算。不同的人学习习惯不一样，有些人喜欢学完基础再学应用，有些人习惯先动手开始实践，遇到没有见过的知识点再去学习。这里将常用 Module 放到附录中，方便想要先学这些基础工具包的人，也方便需要的时候快速查看。然而事实并不总是如此，因为许多时候，你也不知道要学的内容里有哪些是先决条件。只有遇到了才知道要用到。所以在使用的时候，会加以说明。

### python

python3已经出现有几年的时间了，使用python3更面向未来。如果你看到哪个资料上仍旧提醒使用python2，建议看一下资料的发表时间。

###### ubuntu

> python

sudo apt install python3

> pip安装

pip 是 python 的模块安装的命令行工具，能够自动从官方的库中安装其他模块。  
sudo apt install python3-pip

安装了pip之后 pip 在ubuntu的命令名称是 pip3

> NumPy安装  
> NumPy 是一个  
> sudo pip3 install numpy

有些教程上面建议使用Anaconda或者Canopy，或者Python\(x,y\)来安装python科学计算库，这些软件库提供了一个用于科学计算的python库打包。能够方便的安装各种计算模块，省心省力。对与我这种不愿意安装用不到的软件包的强迫症来说，我还是愿意单独安装需要的软件包，这也意味着要自己解决一些软件问题。

###### Arch

python

相较于其他版本，arch的软件包是非常激进的，总是使用最新发布的软件包，这也是我喜欢的地方。所以arch默认的python版本是python3。

python3安装

sudo  pacman -S python

pip安装

sudo pacman -S python-pip

NumPy 安装

sudo pip install numpy
###### 测试是否安装成功

先进入python环境，然后导入numpy包即可

```shell
$ python3
>> import numpy
```

如果没有任何反馈，说明已经安装成功了，否则，就是没有安装成功，则会收到如下反馈。

```
Traceback (most recent call last):
   File "<pyshell#0>", line 1, in <module>
      import numpy
ImportError: No module named 'numpy'
```

## Matplotlib

2D 绘图领域的基础套件，它让使用者将数据图形化，并提供多样化的输出格式。

## pandas

pandas 是基于 Numpy 开发的住啊们用于数据分析的开源 Python 库。

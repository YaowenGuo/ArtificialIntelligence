> 本课要点

- linear regression
- 监督学习的整个过程是什么样子的。


这有一个预测房屋价格的例子，其中房屋价格的数据集是这样的：
![](/assets/house_price_example.png)

有一套1250feet<sup>2</sup> 的房子，想要知道这套房子能卖多少钱。根据已有的数据需要构建一个模型，如果是直线型，根据这个数据集构建的模型大致是这样的：
![](/assets/house_price_example2.png)
从直线模型中可以得到大致220000美元。

这个例子被归类为监督学习，因为对于每个数据，都给出了“正确答案”，即：对于确定的房屋面积，房屋的价格是多少。更确切的说，是监督学习中的线性回归问题，回归是指：根据已有的数据，预测任意给定输入的输出值。对于这个立即就是房屋价格。


> 训练集

在监督学习中已有的数据集被称为训练集。对于预测房屋价格的例子，训练集就是已知的房屋面积和价格。

> 课程中使用到的符号

   m ： 训练集的数量，对于上面的例子。如果已知的房屋价格有47个，则m=47.
   x ： 输入值、也称作特征量
   y ： 输出变量，也称作目标量
   (x, y) ： 表示一个训练样本。为了指出某个训练样本，可以使用（x<sup>(i)</sup>, y<sup>(i)</sup>)表示第i个训练样本。
   
   
> 测试题
![](/assets/house_price_test1.png)

以上就是学习算减的工作流程，它大致是这样的：给学习算法（Learning Algorithm）喂一个数据集（Training Set），它将输出一个函数h,(h表示hypothesis(假设）,之所以这样叫是因为早期的机器学习资料中这样叫，现在成了机器学习的标准用语）。函数h是关于输入和输出的函数。对于上面的例子，输入为房屋的面积x，输出为房屋的价格y。h是x到y的一个函数映射。
![](/assets/training_model.png)
机器学习算法的重点是，如何得到这个函数h，对于一个未知的线性函数，通常这样表示：

h<sub>θ</sub>(x) = θ<sub>0</sub> + θ<sub>1</sub>x

该函数就是线性回归模型（Linear Regression),并且是线性回归中的单变量线性回归，这个变量就是x。其中 θ<sub>i</sub>被称为模型参数。

> 在单变量线性回归中如何计算θ0和θ1

![](/assets/learning_algorithm.png)

计算点变量线性回归的思路是，要想让这些点尽量和结果的线靠近，一个好的方法是计算点到直线的距离最小。这将求θ<sub>0</sub>,θ<sub>1</sub>转换成了一个最小化问题。

要使距离最小 就要求|hθ(x) - y| 最小，对于绝对值不好求，可以使用其平方
(hθ(x) - y)<sup>2</sup>

对于所有的已知数据集，我们希望算出所有的距离平均最小。因此就是求：
![](/assets/learning_algorithm1.png)

其中m就是数据集的数量。h<sub>θ</sub>(x<sup>(i)</sup>) = θ<sub>0</sub> + θ<sub>1</sub>x<sup>(i)</sup>
要求θ<sub>0</sub>，θ<sub>1</sub>就变成了一个关于θ<sub>0</sub>，θ<sub>1</sub>的函数。对上面的函数进行改写：
![](/assets/liner_function1.png)

![](/assets/liner_function2.png)

To break it apart, it is 12 x¯ where x¯ is the mean of the squares of hθ(xi)−yi , or the difference between the predicted value and the actual value.

上面的式子也叫平方误差方程。




   
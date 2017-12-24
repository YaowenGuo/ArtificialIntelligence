# 多元线性回归 
一个新的更有效的的线性回归函数，这种形式适合于多变量或者多特征的情况。

之前的房子价格预测的例子中，价格只和房屋面积进行了关联，然而房屋的价格可能还和其他许多属性有关系，例如房间数量、楼层数、房屋的年限等
![](/assets/house_price_pridict1.png)

为了使用更多的特征预测房子价格，需要像之前一样对属性和房屋价格之间构建一个相关函数。为了更好的表示，需要对符号进行一些约定：
符号：
- n = 属性的数量
- $$\\x^{(i)}\\$$ = 第i个训练样本的输入特征值
- $$\\x_j^{(i)}\\$$ = 第i个训练样本的第j个特征值

对于上面的例子，n = 4，$$\\x^{(1)}\\$$就是第一行除房屋价格的所有数据。而$$\\x_1^{(2)}\\$$就是第一行第二列，Number of bedrooms 5.

对于多特征的例子。线性函数的构造是这个样子
$$\\
h_\theta(x) = \theta_0 + \theta_1 x_1 + \theta_2 x_2 + ... + \theta_n x_n \\

x = \begin{bmatrix} x_0 \\ x_1 \\ x_2 \\ \vdots \\ x_n \end{bmatrix} \in R^{n+1}  \\

\theta = \begin{bmatrix} \theta_0 \\ \theta_1 \\ \theta_2 \\ \vdots \\ \theta_n \end{bmatrix} \in R^{n+1}  \\

上面的公式也可以写成 \\

h_\theta(x) = \theta_0 x_0 + \theta_1 x_1 + \theta_2 x_2 + ... + \theta_n x_n \\
= \theta^T x \\
x_0 = 1 \\
\theta^T = \begin{bmatrix} \theta_0 & \theta_1 & \dots & \theta_n \end{bmatrix} \\
x = \begin{bmatrix} x_0 \\ x_1 \\ \vdots \\ x_n \end{bmatrix}

\\$$
该函数就是多元线性回归（multivariate linear regression)，多元是指函数的变量有多个。
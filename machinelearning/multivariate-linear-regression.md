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

# 多变量的梯度下降（Gradient Descent for Multiple Variables)
  之前学习了假设的多变量的线性回归函数，接下来学习在如何找到满足这一假设的参数。尤其是如何使用梯度下降法来解决多特征的线性回归问题。
   现假设现有多元线性回归并约定 x0=1 该模型的参数是从 θ0 到 θn。
$$\\\begin{alignat}{0}
Hypotheisi : h_\theta(x) = \theta_0 x_0 + \theta_1 x_1 + \theta_2 x_2 + ... + \theta_n x_n \\

Parameters : \theta_0, \theta_1, \dots, \theta_n \\

Cost Function : J(\theta_0, \theta_1, \dots, \theta_n） = \frac1{2m} \sum_{i = 1}^m (h_\theta(x^{(i)}) - y^{(i)})^2
\end{alignat}\\$$ 

该模型的参数是θ0到θn，但是不是把它看作是n个独立的参数，而是将其作为有效的整体theta，其中theta是一个n + 1维向量。所以 你现在就可以把这个模型的参数想象成其本身就是一个 n+1 维的向量，对于函数J也是如此。[这时候我突然明白之前的梯度下降为什么要同时更新θ0、θ1了，就是因为它们是一个整体，而不是单独的两个变量]
   它的梯度下降算法看题来是这个样子。
repeat {
$$\\\begin{gather}
\theta_j := \theta_j - \alpha\frac{\partial}{\partial\theta_j} J(\theta_0, \dots , \theta_n) \qquad (simutaneously \quad update \quad for \quad every \quad j = 0, \dots , n)
\end{gather}\\$$
}
 
  在之前的课程中，我们知道，当特征 N = 1 时，得到的梯度下降是有两个分别更新θ0和θ1的规则公式。
$$\\\begin{align*}
 & \text{repeat until convergence:} \; \lbrace \newline \; & \theta_0 := \theta_0 - \alpha \frac{1}{m} \sum\limits_{i=1}^{m} (h_\theta(x^{(i)}) - y^{(i)}) \cdot x_0^{(i)}\newline \; & \theta_1 := \theta_1 - \alpha \frac{1}{m} \sum\limits_{i=1}^{m} (h_\theta(x^{(i)}) - y^{(i)}) \cdot x_1^{(i)} \newline \; &  \rbrace 
\end{align*}\\$$
  
  当特征 N >= 1 的时候，对偏导数求导将得到如下的规则：
repeat {
$$\\\begin{gather}
\theta_j := \theta_j - \alpha \frac1{m} \sum_{i = m}^m(h_\theta(x^{(i)}) - y^{(i)}) x_j^{(i)} \qquad (simutaneously \quad update \quad \theta_j \quad for \quad j = 0, \dots , n)

\end{gather}\\$$
}

最后，需要弄明白的是，为什么新旧两种算法实际上是一回事儿或者说为什么这两个是类似的算法，为什么它们都是梯度下降算法。假设N = 1，对上述的公式进行特化，这时会发现，将特殊j = 0, 1带入后的样子和之前课程的梯度下降算法是一样的。


# 梯度下降实践（gradient descent in practice）
- 一些关于梯度下降运算中的实用技巧

### 特征缩放（feature scaling）

> 中心思想:
    如果在一个问题中有多个特征，如果能过确不同保特征的取值都在相近的取值范围内，注意是不同特征。这样梯度下降法就能更快第收敛。

   具体地说，假如一个问题有两个特征，其中
 
- x1 是房屋面积大小，它的取值在0到2000之间。
- x2 是卧室的数量，可能这个值取值范围在1到5之间。

如果要画出代价函数J(θ) 的轮廓图，J(θ) 是一个关于参数 θ0 θ1 和 θ2 的函数。但在这里要忽略 θ0，暂时不考虑 θ0。并假想一个函数的变量只有 θ1 和 θ2。但因为 x1 的取值范围远远大于 x2 的取值范围，最终画出来的代价函数 J(θ) 的轮廓图就会呈现出这样一种非常偏斜并且椭圆的形状。2000 和 5的比例会让这个椭圆非常瘦长。所以这是一个又瘦又高的椭圆形轮廓图。就是这些非常高大细长的椭圆形构成了代价函数 J(θ)。
![](/assets/feature_scaling1.png)
 
而如果你用这个代价函数来运行梯度下降的话。想要得到最终稳定的梯度值可能需要花很长一段时间。并且可能会来回波动然后会经过很长时间最终才收敛到全局最小值。
![](/assets/feature_scaling2.png)
事实上，你可以想像，如果这些比例再被放大一些的话，长宽比例更大，画出来的更加细长。那么可能情况会更糟糕，梯度下降的过程可能更加缓慢。需要花更长的时间反复来回振荡，才找最终到一条正确通往全局最小值的路经。

   这种情况下，一种有效的方法是对特征进行缩放。具体来说，如果把x1定义为房屋的大小除以2000，x2定义为房屋的数量除以5。 那么表示代价函数 J(θ)的轮廓图的形状就会变得扁得没那么严重，可能看起来更圆一些了。如果你用这样的代价函数来执行梯度下降的话，你可以从数学上来证明，梯度下降算法就会找到一条更捷径的路径通向全局最小。而不是像刚才那样沿着一条让人摸不着头脑的路径一条复杂得多的轨迹来找到全局最小值。
![](/assets/feature_scaling3.png)
因此，通过特征缩放"消耗掉"这些值的范围差异。在这个例子中，我们最终得到的两个特征x1 和 x2 都在0和1之间，这样得到的梯度下降算法就会更快地收敛。

   一般第，我们执行特征缩放时，通常的目的是将特征的取值约束到-1 到 +1 的范围内。你的特征 x0 是总是等于1，因此这已经是在这个范围内。但对其他的特征你可能需要通过除以不同的数来让它们处于同一范围内。-1 和 +1 这两个数字并不是太重要，所以 如果你有一个特征 x1，它的取值在0和3之间，这没问题。如果你有另外一个特征取值在-2 到 +0.5之间，这也没什么关系。这都非常接近 -1 ~ +1 的范围，所以它们都可以。
但如果你有另一个特征，比如叫 x3。假如它的范围在 -100 到 +100之间。那么 这个范围跟-1到+1就有很大不同了。这可能是一个不那么好的特征。类似地 如果你的特征在一个
非常非常小的范围内，比如另外一个特征 x4 它的范围在 0.0001 和 +0.0001 之间，那么这同样是一个比-1到+1小得多的范围。因此，同样会认为这个特征也不太好。
 
所以 合适的范围可以大于或者小于 -1 到 +1，但是也别太大。只要大得不多就可以接受
，比如 +100。或者也别太小，比如这里的0.001。不同的人有不同的经验，但是一般的考虑是：
- 如果一个特征是在 -3 到 +3 的范围内，那么你应该认为这个范围是可以接受的
 但如果这个范围大于了 -3 到 +3 的范围，可能就要开始注意了
- 如果它的取值在-1/3 到+1/3的话可以接受。或者是0到1/3 或-1/3到0这些典型的范围，都是可以接受的。

  但如果特征的范围取得很小的话，比如像这里的 x4，就要开始考虑进行特征缩放了。因此 总的来说，不用过于担心你的特征是否在完全相同的范围或区间内，只要它们都足够接近，梯度下降法就会正常地工作。
   除了在特征缩放中将特征除以最大值以外，有时候我们也会进行一个称为均值归一化的工作(mean normalization)

### 均值归一化（mean normalization）

> 核心思想

如果你有一个特征 xi。使用 xi - μi 来替换 xi 以使xi的平均值为0。
 
很明显，我们不会把这一步应用到 x0 中，因为 x0 总是等于1，所以它不可能有为0的的平均值。但是对其他的特征来说，比如房子的大小取值介于0到2000，并且假如房子面积的平均值是等于1000的，那么你可以用这个公式将 x1 的具有平均0。
$$\\
x_1 = \frac{size - 1000}{2000} \\
x_2 = \frac{\#bedrooms - 2}{5}
\\$$
 x1 减去平均值 μ1 再除以2000。类似地，如果你的房子有五间卧室，并且平均一套房子有两间卧室，那么你可以使用第二个公式来归一化你的第二个特征 x2。
在这两种情况下，你可以算出新的特征 x1 和 x2。它们的范围可以在-0.5和+0.5之间，x2的值实际上肯定会大于0.5 但很接近。更一般的规律是你可以用这样的公式$$\\x_i := \dfrac{x_i - \mu_i}{s_i}\\$$。
 其中定义：
- μi的意思是在训练集中特征 xi 的平均值
- Si 是该特征值的范围（范围是指最大值减去最小值）或者学过标准差的同学可以记住
 也可以把 Si 设为变量的标准差，但其实用最大值减最小值就可以了。
  
对于第二个例子需要说明的是，如果最大值为5，那么减去最小值1。这个范围值就是4。但不管咋说 这些取值都是非常近似的。只要将特征转换为相近似的范围就都是可以的。特征缩放其实并不需要太精确，只是为了让梯度下降能够运行得更快一点而已。让梯度下降收敛所需的循环次数更少。

## 关于α的优化策略

repeat {
$$\\\begin{gather}
\theta_j := \theta_j - \alpha\frac{\partial}{\partial\theta_j} J(\theta_0, \dots , \theta_n) 
\end{gather}\\$$
}

- "Debugging"：如何确保梯度下降正常的工作
- 如何选择学习速率α

梯度下降算法所做的事情 就是为你找到 一个 θ 值 并希望它能够最小化代价函数 J(θ)。一个做法是在梯度下降算法运行时绘出代价函数 J(θ) 的值 ：
![](/assets/value_of_function_gradient.png)

这里，x（横）轴是梯度下降算法迭代的次数，而不是θ，在迭代一定步数之后，得到一个θ值，将该值代入J(θ) 得到的值，就是该值的纵坐标。 所以这条曲线显示的是梯度下降算法迭代过程中代价函数 J(θ) 的值。如果梯度下降算法正常工作，那么每一步迭代之后 J(θ) 都应该下降。这条曲线的一个用处在于：它可以告诉你，如果你看一下 在这条曲线 达到300步迭代之后 也就是300步到400步迭代之间，看起来 J(θ) 并没有下降多少，所以当你到达400步迭代时这条曲线看起来已经很平坦了。也就是说，在这里400步迭代的时候梯度下降算法基本上已经收敛了。因为代价函数并没有继续下降，所以说观察这条曲线 可以帮助你判断梯度下降算法是否已经收敛。顺便说一下，对于每一个特定的问题 梯度下降算法所需的迭代次数可以相差很大。也许对于某一个问题，梯度下降算法只需要30步迭代就可以收敛。然而换一个问题，也许梯度下降算法就需要3000步迭代，对于另一个机器学习问题则可能需要三百万步迭代。实际上我们很难提前判断梯度下降算法需要多少步迭代才能收敛。通常我们需要画出这类曲线，画出代价函数随迭代步数数增加的变化曲线。通常，通过看这种曲线可以判断梯度下降算法是否已经收敛。另外，进行一些自动的收敛测试也可以看出梯度下降的工作效果，也就是说用一种算法来判断梯度下降算法是否已经收敛。自动收敛测试的一个非常典型的例子是：如果代价函数 J(θ) 的下降小于一个很小的值 ε，那么就认为已经收敛。比如可以选择 1e-3。但我发现，通常要选择一个合适的阈值 ε 是相当困难的。因此，为了检查梯度下降算法是否收敛实际上还是通过看上面的那条曲线图。而不是依靠自动收敛测试。此外，这种曲线图也可以在算法没有正常工作时提前警告你。具体来说，如果代价函数 J(θ) 随迭代步数的变化曲线是这个样子：
![](/assets/value_of_function_gradient1.png)
J(θ) 实际上在不断上升，你就能明确地判断出梯度下降并没有很好的工作，而需要用一个更小的α（当然，判断这一切的前提是你的程序没有bug）。但是这种趋势的走向可以明确判断出，一定有哪里出了问题。

   有时候也可能遇到J(θ)的值呈现这种趋势：
![](/assets/value_of_function_gradient2.png)
下降一段时间后，开始上升，然后在下降一段然后又是上升，如此循环。解决这类问题的办法也是选用一个小一点的α。这里没有给出证明方法，但是在其他关于成本函数J的假设下，这对于线性回归是成立的，数学家们已经表明，如果你的学习率α足够小，那么J（theta）应该在每次迭代中减少。所以发生以上两种现象的原始都是α太大了，需要选取一个更小的。但是不要把α选的太小了，太小会导致梯度下降的很慢。
![](/assets/value_of_function_gradient3.png)

α选择通常测试如下一些数字：
..., 0.001, 0.01, 0.1, 1, ...
这些是不同数量级的数，通过这些不同的α值计算J(θ)的迭代次数函数，然后选择导致J(θ)快速下降的α。实际上并不一定以十倍的步进，这只是一个例子。通常会尝试这个范围的取值。例如：
..., 0.001, 0.003, 0.01, 0.03, 0.1, , 0.3, 1, ...

这个间隔每个数比以前的值大约3倍。所以要做的就是尝试一系列值，直到找到一个太小的值，并确保找到一个太大的值。然后尽量选择最大的可能值，或者稍微小于最大合理值。这样做通常能得到一个很好的学习速度。
 
 
 

 
 
 

 
 
 
 

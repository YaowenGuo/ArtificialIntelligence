# Matrix & Vector

***目标：***
- 掌握矩阵(Matrix)和向量(Vector)

---

Matrice: (rectangular array of numbers written between square brackets.)矩阵是一个m行n列的数字集合，为了表示改数据集，将其放在一对方括号中。
例如：
$$\\
\begin{bmatrix}

1 & 2 & 3 \\
2 & 6 & 3 \\
4 & 4 & 2

\end{bmatrix}
\\$$

或者，这也是一个矩阵
$$\\
\begin{bmatrix}

1 & 2 & 3 \\
2 & 6 & 3 
\end{bmatrix}
\\$$

上面这两种都是2D或者二维（two dimensional array）数组。矩阵的维数可以写成行*列的形式。第一个矩阵维数是3*3,第二个矩阵维数可以写成2*3。维度m*n的矩阵记做
$$\\
R^{2 \times 3}
\\$$

矩阵的元素是矩阵中的每一个数字。对于一个矩阵A，第i行j列的元素记为(注意索引从1开始)：
$$\\
A_{ij}
\\$$

#### 向量

向量是矩阵的一种特例：只有一列的矩阵。例如
$$\\
y = 
\begin{bmatrix}

1 \\
2 \\
4

\end{bmatrix}
\\$$

这是一个向量，由于它有3行，它被称为3维向量。
需要注意的是：
- 在编程语言中一些索引会从0开始，但是在数学中，都是从1开始的。
- 在矩阵的表示中经常使用大写字母表示矩阵或者向量。而小写字母表示它们的元素。不和谐的表示并不会错，只是人们习惯这样表示。

# Addition and Scalar Multiplication
目标：
- 矩阵的加法和乘法
- 数字和矩阵的乘法，也就是向量的乘法

---

### 加法
矩阵的加法是将连个矩阵的每个元素逐一相加，的到一个新的矩阵。矩阵的加法要求两个矩阵维度相同，否则无法相加。
$$\\
\begin{bmatrix} a & b \newline c & d \newline \end{bmatrix} +\begin{bmatrix} w & x \newline y & z \newline \end{bmatrix} =\begin{bmatrix} a+w & b+x \newline c+y & d+z \newline \end{bmatrix}
\\$$
$$\\
\begin{bmatrix} a & b \newline c & d \newline \end{bmatrix} - \begin{bmatrix} w & x \newline y & z \newline \end{bmatrix} =\begin{bmatrix} a-w & b-x \newline c-y & d-z \newline \end{bmatrix}
\\$$




### 数字和矩阵的乘法 除法
##### 乘法
实数和矩阵的乘法是一个和矩阵因子相同形状的矩阵。实数和矩阵的每一个元素相乘得到结果矩阵相应位置的元素值。

$$\\
\begin{bmatrix} a & b \newline c & d \newline \end{bmatrix} * x =\begin{bmatrix} a*x & b*x \newline c*x & d*x \newline \end{bmatrix}
\\$$

$$\\
3 \times \begin{bmatrix} 1 & 0 \\ 2 & 5 \\ 3 & 1 \end{bmatrix} = 
\begin{bmatrix} 3 & 0 \\ 6 & 15 \\ 9 & 3 \end{bmatrix} = 
\begin{bmatrix} 1 & 0 \\ 2 & 5 \\ 3 & 1 \end{bmatrix} \times 3
\\$$

##### 除法
矩阵除以一个整数相当于乘以这个数的倒数。
$$\\
\begin{bmatrix} 4 & 0 \\ 6 & 3 \end{bmatrix} / 4 = 
\frac1{4}\begin{bmatrix} 4 & 0 \\ 6 & 3 \end{bmatrix}
\\$$

***注意***
- 矩阵的除法被看做是乘法的变形。
- 不存在整数除以矩阵的情况，这种做法没有意义

### 算数符号优先级（combination of operands）
矩阵运算的优先级沿用了数字计算的符号优先级。
- 括号优先级最高
- 没有括号时，先乘除，后加减。想用优先级的运算符从左到右计算。

---

> numpy时间

```python
A = numpy.mat([[1, 2, 4], [5, 3, 2]])
B = numpy.mat([[1, 3, 4], [1, 1, 1]])

s = 2

add_AB = A + B

sub_AB = A - B

mult_As = A * s

div_As = A / s

add_As = A + s


print(add_AB, '\n')

print(sub_AB, '\n')

print(mult_As, '\n')

print(div_As, '\n')

print(add_As, '\n')

```

### 矩阵相乘

两个矩阵相乘
$$\\
\begin{bmatrix} a & b \newline c & d \newline e & f \end{bmatrix} *\begin{bmatrix} x \newline y \newline \end{bmatrix} =\begin{bmatrix} a*x + b*y \newline c*x + d*y \newline e*x + f*y\end{bmatrix}
\\$$

---

> numpy时间

```python
# mat函数用于生成矩阵
A = numpy.mat([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
v = numpy.mat([[1], [1], [1]])
Av = A * v

print(Av)

# 如果是数组，就要用特殊的函数进行点乘。或者改变数据类型
A = numpy.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
v = numpy.array([[1], [1], [1]])
Av = numpy.dot(A, v)
# Mul = A * v 是各对应项相乘。
print(Av)

# 函数不管数据类型是什么，都进行矩阵乘法，而multiply则不管数据类型是什么都进行
# 点乘（对应位置元素相乘）
# 数据类型不同的时候（一个数数组，一个是矩阵），默认按照矩阵乘法。
```

### 应用

矩阵的乘法对于一次性打包大量运算非常有用。

### 矩阵乘法的性质

- 普通数字或者标量的乘法是可交换的，但是矩阵乘法不是。可交换是指 a * b = b * a
- 矩阵乘法满足结合律 A \* (B \* C) = A \* (B \* C)

### 单位矩阵（identity matrix）
单位在这里指不会变化，在普通数字中，1是单位数，因为1乘以任何数都不改变他们的值。同样，在矩阵乘法中也存在镇这种现象，只不过单位不再是一个数字，而是一个矩阵，矩阵乘法中也存在这这样的矩阵。被称为单位矩阵（identity matrix）
。

单位矩阵是主对角线上是1，其他都是0的n*n矩形矩阵。
记做$$\\I或者I_{n \times n}\\$$。例如：
$$\\
I = 
\begin{bmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}
\\$$

For any Matrix A
$$\\
A_{m \times n} \times I_{n \times n} = I_{m \times m} \times A_{m \times n} = A
\\$$

---

> numpy 时间

```python
# 默认生成的是浮点数，要想生成整数需要特备指定
I1 = numpy.eye(2, dtype=numpy.int)
I2 = numpy.identity(2, dtype=numpy.int)
```

### 逆和转置（inverse and transpose）
##### 逆
对于普通的数字，单位1是很特殊的，对于数字a，存在着a * b = 1，我们都知道b = 1 / a。并不是所有的数字都有逆，例如0就没有。那么，在矩阵的乘法运算中，是否也存在着这种现象呢？类似的，我们把两个相乘得到单位矩阵的矩阵称为互逆矩阵。
如果A是一个m * n 的矩阵，并且具有逆，那么：
$$\\
A A^{-1} = A^{-1}A = I
\\$$

***注意***
- 只有方形矩阵才有逆矩阵
- 全零矩阵也没有逆矩阵
- 没有逆矩阵的矩阵被称为奇异矩阵，或者叫退化矩阵

##### 转置

矩阵的转置是将矩阵的行编程矩阵的列，如果A是一个m * n的矩阵，如果B是A的转置矩阵，则B是一个n * m 大小的矩阵，并且$$\\A_{ij} = B_{ji}$$。A的转置矩阵B记做：$$\\A^T\\$$。对于矩阵的转置，可以看做沿着主对角线，即$$\\A_{ii}\\$$翻转的结果。

---

> numpy 时间

```python
# 矩阵的逆用对象的.I返回
# 矩阵的转置使用.T获得
A = numpy.mat([[1,2,0], [0,5,6], [7,0,9]])

B = A.T
C = A.I
print(B)
print(C)
```

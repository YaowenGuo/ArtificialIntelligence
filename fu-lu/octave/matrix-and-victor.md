# 矩阵和向量
> 创建矩阵或者向量

% The ; denotes we are going back to a new row.
A = [1, 2, 3; 4, 5, 6; 7, 8, 9; 10, 11, 12]
% Initialize a vector 
v = [1;2;3] 

---

A = numpy.array([[1, 2, 3], [4, 5, 6], [7, 8, 9], [10, 11, 12]])


> 获取矩阵/向量大小

% Get the dimension of the matrix A where m = rows and n = columns
[m,n] = size(A)

---

m, n = A.shape
suze = A.shape

> 获取某一元素 注意:Octave索引从1开始，而python索引从0开始。

a_23 = A(2,3)

---

a_23 = A[1][2]

> 算术运算

```Octave
% Initialize matrix A and B 
A = [1, 2, 4; 5, 3, 2]
B = [1, 3, 4; 1, 1, 1]

% Initialize constant s 
s = 2

% See how element-wise addition works
add_AB = A + B 

% See how element-wise subtraction works
sub_AB = A - B

% See how scalar multiplication works
mult_As = A * s

% Divide A by s
div_As = A / s

% What happens if we have a Matrix + scalar?
add_As = A + s

```

---

```python
A = numpy.array([[1, 2, 4], [5, 3, 2]])
B = numpy.array([[1, 3, 4], [1, 1, 1]])

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

> 矩阵乘法

```octave
% Initialize matrix A 
A = [1, 2, 3; 4, 5, 6;7, 8, 9] 

% Initialize vector v 
v = [1; 1; 1] 

% Multiply A * v
Av = A * v
```

---

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


> 单位矩阵

```octave
% Initialize a 2 by 2 identity matrix
I = eye(2)
```

---

```python
# 默认生成的是浮点数，要想生成整数需要特备指定
I1 = numpy.eye(2, dtype=numpy.int)
I2 = numpy.identity(2, dtype=numpy.int)
```

> 逆和转置

```
% Initialize matrix A 
A = [1,2,0;0,5,6;7,0,9]

% Transpose A 
A_trans = A' 

% Take the inverse of A 
A_inv = inv(A)

% What is A^(-1)*A? 
A_invA = inv(A)*A
```

---

```python
# 矩阵的逆用对象的.I返回
# 矩阵的转置使用.T获得
A = numpy.mat([[1,2,0], [0,5,6], [7,0,9]])

B = A.T
C = A.I
print(B)
print(C)
```
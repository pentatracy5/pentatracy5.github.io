---
layout: default
title: 高斯消去法
---

设有线性方程组 $ Ax = b $

$$
\begin{bmatrix}
a_{11} & a_{12} & \cdots & a_{1n} \\
a_{21} & a_{22} & \cdots & a_{2n} \\
\vdots & \vdots &        & \vdots \\
a_{n1} & a_{n2} & \cdots & a_{nn} 
\end{bmatrix}
\begin{bmatrix}
x_1     \\
x_2     \\
\vdots  \\
x_n
\end{bmatrix}
 = 
\begin{bmatrix}
b_1     \\
b_2     \\
\vdots  \\
b_n
\end{bmatrix}
$$

令 $ a_{ij}^{(1)} = a_{ij} (i, j = 1, 2, \cdots, n) $ ，按照公式

$$
\begin{cases}
m_{ik} = a_{ik}^{(k)} / a_{kk}^{(k)}, i = k+1, \cdots, n \\
a_{ij}^{(k+1)} = a_{ij}^{(k)} - m_{ik} a_{kj}^{(k)}, i, j = k+1, \cdots, n \\
b_{i}^{(k+1)} = b_{i}^{(k)} - m_{ik} b_{k}^{(k)}, i = k+1, \cdots, n
\end{cases} \quad k = 1, 2, \cdots, n-1
$$

进行计算，如果 $ a_{kk}^{(k)} \neq 0 (k = 1, 2, \cdots, n-1) $ ，则可得与原方程组等价的简单方程组 $ A^{(n)}x = b^{(n)} $

$$
\begin{bmatrix}
a_{11}^{(1)} & a_{12}^{(1)} & \cdots & a_{1n}^{(1)} \\
             & a_{22}^{(2)} & \cdots & a_{2n}^{(2)} \\
             &              & \ddots & \vdots       \\
             &              &        & a_{nn}^{(n)} 
\end{bmatrix}
\begin{bmatrix}
x_1     \\
x_2     \\
\vdots  \\
x_n
\end{bmatrix}
 = 
\begin{bmatrix}
b_1^{(1)} \\
b_2^{(2)} \\
\vdots    \\
b_n^{(n)}
\end{bmatrix}
$$

该过程称为**消元过程**。

如果 $ a_{nn}^{(n)} \neq 0 $ ，则可根据公式

$$
\begin{cases}
x_n = b_n^{(n)} / a_{nn}^{(n)} \\
x_k = (b_{k}^{(k)} - \sum_{j=k+1}^{n} a_{kj}^{(k)} x_j) / a_{kk}^{(k)}, k = n-1, n-2, \cdots, 1
\end{cases}
$$

求解 $ x $ ，该过程称为**回代过程**。

消元过程和回代过程统称为**高斯消去法**。

* * *

高斯消去法能成功求解 $ x $ 的条件是 $ a_{kk}^{(k)} \neq 0 (k = 1, 2, \cdots, n) $ 。

* * *

定理：$ a_{kk}^{(k)} \neq 0 (k = 1, 2, \cdots, m) $ 的充要条件是 $ A $ 的顺序主子式 $ D_k \neq 0 (k = 1, 2, \cdots, m) $ ，即

$$
D_k = \begin{vmatrix}
a_{11} & \cdots & a_{1k} \\
\vdots &        & \vdots \\
a_{k1} & \cdots & a_{kk} 
\end{vmatrix} \neq 0, k = 1, 2, \cdots, m
$$

证明：利用归纳法证明充分性。

当 $ m=1 $ 时，充分性成立。

现假设充分性对 $ m-1 $ 成立，往证充分性对 $ m $ 成立。设 $ D_k \neq 0 (k = 1, 2, \cdots, m) $ ，由归纳假设有 $ a_{kk}^{(k)} \neq 0 (k = 1, 2, \cdots, m-1) $ ，从而可对 $ A $ 消元得到

$$
\begin{bmatrix}
a_{11}^{(1)} & a_{12}^{(1)} & \cdots & a_{1m}^{(1)} & \cdots & a_{1n}^{(1)} \\
             & a_{22}^{(2)} & \cdots & a_{2m}^{(2)} & \cdots & a_{2n}^{(2)} \\
             &              & \ddots & \vdots       &        & \vdots       \\
             &              &        & a_{mm}^{(m)} & \cdots & a_{mn}^{(m)} \\
             &              &        & \vdots       &        & \vdots       \\
             &              &        & a_{nm}^{(m)} & \cdots & a_{nn}^{(m)} 
\end{bmatrix}
$$

从而有

$$
D_k = \begin{vmatrix}
a_{11}^{(1)} & \cdots & a_{1k}^{(1)} \\
             & \ddots & \vdots       \\
             &        & a_{kk}^{(k)} 
\end{vmatrix} = a_{11}^{(1)} a_{22}^{(2)} \cdots a_{kk}^{(k)} \neq 0, k = 1, 2, \cdots, m
$$

由 $ D_{m-1} \neq 0 $ 以及 $ D_m \neq 0 $ 可知 $a_{mm}^{(m)} \neq 0 $ ，充分性成立。

必要性显然成立。

* * *

推论：如果 $ A $ 的顺序主子式 $ D_k \neq 0 (k = 1, 2, \cdots, n-1) $ ，则

$$
\begin{cases}
a_{11}^{(1)} = D_1 \\
a_{kk}^{(k)} = D_k / D_{k-1}, k = 2, 3, \cdots, n
\end{cases}
$$

* * *

如果遇到 $ a_{kk}^{(k)} = 0 $ ，则高斯消去法会失效。但如果 $ A $ 非奇异，那么在遇到 $ a_{kk}^{(k)} = 0 $ 的情况时，可以保证 $ a_{ik}^{(k)}, i = k+1, \cdots, n $ 中必定有非零元素，从而可以做一次行交换初等变换，使得高斯消去法可以继续进行下去。

* * *

事实上，如果 $ a_{kk}^{(k)} \neq 0 $ 但很小时，用其做除数，会导致其他元素数量级的严重增长和舍入误差的扩散，最后也使得计算解不可靠。

* * *

如果 $ A $ 非奇异，那么可以在第 $ k $ 步消元之前，选取 $ i_k $ ，使其满足

$$
\vert a_{i_k k} \vert = \underset {k \leqslant i \leqslant n} {\max} \vert a_{ik} \vert \neq 0
$$

交换第 $ k $ 行和第 $ i_k $ 行的元素，再进行消元计算，这种算法称为**列主元消去法**。

* * *

如果 $ A $ 非奇异，那么可以在第 $ k $ 步消元之前，选取 $ i_k, j_k $ ，使其满足

$$
\vert a_{i_k j_k} \vert = \underset {k \leqslant i, j \leqslant n} {\max} \vert a_{ij} \vert \neq 0
$$

交换第 $ k $ 行和第 $ i_k $ 行的元素，然后再交换第 $ k $ 行和第 $ j_k $ 行的元素，再进行消元计算，这种算法称为**全主元消去法**。注意，全主元消去法的自变量顺序会变化。

* * *

[上一级](./../index.html)

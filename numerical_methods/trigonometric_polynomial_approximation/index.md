---
layout: default
title: 三角多项式逼近
---

设 $ f(x) $ 是以 $ 2\pi $ 为周期的平方可积函数，用三角多项式

$$
S_n(x) = \frac {a_0} {2} + a_1 \cos x + b_1 \sin x + \cdots + a_n \cos nx + b_n \sin nx
$$

做最佳平方逼近函数。由于三角函数族

$$
1, \cos x, \sin x, \cdots, \cos kx, \sin kx, \cdots
$$

在 $ [0, 2\pi] $ 上是正交函数族，于是 $ f(x) $ 在 $ [0, 2\pi] $ 上的最佳平方三角逼近多项式 $ S_n(x) $ 的系数是

$$
\begin{cases}
a_k = \frac {1} {\pi} \int_0^{2\pi} f(x) \cos kx dx, k = 0, 1, \cdots, n \\
b_k = \frac {1} {\pi} \int_0^{2\pi} f(x) \sin kx dx, k = 1, 2, \cdots, n 
\end{cases}
$$

$ a_k, b_k $ 称为傅里叶系数，函数 $ f(x) $ 按傅里叶系数展开得到的级数

$$
\frac {a_0} {2} + \sum_{k=1}^{\infty} (a_k \cos kx + b_k \sin kx)
$$

就称为**傅里叶级数**。

* * *

只要 $ f'(x) $ 在 $ [0, 2\pi] $ 上分段连续，则傅里叶级数一致收敛到 $ f(x) $ 。

* * *

根据最佳平方逼近的贝塞尔不等式可得

$$
\frac {a_0^2} {2} + \sum_{k=1}^{n} (a_k^2 + b_k^2) \leqslant \frac {1} {\pi} \int_0^{2\pi} [f(x)]^2 dx
$$

由于右边不依赖于 $ n $ ，左边单调有界，所以级数 $ \frac {a_0^2} {2} + \sum_{k=1}^{\infty} (a_k^2 + b_k^2) $ 收敛，并且有

$$
\lim\limits_{k \rightarrow \infty} a_k = \lim\limits_{k \rightarrow \infty} b_k = 0
$$

* * *

$ 1, \cos x, \sin x, \cdots, \cos mx, \sin mx $ 在离散点集 $ \lbrace x_j = \frac {2\pi j} {2m + 1}, j = 0, 1, \cdots, 2m \rbrace $ 上正交。

证明：先证对任意 $ n $ 和任意 $ 1 \leq k \leq n-1 $ 有

$$
\sum_{j=0}^{n-1} \sin k \frac {2\pi j} {n} = \sum_{j=0}^{n-1} \cos k \frac {2\pi j} {n} = 0
$$

显然

$$
\begin{aligned}
\sum_{j=0}^{n-1} \sin k \frac {2\pi j} {n} &= \sum_{j=1}^{\lfloor \frac {n-1} {2} \rfloor} \sin k \frac {2\pi j} {n} + \sum_{j=\lceil \frac {n-1} {2} \rceil}^{n-1} \sin k \frac {2\pi j} {n} \\
&= \sum_{j=1}^{\lfloor \frac {n-1} {2} \rfloor} (\sin k \frac {2\pi j} {n} + \sin k \frac {2\pi (n-j)} {n}) \\
&= \sum_{j=1}^{\lfloor \frac {n-1} {2} \rfloor} (\sin k \frac {2\pi j} {n} - \sin k \frac {2\pi (j-n)} {n}) \\
&= \sum_{j=1}^{\lfloor \frac {n-1} {2} \rfloor} (\sin k \frac {2\pi j} {n} - \sin k \frac {2\pi j} {n}) \\
&= 0
\end{aligned}
$$

又

$$
\begin{aligned}
\sum_{j=0}^{n-1} \cos k \frac {2\pi j} {n} &= \sum_{j=1}^{n} \cos k \frac {2\pi j} {n} \\
&= \sum_{j=0}^{n-1} \cos (k \frac {2\pi j} {n} + k \frac {2\pi} {n}) \\
&= \sum_{j=0}^{n-1} (\cos k \frac {2\pi j} {n} \cos k \frac {2\pi} {n} - \sin k \frac {2\pi j} {n} \sin k \frac {2\pi} {n}) \\
&= \cos k \frac {2\pi} {n} \sum_{j=0}^{n-1} \cos k \frac {2\pi j} {n} - \sin k \frac {2\pi} {n} \sum_{j=0}^{n-1} \sin k \frac {2\pi j} {n} \\
&= \cos k \frac {2\pi} {n} \sum_{j=0}^{n-1} \cos k \frac {2\pi j} {n}
\end{aligned}
$$

从而

$$
(1 - \cos k \frac {2\pi} {n}) \sum_{j=0}^{n-1} \cos k \frac {2\pi j} {n} = 0
$$

因为 $ 1 \leq k \leq n-1 $ ，故 $ 1 - \cos k \frac {2\pi} {n} \neq 0 $ ，从而

$$
\sum_{j=0}^{n-1} \cos k \frac {2\pi j} {n} = 0
$$

下面考虑三种情况

$$
\sum_{j=0}^{2m} \cos k \frac {2\pi j} {2m+1} \cos l \frac {2\pi j} {2m+1}, k, l = 0, 1, \cdots, m \\
\sum_{j=0}^{2m} \sin k \frac {2\pi j} {2m+1} \sin l \frac {2\pi j} {2m+1}, k, l = 1, 2, \cdots, m \\
\sum_{j=0}^{2m} \cos k \frac {2\pi j} {2m+1} \sin l \frac {2\pi j} {2m+1}, k = 0, 1, \cdots, m, l = 1, 2, \cdots, m \\
$$

对第一种有

$$
\sum_{j=0}^{2m} \cos k \frac {2\pi j} {2m+1} \cos l \frac {2\pi j} {2m+1} = \frac {1} {2} \sum_{j=0}^{2m} \cos (k+l) \frac {2\pi j} {2m+1} + \frac {1} {2} \sum_{j=0}^{2m} \cos (k-l) \frac {2\pi j} {2m+1}
$$

显然

$$
\sum_{j=0}^{2m} \cos k \frac {2\pi j} {2m+1} \cos l \frac {2\pi j} {2m+1} = \begin{cases}
0, k \neq l \\
\frac {2m+1} {2}, k = l \neq 0 \\
2m+1, k = l = 0
\end{cases}
$$

对第二种有

$$
\sum_{j=0}^{2m} \sin k \frac {2\pi j} {2m+1} \sin l \frac {2\pi j} {2m+1} = \frac {1} {2} \sum_{j=0}^{2m} \cos (k-l) \frac {2\pi j} {2m+1} - \frac {1} {2} \sum_{j=0}^{2m} \cos (k+l) \frac {2\pi j} {2m+1}
$$

显然

$$
\sum_{j=0}^{2m} \sin k \frac {2\pi j} {2m+1} \sin l \frac {2\pi j} {2m+1} = \begin{cases}
0, k \neq l \\
\frac {2m+1} {2}, k = l
\end{cases}
$$

对于第三种有

$$
\sum_{j=0}^{2m} \cos k \frac {2\pi j} {2m+1} \sin l \frac {2\pi j} {2m+1} = \frac {1} {2} \sum_{j=0}^{2m} \sin (k+l) \frac {2\pi j} {2m+1} - \frac {1} {2} \sum_{j=0}^{2m} \sin (k-l) \frac {2\pi j} {2m+1} = 0
$$

从而正交性成立。

* * *

若令 $ f_j = f(x_j)(j = 0, 1, \cdots, 2m) $ ，则 $ f(x) $ 的最小二乘三角逼近为

$$
S_n(x) = \frac {a_0} {2} + \sum_{k=1}^{n} (a_k \cos kx + b_k \sin kx), n \leqslant m
$$

其中

$$
a_k = \frac {2} {2m+1} \sum_{j=0}^{2m} f_j \cos k \frac {2\pi j} {2m+1}, k = 0, 1, \cdots, n \\
b_k = \frac {2} {2m+1} \sum_{j=0}^{2m} f_j \sin k \frac {2\pi j} {2m+1}, k = 1, 2, \cdots, n
$$

* * *

$ S_m(x) $ 是 $ f(x) $ 的三角插值多项式，即 $ \forall i, S_m(x_i) = f_i $ 。

证明：

$$
\begin{aligned}
S_m(x_i) &= \frac {a_0} {2} + \sum_{k=1}^{m} (a_k \cos kx_i + b_k \sin kx_i) \\ 
&= \frac {2} {2m+1} \sum_{j=0}^{2m} f_j \frac {1} {2} + \frac {2} {2m+1} \sum_{k=1}^{m} \sum_{j=0}^{2m} f_j (\cos kx_j \cos kx_i + \sin kx_j \sin kx_i) \\
&= \frac {2} {2m+1} \sum_{j=0}^{2m} f_j \Big[ \frac {1} {2} + \sum_{k=1}^{m} (\cos (j-i) \frac {2\pi k} {2m+1}) \Big]
\end{aligned}
$$

当 $ j=i $ 时， $ \cos (j-i) \frac {2\pi k} {2m+1} = 1 $ ；当 $ j \neq i $ 时，由之前的结论可知

$$
\sum_{k=0}^{2m} (\cos (j-i) \frac {2\pi k} {2m+1}) = 0 \\
\sum_{k=1}^{2m} (\cos (j-i) \frac {2\pi k} {2m+1}) = -1
$$

再由对称性可知

$$
\sum_{k=1}^{m} (\cos (j-i) \frac {2\pi k} {2m+1}) = -\frac {1} {2}
$$

从而

$$
S_m(x_i) = \frac {2} {2m+1} f_i (\frac {1} {2} + m) = f_i
$$

* * *

[上一级](./../index.html)

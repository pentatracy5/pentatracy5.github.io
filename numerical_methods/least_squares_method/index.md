---
layout: default
title: 最小二乘法
---

具有一般性的最小二乘问题提法：设 $ f(x) \in C[a, b] $ ， $ f(x) $ 只在一组离散点集 $ \lbrace x_i, i = 0, 1, ... , m \rbrace $ 上给出， $ y_i = f(x_i) $ ， $ \varphi_0(x), \varphi_1(x), ... , \varphi_n(x) (n \leqslant m) $ 是 $ C[a, b] $ 上线性无关的函数族， $ \varphi = span \lbrace \varphi_0(x), \varphi_1(x), ... , \varphi_n(x) \rbrace $ ， $ \omega(x) $ 是 $ [a, b] $ 上的权函数。在 $ \varphi $ 中找一个函数 $ S^* (x) $ ，使得

$$
\sum_{i=0}^m \omega(x_i) \Big[ S^* (x_i) - y_i \Big]^2 = \underset {S(x) \in \varphi} {\min} \sum_{i=0}^m \omega(x_i) \Big[ S(x_i) - y_i \Big]^2
$$

其中 $ S(x) $ 可表示为

$$
S(x) = a_0 \varphi_0(x) + a_1 \varphi_1(x) + ... + a_n \varphi_n(x) 
$$

* * *

最小二乘问题可转化为求多元函数

$$
I(a_0, a_1, ... , a_n) = \sum_{i=0}^m \omega(x_i) \Big[ \sum_{j=0}^n a_j \varphi_j(x_i) - y_i \Big]^2
$$

由求多元函数极值的必要条件有

$$
\frac {\partial I} {\partial a_k} = 2 \sum_{i=0}^m \omega(x_i) \Big[ \sum_{j=0}^n a_j \varphi_j(x_i) - y_i \Big] \varphi_k(x_i) = 0, k = 0, 1, ... , n
$$

若记

$$
(\varphi_j, \varphi_k) = \sum_{i=0}^m \omega(x_i) \varphi_j(x_i) \varphi_k(x_i) \\
(f, \varphi_k) = \sum_{i=0}^m \omega(x_i) f(x_i) \varphi_k(x_i) \equiv d_k, k = 0, 1, ... , n
$$

则有

$$
\sum_{j=0}^n (\varphi_j, \varphi_k) a_j = d_k, k = 0, 1, ... , n
$$

称为**法方程**，可将其写为矩阵形式

$$
Ga = d
$$

其中

$$
a = (a_0, a_1, ... , a_n)^T \\
d = (d_0, d_1, ... , d_n)^T \\
G = \begin{bmatrix}
(\varphi_0, \varphi_0)  & (\varphi_0, \varphi_1)    & \cdots    & (\varphi_0, \varphi_n)    \\
(\varphi_1, \varphi_0)  & (\varphi_1, \varphi_1)    & \cdots    & (\varphi_1, \varphi_n)    \\
\vdots                  & \vdots                    &           & \vdots                    \\
(\varphi_n, \varphi_0)  & (\varphi_n, \varphi_1)    & \cdots    & (\varphi_n, \varphi_n)
\end{bmatrix}
$$

要使法方程有唯一解，就要求矩阵 $ G $ 非奇异。必须指出， $ \varphi_0(x), \varphi_1(x), ... , \varphi_n(x) $ 线性无关不能推出 $ G $ 非奇异。

* * *

定义：设 $ \varphi_0(x), \varphi_1(x), ... , \varphi_n(x) \in C[a, b] $ 的任意线性组合在点集 $ \lbrace x_i, i = 0, 1, ... , m \rbrace (n \leqslant m) $ 上至多只有 $ n $ 个不同的零点，则称 $ \varphi_0(x), \varphi_1(x), ... , \varphi_n(x) $ 在点集 $ \lbrace x_i, i = 0, 1, ... , m \rbrace $ 上满足**哈尔条件**。

* * *

显然 $ 1, x, ... , x^n $ 在任意 $ m (n \leqslant m) $ 个点上满足哈尔条件。

* * *

定理：如果 $ \varphi_0(x), \varphi_1(x), ... , \varphi_n(x) \in C[a, b] $ 在 $ \lbrace x_i, i = 0, 1, ... , m \rbrace $ 上满足哈尔条件，则法方程的系数矩阵非奇异，从而法方程存在唯一解。

证明：由于 $ \varphi_0(x), \varphi_1(x), ... , \varphi_n(x) \in C[a, b] $ 在 $ \lbrace x_i, i = 0, 1, ... , m \rbrace $ 上满足哈尔条件，因此任取 $ \lbrace x_i, i = 0, 1, ... , m \rbrace $ 中的 $ n+1 $ 个点（不妨记为 $ x_0, x_1, ... , x_n $ ）都有

$$
\begin{bmatrix}
\varphi_0(x_0)  & \varphi_1(x_0)    & \cdots    & \varphi_n(x_0)    \\
\varphi_0(x_1)  & \varphi_1(x_1)    & \cdots    & \varphi_n(x_1)    \\
\vdots          & \vdots            &           & \vdots            \\
\varphi_0(x_n)  & \varphi_1(x_n)    & \cdots    & \varphi_n(x_n)
\end{bmatrix}
$$

的行列式不为 $ 0 $ ，从而

$$
\begin{bmatrix}
\varphi_0(x_0)  & \varphi_1(x_0)    & \cdots    & \varphi_n(x_0)    \\
\varphi_0(x_1)  & \varphi_1(x_1)    & \cdots    & \varphi_n(x_1)    \\
\vdots          & \vdots            &           & \vdots            \\
\varphi_0(x_m)  & \varphi_1(x_m)    & \cdots    & \varphi_n(x_m)
\end{bmatrix}
$$

满秩，进而

$$
G = \begin{bmatrix}
\varphi_0(x_0)  & \varphi_0(x_1)    & \cdots    & \varphi_0(x_m)    \\
\varphi_1(x_0)  & \varphi_1(x_1)    & \cdots    & \varphi_1(x_m)    \\
\vdots          & \vdots            &           & \vdots            \\
\varphi_n(x_0)  & \varphi_n(x_1)    & \cdots    & \varphi_n(x_m)
\end{bmatrix}
\begin{bmatrix}
\omega(x_0) &               &           &               \\
            & \omega(x_1)   &           &               \\
            &               & \ddots    &               \\
            &               &           & \omega(x_m)
\end{bmatrix}
\begin{bmatrix}
\varphi_0(x_0)  & \varphi_1(x_0)    & \cdots    & \varphi_n(x_0)    \\
\varphi_0(x_1)  & \varphi_1(x_1)    & \cdots    & \varphi_n(x_1)    \\
\vdots          & \vdots            &           & \vdots            \\
\varphi_0(x_m)  & \varphi_1(x_m)    & \cdots    & \varphi_n(x_m)
\end{bmatrix}
$$
\vdots          & \vdots            &           & \vdots            \\
\varphi_0(x_m)  & \varphi_1(x_m)    & \cdots    & \varphi_n(x_m)
\end{bmatrix}
$$

也是满秩的，故 $ G $ 非奇异。

* * *

若法方程存在唯一解 $ a_k = a_k^* , k = 0, 1, ... , n $ ，则对

$$
S^*(x) = a_0^* \varphi_0(x) + a_1^* \varphi_1(x) + ... + a_n^* \varphi_n(x)
$$

有

$$
\sum_{i=0}^m \omega(x_i) \Big[ S^* (x_i) - y_i \Big]^2 = \underset {S(x) \in \varphi} {\min} \sum_{i=0}^m \omega(x_i) \Big[ S(x_i) - y_i \Big]^2
$$

证明：

* * *

当 $ \varphi = span \lbrace 1, x, ... , x^n \rbrace $ ， $ n \geqslant 3 $ 时， $ G $ 可能变得病态，这种情况下解法方程得到最小二乘解的方法不可取。

* * *

通常对于 $ n=1 $ 的简单情形都可通过求法方程的方法得到 $ S^*(x) $ ，这种情形可得到线性回归的计算公式

$$

$$

* * *

[上一级](./../index.html)

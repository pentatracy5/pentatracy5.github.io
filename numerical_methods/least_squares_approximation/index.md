---
layout: default
title: 最佳平方逼近
---

定义：对 $ f(x) \in C[a, b] $ 及 $ C[a, b] $ 中的一个子集 $ \varphi = span \lbrace \varphi_0(x), \varphi_1(x), ... , \varphi_n(x) \rbrace $ ，若存在 $ S^* (x) \in \varphi $ ，使

$$
\Vert f(x) - S^* (x) \Vert_2^2 = \underset {S(x) \in \varphi} {\min} \Vert f(x) - S(x) \Vert_2^2 = \underset {S(x) \in \varphi} {\min} \int_a^b \rho(x) [f(x) - S(x)]^2 dx
$$

则称 $ S^* (x) $ 是 $ f(x) $ 在子集 $ \varphi \subseteq C[a, b] $ 中的**最佳平方逼近函数**。

* * *

定理：对 $ f(x) \in C[a, b] $ 及 $ C[a, b] $ 中的一个子集 $ \varphi = span \lbrace \varphi_0(x), \varphi_1(x), ... , \varphi_n(x) \rbrace $ ，**最佳平方逼近函数** $ S^* (x) \in \varphi $ 存在且唯一。

证明：若记

$$
S(x) = a_0 \varphi_0(x) + a_1 \varphi_1(x) + ... + a_n \varphi_n(x)
$$

则求 $ S^* (x) $ 等价于求多元函数

$$
I(a_0, a_1, ... , a_n) = \Vert S(x) - f(x) \Vert_2^2 = \int_a^b \rho(x) [\sum_{j=0}^n a_j \varphi_j(x) - f(x)]^2 dx
$$

的最小值。利用多元函数求极值的必要条件有

$$
\frac {\partial I} {\partial a_k} = 2 \int_a^b \rho(x) [\sum_{j=0}^n a_j \varphi_j(x) - f(x)] \varphi_k(x) dx = 0, k = 0, 1, ... , n
$$

于是

$$
\sum_{j=0}^n (\varphi_k(x), \varphi_j(x)) a_j = (f(x), \varphi_k(x)), k = 0, 1, ... , n
$$

这是关于 $ a_0, a_1, ... , a_n $ 的线性方程组，称为**法方程**，由于 $ \varphi_0(x), \varphi_1(x), ... , \varphi_n(x) $ 线性无关，故系数 $ detG(\varphi_0(x), \varphi_1(x), ... , \varphi_n(x)) \neq 0 $ ，于是有唯一解 $ a_k = a_k^* (k = 0, 1, ... , n) $ 。

若记

$$
S^* (x) = a_0^* \varphi_0(x) + a_1^* \varphi_1(x) + ... + a_n^* \varphi_n(x)
$$

再证明 $ I(a_0, a_1, ... , a_n) $ 在 $ S^* (x) $ 处取最小值。对任何 $ S(x) \in \varphi $ ，有

$$
\begin{aligned}
D &= \int_a^b \rho(x) [f(x) - S(x)]^2 dx - \int_a^b \rho(x) [f(x) - S^* (x)]^2 dx \\
&= \int_a^b \rho(x) [S(x) - S^* (x)]^2 dx + 2 \int_a^b \rho(x) [S^* (x) - S(x)] [f(x) - S^* (x)] dx
\end{aligned}
$$

由于 $ S^* (x) $ 的系数是法方程的解，故

$$
\int_a^b \rho(x) [f(x) - S^* (x)] \varphi_k(x) dx = 0, k = 0, 1, ... , n
$$

从而

$$
D = \int_a^b \rho(x) [S(x) - S^* (x)]^2 dx \geqslant 0
$$

并且由权函数的定义可知当且仅当 $ S(x) = S^* (x) $ 时等号成立，综上存在唯一性得证。

* * *

若令 $ \delta(x) = f(x) - S^* (x) $ ，则最佳平方逼近的误差为

$$
\begin{aligned}
\Vert \delta(x) \Vert_2^2 &= (f(x) - S^* (x), f(x) - S^* (x)) \\
&= (f(x), f(x)) - (S^* (x), f(x)) \\
&= (f(x), f(x)) - \sum_{k=0}^n a_k^* (\varphi_k(x), f(x))
\end{aligned}
$$

* * *

若取 $ \varphi_k(x) = x^k $ ， $ \rho(x) \equiv 1 $ ， $ f(x) \in C[0, 1] $ ，则有

$$
(\varphi_j(x), \varphi_k(x)) = \int_0^1 x^{k+j} dx = \frac {1} {k+j+1} \\
(f(x), \varphi_k(x)) = \int_0^1 f(x) x^k dx \equiv d_k
$$

记 $ G(1, x, ... , x^n) = G_n = H_n $ ，则

$$
H_n = \begin{bmatrix}
1               & \frac {1} {2}     & \cdots    & \frac {1} {n+1} \\
\frac {1} {2}   & \frac {1} {3}     & \cdots    & \frac {1} {n+2} \\
\vdots          & \vdots            &           & \vdots \\
\frac {1} {n+1} & \frac {1} {n+2}   & \cdots    & \frac {1} {2n+1} \\
\end{bmatrix}
$$

称 $ H_n $ 为**希尔伯特矩阵**。

该条件下的最佳平方逼近函数即为最佳平方逼近多项式。

* * *

对 $ f(x) \in C[a, b] $ 及 $ C[a, b] $ 中的一个子集 $ \varphi = span \lbrace \varphi_0(x), \varphi_1(x), ... , \varphi_n(x) \rbrace $ ，若 $ \varphi_0(x), \varphi_1(x), ... , \varphi_n(x) $ 是正交函数族，则法方程系数矩阵为为非奇异对角阵，且解为

$$
a_k^* = \frac {(f(x), \varphi_k(x))} {(\varphi_k(x), \varphi_k(x))}, k = 0, 1, ... , n
$$

于是 $ f(x) $ 在 $ \varphi $ 中的最佳平方逼近函数为

$$
S^* (x) = \sum_{k=0}^n \frac {(f(x), \varphi_k(x))} {(\varphi_k(x), \varphi_k(x))} \varphi_k(x)
$$

平方逼近误差为

$$
\Vert \delta_n(x) \Vert_2^2 = \Vert f(x) \Vert_2^2 - \sum_{k=0}^n (a_k^* \Vert \varphi_k(x) \Vert_2)^2
$$

由此可得**贝塞尔不等式**

$$
\Vert f(x) \Vert_2^2 \geqslant \sum_{k=0}^n (a_k^* \Vert \varphi_k(x) \Vert_2)^2
$$

* * *

定义：若 $ f(x) \in C[a, b] $ 按正交函数族 $ \lbrace \varphi_k(x), k = 0, 1, ... \rbrace $ 展开得级数

$$
\sum_{k=0}^{\infty} a_k^* \varphi_k(x) \\
a_k^* = \frac {(f(x), \varphi_k(x))} {(\varphi_k(x), \varphi_k(x))}
$$

称其为 $ f(x) $ 的**广义傅里叶级数**，系数 $ a_k^* $ 称为**广义傅里叶系数**，它是傅里叶级数得直接推广。

* * *

定理：设 $ f(x) \in C[a, b] $ ， $ S_n^* (x) $ 是 $ n $ 次最佳平方逼近多项式，则有

$$
\lim\limits_{n \rightarrow \infty} \Vert f(x) - S_n^* (x) \Vert_2 = 0
$$

证明：？？？（《多项式最佳逼近的实现》中有证明过程）

* * *

上述定理说明了 $ f(x) $ 按照正交多项式族展开的广义傅里叶级数收敛到 $ f(x) $ 。

* * *

定理：设 $ f(x) \in C^2[-1, 1] $ ， $ S_n^* (x) $ 是 $ n $ 次最佳平方逼近多项式，则有 $ \forall \epsilon > 0 $ ， $ \exists n_0 > 0 $ ， 使得对 $ \forall x \in [-1, 1] $ ， $ \forall n > n_0 $

$$
\vert f(x) - S_n^*(x) \vert \leqslant \frac {\epsilon} {\sqrt{n}}
$$

证明：？？？（《多项式最佳逼近的实现》中有证明过程）

* * *

上述定理说明了，当 $ f(x) $ 满足光滑性条件时， $ S_n^* (x) $ 一致收敛于 $ f(x) $ ，只不过对于不同的定义域， $ \vert f(x) - S_n^*(x) \vert $ 的上限不再是 $ \frac {\epsilon} {\sqrt{n}} $ 。

* * *

考虑 $ f(x) \in C[-1, 1] $ ，按勒让德多项式展开有

$$
S_n^* (x) = a_0^* P_0(x) + a_1^* P_1(x) + ... + a_n^* P_n(x) \\
a_k^* = \frac {(f(x), P_k(x))} {(P_k(x), P_k(x))} = \frac {2k+1} {2} \int_{-1}^1 f(x) P_k(x) dx
$$

平方逼近的误差为

$$
\Vert \delta_n(x) \Vert_2^2 = \int_{-1}^1 f^2(x) dx - \sum_{k=0}^n \frac {2} {2k+1} { a_k^* }^2
$$

* * *

如果 $ f(x) \in C[a, b] $ ，可做变换

$$
x = \frac {b-a} {2} t + \frac {b+a} {2}, (-1 \leqslant t \leqslant 1)
$$

于是 $ F(t) = f(\frac {b-a} {2} t + \frac {b+a} {2}) \in C[-1, 1] $ ，可用勒让德多项式做最佳平方逼近多项式 $ S_n^* (t) $ ，从而得到区间 $ [a, b] $ 上的最佳平方逼近多项式 $ S_n^* (\frac {2x-a-b} {b-a}) $ 。

* * *

由最佳平方逼近多项式的唯一性可知，利用函数的勒让德展开部分和的方法与直接解以 $ H $ 为系数矩阵的法方程的方法的结果是一致的，然而当 $ n $ 比较大的时候， $ H_n $ 高度病态，因此直接求解法方程相当困难，而前者不用解线性方程组，不存在病态问题，且计算公式简单，因此通常用这种方法求最佳平方逼近多项式。

* * *

定理：在所有首 $ 1 $ 的 $ n $ 次多项式中，勒让德多项式 $ \widetilde{P_n}(x) $ 在 $ [-1, 1] $ 上与零的平方逼近误差最小。

证明：设 $ Q_n(x) $ 是任意一个首 $ 1 $ 的 $ n $ 次多项式，它可以表示为

$$
Q_n(x) = \widetilde{P_n}(x) + \sum_{k=0}^{n-1} a_k \widetilde{P_k}(x)
$$

于是

$$
\begin{aligned}
\Vert Q_n(x) \Vert_2^2 &= (Q_n(x), Q_n(x)) \\
&= \int_{-1}^1 Q_n^2(x) dx \\
&= (\widetilde{P_n}(x), \widetilde{P_n}(x)) + \sum_{k=0}^{n-1} a_k^2 (\widetilde{P_k}(x), \widetilde{P_k}(x)) \\
&\geqslant (\widetilde{P_n}(x), \widetilde{P_n}(x)) \\
&= \Vert \widetilde{P_n}(x) \Vert_2^2
\end{aligned}
$$

当且仅当 $ a_0 = a_1 = ... = a_n = 0 $ 时等号才成立，即当 $ Q_n(x) \equiv \widetilde{P_n}(x) $ 时平方逼近误差最小。

* * *

[上一级](./../index.html)

---
layout: default
title: 函数逼近
---

定义：设集合 $ S $ 是数域 $ P $ 上的线性空间，元素 $ x_1, x_2, ... , x_n \in S $ ，如果存在不全为零的数 $ \alpha_1, \alpha_2, ... , \alpha_n \in P $ ，使得

$$
\alpha_1 x_1 + \alpha_2 x_2 + ... + \alpha_n x_n = 0
$$

则称 $ x_1, x_2, ... , x_n $ **线性相关**，否则称 $ x_1, x_2, ... , x_n $ **线性相关**。

若线性空间 $ S $ 是由 $ n $ 个线性无关元素 $ x_1, x_2, ... , x_n $ 生成的，即 $ \forall x \in S, \exists \alpha_1, \alpha_2, ... , \alpha_n \in P $ ，使得

$$
x = \alpha_1 x_1 + \alpha_2 x_2 + ... + \alpha_n x_n
$$

则 $ x_1, x_2, ... , x_n $ 称为空间 $ S $ 的一组基，记为 $ S = span \lbrace x_1, x_2, ... , x_n \rbrace $ ，并称空间 $ S $ 为 $ n $ **维空间**，系数 $ \alpha_1, \alpha_2, ... , \alpha_n $ 称为 $ x $ 在基 $ x_1, x_2, ... , x_n $ 下的**坐标**，记做 $ (\alpha_1, \alpha_2, ... , \alpha_n) $ ，如果 $ S $ 中有无限个线性无关元素 $ x_1, x_2, ... , x_n, ... $ ，则称 $ S $ 为**无限维线性空间**。

* * *

考虑次数不超过 $ n $ 次的多项式集合 $ H_n $ ，其元素 $ p(x) $ 表示为

$$
p(x) = a_0 + a_1 x + ... + a_n x^n
$$

它由 $ n+1 $ 个系数 $ (a_0, a_1, ... , a_n) $ 唯一确定。 $ 1, x, ... , x^n $ 线性无关，故而是 $ H_n $ 的一组基，有 $ H_n = span \lbrace 1, x, ... , x^n \rbrace $ ，且 $ (a_0, a_1, ... , a_n) $ 是 $ p(x) $ 的坐标向量， $ H_n $ 是 $ n+1 $ 维的。

* * *

考虑连续函数 $ f(x) \in C[a, b] $ ，它不能用有限个线性无关的函数表示，故 $ C[a, b] $ 是无限维的。

* * *

定义：设 $ S $ 为线性空间， $ x \in S $ ，若存在唯一实数 $ \Vert \cdot \Vert $ ，满足条件：

（1） $ \Vert x \Vert \geqslant 0 $ ，当且仅当 $ x = 0 $ 时， $ \Vert x \Vert = 0 $ （正定性）

（2） $ \Vert \alpha x \Vert = \vert \alpha \vert \Vert x \Vert, \alpha \in \mathbb{R} $ （齐次性）

（3） $ \Vert x + y \Vert \leqslant \Vert x \Vert + \Vert y \Vert, x, y \in S $ （三角不等式性）

则称 $ \Vert \cdot \Vert $ 为线性空间 $ S $ 上的**范数**， $ S $ 与 $ \Vert \cdot \Vert $ 一起称为**赋范线性空间**，记为 $ X $ 。

* * *

对于在 $ \mathbb{R}^n $ 上的向量 $ \pmb{x} = (x_1, x_2, ... , x_n)^T \in \mathbb{R}^n $ ，有三种常用范数：

（1） $ \Vert \pmb{x} \Vert_{\infty} = \underset {1 \leqslant i \leqslant n} {\max} \vert x_i \vert $ ，称为 $ \infty $ -范数或最大范数

（2） $ \Vert \pmb{x} \Vert_1 = \sum_{i=1}^n \vert x_i \vert $ ，称为 $ 1 $ -范数

（3） $ \Vert \pmb{x} \Vert_2 = (\sum_{i=1}^n x_i^2)^{\frac {1} {2}} $ ，称为 $ 2 $ -范数

* * *

对于连续函数空间 $ C[a, b] $ ，若 $ f \in C[a, b] $ ，可定义三种常用范数：

（1） $ \Vert f \Vert_{\infty} = \underset {a \leqslant x \leqslant b} {\max} \vert f(x) \vert $ ，称为 $ \infty $ -范数

（2） $ \Vert f \Vert_1 = \int_a^b \vert f(x) \vert dx $ ，称为 $ 1 $ -范数

（3） $ \Vert f \Vert_2 = (\int_a^b f^2(x) dx)^{\frac {1} {2}} $ ，称为 $ 2 $ -范数

* * *

定义：设 $ X $ 是数域 $ K $ 上的线性空间，对 $ \forall u, v \in X $ ，有 $ K $ 中的一个数与之相对应，记为 $ (u, v) $ ，它满足条件：

（1） $ (u, v) = \overline{ (v, u) } \quad u, v \in X $ （ $ \overline{ (v, u) } $ 称为 $ (v, u) $ 的共轭）

（2） $ (\alpha u, v) = \alpha (u, v) \quad \alpha \in K \quad u, v \in X $ 

（3） $ (u + v, w) = (u, w) + (v, w) \quad u, v, w \in X $ 

（4） $ (u, u) \geqslant 0 $ ，当且仅当 $ u = 0 $ 时， $ (u, u) = 0 $ 

则称 $ (u, v) $ 为 $ X $ 上 $ u $ 与 $ v $ 的**内积**。定义了内积的线性空间称为**内积空间**。如果 $ (u, v) = 0 $ ，则称 $ u $ 与 $ v $ **正交**。

* * *

定理：设 $ X $ 为一个内积空间，对 $ \forall u, v \in X $ ，有

$$
(u, v)^2 \leqslant (u, u) (v, v)
$$

称其为**柯西-施瓦茨不等式**。

证明：当 $ v = 0 $ 时，不等式显然成立。

现设 $ v \neq 0 $ ，则 $ (v, v) > 0 $ ，且对任何数 $ \lambda $ 有

$$
0 \leqslant (u + \lambda v, u + \lambda v) = (u, u) + 2 \lambda (u, v) + \lambda^2 (v, v)
$$

取 $ \lambda = - \frac {(u, v)} {(v, v)} $ ，代入上式右端，得

$$
0 \leqslant (u, u) - \frac {(u, v)^2} {(v, v)}
$$

得证。

* * *

定理：设 $ X $ 为一个内积空间， $ u_1, u_2, ... , u_n \in X $ ，矩阵

$$
G = \begin{bmatrix}
(u_1, u_1)  & (u_2, u_1)    & \cdots    & (u_n, u_1)    \\
(u_1, u_2)  & (u_2, u_2)    & \cdots    & (u_n, u_2)    \\
\vdots      & \vdots        &           & \vdots        \\
(u_1, u_n)  & (u_2, u_n)    & \cdots    & (u_n, u_n)
\end{bmatrix}
$$

称为格拉姆矩阵。矩阵 $ G $ 非奇异的充分必要条件是 $ u_1, u_2, ... , u_n $ 线性无关。

证明：考虑关于 $ \alpha_1, \alpha_2, ... , \alpha_n $ 的以 $ G $ 为系数矩阵的齐次线性方程组 

$$
\sum_{j=1}^n (u_j, u_k) \alpha_j = 0(k = 1, 2, ... , n) \tag{1}
$$

该方程的解也是方程

$$
(\sum_{j=1}^n a_j u_j, \sum_{j=1}^n a_j u_j) = 0 \tag{2}
$$

的解，从而也是

$$
\sum_{j=1}^n a_j u_j = 0 \tag{3}
$$

的解，而 $ (3) $ 的解又显然是 $ (1) $ 的解。因此

$ G $ 非奇异 $ \iff (1) $ 只有零解 $ \iff (2) $ 只有零解 $ \iff (3) $ 只有零解 $ \iff u_1, u_2, ... , u_n $ 线性无关。

* * *

在内积空间 $ X $ 上可以由内积诱导出一种范数，即对 $ u \in X $ ，记

$$
\Vert u \Vert = \sqrt{(u, u)}
$$

容易验证其满足范数的定义。

* * *

定义：若给定实数 $ \omega_i > 0 (i = 1, 2, ... , n) $ ，称 $ \lbrace \omega_i \rbrace $ 为**权系数**，则在 $ \mathbb{R}^n $ 上可定义**加权内积**为

$$
(\pmb{x}, \pmb{y}) = \sum_{i=1}^n \omega_i x_i y_i
$$

其中 $ \pmb{x}, \pmb{y} \in \mathbb{R}^n, \pmb{x} = (x_1, x_2, ... , x_n)^T, \pmb{y} = (y_1, y_2, ... , y_n)^T $ 。

* * *

定义：设 $ [a, b] $ 是有限或无限区间，在 $ [a, b] $ 上的非负函数 $ \rho(x) $ 满足条件：

(1) $ \int_a^b x^k \rho(x) dx $ 存在且为有限值 $ (k = 0, 1, ...) $ 

(2)对 $ [a, b] $ 上的非负连续函数 $ g(x) $ ，如果 $ \int_a^b g(x) \rho(x) dx = 0 $ ，则 $ g(x) \equiv 0 $ 

则称 $ \rho(x) $ 为 $ [a, b] $ 上的一个**权函数**。

* * *

定义：设 $ f(x), g(x) \in C[a, b] $ ， $ \rho(x) $ 是 $ [a, b] $ 上给定的权函数，则可定义内积

$$
(f(x), g(x)) = \int_a^b \rho(x) f(x) g(x) dx
$$

若 $ [a, b] $ 为无限区间，则这种方法定义的积分不一定存在，容易在区间 $ [0, +\infty] $ 上构造反例，取 $ \rho(x) = e^{-x}, f(x) = e^x, g(x) = 1 \in C[0, +\infty] $ 。

* * *

若 $ \varphi_0, \varphi_1, ... , \varphi_n $ 是 $ C[a, b] $ 中的线性无关函数族，记 $ \Phi = span \lbrace \varphi_0, \varphi_1, ... , \varphi_n \rbrace $ ，它的格拉姆矩阵为

$$
G = G(\varphi_0, \varphi_1, ... , \varphi_n) = \begin{bmatrix}
(\varphi_1, \varphi_1) & (\varphi_2, \varphi_1) & \cdots & (\varphi_n, \varphi_1) \\
(\varphi_1, \varphi_2) & (\varphi_2, \varphi_2) & \cdots & (\varphi_n, \varphi_2) \\
\vdots                 & \vdots                 &        & \vdots                 \\
(\varphi_1, \varphi_n) & (\varphi_2, \varphi_n) & \cdots & (\varphi_n, \varphi_n)
\end{bmatrix}
$$

易知 $ \varphi_0, \varphi_1, ... , \varphi_n $ 线性无关的充要条件是 $ detG(\varphi_0, \varphi_1, ... , \varphi_n) \neq 0 $ 。

* * *

函数逼近主要讨论给定 $ f(x) \in C[a, b] $ ，求它的最佳逼近多项式。

定义：若 $ P^* (x) \in H_n $ 使误差

$$
\Vert f(x) - P^* (x) \Vert = \underset {P \in H_n} {min} \Vert f(x) - P(x) \Vert
$$

则称 $ P^* (x) $ 是 $ f(x) $ 在 $ [a, b] $ 上的**最佳逼近多项式**。

若 $ \Vert \cdot \Vert $ 取 $ \Vert \cdot \Vert_{\infty} $ ，则称 $ P^* (x) $ 是 $ f(x) $ 在 $ [a, b] $ 上的**最优一致逼近多项式**。

若 $ \Vert \cdot \Vert $ 取 $ \Vert \cdot \Vert_2 $ ，则称 $ P^* (x) $ 是 $ f(x) $ 在 $ [a, b] $ 上的**最佳平方逼近多项式**。

* * *

更一般地，若 $ \varphi_0, \varphi_1, ... , \varphi_n $ 是 $ C[a, b] $ 中的线性无关函数族， $ P^* (x) \in \Phi = span \lbrace \varphi_0, \varphi_1, ... , \varphi_n \rbrace $ ，且

$$
\Vert f(x) - P^* (x) \Vert = \underset {P \in \Phi} {min} \Vert f(x) - P(x) \Vert
$$

则称 $ P^* (x) $ 是 $ f(x) $ 在 $ [a, b] $ 上的**最佳逼近函数**。

* * *

定义：若给定 $ f(x) \in C[a, b] $ ，并且在 $ a \leqslant x_0 < x_1 < ... < x_m \leqslant b $ 上给出 $ f(x_i) (i = 0, 1, ... , m) $ ，若 $ P^* (x) \in \Phi $ ， $ \Phi $ 是一族 $ [a, b] $ 上的连续函数张成的线性空间，使得

$$
\Vert \pmb{f} - \pmb{ P^* } \Vert_2 = \underset {P \in \Phi} {min} \Vert \pmb{f} - \pmb{P} \Vert_2
$$

其中 $ \pmb{f} = (f(x_0), f(x_1), ... , f(x_m))^T, \pmb{P} = (P(x_0), P(x_1), ... , P(x_m))^T, \pmb{ P^* } = (P^* (x_0), P^* (x_1), ... , P^* (x_m))^T $ ，则称 $ P^* (x) $ 是 $ f(x) $ 的**最小二乘拟合**。

* * *

一般地，函数逼近问题就是对任何 $ f(x) \in C[a, b] $ ，在 $ C[a, b] $ 的子空间 $ \Phi $ 中找一个元素 $ \varphi^* (x) \in \Phi $ ，使得 $ f(x) - \varphi^* (x) $ 在某种意义下最小。

* * *

插值问题可以看成是特殊的最小二乘拟合，也是函数逼近的特殊情形。

* * *

定理（魏尔斯特拉斯定理）：设 $ f(x) \in C[a, b] $ ，则对任何 $ \epsilon > 0 $ ，总存在一个代数多项式 $ p(x) $ ，使得

$$
\underset {a \leqslant x \leqslant b} {\max} \vert f(x) - p(x) \vert < \epsilon
$$

在 $ [a, b] $ 上一致成立。

证明思路：考虑伯恩斯坦多项式

$$
B_n(f, x) = \sum_{k=0}^n f(\frac {k} {n}) P_k(x)
$$

其中

$$
P_k(x) = \binom {n} {k} x^k (1 - x)^{n-k} \\
\binom {n} {k} = \frac {n (n-1) ... (n-k+1)} {k!}
$$

证明 $ \lim \limits_{n \rightarrow \infty} B_n(f, x) = f(x) $ 在 $ [0, 1] $ 上一致成立。

事实上还可证明，若 $ f(x) $ 在 $ [0, 1] $ 上的 $ m $ 阶导数连续，则 $ \lim \limits_{n \rightarrow \infty} B_n^{(m)}(f, x) = f^{(m)}(x) $ 。

* * *

魏尔斯特拉斯定理说明了，若 $ \Phi $ 取所有多项式构成的子空间，则虽然 $ \underset {P \in \Phi} {min} \Vert f(x) - P(x) \Vert_{\infty} $ 不存在，但我们有

$$
\inf \limits_{P \in \Phi} \Vert f(x) - P(x) \Vert_{\infty} = 0
$$

即我们可以用代数多项式对 $ f(x) $ 做任意程度的逼近，所以 $ B_n(f, x) $ 也可视为 $ f(x) $ 在 $ [0, 1] $ 上的一个逼近多项式，但它收敛太慢，实际中很少使用。

* * *

[上一级](./../index.html)

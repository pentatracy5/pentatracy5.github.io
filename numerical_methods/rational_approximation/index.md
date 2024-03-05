---
layout: default
title: 有理逼近
---

定义：**有理逼近函数**是指用形如

$$
R_{nm}(x) = \frac {P_n(x)} {Q_m(x)} = \frac {\sum_{k=0}^n a_k x^k} {\sum_{k=0}^m b_k x^k}
$$

的函数逼近 $ f(x) $ 。如果取 $ \Vert f(x) - R_{nm}(x) \Vert_{\infty} $ 最小就可得到**最佳有理一致逼近函数**。如果取 $ \Vert f(x) - R_{nm}(x) \Vert_2 $ 最小就可得到**最佳有理平方逼近函数**。

* * *

由无穷级数相关知识可知 $ x \in (-1, 1) $ 时有 $ \frac {1} {1+x} = 1 - x + x^2 - x^3 + x^4 - ... $ ，从而对 $ \beta(x) \in (-1, 1) $ 有 $ \frac {1} {1 + \beta(x)} = 1 - \beta(x) + \beta^2(x) - \beta^3(x) + \beta^4(x) - ... $ 。

根据该公式以及函数的泰勒展开，我们可以将 $ f(x) $ 写成连分式的形式，从而求得 $ f(x) \in C^{N+1}(-a, a) $ 的有理逼近。

设 $ f(x) $ 在 $ x=0 $ 的泰勒展开为

$$
\begin{aligned}
f(x) &= \sum_{k=0}^N \frac {f^{(k)}(0)} {k!} x^k + \frac {f^{(N+1)}(\xi)} {(N+1)!} x^{N+1} \\
&= f(0) + f^{(1)}(0) x + \frac {f^{(2)}(0)} {2!} x^2 + \frac {f^{(3)}(0)} {3!} x^3 + ... + \frac {f^{(N+1)}(\xi)} {(N+1)!} x^{N+1}
\end{aligned}
$$

用辗转相除法有

$$
f(x) = f(0) + \frac {f^{(1)}(0) x} {\frac {1} {1 + \frac {f^{(2)}(0)} {2! f^{(1)}(0)} x + \frac {f^{(3)}(0)} {3! f^{(1)}(0)} x^2 + ... + \frac {f^{(N+1)}(\xi)} {(N+1)! f^{(1)}(0)} x^N}} 
$$

令

$$
\beta(x) = \frac {f^{(2)}(0)} {2! f^{(1)}(0)} x + \frac {f^{(3)}(0)} {3! f^{(1)}(0)} x^2 + ... + \frac {f^{(N+1)}(\xi)} {(N+1)! f^{(1)}(0)} x^N
$$

则

$$
\begin{aligned}
f(x) &= f(0) + \frac {f^{(1)}(0) x} {\frac {1} {1 + \beta(x)}} \\
&= f(0) + \frac {f^{(1)}(0) x} {\frac {1} {f^{(1)}(0)} \Big[ 1 - \beta(x) + \beta^2(x) - \beta^3(x) + \beta^4(x) - ... \Big]} \\
&= f(0) + \frac {x} {\frac {1} {f^{(1)}(0)} + \frac {1} {f^{(1)}(0)} \Big[ -\beta(x) + \beta^2(x) - \beta^3(x) + \beta^4(x) - ... \Big]}
\end{aligned}
$$

对于逼近问题来说，一般只需要前若干项，从而可以通过计算得 $ \frac {1} {f^{(1)}(0)} \Big[ -\beta(x) + \beta^2(x) - \beta^3(x) + \beta^4(x) - ... \Big] = d_1 x + d_2 x^2 + d_3 x^3 + d_4 x^4 + ... $ ，故有

$$
\begin{aligned}
f(x) &= f(0) + \frac {x} {\frac {1} {f^{(1)}(0)} + d_1 x + d_2 x^2 + d_3 x^3 + d_4 x^4 + ...} \\
&= f(0) + \frac {x} {\frac {1} {f^{(1)}(0)} + \frac {x} {\frac {1} {d_1 x + d_2 x^2 + d_3 x^3 + d_4 x^4 + ...}}}
\end{aligned}
$$

按照此思路继续计算下去，则可得到连分式形式的函数表达式

$$
f(x) = r_1 + \frac {s_1 x} {r_2 + \frac {s_2 x} {r_3 + \frac {s_3 x} {r_4 + ...}}}
$$

也可记为

$$
f(x) = r_1 + \frac {s_1 x} {r_2} {\tiny+} \frac {s_2 x} {r_3} {\tiny+} \frac {s_3 x} {r_4} {\tiny+} ...
$$

按照需要取前若干项，就可得到有理逼近函数。

* * *

用辗转相除法可以将有理函数化为连分式的形式，比直接用秦九韶算法计算多项式的乘除法计算次数更少。

* * *

定义：设 $ f(x) \in C^{N+1}(-a, a), N = n+m $ ，如果有理函数

$$
R_{nm}(x) = \frac {a_0 + a_1 x + ... + a_n x^n} {1 + b_1 x + ... + b_m x^m} = \frac {P_n(x)} {Q_m(x)}
$$

其中 $ P_n(x), Q_m(x) $ 无公因式，且满足条件

$$
R_{nm}^{(k)}(0) = f^{(k)}(0), k = 0, 1, ... , N
$$

则称 $ R_{nm}(x) $ 为函数 $ f(x) $ 在 $ x=0 $ 处的 $ (n, m) $ 阶**帕德逼近**，记作 $ R(n, m) $ ，简称 $ R(n, m) $ 的帕德逼近。

* * *

定理：设 $ f(x) \in C^{N+1}(-a, a), N = n+m $ ，若有理函数

$$
R_{nm}(x) = \frac {a_0 + a_1 x + ... + a_n x^n} {1 + b_1 x + ... + b_m x^m} = \frac {P_n(x)} {Q_m(x)}
$$

是 $ f(x) $ 在 $ x=0 $ 处的 $ (n, m) $ 阶帕德逼近，则 $ a_0, a_1, ... , a_n, b_1, b_2, ... , b_m $ 满足

$$
a_k = \sum_{j=0}^{k-1} c_j b_{k-j} + c_k, k = 0, 1, ... , N
$$

其中

$$
a_i = 0, i > n \\
b_j = 0, j > m \\
c_j = \begin{cases}
\frac {f^{(j)}(0)} {j!}, j \geqslant 0 \\
0, j<0
\end{cases}
$$

证明：先证明对于任意 $ g(x), h(x) \in C^N(-a, a) $ ，且 $ g(0) \neq 0 $ ，则 $ [h(x) g(x)]^{(k)} \vert_{x=0} = 0, k = 0, 1, ... , N $ 等价于 $ h^{(k)}(0) = 0, k = 0, 1, ... , N $ 。

用数学归纳法。当 $ [h(x) g(x)]^{(k)} \vert_{x=0} = 0, k = 0 $ 时，由于 $ g(0) \neq 0 $ ，显然有 $ h^{(k)}(0) = 0, k = 0 $ 。

现假设有 $ [h(x) g(x)]^{(k)} \vert_{x=0} = 0, k = 0, 1, ... , n $ 等价于 $ h^{(k)}(0) = 0, k = 0, 1, ... , l $ ，考虑 $ [h(x) g(x)]^{(k)} \vert_{x=0} = 0, k = 0, 1, ... , l+1 $ 的情况。

显然此时 $ h^{(k)}(0) = 0, k = 0, 1, ... , l $ ，再根据莱布尼兹求导公式有 $ [h(x) g(x)]^{(l+1)} \vert_{x=0} = h^{(l+1)}(0) g(0) = 0 $ ，从而 $ h^{(l+1)}(0) = 0 $ ，反之亦然，故等价性成立。

根据定义有

$$
\begin{aligned}
R_{nm}^{(k)}(0) &= f^{(k)}(0) \\
\Big[ f(x) - R_{nm}(x) \Big]^{(k)} \Big\vert_{x=0} &= 0 \\
\Big[ \frac {f(x) Q_m(x) - P_n(x)} {Q_m(x)} \Big]^{(k)} \Big\vert_{x=0} &= 0 \\
\end{aligned}
$$

令 $ h(x) = f(x) Q_m(x) - P_n(x), g(x) = \frac {1} {Q_m(x)} $ ，由之前证明的结论有

$$
R_{nm}^{(k)}(0) = f^{(k)}(0), k = 0, 1, ... , N
$$
 
等价于

$$
\Big[ f(x) Q_m(x) - P_n(x) \Big]^{(k)} \Big\vert_{x=0} = 0, k = 0, 1, ... , N
$$

由莱布尼兹求导公式及 $ a_i = 0(i > n), b_0 = 1, b_j = 0(j > m) $ 有

$$
a_k = \sum_{j=0}^{k-1} c_j b_{k-j} + c_k, k = 0, 1, ... , N
$$

* * *

当 $ k > n $ 时，有 $ -\sum_{j=0}^{k-1} c_j b_{k-j} = c_k $ ，即

$$
\begin{cases}
-c_{n-m+1} b_m - ... - c_{n-1} b_2 - c_n b_1 = c_{n+1} \\
-c_{n-m+2} b_m - ... - c_n b_2 - c_{n+1} b_1 = c_{n+2} \\
\vdots \\
-c_n b_m - ... - c_{n+m-2} b_2 - c_{n+m-1} b_1 = c_{n+m}
\end{cases}
$$

若记

$$
\begin{aligned}
H &= \begin{bmatrix}
-c_{n-m+1}  & \cdots    & c_{n-1}   & c_n       \\
-c_{n-m+2}  & \cdots    & c_n       & c_{n+1}   \\
\vdots      &           & \vdots    & \vdots    \\
-c_n        & \cdots    & c_{n+m-2} & c_{n+m-1} 
\end{bmatrix} \\
b &= (b_m, b_{m-1}, ... , b_1)^T \\
c &= (c_{n+1}, c_{n+2}, ... , c_{n+m})^T
\end{aligned}
$$

则可通过解线性方程组 $ Hb = c $ 来确定 $ b_1, b_2, ... , b_m $ 。

若 $ b_1, b_2, ... , b_m $ 有唯一解，再根据 $ k \leqslant n $ 时有 $ a_k = \sum_{j=0}^{k-1} c_j b_{k-j} + c_k $ 可确定 $ a_0, a_1, ... , a_n $ 。此时若满足 $ P_n(x) $ 和 $ Q_m(x) $ 没有公因式，则 $ R_{nm}(x) $ 即为函数 $ f(x) $ 在 $ x=0 $ 处的 $ (n, m) $ 阶帕德逼近。

* * *

利用泰勒展开可得帕德逼近的误差估计

$$
f(x) - R_{nm}(x) = \frac {x^{n+m+1} \sum_{l=0}^{\infty} r_l x^l} {Q_m(x)} \\
r_l = \sum_{k=0}^m b_k c_{n+m+l+1-k}
$$

当 $ \vert x \vert < 1 $ 时可得误差近似表达式

$$
f(x) - R_{nm}(x) \approx r_0 x^{n+m+1} \\
r_0 = \sum_{k=0}^m b_k c_{n+m+1-k}
$$

* * *

[上一级](./../index.html)

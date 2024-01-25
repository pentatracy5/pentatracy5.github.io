---
layout: default
title: 正交多项式
---

定义：若 $ f(x), g(x) \in C[a, b] $ ， $ \rho(x) $ 为 $ [a, b] $ 上的权函数且满足

$$
(f(x), g(x)) = \int_a^b \rho(x) f(x) g(x) dx = 0
$$

则称 $ f(x) $ 与 $ g(x) $ 在 $ [a, b] $ 上带权 $ \rho(x) $ **正交**。若函数族 $ \varphi_0(x), \varphi_1(x), ... , \varphi_n(x), ... $ 满足关系

$$
(\varphi_j(x), \varphi_k(x)) = \int_a^b \rho(x) \varphi_j(x) \varphi_k(x) dx = 
\begin{cases}
0, j \neq k \\
A_k > 0, j = k
\end{cases}
$$

则称 $ \lbrace \varphi_k(x) \rbrace $ 是 $ [a, b] $ 上带权 $ \rho(x) $ 的**正交函数族**。若 $ A_k \equiv 1 $ ，则称为**标准正交函数族**。

* * *

定理：三角函数族

$$
1, \cos x, \sin x, \cos 2x, \sin 2x, ...
$$

是区间 $ [-\pi, \pi] $ 上带权 $ \rho(x) \equiv 1 $ 的正交函数族。

证明：对 $ k = 1, 2, ... $

$$
(1, 1) = \int_{-\pi}^{\pi} 1 dx = 2 \pi
$$

$$
(\sin kx, \sin kx) = \int_{-\pi}^{\pi} \sin^2 kx dx = \frac {x - \frac {\sin 2kx} {2k}} {2} \bigg\vert_{-\pi}^{\pi} = \pi
$$

$$
(\cos kx, \cos kx) = \int_{-\pi}^{\pi} \cos^2 kx dx = \frac {x + \frac {\sin 2kx} {2k}} {2} \bigg\vert_{-\pi}^{\pi} = \pi
$$

$$
(1, \sin kx) = \int_{-\pi}^{\pi} \sin kx dx = -\frac {\cos kx} {k} \bigg\vert_{-\pi}^{\pi} = 0
$$

$$
(1, \cos kx) = \int_{-\pi}^{\pi} \cos kx dx = \frac {\sin kx} {k} \bigg\vert_{-\pi}^{\pi} = 0
$$

$$
(\sin kx, \cos kx) = \int_{-\pi}^{\pi} \sin kx \cos kx dx = \frac {1} {2} \int_{-\pi}^{\pi} \sin 2kx dx = 0
$$

再对 $ j = 1, 2, ... $ 且 $ j \neq k $

$$
(\sin kx, \sin jx) = \int_{-\pi}^{\pi} \sin kx \sin jx dx = \frac {1} {2} (\int_{-\pi}^{\pi} \cos (k-j)x dx - \int_{-\pi}^{\pi} \cos (k+j)x dx) = 0
$$

$$
(\cos kx, \cos jx) = \int_{-\pi}^{\pi} \cos kx \cos jx dx = \frac {1} {2} (\int_{-\pi}^{\pi} \cos (k+j)x dx + \int_{-\pi}^{\pi} \cos (k-j)x dx) = 0
$$

$$
(\sin kx, \cos jx) = \int_{-\pi}^{\pi} \sin kx \cos jx dx = \frac {1} {2} (\int_{-\pi}^{\pi} \sin (k+j)x dx + \int_{-\pi}^{\pi} \sin (k-j)x dx) = 0
$$

* * *

定义：设 $ \varphi_n(x) $ 是 $ [a, b] $ 上首项系数 $ a_n \neq 0 $ 的 $ n $ 次多项式， $ \rho(x) $ 为 $ [a, b] $ 上的权函数。如果多项式序列 $ \lbrace \varphi_n(x) \rbrace_0^{\infty} $ 是正交函数族，则称 $ \lbrace \varphi_n(x) \rbrace_0^{\infty} $ 为 $ [a, b] $ 上带权 $ \rho(x) $ 的**正交多项式**，称 $ \varphi_n(x) $ 为 $ n $ **次正交多项式**。

* * *

给定区间 $ [a, b] $ 及权函数 $ \rho(x) $ ，以及一族线性无关的幂函数 $ 1, x, x^2, ... $ ，利用施密特正交化可以构造出正交多项式 $ \lbrace \varphi_n(x) \rbrace_0^{\infty} $ 

$$
\varphi_0(x) = 1 \\
\varphi_n(x) = x^n - \sum_{j=0}^{n-1} \frac {(x^n, \varphi_j(x))} {(\varphi_j(x), \varphi_j(x))} \varphi_j(x), n = 1, 2, ...
$$

易知 $ \varphi_n(x) $ 最高项系数为 $ 1 $ 。

* * *

若 $ \lbrace \varphi_n(x) \rbrace_0^{\infty} $ 是正交多项式，易证对任意 $ n $ ， $ \varphi_0(x), \varphi_1(x), ... , \varphi_n(x) $ 在 $ [a, b] $ 上是线性无关的。从而有，任何 $ P(x) \in H_n $ 均可表示为 $ \varphi_0(x), \varphi_1(x), ... , \varphi_n(x) $ 的线性组合。此外， $ \varphi_n(x) $ 与任何 $ P(x) \in H_{n-1} $ 正交。

* * *

定理：设 $ \lbrace \varphi_n(x) \rbrace_0^{\infty} $ 是 $ [a, b] $ 上带权 $ \rho(x) $ 的正交多项式，对 $ n \geqslant 0 $ 成立递推关系

$$
\gamma \varphi_{n+1}(x) = (x - \beta) \varphi_n(x) - \alpha \varphi_{n-1}(x), n = 0, 1, ...
$$

其中

$$
\varphi_0(x) = 1 \\
\varphi_{-1}(x) = 0 \\
\alpha = \frac {(x \varphi_n(x), \varphi_{n-1}(x))} {(\varphi_{n-1}(x), \varphi_{n-1}(x))} \\
\beta = \frac {(x \varphi_n(x), \varphi_n(x))} {(\varphi_n(x), \varphi_n(x))} \\
\gamma = \frac {(x \varphi_n(x), \varphi_{n+1}(x))} {(\varphi_{n+1}(x), \varphi_{n+1}(x))}
$$

证明：由于 $ \varphi_0(x), \varphi_1(x), ... , \varphi_{n+1}(x) $ 构成 $ H_{n+1} $ 的一组基，而 $ x \varphi_n(x) \in H_{n+1} $ ，故 $ x \varphi_n(x) $ 可以表示为

$$
x \varphi_n(x) = a_0 \varphi_0(x) + a_1 \varphi_1(x) + ... + a_{n-2} \varphi_{n-2}(x) + \alpha \varphi_{n-1}(x) + \beta \varphi_n(x) + \gamma \varphi_{n+1}(x)
$$

两边用 $ \varphi_k(x), k = 0, 1, ... , n-2 $ 做内积，利用 $ \lbrace \varphi_n(x) \rbrace_0^{\infty} $ 的正交性可得

$$
(x \varphi_n(x), \varphi_k(x)) = a_k (\varphi_k(x), \varphi_k(x))
$$

又由正交多项式的性质可知

$$
(x \varphi_n(x), \varphi_k(x)) = (\varphi_n(x), x \varphi_k(x)) = 0
$$

因此

$$
a_k = 0, k = 0, 1, ... , n-2
$$

于是

$$
x \varphi_n(x) = \alpha \varphi_{n-1}(x) + \beta \varphi_n(x) + \gamma \varphi_{n+1}(x)
$$

两边分别用 $ \varphi_{n-1}(x), \varphi_n(x), \varphi_{n+1}(x) $ 做内积，可得

$$
\alpha = \frac {(x \varphi_n(x), \varphi_{n-1}(x))} {(\varphi_{n-1}(x), \varphi_{n-1}(x))} \\
\beta = \frac {(x \varphi_n(x), \varphi_n(x))} {(\varphi_n(x), \varphi_n(x))} \\
\gamma = \frac {(x \varphi_n(x), \varphi_{n+1}(x))} {(\varphi_{n+1}(x), \varphi_{n+1}(x))}
$$

并且

$$
\gamma \varphi_{n+1}(x) = (x - \beta) \varphi_n(x) - \alpha \varphi_{n-1}(x)
$$

得证。

特别地，若 $ \lbrace \varphi_n(x) \rbrace_0^{\infty} $ 的最高项次数为 $ 1 $ ，则有 $ x \varphi_{n-1}(x) - \varphi_n(x) \in H_{n-1} $ ，因此 $ (\varphi_n(x), x \varphi_{n-1}(x) - \varphi_n(x)) = 0 $ ，从而

$$
(x \varphi_n(x), \varphi_{n-1}(x)) = (\varphi_n(x), x \varphi_{n-1}(x)) = (\varphi_n(x), \varphi_n(x)) + (\varphi_n(x), x \varphi_{n-1}(x) - \varphi_n(x)) = (\varphi_n(x), \varphi_n(x))
$$

同理

$$
(\varphi_{n+1}(x), x \varphi_n(x)) = (\varphi_{n+1}(x), \varphi_{n+1}(x))
$$

故

$$
\alpha = \frac {(\varphi_n(x), \varphi_n(x))} {(\varphi_{n-1}(x), \varphi_{n-1}(x))} \\
\gamma = 1
$$

* * *

定理：设 $ \lbrace \varphi_n(x) \rbrace_0^{\infty} $ 是 $ [a, b] $ 上带权 $ \rho(x) $ 的正交多项式，则 $ \varphi_n(x) $ 在区间 $ (a, b) $ 内有 $ n $ 个不同的零点。

证明：假定 $ \varphi_n(x) $ 在区间 $ (a, b) $ 内的零点都是偶数重的，则 $ \varphi_n(x) $ 在区间 $ [a, b] $ 保持符号不变，这与

$$
(\varphi_n(x), \varphi_0(x)) = \int_a^b \rho(x) \varphi_n(x) \varphi_0(x) dx = 0
$$

矛盾，故 $ \varphi_n(x) $ 在区间 $ (a, b) $ 内存在奇数重的零点，不妨设为 $ a < x_1 < x_2 < ... < x_l < b $ 。令

$$
q(x) = (x - x_1) (x - x_2) ... (x - x_l)
$$

若 $ l < n $ ，则根据正交性有

$$
(q(x), \varphi_n(x)) = \int_a^b \rho(x) q(x) \varphi_n(x) dx = 0
$$

又根据 $ q(x) $ 的定义可知 $ q(x) \varphi_n(x) $ 在 $ (a, b) $ 内的零点全为偶数重的，故在区间 $ [a, b] $ 保持符号不变，与$ (q(x), \varphi_n(x)) = 0 $ 矛盾。

因此 $ l \geqslant n $ ，再由多项式为 $ n $ 次得证。

* * *

定义：当区间为 $ [-1, 1] $ ，权函数为 $ \rho(x) \equiv 1 $ 时，由 $ 1, x, ... , x^n, ... $ 正交化得到的多项式称为**勒让德多项式**，并用 $ P_0(x), P_1(x), ... , P_n(x), ... $ 表示。

* * *

1814年罗德利克给出了勒让德多项式的简单表达式

$$
P_0(x) = 1 \\
P_n(x) = \frac {1} {2^n n!} \frac {d^n} {dx^n} (x^2 - 1)^n, n = 1, 2, ...
$$

* * *

$ P_n(x) $ 中首项 $ x^n $ 的系数为 $ \frac {(2n)!} {2^n (n!)^2} $ ，显然最高项次数为 $ 1 $ 的勒让德多项式为

$$
\widetilde{P}_0(x) = 1 \\
\widetilde{P}_n(x) = \frac {n!} {(2n)!} \frac {d^n} {dx^n} (x^2 - 1)^n, n = 1, 2, ...
$$

* * *

勒让德多项式的正交性

$$
\int_{-1}^1 P_n(x) P_m(x) dx = \begin{cases}
0, m \neq n \\
\frac {2} {2n+1}, m = n
\end{cases}
$$

证明：令 $ \varphi(x) = (x^2 - 1)^n $ ，则

$$
\varphi^{(k)}(\pm 1) = 0, k = 0, 1, ... , n-1
$$

设 $ Q(x) $ 是在区间 $ [-1, 1] $ 上有 $ n $ 阶连续可微的函数，由分部积分法可知

$$
\begin{aligned}
\int_{-1}^1 P_n(x) Q(x) dx &= \frac {1} {2^n n!} \int_{-1}^1 \varphi^{(n)}(x) Q(x) dx \\
&= \frac {-1} {2^n n!} \int_{-1}^1 \varphi^{(n-1)}(x) Q^{(1)}(x) dx \\
&= ... \\
&= \frac {(-1)^n} {2^n n!} \int_{-1}^1 \varphi(x) Q^{(n)}(x) dx
\end{aligned}
$$

若 $ Q(x) $ 是次数小于 $ n $ 的多项式，则 $ Q^{(n)}(x) \equiv 0 $ ，故得

$$
\int_{-1}^1 P_n(x) P_m(x) dx = 0, m \neq n
$$

若

$$
Q(x) = P_n(x) = \frac {(2n)!} {2^n (n!)^2} x^n + ...
$$

则

$$
Q^{(n)}(x) = \frac {(2n)!} {2^n n!}
$$

于是

$$
\begin{aligned}
\int_{-1}^1 P_n^2(x) dx &= \frac {(-1)^n (2n)!} {2^{2n} (n!)^2} \int_{-1}^1 \varphi(x) dx \\
&= \frac {(2n)!} {2^{2n} (n!)^2} \int_{-1}^1 (1 - x^2)^n dx \\
&= \frac {2 (2n)!} {2^{2n} (n!)^2} \int_{0}^1 (1 - x^2)^n dx \\
&= \frac {2 (2n)!} {2^{2n} (n!)^2} \int_{0}^{\frac {\pi} {2}} \cos^{2n+1} t dt \\
&= \frac {2 (2n)!} {2^{2n} (n!)^2} \frac {2 * 4 * ... * (2n)} {1 * 3 * ... * (2n+1)} \\
&= \frac {2} {2n+1}
\end{aligned}
$$

得证。

* * *

勒让德多项式的奇偶性

$$
P_n(-x) = (-1)^n P_n(x)
$$

证明：由于 $ (x^2 - 1)^n $ 是偶函数，故经过偶数次求导仍为偶函数，经过奇数次求导为奇函数。得证。

* * *

勒让德多项式的递推关系

$$
(n+1) P_{n+1}(x) = (2n+1) x P_n(x) - n P_{n-1}(x), n = 1, 2, ...
$$

证明：考虑正交多项式所满足的递推公式

$$
x P_n(x) = \alpha P_{n-1}(x) + \beta P_n(x) + \gamma P_{n+1}(x)
$$

等式左边最高次项的系数为 $ \frac {(2n)!} {2^n (n!)^2} $ ，等式右边最高次项的系数为 $ \frac {\gamma (2n+2)!} {2^{n+1} ((n+1)!)^2} $ ，二者应该相等，从而有

$$
\gamma = \frac {(x P_n(x), P_{n+1}(x))} {(P_{n+1}(x), P_{n+1}(x))} = \frac {n+1} {2n+1}
$$

故

$$
(x P_n(x), P_{n+1}(x)) = \frac {n+1} {2n+1} (P_{n+1}(x), P_{n+1}(x)) = \frac {2n+2} {(2n+1) (2n+3)}
$$

同理有

$$
(x P_n(x), P_{n-1}(x)) = (x P_{n-1}(x), P_n(x)) = \frac {2n} {(2n-1) (2n+1)}
$$

故

$$
\alpha = \frac {(x P_n(x), P_{n-1}(x))} {(P_{n-1}(x), P_{n-1}(x))} = \frac {n} {2n+1}
$$

又

$$
\alpha = \frac {(x P_n(x), P_{n-1}(x))} {(P_{n-1}(x), P_{n-1}(x))} = \frac {n} {2n+1}
$$

又 $ x P_n^2(x) $ 为奇函数，故 $ (x P_n(x), P_n(x)) = \int_{-1}^1 x P_n^2(x) dx = 0 $ ，因此

$$
\beta = \frac {(x P_n(x), P_n(x))} {(P_n(x), P_n(x))} = 0
$$

将 $ \alpha, \beta, \gamma $ 代入递推公式，得证。

* * *

利用勒让德多项式的递推公式有

$$
\begin{aligned}
&P_0(x) = 1 \\
&P_1(x) = x \\
&P_2(x) = \frac {3 x^2 - 1} {2} \\
&P_3(x) = \frac {5 x^3 - 3 x} {2} \\
&P_4(x) = \frac {35 x^4 - 30 x^2 + 3} {8} \\
&P_5(x) = \frac {63 x^5 - 70 x^3 + 15x} {8} \\
&P_6(x) = \frac {231 x^6 - 315 x^4 + 105 x^2 - 5} {16} \\
&...
\end{aligned}
$$

[...img]

* * *

勒让德多项式在区间 $ (-1, 1) $ 内有 $ n $ 个不同的实零点。

* * *

[上一级](./../index.html)

---
layout: default
title: 最佳一致逼近多项式
---

定理：对任意 $ f(x) \in C[a, b] $ ，以及任何 $ n = 0, 1, ... $ ， $ f(x) $ 的 $ n $ 次最佳一致逼近多项式存在。

证明：用数学归纳法。先证零次最佳一致逼近多项式存在。设 $ f(x) $ 在 $ [a, b] $ 上的上下确界分别为 $ M, m $ ，取恒为 $ \frac {m+M} {2} $ 的函数即得 $ f(x) $ 的零次最佳一致逼近多项式。

假设任意 $ f(x) \in C[a, b] $ 的 $ n $ 次最佳一致逼近多项式存在，往证任意 $ f(x) \in C[a, b] $ 的 $ n+1 $ 次最佳一致逼近多项式也存在。

记 $ P_n(x) $ 是不高于 $ n $ 次的多项式，为阐述简便做如下定义

$$
\Delta_f(P_n) = \underset {x \in [a, b]} {\sup} \vert f(x) - P_n(x) \vert \\
E_n(f) = \underset {P_n} {\inf} \Delta_f(P_n)
$$

考虑关于 $ \lambda \in \mathbb{R} $ 的函数 $ g(\lambda) = E_n(f - \lambda x^{n+1}) $ ，对 $ \forall \lambda \in \mathbb{R} $ ， $ \forall \epsilon > 0 $ ，令 $ \delta = \frac {\epsilon} {\max \lbrace \vert a^{n+1} \vert, \vert b^{n+1} \vert \rbrace} $ ，则对 $ \forall \lambda' \in (\lambda - \epsilon, \lambda + \epsilon) $ 有

$$
\begin{aligned}
g(\lambda) &= E_n(f - \lambda x^{n+1}) \\
&= \underset {P_n} {\inf} \underset {x \in [a, b]} {\sup} \vert f(x) - \lambda x^{n+1} - P_n(x) \vert \\
&= \underset {P_n} {\inf} \underset {x \in [a, b]} {\sup} \vert f(x) - \lambda' x^{n+1} - P_n(x) + (\lambda' - \lambda) x^{n+1} \vert \\
&\leqslant \underset {P_n} {\inf} \underset {x \in [a, b]} {\sup} \Big[ \vert f(x) - \lambda' x^{n+1} - P_n(x) \vert + \vert \lambda' - \lambda \vert \vert x^{n+1} \vert \Big] \\
&\leqslant \underset {P_n} {\inf} \underset {x \in [a, b]} {\sup} \vert f(x) - \lambda' x^{n+1} - P_n(x) \vert + \underset {x \in [a, b]} {\sup} \vert \lambda' - \lambda \vert \vert x^{n+1} \vert \\
&\leqslant E_n(f - \lambda' x^{n+1}) + \vert \lambda' - \lambda \vert \max \lbrace \vert a^{n+1} \vert, \vert b^{n+1} \vert \rbrace \\
&< g(\lambda') + \epsilon
\end{aligned}
$$

同理有 $ g(\lambda') < g(\lambda) + \epsilon $ ，从而 $ \vert g(\lambda') - g(\lambda) \vert < \epsilon $ ，即 $ g(\lambda) $ 关于 $ \lambda $ 连续。

根据归纳假设，记 $ P_n^* (x) $ 为满足 $ \Delta_{x^{n+1}}( P_n^* ) = E_n(x^{n+1}) $ 的多项式，则有

$$
E_n(\lambda x^{n+1}) = \Delta_{\lambda x^{n+1}}( \lambda P_n^* ) = \vert \lambda \vert \Delta_{x^{n+1}}( P_n^* ) = \vert \lambda \vert E_n(x^{n+1})
$$

从而

$$
\begin{aligned}
g(\lambda) &= E_n(f - \lambda x^{n+1}) \\
&= \underset {P_n} {\inf} \underset {x \in [a, b]} {\sup} \vert f(x) - \lambda x^{n+1} - P_n(x) \vert \\
&= \underset {P_n} {\inf} \underset {x \in [a, b]} {\sup} \vert \lambda x^{n+1} + P_n(x) - f(x) \vert \\
&\geqslant \underset {P_n} {\inf} \Big[ \underset {x \in [a, b]} {\sup} \vert \lambda x^{n+1} + P_n(x) \vert - \underset {x \in [a, b]} {\sup} \vert f(x) \vert \Big] \\
&= E_n(\lambda x^{n+1}) - \underset {x \in [a, b]} {\sup} \vert f(x) \vert \\
&= \vert \lambda \vert E_n(x^{n+1}) - \underset {x \in [a, b]} {\sup} \vert f(x) \vert
\end{aligned}
$$

故有 $ \lim\limits_{\lambda \rightarrow \infty} g(\lambda) = \infty $ 

又根据 $ g(\lambda) $ 定义可知 $ g(\lambda) \geqslant 0 $ ，故存在 $ \mu = \underset {\lambda \in \mathbb{R}} {\inf} g(\lambda) $ ，从而存在序列 $ \lbrace \lambda_n \rbrace $ 使得 $ \mu = \lim\limits_{n \rightarrow \infty} g(\lambda_n) $ ，并且 $ \lbrace \lambda_n \rbrace $ 有界。

由于有界序列必有收敛子列，因此不妨设 $ \lbrace \lambda_n \rbrace $ 收敛到 $ \lambda^* $ ，从而 $ \mu = \lim\limits_{n \rightarrow \infty} g(\lambda_n) = g( \lambda^* ) $ ，即 $ \lambda^* $ 为 $ g(\lambda) $ 的最小值点。

再次根据归纳假设，记 $ P_n'(x) $ 为满足 $ \Delta_{f - \lambda^* x^{n+1}}(P_n') = E_n(f - \lambda^* x^{n+1}) $ 的多项式，则有

$$
\begin{aligned}
E_{n+1}(f) &= \underset {\lambda \in \mathbb{R}} {\inf} \underset {P_n} {\inf} \underset {x \in [a, b]} {\sup} \vert f(x) - \lambda x^{n+1} - P_n(x) \vert \\
&= \underset {\lambda \in \mathbb{R}} {\inf} E_n(f - \lambda x^{n+1}) \\
&= E_n(f - \lambda^* x^{n+1}) \\
&= \Delta_{f - \lambda^* x^{n+1}}(P_n') \\
&= \underset {x \in [a, b]} {\sup} \vert f(x) - \lambda^* x^{n+1} - P_n'(x) \vert \\
&= \Delta_f(\lambda^* x^{n+1} + P_n')
\end{aligned}
$$

即 $ f(x) $ 的 $ n+1 $ 次最佳一致逼近多项式为 $ \lambda^* x^{n+1} + P_n' $ 。

综上得证。

* * *

定义：设 $ g(x) \in C[a, b] $ ，对于满足 $ a \leqslant x_0 \leqslant x_1 \leqslant ... \leqslant x_k \leqslant b $ 的点集 $ \lbrace x_0, x_1, ... , x_k \rbrace $ ，称为 $ g(x) $ 在 $ [a, b] $ 上的切比雪夫交错点组，当且仅当

$$
g(x_j) = (-1)^j \sigma \Vert g(x) \Vert_{\infty}, j = 0, 1, ... , k
$$

这里 $ \sigma $ 取 $ 1 $ 或 $ -1 $ ，由 $ g(x) $ 决定。

* * *

定理：切比雪夫交错定理

$ n $ 次多项式 $ P_n(x) $ 是函数 $ f \in C[a, b] $ 的最佳一致逼近多项式的充要条件是 $ f - P_n $ 在闭区间 $ [a, b] $ 上存在至少 $ n+2 $ 个切比雪夫交错点。

证明：为阐述简便，记 $ r = f - P_n $ 称为误差函数。

先证充分性。假设 $ r $ 在闭区间 $ [a, b] $ 上存在 $ n+2 $ 个切比雪夫交错点 $ x_0 < x_1 < ... < x_{n+1} $ ，用反证法，若 $ P_n $ 不是 $ f $ 的最佳一致逼近多项式，则存在另一多项式 $ Q_n $ ，使得 $ \Vert f - Q_n \Vert < \Vert r \Vert $ 。

按照交错点的定义，不妨设 $ r(x_j) = (-1)^j \Vert r \Vert, j = 0, 1, ... , n+1 $ ，再根据

$$
-\Vert r \Vert < -\Vert f - Q_n \Vert < f(x_j) - Q_n(x_j) < \Vert f - Q_n \Vert < \Vert r \Vert, j = 0, 1, ... , n+1
$$

有

$$
r(x_j) < f(x_j) - Q_n(x_j), j < n+2, j = 1, 3, ... \\
r(x_j) > f(x_j) - Q_n(x_j), j < n+2, j = 0, 2, ...
$$

从而

$$
Q_n(x_j) - P_n(x_j) < 0, j < n+2, j = 1, 3, ... \\
Q_n(x_j) - P_n(x_j) > 0, j < n+2, j = 0, 2, ...
$$

即 $ Q_n - P_n $ 在 $ x_0 < x_1 < ... < x_{n+1} $ 交替变号，从而 $ Q_n - P_n $ 在 $ [a, b] $ 上至少有 $ n+1 $ 个根，从而 $ Q_n \equiv P_n $ ，矛盾。充分性得证。

再证必要性。用反证法，假设 $ r $ 在闭区间 $ [a, b] $ 上存在不多于 $ n+1 $ 个切比雪夫交错点，不妨记为 $ x_0 < x_1 < ... < x_k, k < n+1 $ 且 $ r(x_j) = (-1)^j \Vert r \Vert, j = 0, 1, ... , k $ ，记 $ s_i(i = 1, 2, ... , k) $ 为 $ r $ 在 $ [x_{i-1}, x_i] $ 上最大的根，令

$$
h(x) = \pm \prod_{i=1}^k (x - s_i)
$$

其中的正负号可适当选取以使 $ h(x_0) < 0 $ ，则 $ r(x_i)h(x_i) < 0, i = 0, 1, ... , k $ 。记 $ s = \underset {0 \leqslant i \leqslant k} {\max} r(x_i) h(x_i) < 0 $ ， $ S = \lbrace x \in [a, b] \vert r(x)h(x) \geqslant \frac {s} {2} \rbrace $ 。

令 $ \Vert H \Vert = \underset {x \in [a, b]} {\max} \vert h(x) \vert $ ，由 $ S $ 以及 $ s $ 的定义可知 $ x_i \notin S $ ，从而有 $ E = \underset {x \in S} {r(x)} < E_n(f) $ ，令 $ 0 < \lambda_1 < \frac {E_n(f) - E} {H} $ ，则有

$$
\begin{aligned}
\underset {x \in S} {\sup} \vert r + \lambda_1 h \vert &\leqslant \underset {x \in S} {\sup} (\vert r \vert + \vert \lambda_1 h \vert) \\
&\leqslant \underset {x \in S} {\sup} \vert r \vert + \underset {x \in S} {\sup} \vert \lambda_1 h \vert \\
&\leqslant E + \vert \lambda_1 \vert H \\
&< E_n(f)
\end{aligned}
$$

再由 $ S $ 的定义可知，对 $ x \in [a, b] / S $ ，有 $ r(x)h(x) < \frac {s} {2} $ 。令 $ 0 < \lambda_2 < -\frac {s} {H^2} $ ，则对 $ x \in [a, b] / S $ 有

$$
\begin{aligned}
(r + \lambda_2 h)^2 &= r^2 + 2 \lambda_2 r h + \lambda_2^2 h^2 \\
&< [E_n(f)]^2 + \lambda_2 (s + \lambda_2 H^2) \\
&< [E_n(f)]^2
\end{aligned}
$$

即

$$
\begin{aligned}
\underset {x \in [a, b] / S} {\sup} \vert r + \lambda_2 h \vert &\leqslant \sqrt{[E_n(f)]^2 + \lambda_2 (s + \lambda_2 H^2)} \\
&< [E_n(f)]
\end{aligned}
$$

令 $ \lambda = \min \lbrace \lambda_1, \lambda_2 \rbrace $ ，则有 $ \Delta_f(P_n - \lambda h) < E_n(f) $ ，矛盾。

* * *

推论： $ n $ 次最佳一致逼近多项式唯一

证明：若 $ P_n $ 和 $ Q_n $ 均为 $ f $ 的 $ n $ 次最佳一致逼近多项式，则

$$
\Delta_f(P_n) = \Delta_f(Q_n) = E_n(f)
$$

从而

$$
\Delta_f(\frac {P_n + Q_n} {2}) = E_n(f)
$$

由交错定理可知在 $ [a, b] $ 上存在 $ n+1 $ 个点 $ x_0, x_1, ... , x_n $ 使得

$$
f(x_i) - \frac {P_n(x_i) + Q_n(x_i)} {2} = \frac {f(x_i) - P_n(x_i)} {2} + \frac {f(x_i) - Q_n(x_i)} {2} = (-1)^i E_n(f) \alpha
$$

又 $ \vert f(x_i) - P_n(x_i) \vert \leqslant E_n(f) $ ， $ \vert f(x_i) - Q_n(x_i) \vert \leqslant E_n(f) $ ，故

$$
f(x_i) - P_n(x_i) = f(x_i) - Q_n(x_i) = (-1)^i E_n(f) \alpha
$$

即 $ P_n(x_i) = Q_n(x_i), i = 0, 1, ... , n $ ，从而 $ P_n \equiv Q_n $ 。

* * *

推论： $ f $ 的 $ n $ 次最佳一致逼近多项式是 $ f $ 的某个 $ n $ 次拉格朗日插值多项式。

证明：由交错定理易知。

* * *

推论：如果 $ f $ 在 $ [a, b] $ 有 $ n+1 $ 阶导数且 $ f^{(n+1)}(x) $ 在区间 $ [a, b] $ 保号， $ P_n $ 是 $ f $ 的 $ n $ 次最佳一致逼近多项式，那么区间 $ [a, b] $ 的端点属于 $ f - P_n $ 的切比雪夫交错点组。

证明：用反证法，利用罗尔中值定理易知。

* * *

定义：如果 $ f(x) \in C[-1, 1] $ ，按切比雪夫多项式展成广义傅里叶级数，可得级数

$$
\frac { C_0^* } {2} + \sum_{k=1}^{\infty} C_k^* T_k(x) \\
C_k = \frac {2} {\pi} \int_{-1}^{1} \frac {f(x) T_k(x)} {\sqrt{1 - x^2}} dx, k = 0, 1, ... \\
T_k(x) = \cos(k \arccos x), -1 \leqslant x \leqslant 1, k = 0, 1, ... 
$$

称为**切比雪夫级数**。

* * *

若令 $ x = \cos \theta, 0 \leqslant \theta \leqslant \pi $ ，则 $ f(x) $ 的切比雪夫级数即为 $ f(\cos \theta) $ 的傅里叶级数，其中

$$
C_k = \frac {2} {\pi} \int_{0}^{\pi} \frac {f(\cos \theta) T_k(x)} {\sqrt{1 - x^2}} dx, k = 0, 1, ... 
$$

于是根据傅里叶级数理论知，只要 $ f(x) $ 在 $ [-1, 1] $ 上分段连续，则 $ f(x) $ 在 $ [-1, 1] $ 上的切比雪夫级数一致收敛于 $ f(x) $ ，从而可表示为

$$
f(x) = \frac { C_0^* } {2} + \sum_{k=1}^{\infty} C_k^* T_k(x)
$$

取它的部分和

$$
C_n(x) = \frac { C_0^* } {2} + \sum_{k=1}^{n} C_k^* T_k(x)
$$

其误差为

$$
f(x) - C_n(x) \approx C_{n+1}^* T_{n+1}(x)
$$

由于切比雪夫多项式对零的最佳一致逼近的性质， $ C_n(x) $ 可做为 $ f(x) $ 在 $ [-1, 1] $ 上的近似最佳一致逼近多项式。

* * *

[上一级](./../index.html)

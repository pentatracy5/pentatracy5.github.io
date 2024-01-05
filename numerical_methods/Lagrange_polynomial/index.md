---
layout: default
title: 拉格朗日插值
---

定义：若 $ n $ 次多项式 $ l_j(x) (j = 0, 1, ... , n) $ 在 $ n + 1 $ 个节点 $ x_0 < x_1 < ... < x_n $ 上满足条件

$$
    l_j(x) = \begin{cases}
                1, k = j\\
                0, k \neq j
             \end{cases}
             j, k = 0, 1, ... , n
$$

就称这 $ n + 1 $ 个 $ n $ 次多项式 $ l_0(x), l_1(x), ... , l_n(x) $ 为节点 $ x_0, x_1, ... , x_n $ 上的 $ n $ **次插值基函数**。

* * *

$$ l_k(x) = \frac {(x - x_0)...(x - x_{k-1})(x - x_{k+1})...(x - x_n)} {(x_k - x_0)...(x_k - x_{k-1})(x_k - x_{k+1})...(x_k - x_n)}, k = 0, 1, ... , n $$

* * *

定义：通过 $ n + 1 $ 个节点 $ x_0 < x_1 < ... < x_n $ 的 $ n $ 次插值多项式 $ L_n(x) $ 若满足条件

$$ L_n(x_i) = y_i, i = 0, 1, ... , n $$

则可表示为

$$ L_n(x) = \sum_{k=0}^n y_k l_k(x) $$

称为**拉格朗日插值多项式**。

* * *

若引入记号

$$ \omega_{n+1}(x) = (x - x_0)(x - x_1)...(x - x_n) $$

易得

$$ \omega'_{n+1}(x_k) = (x_k - x_0)...(x_k - x_{k-1})(x_k - x_{k+1})...(x_k - x_n) $$

从而

$$ L_n(x) = \sum_{k=0}^n y_k \frac {\omega_{n+1}(x)} {(x - x_k) \omega'_{n+1}(x_k)} $$

* * *

定理：设 $ f^{(n)}(x) $ 在 $ [a, b] $ 上连续， $ f^{(n+1)}(x) $ 在 $ (a, b) $ 内存在，插值节点为 $ a \leqslant x_0 < x_1 < ... < x_n \leqslant b $ ， $ L_n(x) $ 是对应的 $ n $ 次插值多项式，则对任何 $ x \in [a, b] $ ，插值余项

$$ R_n(x) = f(x) - L_n(x) = \frac {f^{(n+1)}(\xi)} {(n + 1)!} \omega_{n + 1}(x) $$

这里 $ \xi \in (a, b) $ 且依赖于 $ x $ 。

证明：由给定条件知 $ R_n(x_k) = 0 (k = 0, 1, ... , n) $ ，于是 $ R_n(x) $ 可表示为

$$ R_n(x) = K(x) (x - x_0) (x - x_1) ... (x - x_n) $$

其中 $ K(x) $ 是与 $ x $ 有关的待定函数。

现把 $ x $ 看成 $ [a, b] $ 上的一个固定点，做函数

$$ \varphi(t) = f(t) - L_n(t) - K(x) (t - x_0) (t - x_1) ... (t - x_n) $$

根据 $ f(t) $ 的假设可知 $ \varphi^{(n)}(t) $ 在 $ [a, b] $ 上连续， $ \varphi^{(n+1)}(t) $ 在 $ (a, b) $ 内存在。根据插值条件及余项定义，可知 $ \varphi(t) $ 在点 $ x_0, x_1, ... , x_n $ 及 $ x $ 处均为零，故 $ \varphi(t) $ 在 $ [a, b] $ 上有 $ n + 2 $ 个零点。

根据罗尔定理， $ \varphi'(t) $ 在 $ \varphi(t) $ 的两个零点间至少有一个零点，故 $ \varphi'(t) $ 在 $ [a, b] $ 内至少有 $ n + 1 $ 个零点。

对 $ \varphi'(t) $ 再用罗尔定理，可知 $ \ddot{\varphi}(t) $ 在 $ [a, b] $ 内至少有 $ n $ 个零点。依此类推， $ \varphi^{(n+1)}(t) $ 在 $ [a, b] $ 内至少有一个零点，记为 $ \xi \in [a, b] $ ，使

$$ \varphi^{(n+1)}(\xi) = f^{(n+1)}(\xi) - (n + 1)! K(x) = 0 $$

于是

$$ K(x) = \frac {f^{(n+1)}(\xi)} {(n + 1)!}, \xi \in (a, b), 且依赖于 x $$

从而

$$ R_n(x) = \frac {f^{(n+1)}(\xi)} {(n + 1)!} \omega_{n + 1}(x) $$

* * *

余项表达式只有在 $ f(x) $ 的高阶导数存在的时候才能应用。 $ \xi $ 在 $ (a, b) $ 内的具体位置通常不可能给出。如果我们可以求出 $ M_{n+1} = \max_{a \leqslant x \leqslant b} \vert f^{(n+1)}(x) \vert $ ，那么插值多项式 $ L_n(x) $ 逼近 $ f(x) $ 的截断误差限是

$$ \vert R_n(x) \vert \leqslant \frac {M_{n+1}} {(n + 1)!} \vert \omega_{n+1}(x) \vert $$

* * *

当 $ f(x) $ 为次数不超过 $ n $ 的多项式时，由于 $ f^{(n+1)}(x) = 0 $ ，于是

$$ R_n(x) = f(x) - \sum_{i=0}^n f(x_i) l_i(x) = 0 $$

从而

$$ f(x) = \sum_{i=0}^n f(x_i) l_i(x) = L_n(x) $$

特别地，当 $ f(x) = 1 $ 时，有

$$ \sum_{i=0}^n l_i(x) = 1 $$

* * *

[上一级](./../index.html)

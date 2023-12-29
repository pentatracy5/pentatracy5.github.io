---
layout: default
title: 多项式求值的秦九韶算法
---

$$
\begin{cases}
p(x) = b_{n} + ( x - x^* )q(x), \quad p( x^* ) = b_{n}\\
p'(x) = q(x) + ( x - x^* )q'(x), \quad p'( x^* ) = q( x^* )\\
p''(x) = 2q'(x) + ( x - x^* )q''(x), \quad p''( x^* ) = 2q'( x^* )\\
p'''(x) = 3q''(x) + ( x - x^* )q'''(x), \quad p'''( x^* ) = 3q''( x^* )\\
...\\
p^{(n)}(x) = nq^{(n-1)}(x) + ( x - x^* )q^{(n)}(x), \quad p^{(n)}( x^* ) = nq^{(n-1)}( x^* )
\end{cases}
$$

[上一级](./../index.html)

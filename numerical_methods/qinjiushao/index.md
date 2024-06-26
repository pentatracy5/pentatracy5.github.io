---
layout: default
title: 多项式求值的秦九韶算法
---

设给定 $ n $ 次多项式

$$ p(x) = a_{0} x^{n} + a_{1} x^{n-1} + ... + a_{n-1} x + a_{n}, a_0 \neq 0 $$

求 $ x^* $ 处的值 $ p( x^* ) $ 。

若直接计算每一项 $ a_{i} x^{n-i} $ 再相加，共需进行 $ O(n^2) $ 次四则运算。

若采用

$$ p(x) = (...(a_{0} x + a_{1})x + ... + a_{n-1})x + a_{n} $$

且记

$$
    \begin{cases}
        b_0 = a_0\\
        b_{i} = b_{i-1} x^* + a_{i}, i = 1, 2, ... , n
    \end{cases}
$$

则 $ b_{n} = p( x^* ) $ 即为所求，且只需进行 $ O(n) $ 次四则运算。此算法称为**秦九韶算法**。
* * *
秦九韶算法的另一个好处是求 $ p'(x) $ 在 $ x^* $ 点的值。令

$$ q(x) = b_{0} x^{n-1} + b_{1} x^{n-2} + ... + b_{n-2} x + b_{n-1} $$

则有

$$ p(x) = b_{n} + ( x - x^* )q(x) $$

对 $ x $ 求导得

$$ p'(x) = q(x) + ( x - x^* )q'(x) $$

故 $ p'( x^* ) = q( x^* ) $ 。再次用秦九韶算法计算 $ q( x^* ) $ 有

$$
    \begin{cases}
        c_0 = b_0\\
        c_{i} = c_{i-1} x^* + b_{i}, i = 1, 2, ... , n-1
    \end{cases}
$$

从而有 $ c_{n-1} = q( x^* ) = p'( x^* ) $ 。
* * *
进一步地，令

$$ r(x) = c_{0} x^{n-2} + c_{1} x^{n-3} + ... + c_{n-3} x + c_{n-2} $$

再用秦九韶算法计算得

$$
    \begin{cases}
        d_0 = c_0\\
        d_{i} = d_{i-1} x^* + c_{i}, i = 1, 2, ... , n-2
    \end{cases}
$$

然后我们又可以利用 $ d_{i}, i = 0, 1, ... , n-3 $ 构造 $ n-3 $ 次多项式，并且继续用秦九韶算法计算得到新的数列，反复继续下去可得到

$$ p(x) = a_{0} x^{n} + a_{1} x^{n-1} + ... + a_{n-1} x + a_{n} $$

$$ q(x) = b_{0} x^{n-1} + b_{1} x^{n-2} + ... + b_{n-2} x + b_{n-1} $$

$$ r(x) = c_{0} x^{n-2} + c_{1} x^{n-3} + ... + c_{n-3} x + c_{n-2} $$

$$ s(x) = d_{0} x^{n-3} + d_{1} x^{n-4} + ... + d_{n-4} x + d_{n-3} $$

$$ t(x) = e_{0} x^{n-4} + e_{1} x^{n-5} + ... + e_{n-5} x + e_{n-4} $$

$$ ... $$

$$ z(x) = k_{0} $$

利用这 $n+1$ 个多项式，我们可以得到 $ p(x) $ 在 $ x^* $ 处的任意阶导数值，推导过程如下： 

若计算这 $n+1$ 个多项式在 $ x^* $ 处的各阶导数，则由上文的推导过程可得

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

$$
    \begin{cases}
        q(x) = c_{n-1} + ( x - x^* )r(x), \quad q( x^* ) = c_{n-1}\\
        q'(x) = r(x) + ( x - x^* )r'(x), \quad q'( x^* ) = r( x^* )\\
        q''(x) = 2r'(x) + ( x - x^* )r''(x), \quad q''( x^* ) = 2r'( x^* )\\
        q'''(x) = 3r''(x) + ( x - x^* )r'''(x), \quad q'''( x^* ) = 3r''( x^* )\\
        ...\\
        q^{(n-1)}(x) = (n-1)r^{(n-2)}(x) + ( x - x^* )r^{(n-1)}(x), \quad q^{(n-1)}( x^* ) = (n-1)r^{(n-2)}( x^* )
    \end{cases}
$$

$$
    \begin{cases}
        r(x) = d_{n-2} + ( x - x^* )s(x), \quad r( x^* ) = d_{n-2}\\
        r'(x) = s(x) + ( x - x^* )s'(x), \quad r'( x^* ) = s( x^* )\\
        r''(x) = 2s'(x) + ( x - x^* )s''(x), \quad r''( x^* ) = 2s'( x^* )\\
        r'''(x) = 3s''(x) + ( x - x^* )s'''(x), \quad r'''( x^* ) = 3s''( x^* )\\
        ...\\
        r^{(n-2)}(x) = (n-2)s^{(n-3)}(x) + ( x - x^* )s^{(n-2)}(x), \quad r^{(n-2)}( x^* ) = (n-2)s^{(n-3)}( x^* )
    \end{cases}
$$

$$ ... $$

$$
    \begin{cases}
        z(x) = k_{0}, \quad z( x^* ) = k_{0}
    \end{cases}
$$

从而

$$
    \begin{cases}
        p( x^* ) = b_{n}\\
        p'( x^* ) = 1!q( x^* ) = c_{n-1}\\
        p''( x^* ) = 2q'( x^* ) = 2!r( x^* ) = 2d_{n-2}\\
        p'''( x^* ) = 3q''( x^* ) = 3[2r'( x^* )] = 3!s( x^* ) = 6e_{n-3}\\
        ...\\
        p^{(n)}( x^* ) = nq^{(n-1)}( x^* ) = n[(n-1)r^{(n-2)}( x^* )] = n(n-1)[(n-2)s^{(n-3)}( x^* )] = ... = n!z( x^* ) = n!k_{0}
    \end{cases}
$$

* * *
秦九韶算法的C++实现
```C++
#include <vector>
using std::vector;
    
float Qinjiushao(const vector<float>& a, float x)
{
    float result = 0.f;
    for(auto ai : a)
    {
        result = result * x + ai;
    }
    return result;
}
```
* * *

[上一级](./../index.html)

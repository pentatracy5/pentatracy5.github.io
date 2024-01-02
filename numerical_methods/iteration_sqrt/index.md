---
layout: default
title: 迭代法与开方求值
---

**迭代法**是一种按同一公式重复计算逐次逼近真值的算法。

* * *

假定 $ a>0 $ ，求 $ \sqrt a $ 。

可利用迭代公式

$$ x_{k+1} = \frac {1} {2} (x_{k} + \frac {a} {x_{k}}), k = 0, 1, ... $$

* * *

如何证明数列 $ x_{k} $ 收敛到 $ \sqrt a $ ？？？

如果知道收敛，则易知极限是 $ \sqrt a $。目前还不知道如何根据数列的递推公式证明其收敛。

一种证明数列收敛的方法是，将其看成用牛顿法求解 $ F(x) = x^2 - a $ 的根的迭代过程的结果，然后证明 $ F(x) $ 满足牛顿法的收敛条件，从而 $ x_{k} $ 收敛。

* * *

开方求值迭代算法的C++实现
```C++   
float sqrt(float a, float x0, unsigned int iterNum)
{
    for(unsigned int i = 0; i < iterNum; i++)
    {
        x0 = 0.5f * (x0 + a / x0);
    }
    return x0;
}
```

* * *

[上一级](./../index.html)

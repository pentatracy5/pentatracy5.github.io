---
layout: default
title: 数值计算的误差
---

定义：数学模型与实际问题之间出现的误差称为**模型误差**。（不关注）

* * *

定义：由观测产生的误差称为**测量误差**。（不关注）

* * *

定义：用数值方法求得的数学模型的近似解与模型精确解之间的误差称为**截断误差**或**方法误差**。（关注）

* * *

定义：原始数据在计算机上表示时会产生误差，计算过程又可能产生新的误差，这种误差称为**舍入误差**。（关注）

* * *

定义：设 $ x $ 为准确值， $ x^* $ 为 $ x $ 的一个近似值，称 $ e^* = x^* - x $ 为近似值的**绝对误差**，简称**误差**。

* * *

定义：误差绝对值的一个上界 $ \varepsilon^* $ 叫做近似值的**误差限**。

* * *

定义：近似值的误差 $ e^* $ 与准确值 $ x $ 的比值

$$ \frac { e^* } { x } = \frac { x^* - x } { x } $$

称为近似值 $ x^* $ 的**相对误差**，记作 $ e_r^* $ 。

* * *

在实际计算中，由于真值 $ x $ 总是不知道的，通常取

$$ e_r^* = \frac { e^* } { x^* } = \frac { x^* - x } { x^* } $$

条件是 $ e_r^* = \frac { e^* } { x^* } $ 较小，此时

$$ \frac { e^* } { x } - \frac { e^* } { x^* } = \frac { (\frac { e^* } { x^* })^2 } { 1 - \frac { e^* } { x^* } } $$

是 $ e_r^* $ 的平方项级，故可忽略不计。

* * *

定义：相对误差的绝对值上界叫做**相对误差限**，记做 $ \varepsilon_r^* $ ，即 $ \varepsilon_r^* = \frac { \varepsilon^* } { \vert x^* \vert } $

* * *

定义：若近似值 $ x^* $ 的误差限是某一位的半个单位，该位到 $ x^* $ 的第一个非零数字共有 $ n $ 位，就说 $ x^* $ 有 $ n $ 位**有效数字**。它可表示为

$$ x^* = \pm 10^m * (a_1 + a_2 * 10^{-1} + ... + a_n * 10^{-(n-1)}) $$

其中 $ a_i(i = 1, 2, ... , n) $ 是0到9中的一个数字， $ a_1 \neq 0 $ ， $ m $ 为整数，且

$$ | x - x^* | \leqslant \frac 1 2 * 10^{m - n + 1} $$

* * *

定理：设近似数 $ x^* $ 表示为

$$ x^* = \pm 10^m * (a_1 + a_2 * 10^{-1} + ... + a_l * 10^{-(l-1)}) $$

其中 $ a_i(i = 1, 2, ... , l) $ 是0到9中的一个数字， $ a_1 \neq 0 $ ， $ m $ 为整数。若 $ x^* $ 具有 $ n $ 位有效数字，则其相对误差限

$$ \varepsilon_r^* \leqslant \frac 1 {2a_1} * 10^{- (n - 1)} $$

反之，若 $ x^* $ 的相对误差限

$$ \varepsilon_r^* \leqslant \frac 1 {2(a_1 + 1)} * 10^{- (n - 1)} $$

则 $ x^* $ 至少具有 $ n $ 位有效数字。

* * *

设两个近似数 $ x_1^* $和$ x_2^* $ 的误差限分别为 $ \varepsilon ( x_1^* ) $ 和 $ \varepsilon ( x_2^* ) $ ， $ x_2^* $ 的相对误差限为 $ \varepsilon_r ( x_2^* ) $ ，则它们进行加减乘除运算得到的误差限分别满足不等式

$$ \varepsilon ( x_1^* \pm x_2^* ) \leqslant \varepsilon ( x_1^* ) + \varepsilon ( x_2^* ) $$

$$ \varepsilon ( x_1^* x_2^* ) \leqslant | x_1^* | \varepsilon ( x_2^* ) + | x_2^* | \varepsilon ( x_1^* ) + \varepsilon ( x_1^* ) \varepsilon ( x_2^* ) $$

$$ \varepsilon ( \frac { x_1^* } { x_2^* } ) \leqslant \frac {| x_1^* | \varepsilon ( x_2^* ) + | x_2^* | \varepsilon ( x_1^* )} { { | x_2^* | }^2 } \frac {1} { 1 - \varepsilon_r ( x_2^* ) }, x_2 \neq 0, x_2^* \neq 0, \varepsilon_r ( x_2^* ) < 1 $$

由所得的误差限可得，相对误差限分别满足不等式

$$ \varepsilon_r ( x_1^* \pm x_2^* ) \leqslant \frac {\varepsilon ( x_1^* ) + \varepsilon ( x_2^* )} {| x_1^* + x_2^* |} $$

$$ \varepsilon_r ( x_1^* x_2^* ) \leqslant \varepsilon_r ( x_1^* ) + \varepsilon_r ( x_2^* ) + \varepsilon_r ( x_1^* ) \varepsilon_r ( x_2^* ) $$

$$ \varepsilon_r ( \frac { x_1^* } { x_2^* } ) \leqslant \frac {\varepsilon_r ( x_1^* ) + \varepsilon_r ( x_2^* )} { 1 - \varepsilon_r ( x_2^* ) } $$

在实践中，当近似值足够好的时候，有

$$ \varepsilon ( x_1^* ) \varepsilon ( x_2^* ) \approx 0 $$

$$ \varepsilon_r ( x_1^* ) \varepsilon_r ( x_2^* ) \approx 0 $$

$$ 1 - \varepsilon_r ( x_2^* ) \approx 1 $$

从而有

$$ \varepsilon ( x_1^* x_2^* ) \leqslant | x_1^* | \varepsilon ( x_2^* ) + | x_2^* | \varepsilon ( x_1^* ) $$

$$ \varepsilon ( \frac { x_1^* } { x_2^* } ) \leqslant \frac {| x_1^* | \varepsilon ( x_2^* ) + | x_2^* | \varepsilon ( x_1^* )} { { | x_2^* | }^2 } $$

$$ \varepsilon_r ( x_1^* x_2^* ) \leqslant \varepsilon_r ( x_1^* ) + \varepsilon_r ( x_2^* ) $$

$$ \varepsilon_r ( \frac { x_1^* } { x_2^* } ) \leqslant \varepsilon_r ( x_1^* ) + \varepsilon_r ( x_2^* ) $$

* * *

设 $ f(x) $ 是一元可微函数， $ x $ 的近似值为 $ x^* $ ，以 $ f( x^* ) $ 近似 $ f(x) $ ，其误差界记做 $ \varepsilon (f( x^* )) $ 。由泰勒展开有

$$ | f(x) - f( x^* ) | \leqslant | f'( x^* ) | \varepsilon( x^* ) + \frac { | f''( \xi ) | } {2} { \varepsilon ( x^* ) }^2, \xi 介于 x 与 x^* 之间 $$

假定 $ \frac { \lvert f''( \xi ) \rvert } {2} { \varepsilon ( x^* ) }^2 $ 可忽略，则

$$ \varepsilon (f( x^* )) \approx | f'( x^* ) | \varepsilon ( x^* ) $$

当 $ f $ 为多元函数时，例如计算 $ A = f(x_1, x_2, ..., x_n) $ 。如果 $ x_1, x_2, ..., x_n $ 的近似值为 $ x_1^* , x_2^* , ..., x_n^* $ ，则 $ A $ 的近似值为 $ A^* = f( x_1^* , x_2^* , ..., x_n^* ) $ 。由泰勒展开得函数值 $ A^* $ 的误差限

$$ \varepsilon ( A^* ) \approx \sum_{k=1}^{n} | \frac { \partial f( x_1^* , x_2^* , ..., x_n^* ) } { \partial x_k } | \varepsilon ( x_k^* ) $$

$ A^* $ 的相对误差限

$$ \varepsilon_r ( A^* ) \approx \sum_{k=1}^{n} | \frac { \partial f( x_1^* , x_2^* , ..., x_n^* ) } { \partial x_k } | \frac { \varepsilon ( x_k^* ) } { | A^* | } $$

* * *

定义：一个算法如果输入数据有误差，而在计算过程中舍入误差不增长，则称此算法是**数值稳定**的；否则称此算法为**不稳定**的。

* * *

定义：对一个数值问题本身如果输入数据有微小扰动（即误差），引起输出数据（即问题解）相对误差很大，这就是**病态问题**。

* * *

定义：计算函数值 $ f(x) $ 时，若 $ x $ 有扰动 $ \Delta x = x - x^* $ ，其相对误差为 $ \frac { \Delta x } { x } $ ，函数值 $ f( x^* ) $ 的相对误差为 $ \frac { f(x) - f( x^* ) } { f(x) } $ 。相对误差比值

$$ \frac { | \frac { f(x) - f( x^* ) } { f(x) } | } { | \frac { \Delta x } { x } | } \approx | \frac { xf'(x) } { f(x) } | = C_p $$

$ C_p $ 称为**计算函数值问题的条件数**。

* * *

自变量相对误差一般不会太大，如果条件数 $ C_p $ 很大，将引起函数值相对误差很大，出现这种情况的问题就是病态问题。

* * *

病态问题不是计算方法引起的，是数值问题本身固有的。

* * *

设计数值算法时，应尽量避免误差危害，防止有效数字损失，通常要**避免两相近数相减**和**用绝对值很小的数做除数**，还要注意**运算次序**和**减少运算次数**。

* * *

[上一级](./../index.html)

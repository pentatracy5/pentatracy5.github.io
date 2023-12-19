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

<center>$ \frac { e^* } { x } = \frac { x^* - x } { x } $</center>

称为近似值 $ x^* $ 的**相对误差**，记作 $ e_r^* $ 。
* * *
在实际计算中，由于真值 $ x $ 总是不知道的，通常取

<center>$ e_r^* = \frac { e^* } { x^* } = \frac { x^* - x } { x^* } $</center>

条件是 $ e_r^* = \frac { e^* } { x^* } $ 较小，此时

<center>$ \frac { e^* } { x } - \frac { e^* } { x^* } = \frac { (\frac { e^* } { x^* })^2 } { 1 - \frac { e^* } { x^* } } $</center>

是 $ e_r^* $ 的平方项级，故可忽略不计。
* * *
定义：相对误差的绝对值上界叫做**相对误差限**，记做 $ \varepsilon_r^* $，即 $ \varepsilon_r^* = \frac { \varepsilon^* } { | x^* | } $
* * *
定义：若近似值 $ x^* $ 的误差限是某一位的半个单位，该位到 $ x^* $ 的第一个非零数字共有 $ n $ 位，就说 $ x^* $ 有 $ n $ 位**有效数字**。它可表示为

<center>$ x^* = \pm 10^m * (a_1 + a_2 * 10^{-1} + ... + a_n * 10^{-(n-1)}) $</center>

其中 $ a_i(i = 1, 2, ... , n) $ 是0到9中的一个数字， $ a_1 \neq 0 $ ， $ m $ 为整数，且

<center>$ | x - x^* | \leqslant \frac 1 2 * 10^{m - n + 1} $</center>
* * *
定理：设近似数 $ x^* $ 表示为

<center>$ x^* = \pm 10^m * (a_1 + a_2 * 10^{-1} + ... + a_l * 10^{-(l-1)}) $</center>

其中 $ a_i(i = 1, 2, ... , l) $ 是0到9中的一个数字， $ a_1 \neq 0 $ ， $ m $ 为整数。若 $ x^* $ 具有 $ n $ 位有效数字，则其相对误差限

<center>$ \varepsilon_r^* \leqslant \frac 1 {2a_1} * 10^{- (n - 1)} $</center>

反之，若 $ x^* $ 的相对误差限

<center>$ \varepsilon_r^* \leqslant \frac 1 {2(a_1 + 1)} * 10^{- (n - 1)} $</center>

则 $ x^* $ 至少具有 $ n $ 位有效数字。
* * *
设两个近似数 $ x_1^* $和$ x_2^* $ 的误差限分别为 $ \varepsilon ( x_1^* ) $ 和 $ \varepsilon ( x_2^* ) $ ， $ x_2^* $ 的相对误差限为 $ \varepsilon_r ( x_2^* ) $ ，则它们进行加减乘除运算得到的误差限分别满足不等式

<center>$ \varepsilon ( x_1^* \pm x_2^* ) \leqslant \varepsilon ( x_1^* ) + \varepsilon ( x_2^* ) $</center>

<center>$ \varepsilon ( x_1^* x_2^* ) \leqslant | x_1^* | \varepsilon ( x_2^* ) + | x_2^* | \varepsilon ( x_1^* ) + \varepsilon ( x_1^* ) \varepsilon ( x_2^* ) $</center>

<center>$ \varepsilon ( \frac { x_1^* } { x_2^* } ) \leqslant \frac {| x_1^* | \varepsilon ( x_2^* ) + | x_2^* | \varepsilon ( x_1^* )} { { | x_2^* | }^2 } \frac {1} { 1 - \varepsilon_r ( x_2^* ) }, x_2 \neq 0, x_2^* \neq 0, \varepsilon_r ( x_2^* ) < 1 $</center>

由所得的误差限可得，相对误差限分别满足不等式

<center>$ \varepsilon_r ( x_1^* \pm x_2^* ) \leqslant \frac {\varepsilon ( x_1^* ) + \varepsilon ( x_2^* )} {| x_1^* + x_2^* |} $</center>

<center>$ \varepsilon_r ( x_1^* x_2^* ) \leqslant \varepsilon_r ( x_1^* ) + \varepsilon_r ( x_2^* ) + \varepsilon_r ( x_1^* ) \varepsilon_r ( x_2^* ) $</center>

<center>$ \varepsilon_r ( \frac { x_1^* } { x_2^* } ) \leqslant \frac {\varepsilon_r ( x_1^* ) + \varepsilon_r ( x_2^* )} { 1 - \varepsilon_r ( x_2^* ) } $</center>

在实践中，当近似值足够好的时候，有

<center>$ \varepsilon ( x_1^* ) \varepsilon ( x_2^* ) \approx 0 $</center>

<center>$ \varepsilon_r ( x_1^* ) \varepsilon_r ( x_2^* ) \approx 0 $</center>

<center>$ 1 - \varepsilon_r ( x_2^* ) \approx 1 $</center>

从而有

<center>$ \varepsilon ( x_1^* x_2^* ) \leqslant | x_1^* | \varepsilon ( x_2^* ) + | x_2^* | \varepsilon ( x_1^* ) $</center>

<center>$ \varepsilon ( \frac { x_1^* } { x_2^* } ) \leqslant \frac {| x_1^* | \varepsilon ( x_2^* ) + | x_2^* | \varepsilon ( x_1^* )} { { | x_2^* | }^2 } $</center>

<center>$ \varepsilon_r ( x_1^* x_2^* ) \leqslant \varepsilon_r ( x_1^* ) + \varepsilon_r ( x_2^* ) $</center>

<center>$ \varepsilon_r ( \frac { x_1^* } { x_2^* } ) \leqslant \varepsilon_r ( x_1^* ) + \varepsilon_r ( x_2^* ) $</center>
* * *
设 $ f(x) $ 是一元可微函数， $ x $ 的近似值为 $ x^* $ ，以 $ f( x^* ) $ 近似 $ f(x) $ ，其误差界记做 $ \varepsilon (f( x^* )) $ 。由泰勒展开有

<center>$ | f(x) - f( x^* ) | \leqslant | f'( x^* ) | \varepsilon( x^* ) + \frac { | f''( \xi ) | } {2} { \varepsilon ( x^* ) }^2, \xi 介于 x 与 x^* 之间 $</center>

假定 $ \frac { \lvert f''( \xi ) \rvert } {2} { \varepsilon ( x^* ) }^2 $ 可忽略，则

<center>$ \varepsilon (f( x^* )) \approx | f'( x^* ) | \varepsilon ( x^* ) $</center>

当 $ f $ 为多元函数时，例如计算 $ A = f(x_1, x_2, ..., x_n) $ 。如果 $ x_1, x_2, ..., x_n $ 的近似值为 $ x_1^* , x_2^* , ..., x_n^* $ ，则 $ A $ 的近似值为 $ A^* = f( x_1^* , x_2^* , ..., x_n^* ) $ 。由泰勒展开得函数值 $ A^* $ 的误差限

<center>$ \varepsilon ( A^* ) \approx \sum_{k=1}^{n} | \frac { \partial f( x_1^* , x_2^* , ..., x_n^* ) } { \partial x_k } | \varepsilon ( x_k^* ) $</center>

$ A^* $ 的相对误差限

<center>$ \varepsilon_r ( A^* ) \approx \sum_{k=1}^{n} | \frac { \partial f( x_1^* , x_2^* , ..., x_n^* ) } { \partial x_k } | \frac { \varepsilon ( x_k^* ) } { | A^* | } $</center>
* * *

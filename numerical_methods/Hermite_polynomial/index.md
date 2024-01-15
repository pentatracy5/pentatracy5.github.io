---
layout: default
title: 埃尔米特插值
---

定义：插值多项式要求在插值节点上函数值相等，有的实际问题还要求在节点上导数值相等，甚至高阶导数值也相等，满足这种要求的插值多项式称为**埃尔米特插值多项式**。

* * *

定理：设 $ f \in C^n [a, b] $ ， $ x_0, x_1, ... , x_n $ 为 $ [a, b] $ 上的相异节点，则 $ f[x_0, x_1, ... , x_n] $ 是其变量的连续函数。（连续函数经过四则运算还是连续函数）

* * *

定理：设 $ f \in C^n [a, b] $ ， $ x_0, x_1, ... , x_n $ 为 $ [a, b] $ 上的节点，则

$$
\lim \limits_{y_i \rightarrow x_i (i = 0, 1, ... , n)} f[y_0, y_1, ... , y_n]
$$

存在。

证明：若 $ x_0, x_1, ... , x_n $ 相异，则结论显然成立。

当存在相同节点时，应用数学归纳法。

当 $ n = 1 $ 时，有

$$
\lim \limits_{y_i \rightarrow x_0 (i = 0, 1)} f[y_0, y_1] = \lim \limits_{y_i \rightarrow x_0 (i = 0, 1)} \frac {f(y_0) - f(y_1)} {y_0 - y_1} = f'(x_0)
$$

假设结论对 $ n = k - 1 $ 的情况成立，当 $ n = k $ 时，分两种情况

若存在相异节点 $ x_p \neq x_q $，则 

$$
\lim \limits_{y_i \rightarrow x_i (i = 0, 1, ... , k)} f[y_0, y_1, ... , y_k] = \lim \limits_{y_i \rightarrow x_i (i = 0, 1, ... , k)} \frac {f[y_0, ... , y_{q-1}, y_{q+1}, ... , y_k] - f[y_0, ... , y_{p-1}, y_{p+1}, ... , y_k]} {y_p - y_q}
$$

由归纳假设结论成立；

若不存在相异节点，则由均差与导数的关系有

$$
\lim \limits_{y_i \rightarrow x_0 (i = 0, 1, ... , k)} f[y_0, y_1, ... , y_k] = \lim \limits_{y_i \rightarrow x_0 (i = 1, 2, ... , k)(\xi \in (y_0, y_k))} \frac {f^{(k)}(\xi)} {n!} = \frac {f^{(k)}(x_0)} {n!}
$$

结论成立。得证。

* * *

我们可以将 $ f[x_0, x_1, ... , x_n] $ 定义到 $ [a, b] $ 上的任意一组节点（而不仅限于相异节点）

$$
f[x_0, x_1, ... , x_n] \stackrel {\Delta} {=} \lim \limits_{y_i \rightarrow x_i (i = 1, 2, ... , n)} f[y_0, y_1, ... , y_n]
$$

并且这样定义的 $ f[x_0, x_1, ... , x_n] $ 是其变量的连续函数。(处处连续)

* * *

定义：在牛顿均差插值多项式中，令 $ x_i \rightarrow x_0 (i = 1, 2, ... , n) $ ，则有

$$
\lim \limits_{x_i \rightarrow x_0 (i = 1, 2, ... , n)} P_n(x) = f(x_0) + f'(x_0) (x - x_0) + ... + \frac {f^{(n)}(x_0)} {n!} (x - x_0)^n
$$

它实际上是在点 $ x_0 $ 附近逼近 $ f(x) $ 的一个带导数的插值多项式，它满足条件

$$
P_n^k(x_0) = f^{(k)}(x_0), k = 0, 1, ... , n
$$

称为**泰勒插值多项式**。

* * *

泰勒插值多项式的余项即为 $ f(x) $ 在 $ x_0 $ 处做泰勒展开的拉格朗日余项

$$
R_n(x) = \frac {f^{(n+1)}(\xi)} {(n + 1)!} (x - x_0)^{n+1}, \xi \in (a, b)
$$

它与令 $ x_i \rightarrow x_0 (i = 1, 2, ... , n) $ 时 $ R_n(x) $ [...]的结果一致？？？

实际上泰勒插值是牛顿插值的极限形式，也是只在一点 $ x_0 $ 处给出 $ n + 1 $ 个插值条件的 $ n $ 次埃尔米特插值多项式。

* * *

一种典型的埃尔米特插值：考虑满足条件 $ P(x_i) = f(x_i), (i = 0, 1, 2), P'(x_1) = f'(x_1) $ 的插值多项式。

假定插值多项式次数不超过3，根据其通过点 $ (x_0, f(x_0)), (x_1, f(x_1)), (x_2, f(x_2)) $ ，可设其形式为

$$
P(x) = f(x_0) + f[x_0, x_1](x - x_0) + f[x_0, x_1, x_2](x - x_0)(x - x_1) + A(x - x_0)(x - x_1)(x - x_2)
$$

其中 $ A $ 为待定常数，可由条件 $ P'(x_1) = f'(x_1) $ 计算得到

$$
A = \frac {f'(x_1) - f[x_0, x_1] - (x_1 - x_0)f[x_0, x_1, x_2]} {(x_1 - x_0)(x_1 - x_2)}
$$

类似于之前余项的推导，可设余项形式为

$$
R(x) = k(x) (x - x_0) (x - x_1)^2 (x - x_2)
$$

其中 $ k(x) $ 为待定函数，构造

$$
\varphi(t) = f(t) - P(t) - k(x) (t - x_0) (t - x_1)^2 (t - x_2)
$$

则由插值条件可知 $ \varphi(x_i) = 0, (i = 0, 1, 2), \varphi(x) = 0, \varphi'(x_1) = 0 $ ，故 $ \varphi(t) $ 在 $ (a, b) $ 内有5个零点（二重根算两个）。假设 $ f(x) $ 高阶导数存在，反复应用罗尔定理可知 $ \varphi^{(4)}(t) $ 在 $ (a, b) $ 内至少有一个零点 $ \xi $ ，故

$$
\varphi^{(4)}(\xi) = f^{(4)}(\xi) - 4! k(x) = 0
$$

式中 $ \xi $ 位于 $ x, x_0, x_1, x_2 $ 所界定的范围内。

* * *

另一种典型的埃尔米特插值：两点三次埃尔米特插值。插值节点取为 $ x_k, x_{k+1} $ ，插值多项式记为 $ H_3(x) $ ，满足条件

$$
\begin{cases}
    H_3(x_k) = y_k \\
    H_3(x_{k+1}) = y_{k+1} \\
    H_3'(x_k) = m_k \\
    H_3'(x_{k+1}) = m_{k+1}
\end{cases}
$$

采用基函数法，令

$$
H_3(x) = \alpha_k(x) y_k + \alpha_{k+1}(x) y_{k+1} + \beta_k(x) m_k + \beta_{k+1}(x) m_{k+1}
$$

其中 $ \alpha_k(x), \alpha_{k+1}(x), \beta_k(x), \beta_{k+1}(x) $ 是关于节点 $ x_k, x_{k+1} $ 的三次埃尔米特插值基函数，它们分别满足条件

$$
\alpha_k(x_k) = 1 \quad \alpha_k(x_{k+1}) = 0 \quad \alpha_k'(x_k) = 0 \quad \alpha_k'(x_{k+1}) = 0 \\
\alpha_{k+1}(x_k) = 0 \quad \alpha_{k+1}(x_{k+1}) = 1 \quad \alpha_{k+1}'(x_k) = 0 \quad \alpha_{k+1}'(x_{k+1}) = 0 \\
\beta_k(x_k) = 0 \quad \beta_k(x_{k+1}) = 0 \quad \beta_k'(x_k) = 1 \quad \beta_k'(x_{k+1}) = 0 \\
\beta_{k+1}(x_k) = 0 \quad \beta_{k+1}(x_{k+1}) = 0 \quad \beta_{k+1}'(x_k) = 0 \quad \beta_{k+1}'(x_{k+1}) = 1
$$

根据给定条件可令

$$
\alpha_k(x) = (ax + b) (x - x_{k+1})^2
$$

显然

$$
\alpha_k(x_{k+1}) = 0 \quad \alpha_k'(x_{k+1}) = 0 
$$

再利用

$$
\alpha_k(x_k) = (a x_k + b) (x_k - x_{k+1})^2 = 1 \quad \alpha_k'(x_k) = a (x_k - x_{k+1})^2 + 2(a x_k + b) (x_k - x_{k+1}) = 0
$$

解得

$$
a = \frac {2} {(x_{k+1} - x_k)^3} \quad b = \frac {x_{k+1} - 3x_k} {(x_{k+1} - x_k)^3}
$$

于是求得

$$
\alpha_k(x) = \frac {(2x + x_{k+1} - 3x_k) (x - x_{k+1})^2} {(x_{k+1} - x_k)^3}
$$

同理可求得

$$
\alpha_{k+1}(x) = \frac {(2x + x_k - 3x_{k+1}) (x - x_k)^2} {(x_k - x_{k+1})^3}
$$

为求 $ \beta_k(x) $ ，由给定条件可令

$$
\beta_k(x) = a(x - x_k) (x - x_{k+1})^2
$$

直接由 $ \beta_k'(x_k) = a(x_k - x_{k+1})^2 = 1 $ 得到

$$
\beta_k(x) = \frac {(x - x_k) (x - x_{k+1})^2} {(x_k - x_{k+1})^2}
$$

同理有

$$
\beta_{k+1}(x) = \frac {(x - x_{k+1}) (x - x_k)^2} {(x_{k+1} - x_k)^2}
$$

类似地，其余项

$$
R_3(x) = f(x) - H_3(x) = \frac {f^{(4)}(\xi)} {4!} (x - x_k)^2 (x - x_{k+1})^2, \xi \in (x_k, x_{k+1})
$$

* * *

一般地，只要给出 $ m + 1 $ 个插值条件（含函数值和导数值）就可构造出次数不超过 $ m $ 次的埃尔米特插值多项式。常规的构造方式可以采用设定基函数，然后根据插值条件计算基函数中的待定系数（一定有解，至于怎么证明一定有解，暂时还没推，推导过程应该比较琐碎？？？）。这种方法说明了次数不超过 $ m $ 次的埃尔米特插值多项式的存在性。

埃尔米特插值多项式的余项是 $ f^{(m+1)}(\xi) $ 乘以一个 $ x $ 的多项式， $ \xi $ 依赖于插值节点和 $ x $ 。假设存在两个次数不超过 $ m $ 次的埃尔米特插值多项式，则可将其中一个多项式视为 $ f(x) $ ，另一个多项式视为 $ f(x) $ 的埃尔米特插值多项式。由于 $ f(x) $ 次数为 $ m $ ，故 $ f^{(m+1)}(x) = 0 $ ，从而余项恒为0，即两个插值多项式相等，这说明了次数不超过 $ m $ 次的埃尔米特插值多项式的唯一性。

* * *

两种典型的埃尔米特插值的C++实现
```C++   
#include <vector>
using std::vector;

class Three_points_Hermite_polynomial
{
public:
	Three_points_Hermite_polynomial(const vector<float>& x, const vector<float>& y, float dy1)
	{
		x_ = x;
		y_ = y;
		dy1_ = dy1;
		A_.resize(4);
		A_[0] = y_[0];
		A_[1] = (y_[0] - y_[1]) / (x_[0] - x_[1]);
		float temp = (y_[1] - y_[2]) / (x_[1] - x_[2]);
		A_[2] = (A_[1] - temp) / (x_[0] - x_[2]);
		A_[3] = (dy1_ - A_[1] - (x_[1] - x_[0]) * A_[2]) / ((x_[1] - x_[0]) * (x_[1] - x_[2]));
	}

	virtual ~Three_points_Hermite_polynomial()
	{

	}

	virtual void Set_interpolation_nodes(const vector<float>& x, const vector<float>& y, float dy1)
	{
		x_ = x;
		y_ = y;
		dy1_ = dy1;
		A_.resize(4);
		A_[0] = y_[0];
		A_[1] = (y_[0] - y_[1]) / (x_[0] - x_[1]);
		float temp = (y_[1] - y_[2]) / (x_[1] - x_[2]);
		A_[2] = (A_[1] - temp) / (x_[0] - x_[2]);
		A_[3] = (dy1_ - A_[1] - (x_[1] - x_[0]) * A_[2]) / ((x_[1] - x_[0]) * (x_[1] - x_[2]));
	}

	virtual float Eval(float x)
	{
		float H_3 = A_[0];
		float omega = 1.f;
		for (size_t i = 1; i <= 3; i++)
		{
			omega *= (x - x_[i - 1]);
			H_3 += A_[i] * omega;
		}
		return H_3;
	}

private:
	vector<float> x_;
	vector<float> y_;
	float dy1_;
	vector<float> A_;
}

class Two_points_Hermimte_polynomial
{
public:
	Two_points_Hermimte_polynomial(const vector<float>& x, const vector<float>& y, const vector<float>& dy)
	{
		x_ = x;
		y_ = y;
		dy_ = dy;
	}

	virtual ~Two_points_Hermimte_polynomial()
	{

	}

	virtual void Set_interpolation_nodes(const vector<float>& x, const vector<float>& y, const vector<float>& dy)
	{
		x_ = x;
		y_ = y;
		dy_ = dy;
	}

	virtual float Eval(float x)
	{
		vector<float> alpha(2);
		vector<float> beta(2);
		float deltaX = x_[1] - x_[0];
		float temp = deltaX * deltaX;
		beta[0] = (x - x_[0]) * (x - x_[1]) * (x - x_[1]) / temp;
		beta[1] = (x - x_[1]) * (x - x_[0]) * (x - x_[0]) / temp;
		temp *= deltaX;
		alpha[0] = (2.f * x + x_[1] - 3.f * x_[0]) * (x - x_[1]) * (x - x_[1]) / temp;
		alpha[1] = (2.f * x + x_[0] - 3.f * x_[1]) * (x - x_[0]) * (x - x_[0]) / -temp;
		return y_[0] * alpha[0] + y_[1] * alpha[1] + dy_[0] * beta[0] + dy_[1] * beta[1];
	}

private:
	vector<float> x_;
	vector<float> y_;
	vector<float> dy_;
};
```

* * *

[上一级](./../index.html)

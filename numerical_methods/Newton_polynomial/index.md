---
layout: default
title: 牛顿插值
---

定义：称 $ f[x_0, x_1] = \frac {f(x_1) - f(x_0)} {x_1 - x_0} $ 为函数 $ f(x) $ 关于点 $ x_0, x_1 $ 的**一阶均差**。 $ f[x_0, x_1, x_2] = \frac {f[x_0, x_2] - f[x_0, x_1]} {x_2 - x_1} $ 称为 $ f(x) $ 的**二阶均差**。一般地，称

$$
f[x_0, x_1, ... , x_k] = \frac {f[x_0, ... , x_{k-2}, x_k] - f[x_0, x_1, ... , x_{k-1}]} {x_k - x_{k-1}}
$$

为 $ f(x) $ 的 $ k $ **阶均差**（均差也称为**差商**）。

* * *

$ k $ 阶均差可表示为函数值 $ f(x_0), f(x_1), ... , f(x_k) $ 的线性组合，即

$$
f[x_0, x_1, ... , x_k] = \sum_{j=0}^k \frac {f(x_j)} {(x_j - x_0) ... (x_j - x_{j-1})(x_j - x_{j+1}) ... (x_j - x_k)}
$$

可用归纳法证明此性质。该性质表明均差与节点的排列次序无关，称为**均差的对称性**，即

$$
f[x_0, x_1, ... , x_k] = f[x_1, x_0, ... , x_k] = ... = f[x_1, ... , x_k, x_0]
$$

由该性质及均差定义可得

$$
f[x_0, x_1, ... , x_k] = \frac {f[x_1, x_2, ... , x_k] - f[x_0, x_1, ... , x_{k-1}]} {x_k - x_0}
$$

* * *

定义：根据均差定义，将 $ x $ 看成 $ [a, b] $ 上的一点，可得

$$
f(x) = f(x_0) + f[x, x_0] (x - x_0)
$$

$$
f[x, x_0] = f[x_0, x_1] + f[x, x_0, x_1] (x - x_1)
$$

$$
...
$$

$$
f[x, x_0, ... , x_{n-1}] = f[x_0, x_1, ... , x_n] + f[x, x_0, ... , x_n] (x - x_n)
$$

把后一式依次代入前一式可得

$$
f(x) = f(x_0) + f[x_0, x_1] (x - x_0) + f[x_0, x_1, x_2] (x - x_0) (x - x_1) + ... + f[x_0, x_1, ... , x_n] (x - x_0) ... (x - x_{n-1}) + f[x, x_0, ... , x_n] \omega_{n+1}(x)
$$

其中 $ \omega_{n+1}(x) $ 定义见[[拉格朗日插值](./../Lagrange_polynomial/index.html)]。记

$$
P_n(x) = f(x_0) + f[x_0, x_1] (x - x_0) + f[x_0, x_1, x_2] (x - x_0) (x - x_1) + ... + f[x_0, x_1, ... , x_n] (x - x_0) ... (x - x_{n-1})
$$

$$
R_n(x) = f[x, x_0, ... , x_n] \omega_{n+1}(x)
$$

则

$$
f(x) = P_n(x) + R_n(x)
$$

由于 $ R_n(x_i) = 0 (i = 0, 1, ... , n) $ ，从而 $ f(x_i) = P_n(x_i) $ ，故 $ P_n(x) $ 满足插值条件并且次数不超过 $ n $ ，我们称 $ P_n(x) $ 为**牛顿均差插值多项式**。

若记

$$
a_0 = f(x_0)
$$

$$
a_k = f[x_0, x_1, ... , x_k], k = 1, ... , n
$$

则 $ P_n(x) $ 可表示为

$$
P_n(x) = \sum_{k=0}^n a_k \prod_{i=0}^{k-1} (x - x_i)
$$

* * *

与拉格朗日插值不同，牛顿均差插值多项式的基函数是 $ \{1, x - x_0, ... , (x - x_0)...(x - x_{n-1})\} $ 。系数 $ a_k $ 可根据如下均差表逐次递推给出

| $x_k$ | $f(x_k)$ | 一阶均差      | 二阶均差           | 三阶均差                | 四阶均差                     |
| ----- | -------- | ------------- | ------------------ | ----------------------- | ---------------------------- |
| $x_0$ | $f(x_0)$ |               |                    |                         |                              |
| $x_1$ | $f(x_1)$ | $f[x_0, x_1]$ |                    |                         |                              |
| $x_2$ | $f(x_2)$ | $f[x_1, x_2]$ | $f[x_0, x_1, x_2]$ |                         |                              |
| $x_3$ | $f(x_3)$ | $f[x_2, x_3]$ | $f[x_1, x_2, x_3]$ | $f[x_0, x_1, x_2, x_3]$ |                              |
| $x_4$ | $f(x_4)$ | $f[x_3, x_4]$ | $f[x_2, x_3, x_4]$ | $f[x_1, x_2, x_3, x_4]$ | $f[x_0, x_1, x_2, x_3, x_4]$ |
| $...$ | $...$    | $...$         | $...$              | $...$                   | $...$                        |

* * *

牛顿均差插值比拉格朗日插值计算量省，且便于程序设计；在增加插值节点的时候，已计算出来的均差结果可以被利用。

* * *

$ R_n(x) $ 为插值余项，由插值多项式的唯一性可知，在 $ f(x) $ 的高阶导数存在的时候，它与 $ R_n(x) $ [[拉格朗日插值](./../Lagrange_polynomial/index.html)]是等价的，但是当 $ f(x) $ 的高阶导数不存在的时候该插值余项也适用，因此更具一般性。

* * *

若 $ f(x) $ 在 $ [a, b] $ 上存在 $ n $ 阶导数，则通过构造函数

$$
\varphi(x) = f(x) - P_n(x)
$$

可得 $ \varphi(x) $ 在 $ [a, b] $ 上至少有 $ n + 1 $ 个零点，再依据罗尔定理可知 $ \varphi^{(n)}(x) $ 在 $ [a, b] $ 上至少有一个零点，即存在 $ \xi \in [a, b] $ 使得

$$
\varphi^{(n)}(\xi) = f^{(n)}(\xi) - n! f[x_0, x_1, ... , x_n] = 0
$$

从而 $ n $ 阶均差与导数的关系为

$$
f[x_0, x_1, ... , x_n] = \frac {f^{(n)}(\xi)} {n!}, \xi \in [a, b]
$$

* * *

定义：若插值节点是等距的，即满足 $ x_k = x_0 + kh (k = 0, 1, ... , n) $ ，则称 $ h $ 为**步长**。

* * *

定义：设 $ \{x_k\} (k = 0, 1, ... , n) $ 为一组等距节点， $ x_k $ 点的函数值为 $ f_k = f(x_k) $ ，称 $ \Delta f_k = f_{k+1} - f_k $ 为 $ x_k $ 处（以 $ h $ 为步长）的**一阶**（向前）**差分**。

一般地，称 $ \Delta^n f_k = \Delta^{n-1} f_{k+1} - \Delta^{n-1} f_k $ 为 $ x_k $ 处的 $ n $ **阶差分**。 $ \Delta $ 称为**差分算子**。

* * *

为了表示方便，再引入两个常用算子符号：

$$
I f_k = f_k, E f_k = f_{k+1}
$$

$ I $ 称为不变算子， $ E $ 称为步长为 $ h $ 的位移算子。

由此可推出

$$
\Delta f_k = f_{k+1} - f_k = E f_k - I f_k = (E - I) f_k
$$

即

$$
\Delta = E - I
$$

从而

$$
\Delta^n f_k = (E - I)^n f_k = \sum_{j=0}^n (-1)^j \binom {n} {j} E^{n-j} f_k = \sum_{j=0}^n (-1)^j \binom {n} {j} f_{n+k-j}
$$

$$
f_{n+k} = E^n f_k = (I + \Delta)^n f_k = \sum_{j=0}^n \binom {n} {j} \Delta^j f_k
$$

其中 $ \binom {n} {j} = \frac {n!} {(n-j)! j!} $ 为二项式展开系数。由后两式可见各阶差分和函数值可互相线性表出。

* * *

均差和差分的关系：

$$
f[x_k, x_{k+1}] = \frac {f_{k+1} - f_k} {x_{k+1} - x_k} = \frac {\Delta f_k} {h}
$$

$$
f[x_k, x_{k+1}, x_{k+2}] = \frac {f[x_{k+1}, x_{k+2}] - f[x_k, x_{k+1}]} {x_{k+2} - x_k} = \frac {\Delta^2 f_k} {2h^2}
$$

$$
...
$$

$$
f[x_k, ... , x_{k+m}] = \frac {\Delta^m f_k} {m!h^m}, m = 1, 2, ... , n
$$

* * *

如果 $ f(x) $ 的高阶导数存在，根据均差和导数的关系可知差分和导数的关系：

$$
\Delta^m f_k = h^m f^{(n)}(\xi), \xi \in (x_k, x_{k+n})
$$

* * *

定义：若插值节点等距，令 $ x = x_0 + th $ ，则牛顿插值多项式可表示为

$$
P_n(x_0 + th) = f_0 + t \Delta f_0 + \frac {t (t - 1)} {2!} \Delta^2 f_0 + ... + \frac {t (t - 1) ... (t - n + 1)} {n!} \Delta^n f_0
$$

称为**牛顿前插公式**。

* * *

牛顿前插公式的余项为

$$
R_n(x) = f[x, x_0, ... , x_n] t (t - 1) ... (t - n) h^{n+1} = \frac {t (t - 1) ... (t - n) h^{n+1}} {(n + 1)!} f^{(n+1)}(\xi), \xi \in (x_0, x_n)
$$

* * *

牛顿插值的C++实现
```C++   
#include <vector>
using std::vector;

class Newton_polynomial
{
public:
	Newton_polynomial(const vector<float>& x, const vector<float>& y)
	{
		Set_interpolation_nodes(x, y);
	}

	virtual ~Newton_polynomial()
	{

	}

	virtual void Set_interpolation_nodes(const vector<float>& x, const vector<float>& y)
	{
		x_ = x;
		n_ = int(x.size()) - 1;
		dd_.resize(n_ + 1);
		dd_.at(0) = y;
		for (size_t k = 1; k <= n_; k++)
		{
			dd_[k].resize(n_ - k + 1);
			for (size_t i = 0; i < n_ - k + 1; i++)
			{
				dd_[k][i] = (dd_[k - 1][i + 1] - dd_[k - 1][i]) / (x_[i + k] - x_[i]);
			}
		}
	}

	virtual void Insert_interpolation_nodes(float x, float y)
	{
		x_.push_back(x);
		n_ += 1;
		dd_.resize(n_ + 1);
		dd_.at(0).push_back(y);
		for (size_t k = 1; k <= n_; k++)
		{
			dd_[k].resize(n_ - k + 1);
			dd_[k][n_ - k] = (dd_[k - 1][n_ - k + 1] - dd_[k - 1][n_ - k]) / (x_[n_] - x_[n_ - k]);
		}
	}

	virtual float Eval(float x)
	{
		float P_n = dd_.at(0).at(0);
		float omega = 1.f;
		for (size_t k = 1; k <= n_; k++)
		{
			omega *= (x - x_[k - 1]);
			P_n += dd_[k][0] * omega;
		}
		return P_n;
	}

private:
	int n_;
	vector<float> x_;
	vector<vector<float>> dd_;
};

class Newton_forward_polynomial
{
public:
	Newton_forward_polynomial(float x0, float h, const vector<float>& y)
	{
		Set_interpolation_nodes(x0, h, y);
	}

	virtual ~Newton_forward_polynomial()
	{

	}

	virtual void Set_interpolation_nodes(float x0, float h, const vector<float>& y)
	{
		x0_ = x0;
		h_ = h;
		n_ = int(y.size()) - 1;
		d_.resize(n_ + 1);
		d_.at(0) = y;
		for (size_t k = 1; k <= n_; k++)
		{
			d_[k].resize(n_ - k + 1);
			for (size_t i = 0; i < n_ - k + 1; i++)
			{
				d_[k][i] = d_[k - 1][i + 1] - d_[k - 1][i];
			}
		}
	}

	virtual void Insert_interpolation_nodes(float y)
	{
		n_ += 1;
		d_.resize(n_ + 1);
		d_.at(0).push_back(y);
		for (size_t k = 1; k <= n_; k++)
		{
			d_[k].resize(n_ - k + 1);
			d_[k][n_ - k] = d_[k - 1][n_ - k + 1] - d_[k - 1][n_ - k];
		}
	}

	virtual float Eval(float x)
	{
		float P_n = d_.at(0).at(0);
		float t = (x - x0_) / h_;
		float omega = 1.f;
		for (size_t k = 1; k <= n_; k++)
		{
			omega *= (t - k + 1) / k;
			P_n += d_[k][0] * omega;
		}
		return P_n;
	}

private:
	int n_;
	float x0_;
	float h_;
	vector<vector<float>> d_;
};
```

* * *

[上一级](./../index.html)

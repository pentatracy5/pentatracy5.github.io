---
layout: default
title: 最小二乘法
---

具有一般性的最小二乘问题提法：设 $ f(x) \in C[a, b] $ ， $ f(x) $ 只在一组离散点集 $ \lbrace x_i, i = 0, 1, ... , m \rbrace $ 上给出， $ y_i = f(x_i) $ ， $ \varphi_0(x), \varphi_1(x), ... , \varphi_n(x) (n \leqslant m) $ 是 $ C[a, b] $ 上线性无关的函数族， $ \varphi = span \lbrace \varphi_0(x), \varphi_1(x), ... , \varphi_n(x) \rbrace $ ， $ \omega(x) $ 是 $ [a, b] $ 上的权函数。在 $ \varphi $ 中找一个函数 $ S^* (x) $ ，使得

$$
\sum_{i=0}^m \omega(x_i) \Big[ S^* (x_i) - y_i \Big]^2 = \underset {S(x) \in \varphi} {\min} \sum_{i=0}^m \omega(x_i) \Big[ S(x_i) - y_i \Big]^2
$$

其中 $ S(x) $ 可表示为

$$
S(x) = a_0 \varphi_0(x) + a_1 \varphi_1(x) + ... + a_n \varphi_n(x) 
$$

* * *

最小二乘问题可转化为求多元函数

$$
I(a_0, a_1, ... , a_n) = \sum_{i=0}^m \omega(x_i) \Big[ \sum_{j=0}^n a_j \varphi_j(x_i) - y_i \Big]^2
$$

由求多元函数极值的必要条件有

$$
\frac {\partial I} {\partial a_k} = 2 \sum_{i=0}^m \omega(x_i) \Big[ \sum_{j=0}^n a_j \varphi_j(x_i) - y_i \Big] \varphi_k(x_i) = 0, k = 0, 1, ... , n
$$

若记

$$
(\varphi_j, \varphi_k) = \sum_{i=0}^m \omega(x_i) \varphi_j(x_i) \varphi_k(x_i) \\
(f, \varphi_k) = \sum_{i=0}^m \omega(x_i) f(x_i) \varphi_k(x_i) \equiv d_k, k = 0, 1, ... , n
$$

则有

$$
\sum_{j=0}^n (\varphi_j, \varphi_k) a_j = d_k, k = 0, 1, ... , n
$$

称为**法方程**，可将其写为矩阵形式

$$
Ga = d
$$

其中

$$
a = (a_0, a_1, ... , a_n)^T \\
d = (d_0, d_1, ... , d_n)^T \\
G = \begin{bmatrix}
(\varphi_0, \varphi_0)  & (\varphi_0, \varphi_1)    & \cdots    & (\varphi_0, \varphi_n)    \\
(\varphi_1, \varphi_0)  & (\varphi_1, \varphi_1)    & \cdots    & (\varphi_1, \varphi_n)    \\
\vdots                  & \vdots                    &           & \vdots                    \\
(\varphi_n, \varphi_0)  & (\varphi_n, \varphi_1)    & \cdots    & (\varphi_n, \varphi_n)
\end{bmatrix}
$$

要使法方程有唯一解，就要求矩阵 $ G $ 非奇异。必须指出， $ \varphi_0(x), \varphi_1(x), ... , \varphi_n(x) $ 线性无关不能推出 $ G $ 非奇异。

* * *

定义：设 $ \varphi_0(x), \varphi_1(x), ... , \varphi_n(x) \in C[a, b] $ 的任意线性组合在点集 $ \lbrace x_i, i = 0, 1, ... , m \rbrace (n \leqslant m) $ 上至多只有 $ n $ 个不同的零点，则称 $ \varphi_0(x), \varphi_1(x), ... , \varphi_n(x) $ 在点集 $ \lbrace x_i, i = 0, 1, ... , m \rbrace $ 上满足**哈尔条件**。

* * *

显然 $ 1, x, ... , x^n $ 在任意 $ m (n \leqslant m) $ 个点上满足哈尔条件。

* * *

定理：如果 $ \varphi_0(x), \varphi_1(x), ... , \varphi_n(x) \in C[a, b] $ 在 $ \lbrace x_i, i = 0, 1, ... , m \rbrace $ 上满足哈尔条件，则法方程的系数矩阵非奇异，从而法方程存在唯一解。

证明：由于 $ \varphi_0(x), \varphi_1(x), ... , \varphi_n(x) \in C[a, b] $ 在 $ \lbrace x_i, i = 0, 1, ... , m \rbrace $ 上满足哈尔条件，因此任取 $ \lbrace x_i, i = 0, 1, ... , m \rbrace $ 中的 $ n+1 $ 个点（不妨记为 $ x_0, x_1, ... , x_n $ ）都有

$$
\begin{bmatrix}
\varphi_0(x_0)  & \varphi_1(x_0)    & \cdots    & \varphi_n(x_0)    \\
\varphi_0(x_1)  & \varphi_1(x_1)    & \cdots    & \varphi_n(x_1)    \\
\vdots          & \vdots            &           & \vdots            \\
\varphi_0(x_n)  & \varphi_1(x_n)    & \cdots    & \varphi_n(x_n)
\end{bmatrix}
$$

的行列式不为 $ 0 $ ，从而

$$
\begin{bmatrix}
\varphi_0(x_0)  & \varphi_1(x_0)    & \cdots    & \varphi_n(x_0)    \\
\varphi_0(x_1)  & \varphi_1(x_1)    & \cdots    & \varphi_n(x_1)    \\
\vdots          & \vdots            &           & \vdots            \\
\varphi_0(x_m)  & \varphi_1(x_m)    & \cdots    & \varphi_n(x_m)
\end{bmatrix}
$$

满秩，进而

$$
G = \begin{bmatrix}
\varphi_0(x_0)  & \varphi_0(x_1)    & \cdots    & \varphi_0(x_m)    \\
\varphi_1(x_0)  & \varphi_1(x_1)    & \cdots    & \varphi_1(x_m)    \\
\vdots          & \vdots            &           & \vdots            \\
\varphi_n(x_0)  & \varphi_n(x_1)    & \cdots    & \varphi_n(x_m)
\end{bmatrix}
\begin{bmatrix}
\omega(x_0) &               &           &               \\
            & \omega(x_1)   &           &               \\
            &               & \ddots    &               \\
            &               &           & \omega(x_m)
\end{bmatrix}
\begin{bmatrix}
\varphi_0(x_0)  & \varphi_1(x_0)    & \cdots    & \varphi_n(x_0)    \\
\varphi_0(x_1)  & \varphi_1(x_1)    & \cdots    & \varphi_n(x_1)    \\
\vdots          & \vdots            &           & \vdots            \\
\varphi_0(x_m)  & \varphi_1(x_m)    & \cdots    & \varphi_n(x_m)
\end{bmatrix}
$$

也是满秩的，故 $ G $ 非奇异。

* * *

若法方程存在唯一解 $ a_k = a_k^* , k = 0, 1, ... , n $ ，则对

$$
S^*(x) = a_0^* \varphi_0(x) + a_1^* \varphi_1(x) + ... + a_n^* \varphi_n(x)
$$

有

$$
\sum_{i=0}^m \omega(x_i) \Big[ S^* (x_i) - y_i \Big]^2 = \underset {S(x) \in \varphi} {\min} \sum_{i=0}^m \omega(x_i) \Big[ S(x_i) - y_i \Big]^2
$$

证明：类似于最佳平方逼近函数的证明过程。

* * *

当 $ \varphi = span \lbrace 1, x, ... , x^n \rbrace $ ， $ n \geqslant 3 $ 时， $ G $ 可能变得病态，这种情况下解法方程得到最小二乘解的方法不可取。

* * *

通常对于 $ n=1 $ 的简单情形都可通过求法方程的方法得到 $ S^*(x) $ ，若 $ \omega(x) \equiv \frac {1} {m+1} $ 且 $ \varphi = span \lbrace 1, x \rbrace $ ，这种情形可得到线性回归的计算公式

$$
S(x) = a_0 + a_1 x \\
a_0 = \frac {(m+1)\sum_{i=0}^m x_i y_i - \sum_{i=0}^m x_i \sum_{i=0}^m y_i} {(m+1)\sum_{i=0}^m x_i^2 - (\sum_{i=0}^m x_i)^2} \\
a_1 = \frac {\sum_{i=0}^m x_i^2 \sum_{i=0}^m y_i - \sum_{i=0}^m x_i y_i \sum_{i=0}^m x_i} {(m+1)\sum_{i=0}^m x_i^2 - (\sum_{i=0}^m x_i)^2}
$$

* * *

定义： $ \omega(x) $ 是 $ [a, b] $ 上的权函数，如果 $ \varphi_0(x), \varphi_1(x), ... , \varphi_n(x) \in C[a, b] $ 关于点集 $ \lbrace x_i, i = 0, 1, ... , m \rbrace $ 满足

$$
(\varphi_j, \varphi_k) = \sum_{i=0}^m \omega(x_i) \varphi_j(x_i) \varphi_k(x_i) = \begin{cases}
0, j \neq k \\
A_k > 0, j = k
\end{cases}
$$

则称 $ \varphi_0(x), \varphi_1(x), ... , \varphi_n(x) $ 关于 $ \lbrace x_i \rbrace $ 带权 $ \omega(x_i) $ 正交。

* * *

若 $ \varphi_0(x), \varphi_1(x), ... , \varphi_n(x) \in C[a, b] $ 关于点集 $ \lbrace x_i, i = 0, 1, ... , m \rbrace $ 带权 $ \omega(x_i) (i = 0, 1, ... , m) $ 正交，则法方程的解为

$$
a_k^* = \frac {(f, \varphi_k)} {(\varphi_k, \varphi_k)} = \frac {\sum_{i=0}^m \omega(x_i) f(x_i) \varphi_k(x_i)} {\sum_{i=0}^m \omega(x_i) \varphi_k(x_i) \varphi_k(x_i)}, k = 0, 1, ... , n
$$

且平方误差为

$$
\sum_{i=0}^m \omega(x_i) \Big[ f(x_i) - S^* (x_i) \Big]^2 = \sum_{i=0}^m \omega(x_i) f(x_i)^2 - \sum_{k=0}^n A_k { a_k^* }^2
$$

* * *

性质：给定点集 $ \lbrace x_i, i = 0, 1, ... , m \rbrace $ 和权函数 $ \omega(x) $ ，对 $ n \leqslant m $ ，按照如下定义的多项式 $ \lbrace P_k(x) \rbrace $ 关于给定点集带给定权正交

$$
\begin{aligned}
&\begin{cases}
P_0(x) = 1 \\
P_1(x) = (x - \alpha_1) P_0(x) \\
P_{k+1}(x) = (x - \alpha_{k+1}) P_k(x) - \beta_k P_{k-1}(x), k = 1, 2, ... , n-1
\end{cases} \\
&\begin{cases}
\alpha_{k+1} = \frac {(x P_k, P_k)} {(P_k, P_k)}, k = 0, 1, ... , n-1 \\
\beta_k = \frac {(P_k, P_k)} {(P_{k-1}, P_{k-1})}, k = 1, 2, ... , n-1
\end{cases}
\end{aligned}
$$

证明：用归纳法。

首先易知

$$
(P_0, P_1) = (P_0, x P_0) - \alpha_1 (P_0, P_0) = (P_0, x P_0) - \frac {(x P_0, P_0)} {(P_0, P_0)} (P_0, P_0) = 0
$$

假定 $ P_0, P_1, ... , P_k $ 两两正交，往证 $ (P_{k+1}, P_s) = 0, s = 0, 1, ... , k $ 成立。易知

$$
(P_{k+1}, P_s) = ((x - \alpha_{k+1}) P_k, P_s) - (\beta_k P_{k-1}, P_s) = (x P_k, P_s) - \alpha_{k+1}(P_k, P_s) - \beta_k (P_{k-1}, P_s)
$$

当 $ 0 \leqslant s \leqslant k-2 $ 时，有

$$
(P_k, P_s) = (P_{k-1}, P_s) = 0
$$

又 $ x P_s $ 是首项系数为 $ 1 $ 的 $ s+1 (< k) $ 次多项式，可由 $ P_0, P_1, ... , P_{k-1} $ 线性表出，故

$$
(x P_k, P_s) = (P_k, x P_s) = 0
$$

从而

$$
(P_{k+1}, P_s) = 0
$$

当 $ s = k-1 $ 时，有

$$
(P_k, P_s) = (P_k, P_{k-1}) = 0
$$

并且类似的， $ x P_s = x P_{k-1} $ 可由 $ P_0, P_1, ... , P_k $ 线性表出，并且由首项系数可知， $ P_k $ 的系数为 $ 1 $ ，从而

$$
(x P_k, P_s) = (x P_k, P_{k-1}) = (P_k, x P_{k-1}) = (P_k, P_k)
$$

故

$$
(P_{k+1}, P_s) = (P_{k+1}, P_{k-1}) = (x P_k, P_{k-1}) - \beta_k (P_{k-1}, P_{k-1}) = (P_k, P_k) - \frac {(P_k, P_k)} {(P_{k-1}, P_{k-1})} (P_{k-1}, P_{k-1}) = 0
$$

当 $ s = k $ 时，有

$$
(P_{k+1}, P_s) = (P_{k+1}, P_k) = (x P_k, P_k) - \alpha_{k+1}(P_k, P_k) = (x P_k, P_k) - \frac {(x P_k, P_k)} {(P_k, P_k)} (P_k, P_k) = 0
$$

综上结论成立。

* * *

最小二乘多项式的C++实现
```C++
#include <vector>
using std::vector;

float Qinjiushao(const vector<float>& a, float x);

class Least_squares_polynomial
{
public:
	Least_squares_polynomial()
	{
		m_ = 0;
		n_ = 0;
	}

	
	Least_squares_polynomial()
	{
		m_ = 0;
		n_ = 0;
	}

	Least_squares_polynomial(const vector<float>& x, const vector<float>& y, const vector<float>& omega, size_t n)
	{
		Set_data(x, y, omega, n);
	}

	virtual ~Least_squares_polynomial()
	{

	}

			Set_data(x, y, omega, n);
	}

	virtual ~Least_squares_polynomial()
	{

	}

	virtual void Set_data(const vector<float>& x, const vector<float>& y, const vector<float>& omega, size_t n)
	{
		x_ = x;
		y_ = y;
		omega_ = omega;
		m_ = x_.size() - 1;
		n_ = n <= m_ ? n : m_;
		a_.resize(n_ + 1);
		P_.resize(n_ + 1);
		for (size_t k = 0; k <= n_; k++)
		{
			P_[k].resize(k + 1);
		}

		float dot1 = 0.f;	// (xP[k], P[k])
		float dot2 = 0.f;	// (P[k], P[k])
		float dot3 = 0.f;	// (f, P[k])
		float dot4 = 0.f;	// (P[k-1], P[k-1])
		float alpha = 0.f;	// dot1 / dot2
		float beta = 0.f;	// dot2 / dot4

		P_[0][0] = 1.f;
		for (size_t i = 0; i <= m_; i++)
		{
			dot1 += omega_[i] * x_[i];
			dot2 += omega_[i];
			dot3 += omega_[i] * y_[i];
		}
		a_[0] = dot3 / dot2;
		if (0 == n_)
		{
			return;
		}
		P_[1][0] = 1.f;
		P_[1][1] = -dot1 / dot2;

		for (size_t k = 1; k < n_; k++)
		{
			dot4 = dot2;
			dot1 = 0.f;
			dot2 = 0.f;
			dot3 = 0.f;
			for (size_t i = 0; i <= m_; i++)
			{
				float Pk_xi = Qinjiushao(P_[k], x_[i]);
				dot1 += omega_[i] * x_[i] * Pk_xi * Pk_xi;
				dot2 += omega_[i] * Pk_xi * Pk_xi;
				dot3 += omega_[i] * y_[i] * Pk_xi;
			}
			alpha = dot1 / dot2;
			beta = dot2 / dot4;
			a_[k] = dot3 / dot2;

			P_[k + 1][0] = 1.f;
			P_[k + 1][1] = P_[k][1] - alpha;
			for (size_t j = 2; j <= k; j++)
			{
				P_[k + 1][j] = P_[k][j] - alpha * P_[k][j - 1] - beta * P_[k - 1][j - 2];
			}
			P_[k + 1][k + 1] = -alpha * P_[k][k] - beta * P_[k - 1][k - 1];
		}
		dot2 = 0.f;
		dot3 = 0.f;
		for (size_t i = 0; i <= m_; i++)
		{
			float Pk_xi = Qinjiushao(P_[n_], x_[i]);
			dot2 += omega_[i] * Pk_xi * Pk_xi;
			dot3 += omega_[i] * y_[i] * Pk_xi;
		}
		a_[n_] = dot3 / dot2;
	}

	virtual void Set_n(size_t n)
	{
		n = n <= m_ ? n : m_;
		a_.resize(n + 1);
		P_.resize(n + 1);
		for (size_t k = 0; k <= n; k++)
		{
			P_[k].resize(k + 1);
		}

		if (n > n_)
		{
			float dot1 = 0.f;	// (xP[k], P[k])
			float dot2 = 0.f;	// (P[k], P[k])
			float dot3 = 0.f;	// (f, P[k])
			float dot4 = 0.f;	// (P[k-1], P[k-1])
			float alpha = 0.f;	// dot1 / dot2
			float beta = 0.f;	// dot2 / dot4

			if (0 == n_)
			{
				for (size_t i = 0; i <= m_; i++)
				{
					dot1 += omega_[i] * x_[i];
					dot2 += omega_[i];
				}
				P_[1][0] = 1.f;
				P_[1][1] = -dot1 / dot2;
				n_ = 1;
			}
			else
			{
				for (size_t i = 0; i <= m_; i++)
				{
					float Pk_xi = Qinjiushao(P_[n_ - 1], x_[i]);
					dot2 += omega_[i] * Pk_xi * Pk_xi;
				}
			}

			for (size_t k = n_; k < n; k++)
			{
				dot4 = dot2;
				dot1 = 0.f;
				dot2 = 0.f;
				dot3 = 0.f;
				for (size_t i = 0; i <= m_; i++)
				{
					float Pk_xi = Qinjiushao(P_[k], x_[i]);
					dot1 += omega_[i] * x_[i] * Pk_xi * Pk_xi;
					dot2 += omega_[i] * Pk_xi * Pk_xi;
					dot3 += omega_[i] * y_[i] * Pk_xi;
				}
				alpha = dot1 / dot2;
				beta = dot2 / dot4;
				a_[k] = dot3 / dot2;

				P_[k + 1][0] = 1.f;
				P_[k + 1][1] = P_[k][1] - alpha;
				for (size_t j = 2; j <= k; j++)
				{
					P_[k + 1][j] = P_[k][j] - alpha * P_[k][j - 1] - beta * P_[k - 1][j - 2];
				}
				P_[k + 1][k + 1] = -alpha * P_[k][k] - beta * P_[k - 1][k - 1];
			}
			dot2 = 0.f;
			dot3 = 0.f;
			for (size_t i = 0; i <= m_; i++)
			{
				float Pk_xi = Qinjiushao(P_[n], x_[i]);
				dot2 += omega_[i] * Pk_xi * Pk_xi;
				dot3 += omega_[i] * y_[i] * Pk_xi;
			}
			a_[n] = dot3 / dot2;
		}

		n_ = n;
	}

	virtual float Eval(float x)
	{
		float result = 0.f;
		for (size_t k = 0; k <= n_; k++)
		{
			result += a_[k] * Qinjiushao(P_[k], x);
		}
		return result;
	}

private:
	vector<float> x_;
	vector<float> y_;
	vector<float> omega_;
	size_t m_;
	size_t n_;
	vector<vector<float>> P_;
	vector<float> a_;
};
```

* * *

[上一级](./../index.html)

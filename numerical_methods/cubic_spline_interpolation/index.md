---
layout: default
title: 三次样条插值
---

对任意的插值节点，当 $ n \rightarrow \infty $ 时， $ L_n(x) $ 不一定收敛于 $ f(x) $ 。龙格（Runge）给出了一个等距节点插值多项式 $ L_n(x) $ 不收敛于 $ f(x) $ 的例子。

取 $ f(x) = \frac {1} {1 + x^2} $ ，插值区间为 $ [-5, 5] $ ，插值节点为 $ x_k = -5 + \frac {10k} {n} (k = 0, 1, ... , n) $ 。

令 $ x_{n - 0.5} = 0.5(x_{n-1} + x_n) = 5 - \frac {5} {n} $ ，当 $ n = 2, 4, ... , 20 $ 时， $ x_{n - 0.5} $ 处的插值余项会随着 $ n $ 增加而增加，当 $ n \rightarrow \infty $ 时， $ L_n(x) $ 在 $ [-5, 5] $ 上不收敛。

![y = L_10(x) & y = 1 / (1 + x^2)](cubic_spline_interpolation_1.png)

龙格证明了，存在一个常数 $ c \approx 3.63 $ ，使得当 $ \vert x \vert \leqslant c $ 时， $ \lim \limits_{n \rightarrow \infty} L_n(x) = f(x) $ ，而当 $ \vert x \vert > c $ 时， $ L_n(x) $ 发散。

高次插值多项式的近似效果通常不好，称之为高次插值的病态性质。

* * *

定义：设已知节点 $ a = x_0 < x_1 < ... < x_n = b $ 上的函数值 $ f_0, f_1, ... , f_n $ ，记 $ h_k = x_{k+1} - x_k, h = \underset {k} {max} h_k $ ，求一折线函数 $ I_h(x) $ 满足：

（1） $ I_h(x) \in C[a, b] $ 

（2） $ I_h(x_k) = f_k (k = 0, 1, ... , n) $ 

（3） $ I_h(x) $ 在每个小区间 $ [x_k, x_{k+1}] $ 上是线性函数

则称 $ I_h(x) $ 为**分段线性插值函数**。

* * *

由定义可知 $ I_h(x) $ 在每个小区间 $ [x_k, x_{k+1}] $ 上可表示为

$$
I_h(x) = \frac {x - x_{k+1}} {x_k - x_{k+1}} f_k + \frac {x - x_k} {x_{k+1} - x_k} f_{k+1}, x_k \leqslant x \leqslant x_{k+1}, k = 0, 1, ... , n-1
$$

分段线性插值的误差估计可利用插值余项得到

$$
\underset {x_k \leqslant x \leqslant x_{k+1}} {max} \vert f(x) - I_h(x) \vert \leqslant \frac {M_2} {2} \underset {x_k \leqslant x \leqslant x_{k+1}} {max} \vert (x - x_k) (x - x_{k+1}) \vert
$$

其中 $ M_2 = \underset {a \leqslant x \leqslant b} {max} \vert f''(x) \vert $ 。

进而有

$$
\underset {a \leqslant x \leqslant b} {max} \vert f(x) - I_h(x) \vert \leqslant \frac {M_2} {8} h^2
$$

由此还可得

$$
\lim \limits_{h \rightarrow 0} I_h(x) = f(x)
$$

在 $ [a, b] $ 上一致成立，故 $ I_h(x) $ 在 $ [a, b] $ 上一致收敛到 $ f(x) $ 。

* * *

分段线性插值的C++实现
```C++
#include <vector>
using std::vector;

class Piecewise_linear_interpolation
{
public:
	Piecewise_linear_interpolation(const vector<float>& x, const vector<float>& y)
	{
		x_ = x;
		y_ = y;
		n_ = int(x.size()) - 1;
	}

	virtual ~Piecewise_linear_interpolation()
	{

	}

	virtual void Set_interpolation_nodes(const vector<float>& x, const vector<float>& y)
	{
		x_ = x;
		y_ = y;
		n_ = int(x.size()) - 1;
	}

	virtual float Eval(float x)
	{
		if (x_.at(0) > x || x_.at(n_) < x)
		{
			return 0.f;
		}

		for (size_t k = 0; k < n_; k++)
		{
			if (x_[k + 1] >= x)
			{
				return (x - x_[k + 1]) / (x_[k] - x_[k + 1]) * y_[k] + (x - x_[k]) / (x_[k + 1] - x_[k]) * y_[k + 1];
			}
		}
	}

private:
	int n_;
	vector<float> x_;
	vector<float> y_;
};
```

* * *

若在节点 $ x_k (k = 0, 1, ... , n) $ 上还给出导数值 $ f'_k $ ，则可构造一个导数连续的分段插值函数，它满足条件：

（1） $ I_h(x) \in C^1[a, b] $ 

（2） $ I_h(x_k) = f_k, I'_h(x_k) = f'_k (k = 0, 1, ... , n) $ 

（3） $ I_h(x) $ 在每个小区间 $ [x_k, x_{k+1}] $ 上是三次多项式

则称 $ I_h(x) $ 为**分段三次埃尔米特插值函数**。

* * *

根据两点三次埃尔米特插值可知， $ I_h(x) $ 在区间 $ [x_k, x_{k+1}] $ 上的表达式为

$$
I_h(x) = \frac {(2x + x_{k+1} - 3x_k) (x - x_{k+1})^2} {(x_{k+1} - x_k)^3} f_k + \frac {(2x + x_k - 3x_{k+1}) (x - x_k)^2} {(x_k - x_{k+1})^3} f_{k+1} + \frac {(x - x_k) (x - x_{k+1})^2} {(x_k - x_{k+1})^2} f'_k + \frac {(x - x_{k+1}) (x - x_k)^2} {(x_{k+1} - x_k)^2} f'_{k+1}, k = 0, 1, ... , n-1
$$

* * *

定理：设 $ f \in C^4[a, b] $ ， $ I_h(x) $ 为 $ f(x) $ 在节点 $ a = x_0 < x_1 < ... < x_n = b $ 上的分段三次埃尔米特插值多项式，则有

$$
\underset {a \leqslant x \leqslant b} {max} \vert f(x) - I_h(x) \vert \leqslant \frac {h^4} {384} \underset {a \leqslant x \leqslant b} {max} \vert f^{(4)}(x) \vert
$$

其中 $ h = \underset {0 \leqslant k \leqslant n-1} {max} (x_{k+1} - x_k) $ 。

证明：利用三次埃尔米特插值的余项可得误差估计

$$
\underset {x_k \leqslant x \leqslant x_{k+1}} {max} \vert f(x) - I_h(x) \vert \leqslant \frac {(x_{k+1} - x_k)^4} {384} \underset {x_k \leqslant x \leqslant x_{k+1}} {max} \vert f^{(4)}(x) \vert
$$

易知结论成立。

* * *

分段三次埃尔米特插值函数优点：由上述定理可知其对比分段线性插值误差通常更小；缺点：要求给出插值点的导数值，要给的信息太多，光滑度不高（只有一阶导数连续）。

* * *

分段三次埃尔米特插值的C++实现
```C++
#include <vector>
using std::vector;

class Two_points_Hermimte_polynomial;

class Piecewise_cubic_Hermite_interpolation
{
public:
	Piecewise_cubic_Hermite_interpolation(const vector<float>& x, const vector<float>& y, const vector<float>& dy)
	{
		x_ = x;
		y_ = y;
		dy_ = dy;
		n_ = int(x.size()) - 1;
		H_3s_.resize(n_);
		for (size_t k = 0; k < n_; k++)
		{
			H_3s_[k].Set_interpolation_nodes({ x_[k], x_[k + 1] }, { y_[k], y_[k + 1] }, { dy_[k], dy_[k + 1] });
		}
	}

	virtual ~Piecewise_cubic_Hermite_interpolation()
	{

	}

	virtual void Set_interpolation_nodes(const vector<float>& x, const vector<float>& y, const vector<float>& dy)
	{
		x_ = x;
		y_ = y;
		dy_ = dy;
		n_ = int(x.size()) - 1;
		H_3s_.resize(n_);
		for (size_t k = 0; k < n_; k++)
		{
			H_3s_[k].Set_interpolation_nodes({ x_[k], x_[k + 1] }, { y_[k], y_[k + 1] }, { dy_[k], dy_[k + 1] });
		}
	}

	virtual float Eval(float x)
	{
		if (x_.at(0) > x || x_.at(n_) < x)
		{
			return 0.f;
		}

		for (size_t k = 0; k < n_; k++)
		{
			if (x_[k + 1] >= x)
			{
				return H_3s_[k].Eval(x);
			}
		}
	}

private:
	int n_;
	vector<float> x_;
	vector<float> y_;
	vector<float> dy_;
	vector<Two_points_Hermimte_polynomial> H_3s_;
};
```

* * *

定义：若函数 $ S(x) \in C^2[a, b] $ ，且在每个小区间 $ [x_j, x_{j+1}] $ 上是三次多项式，其中 $ a = x_0 < x_1 < ... < x_n = b $ 是给定节点，则称 $ S(x) $ 是节点 $ x_0, x_1, ... , x_n $ 上的**三次样条函数**。若在节点 $ x_j $ 上给定函数值 $ y_j = f(x_j) (j = 0, 1, ... , n) $ ，并成立

$$
S(x_j) = y_j, j = 0, 1, ... , n
$$

则称 $ S(x) $ 为**三次样条插值函数**。

* * *

[上一级](./../index.html)

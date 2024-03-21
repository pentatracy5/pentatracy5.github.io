---
layout: default
title: 矩阵基础
---

$ \det (A) = \sum_{j=1}^n a_{ij} A_{ij}, i = 1, 2, \cdots, n, A \in \mathbb{R}^{n \times n} $ ，其中 $ A_{ij} $ 为 $ a_{ij} $ 的代数余子式， $ A_{ij} = (-1)^{i+j} M_{ij} $ ， $ M_{ij} $ 为元素 $ a_{ij} $ 的余子式。

* * *

$ \det(AB) = \det(A) \det(B), A, B \in \mathbb{R}^{n \times n} $

* * *

$ \det(A^T) = \det(A), A \in \mathbb{R}^{n \times n} $

* * *

$ \det(cA) = c^n \det(A), c \in \mathbb{R}, A \in \mathbb{R}^{n \times n} $

* * *

$ \det(A) \neq 0 \Leftrightarrow A $ 是非奇异矩阵

* * *

定义：设 $ A = a_{ij} \in \mathbb{R}^{n \times n} $ ，若存在数 $ \lambda $ （实数或者复数）和非零向量 $ x = (x_1, x_2, \cdots, x_n)^T \in \mathbb{R}^n $ ，使得

$$
A x = \lambda x
$$

则称 $ \lambda $ 为 $ A $ 的**特征值**， $ x $ 为 $ A $ 对应 $ \lambda $ 的**特征向量**， $ A $ 的全体特征值称为 $ A $ 的**谱**，记作 $ \sigma(A) $ ，即 $ \sigma(A) = \lbrace \lambda_1, \lambda_2, \cdots, \lambda_n \rbrace $ ，记

$$
\rho(A) = \underset {1 \leqslant i \leqslant n} {\max} \vert \lambda_i \vert
$$

称为 $ A $ 的**谱半径**。

由特征值和特征向量的定义可知齐次线性方程组

$$
(\lambda I - A) x = 0
$$

有非零解，故关于系数行列式有

$$
p(\lambda) \triangleq \det (\lambda I - A) = \begin{vmatrix}
\lambda - a_{11}    & -a_{12}           & \cdots    & -a_{1n}           \\
-a_{21}             & \lambda - a_{22}  & \cdots    & -a_{2n}           \\
\vdots              & \vdots            &           & \vdots            \\
-a_{n1}             & -a_{n2}           & \cdots    & \lambda - a_{nn}
\end{vmatrix} = \lambda^n + c_1 \lambda^{n-1} + \cdots + c_{n-1} \lambda + c_n = 0
$$

$ p(\lambda) $ 称为矩阵 $ A $ 的**特征多项式**， $ p(\lambda) = 0 $ 称为矩阵 $ A $ 的**特征方程**。

由代数基本定理可知特征方程在复数域上有 $ n $ 个根 $ \lambda_1, \lambda_2, \cdots, \lambda_n $ ，故

$$
p(\lambda) = (\lambda - \lambda_1)(\lambda - \lambda_2)\cdots(\lambda - \lambda_n)
$$

从而

$$
trA \triangleq \sum_{i=1}^n \lambda_i = -c_1 = \sum_{i=1}^n a_{ii} \\
\prod_{i=1}^n \lambda_i = (-1)^n c_n = \det(A)
$$

称 $ trA $ 为 $ A $ 的**迹**。

* * *

$ A^T $ 和 $ A $ 有相同的特征值，但特征向量不一定相同。可令

$$
A = \begin{bmatrix}
1 & 1 \\
0 & 1
\end{bmatrix}
$$

则 $ A $ 和 $ A^T $ 均有特征值 $ 1 $ ，但对应的特征向量分别是 $ (1, 0)^T $ 和 $ (0, 1)^T $ 。

* * *

若 $ A $ 非奇异，则 $ A^{-1} $ 的特征值为 $ \lambda^{-1} $ ，特征向量仍为 $ x $ 。

* * *

相似矩阵 $ B = S^{-1}AS $ 有相同的特征多项式。

* * *

若 $ i-j > 1 $ 时， $ a_{ij} = 0 $ ，则称 $ A $ 为**上海森伯格阵**；相应的，若 $ j-i > 1 $ 时， $ a_{ij} = 0 $ ，则称 $ A $ 为**下海森伯格阵**。

* * *

若 $ \vert i-j \vert > 1 $ 时， $ a_{ij} = 0 $ ，即 $ A $ 既为上海森伯格阵也为下海森伯格阵，则称 $ A $ 为***三对角矩阵**。

* * *

若 $ A \in \mathbb{C}^{n \times n} $ ，如果 $ A^H \triangleq \overline{A}^T = A $ ，即 $ A $ 的共轭转置等于其自身，则称 $ A $ 为**埃尔米特矩阵**。

* * *

若对任意非零向量 $ x \in \mathbb{R}^n $ ， $ x^T A x > 0 $ ，则称 $ A $ 为**正定矩阵**。

* * *

若 $ A^{-1} = A^T $ ，则称 $ A $ 为**正交矩阵**。

* * *

若 $ A \in \mathbb{C}^{n \times n} $ ，如果 $ A^{-1} = A^H $ ，则称 $ A $ 为**酉矩阵**。

* * *

由单位矩阵 $ I $ 交换第 $ i $ 行和第 $ j $ 行（或者第 $ i $ 列和第 $ j $ 列），得到的矩阵记为 $ I_{ij} $ ，称为**初等置换阵**，且 $ I_{ij} A $ 为交换 $ A $ 第 $ i $ 行和第 $ j $ 行所得到的矩阵， $ A I_{ij} $ 为交换 $ A $ 第 $ i $ 列和第 $ j $ 列所得到的矩阵。

* * *

初等置换阵的乘积称为**置换阵**。

* * *

定理：设 $ A \in \mathbb{R}^{n \times n} $ ，则下述命题等价：

1）对任何 $ b \in \mathbb{R} $ ，方程组 $ Ax = b $ 只有唯一解。

2）方程组 $ Ax = 0 $ 只有唯一解。

3） $ \det(A) \neq 0 $ 

4） $ A^{-1} $ 存在。

5） $ rank(A) = n $ 

* * *

定理：设 $ A \in \mathbb{R}^{n \times n} $ 为对称正定阵，则：

1） $ A $ 非奇异，且 $ A^{-1} $ 对称正定。

2）记 $ A_k $ 为 $ A $ 的顺序主子阵，即

$$
A_k = \begin{bmatrix}
a_{11} & \cdots & a_{1k} \\
\vdots &        & \vdots \\
a_{k1} & \cdots & a_{kk}
\end{bmatrix}, k = 1, 2, \cdots, n
$$

则 $ A_k(k = 1, 2, \cdots, n) $ 对称正定。

3） $ A $ 的特征值 $ \lambda_i > 0(i = 1, 2, \cdots, n) $ 

4） $ A $ 的顺序主子式 $ \det(A_k) > 0(k = 1, 2, \cdots, n) $ 

* * *

定理：设 $ A \in \mathbb{R}^{n \times n} $ 为对称矩阵，如果 $ \det(A_k) > 0(k = 1, 2, \cdots, n) $ ，或 $ A $ 的特征值 $ \lambda_i > 0(i = 1, 2, \cdots, n) $ ，则 $ A $ 正定。

* * *

定理：设 $ A $ 为 $ n $ 阶矩阵，则存在一个非奇异矩阵 $ P $ 使得

$$
P^{-1}AP = \begin{bmatrix}
J_1(\lambda_1)  &                   &           &               \\
                & J_2(\lambda_2)    &           &               \\
                &                   & \ddots    &               \\
                &                   &           & J_r(\lambda_r)
\end{bmatrix}
$$

称为**若尔当标准形**，其中

$$
J_i = \begin{bmatrix}
\lambda_i   & 1         &           &           &           \\
            & \lambda_i & 1         &           &           \\
            &           & \ddots    & \ddots    &           \\
            &           &           & \lambda_i & 1         \\
            &           &           &           & \lambda_i
\end{bmatrix}_{n_i \times n_i}, n_i \geqslant 1(i = 1, 2, \cdots, r), \sum_{i=1}^r n_i = n
$$

称为**若尔当块**。

* * *

$ A $ 的若尔当标准形的对角线元素包含 $ A $ 的所有特征值，因此如果 $ A $ 的特征值各不相同，则其若尔当标准形为对角阵。

* * *

[上一级](./../index.html)

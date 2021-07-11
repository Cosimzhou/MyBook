Linear Algebra
==============

## Determinant

$$D=\begin{vmatrix}	a_{1,1} & a_{1,2} & a_{1,3} & \dots & a_{1,n} \\\
a_{2,1} & a_{2,2} & a_{2,3} & \dots & a_{2,n} \\\
\vdots & \vdots & \vdots & \ddots & \vdots \\\
a_{n,1} & a_{n,2} & a_{n,3} & \dots & a_{n,n} \end{vmatrix}$$
$\begin{aligned}D=\sum^k\left[(-1)^k\prod_{j=n}^n a_{j,k_j}\right]\end{aligned}$

## Matrix


$$A=\begin{pmatrix}	a_{1,1} & a_{1,2} & a_{1,3} & \dots & a_{1,n} \\\
a_{2,1} & a_{2,2} & a_{2,3} & \dots & a_{2,n} \\\
\vdots & \vdots & \vdots & \ddots & \vdots \\\
a_{m,1} & a_{m,2} & a_{m,3} & \dots & a_{m,n} \end{pmatrix},\quad A\in\mathbb{R}^{m\times n} $$

| Operation           |        Comment          | Description         |
| ------------------- | ----------------------- | ------------------- |
| $A^{-1}$            | 矩阵的逆                | $\begin{aligned}A^{-1}=\frac{1}{\lvert A\rvert}A^{*}\end{aligned}$ |
| $A^{*}$             | 伴随矩阵                | $\begin{aligned}M_{ij}\in\rm{det}\mathbb{R}^{(n-1)\times(n-1)},A_{ij}=(-1)^{i+j}M_{i,j},A^{*}=\begin{pmatrix}A_{1,1}&A_{1,2}&\dots&A_{1,n}\\A_{2,1}&A_{2,2}&\dots&A_{2,n}\\\vdots&\vdots&\ddots&\vdots\\A_{n,1}&A_{n,2}&\dots&A_{n,n}\end{pmatrix}\end{aligned}$|
| $A^{H}$             | 共轭矩阵(Hermite)       | $A^H=\overline{A}=\begin{pmatrix}\overline{a}_{1,1}&\overline{a}_{2,1}&\dots&\overline{a}_{m,1}\\\overline{a}_{1,2}&\overline{a}_{2,2}&\dots&\overline{a}_{m,2}\\\vdots&\vdots&\ddots&\vdots\\\overline{a}_{1,n}&\overline{a}_{2,n}&\dots&\overline{a}_{m,n}\end{pmatrix}$|
| $A^{T}$             | 转置矩阵(Transposition) | $\begin{aligned}A\in\mathbb{R}^{m\times n},A^T\in\mathbb{R}^{n\times m},A^T=\begin{pmatrix}a_{1,1}&a_{2,1}&\dots&a_{m,1}\\a_{1,2}&a_{2,2}&\dots&a_{m,2}\\\vdots&\vdots&\ddots&\vdots\\a_{1,n}&a_{2,n}&\dots&a_{m,n}\end{pmatrix}\end{aligned}$ |
| $trA$               | 矩阵的迹(Trace)         | $\begin{aligned}trA=\sum_{i=1}^{n}a_{ii}\end{aligned}$ |
| $\rm{det}A$         | 矩阵的行列式            | $\begin{aligned}\rm{det}A=\begin{vmatrix}a_{1,1}&a_{1,2}&a_{1,3}&\dots&a_{1,n}\\a_{2,1}&a_{2,2}&a_{2,3}&\dots&a_{2,n}\\ \vdots&\vdots&\vdots&\ddots&\vdots\\a_{n,1}&a_{n,2}&a_{n,3}&\dots&a_{n,n}\end{vmatrix}\end{aligned}$ |
| $\rm{eig}A$         | 单位矩阵                | $\begin{aligned}\rm{eig}A=\begin{pmatrix}1&&&\\&1&&\\&&\ddots&\\&&&1\end{pmatrix}\in\mathbb{R}^{n\times n}\end{aligned}$ |
| $\lVert A\rVert$    | 范数                    | |
| $A\times B$         | 矩阵乘法                | $\begin{aligned}A_{m\times l}\times B_{l\times n}=A_{m\times l}B_{l\times n}\in \mathbb{R}^{m\times n}\end{aligned}$ |
| $A\circ B$          | 哈达马积(Hadamard product)| $\begin{aligned}A,B\in R^{m\times n},A\circ B=\begin{pmatrix}a_{1,1}b_{1,1}&a_{1,2}b_{1,2}&\dots&a_{1,n}b_{1,n}\\a_{2,1}b_{2,1}&a_{2,2}b_{2,2}&\dots&a_{2,n}b_{2,n}\\\vdots&\vdots&\ddots&\vdots\\a_{m,1}b_{m,1}&a_{m,2}b_{m,2}&\dots&a_{m,n}b_{m,n}\end{pmatrix}\in\mathbb{R}^{m\times n}\end{aligned}$ |
| $A\otimes B$        | 克罗内克积(Kronecker Product)| $\begin{aligned}A^{a\times b}\otimes B^{c\times d}=\begin{pmatrix}a_{1,1}B&a_{1,2}B&\dots&a_{1,b}B\\a_{2,1}B&a_{2,2}B&\dots&a_{2,b}B\\\vdots&\vdots&\ddots&\vdots\\a_{a,1}B&a_{a,2}B&\dots&a_{a,b}B\end{pmatrix}\in\mathbb{R}^{ac\times bd}\end{aligned}$ |






### Transposition

#### Properties
1. $(A^T)^T=A$
2. $(A+B)^T=A^T+B^T$
3. $(kA)^T=kA^T$
4. $(AB)^T=B^TA^T$
5. $det(A^T)=det(A)$


### Normal

$\begin{aligned}\lVert A\rVert_{1}=\max_j\sum_{i=1}^{m}\lvert a_{i,j}\rvert\end{aligned}$

$\begin{aligned}\lVert A\rVert_{2}=\sqrt{\lambda_1}\end{aligned}$

$\begin{aligned}\lVert A\rVert_{\infty}=\max_j\sum_{j=1}^{m}\lvert a_{i,j}\rvert\end{aligned}$

$\begin{aligned}\lVert A\rVert_{F}=(\sum_{i=1}^m\sum_{j=1}^na^2_{i,j})^{\frac{1}{2}}\end{aligned}$

### Eigen value

$Av=\lambda v$

$det(A-\lambda E)=0$

### Eigen Value Decomposition
假设有 $n\times n$ 方阵$A$，其有$n$个特征值：$\lambda_1\le\lambda_2\le\dots\le\lambda_n$，对应的单位化($w_i^Tw_i=1$)后的特征向量为$w_1,w_2,\dots w_n$,
$W$为$n$个特征向量所张成的$n\times n$矩阵，而$\Sigma$为这$n$个特征值为主对角线的矩阵，则 $A=W\Sigma W^{-1}$ 。这一过程称为EVD。

由EVD分解的形式易知，可进行分解的方阵必然为对称矩阵($A=A^T$)

### Singular Value Decomposition

$A=U\Sigma V^{T}, A,\Sigma\in\mathbb{R}^{m\times n}, U\in\mathbb{R}^{m\times m}, V\in\mathbb{R}^{n\times n}$

假设有 $m\times n$ 矩阵$A$，其有$n$个特征值：$\lambda_1\le\lambda_2\le\dots\le\lambda_n$，对应的单位化($w_i^Tw_i=1$)后的特征向量为$w_1,w_2,\dots w_n$,
$W$为$n$个特征向量所张成的$n\times n$矩阵，而$\Sigma$为这$n$个特征值为主对角线的矩阵，则 $A=W\Sigma W^{-1}$ 。这一过程称为SVD。


### Similiar matrix
Prerequisite
判断相似矩阵的必要条件
设有n阶矩阵A和B，若A和B相似（A∽B），则有：
1. A的特征值与B的特征值相同——λ(A)=λ(B)，特别地，λ(A)=λ(Λ)，Λ为A的对角矩阵；
2. A的特征多项式与B的特征多项式相同——|λE-A|=|λE-B|；
3. A的迹等于B的迹——trA=trB/，其中i=1,2,…n（即主对角线上元素的和）；
4. A的行列式值等于B的行列式值——|A|=|B|；
5. A的秩等于B的秩——r(A)=r(B)。 [1]
因而A与B的特征值是否相同是判断A与B是否相似的根本依据。

Sufficient and necessary condition
矩阵可对角化有两个充要条件：
1. 矩阵有n个不同的特征向量；
2. 特征向量重根的重数等于基础解系的个数。对于第二个充要条件，则需要出现二重以上的重特征值可验证（一重相当于没有重根）。 [1]
若矩阵A可对角化，则其对角矩阵Λ的主对角线元素全部为A的特征值，其余元素全部为0。（一个矩阵的对角阵不唯一，其特征值可以换序，但都存在由对应特征向量顺序组成的可逆矩阵P使=Λ）





#### Rotation

$\begin{pmatrix}\cos\theta&\sin\theta\\-\sin\theta&\cos\theta\end{pmatrix}$



3D空间中任意一个 $v$ 沿着单位向量$u$ 旋转 $\theta$ 角度之后的 $v'$ 为：

$v'=v\cos\theta+(u\cdot v)u(1-\cos\theta)+(u\times v)sin\theta$



$\arctan$

## Quaternions

$Q=ai+bj+ck+\omega$， $a^2+b^2+c^2=1$

$P=(x,y,z)=xi+yj+zk$

$i\times i=j\times j=k\times k=i\times j\times k=-1$

$i\times j=k$,$j\times i=-k$,$j\times k=i$,$k\times j=-i$,$k\times i=j$,$i\times k=-j$

$$QP=aixi+aiyj+aizk+bjxi+bjyj+bjzk+ckxi+ckyj+ckzk+\omega xi+\omega yj+\omega zk\\
 =-ax+ayk-azj-bxk-by+bzi+cxj-cyi-cz+x\omega i+y\omega j+z\omega k\\
=(bz-cy+x\omega)i+(cx-az+y\omega)j+(ay-bx+z\omega)k-(ax+by+cz) $$



欧拉旋转$(\theta,\varphi,\psi)$

$$\begin{aligned}\left\{\begin{array}.x = \sin\frac{\theta}{2}\cos\frac{\varphi}{2}\cos\frac{\psi}{2}+\cos\frac{\theta}{2}\sin\frac{\varphi}{2}\sin\frac{\psi}{2}\\
y = \cos\frac{\theta}{2}\sin\frac{\varphi}{2}\cos\frac{\psi}{2}+\sin\frac{\theta}{2}\cos\frac{\varphi}{2}\sin\frac{\psi}{2}\\
z = \cos\frac{\theta}{2}\cos\frac{\varphi}{2}\sin\frac{\psi}{2}-\sin\frac{\theta}{2}\sin\frac{\varphi}{2}\cos\frac{\psi}{2}\\
w = \cos\frac{\theta}{2}\cos\frac{\varphi}{2}\cos\frac{\psi}{2}-\sin\frac{\theta}{2}\sin\frac{\varphi}{2}\sin\frac{\psi}{2}\end{array}\right.\rarr
q = ((x, y, z), w)\end{aligned}$$

$$(\theta,\varphi,\psi)^T=\begin{pmatrix}\arctan\frac{2xy+yz}{1-2(x^2+y^2)}\\ \arcsin2() \end{pmatrix}$$


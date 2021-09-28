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
| $A^{-1}$            | 矩阵的逆(Inverse)       | $\begin{aligned}A^{-1}=\frac{1}{\lvert A\rvert}A^{*}\end{aligned}$ |
| $A^{*}$             | 伴随矩阵(Adjugate) | $\begin{aligned}M_{ij}\in\mathrm{det}\mathbb{R}^{(n-1)\times(n-1)},A_{ij}=(-1)^{i+j}M_{i,j},A^{*}=\begin{pmatrix}A_{1,1}&A_{1,2}&\dots&A_{1,n}\\A_{2,1}&A_{2,2}&\dots&A_{2,n}\\\vdots&\vdots&\ddots&\vdots\\A_{n,1}&A_{n,2}&\dots&A_{n,n}\end{pmatrix}\end{aligned}$ |
| $A^{H}$             | 共轭矩阵(Hermite/ Conjugate transpose) | $A^H=(\overline{A})^T=\begin{pmatrix}\overline{a}_{1,1}&\overline{a}_{2,1}&\dots&\overline{a}_{m,1}\\\overline{a}_{1,2}&\overline{a}_{2,2}&\dots&\overline{a}_{m,2}\\\vdots&\vdots&\ddots&\vdots\\\overline{a}_{1,n}&\overline{a}_{2,n}&\dots&\overline{a}_{m,n}\end{pmatrix}$ |
| $A^{T}$             | 转置矩阵(Transposition) | $\begin{aligned}A\in\mathbb{R}^{m\times n},A^T\in\mathbb{R}^{n\times m},A^T=\begin{pmatrix}a_{1,1}&a_{2,1}&\dots&a_{m,1}\\a_{1,2}&a_{2,2}&\dots&a_{m,2}\\\vdots&\vdots&\ddots&\vdots\\a_{1,n}&a_{2,n}&\dots&a_{m,n}\end{pmatrix}\end{aligned}$ |
| $\mathrm{tr}A$      | 矩阵的迹(Trace)         | $\begin{aligned}\mathrm{tr}A=\sum_{i=1}^{n}a_{ii}\end{aligned}$ |
| $\rm{det}A$         | 矩阵的行列式            | $\begin{aligned}\rm{det}A=\begin{vmatrix}a_{1,1}&a_{1,2}&a_{1,3}&\dots&a_{1,n}\\a_{2,1}&a_{2,2}&a_{2,3}&\dots&a_{2,n}\\ \vdots&\vdots&\vdots&\ddots&\vdots\\a_{n,1}&a_{n,2}&a_{n,3}&\dots&a_{n,n}\end{vmatrix}\end{aligned}$ |
| $\rm{eig}A$         | 单位矩阵                | $\begin{aligned}\rm{eig}A=\begin{pmatrix}1&&&\\&1&&\\&&\ddots&\\&&&1\end{pmatrix}\in\mathbb{R}^{n\times n}\end{aligned}$ |
| $\lVert A\rVert$    | 范数                    | |
| $A\times B$         | 矩阵乘法                | $\begin{aligned}A_{m\times l}\times B_{l\times n}=A_{m\times l}B_{l\times n}\in \mathbb{R}^{m\times n}\end{aligned}$ |
| $A\circ B$          | 哈达马积(Hadamard product)| $\begin{aligned}A,B\in R^{m\times n},A\circ B=\begin{pmatrix}a_{1,1}b_{1,1}&a_{1,2}b_{1,2}&\dots&a_{1,n}b_{1,n}\\a_{2,1}b_{2,1}&a_{2,2}b_{2,2}&\dots&a_{2,n}b_{2,n}\\\vdots&\vdots&\ddots&\vdots\\a_{m,1}b_{m,1}&a_{m,2}b_{m,2}&\dots&a_{m,n}b_{m,n}\end{pmatrix}\in\mathbb{R}^{m\times n}\end{aligned}$ |
| $A\otimes B$        | 克罗内克积(Kronecker Product)| $\begin{aligned}A^{a\times b}\otimes B^{c\times d}=\begin{pmatrix}a_{1,1}B&a_{1,2}B&\dots&a_{1,b}B\\a_{2,1}B&a_{2,2}B&\dots&a_{2,b}B\\\vdots&\vdots&\ddots&\vdots\\a_{a,1}B&a_{a,2}B&\dots&a_{a,b}B\end{pmatrix}\in\mathbb{R}^{ac\times bd}\end{aligned}$ |







Symmetric matrix（对称阵）：$A=A^T$

Skew-symmetric matrix（反对称阵）：$A^T=-A$

Hermitian matrix（厄米特矩阵）：$A=A^H$

Orthogonal matrix（正交矩阵）：$A^TA=E$

Positive definite matrix（正定矩阵）：$\forall x\ne0, x^TAx>0$

Positive semidefinite matrix（半正定矩阵）：$\forall x\ne0, x^TAx\ge0$

Upper triangle matrix（上三角矩阵）：$A=(a_{ij}),a_{ij}=\left\{\begin{array}l0&i>j\\\forall&other\end{array}\right.$

Upper Hessenberg matrix（上海森伯格矩阵）：$A=(a_{ij}),a_{ij}=\left\{\begin{array}l0&i+j>n+1\\\forall&other\end{array}\right.$

Lower triangle matrix（下三角矩阵）：$A=(a_{ij}),a_{ij}=\left\{\begin{array}l0&i<j\\\forall&other\end{array}\right.$

Lower Hessenberg matrix（下海森伯格矩阵）：$A=(a_{ij}),a_{ij}=\left\{\begin{array}l0&i+j<n+1\\\forall&other\end{array}\right.$



### Adjugate matrix

#### Properties

1. $\exist M=A^{-1}\Leftrightarrow\exist M=(A^*)^{-1}$
2. $\exist M=A^{-1}\Rightarrow A^*=|A|A^{-1}$
3. $\exist M=A^{-1}\Rightarrow (A^{-1})^*=(A^*)^{-1}$
4. $|A^*|=|A|^{n-1}$
5. $(kA)*=k^{n-1}A^*$
6. $(A^T)^*=(A^*)^T$
7. $(AB)^*=B^*A^*$
8. $AA^*=A^*A=|A|E$
9. $rank(A*)=n\Leftrightarrow rank(A)=n$
   $rank(A*)=1\Leftrightarrow rank(A)=n-1$
   $rank(A*)=0\Leftrightarrow rank(A)<n-1$




### Transposition

#### Properties
1. $(A^T)^T=A$
2. $(A+B)^T=A^T+B^T$
3. $(kA)^T=kA^T$
4. $(AB)^T=B^TA^T$
5. $det(A^T)=det(A)$


### Norm

$\begin{aligned}\lVert A\rVert_{1}=\max_j\sum_{i=1}^{m}\lvert a_{i,j}\rvert\end{aligned}$

$\begin{aligned}\lVert A\rVert_{2}=\sqrt{\lambda_1}\end{aligned}$

$\begin{aligned}\lVert A\rVert_{\infty}=\max_j\sum_{j=1}^{m}\lvert a_{i,j}\rvert\end{aligned}$

$\begin{aligned}\lVert A\rVert_{p}=\sqrt[p]{\sum_{i=1}^m\sum_{j=1}^na^p_{i,j}}\end{aligned}$

$\begin{aligned}\lVert A\rVert_{F}=(\sum_{i=1}^m\sum_{j=1}^na^2_{i,j})^{\frac{1}{2}}\end{aligned}$

### Eigen value

$Av=\lambda v$

$det(A-\lambda E)=0$

### Eigen Value Decomposition
假设有 $n\times n$ 方阵$A$，其有$n$个特征值：$\lambda_1\le\lambda_2\le\dots\le\lambda_n$，对应的单位化($w_i^Tw_i=1$)后的特征向量为$w_1,w_2,\dots w_n$,$W=(w_1,w_2,\dots,w_n)$为$n$个特征向量所张成的$n\times n$矩阵，而$\Sigma$为这$n$个特征值为主对角线的矩阵，则 $A=W\Sigma W^{-1}$ 。这一过程称为EVD。

由EVD分解的形式易知，可进行分解的方阵必然为**对称矩阵**($A=A^T$)

### Singular Value Decomposition

$A=U\Sigma V^{T}, A,\Sigma\in\mathbb{R}^{m\times n}, U\in\mathbb{R}^{m\times m}, V\in\mathbb{R}^{n\times n}$

假设有 $m\times n$ 矩阵$A$，其有$n$个特征值：$\lambda_1\le\lambda_2\le\dots\le\lambda_n$，对应的单位化($w_i^Tw_i=1$)后的特征向量为$w_1,w_2,\dots w_n$,

$W=(w_1,w_2,\dots,w_n)$为$n$个特征向量所张成的$n\times n$矩阵，而$\Sigma$为这$n$个特征值为主对角线的矩阵，则 $A=W\Sigma W^{-1}$ 。这一过程称为SVD。


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



**正交矩阵(Orthogonal matrix)**

如果：$AA^T=E$或$A^TA=E$，则$n$阶实矩阵$A$称为正交矩阵

Properties:

0. $A^T$是正交矩阵
1. $A^T$的各行是单位向量且两两正交
2. $A^T$的各列是单位向量且两两正交
3. $(Ax,Ay)=(x,y)x,y\in R$
4. $|A|=1$或-1



**正定矩阵：**给定一个大小为$n\times n$的实对称矩阵$A$，若对于任意长度为$n$的非零向量$x$，有$x^TAx>0$恒成立，则矩阵$A$是一个正定矩阵。

**半正定矩阵：**给定一个大小为$n\times n$的实对称矩阵$A$，若对于任意长度为$n$的非零向量$x$，有$x^TAx\ge 0$恒成立，则矩阵$A$是一个半正定矩阵。



**厄米特矩阵(Hermitian Matrix):**自共轭矩阵，$A=A^H$

Properties:

0. 主对角线元素是实数，转置位的元素互为共轭复数
1. 可逆的埃尔米特矩阵$A$的逆矩$A^{-1}$仍然是埃尔米特矩阵
2. $n$阶厄米特矩阵$A$为正定（半正定）矩阵的充要条件是：$A$的所有特征值大于（大于等于）0。
3. 若$A$是$n$阶厄米特矩阵，其特征值对角阵为$V$，则存在一个[酉矩阵](https://baike.baidu.com/item/酉矩阵)U，使$AU=UV$。
4. 若$A$是$n$阶厄米特矩阵，其弗罗伯尼范数的平方等于其所有特征值的平方和。
5. 主对角线元素皆为实数的埃尔米特矩阵的[特征值](https://baike.baidu.com/item/特征值)均为实数, [斜埃尔米特矩阵](https://baike.baidu.com/item/斜埃尔米特矩阵)的特征值为零或纯虚数。



# Rotation

2D Rotation

$\begin{pmatrix}\cos\theta&\sin\theta\\-\sin\theta&\cos\theta\end{pmatrix}$



3D Rotation

#### Rodrigues' rotation formula

3D空间中任意一个 $v=(x,y,z)$ 沿着单位向量$u=(r,s,t)$ 旋转 $\theta$ 角度之后的 $v'$ 为：

$v'=v\cos\theta+(u\cdot v)u(1-\cos\theta)+(u\times v)\sin\theta$

##### Calculation:

$\begin{aligned}u\times v=\begin{vmatrix}i&j&k\\r&s&t\\x&y&z\end{vmatrix}=(sz-ty,tx-rz,ry-sx)\end{aligned}$

$\begin{aligned}u\cdot v=rx+sy+tz\end{aligned}$

$\begin{aligned}\begin{array}lv'&=&\cos\theta\begin{pmatrix}x\\y\\z\end{pmatrix}+(rx+sy+tz)(1-\cos\theta)\begin{pmatrix}r\\s\\t\end{pmatrix}+\sin\theta\begin{pmatrix}sz-ty\\tx-rz\\ry-sx\end{pmatrix}\\
&=&(2\cos^2\frac{\theta}{2}-1)\begin{pmatrix}x\\y\\z\end{pmatrix}+2(rx+sy+tz)(1-\cos^2\frac{\theta}{2})\begin{pmatrix}r\\s\\t\end{pmatrix}+2\sin\frac{\theta}{2}\cos\frac{\theta}{2}\begin{pmatrix}sz-ty\\tx-rz\\ry-sx\end{pmatrix}\\
&=&(2\cos^2\frac{\theta}{2}-1)\begin{pmatrix}x\\y\\z\end{pmatrix}+2(ax+by+cz)\begin{pmatrix}a\\b\\c\end{pmatrix}+2\cos\frac{\theta}{2}\begin{pmatrix}bz-cy\\cx-az\\ay-bx\end{pmatrix}\\
&=&(2\omega^2-1)\begin{pmatrix}x\\y\\z\end{pmatrix}+2(ax+by+cz)\begin{pmatrix}a\\b\\c\end{pmatrix}+2\omega\begin{pmatrix}bz-cy\\cx-az\\ay-bx\end{pmatrix}\\
&=&\begin{bmatrix}(2\omega^2-1)x\\(2\omega^2-1)y\\(2\omega^2-1)z\end{bmatrix}+\begin{bmatrix}2(ax+by+cz)a\\2(ax+by+cz)b\\2(ax+by+cz)c\end{bmatrix}+\begin{bmatrix}2\omega(bz-cy)\\2\omega(cx-az)\\2\omega(ay-bx)\end{bmatrix}\\
&=&\begin{bmatrix}(2\omega^2-1)x+2(ax+by+cz)a+2\omega(bz-cy)\\(2\omega^2-1)y+2(ax+by+cz)b+2\omega(cx-az)\\(2\omega^2-1)z+2(ax+by+cz)c+2\omega(ay-bx)\end{bmatrix}\\
&=&\begin{bmatrix}(2\omega^2+2a^2-1)x+2(ab-c\omega)y+2(ac+b\omega)z\\2(ab+c\omega)x+(2\omega^2+2b^2-1)y+2(bc-a\omega)z\\2(ac-b\omega)x+2(bc+a\omega)y+(2\omega^2+2c^2-1)z\end{bmatrix}\\
&=&\begin{bmatrix}1-2b^2-2c^2&2ab-2c\omega&2ac+2b\omega\\2ab+2c\omega&1-2a^2-2c^2&2bc-2a\omega\\2ac-2b\omega&2bc+2a\omega&1-2a^2-2b^2\end{bmatrix}\begin{pmatrix}x\\y\\z\end{pmatrix}\\
&=&Rv\end{array}\end{aligned}$

$R$ 即为旋转矩阵，其中$\begin{aligned}\omega=\cos\frac{\theta}{2},a=r\sin\frac{\theta}{2},b=s\sin\frac{\theta}{2},c=t\sin\frac{\theta}{2}\end{aligned}$

#### Quaternions

$Q=ai+bj+ck+\omega$， $a^2+b^2+c^2+\omega^2=1$

$i\times i=j\times j=k\times k=i\times j\times k=-1$

$i\times j=k$,$j\times i=-k$,$j\times k=i$,$k\times j=-i$,$k\times i=j$,$i\times k=-j$

$Q^{-1}=\omega-ai-bj-ck$

Properties: $QQ^{-1}=1$

##### Quaternions Rotation

$P=(x,y,z)=xi+yj+zk$

##### Calculation:

$\begin{array}l QP&=&aixi+aiyj+aizk+bjxi+bjyj+bjzk+ckxi+ckyj+ckzk+\omega xi+\omega yj+\omega zk\\
 &=&-ax+ayk-azj-bxk-by+bzi+cxj-cyi-cz+x\omega i+y\omega j+z\omega k\\
&=&(bz-cy+x\omega)i+(cx-az+y\omega)j+(ay-bx+z\omega)k-(ax+by+cz)\end{array}$

$$\begin{array}l QPQ^{-1}&=&[(bz-cy+x\omega)i+(cx-az+y\omega)j+(ay-bx+z\omega)k-(ax+by+cz)](-ai-bj-ck+\omega)\\
&=&(abz-acy+ax\omega)+(acx-a^2z+ay\omega)k-(a^2y-abx+az\omega)j+(a^2x+aby+acz)i\\
&&-(b^2z-bcy+bx\omega)k+(bcx-abz+by\omega)+(aby-b^2x+bz\omega)i+(abx+b^2y+bcz)j+\\
&&(bcz-c^2y+cx\omega)j-(c^2x-acz+cy\omega)i+(acy-bcx+cz\omega)+(acx+bcy+c^2z)k+\\
&&(bz\omega-cy\omega+x\omega^2)i+(cx\omega-az\omega+y\omega^2)j+(ay\omega-bx\omega+z\omega^2)k-(ax\omega+by\omega+cz\omega)\\
&=&(a^2x+aby+acz+aby-b^2x+bz\omega+bz\omega-cy\omega+x\omega^2-c^2x+acz-cy\omega)i+\\
&&(abx+b^2y+bcz+bcz-c^2y+cx\omega+cx\omega-az\omega+y\omega^2-a^2y+abx-az\omega)j+\\
&&(acx-a^2z+ay\omega+acx+bcy+c^2z+ay\omega-bx\omega+z\omega^2-b^2z+bcy-bx\omega)k+\\
&&(abz-acy+ax\omega+bcx-abz+by\omega+acy-bcx+cz\omega-ax\omega-by\omega-cz\omega)\\
&=&[(\omega^2+a^2-b^2-c^2)x+(2ab-2c\omega)y+(2ac+2b\omega)z]i+\\
&&[(2ab+2c\omega)x+(\omega^2-a^2+b^2-c^2)y+(2bc-a\omega)z]j+\\
&&[(2ac-2b\omega)x+(2bc+2a\omega)y+(\omega^2-a^2-b^2+c^2)z]k+0\\
&=&[(1-2b^2-2c^2)x+(2ab-2c\omega)y+(2ac+2b\omega)z]i+\\
&&[(2ab+2c\omega)x+(1-2a^2-2c^2)y+(2bc-a\omega)z]j+\\
&&[(2ac-2b\omega)x+(2bc+2a\omega)y+(1-2a^2-2b^2)z]k\\
&=&R(Q)P\end{array}$$

其中 $\begin{aligned}R(Q)=\begin{bmatrix}1-2b^2-2c^2&2ab-2c\omega&2ac+2b\omega\\2ab+2c\omega&1-2a^2-2c^2&2bc-2a\omega\\2ac-2b\omega&2bc+2a\omega&1-2a^2-2b^2\end{bmatrix}\end{aligned}$

$\begin{aligned}R(Q)P=\begin{bmatrix}(1-2b^2-2c^2)x+(2ab-2c\omega)y+(2ac+2b\omega)z\\(2ab+2c\omega)x+(1-2a^2-2c^2)y+(2bc-a\omega)z\\(2ac-2b\omega)x+(2bc+2a\omega)y+(1-2a^2-2b^2)z\end{bmatrix}\end{aligned}$

$\omega=\cos\frac{\theta}{2}$，其中$\theta$为绕轴$(a,b,c)$所旋转的角度，$(a,b,c)=\sin\frac{\theta}{2}(r,s,t)$， $a^2+b^2+c^2=\sin^2\frac{\theta}{2}$

$tr(R)=4\omega^2+1$

$\left\{\begin{array}l\omega&=&\frac{\sqrt{tr(R)-1}}{2}\\a&=&\frac{r_{3,2}-r_{2,3}}{4\omega}\\b&=&\frac{r_{1,3}-r_{3,1}}{4\omega}\\c&=&\frac{r_{2,1}-r_{1,2}}{4\omega}\end{array}\right.$



欧拉旋转$(\theta,\varphi,\psi)$

$$\begin{aligned}\left\{\begin{array}.x = \sin\frac{\theta}{2}\cos\frac{\varphi}{2}\cos\frac{\psi}{2}+\cos\frac{\theta}{2}\sin\frac{\varphi}{2}\sin\frac{\psi}{2}\\
y = \cos\frac{\theta}{2}\sin\frac{\varphi}{2}\cos\frac{\psi}{2}+\sin\frac{\theta}{2}\cos\frac{\varphi}{2}\sin\frac{\psi}{2}\\
z = \cos\frac{\theta}{2}\cos\frac{\varphi}{2}\sin\frac{\psi}{2}-\sin\frac{\theta}{2}\sin\frac{\varphi}{2}\cos\frac{\psi}{2}\\
w = \cos\frac{\theta}{2}\cos\frac{\varphi}{2}\cos\frac{\psi}{2}-\sin\frac{\theta}{2}\sin\frac{\varphi}{2}\sin\frac{\psi}{2}\end{array}\right.\rarr
q = ((x, y, z), w)\end{aligned}$$

$$(\theta,\varphi,\psi)^T=\begin{pmatrix}\arctan\frac{2xy+yz}{1-2(x^2+y^2)}\\ \arcsin2() \end{pmatrix}$$



# QR Decomposition

矩阵的正交分解又称为QR分解，是将矩阵分解为一个正交矩阵Q和一个上三角矩阵的乘积的形式。
**任意实数方阵A，都能QR分解**。这里的Q为正交单位阵，R是一个上三角矩阵。这种分解被称为QR分解。

## Gram–Schmidt Decomposition

$n$阶的满秩方阵$A$的列向量：$\alpha_1,\alpha_2,\alpha_3,\dots,\alpha_n$，通过转换变得到$n$个新的向量，$\beta_1,\beta_2,\beta_3,\dots,\beta_n$，其中$\begin{aligned}\beta_i=\alpha_i-\sum_{j=1}^{i-1}\frac{a_i^T\beta_j}{\beta^T_j\beta_j}\beta_j\end{aligned}$

以$\begin{aligned}\frac{\beta_i}{||\beta_i||}\end{aligned}$为列向量，组成新的方阵$Q=\begin{pmatrix}\frac{\beta_1}{||\beta_1||},\frac{\beta_2}{||\beta_2||},\cdots,\frac{\beta_n}{||\beta_n||}\end{pmatrix}$ 

构造$n$阶的方阵$S=\begin{pmatrix}s_{ij}\end{pmatrix}$ ，其中$1\le i,j\le n$，$s_{ij}=\left\{\begin{array}c ||\beta_i||&i=j\\0&i\neq j\end{array}\right.$

构造$n$阶的方阵$P=\begin{pmatrix}p_{ij}\end{pmatrix}$ ，其中$1\le i,j\le n$，$\begin{aligned}p_{ij}=\left\{\begin{array}c \frac{\alpha_j^T\beta_i}{\beta_i^T\beta_i}&i<j\\1&i=j\\0&i> j\end{array}\right.\end{aligned}$

则上三角方阵$R=SP$ 与$Q$为$A$的QR分解。



##### Proof:

* $\forall i\le n,\beta_i\neq0$
* 当$1\le i\neq j\le n$时，$\beta_i^T\beta_j=0$
* $Q^TQ=E$
* $A=QR$

1）$\because $ $A$满秩  $\therefore$ $\forall i\neq j, \alpha_i,\alpha_j$ 线性无关且不为0，易知$\forall i\le n,\beta_i\neq0$

2）由于$\beta_i^T\beta_j=\beta_j^T\beta_i$，不妨令$i<j$。首先：

$\begin{aligned}\begin{array}l\beta_1^T\beta_2&=&\alpha_1^T(\alpha_2-\frac{\alpha_2^T\beta_1}{\beta_1^T\beta_1}\beta_1)\\
&=&\alpha_1^T\alpha_2-\frac{\alpha_2^T\alpha_1}{\alpha_1^T\alpha_1}\alpha_1^T\alpha_1\\
&=&\alpha_1^T\alpha_2-\alpha_2^T\alpha_1\\
&=&0\end{array}\end{aligned}$

假设对于任意$1<t\le i$的$t$都有 $\beta_1^T\beta_t=0$，则

$\begin{aligned}\begin{array}l\beta_1^T\beta_{i+1}&=&\beta_1^T(\alpha_{i+1}-\sum\limits_{j=1}^i\frac{\alpha_{i+1}^T\beta_j}{\beta_j^T\beta_j}\beta_j)\\
&=&\beta_1^T\alpha_{i+1}-\sum\limits_{j=1}^i\frac{\alpha_{i+1}^T\beta_j}{\beta_j^T\beta_j}\beta_1^T\beta_j\\
&=&\beta_1^T\alpha_{i+1}-\frac{\alpha_{i+1}^T\beta_1}{\beta_1^T\beta_1}\beta_1^T\beta_1\\
&=&\beta_1^T\alpha_{i+1}-\alpha_{i+1}^T\beta_1=0\end{array}\end{aligned}$

故而，归纳得$\forall i\le n$，均有 $\beta_1^T\beta_i=\beta_i^T\beta_1=0$。

$\begin{aligned}\begin{array}l\beta_2^T\beta_3&=&\beta_2^T(\alpha_3-\frac{\alpha_3^T\beta_1}{\beta_1^T\beta_1}\beta_1-\frac{\alpha_3^T\beta_2}{\beta_2^T\beta_2}\beta_2)\\
&=&\beta_2^T\alpha_3-\frac{\alpha_3^T\beta_2}{\beta_2^T\beta_2}\beta_2^T\beta_2\\
&=&0\end{array}\end{aligned}$

假设对于任意$1<t\le i$的$t$都有 $\beta_t^T\beta_{t+1}=0$，则

$\begin{aligned}\begin{array}l\beta_{i+1}^T\beta_{i+2}&=&\beta^T_{i+1}(\alpha_{i+2}-\sum\limits_{t=1}^{i+1}\frac{\alpha_{i+2}^T\beta_t}{\beta_t^T\beta_t}\beta_t)\\
&=&\beta_{i+1}^T\alpha_{i+2}-\frac{\alpha_{i+2}^T\beta_{i+1}}{\beta_{i+1}^T\beta_{i+1}}\beta_{i+1}^T\beta_{i+1}\\
&=&0\end{array}\end{aligned}$

$\therefore \forall i\neq j\le n,\beta_i^T\beta_j=0$



$\beta_2^T\alpha_3-\frac{\alpha_3^T\beta_1}{\beta_1^T\beta_1}\beta_2^T\beta_1-\frac{\alpha_3^T\beta_2}{\beta_2^T\beta_2}\beta_2^T\beta_2$

$\begin{aligned}\begin{array}l\beta_2^T\beta_3&=&(\alpha_2-\frac{\alpha_2^T\beta_1}{\beta_1^T\beta_1}\beta_1)^T(\alpha_3-\frac{\alpha_3^T\beta_1}{\beta_1^T\beta_1}\beta_1-\frac{\alpha_3^T\beta_2}{\beta_2^T\beta_2}\beta_2)\\
&=&\alpha_2^T\alpha_3-\alpha_2^T\frac{\alpha_3^T\alpha_1}{\alpha_1^T\alpha_1}\alpha_1-\alpha_2^T\frac{\alpha_3^T\beta_2}{\beta_2^T\beta_2}\beta_2-\frac{\alpha_2^T\beta_1}{\beta_1^T\beta_1}\beta_1^T\alpha_3+\frac{\alpha_2^T\beta_1}{\beta_1^T\beta_1}\beta_1^T\frac{\alpha_3^T\beta_1}{\beta_1^T\beta_1}\beta_1+\frac{\alpha_2^T\beta_1}{\beta_1^T\beta_1}\beta_1^T\frac{\alpha_3^T\beta_2}{\beta_2^T\beta_2}\beta_2\\
&=&\alpha_2^T\alpha_3-\frac{\alpha_3^T\alpha_1}{\alpha_1^T\alpha_1}\alpha_2^T\alpha_1-\frac{\alpha_3^T\beta_2}{\beta_2^T\beta_2}\alpha_2^T\beta_2-\frac{\alpha_2^T\beta_1}{\beta_1^T\beta_1}\beta_1^T\alpha_3+\frac{\alpha_2^T\beta_1}{\beta_1^T\beta_1}\frac{\alpha_3^T\beta_1}{\beta_1^T\beta_1}\beta_1^T\beta_1\\
&=&\alpha_2^T\alpha_3-\frac{\alpha_3^T\alpha_1}{\alpha_1^T\alpha_1}\alpha_2^T\alpha_1-\frac{\alpha_3^T\beta_2}{\beta_2^T\beta_2}\alpha_2^T\beta_2\\
&=&\alpha_1^T\alpha_3-\alpha_3^T\alpha_1-\frac{\alpha_3^T\beta_2}{\beta_2^T\beta_2}(\alpha_1^T\alpha_2-\alpha_2^T\alpha_1)=0\end{array}\end{aligned}$



$\alpha_2^T\alpha_3-\frac{\alpha_3^T\alpha_1}{\alpha_1^T\alpha_1}\alpha_2^T\alpha_1-\frac{\alpha_3^T\beta_2}{\beta_2^T\beta_2}\alpha_2^T\beta_2$

$\begin{aligned}\begin{array}l\beta_i^T\beta_j&=&(\alpha_i-\sum\limits_{l=1}^{i-1}\frac{a_i^T\beta_l}{\beta^T_l\beta_l}\beta_l)^T(\alpha_j-\sum\limits_{k=1}^{j-1}\frac{a_j^T\beta_k}{\beta^T_k\beta_k}\beta_k)\\
&=&\sum\limits_{t=1}^n(a_{it}-\sum\limits_{l=1}^{i-1}\frac{a_i^T\beta_l}{\beta^T_l\beta_l}b_{lt})(a_{jt}-\sum\limits_{k=1}^{j-1}\frac{a_j^T\beta_k}{\beta^T_k\beta_k}b_{kt})\\
&=&\alpha_i^T\alpha_j+\sum\limits_{t=1}^n(\sum\limits_{l=1}^{i-1}\frac{a_i^T\beta_l}{\beta^T_l\beta_l}b_{lt}\sum\limits_{k=1}^{j-1}\frac{a_j^T\beta_k}{\beta^T_k\beta_k}b_{kt})-\sum\limits_{t=1}^n(a_{jt}\sum\limits_{l=1}^{i-1}\frac{a_i^T\beta_l}{\beta^T_l\beta_l}b_{lt}+a_{it}\sum\limits_{k=1}^{j-1}\frac{a_j^T\beta_k}{\beta^T_k\beta_k}b_{kt})\\
&=&0\end{array}\end{aligned}$



3）$Q^TQ=\begin{pmatrix}a_{ij}\end{pmatrix}$

$\begin{aligned}a_{ij}=\frac{\beta_i^T\beta_j}{||\beta_i||\cdot||\beta_j||}=\left\{\begin{array}l\frac{\beta_i^T\beta_i}{||\beta_i||^2}=1&i=j\\0&i\neq j\end{array}\right.\end{aligned}$

$Q^TQ=\underbrace{\begin{pmatrix}1&0&\cdots&0\\0&1&\cdots&0\\\vdots&\vdots&\ddots&\vdots\\0&0&\cdots&1\end{pmatrix}}_{n}=E$

4）  $R=SP=\begin{pmatrix}||\beta_1||&\frac{\alpha_2^T\beta_1}{||\beta_1||}&\frac{\alpha_3^T\beta_1}{||\beta_1||}&\dots&\frac{\alpha_n^T\beta_1}{||\beta_1||}\\
0&||\beta_2||&\frac{\alpha_3^T\beta_2}{||\beta_2||}&\dots&\frac{\alpha_n^T\beta_2}{||\beta_2||}\\
\vdots&\vdots&\vdots&\ddots&\vdots\\
0&0&0&\dots&||\beta_n||\end{pmatrix}$

设$QR$的列向量 $QR=(\gamma_1,\gamma_2,\dots,\gamma_n)$

$\gamma_1=\frac{\beta_1}{||\beta_1||}||\beta_1||=\beta_1=\alpha_1$

$\gamma_2=\frac{\beta_1}{||\beta_1||}\frac{\alpha_2^T\beta_1}{||\beta_1||}+\frac{\beta_2}{||\beta_2||}||\beta_2||=\frac{\alpha_2^T\beta_1}{\beta_1^T\beta_1}\beta_1+\beta_2=\alpha_2$

$\gamma_i=\sum\limits_{t=1}^{i-1}\frac{\alpha_i^T\beta_t}{\beta_t^T\beta_t}\beta_t+\beta_i=\alpha_i$

故而 $QR=(\gamma_1,\gamma_2,\dots,\gamma_n)=(\alpha_1,\alpha_2,\dots,\alpha_n)=A$



# LU Decomposition

可以将一个矩阵分解为一个单位下三角矩阵和一个上三角矩阵的乘积







# Givens transformation

**[Definition]** 平面旋转变换$G$：对$n$阶单位矩阵的$l,k$列（$l<k$）向量替换为第$l,k$分量的向量为$\theta$ 的二维旋转向量，而形成的矩阵$G$：

$G(\theta,l,k)=\begin{bmatrix}1&\\&\ddots&\\&&1&\\
&&&\cos\theta&\cdots&\sin\theta&\\
&&&\vdots&\ddots&\vdots&\\
&&&-\sin\theta&\cdots&\cos\theta&\\
&&&&&&1&\\
&&&&&&&\ddots&\\
&&&&&&&&1\end{bmatrix}$

$G=(g_{ij})$，$g_{ij}=\left\{\begin{array}l\cos\theta&i=j\wedge i=l,k\\-\sin\theta&i=k,j=l\\\sin\theta&i=l,j=k\\1&i=j\wedge i\neq l,k\\0&other\end{array}\right.$

#### Properties:

1. $GG^T=E$
2. $G(\alpha,l,k)G(\beta,l,k)=G(\alpha+\beta,l,k)$
3. $|Gv|=|v|$



$Gv=(\underbrace{v_1,v_2,\dots,v_l\cos\theta+v_k\sin\theta}_{l},\underbrace{v_{l+1},\dots,v_k\cos\theta-v_l\sin\theta}_{k-l},v_{k+1},\dots,v_n)$

故当$\theta=\arctan\frac{v_k}{v_l}$时，$Gv=(v_1,v_2,\dots,\sqrt{v_l^2+v_k^2},v_{l+1},\dots,0,v_{k+1},\dots,v_n)$



#### Practice:

$\begin{array}l |Gv|&=&\sqrt{(Gv)^TGv}\\
&=&\sqrt{v^TG^TGv}\\
&=&\sqrt{v^TEv}\\
&=&\sqrt{v^Tv}=|v|\end{array}$



# Householder transformation

**[Definition]** 反射变换$H$： $v\in\mathbb{C}^{n\times1},|v|=1$​ ， $H=E-2vv^H$​

#### Properties:

1. $HH=E$
2. $H^T=H$
3. $\forall u\cdot v=0\Rightarrow Hu=u$
   $\forall\lambda\in\mathbb{R},u=\lambda v\Rightarrow Hu=-u$
4. $|u|=|Hu|$

#### Householder Decomposition

对于一个非零向量$u=(u_1,u_2,\dots,u_n)^T$，构造新向量 $t=(u_1+|u|,u_2,\dots,u_n)^T$，$\begin{aligned}v=\frac{t}{|t|}=(v_1,v_2,\dots,v_n)^T\end{aligned}$，可计算得：

$\begin{array}l|t|&=&\sqrt{(u_1+|u|)^2+\sum\limits_{i=2}^nu_i^2}\\
&=&\sqrt{\sum\limits_{i=1}^nu_i^2+2u_1|u|+|u|^2}\\
&=&\sqrt{2|u|t_1}\end{array}$

$\therefore\quad\begin{aligned}v_i=\frac{t_i}{|t|}=\left\{\begin{array}c\frac{u_1+|u|}{|t|}&i=1\\\frac{u_i}{|t|}&1<i\le n\end{array}\right.\end{aligned}$

$\begin{array}lv^Tu&=&\sum\limits_{i=1}^nv_iu_i\\
&=&\frac{u_i^2+2u_1|u|+|u|^2+\sum\limits_{i=2}^nu_i^2}{|t|}\\
&=&\frac{2(u_1|u|+|u|^2)}{|t|}\\
&=&\frac{2|u|t_1}{|t|}=|t|\end{array}$

$vv^Tu=|t|v=t$

$\begin{array}lHu&=&u-vv^Tu\\
&=&u-t\\
&=&(-|u|,\underbrace{0,0,\dots,0}_{n-1})^T\end{array}$

相应地，对向量$u$扩展$m$维，得$n+m$维的新向量$r=(\underbrace{\forall,\forall,\dots,\forall}_{m},u_1,u_2,\dots,u_n)^T$

构造新向量 $t=(\underbrace{0,0,\dots,0}_{m},u_1+|u|,u_2,\dots,u_n)^T$，$\begin{aligned}v=\frac{t}{|t|}\end{aligned}$，其余计算与扩展前一致，易得：

$\begin{array}lHr&=&r-vv^Tr\\
&=&r-t\\
&=&(\underbrace{\forall,\forall,\dots,\forall}_{m},-|u|,\underbrace{0,0,\dots,0}_{n-1})^T\end{array}$

在此过程中，该变换可以对向量指定部分分量置零，且$|Hu|=|u|$

#### Practice:

$\begin{array}l HH&=&(E-2vv^T)(E-2vv^T)\\&=&E-4vv^T+4vv^Tvv^T\\&=&E-4vv^T+4v(v^Tv)v^T\\&=&E-4vv^T+4v|v|^2v^T\\&=&E-4vv^T+4vv^T=E\end{array}$

$\begin{array}l |Hu|&=&|(E-2vv^T)u|\\
&=&\sqrt{(u-2vv^Tu)^T(u-2vv^Tu)}\\
&=&\sqrt{u^Tu-2v^Tuv^Tu-2u^Tvv^Tu+4v^Tuv^Tv}\\
&=&\sqrt{u^Tu-2(v^Tu)^2-2(u^Tv)^2+4(v^Tu)^2}\\
&=&\sqrt{u^Tu-4(v^Tu)^2+4(v^Tu)^2}\\
&=&\sqrt{u^Tu}=|u|\end{array}$





#### Practice:

$$\begin{aligned}a=\begin{bmatrix}a_1\\a_2\\a_3\end{bmatrix},a^{\wedge}=A=\begin{bmatrix}0&-a_3&a_2\\a_3&0&-a_1\\-a_2&a_1&0\end{bmatrix},A^{\vee}=a\end{aligned}$$

$$\begin{aligned}aa^T=\begin{bmatrix}a_1^2&a_1a_2&a_1a_3\\a_1a_2&a_2^2&a_2a_3\\a_1a_3&a_2a_3&a_3^2\end{bmatrix}\end{aligned}$$

$a^{\wedge}a^{\wedge}=aa^T-E$ ,    $a^{\wedge}aa^T=[0]$

$a^{\wedge}a^{\wedge}a^{\wedge}=a^{\wedge}(aa^T-E)=-a^{\wedge}=A^T$



##### Proof:

$$\begin{aligned}a^{\wedge}aa^T=\begin{bmatrix}-a_1a_2a_3+a_1a_2a_3&-a_2^2a_3+a_2^2a_3&-a_2a_3^2+a_2a_3^2\\
a_1^2a_3-a_1^2a_3&a_1a_2a_3-a_1a_2a_3&a_1a_3^2-a_1a_3^2\\
-a_1^2a_2+a_1a_2a_3&-a_1a_2^2+a_1a_3^2&-a_1a_2a_3+a_1a_2a_3\end{bmatrix}=\begin{bmatrix}0&0&0\\0&0&0\\0&0&0\end{bmatrix}\end{aligned}$$


Linear Algebra
==============

## Matrix


$$A=\begin{pmatrix}	a_{1,1} & a_{1,2} & a_{1,3} & \dots & a_{1,n} \\\
a_{2,1} & a_{2,2} & a_{2,3} & \dots & a_{2,n} \\\
\vdots & \vdots & \vdots & \ddots & \vdots \\\
a_{m,1} & a_{m,2} & a_{m,3} & \dots & a_{m,n} \end{pmatrix},\quad A\in\mathbb{R}^{m\times n} $$

| Operation           |        Comment          | Description         |
| ------------------- | ----------------------- | ------------------- |
| $A^{-1}$            | 矩阵的逆                | $\begin{aligned}A^{-1}=\frac{1}{\lvert A\rvert}A^{*}\end{aligned}$ |
| $A^{*}$             | 伴随矩阵                | $\begin{aligned}M_{ij}\in\rm{det}\mathbb{R}^{(n-1)\times(n-1)},A_{ij}=(-1)^{i+j}M_{i,j},A^{*}=\begin{pmatrix}A_{1,1}&A_{1,2}&\dots&A_{1,n}\\A_{2,1}&A_{2,2}&\dots&A_{2,n}\\\vdots&\vdots&\ddots&\vdots\\A_{n,1}&A_{n,2}&\dots&A_{n,n}\end{pmatrix}\end{aligned}$|
| $A^{H}$             | 共轭矩阵                | |
| $A^{T}$             | 转置矩阵(Transposition) | $\begin{aligned}A\in\mathbb{R}^{m\times n},A^T\in\mathbb{R}^{n\times m},A^T=\begin{pmatrix}a_{1,1}&a_{2,1}&\dots&a_{m,1}\\a_{1,2}&a_{2,2}&\dots&a_{m,2}\\\vdots&\vdots&\ddots&\vdots\\a_{1,n}&a_{2,n}&\dots&a_{m,n}\end{pmatrix}\end{aligned}$ |
| $trA$               | 矩阵的迹(Trace)         | $\begin{aligned}trA=\sum_{i=1}^{n}a_{ii}\end{aligned}$ |
| $\rm{det}A$         | 矩阵的行列式            | $\begin{aligned}\rm{det}A=\begin{vmatrix}a_{1,1}&a_{1,2}&a_{1,3}&\dots&a_{1,n}\\a_{2,1}&a_{2,2}&a_{2,3}&\dots&a_{2,n}\\ \vdots&\vdots&\vdots&\ddots&\vdots\\a_{n,1}&a_{n,2}&a_{n,3}&\dots&a_{n,n}\end{vmatrix}\end{aligned}$ |
| $\rm{eig}A$         | 单位矩阵                | $\begin{aligned}\rm{eig}A=\begin{pmatrix}1&&&\\&1&&\\&&\ddots&\\&&&1\end{pmatrix}\in\mathbb{R}^{n\times n}\end{aligned}$ |
| $\lVert A\rVert$    | 范数                    | |
| $A\times B$         | 矩阵乘法                | $\begin{aligned}A_{m\times l}\times B_{l\times n}=A_{m\times l}B_{l\times n}\in \mathbb{R}^{m\times n}\end{aligned}$ |
| $A\circ B$          | 哈达马积(Hadamard product)| $\begin{aligned}A,B\in R^{m\times n},A\circ B=\begin{pmatrix}a_{1,1}b_{1,1}&a_{1,2}b_{1,2}&\dots&a_{1,n}b_{1,n}\\&&\vdots&\\a_{m,1}b_{m,1}&a_{m,2}b_{m,2}&\dots&a_{m,n}b_{m,n}\end{pmatrix}\in\mathbb{R}^{m\times n}\end{aligned}$ |
| $A\otimes B$        | 克罗内克积(Kronecker Product)| $\begin{aligned}A^{a\times b}\otimes B^{c\times d}=\begin{pmatrix}a_{1,1}B&a_{1,2}B&\dots&a_{1,b}B\\&&\vdots&\\a_{a,1}B&a_{a,2}B&\dots&a_{a,b}B\end{pmatrix}\in\mathbb{R}^{ac\times bd}\end{aligned}$ |








$\begin{aligned}\lVert A\rVert_{1}=\max_j\sum_{i=1}^{m}\lvert a_{i,j}\rvert\end{aligned}$

$\begin{aligned}\lVert A\rVert_{2}=\sqrt{\lambda_1}\end{aligned}$

$\begin{aligned}\lVert A\rVert_{\infin}=\max_j\sum_{j=1}^{m}\lvert a_{i,j}\rvert\end{aligned}$

$\begin{aligned}\lVert A\rVert_{F}=(\sum_{i=1}^m\sum_{j=1}^na^2_{i,j})^{\frac{1}{2}}\end{aligned}$

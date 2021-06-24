Bezier Curve Mathematical Principle
===================================

## Linear Curve
$$ P = \begin{pmatrix}x_1&y_1\\x_2&y_2\end{pmatrix} $$

$$\begin{align}
x &= \lambda x_2 +(1-\lambda)x_1\\
&= (x_2-x_1) \lambda + x_1
\end{align}$$

$$\begin{align} \left\{\begin{array} \quad
x &= (x_2-x_1) \lambda + x_1\\
y &= (y_2-y_1) \lambda + y_1
\end{array}\right.\end{align}$$

Let $R=\begin{pmatrix}-1&1\\ 1&0\end{pmatrix}$ and $\Lambda=\begin{pmatrix} \lambda & 1 \end{pmatrix}$ ,
then $ f(\lambda)=\Lambda R P =\begin{pmatrix}x & y\end{pmatrix}$, which $\lambda\in[0,1]$ the
linear curve consists of.



## Quadratic Curve
$$ P=\begin{pmatrix}x_1&y_1\\x_2&y_2\\x_3&y_3\end{pmatrix} $$

$$\begin{align}
x &= (1-\lambda)[\lambda x_2 +(1-\lambda)x_1] + \lambda[\lambda x_3 + (1-\lambda)x_2]\\
&= (\lambda-\lambda^2)x_2 +(1-\lambda)^2x_1 + \lambda^2 x_3 + (\lambda-\lambda^2)x_2 \\
&= (\lambda-\lambda^2)x_2 +(1-2\lambda+\lambda^2)x_1 + \lambda^2 x_3 + (\lambda-\lambda^2)x_2 \\
&= (x_1-2x_2+x_3) \lambda^2 + 2(x_2-x_1)\lambda+x_1
\end{align}$$

$$\begin{align} \left\{\begin{array} \quad
x &= (x_1-2x_2+x_3)\lambda^2+2(x_2-x_1)\lambda+x_1 \\
y &= (y_1-2y_2+y_3)\lambda^2+2(y_2-y_1)\lambda+y_1
\end{array}\right.\end{align}$$

Let $R=\begin{pmatrix}1&-2&1\\ -2&2&\\ 1 &&\end{pmatrix}$ and $\Lambda=\begin{pmatrix} \lambda^2 & \lambda & 1 \end{pmatrix}$,
then $ f(\lambda)=\Lambda R P =\begin{pmatrix}x& y\end{pmatrix}$, which $\lambda\in[0,1]$ the
quadratic curve consists of .

## Cubic Curve
$$ P=\begin{pmatrix}x_1&y_1\\x_2&y_2\\x_3&y_3\\x_4&y_4\end{pmatrix} $$

$$\begin{align}
x &= (1-\lambda)\{(1-\lambda)[(1-\lambda)x_1+\lambda x_2]+\lambda[(1-\lambda)x_2+\lambda x_3]\}+\lambda\{(1-\lambda)[(1-\lambda)x_2+\lambda x_3]+\lambda[(1-\lambda)x_3+\lambda x_4]\}\\
&= (1-\lambda)\{[(1-\lambda)^2x_1+\lambda(1-\lambda)x_2]+[\lambda(1-\lambda)x_2+\lambda^2 x_3]\}+\lambda\{[(1-\lambda)^2x_2+\lambda(1-\lambda) x_3]+[\lambda(1-\lambda)x_3+\lambda^2x_4]\}\\
&= (1-\lambda)^3x_1+\lambda(1-\lambda)^2x_2+\lambda(1-\lambda)^2x_2+\lambda^2(1-\lambda)x_3+\lambda(1-\lambda)^2x_2+\lambda^2(1-\lambda)x_3+\lambda^2(1-\lambda)x_3+\lambda^3x_4\\
&= (1-3\lambda+3\lambda^2-\lambda^3)x_1+(\lambda-2\lambda^2+\lambda^3)x_2+(\lambda-2\lambda^2+\lambda^3)x_2+(\lambda^2-\lambda^3)x_3+(\lambda-2\lambda^2+\lambda^3)x_2+(\lambda^2-\lambda^3)x_3+(\lambda^2-\lambda^3)x_3+\lambda^3x_4\\
&= (-x_1+3x_2-3x_3+x_4)\lambda^3+(3x_1-6x_2+3x_3)\lambda^2+(-3x_1+3x_2)\lambda+x_1\\
&= (-x_1+3x_2-3x_3+x_4)\lambda^3+3(x_1-2x_2+x_3)\lambda^2+3(-x_1+x_2)\lambda+x_1
\end{align}$$


$$\begin{align} \left\{\begin{array} \quad
x &= (3x_2-3x_3+x_4-x_1)\lambda^3+3(x_1-2x_2+x_3)\lambda^2+3(x_2-x_1)\lambda+x_1 \\
y &= (3y_2-3y_3+y_4-y_1)\lambda^3+3(y_1-2y_2+y_3)\lambda^2+3(y_2-y_1)\lambda+y_1
\end{array}\right.\end{align}$$


Let $R=\begin{pmatrix}-1&3&-3&1\\ 3&-6&3&\\-3&3&& \\ 1 &&&\end{pmatrix}$ and $\Lambda=\begin{pmatrix} \lambda^3 & \lambda^2 & \lambda & 1 \end{pmatrix}$,
then $ f(\lambda)=\Lambda R P =\begin{pmatrix}x& y\end{pmatrix}$, which $\lambda\in[0,1]$ the
cubic curve consists of.

## Four Order Curve
$$P=\begin{pmatrix}x_1& y_1\\ x_2& y_2\\x_3&y_3 \\x_4&y_4 \\x_5&y_5 \end{pmatrix}$$

$$\begin{align}
x &= (1-\lambda)\{(1-\lambda)\{(1-\lambda)[(1-\lambda)x_1+\lambda x_2]+\lambda[(1-\lambda)x_2+\lambda x_3]\}+\lambda\{(1-\lambda)[(1-\lambda)x_2+\lambda x_3]+\lambda[(1-\lambda)x_3+\lambda x_4]\} +x_5\}+\lambda\{(1-\lambda)\{(1-\lambda)[(1-\lambda)x_1+\lambda x_2]+\lambda[(1-\lambda)x_2+\lambda x_3]\}+\lambda\{(1-\lambda)[(1-\lambda)x_2+\lambda x_3]+\lambda[(1-\lambda)x_3+\lambda x_4]\}\}\\\
&= (1-\lambda)\{[(1-\lambda)^2x_1+\lambda(1-\lambda)x_2]+[\lambda(1-\lambda)x_2+\lambda^2 x_3]\}+\lambda\{[(1-\lambda)^2x_2+\lambda(1-\lambda) x_3]+[\lambda(1-\lambda)x_3+\lambda^2x_4]\}\\
&= (1-\lambda)^3x_1+\lambda(1-\lambda)^2x_2+\lambda(1-\lambda)^2x_2+\lambda^2(1-\lambda)x_3+\lambda(1-\lambda)^2x_2+\lambda^2(1-\lambda)x_3+\lambda^2(1-\lambda)x_3+\lambda^3x_4\\
&= (1-3\lambda+3\lambda^2-\lambda^3)x_1+(\lambda-2\lambda^2+\lambda^3)x_2+(\lambda-2\lambda^2+\lambda^3)x_2+(\lambda^2-\lambda^3)x_3+(\lambda-2\lambda^2+\lambda^3)x_2+(\lambda^2-\lambda^3)x_3+(\lambda^2-\lambda^3)x_3+\lambda^3x_4\\
&= (-x_1+3x_2-3x_3+x_4)\lambda^3+(3x_1-6x_2+3x_3)\lambda^2+(-3x_1+3x_2)\lambda+x_1\\
&= (-x_1+3x_2-3x_3+x_4)\lambda^3+3(x_1-2x_2+x_3)\lambda^2+3(-x_1+x_2)\lambda+x_1
\end{align}$$


Let $R=\begin{pmatrix}-1&3&-3&1\\ 3&-2&3&\\-3&3&& \\ 1 &&&\end{pmatrix}$, $\Lambda=\begin{pmatrix}\lambda^4& \lambda^3 & \lambda^2 & \lambda & 1 \end{pmatrix}$,
then $f(\lambda)=\Lambda R P =\begin{pmatrix}x& y\end{pmatrix}$, which $\lambda\in[0,1]$ the
cubic curve consists of.

## Bernstein Base Function
$$B_{i,n}(t)=\left\{\begin{array}=0&t=0,1\\>0&t\in(0,1),i=1,2,\dots,n-1\end{array}\right.$$

$$B_{i,n}(t)=(1-t)B_{i,n-1}(t)+tB_{i-1,n-1}(t)\quad i=0,1,\dots,n $$
## N-Order Curve
$$ P=\begin{pmatrix}x_1&y_1\\x_2&y_2\\ \vdots&\vdots \\x_n&y_n\end{pmatrix} $$

Let $R=\begin{pmatrix}-1&3&-3&1\\ 3&-2&3&\\-3&3&& \\ 1 &&&\end{pmatrix}$, $\Lambda=\begin{pmatrix}\lambda^n&\dots& \lambda^3 & \lambda^2 & \lambda & 1 \end{pmatrix}$,
then $f(\lambda)=\Lambda R P =\begin{pmatrix}x& y\end{pmatrix}$, which $\lambda\in[0,1]$ the
cubic curve consists of.

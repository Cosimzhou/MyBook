

# 插值

## 三点插值

取三个点$(x_1,y_1),(x_2,y_2),(x_3,y_3)$，其中$(x2-x1)=(x3-x2)$，可以如下求出$a,b,c$
$$
\begin{matrix}
x_1 & y_1 \\
& &a\\
x_2 & y_2& &    c\\
& &b\\
x_3&y_3
\end{matrix}
$$
其中三次差分为0

$$\begin{aligned}\left\{\begin{array}\qaud a& =& y_2-y_1\\ b& =& y_3-y_2\\ c& =& b -a = y_1+y_3-2y_2\end{array}\right.\end{aligned}$$



#### 当知$x'$（与$x_2$相邻）求$y'$

$\begin{aligned}y' = y_2+\frac{r}{2}(a+b+cn)\end{aligned}$    （$\begin{aligned}r=\frac{x'-x}{x_2-x_1}\end{aligned}$，$\lvert r\rvert<0.5$）



#### 求三点区间内的极值

$$\begin{aligned}
y_m = y_2 - \frac{(a+b)^2}{8c} \\
n_m = -\frac{a+b}{2c}\end{aligned}
$$







#### 插值求逆：$y=0$，求$x$对应的$n_0$：

$\begin{aligned}n_0 = -\frac{2y^2}{a+b+c*n_0}\end{aligned}$    以0为初值迭代至稳定

$\begin{aligned}\Delta n_0 = -\frac{ 2y_2+n_0(a+b+cn_0) }{a+b+2cn_0}\end{aligned}$    差值迭代



## 中点插值

$$
\begin{matrix}
x_1&y_1\\
x_2&y_2\\
x_3&y_3\\
x_4&y_4
\end{matrix}
$$



求$\begin{aligned}x=\frac{x_2+x_3}{2}\end{aligned}$对应的y值：$\begin{aligned}y=\frac{1}{16}[9(y_2+y_3)-y_1-y_4]\end{aligned} $



## 五点插值

$$
\begin{matrix}
x_1 & y_1 \\
& & A\\
x_2 & y_2 & & E\\
& & B & & H\\
x_3 & y_3 & & F & & K\\
& & C & & J\\
x_4 & y_4 & & G\\
& & D\\
x_5 & y_5
\end{matrix}
$$



#### 当知知$x'$（与x3相邻）求$y'$

$\begin{aligned} y' = y_3+\frac{[(B+C)-(H+J)]r}{2}+\frac{(12F-K)r^2}{24}+\frac{(H+J)r^3}{12}+\frac{Kn^4}{24} \end{aligned}$ （$\begin{aligned}r=\frac{x'-x}{x_3-x_2}\end{aligned}$，$\lvert r\rvert <0.5$）



求极值：$\begin{aligned}n_m = \frac{6B=6C-H-J+3nm^2(H+J)+2n_m^3K}{K-12F}\end{aligned}$

求0值：

$\begin{aligned}n_0 = \frac{-24y_3+n_0^2(K-12F)-2n_0^3(H+J)-n_0^4K}{2(6B+6C-H-J)}\end{aligned}$

差值迭代：$M=K/24\quad  N=(H+J)/12\quad   P=F/2-M\quad      Q=(B+C)/2-N$

$\begin{aligned}\Delta n_0 = -\frac{ Mn_0^4+Nn_0^3+Pn_0^2+Qn_0+y3 }{4Mn_0^3+3Nn_0^2+2Pn_0+Q}   \end{aligned}$



#### 不等间距插值：拉格朗日插值公式

$(x_1,y_1),(x_2,y_2),\cdots(x_n,y_n)$，其中$x_i$均不相同
$$
y = \sum\limits_{i=1}^{n} y_i L_i\\
L_i = \prod\limits_{j=1,j\neq i}^n \frac{x-x_j}{x_i-x_j}
$$


可求得一个$n-1$次的函数表达式



# 线性拟合

$y = ax+b$

$$\begin{aligned}\left\{\begin{array}\quad
a=\frac{N\sum xy -\sum x\sum y}{N\sum x^2-(\sum x)^2} \\
b=\frac{\sum y\sum x^2 -\sum x\sum xy}{N\sum x^2-(\sum x)^2} \\
r=\frac{N\sum xy-\sum x\sum y}{\sqrt{N\sum x^2-(\sum x)^2} \sqrt{N\sum y^2-(\sum y)^2}}
\end{array}\right.\end{aligned}$$  其中 $-1\le r\le 1$

最小二乘法的推导过程：

令
$\begin{aligned}S=\begin{pmatrix}x_1&y_1&1\\x_2&y_2&1\\\vdots&\vdots&\vdots\\x_n&y_n&1\end{pmatrix}\end{aligned}$,
$\begin{aligned}P=\begin{pmatrix}a\\-1\\b\end{pmatrix}\end{aligned}$,
$\begin{aligned}SP=\begin{pmatrix}d_1\\d_2\\\vdots\\d_3\end{pmatrix}\end{aligned}$,
$\begin{aligned}\epsilon=\sum_{i=1}^nd_i^2=\sum_{i=1}^n(ax_i-y_i+b)^2\end{aligned}$, 求令$\epsilon$取最小值的$P$。

对$\epsilon(P)$求偏导数：
$\begin{aligned}\frac{\partial\epsilon}{\partial a}=2\sum_{i=1}^n(ax_i-y_i+b)x_i=2(a\sum x^2-\sum xy+b\sum x)=0\end{aligned}$,
$\begin{aligned}\frac{\partial\epsilon}{\partial b}=2\sum_{i=1}^n(ax_i-y_i+b)=2(a\sum x-\sum y+nb)=0\end{aligned}$

可得方程组：

$$\begin{aligned}\left\{\begin{array}\quad a\sum x^2-\sum xy+b\sum x&=&0\\ a\sum x-\sum y+nb&=&0\end{array}\right.\end{aligned}$$

解得：
$$\begin{aligned}\left\{\begin{array}\quad a=\frac{N\sum xy -\sum x\sum y}{N\sum x^2-(\sum x)^2}\\b=\frac{\sum y\sum x^2 -\sum x\sum xy}{N\sum x^2-(\sum x)^2} \end{array}\right.\end{aligned}$$

$$\begin{aligned}\left\{\begin{array}\quad a=\frac{M_{1,2}}{M_{2,2}}\\b=\frac{M_{3,2}}{M_{2,2}} \end{array}\right.\end{aligned}$$

线代解：

设方阵$\begin{aligned}A=S^TS=\begin{pmatrix}\sum x^2&\sum xy&\sum x\\\sum xy&\sum y^2&\sum y\\\sum x&\sum y&N\end{pmatrix}\end{aligned}$,
$\begin{aligned}AP=\begin{pmatrix}a\sum x^2-\sum xy+b\sum x\\a\sum xy-\sum y^2+b\sum y\\a\sum x-\sum y+Nb\end{pmatrix}\end{aligned}$,
$\begin{aligned}\epsilon=P^TS^TSP=P^TAP\end{aligned}$,

$\begin{aligned}\begin{array}\quad\epsilon&=&P^TS^TSP=a^2\sum x^2-a\sum xy+ab\sum x -a\sum xy +\sum y^2-b\sum y+ab\sum x-b\sum y+Nb^2\\
&=&a^2\sum x^2-2a\sum xy+2ab\sum x +\sum y^2-2b\sum y+Nb^2\\
&=&\end{array}\end{aligned}$,


#一般线性拟合（多重线性回归）

$y=af_0(x)+bf_1(x)+cf_2(x)$

令
$M=\sum f_0^2\quad      P=\sum f_0f_1\quad      Q=\sum f_0f_2\quad      R=\sum f_1^2\quad      S=\sum f_1f_2$

$T=\sum f_2^2\quad      U=\sum yf_0\quad      V=\sum yf_1\quad        W=\sum yf_2$

$\begin{aligned}D=\begin{vmatrix}M&P&Q\\P&R&S\\Q&S&T\end{vmatrix}=MRT+2PQS-MS^2-RQ^2-TP^2\end{aligned}$

得：
$$\begin{aligned}\left\{\begin{array}\quad
a=\frac{1}{D}\begin{vmatrix}U&V&W\\P&R&S\\Q&S&T\end{vmatrix}\\
b=\frac{1}{D}\begin{vmatrix}U&V&W\\Q&S&T\\M&P&Q\end{vmatrix}\\
c=\frac{1}{D}\begin{vmatrix}U&V&W\\M&P&Q\\P&R&S\end{vmatrix}
\end{array}\right.\end{aligned}$$

即
$$\begin{aligned}\left\{\begin{array}\quad
a=\frac{U(RT-S^2)+V(QS-PT)+W(PS-QR)}{D}\\
b=\frac{U(SQ-PT)+V(MT-Q^2)+W(PQ-MS)}{D}\\
c=\frac{U(PS-RQ)+V(PQ-MS)+W(MR-P^2)}{D}
\end{array}\right.\end{aligned}$$


# 二次拟合

$y=ax^2+bx+c$

令
$P =\sum x\quad    Q=\sum x^2\quad    R = \sum x^3\quad   S=\sum x^4$

$T=\sum y\quad     U=\sum xy\quad    V=\sum x^2y$

$\begin{aligned}D=\begin{vmatrix}N&P&Q\\P&Q&R\\Q&R&S\end{vmatrix}=NQS+2PQR-Q^3-P^2S-NR^2\end{aligned}$


得：
$$\begin{aligned}\left\{\begin{array}\quad
a=\frac{1}{D}\begin{vmatrix}T&U&V\\N&P&Q\\P&Q&R\end{vmatrix}\\
b=\frac{1}{D}\begin{vmatrix}T&U&V\\Q&R&S\\N&P&Q\end{vmatrix}\\
c=\frac{1}{D}\begin{vmatrix}T&U&V\\P&Q&R\\Q&R&S\end{vmatrix}
\end{array}\right.\end{aligned}$$

即
$$\begin{aligned}\left\{\begin{array}\quad
a=\frac{NQV+PRT+PQU-Q^2T-P^2V-NRU}{D}\\
b=\frac{NSU+PQV+QRT-Q^2U-PST-NRV}{D}\\
c=\frac{QST+QRU+PRV-Q^2V-PSU-R^2T}{D}
\end{array}\right.\end{aligned}$$


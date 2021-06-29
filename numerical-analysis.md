

# 三点插值：

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

$a = y_2-y_1, b = y_3-y_2$

$c = b -a = y_1+y_3-2y_2$



#### 当知知$x'$（与$x_2$相邻）求$y'$：

$y' = y_2+(n/2)(a+b+cn)$    （$n=(x’-x)/(x2-x1)$，$|n|<0.5$）



#### 求三点区间内的极值：

$$
y_m = y_2 - \frac{(a+b)^2}{8c} \\
n_m = -\frac{a+b}{2c}
$$







#### 插值求逆：$y=0$，求$x$对应的$n_0$：

$\begin{aligned}n_0 = -\frac{2y^2}{a+b+c*n_0}\end{aligned} $    以0为初值迭代至稳定

$\begin{aligned}\Delta n_0 = -\frac{ 2y_2+n_0(a+b+cn_0) }{a+b+2cn_0}\end{aligned}$    差值迭代



# 中点插值：

$$
\begin{matrix}
x_1&y_1\\
x_2&y_2\\
x_3&y_3\\
x_4&y_4
\end{matrix}
$$



求$x=\frac{1}{2}(x_2+x_3)$对应的y值：$y=\frac{1}{16}[9(y_2+y_3)-y_1-y_4] $



# 五点插值：

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



#### 当知知x'（与x3相邻）求y'：

$ y' = y_3+n/2[(B+C)-(H+J)]+n^2/2(F-K/12)+n^3(H+J)/12+n^4*K/24 $ （$n=(x’-x)/(x_3-x_2)$，$|n| <0.5$）



求极值：$nm = [6B=6C-H-J+3nm^2(H+J)+2n_m^3K]/(K-12F)$

求0值：

$n0 = [-24y_3+n0^2(K-12F)-2n0^3(H+J)-n0^4K]/2/(6B+6C-H-J)$

差值迭代：$M=K/24\quad  N=(H+J)/12\quad   P=F/2-M\quad      Q=(B+C)/2-N$

$\Delta n_0 = -[ Mn0^4+Nn0^3+Pn0^2+Qn0+y3 ]/(4Mn0^3+3Nn0^2+2Pn0+Q)   $



#### 不等间距插值：拉格朗日插值公式

$(x_1,y_1),(x_2,y_2),\cdots(x_n,y_n)$，其中$x_i$均不相同
$$
y = \sum\limits_{i=1}^{n} y_i L_i\\
L_i = \prod\limits_{j=1,j\neq i}^n \frac{x-x_j}{x_i-x_j}
$$


可求得一个n-1次的函数表达式



# 线性拟合

y = ax+b

$a=(N\sum xy -\sum x\sum y)/[N\sum x^2-(\sum x)^2]$

$b=(\sum y\sum x^2 -\sum x\sum xy)/[N\sum x^2-(\sum x)^2]$

$r=(N\sum xy-\sum x\sum y)/[\sqrt{N\sum x^2-(\sum x)^2} \sqrt{N\sum y^2-(\sum y)^2}]$   -1<=r<=1



#一般线性拟合（多重线性回归）

$y=af_0(x)+bf_1(x)+cf_2(x)$

$M=\sum f_0^2\quad      P=\sum f_0f_1\quad      Q=\sum f_0f_2\quad      R=\sum f_1^2\quad      S=\sum f_1f_2$

$T=\sum f_2^2\quad      U=\sum yf_0\quad      V=\sum yf_1\quad        W=\sum yf_2$

$D=MRT+2PQS-MS^2-RQ^2-TP^2$

$a=[U(RT-S^2)+V(QS-PT)+W(PS-QR)]/D$

$b=[U(SQ-PT)+V(MT-Q^2)+W(PQ-MS)]/D$

$c=[U(PS-RQ)+V(PQ-MS)+W(MR-P^2)]/D$



# 二次拟合

$y=ax^2+bx+c$

$P =\sum x\quad    Q=\sum x^2\quad    R = \sum x^3\quad   S=\sum x^4$

$T=\sum y\quad     U=\sum xy\quad    V=\sum x^2y$

$D=NQS+2PQR-Q^3-P^2S-NR^2$

$a=(NQV+PRT+PQU-Q^2T-P^2V-NRU)/D$

$b=(NSU+PQV+QRT-Q^2U-PST-NRV)/D$

$c=(QST+QRU+PRV-Q^2V-PSU-R^2T)/D$


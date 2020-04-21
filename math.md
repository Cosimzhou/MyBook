Math Manual
===========



# SET【集合】

$\mathbb{C}$:  Complex number

$\mathbb{R}$ :  Real number          $\mathbb{R}=\mathbb{R}^+\cup\mathbb{R}^-\cup\{0\}$

$\mathbb{I}$:   Image number

$\mathbb{T}$:  Transcendental number

$\mathbb{A}$:  Algebraic number. Or $\bar{\mathbb{Q}}$

$\mathbb{Q}$:  Rational number

$\mathbb{Z}$:  Integers					$\mathbb{Z}^+$: Positive integers

$\mathbb{N}$:  Natural number      $\mathbb{N}=\mathbb{Z}^+\cup\{0\}$

$\mathbb{P}$:  Prime number         $\mathbb{P}=\{2,3,5,7,11,13,17,\cdots\}$

$\mathbb{P}\subsetneqq\mathbb{N}\subsetneqq\mathbb{Z}\subsetneqq\mathbb{Q}\subsetneqq\mathbb{A}\subsetneqq\mathbb{R}\subsetneqq\mathbb{C}\supsetneqq\mathbb{I}$

$\mathbb{I}\subsetneqq\mathbb{C}$



$\begin{aligned}\frac{a+b}{a}=\frac{a}{b}\xlongequal{\rm{def}}\varphi=\frac{1+\sqrt{5}}{2}=1.6180339887...\end{aligned}$

$\begin{aligned}e=\sum^{\infin}_{n=0}\frac{1}{n!}=\lim_{n\to\infin}\left(1+\frac{1}{n}\right)^n=2.7182818284590452...\end{aligned}$



$\begin{aligned}\pi=\int^1_{-1}\frac{1}{\sqrt{1-x^2}}\mathrm{d}x\end{aligned}$

# Arithmetic【算术】

$a+b=b+a$

$\begin{align}a\times b=\underbrace{a+a+\cdots+a}_{b}=\sum_{i=1}^{n}a\end{align}$

$\begin{align}a^n=\underbrace{a\times a\times\cdots\times a}_{n}=\prod_{i=1}^{n}a\end{align}$

$\begin{align}n!=\prod_{i=1}^{n}i\end{align}=\underbrace{1\times 2\times\cdots\times n}_{n}$

$\begin{align}{\rm C}_n^{m}=\frac{n!}{m!(n-m)!}\end{align}$

$\begin{align}{\rm A}_n^{m}=\frac{n!}{(n-m)!}=\prod_{i=n-m+1}^ni\end{align}$

$\begin{align}\log_ba=\frac{\ln a}{\ln b}\end{align}$



$\begin{aligned}(a+b)^n=\sum_{i=0}^{n}{\rm C}_n^{i}a^{n-i}b^{i}\end{aligned}$

$(a+b)(a-b)=a^2-b^2$

$a^3\pm b^3=(a\pm b)(a^2\mp ab+b^2)$



##### Hyperoperation

$a[n]b=\underbrace{a[n-1](a[n-1](a[n-1](\cdots a[n-1]a)))}_{b\quad coyies \quad of\quad a},n\ge 2$

$a[n]b=a[n-1](a[n](b-1)),n\ge 1$





# Combinatorial 【组合】



* Factorial【阶乘】

$\begin{aligned}f(0)=1,f(n)=nf(n-1)=\prod_{i=1}^ni=n!\quad n>0\end{aligned}$

* Arrangement【排列数】

$\begin{align}{\rm{A}}_n^{m}=\frac{n!}{(n-m)!}=\prod_{i=n-m+1}^ni\end{align}$

* Combination【组合数】

$\begin{align}{\rm{C}}_n^{m}=\frac{n!}{m!(n-m)!}\end{align}$

* Catalan Number【Catalan数】

$\begin{aligned}f(0)=1,f(1)=1,f(n)=\sum\limits_{i=0}^{n-1}f(n-1-i)f(i)=\frac{(2n)!}{(n+1)!n!}=\frac{{\rm{C}}_{2n}^n}{n+1}\end{aligned}$





# Number Theory【数论】

$a\times b\equiv(a\bmod n)\times(b\bmod n)(\bmod n)$





#### Fermat's Little Theorem【费马小定理】

If $p\in \mathbb{P}$, $a\in\mathbb{Z}^+$, and $\begin{aligned}\frac{a}{p}\notin\mathbb{Z}\end{aligned}$, then $a^{p-1}\equiv 1(\bmod p)$.



#### Fermat' Last Theorem【费马大定理】

Equation $x^n+y^n=z^n$  has no positive integer solution about $x,y,z$ , when $n>2\wedge n\in\mathbb{Z}^+$.



#### Chinese Remainder Theorem【中国剩余定理】

$\left\{\begin{array}{ccc}x&\equiv&a_1(\bmod m_1)\\x&\equiv&a_2(\bmod m_2)\\&\vdots&\\x&\equiv&a_n(\bmod m_n)\end{array}\right.$

$\begin{aligned}M=\prod_{i=1}^nm_i, \quad M_i=\frac{M}{m_i},\quad t_iM_i\equiv 1(\bmod m_i)\end{aligned}$

$\begin{aligned}x=kM+\sum_{i=1}^na_it_iM_i\end{aligned},\quad k\in\mathbb{Z}$



# Sequence【数列】

#### Artihmetic series【等差数列】

$a_n=a_0+nd$

$\begin{aligned}\sum_{i=0}^n a_i=na_0+\frac{n(n+1)d}{2}\end{aligned}$



#### Geometric series【等比数列】

$a_n=a_0q^n$

$\begin{aligned}\sum_{i=0}^na_i=\frac{a_0(1-q^n)}{1-q}\end{aligned}$



#### Natural series【自然数列】

$\begin{aligned}\sum_{i=1}^ni=\frac{1}{2}n(n+1)\end{aligned}$                                     $\begin{aligned}\sum^n_{i=1}(2i-1)=n^2\end{aligned}$

$\begin{aligned}\sum_{i=1}^ni^2=\frac{1}{6}n(n+1)(2n+1)\end{aligned}$

$\begin{aligned}\sum_{i=1}^ni^3=\left(\sum_{i=1}^ni\right)^2=\frac{1}{4}\left[n(n+1)\right]^2\end{aligned}$

$\begin{aligned}\sum\limits_{i=0}^ni^4=\frac{1}{30}n(n+1)(2n+1)(3n^2+3n-1)\end{aligned}$

$\begin{aligned}\sum\limits_{i=1}^ni^{k+1}=(n+1)\sum\limits_{i=1}^ni^k-\sum_{i=1}^n\left(\sum\limits_{p=1}^ip^k\right)\end{aligned}$



$\begin{aligned}\lim_{n\to+\infin}\sum_{i=1}^{n}i=-\frac{1}{12}\end{aligned}$



##### Ramanujan Equation

$\sqrt{1+2\sqrt{1+3\sqrt{1+4\sqrt{1+5\sqrt{\cdots \infin}}}}}=3$

$\sqrt{1+(n-1)\sqrt{1+n\sqrt{1+(n+1)\sqrt{1+(n+2)\sqrt{\cdots \infin}}}}}=n$



$\begin{aligned}\prod^n_{i=1}i=n!=\int_0^{+\infin}t^{n}e^{-t}\mathrm{d}t=\Gamma(n+1)\end{aligned}$





#### Fibonacci sequence【斐波纳契数列】

$a_1=1,a_2=1,a_n=a_{n-1}+a_{n-2}\quad n>2$

$\begin{aligned}a_n=\frac{1}{\sqrt{5}}\left[\left(\frac{1+\sqrt{5} }{2}\right)^n-\left(\frac{1-\sqrt{5}}{2}\right)^n\right]=\frac{1}{\sqrt{5}}\left[\varphi^n(1-\varphi)^n\right]\end{aligned}$



#### Lucas sequence【卢卡斯数列】

$a_1=1,a_2=3,a_n=a_{n-1}+a_{n-2}\quad n>2$

$\begin{aligned}a_n=\left(\frac{1+\sqrt{5} }{2}\right)^n+\left(\frac{1-\sqrt{5}}{2}\right)^n\end{aligned}$



Bernoulli number

$\begin{aligned}B_n=\sum^n_{i=0}{\rm C}^i_nB_i\end{aligned}$





Fourier



#### Quadratic Equations【一元二次方程】

$\begin{aligned}ax^2+bx+c=0\end{aligned}$

$\left\{\begin{array}{l}\begin{aligned}x_1=\frac{-b+\sqrt{b^2-4ac}}{2a}\end{aligned}\\\begin{aligned}x_2=\frac{-b-\sqrt{b^2-4ac}}{2a}\end{aligned}\end{array}\right.$



#### Cubic Equations【一元三次方程】

$ax^3+bx^2+cx+d=0$

$\begin{aligned}\left\{\begin{array}{l}u=\frac{9abc-27a^2d-2b^3}{54a^3} \\ v=\frac{\sqrt{3(4ac^3-b^2c^2-18abcd+27a^2d^2+4b^3d)}}{18a^2}\\\omega=-\frac{1}{2}+\frac{\sqrt{3}}{2}i\end{array}\right.\end{aligned}$

$m=\left\{\begin{array}{l}\sqrt[3]{u+v},\quad|u+v|\ge|u-v|\\\sqrt[3]{u-v},\quad|u+v|<|u-v| \end{array}\right.$

$\begin{aligned}n=\left\{\begin{array}{ll}\frac{b^2-3aac}{9am},& |m|\neq 0\\0,& |m|=0\end{array}\right.\end{aligned}$

$\begin{aligned}\left\{\begin{array}{l}x_1=m+n-\frac{b}{3a} \\ x_2=\omega m+\omega^2n-\frac{b}{3a}\\x_3=\omega^3m+\omega n-\frac{b}{3a}\end{array}\right.\end{aligned}$



##### Special Cardano's Formula

$x^3+px+q=0$

$\begin{aligned}\Delta=\left(\frac{q}{2}\right)^2+\left(\frac{p}{3}\right)^3\end{aligned}$

$\begin{aligned}\omega=\frac{-1+\sqrt{3}i}{2}=e^{\frac{2\pi}{3}i}\end{aligned}$

$\begin{aligned}\left\{\begin{array}{l}x_1=\sqrt[3]{-\frac{q}{2}+\sqrt{\Delta}} +\sqrt[3]{-\frac{q}{2}-\sqrt{\Delta}}\\ x_2=\omega\sqrt[3]{-\frac{q}{2}+\sqrt{\Delta}}+\omega^2\sqrt[3]{-\frac{q}{2}-\sqrt{\Delta}}\\x_3=\omega^2\sqrt[3]{-\frac{q}{2}+\sqrt{\Delta}}+\omega\sqrt[3]{-\frac{q}{2}-\sqrt{\Delta}}\end{array}\right.\end{aligned}$

Which satisfies $x_1+x_2+x_3=0$, $\begin{aligned}\frac{1}{x_1}+\frac{1}{x_2}+\frac{1}{x_3}=-\frac{p}{q}\end{aligned}$ and $x_1x_2x_3=-q$



#### Quartic Equation【一元四次方程】

$ax^4+bx^3+cx^2+dx+e=0$

$\begin{aligned} \left\{\begin{array}{l}{\Delta_{1}=c^{2}-3 b d+12 a e} \\ {\Delta_{2}=2 c^{3}-9 b c d+27 a d^{2}+27 b^{2} e-72 a c e}\end{array}\right.\end{aligned}$

$\begin{aligned}\Delta=\frac{\sqrt[3]{2} \Delta_{1}}{3 a \sqrt[3]{\Delta_{2}+\sqrt{-4 \Delta_{1}^{3}+\Delta_{2}^{2}}}}+\frac{\sqrt[3]{\Delta_{2}+\sqrt{-4 \Delta_{1}^{3}+\Delta_{2}^{2}}}}{3 \sqrt[3]{2} a}\end{aligned}$

$\begin{aligned}\Omega=\sqrt{\frac{b^{2}}{4 a^{2}}-\frac{2 c}{3 a}+\Delta}\end{aligned}$

$\left\{\begin{array}{l}\begin{aligned}x_1=-\frac{b}{4 a}+\frac{1}{2}\Omega+\frac{1}{2} \sqrt{\frac{b^{2}}{2 a^{2}}-\frac{4 c}{3 a}-\Delta+\frac{4abc-b^{3}-8a^2 d}{4a^3\Omega}}\end{aligned}\\ \begin{aligned}x_2=-\frac{b}{4 a}+\frac{1}{2}\Omega-\frac{1}{2} \sqrt{\frac{b^{2}}{2 a^{2}}-\frac{4 c}{3 a}-\Delta+\frac{4abc-b^{3}-8a^2 d}{4a^3\Omega}}\end{aligned}\\ \begin{aligned}x_3=-\frac{b}{4 a}-\frac{1}{2}\Omega+\frac{1}{2} \sqrt{\frac{b^{2}}{2 a^{2}}-\frac{4 c}{3 a}-\Delta-\frac{4abc-b^{3}-8a^2 d}{4a^3\Omega}}\end{aligned}\\ \begin{aligned}x_4=-\frac{b}{4 a}-\frac{1}{2}\Omega-\frac{1}{2} \sqrt{\frac{b^{2}}{2 a^{2}}-\frac{4 c}{3 a}-\Delta-\frac{4abc-b^{3}-8a^2 d}{4a^3\Omega}}\end{aligned}\end{array}\right.$





# Triangular【三角函数】



![](tfdef.png)

$\begin{align}\sin\theta=\frac{b}{c},\quad\csc\theta=\frac{c}{b}\end{align}$

$\begin{align}\cos\theta=\frac{a}{c},\quad\sec\theta=\frac{c}{a}\end{align}$

$\begin{align}\tan\theta=\frac{b}{a},\quad\cot\theta=\frac{a}{b}\end{align}$



#### Pythagoras Theorem 【勾股定理】

$a^2+b^2=c^2$

$\left\{\begin{array}{l}a=m^2-n^2\\b=2mn&,m>n>0\\c=m^2+n^2\end{array}\right.$



#### Cosine Theorem【余弦定理】

For any triangle in the Euclidean plane with sides $a,b,c$ and opposite angles $A,B,C$, respectively.

$c^2=a^2+b^2-2ab\cos C$



#### Sine Theorem【正弦定理】

For any triangle in the Euclidean plane with sides $a,b,c$ and opposite angles $A,B,C$, respectively, the equalities

$\begin{aligned}\frac{a}{\sin A}=\frac{b}{\sin B}=\frac{c}{\sin C}=2R\end{aligned}$

hold, where $R$ is the radius of the circumscribed circle.




#### Double angle formula【倍角公式】

$\sin^2\theta+\cos^2\theta=1$

$\begin{aligned}\sin\alpha+\cos\alpha=\sqrt{2}\sin(\alpha+\frac{\pi}{2})\end{aligned}$

$\sin2\alpha=2\sin\alpha\cos\alpha$

$\cos2\alpha=\cos^2\alpha-\sin^2\alpha=1-2\sin^2\alpha=2\cos^2\alpha-1$

$\begin{aligned}\tan2\alpha=\frac{2\tan\alpha}{\tan^2\alpha-1}\end{aligned}$



##### Half angles

$\begin{aligned}\sin\frac{\alpha}{2}=\pm\sqrt{\frac{1-\cos\alpha}{2}}\end{aligned}$

$\begin{aligned}\cos\frac{\alpha}{2}=\pm\sqrt{\frac{1+\cos\alpha}{2}}\end{aligned}$

$\begin{aligned}\tan\frac{\alpha}{2}=\pm\sqrt{\frac{1-\cos\alpha}{1+\cos\alpha}}=\frac{\sin\alpha}{1+\cos\alpha}=\frac{1-\cos\alpha}{\sin\alpha}\end{aligned}$

$\begin{aligned}\cot\frac{\alpha}{2}=\frac{1+\cos\alpha}{\sin\alpha}=\frac{\sin\alpha}{1-\cos\alpha}\end{aligned}$



##### Three times

$\begin{aligned}\sin3\alpha=3\sin\alpha-4\sin^3\alpha=4\sin\alpha\sin\left(\frac{\pi}{3}+\alpha\right)\sin\left(\frac{\pi}{3}-\alpha\right)\end{aligned}$

$\begin{aligned}\cos3\alpha=4\cos^3\alpha-3\cos\alpha=4\cos\alpha\cos\left(\frac{\pi}{3}+\alpha\right)\cos\left(\frac{\pi}{3}-\alpha\right)\end{aligned}$

$\begin{aligned}\tan3\alpha=\frac{\tan^3\alpha-3\tan\alpha}{3\tan^2\alpha-1}=\tan\alpha\tan\left(\frac{\pi}{3}+\alpha\right)\tan\left(\frac{\pi}{3}-\alpha\right)\end{aligned}$

$\begin{aligned}\cot3\alpha=\frac{\cot^3\alpha-3\cot\alpha}{3\cot^2\alpha-1}\end{aligned}$

$\begin{aligned}\sec3\alpha=\frac{\sec^3\alpha}{4-3\sec^2\alpha}\end{aligned}$

$\begin{aligned}\csc3\alpha=\frac{\csc^3\alpha}{3\csc^2\alpha-4}\end{aligned}$




##### Four times

$\begin{aligned}\sin4\alpha=-4\cos\alpha\sin\alpha\left(2\sin^2\alpha-1\right)\end{aligned}$

$\begin{aligned}\cos4\alpha=1-8\cos^4\alpha+8\cos^4\alpha\end{aligned}$

$\begin{aligned}\tan4\alpha=\frac{4\tan\alpha-4\tan^3\alpha}{1-6\tan^2\alpha+\tan^4\alpha}\end{aligned}$



##### Five times

$\begin{aligned}\sin5\alpha=16\sin^5\alpha-20\sin^3\alpha+5\sin\alpha\end{aligned}$

$\begin{aligned}\cos5\alpha=16\cos^5\alpha-20\cos^3\alpha+5\cos\alpha\end{aligned}$

$\begin{aligned}\tan5\alpha=\tan\alpha\frac{5-10\tan^2\alpha+\tan^4\alpha}{1-10\tan^2\alpha+5\tan^4\alpha}\end{aligned}$




##### Six times

$\begin{aligned}\sin6\alpha=2\cos\alpha\sin\alpha(2\sin\alpha+1)(2\sin\alpha-1)(4\sin^2\alpha-3)\end{aligned}$

$\begin{aligned}\cos6\alpha=(2\cos^2\alpha-1)(16\cos^4\alpha-16\cos\alpha+1)\end{aligned}$

$\begin{aligned}\tan6\alpha=\frac{-6\tan\alpha+20\tan^3\alpha-6\tan^5\alpha}{\tan^6\alpha-15\tan^4\alpha+15\tan^2\alpha-1}\end{aligned}$



##### Seven times

$\begin{aligned}\sin7\alpha=-\sin\alpha\left(56\sin^2\alpha-112\sin^4\alpha-64\sin^6\alpha-7\right)\end{aligned}$

$\begin{aligned}\cos7\alpha=\cos\alpha\left(56\cos^2\alpha-112\cos^4\alpha-64\cos^6\alpha-7\right)\end{aligned}$

$\begin{aligned}\tan7\alpha=\tan\alpha\frac{\tan^6\alpha-21\tan^4\alpha+35\tan^2\alpha-7}{7\tan^6\alpha-35\tan^4\alpha+21\tan^2\alpha-1}\end{aligned}$



##### De Moivre's formula 【棣莫弗定理】

$(\cos\theta+i\sin\theta)^n=\cos n\theta+i\sin n\theta$






$(\sin\alpha+\sin\beta)(\sin\alpha-\sin\beta)=\sin(\alpha+\beta)\sin(\alpha-\beta)$

$\begin{aligned}\cos^n\theta=\frac{1}{2^n}\sum^n_{k=0}{\rm C}^k_n\cos(2k-n)\theta\end{aligned}$

$\begin{aligned}\sin^n\theta=\frac{1}{2^n}\sum^n_{k=0}(-1)^k{\rm{C}}^k_n\cos\left((2k-n)\theta+\frac{n\pi}{2}\right)\end{aligned}$




#### Prosthaphaeresis【积化和差】

$\begin{aligned}\sin\alpha\cos\beta=\frac{1}{2}[\sin(\alpha+\beta)+\sin(\alpha-\beta)]\end{aligned}$

$\begin{aligned}\sin\alpha\sin\beta=\frac{1}{2}[\cos(\alpha-\beta)-\cos(\alpha+\beta)]\end{aligned}$

$\begin{aligned}\cos\alpha\cos\beta=\frac{1}{2}[\cos(\alpha+\beta)+\cos(\alpha-\beta)]\end{aligned}$



#### Sum-to-product Identities Fomulas【和差化积】

$\begin{aligned}\sin\alpha+\sin\beta=2\sin\frac{\alpha+\beta}{2}\cos\frac{\alpha-\beta}{2}\end{aligned}$

$\begin{aligned}\cos\alpha+\cos\beta=2\cos\frac{\alpha+\beta}{2}\cos\frac{\alpha-\beta}{2}\end{aligned}$

$\begin{aligned}\cos\alpha-\cos\beta=2\sin\frac{\alpha+\beta}{2}\sin\frac{\alpha-\beta}{2}\end{aligned}$





| $\theta$ | $\sin\theta$ | $\cos\theta$ | $\tan\theta$ | $\cot\theta$ | $\sec\theta$ | $\csc\theta$ |
| -------- | ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
| $15^{\circ}\quad\frac{\pi}{12}$ | $\frac{\sqrt{6}-\sqrt{2}}{4}$ | $\frac{\sqrt{6} +\sqrt{2}}{4}$ | $2-\sqrt{3}$ | $2+\sqrt{3}$ | $\sqrt{6}-\sqrt{2}$ | $\sqrt{6}+\sqrt{2}$ |
| $18^{\circ}\quad\frac{\pi}{10}$ | $\frac{\sqrt{5}-1}{4}$ | $\frac{\sqrt{10+2\sqrt{5}}}{4}$ | $\frac{\sqrt{25-10\sqrt{5}}}{5}$ | $\sqrt{5+2\sqrt{5}}$ | $\frac{\sqrt{50-10\sqrt{5}}}{5}$ | $\sqrt{5}+1$ |
| $22.5^{\circ}\quad\frac{\pi}{8}$ | $\frac{\sqrt{2-\sqrt{2}}}{2}$ | $\frac{\sqrt{2+\sqrt{2}}}{2}$ | $\sqrt{2}-1$ | $\sqrt{2}+1$ | $\sqrt{4-2\sqrt{2}}$ | $\sqrt{4+2\sqrt{2}}$ |
| $30^{\circ}\quad\frac{\pi}{6}$ | $\frac{1}{2}$ | $\frac{\sqrt{3}}{2}$ | $\frac{\sqrt{3}}{3}$ | $\sqrt{3}$ | $\frac{2\sqrt{3}}{3}$ | $2$ |
| $36^{\circ}\quad\frac{\pi}{5}$ | $\frac{\sqrt{10-2\sqrt{5}}}{4}$ | $\frac{\sqrt{5}+1}{4}$ | $\sqrt{5-2\sqrt{5}}$ | $\frac{\sqrt{50+10\sqrt{5}}}{5}$ | $\sqrt{5}-1$ | $\frac{\sqrt{25+10\sqrt{5}}}{5}$ |
| $45^{\circ}\quad\frac{\pi}{4}$ | $\frac{\sqrt{2}}{2}$ | $\frac{\sqrt{2}}{2}$ | $1$ | $1$ | $\sqrt{2}$ | $\sqrt{2}$ |
| $54^{\circ}\quad\frac{3\pi}{10}$ | $\frac{\sqrt{5}+1}{4}$ | $\frac{\sqrt{10-2\sqrt{5}}}{4}$ | $\frac{\sqrt{25+10\sqrt{5}}}{5}$ | $\sqrt{5-2\sqrt{5}}$ | $\frac{50+10\sqrt{5}}{5}$ | $\sqrt{5}-1$ |
| $60^{\circ}\quad\frac{\pi}{3}$ | $\frac{\sqrt{3}}{2}$ | $\frac{1}{2}$ | $\sqrt{3}$ | $\frac{\sqrt{3}}{3}$ | $2$ | $\frac{2\sqrt{3}}{3}$ |
| $67.5^{\circ}\quad\frac{3\pi}{8}$ | $\frac{\sqrt{2+\sqrt{2}}}{2}$ | $\frac{\sqrt{2-\sqrt{2}}}{2}$ | $\sqrt{2}+1$ | $\sqrt{2}-1$ | $\sqrt{4+2\sqrt{2}}$ | $\sqrt{4-2\sqrt{2}}$ |
| $72^{\circ}\quad\frac{2\pi}{5}$ | $\frac{\sqrt{10+2\sqrt{5}}}{4}$ | $\frac{\sqrt{5}-1}{4}$ | $\sqrt{5+2\sqrt{5}}$ | $\frac{\sqrt{25-10\sqrt{5}}}{5}$ | $\sqrt{5}+1$ | $\frac{\sqrt{50-10\sqrt{5}}}{5}$ |
| $75^{\circ}\quad\frac{5\pi}{12}$ | $\frac{\sqrt{6}+\sqrt{2}}{4}$ | $\frac{\sqrt{6}-\sqrt{2}}{4}$ | $2+\sqrt{3}$ | $2-\sqrt{3}$ | $\sqrt{6}+\sqrt{2}$ | $\sqrt{6}-\sqrt{2}$ |
| $90^{\circ}\quad\frac{\pi}{2}$ | $1$ | $0$ | $\to\infin$ | $0$ | $\to\infin$ | $1$ |
| $180^{\circ}\quad\pi$ | $0$ | $-1$ | $0$ | $\to\infin$ | $-1$ | $\to\infin$ |
| $270^{\circ}\quad\frac{3\pi}{2}$ | $-1$ | $0$ | $\to\infin$ | $0$ | $\to\infin$ | $-1$ |
| $360^{\circ}\quad 2\pi$ | $0$ | $1$ | $0$ | $\to\infin$ | $1$ | $\to\infin$ |





    α=15°(π/12) sinα=(√6-√2)/4 cosα=(√6+√2)/4 tαnα=2-√3 cotα=2+√3 secα=√6-√2 cscα=√6+√2
    α=18°(π/10) sinα=(√5-1)/4 cosα=√(10+2√5)/4 tαnα=√(25-10√5)/5 cscα=√5+1 secα=√(50-10√5)/5 cotα=√(5+2√5)
    α=22.5°(π/8) sinα=√(2-√2)/2 cosα=√(2+√2)/2 tαnα=√2-1 cotα=√2+1 secα=√(4-2√2) cscα=√(4+2√2)
    α=30°(π/6) sinα=1/2 cosα=√3/2 tαnα=√3/3 cotα=√3 secα=2√3/3 cscα=2
    α=36°(π/5) sinα=√(10-2√5)/4 cosα=(√5+1)/4 tαnα=√(5-2√5) cscα=√(50+10√5)/5 secα=√5-1 cotα=√(25+10√5)/5
    α=45°(π/4) sinα=√2/2 cosα=√2/2 tαnα=1 cotα=1 secα=√2 cscα=√2
    α=54°(3π/10) sinα=(√5+1)/4 cosα=√(10-2√5)/4 tαnα=√(25+10√5)/5 cscα=√5-1 secα=√(50+10√5)/5 cotα=√(5-2√5)
    α=60°(π/3) sinα=√3/2 cosα=1/2 tαnα=√3 cotα=√3/3 secα=2 cscα=2√3/3
    α=67.5°(3π/8) sinα=√(2+√2)/2 cosα=√(2-√2)/2 tαnα=√2+1 cotα=√2-1 secα=√(4+2√2) cscα=√(4-2√2)
    α=72°(2π/5) sinα=√(10+2√5)/4 cosα=(√5-1)/4 tαnα=√(5+2√5) cscα=√(50-10√5)/5 secα=√5+1 cotα=√(25-10√5)/5
    α=75°(5π/12) sinα=(√6+√2)/4 cosα=(√6-√2)/4 tαnα=2+√3 cotα=2-√3 secα=√6+√2 cscα=√6-√2
    α=90°(π/2) sinα=1 cosα=0 tαnα→∞ cotα=0 secα→∞ cscα=1
    α=180°(π) sinα=0 cosα=-1 tαnα=0 cotα→∞ secα=-1 cscα→∞
    α=270°(3π/2) sinα=-1 cosα=0 tαnα→∞ cotα=0 secα→∞ cscα=-1
    α=360°(2π) sinα=0 cosα=1 tαnα=0 cotα→∞ secα=1 cscα→∞





## hyperbolic function【双曲函数】

$\begin{align}\sinh x=\frac{e^{x}-e^{-x}}{2}=-i\sin ix\end{align}$

$\begin{align}\cosh x=\frac{e^{x}+e^{-x}}{2}=\cos ix\end{align}$

$\begin{align}\tanh x=\frac{e^x-e^{-x}}{e^x+e^{-x}}=-i \tan ix\end{align}$

$\begin{align}\coth x=\frac{e^x+e^{-x}}{e^x-e^{-x}}=i\cot ix\end{align}$

$\begin{align}sech x=\frac{2}{e^{x}+e^{-x}}=\sec ix\end{align}$

$\begin{align}csch x=\frac{2}{e^{x}-e^{-x}}=i\csc ix\end{align}$





# Euler Formula【欧拉公式】

- $e^{ix}=\cos x+i\sin x$
- $e^{i\pi}+1=0$
- $F-E+V=2$



differentiable 【可微】

derivable【可导】

convergence【收敛】

integrable【可积】



# Analytic Geometry

#### Ellipse【椭圆】

$\begin{aligned}\frac{x^2}{a^2}+\frac{y^2}{b^2}=1\quad a,b\neq0\end{aligned}$



#### Parabola【抛物线】

$\begin{aligned}y=ax^2+bx+c\quad a\neq 0\end{aligned}$



#### Hyperbola【双曲线】

$\begin{aligned}\frac{x^2}{a^2}-\frac{y^2}{b^2}=1\quad a,b\neq 0\end{aligned}$



#### Cycloid【摆线】

$\left\{\begin{array}{l}x=r(t-\sin t)\\y=r(1-\cos t)r\end{array}\right.$



### Cantenary【悬链线】

$\begin{aligned}y={\rm{acosh}}\left(\frac{x}{a}\right)=\ln\left|\frac{x\pm\sqrt{x^2-a^2}}{a}\right|\end{aligned}$





# Complex【复数】

$i^2=-1$           $\ln(-1)=i\pi$           $e^{i\pi}+1=0$

$\begin{align}\sin ix=i\sinh x=\frac{e^{x}-e^{-x}}{2}i\end{align}$

$\begin{align}\cos ix=\cosh x=\frac{e^{x}+e^{-x}}{2}\end{align}$

$\begin{align}\tan ix=i\tanh x=\frac{e^x-e^{-x}}{e^x+e^{-x}}i\end{align}$



# Derivable【导数】



$\begin{align}
(u \pm v)^{\prime}=u^{\prime} \pm v^{\prime}
\end{align}$

$(uv)'=u'v+ uv'$

$\begin{align}\left(\frac{u}{v}\right)'=\frac{u'v-uv'}{v^2}\end{align}$

$\begin{align}
\left(\frac{C}{u}\right)^{\prime}=-\frac{C u^{\prime}}{u^{2}}
\end{align}$

$\begin{aligned}f (g(x))'=f'(g(x))g'(x)\end{aligned}$





## Taylor Formula【泰勒公式】

$\begin{aligned}\begin{array}{cl}f(x)&=\sum\limits^n_{i=0}\frac{f^{(i)}(x_0)}{i!}(x-x_0)^i+R_n(x)\\&=f(x_0)+f^{\prime}(x_0)(x-x_0)+\frac{1}{2}f^{\prime\prime}(x_0)(x-x_0)^2+\cdots+\frac{f^{(n)}(x_0)}{n!}(x+x_0)^n+R_n(x) \end{array}\end{aligned}$



### $R_n(x)$【余子式】

* **Peano**  $R_n(x)=o\left[(x-x_0)^n\right]$
* **Schlomilch-Roche**   $\begin{aligned}R_n(x)=f^{(n+1)}[x_0+\theta(x-x_0)]\frac{(1-\theta)^{n+1-p}(x-x_0)^{n+1}}{n!p}\end{aligned}$, $\theta\in(0,1)，p\in \mathbb{R}^+$
* **Lagrange**   $\begin{aligned}R_n(x)=f^{(n+1)}[x_0+\theta(x-x_0)]\frac{(x-x_0)^{n+1}}{(n+1)!}\end{aligned}$
* **Cauchy**   $\begin{aligned}R_n(x)=f^{(n+1)}[x_0+\theta(x-x_0)]\frac{(1-\theta)^{n}(x-x_0)^{n+1}}{n!}\end{aligned}$
* $\begin{aligned}R_n(x)=\frac{(-1)^n}{n!}\int^x_a(t-x)^n f^{(n+1)}(t)\mathrm{d} t\end{aligned}$





$\begin{aligned}e^x=1+\frac{1}{1!}x+\frac{1}{2!}x^2+\frac{1}{3!}x^3+o(x^3)\end{aligned}$

$\begin{aligned}\ln(1+x)=x-\frac{1}{2}x^2+\frac{1}{3}x^3+o(x^3)\end{aligned}$

$\begin{aligned}\sin x=x-\frac{1}{3!}x^3+\frac{1}{5!}x^5+o(x^5)\end{aligned}$

$\begin{aligned}\cos x=1-\frac{1}{2!}x^2+\frac{1}{4!}x^4+o(x^4)\end{aligned}$

$\begin{aligned}\arcsin x=x+\frac{1}{2}\times \frac{x^3}{3}+\frac{1\times 3}{2\times 4}\times\frac{x^4}{5}+\frac{1\times 3\times 5}{2\times 4\times 6}\times\frac{x^7}{7}+o(x^7)\end{aligned}$

$\begin{aligned}\frac{1}{1-x}=1+x+x^2+x^3+o(x^3)\end{aligned}$

$\begin{aligned}(1+x)^a=1+\frac{a}{1!}x+\frac{a(a-1)}{2!}x^2+\frac{a(a-1)(a-2)}{3!}x^3+o(x^3)\end{aligned}$





# Indefinite Integral【不定积分】

$\begin{align}\int x^{k}\mathrm{d}x=\frac{1}{k+1}x^{k+1}+C,\quad k\neq-1\end{align}$

$\begin{align}\int\frac{1}{x}\mathrm{d}x=\ln|x|+C\end{align}$

$\begin{align}\int a^x\mathrm{d}x=\frac{a^x}{\ln a}+C\end{align}$

$\begin{align}\int \cos x\mathrm{d}x=\sin x+C,\quad\int \sin x\mathrm{d}x=-\cos x+C\end{align}$

$\begin{align}\int\tan x\mathrm{d}x=-\ln|\cos x|+C,\quad\int\cot x\mathrm{d}x=\ln|\sin x|+C\end{align}$

$\begin{align}\int\sec{x}\tan{x}\mathrm{d}x=\sec{x}+C,\quad\int\csc{x}\cot{x}\mathrm{d}x=-\csc{x}+C\end{align}$

$\begin{align}\int\sec{x}\mathrm{d}x=\ln{|\sec{x}+\tan{x}|}+C,\quad\int\csc{x}\mathrm{d}x=\ln{|\csc{x}-\cot{x}|}+C\end{align}$

$\begin{align}\int\sec^2{x}\mathrm{d}x=\tan{x}+C,\quad\int\csc^2{x}\mathrm{d}x=-\cot{x}+C\end{align}$

$\begin{align}\int \cosh x\mathrm{d}x=\sinh x+C,\quad\int \sinh x\mathrm{d}x=\cosh x+C\end{align}$

$\begin{align}\int\tanh x\mathrm{d}x=\ln|\cosh x|+C,\quad\int\coth x\mathrm{d}x=\ln|\sinh x|+C\end{align}$

$\begin{align}\int\sec{x}\mathrm{d}x=\arctan(\sinh x)+C,\quad\int\csc{x}\mathrm{d}x=\ln|\tanh\frac{x}{2}|+C\end{align}$

$\begin{align}\int\frac{1}{a^2+x^2}\mathrm{d}x=\frac{1}{a}\arctan\frac{x}{a}+C\end{align}$

$\begin{align}\int\frac{1}{\sqrt{a^2-x^2}}\mathrm{d}x=\arcsin\frac{x}{a}+C\end{align}$

$\begin{align}\int\frac{1}{a^2-x^2}\mathrm{d}x=\frac{1}{2a}\ln{|\frac{a+x}{a-x}|}+C\end{align}$

$\begin{align}\int\frac{1}{\sqrt{x^2\pm a^2}}\mathrm{d}x=\ln{|x+\sqrt{x^2\pm a^2}|} +C\end{align}$

$\begin{align}\int\sqrt{x^2\pm a^2}\mathrm{d}x=\frac{x}{2}\sqrt{x^2\pm a^2}\pm\frac{a^2}{2}\ln(x+\sqrt{x^2\pm a^2}) +C\end{align}$

$\begin{align}\int\sqrt{a^2-x^2}\mathrm{d}x=\frac{x}{2}\sqrt{a^2-x^2}+\frac{a^2}{2}\arcsin\frac{x}{a}+C\end{align}$



## Newton-Leibniz Formula【牛顿-莱布尼兹公式】

$\begin{align}\int^{a}_{b}f(x)\mathrm{d}x=F(x)\bigg|^{a}_{b}=F(a)-F(b)\end{align}$

Which $F^{\prime}(x)=f(x)$



### Convolution【卷积】

$\begin{aligned}(f*g)(n)=\int^{\infin}_{-\infin}f(\tau)g(n-\tau)\mathrm{d}\tau\end{aligned}$

or

$\begin{aligned}(f*g)(n)=\sum^{\infin}_{\tau=-\infin}f(\tau)g(n-\tau)\end{aligned}$



# Transcendental Functions【超越函数】

analytic function



$\begin{align}\Gamma(x)=\int_0^{+\infin}t^{x-1}e^{-t}\mathrm{d}t\end{align}$

$\begin{align}\Beta(m,n) =\frac{\Gamma(n)}{\Gamma(m)\Gamma(n-m)}\end{align}$

$\begin{align}\Gamma(x+1)=x\Gamma(x),\quad\Gamma(n+1)=n!,\quad\Gamma(x)\Gamma(1-x)=\frac{\pi}{\sin\pi x}\end{align}$



$\begin{aligned}\zeta(s)=\sum_{n=1}^{\infin}\frac{1}{n^s}=\frac{1}{\Gamma(s)}\int^{\infin}_0\frac{x^{s-1}}{e^x-1}\mathrm{d}x\end{aligned}$



$\begin{aligned}W(x)=\sum\limits^{\infin}_{i=0}a^n\cos(b^n\pi x)\end{aligned}$ , which $\begin{aligned}0<a<1,b=2k+1,k\in Z^*, ab>1+\frac{3}{2}\pi\end{aligned}$



# Partial Derivative【偏导数】

### Hamiltonian【汉密尔顿算子】

$\begin{align}\nabla &=\frac{\partial}{\partial x}i +\frac{\partial}{\partial y}j + \frac{\partial}{\partial z}k\\ \nabla \cdot f&=\frac{\partial f_{x}}{\partial x} +\frac{\partial f_{y}}{\partial y} + \frac{\partial f_{z}}{\partial z} \\ \nabla \times f &= \begin{vmatrix} i & j & k\\ \frac{\partial}{\partial x} & \frac{\partial}{\partial y} & \frac{\partial}{\partial z} \\ f_{x} & f_{y} & f_{z} \end{vmatrix}\end{align}$

Which $f=f_xi+f_yj+f_zk=(f_x,f_y,f_z)$



### Laplace Operator【拉普拉斯算子】

$\begin{align}\Delta&={\nabla}^{2}=\nabla \cdot \nabla\\&=\frac{\partial^2}{\partial x^2} +\frac{\partial^2}{\partial y^2} + \frac{\partial^2}{\partial z^2}\end{align}$





## Field Theroy【场论】

Assume $u=f(x,y,z)$ is a scalar field, then directional derivative and gradient as follow.

$\begin{align}\frac{\partial u}{\partial n}\bigg|_P=\nabla f\cdot\vec n=\left(\frac{\partial f}{\partial x}\cos\alpha +\frac{\partial f}{\partial y}\cos\beta + \frac{\partial f}{\partial z}\cos\gamma\right)\bigg|_P \end{align}$

$\begin{align}\vec n=\frac{\vec a}{|\vec a|}=\frac{a_xi}{|\vec a|}+\frac{a_y j}{|\vec a|}+\frac{a_zk}{|\vec a|}\end{align}$



$\begin{aligned}{\rm{grad}}u=\frac{\partial u}{\partial x}i+\frac{\partial u}{\partial y}j+\frac{\partial u}{\partial z}k\end{aligned}$



Assume $A=P(x,y,z)i+Q(z,y,z)j+R(x,y,z)k$ is a vector field, then divergence, rotation and flux as follow.

$\begin{aligned}\mathrm{div}A=\nabla\cdot A=\frac{\partial P}{\partial x}+\frac{\partial Q}{\partial y}+\frac{\partial R}{\partial z}\end{aligned}$

$\begin{aligned}\mathrm{rot}A=\nabla\times A=\begin{vmatrix} i & j & k\\ \frac{\partial}{\partial x} & \frac{\partial}{\partial y} & \frac{\partial}{\partial z} \\ P & Q & R \end{vmatrix}\end{aligned}$

$\begin{aligned}\Phi=\iint\limits_{\Sigma}P\mathrm{d}y\mathrm{d}z+Q\mathrm{d}z\mathrm{d}x+R\mathrm{d}x\mathrm{d}y\end{aligned}$



# Surface Integrals【曲面积分】

$\begin{align} &\iint_{\Sigma}P(x,y,z)\mathrm{d}z\mathrm{d}y+Q(x,y,z)\mathrm{d}x\mathrm{d}y+R(x,y,z)\mathrm{d}y\mathrm{d}z\\
=&\iint_{\Sigma}\left(P(x,y,z)\frac{\mathrm{d}z\mathrm{d}y}{\mathrm{d}S}+Q(x,y,z)\frac{\mathrm{d}x\mathrm{d}y}{\mathrm{d}S}+R(x,y,z)\frac{\mathrm{d}y\mathrm{d}z}{\mathrm{d}S}\right)\mathrm{d}\\
=&\iint_{\Sigma}\left(P(x,y,z)\cos\alpha+Q(x,y,z)\cos\beta+R(x,y,z)\cos\gamma\right)\mathrm{d}S\end{align}$





## Green Formula【格林公式】

$\begin{align}\oint_{L} P(x,y)\mathrm{d}x+Q(x,y)\mathrm{d}y=\iint_{D}\left(\frac{\partial Q}{\partial x}-\frac{\partial P}{\partial y}\right)\mathrm{d}x\mathrm{d}y\end{align}$



## Gauss Theorem【高斯定理】

$\begin{aligned}\oiint\limits_{\Sigma}P\rm d\mit y\rm d\mit z+Q\rm d\mit z\rm d\mit x+R\rm d\mit x\rm d\mit y=\iiint\limits_{\Omega}\left(\frac{\partial P}{\partial x}+\frac{\partial Q}{\partial y}+\frac{\partial R}{\partial z}\right)\rm d\mit x\rm d\mit y\rm d\mit z\end{aligned}$

$\begin{aligned}\iiint{\nabla\cdot F\rm d\mit V} =\oiint\limits_{s}{F\cdot\rm d\mit S}\end{aligned}$



## Stokes Formula【斯托克斯公式】

$\begin{align}\oint\limits_{L}P\mathrm{d}x+Q\mathrm{d}y+R\mathrm{d}z&=\iint\limits_{\Sigma} \begin{vmatrix}\mathrm{d}y\mathrm{d}z & \mathrm{d}z\mathrm{d}x & \mathrm{d}x\mathrm{d}y\\ \frac{\partial}{\partial x} & \frac{\partial}{\partial y} & \frac{\partial}{\partial z} \\ P & Q & R \end{vmatrix}\\
&=\iint\limits_{\Sigma} \begin{vmatrix} cos\alpha & cos\beta & cos\gamma\\ \frac{\partial}{\partial x} & \frac{\partial}{\partial y} & \frac{\partial}{\partial z} \\ P & Q & R \end{vmatrix}\mathrm{d}S\end{align}$

$\begin{align}\iint\limits_{S}\nabla\times F\mathrm{d}S=\oint\limits_{\partial S}F\mathrm{d}r\end{align}$







Gauss



$\begin{aligned}f(x|\mu,\sigma^2)=\frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{(x-\mu)^2}{2\sigma^2}}\end{aligned}$





# Applications

Fourier
$$
f_l(x)=\frac{a_0}{2}+\sum^{\infin}_{i=0}(a_n\cos(n\omega x)+b_n\sin(n\omega x))
\\
\omega=\frac{\pi}{l}, a_n=\frac{1}{l}\int^l_{-l}f(t)\cos(n\omega x)\mathrm{d}t\\
b_n=\frac{1}{l}\int^l_{-l}f(t)\sin(n\omega x)\mathrm{d}t
$$




DCT-II

$\begin{aligned}f_m=\sum_{k=0}^{n-1}x_k\cos\left[\frac{\pi}{n}m\left(k+\frac{1}{2}\right)\right]\end{aligned}$





## Navier-Stokes equation

$\begin{aligned}\rho\frac{\mathrm{d}v}{\mathrm{d}t}=-\nabla p+\rho F+\mu\Delta v\end{aligned}$



## wave equations

$\begin{align}\frac{\partial^2 u}{\partial t^2}=c^2\Delta u\end{align}$

$u = u(x,t)$ represents amplitude.

## Maxwell's Equations

$\begin{aligned}
\left
\{\begin{array}{rcl}
\begin{aligned}\nabla\times H\end{aligned}&=&\begin{aligned}J+\frac{\partial D}{\partial t}\end{aligned}\\
\begin{aligned}\nabla\times E\end{aligned}&=&\begin{aligned}-\frac{\partial B}{\partial t}\end{aligned}\\
\begin{aligned}\nabla\cdot B\end{aligned}&=&\begin{aligned}0\end{aligned}\\
\begin{aligned}\nabla\cdot D\end{aligned}&=&\begin{aligned}\rho\end{aligned}
\end{array}
\right.
\end{aligned}$

$D=\varepsilon E \quad B=\mu H \quad J=\sigma E$

磁场强度H的旋度等于该点的全电流密度（传导电流密度J与位移电流密度$\begin{aligned}\frac{\partial D}{\partial t}\end{aligned}$之和

电场强度E的旋度等于该点磁通密度B的时间变化率的负值

磁通密度B的散度恒等于零

电位移D的散度仍等于该点的自由电荷体密度

ε是媒质的介电常数，μ是媒质的磁导率，σ是媒质的电导率



## Lorentz force

$F=q(E+v\times B)$

F是洛伦兹力， q是带电粒子的电荷量，E是电场强度， v是带电粒子的速度， B是磁感应强度。

$\begin{align}F=\int V(pE+J\times B)\mathrm{d}r\end{align}$

V是积分的体积，p是电荷密度，J是电流密度，dr是微小体元素。



Combinatorics
=============

* Factorial【阶乘】

$\begin{aligned}f(0)=1,f(n)=nf(n-1)=\prod_{i=1}^ni=n!\quad n>0\end{aligned}$

* Arrangement【排列数】

$\begin{align}{\rm{A}}_n^{m}=\frac{n!}{(n-m)!}=\prod_{i=n-m+1}^ni\end{align}$

* Combination【组合数】

$\begin{align}{\rm{C}}_n^{m}=\frac{n!}{m!(n-m)!}\end{align}$

* Catalan Number【Catalan数】

$\begin{aligned}f(0)=1,f(1)=1,f(n)=\sum\limits_{i=0}^{n-1}f(n-1-i)f(i)=\frac{(2n)!}{(n+1)!n!}=\frac{{\rm{C}}_{2n}^n}{n+1}\end{aligned}$

## Bertrand's ballot problem

In an election where candidate A receives $p$ votes and candidate B receives $q$ votes with $p > q$, what is the probability that A will be strictly ahead of B throughout the count?

The answer is $\begin{aligned}\frac{p-q}{p+q}\end{aligned}$

What about A will be ahead of B throughout the count NOT strictly?

The answer is? $\begin{aligned}\frac{p-q}{p+q}\end{aligned}$


とある不透明の箱の中に形が一致のN種類の珠が入れています。そのたまの個数はM1、M2、……MN。そのたまを箱から一つ一つ抜き出す、ならば箱に一番抜ききれるのたまは第一種類の珠の可能性はどのくらいですか？

$p(\gamma)=\frac{\sum_{i=0}^{l}p([{\gamma}_{1},{\gamma}_{2},...,{\gamma}_{i}-1,\dots,{\gamma}_{l},])}{\sum_{i=0}^{l}{\gamma}_{i}}$

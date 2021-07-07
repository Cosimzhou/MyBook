Using Latex math expression
=================================



## Usages

### Subscripts & supscripts

> a_1   x^2   e^{-at}    a_{ij}^3     e^{x^2}\neq {e^x}^2

$a_{1}$       $x^{2}$        $e^{-\alpha t}$           $a^{3}_{ij}$           $e^{x^{2}} \neq {e^x}^2$



### Square root

> \sqrt{x}      \sqrt{x^2 + \sqrt{y}}     \sqrt[3]{2}      \surd[x^2+y^2]

$\sqrt{x}$            $\sqrt{x^2 + \sqrt{y}}$           $\sqrt[3]{2}$            $\surd[x^2+y^2]$



### Overlines or underlines

> \overline{m+n}       \underline{m+n}       \underbrace{1+2+\cdots+n}_{n}

$\overline{m+n}$          $\underline{m+n}$             $\underbrace{1+2+\cdots+n}_{n}$



### Vectors

> \overrightarrow{AB}      \vec a

$\overrightarrow{AB}            $               $\vec a$



### Fractions

> 1\frac{1}{2}hours      x^{1/2}         x^\frac{2}{k+1}        \frac{x^2}{k+1}

$1\frac{1}{2}hours$           $x^{1/2}$             $x^\frac{2}{k+1}$               $\frac{x^2}{k+1}$



### Large operators

> \sum\limits_{i=1}^{n}\frac{1}{n^2+1}           \int_{0}^{\frac{\pi}{2}}\sin{x}       \prod_\epsilon

$\sum\limits_{i=1}^{n}\frac{1}{n^2+1}$             $\int_{0}^{\frac{\pi}{2}}\sin{x}$         $\prod_\epsilon$



### Matrix

> \begin{matrix}	0 & 1 \\\   1 & 0 \end{matrix}
> \begin{pmatrix}	0 & -i \\\	i & 0\end{pmatrix}
>
> \begin{bmatrix}    0 & -1 \\\	1 & 0\end{bmatrix}
> \begin{Bmatrix}	1 & 0 \\\	0 & -1\end{Bmatrix}
>
> \begin{vmatrix}	a & b \\\	c & d\end{vmatrix}
> \begin{Vmatrix}	i & 0 \\\	0 & -i\end{Vmatrix}

$\begin{matrix} 0 & 1 \\ 1 & 0 \end{matrix}$        $\begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix}$         $\begin{bmatrix} 0 & -1 \\ 1 & 0 \end{bmatrix}$         $\begin{Bmatrix} 1 & 0 \\ 0 & -1 \end{Bmatrix}$          $\begin{vmatrix} a & b \\ c & d \end{vmatrix}$         $\begin{Vmatrix} i & 0 \\ 0 & -i \end{Vmatrix}$


### Math
> {2n \choose n}
>
> \biniom{p+q}{p}
>
> \frac{p+q}{p}
>
> {k_0,k_1,\ldots>0 \atop k_0+k_1+\cdots=n}



${2n\choose n}$          ${\binom{p+q}{p}}$           ${\frac{p+q}{p}}$             ${k_0,k_1,\ldots>0 \atop k_0+k_1+\cdots=n}$



### Margin

| a             | source    | b      | source | c           | source   |
| ------------- | --------- | ------ | ------ | ----------- | -------- |
| $ab$          | ab        | $a\!b$ | a\\!b  | $a\,b$      | a\,b     |
| $a\ b$        | a\ b      | $a\:b$ | a\;b   | $a \quad b$ | a\quad b |
| $ a \qquad b$ | a\qquad b |        |        |             |          |



### Examples

> \nabla \times f = \begin{vmatrix}
> 			 i & j & k\\\
> 		    \frac{\partial}{\partial x} & \frac{\partial}{\partial y} & \frac{\partial}{\partial z} \\\
> 			 f_{x} & f_{y} & f_{z}
> \end{vmatrix}

$\nabla \times f = \begin{vmatrix} i & j & k\\ \frac{\partial}{\partial x} & \frac{\partial}{\partial y} & \frac{\partial}{\partial z} \\ f_{x} & f_{y} & f_{z} \end{vmatrix}$



> \begin{equation}
> 	\left\\{
> 		\begin{aligned}
> 			\overset{.}x(t) &=A_{ci}x(t)+B_{1ci}w(t)+B_{2ci}u(t) \\\
> 			z(t) &=C_{ci}x(t)+D_{ci}u(t)
> 		\end{aligned}
> 	\right.
> \end{equation}

$\begin{equation}\left\{\begin{aligned}
\overset{.}x(t) &=A_{ci}x(t)+B_{1ci}w(t)+B_{2ci}u(t) \\
z(t) &=C_{ci}x(t)+D_{ci}u(t) \\
\end{aligned} \right.\end{equation}$



> \left\\{
> 	\begin{array}{lr}
> 		x=\dfrac{3\pi}{2}(1+2t)\cos(\dfrac{3\pi}{2}(1+2t)),   & \\\
> 		y=s, 																					& 0\leq s\leq L,|t|\leq1.\\\
> 		z=\dfrac{3\pi}{2}(1+2t)\sin(\dfrac{3\pi}{2}(1+2t)),     &
> 	\end{array}
> \right.

$\left\{\begin{array}{lr}x=\dfrac{3\pi}{2}(1+2t)\cos(\dfrac{3\pi}{2}(1+2t)), & \\ y=s, & 0\leq s\leq L,|t|\leq1.\\ z=\dfrac{3\pi}{2}(1+2t)\sin(\dfrac{3\pi}{2}(1+2t)), & \end{array}\right.$



> \begin{pmatrix}
> 	1 & 1 & 1 & \cdots & 1 \\\
> 	a_{1,1} & a_{2,1} & a_{3,1} & \cdots & a_{n,1} \\\
> 	a_{1,2} & a_{2,2} & a_{3,2} & \cdots& a_{n,2} \\\
> 	\vdots & \vdots & \vdots & \ddots & \vdots \\\
> 	a_{1,m-1} & a_{2,m-1} & a_{3,m-1} &\cdots & a_{n,m-1}
> \end{pmatrix}

$\begin{pmatrix} 1 & 1 & 1 & \cdots & 1 \\ a_{1,1} & a_{2,1} & a_{3,1} & \cdots & a_{n,1} \\ a_{1,2} & a_{2,2} & a_{3,2} & \cdots& a_{n,2} \\ \vdots & \vdots & \vdots & \ddots & \vdots \\ a_{1,m-1} & a_{2,m-1} & a_{3,m-1} &\cdots & a_{n,m-1} \end{pmatrix}$



### Chemistry equations

> \ce{BaCl_2 + H_2SO_4 = 2HCl +BaSO_4 v}
> \ce{2KClO_3 = 2KCl +3O_2\uparrow}​

$\ce{BaCl_2 + H_2SO_4 = 2HCl +BaSO_4 v}$

$\ce{2KClO_3 = 2KCl +3O_2\uparrow}$



## Latex Symbols

### Alphabet

| a           | source    | b           | source    | c             | source      | d               | source        |
| ----------- | --------- | ----------- | --------- | ------------- | ----------- | --------------- | ------------- |
| $\hat{a}$   | \hat{a}   | $\check{a}$ | \check{a} | $\tilde{a}$   | \tilde{a}   | $\acute{a}$     | \acute{a}     |
| $\grave{a}$ | \grace{a} | $\dot{a}$   | \dot{a}   | $\ddot{a}$    | \ddot{a}    | $\breve{a}$     | \breve{a}     |
| $\bar{a}$   | \bar{a}   | $\vec{a}$   | \vec{a}   | $\widehat{a}$ | \widehat{a} | $\widetilde{a}$ | \widetilde{a} |

### Greek alphabeta

| a             | source      | b           | source    | c           | source    | d          | source   |
| ------------- | ----------- | ----------- | --------- | ----------- | --------- | ---------- | -------- |
| $\alpha$      | \alpha      | $\theta$    | \theta    | $o$         | o         | $\upsilon$ | \upsilon |
| $\beta$       | \beta       | $\vartheta$ | \vartheta | $\pi$       | \pi       | $\phi$     | \phi     |
| $\gamma$      | \gamma      | $\iota$     | \iota     | $\varpi$    | \varpi    | $\varphi$  | \varphi  |
| $\delta$      | \delta      | $\kappa$    | \kappa    | $\rho$      | \rho      | $\chi$     | \chi     |
| $\epsilon$    | \epsilon    | $\lambda$   | \lambda   | $\varrho$   | \varrho   | $\psi$     | \psi     |
| $\varepsilon$ | \varepsilon | $\mu$       | \mu       | $\sigma$    | \sigma    | $\omega$   | \omega   |
| $\zeta$       | \zeta       | $\nu$       | \nu       | $\varsigma$ | \varsigma |            |          |
| $\eta$        | \eta        | $\xi$       | \xi       | $\tau$      | \tau      |            |          |

| a        | source | b         | source  | c          | source   | d        | source |
| -------- | ------ | --------- | ------- | ---------- | -------- | -------- | ------ |
| $\Delta$ | \Delta | $\Lambda$ | \Lambda | $\Sigma$   | \Sigma   | $\Psi$   | \Psi   |
| $\Gamma$ | \Gamma | $\Xi$     | \Xi     | $\Upsilon$ | \Upsilon | $\Omega$ | \Omega |
| $\Theta$ | \Theta | $\Pi$     | \Pi     | $\Phi$     | \Phi     |          |        |



### Binary relational operators

| a             | source      | b             | source       | c         | source      |
| ------------- | ----------- | ------------- | ------------ | --------- | ----------- |
| $<$           | <           | $>$           | >            | $=$       | =           |
| $\leq$        | \leq or \le | $\geq$        | \geq or \ge  | $\equiv$  | \equiv      |
| $\ll$         | \ll         | $\gg$         | \gg          | $\doteq$  | \doteq      |
| $\prec$       | \prec       | $\succ$       | \succ        | $\sim$    | \sim        |
| $\preceq$     | \preceq     | $\succeq$     | \succeq      | $\simeq$  | \simeq      |
| $\subset$     | \subset     | $\supset$     | \supset      | $\approx$ | \approx     |
| $\subseteq$   | \subseteq   | $\supseteq$   | \supseteq    | $\cong$   | \cong       |
| $\sqsubset$   | \sqsubset   | $\sqsupset$   | \sqsupset    | $\Join$   | \Join       |
| $\sqsubseteq$ | \sqsubseteq | $\sqsupseteq$ | \sqsupseteq  | $\bowtie$ | \bowtie     |
| $\in$         | \in         | $\ni$         | \ni or \owns | $\propto$ | \propto     |
| $\vdash$      | \vdash      | $\dashv$      | \dashv       | $\models$ | \models     |
| $\mid$        | \mid        | $\parallel$   | \parallel    | $\perp$   | \perp       |
| $\smile$      | \smile      | $\frown$      | \frown       | $\asymp$  | \asymp      |
| $:$           | :           | $\notin$      | \notin       | $\neq$    | \neq or \ne |



### Binary operators

| a                | source         | b                  | source           | c                | source         |
| ---------------- | -------------- | ------------------ | ---------------- | ---------------- | -------------- |
| $+$              | +              | $-$                | -                | $\triangleleft$  | \triangleleft  |
| $\pm$            | \pm            | $\mp$              | \mp              | $\triangleright$ | \triangleright |
| $\cdot$          | \cdot          | $\div$             | \div             | $\star$          | \star          |
| $\times$         | \times         | $\setminus$        | \setminus        | $\ast$           | \ast           |
| $\cup$           | \cup           | $\cap$             | \cap             | $\circ$          | \circ          |
| $\sqcup$         | \sqcup         | $\sqcap$           | \sqcap           | $\bullet$        | \bullet        |
| $\vee$           | \vee or \lor   | $\wedge$           | \wedge or \land  | $\diamond$       | \diamond       |
| $\oplus$         | \oplus         | $\ominus$          | \ominus          | $\uplus$         | \uplus         |
| $\odot$          | \odot          | $\oslash$          | \oslash          | $\amalg$         | \amalg         |
| $\otimes$        | \otimes        | $\bigcirc$         | \bigcirc         | $\dagger$        | \dagger        |
| $\bigtriangleup$ | \bigtriangleup | $\bigtriangledown$ | \bigtriangledown | $\ddagger$       | \ddagger       |
| $\lhd$           | \lhd           | $\rhd$             | \rhd             | $\wr$            | \wr            |
| $\unlhd$         | \unlhd         | $\unrhd$           | \unrhd           |                  |                |



### Large operators

| a         | source  | b           | source    | c           | source    | d            | source     |
| --------- | ------- | ----------- | --------- | ----------- | --------- | ------------ | ---------- |
| $\sum$    | \sum    | $\bigcup$   | \bigcup   | $\bigvee$   | \bigvee   | $\bigoplus$  | \bigoplus  |
| $\prod$   | \prod   | $\bigcap$   | \bigcap   | $\bigwedge$ | \bigwedge | $\bigotimes$ | \bigotimes |
| $\coprod$ | \coprod | $\bigsqcup$ | \bigsqcup | $\biguplus$ | \biguplus | $\bigodot$   | \bigodot   |
| $\int$    | \int    | $\iint$     | \iint     | $\iiint$    | \iiint    | $\iiiint$    | \iiiint    |
| $\oint$   | \oint   | $\oiint$    | \oiint    | $\oiiint$   | \oiiint   |              |            |



### Arrows

| a                    | source              | b                     | source              | c              | source       |
| -------------------- | ------------------- | --------------------- | ------------------- | -------------- | ------------ |
| $\gets$              | \leftarrow or \gets | $\longleftarrow$      | \longleftarrow      | $\uparrow$     | \uparrow     |
| $\to$                | \rightarrow or \to  | $\longrightarrow$     | \longrightarrow     | $\downarrow$   | \downarrow   |
| $\leftrightarrow$    | \leftrightarrow     | $\longleftrightarrow$ | \longleftrightarrow | $\updownarrow$ | \updownarrow |
| $\Leftarrow$         | \Leftarrow          | $\Longleftarrow$      | \Longleftarrow      | $\Uparrow$     | \Uparrow     |
| $\Rightarrow$        | \Rightarrow         | $\Longrightarrow$     | \Longrightarrow     | $\Downarrow$   | \Downarrow   |
| $\Leftrightarrow$    | \Leftrightarrow     | $\Longleftrightarrow$ | \Longleftrightarrow | $\Updownarrow$ | \Updownarrow |
| $\mapsto$            | \mapsto             | $\longmapsto$         | \longmapsto         | $\nearrow$     | \nearrow     |
| $\hookleftarrow$     | \hookleftarrow      | $\hookrightarrow$     | \hookrightarrow     | $\searrow$     | \searrow     |
| $\leftharpoonup$     | \leftharpoonup      | $\rightharpoonup$     | \rightharpoonup     | $\swarrow$     | \swarrow     |
| $\leftharpoondown$   | \leftharpoondown    | $\rightharpoondown$   | \rightharpoondown   | $\nwarrow$     | \nwarrow     |
| $\rightleftharpoons$ | \rightleftharpoons  | $\iff$                | \iff                | $\leadsto$     | \leadsto     |



### Delimitors

| a         | source         | b            | source         | c              | source       | d              | source       |
| --------- | -------------- | ------------ | -------------- | -------------- | ------------ | -------------- | ------------ |
| $($       | (              | $)$          | )              | $\uparrow$     | \uparrow     | $\Uparrow$     | \Uparrow     |
| $\lbrack$ | [ or \lbrack   | $\rbrack$    | ] or \rbrack   | $\downarrow$   | \downarrow   | $\Downarrow$   | \Downarrow   |
| $\{$      | \\{ or \lbrace | $\}$         | \\} or \rbrace | $\updownarrow$ | \updownarrow | $\Updownarrow$ | \Updownarrow |
| $\langle$ | \langle        | $\rangle$    | \rangle        | $\vert$        | \| or \vert  | $\Vert$        | \\           |
| $\lfloor$ | \lfloor        | $\rfloor$    | \rfloor        | $\lceil$       | \lceil       | $\rceil$       | \rceil       |
| $/$       | /              | $\backslash$ | \backslash     | $.$            | .            |                |              |



### Large delimitors

| a         | source  | b             | source      | c            | source     |
| --------- | ------- | ------------- | ----------- | ------------ | ---------- |
| $\lgroup$ | \lgroup | $\lmoustache$ | \lmoustache | $\arrowvert$ | \arrowvert |
| $\rgroup$ | \rgroup | $\rmoustache$ | \rmoustache | $\Arrowvert$ | \Arrowvert |
|           |         |               |             | $\bracevert$ | \bracevert |



### Other symbols

| a              | source        | b            | source     | c           | source    | d            | source     |
| -------------- | ------------- | ------------ | ---------- | ----------- | --------- | ------------ | ---------- |
| $\dots$        | \dots         | $\cdots$     | \cdots     | $\vdots$    | \vdots    | $\ddots$     | \ddots     |
| $\hbar$        | \hbar         | $\imath$     | \imath     | $\jmath$    | \jmath    | $\ell$       | \ell       |
| $\Re$          | \Re           | $\Im$        | \Im        | $\aleph$    | \aleph    | $\wp$        | \wp        |
| $\forall$      | \forall       | $\exists$    | \exists    | $\mho$      | \mho      | $\partial$   | \partial   |
| $'$            | '             | $\prime$     | \prime     | $\emptyset$ | \emptyset | $\infty$     | \infty     |
| $\nabla$       | \nabla        | $\triangle$  | \triangle  | $\Box$      | \Box      | $\Diamond$   | \Diamond   |
| $\bot$         | \bot          | $\top$       | \top       | $\angle$    | \angle    | $\surd$      | \surd      |
| $\diamondsuit$ | \diamondsuit  | $\heartsuit$ | \heartsuit | $\clubsuit$ | \clubsuit | $\spadesuit$ | \spadesuit |
| $\neg$         | \neg or \lnot | $\flat$      | \flat      | $\natural$  | \natural  | $\sharp$     | \sharp     |



### Unmath symbols

| a    | source | b    | source | c    | source     |
| ---- | ------ | ---- | ------ | ---- | ---------- |
| $†$  | \dag   | $\S$ | \S     | $©$  | \copyright |
| $‡$  | \ddag  | $\P$ | \P     | $£$  | \pouds     |

### AMS delimitors

| a           | source    | b           | source    | c        | source |
| ----------- | --------- | ----------- | --------- | -------- | ------ |
| $\ulcorner$ | \ulcorner | $\lrcorner$ | \lrcorner | $\lVert$ | \lVert |
| $\urcorner$ | \urcorner | $\lvert$    | \lvert    | $\rVert$ | \rVert |
| $\llcorner$ | \llcorner | $\rvert$    | \rvert    |          |        |

### AMS Greek and Hebrew letters

| a          | source   | b           | source    | c        | source |
| ---------- | -------- | ----------- | --------- | -------- | ------ |
| $\digamma$ | \digamma | $\varkappa$ | \varkappa | $\beth$  | \beth  |
| $\daleth$  | \daleth  | $\gimel$    | \gimel    | $\aleph$ | \aleph |



### AMS binary relational symbols

| a                  | source           | b                   | source            | c                     | source              |
| ------------------ | ---------------- | ------------------- | ----------------- | --------------------- | ------------------- |
| $\lessdot$         | \lessdot         | $\gtrdot$           | \gtrdot           | $\Doteq$              | \doteqdot or \Doteq |
| $\leqslant$        | \leqslant        | $\geqslant$         | \geqslant         | $\risingdotseq$       | \risingdotseq       |
| $\eqslantless$     | \eqslantless     | $\eqslantgtr$       | \eqslantgtr       | $\fallingdotseq$      | \fallingdotseq      |
| $\leqq$            | \leqq            | $\geqq$             | \geqq             | $\eqcirc$             | \eqcirc             |
| $\lll$             | \lll or \llless  | $\ggg$              | \ggg or \gggtr    | $\circeq$             | \circeq             |
| $\lesssim$         | \lesssim         | $\gtrsim$           | \gtrsim           | $\triangleq$          | \triangleq          |
| $\lessapprox$      | \lessapprox      | $\gtrapprox$        | \gtrapprox        | $\bumpeq$             | \bumpeq             |
| $\lessgtr$         | \lessgtr         | $\gtrless$          | \gtrless          | $\Bumpeq$             | \Bumpeq             |
| $\lesseqgtr$       | \lesseqgtr       | $\gtreqless$        | \gtreqless        | $\thicksim$           | \thicksim           |
| $\lesseqqgtr$      | \lesseqqgtr      | $\gtreqqless$       | \gtreqqless       | $\thickapprox$        | \thickapprox        |
| $\preccurlyeq$     | \preccurlyeq     | $\succcurlyeq$      | \succcurlyeq      | $\approxeq$           | \approxeq           |
| $\curlyeqprec$     | \curlyeqprec     | $\curlyeqsucc$      | \curlyeqsucc      | $\backsim$            | \backsim            |
| $\precsim$         | \precsim         | $\succsim$          | \succsim          | $\backsimeq$          | \backsimeq          |
| $\precapprox$      | \precapprox      | $\succapprox$       | \succapprox       | $\vDash$              | \vDash              |
| $\subseteqq$       | \subseteqq       | $\supseteqq$        | \supseteqq        | $\Vdash$              | \Vdash              |
| $\Subset$          | \Subset          | $\Supset$           | \Supset           | $\Vvdash$             | \Vvdash             |
| $\sqsubset$        | \sqsubset        | $\sqsupset$         | \sqsupset         | $\backepsilon$        | \backepsilon        |
| $\therefore$       | \therefore       | $\because$          | \because          | $\varpropto$          | \varpropto          |
| $\shortmid$        | \shortmid        | $\shortparallel$    | \shortparallel    | $\between$            | \between            |
| $\smallsmile$      | \smallsmile      | $\smallfrown$       | \smallfrown       | $\pitchfork$          | \pitchfork          |
| $\vartriangleleft$ | \vartriangleleft | $\vartriangleright$ | \vartriangleright | $\blacktriangleleft$  | \blacktriangleleft  |
| $\trianglelefteq$  | \trianglelefteq  | $\trianglerighteq$  | \trianglerighteq  | $\blacktriangleright$ | \blacktriangleright |





### AMS arrows

| a                    | source             | b                    | source             | c                      | source               |
| -------------------- | ------------------ | -------------------- | ------------------ | ---------------------- | -------------------- |
| $\dashleftarrow$     | \dashleftarrow     | $\dashrightarrow$    | \dashrightarrow    | $\multimap$            | \multimap            |
| $\leftleftarrows$    | \leftleftarrows    | $\rightrightarrows$  | \rightrightarrows  | $\upuparrows$          | \upuparrows          |
| $\leftrightarrows$   | \leftrightarrows   | $\rightleftarrows$   | \rightleftarrows   | $\downdownarrows$      | \downdownarrows      |
| $\Lleftarrow$        | \Lleftarrow        | $\Rightarrow$        | \Rightarrow        | $\upharpoonleft$       | \upharpoonleft       |
| $\twoheadleftarrow$  | \twoheadleftarrow  | $\twoheadrightarrow$ | \twoheadrightarrow | $\upharpoonright$      | \upharpoonright      |
| $\leftarrowtail$     | \leftarrowtail     | $\rightarrowtail$    | \rightarrowtail    | $\downharpoonleft$     | \downharpoonleft     |
| $\leftrightharpoons$ | \leftrightharpoons | $\rightleftharpoons$ | \rightleftharpoons | $\downharpoonright$    | \downharpoonright    |
| $\Lsh$               | \Lsh               | $\Rsh$               | \Rsh               | $\rightsquigarrow$     | \rightsquigarrow     |
| $\looparrowleft$     | \looparrowleft     | $\looparrowright$    | \looparrowright    | $\leftrightsquigarrow$ | \leftrightsquigarrow |
| $\curvearrowleft$    | \curvearrowleft    | $\curvearrowright$   | \curvearrowright   |                        |                      |
| $\circlearrowleft$   | \circlearrowleft   | $\circlearrowright$  | \circlearrowright  |                        |                      |



### AMS binary negative operators and arrows

| a               | Source        | b               | source        | c                   | source            |
| --------------- | ------------- | --------------- | ------------- | ------------------- | ----------------- |
| $\nless$        | \nless        | $\ngtr$         | \ngtr         | $\varsubsetneqq$    | \varsubsetneqq    |
| $\lneq$         | \lneq         | $\gneq$         | \gneq         | $\varsupsetneqq$    | \varsupsetneqq    |
| $\nleq$         | \nleq         | $\ngeq$         | \ngeq         | $\nsubseteqq$       | \nsubseteqq       |
| $\nleqslant$    | \nleqslant    | $\ngeqslant$    | \ngeqslant    | $\nsupseteqq$       | \nsupseteqq       |
| $\lneqq$        | \lneqq        | $\gneqq$        | \gneqq        | $\nmid$             | \nmid             |
| $\lvertneqq$    | \lvertneqq    | $\gvertneqq$    | \gvertneqq    | $\nparallel$        | \nparallel        |
| $\nleqq$        | \nleqq        | $\ngeqq$        | \ngeqq        | $\nshortmid$        | \nshortmid        |
| $\lnsim$        | \lnsim        | $\gnsim$        | \gnsim        | $\nshortparallel$   | \nshortparallel   |
| $\lnapprox$     | \lnapprox     | $\gnapprox$     | \gnapprox     | $\nsim$             | \nsim             |
| $\nprec$        | \nprec        | $\nsucc$        | \nsucc        | $\ncong$            | \ncong            |
| $\npreceq$      | \npreceq      | $\nsucceq$      | \nsucceq      | $\nvdash$           | \nvdash           |
| $\precneqq$     | \precneqq     | $\succneqq$     | \succneqq     | $\nvDash$           | \nvDash           |
| $\precnsim$     | \precnsim     | $\succnsim$     | \succnsim     | $\nVdash$           | \nVdash           |
| $\precnapprox$  | \precnapprox  | $\succnapprox$  | \succnapprox  | $\nVDash$           | \nVDash           |
| $\subsetneq$    | \subsetneq    | $\supsetneq$    | \supsetneq    | $\ntriangleleft$    | \ntriangleleft    |
| $\varsubsetneq$ | \varsubsetneq | $\varsupsetneq$ | \varsupsetneq | $\ntriangleright$   | \ntriangleright   |
| $\nsubseteq$    | \nsubseteq    | $\nsupseteq$    | \nsupseteq    | $\ntrianglelefteq$  | \ntrianglelefteq  |
| $\subsetneqq$   | \subsetneqq   | $\supsetneqq$   | \supsetneqq   | $\ntrianglerighteq$ | \ntrianglerighteq |
| $\nleftarrow$   | \nleftarrow   | $\nrightarrow$  | \nrightarrow  | $\nleftrightarrow$  | \nleftrightarrow  |
| $\nLeftarrow$   | \nLeftarrow   | $\nRightarrow$  | \nRightarrow  | $\nLeftrightarrow$  | \nLeftrightarrow  |



### AMS binary operators

| a                 | source             | b                  | source             | c                 | source          |
| ----------------- | ------------------ | ------------------ | ------------------ | ----------------- | --------------- |
| $\dotplus$        | \dotplus           | $\centerdot$       | \centerdot         | $\intercal$       | \intercal       |
| $\ltimes$         | \ltimes            | $\rtimes$          | \rtimes            | $\divideontimes$  | \divideontimes  |
| $\Cup$            | \Cup or \doublecup | $\Cap$             | \Cap or \doublecap | $\smallsetminus$  | \smallsetminus  |
| $\veebar$         | \veebar            | $\barwedge$        | \barwedge          | $\doublebarwedge$ | \doublebarwedge |
| $\boxplus$        | \boxplus           | $\boxminus$        | \boxminus          | $\circleddash$    | \circleddash    |
| $\boxtimes$       | \boxtimes          | $\boxdot$          | \boxdot            | $\circledcirc$    | \circledcirc    |
| $\leftthreetimes$ | \leftthreetimes    | $\rightthreetimes$ | \rightthreetimes   | $\circledast$     | \circledast     |
| $\curlyvee$       | \curlyvee          | $\curlywedge$      | \curlywedge        |                   |                 |

### AMS other symbols

| a               | source        | b                    | source             | c                 | source          |
| --------------- | ------------- | -------------------- | ------------------ | ----------------- | --------------- |
| $\hbar$         | \hbar         | $\hslash$            | \hslash            | $\Bbbk$           | \Bbbk           |
| $\square$       | \square       | $\blacksquare$       | \blacksquare       | $\circledS$       | \circledS       |
| $\vartriangle$  | \vartriangle  | $\blacktriangle$     | \blacktriangle     | $\complement$     | \complement     |
| $\triangledown$ | \triangledown | $\blacktriangledown$ | \blacktriangledown | $\Game$           | \Game           |
| $\lozenge$      | \lozenge      | $\blacklozenge$      | \blacklozenge      | $\bigstar$        | \bigstar        |
| $\angle$        | \angle        | $\measuredangle$     | \measuredangle     | $\sphericalangle$ | \sphericalangle |
| $\diagup$       | \diagup       | $\diagdown$          | \diagdown          | $\backprime$      | \backprime      |
| $\nexists$      | \nexists      | $\Finv$              | \Finv              | $\varnothing$     | \varnothing     |
| $\eth$          | \eth          | $\mho$               | \mho               |                   |                 |

### Math Letter

| Example             | source            | package |
| ------------------- | ----------------- | ------- |
| $\mathrm{ABCdef}$   | \mathrm{ABCdef}   |         |
| $\mathit{ABCdef}$   | \mathit{ABCdef}   |         |
| $\mathcal{ABC}$     | \mathcal{ABC}     |         |
| $\mathscr{ABC}$     | \mathscr{ABC}     |         |
| $\mathfrak{ABCdef}$ | \mathfrak{ABCdef} |         |
| $\mathbb{ABC}$      | \mathbb{ABC}      |         |
| $\boldsymbol{ABC}$  | \boldsymbol{ABC}  |         |


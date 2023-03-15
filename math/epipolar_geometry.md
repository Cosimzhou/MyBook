Epipolar Geometry
=================

$a=(x_1,y_1,z_1),b=(x_2,y_2,z_2)$

$a\times b=\det\begin{vmatrix}i&j&k\\x_1&y_1&z_1\\x_2&y_2&z_2\end{vmatrix}=(y_1z_2-y_2z_1)i+(x_2z_1-x_1z_2)j+(x_1y_2-x_2y_1)j$


* $\sin^2\theta+\cos^2\theta=1$
* $\begin{align}\tan\theta=\frac{\sin\theta}{\cos\theta}\end{align}$
* $\begin{align}\cot\theta=\frac{\cos\theta}{\sin\theta}\end{align}$
* $\begin{align}\cos^2\theta=\frac{1}{1+\tan^2\theta}\end{align}$
* $\begin{align}\sin^2\theta=\frac{1}{1+\cot^2\theta}\end{align}$

* $\sin(\alpha+\beta)=\sin\alpha\cos\beta+\cos\alpha\sin\beta$
* $\cos(\alpha+\beta)=\cos\alpha\cos\beta-\sin\alpha\sin\beta$
* $\begin{align}\tan(\alpha+\beta)=\frac{\tan\alpha+\tan\beta}{1-\tan\alpha\tan\beta}\end{align}$

* $\begin{align}\sin\alpha\sin\beta=\frac{1}{2}\Big[\cos(\alpha-\beta)+\cos(\alpha+\beta)\Big]\end{align}$
* $\begin{align}\cos\alpha\cos\beta=\frac{1}{2}\Big[\cos(\alpha-\beta)-\cos(\alpha+\beta)\Big]\end{align}$
* $\begin{align}\sin\alpha\cos\beta=\frac{1}{2}\Big[\sin(\alpha-\beta)+\sin(\alpha+\beta)\Big]\end{align}$
* $\begin{align}\cos\alpha\sin\beta=\frac{1}{2}\Big[\sin(\alpha+\beta)-\sin(\alpha-\beta)\Big]\end{align}$

* $\begin{align}\sin\alpha+\sin\beta=2\sin\frac{\alpha+\beta}{2}\cos\frac{\alpha-\beta}{2}\end{align}$
* $\begin{align}\sin\alpha-\sin\beta=2\cos\frac{\alpha+\beta}{2}\sin\frac{\alpha-\beta}{2}\end{align}$
* $\begin{align}\cos\alpha+\cos\beta=2\cos\frac{\alpha+\beta}{2}\cos\frac{\alpha-\beta}{2}\end{align}$
* $\begin{align}\cos\alpha-\cos\beta=-2\sin\frac{\alpha+\beta}{2}\sin\frac{\alpha-\beta}{2}\end{align}$

* $\begin{align}\tan\alpha+\tan\beta=\frac{\sin(\alpha+\beta)}{\cos\alpha\cos\beta}\end{align}$
* $\begin{align}\tan\alpha-\tan\beta=\frac{\sin(\alpha-\beta)}{\cos\alpha\cos\beta}\end{align}$
* $\begin{align}\cot\alpha+\cot\beta=\frac{\sin(\alpha+\beta)}{\sin\alpha\sin\beta}\end{align}$
* $\begin{align}\cot\alpha-\cot\beta=-\frac{\sin(\alpha-\beta)}{\sin\alpha\sin\beta}\end{align}$
* $\begin{align}\tan\alpha+\cot\beta=\frac{\cos(\alpha-\beta)}{\cos\alpha\sin\beta}\end{align}$
* $\begin{align}\tan\alpha-\cot\beta=-\frac{\cos(\alpha+\beta)}{\cos\alpha\sin\beta}\end{align}$

* $\begin{align}\sin^2\alpha-\sin^2\beta=\sin(\alpha+\beta)\sin(\alpha-\beta)\end{align}$
* $\begin{align}\cos^2\alpha-\cos^2\beta=-\sin(\alpha+\beta)\sin(\alpha-\beta)\end{align}$
* $\begin{align}\cos^2\alpha-\sin^2\beta=\cos(\alpha+\beta)\cos(\alpha-\beta)\end{align}$
* $\begin{align}\sin^2\alpha-\cos^2\beta=-\cos(\alpha+\beta)\cos(\alpha-\beta)\end{align}$

# Preface

There are two points $O$ and $O_1$. The distance between them is $l$. And there are alse two points $A, B$
coplaned with the former two points $O, O_1$. The angles $\angle AOB$ and $\angle AO_1B$ is known.
Solve the relationship between the $A$ and $B$.

Build a polar coordinate system $OO_1$, which origin point is $O$ and the axis is along the $OO_1$.

Assume that $\angle AOB=\alpha$, $\angle AO_1B=\beta$, $\angle AOO_1B=\theta$ and the $\lVert\overline{OA}\rVert=\rho$.

So we can easy get $\angle BOO_1=\alpha+\theta$ and the $\cot\angle BO_1O=c$.

which
$$
c = \frac{l + \rho (\sin\theta \tan\beta - \cos\theta)}{\rho (sin\theta + cos\theta tan\beta) - l\tan\beta} \\

\lVert\overline{OB}\rVert=\frac{l}{\sin(\alpha + \theta) c + \cos(\alpha + \theta)}
$$

So the $A$ is at $(\rho;\theta)$ and the $B$ is at $(\lVert\overline{OB}\rVert;\alpha+\theta)$

# Spatial Polar Coordinate

## 0. Angle between two points on a spheric surface
As we known, a point is at spheric coordinate $(\psi, \varphi)$, which represent the **latitude** and the **longitude** separately.

Assume there are A and B two points at a spheric coordinate $(\psi_1, \varphi_1)$ and $(\psi_2, \varphi_2)$.  The angle $\alpha$ is between the two point.

Calculation:

$$\cos\alpha=\cos\psi_1\cos\psi_2\cos(\varphi_1-\varphi_2)+\sin\psi_1\sin\psi_2$$

or

$$\begin{align}\cos\alpha=\frac{1}{2}\Big[\cos\Delta\psi(\cos\Delta\varphi+1)+\cos\Sigma\psi(\cos\Delta\varphi-1)\Big]\end{align}$$

Which $\Delta\psi=\psi_1-\psi_2, \Sigma\psi=\psi_1+\psi_2$ and $\Delta\varphi=\varphi_1-\varphi_2$ .

## 1. A circle on the spheric surface
The equation of the specified angular radius $\alpha$ and center $(\psi_0, \varphi_0)$ is

$$\varphi=\pi+\varphi_0-\arccos\frac{\sin\psi_0\sin\psi-\cos\alpha}{\cos\psi_0\cos\psi}$$

Which $\psi\in[-\frac{\pi}{2},\frac{\pi}{2}]$ and $\varphi\in(-\pi,\pi]$

Specially, if the $\alpha=\frac{\pi}{2}$, it represnts the big circle on the sphere. The equation is $\cos(\varphi-\varphi_0)=-\tan\psi_0\tan\psi$


### A big circle crossing two points
Assume there are A and B two points at a unit spheric coordinate $(\psi_1, \varphi_1)$ $(\psi_2, \varphi_2)$.

#### The axis of the big circle crossing the two points
$$\vec{A}\times\vec{B}=\begin{pmatrix}y_1z_2-y_2z_1\\x_2z1-x_1z_2\\x_1y_2-x_2y_1\end{pmatrix}
=\begin{pmatrix}\cos\psi_1\sin\varphi_1\sin\psi_2-\cos\psi_2\sin\varphi_2\sin\psi_1\\
  \cos\psi_2\cos\varphi_2\sin\psi_1-\cos\psi_1\cos\varphi_1\sin\psi_2\\
  \cos\psi_1\cos\varphi_1\cos\psi_2\sin\varphi_2-\cos\psi_2\cos\varphi_2\cos\psi_1\sin\varphi_1\end{pmatrix}
=\begin{pmatrix}\rho\cos\psi\cos\varphi\\\rho\cos\psi\sin\varphi\\\rho\sin\psi\end{pmatrix}$$


$$\left\{\begin{array}l \tan\varphi=\begin{align}\frac{\cos\psi_2\sin\psi_1\cos\varphi_2-\cos\psi_1\sin\psi_2\cos\varphi_1}{\cos\psi_1\sin\psi_2\sin\varphi_1-\cos\psi_2\sin\psi_1\sin\varphi_2}
=\frac{(\sin\Sigma\psi-\sin\Delta\psi)\cos\varphi_2-(\sin\Sigma\psi+\sin\Delta\psi)\cos\varphi_1}{(\sin\Sigma\psi+\sin\Delta\psi)\sin\varphi_1-(\sin\Sigma\psi-\sin\Delta\psi)\sin\varphi_2}\end{align} \\

\tan\psi=-\cos(\varphi-\varphi_1)\cot\psi_1\end{array}\right.$$

##### Another way
$\cos\psi_1\cos\psi_2\sin(\varphi_2-\varphi_1)=\rho\sin\psi$

Which $\rho=|\sin\theta|$ and $\cos\theta=\cos\psi_1\cos\psi_2\cos(\varphi_1-\varphi_2)+\sin\psi_1\sin\psi_2$

$\begin{align}\sin\psi=-\frac{\cos\psi_1\cos\psi_2\sin(\varphi_1-\varphi_2)}{\sqrt{1-(\cos\psi_1\cos\psi_2\cos(\varphi_1-\varphi_2)+\sin\psi_1\sin\psi_2)^2}}\end{align}$

##### Another way

$\frac{\cos(\varphi-\varphi_1)}{\cos(\varphi-\varphi_2)}=\frac{\tan\psi_1}{\tan\psi_2}$

$\varphi=\arccos(\tan\psi_2\tan\psi)+\varphi_2=\arccos(\tan\psi_1\tan\psi)+\varphi_1$

$\tan\psi_2\tan\psi=\cos(\arccos(\tan\psi_1\tan\psi)+\Delta\varphi)$

$\tan\psi_2\tan\psi=\tan\psi_1\tan\psi\cos\Delta\varphi-\sin\arccos(\tan\psi_1\tan\psi)\sin\Delta\varphi$

$\tan\psi_2\tan\psi=\tan\psi_1\tan\psi\cos\Delta\varphi-\sqrt{1-\tan^2\psi_1\tan^2\psi}\sin\Delta\varphi$

$\sqrt{\cot^2\psi-\tan^2\psi_1}\sin\Delta\varphi=\tan\psi_1\cos\Delta\varphi-\tan\psi_2$

$$\cot^2\psi=(\tan\psi_1\cot\Delta\varphi-\tan\psi_2\csc\Delta\varphi)^2+\tan^2\psi_1$$


## 2. A straight line in the spheric coordinate

$$\frac{x-a}{x_n}=\frac{y-b}{y_n}=\frac{z-c}{z_n}$$

$$\left\{\begin{array}l x=&x_nt+a \\ y=&y_nt+b \\ z=&z_nt+c \end{array}\right.$$

which $x_n^2+y_n^2+z_n^2=1$, and assume $l=\sqrt{a^2+b^2+c^2}$, $\cos\theta=\frac{ax_n+by_n+cz_n}{l}$


Assume the A is at spheric coordinate $(\psi, \varphi, \rho)$, which represent the latitude and the longitude separately.

$$\left\{\begin{array}l x=&\rho\cos\psi\cos\varphi \\ y=&\rho\cos\psi\sin\varphi \\ z=&\rho\sin\psi \end{array}\right.$$


$$\Rightarrow\left\{\begin{array}l \psi=&\arcsin\frac{z}{\sqrt{x^2+y^2+z^2}} \\ \varphi=&\arctan\frac{y}{x} \\ \rho=&\sqrt{x^2+y^2+z^2} \end{array}\right.$$


$$\Rightarrow\left\{\begin{array}l \psi=&\arcsin\frac{z_nt+c}{\rho} \\ \varphi=&\arctan\frac{y_nt+b}{x_nt+a} \\ \rho=&\sqrt{l^2+t^2-2lt\cos\theta}=\sqrt{l^2+t^2-2(ax_n+by_n+cz_n)t} \end{array}\right.$$

The surface of the a line spining around the certain linear axis, which line crosses the axis at point$(a,b,c)$ and the angle consisted by the line and the axis is $\beta$:

$$\left\{\begin{array}l x_n(x-x(t))+y_n(y-y(t))+z_n(z-z(t))&=0\\ \sqrt{(x-x(t))^2+(y-y(t))^2+(z-z(t))^2}&=t\tan\beta \end{array}\right.$$
$$a $$

# Area of a triangle on a spheric surface

$S=A+B+C-\pi$

3D空间中任意一个 $v=(x,y,z)$ 沿着单位向量$u=(r,s,t)$ 旋转 $\theta$ 角度之后的 $v'$ 为：

$$v'=v\cos\theta+(u\cdot v)u(1-\cos\theta)+(u\times v)\sin\theta$$

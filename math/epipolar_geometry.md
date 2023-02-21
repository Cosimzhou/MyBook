Epipolar Geometry
=================


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

Assume the A is at spheric coordinate $(\varphi, \psi)$,

Distance calculation: $\sin\alpha=\cos\psi_1\cos\psi_2\cos(\varphi_1-\varphi_2)+\sin\psi_1\sin\psi_2$

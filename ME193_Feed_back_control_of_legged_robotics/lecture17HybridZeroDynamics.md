
# CUE
- Why do we introduce hybrid zero dynamics?
- compute the zero dynamics
## big picture

The dynamics for legged robotics are always underactuated.

for example:
$$
\begin{array}
    {c|c|c|c}
    robot & DoF & actuactors & dimstates \\ \hline
    3link& 3 & 2 & 6\\
    5link& 5 & 4 & 10\\
\end{array}
$$

for a system
$$
\Sigma : \left\{\begin{aligned} 
\dot{x} &= f(x)+ g(x)u  &x^{-} \not\in S\\
x^{+} &= \Delta (x^{-} ) &x^{-} \in S
 \end{aligned}\right. 
$$

when added virtual constraints(the same number of acturacters)

$$
V_C: y=h(q) = h_0(q) - h_{d} (\tau (q))
$$

We look at the remaining dynamics

$$
\Sigma_{\text{zero}} : \left\{\begin{aligned} 
\dot{z} &= f_{zero}(z)  &z^{-} \not\in S \cap Z\\
z^{+} &= \Delta (z^{-} ) &z^{-} \in S\cap Z
 \end{aligned}\right. 
$$

in the example of 3 and 5 link robot, the space $Z$ is only $2$ dim.
$$
z  = \left[\begin{array}c \eta_1 \\ \eta _{2} \\ \zeta _{1} \\ \zeta _{2}  \end{array}\right] \in R^{10}
$$
where $\eta$ is $y$ and $\dot{y}$, and $\zeta$ is the remaining space

## to compute the zero dynamics

from the same routine of virtual constraints

$$
y = h(q)\\
\dot{y} = L_{f} h(x) - \underbrace{L_{f} h(x) }_0u\\
\ddot{y} = L_{f} ^{2} h(x) + L_{g} L_{f} h(x)u
$$

Thus to keep the system met the virtual constraint when the system is in Z

$$
u = L_{f} L_{f} h(x)^{-1} \left\{-L_{f}^{2} h(x) \right\}
$$

then when we put the $u^*$ back and get
$$
\dot{x} = f(x)+ g(x)u^*(x) = f_{zero}(x) 
$$

### state transformation
**transform the dynamics**
$$
z  = \left[\begin{array}c \eta_1 \\ \eta _{2} \\ \zeta _{1} \\ \zeta _{2}  \end{array}\right] = \left[\begin{array}c y \\ \dot{y}\\ \theta \\\dot{\theta } \end{array}\right] 
= \left[\begin{array}c 
h(q)\\ L_{f} h(x)\\ \theta (q) \\ L_{f} \theta (q)
 \end{array}\right] 
$$

where the $\theta$ is the orthogornal dimension to the constraints $h(q)$

then on the $Z$ surface, the dynamics becomes
$$
\left[\begin{array}c \dot{\theta (q)} \\ \ddot{\theta (q)}  \end{array}\right] =
\left[\begin{array}c \dot{\theta (q)}  \\ L_{f} ^{2} \theta  + L_{g} L_{f} \theta u^* \end{array}\right] 
$$
**transform the impact map**

we have to make sure that the end state of the impact map is also in zero map

$$
\begin{aligned}
    &h\circ \Delta  | _{S\cap Z} = 0 & y^+= 0\\
    &L_{f} h\circ \Delta  | _{S\cap Z} = 0 & \dot{y}^+= 0\\
\end{aligned}
$$

> this has to prove for all the states in $Z$

however, if the robot is planar walking robot, the impact map is linear, then we only need to show exist one state.


$$
h\circ \Delta (q_{0}^{-} , \dot{q}_{0}^{-} ) = 0 \qquad 
L_{f} h\circ \Delta (q_{0}^{-} , \dot{q}_{0}^{-} ) = 0
$$

> this comes after linearity

Then we can study the stability of the reduced poincare map
$$
\mathcal{P}: S\cap Z\rightarrow S\cap Z
$$
and we want 
$$
\left|Re\left\{\lambda _{i} (\frac{\partial p }{\partial z }|_{z = z^*}) \right\}\right| <1
$$

> II TODO: what is the difference of this(calculate $u^*$ and put it back) with directly find the subspace $h(q)$ and $\theta (q)$?\
> why do we have to calculate $u^*$?

> What if the constraint $h(q)$ is not only function of $q$ but also $h(q,\dot{q})$, how much influence will this change affect the whole derivation

> What if the constraint is inequality constraint that only needs the state in a certain space? Can we build a system that supports both standing still and walk when a force applied on it? That is, when there is a large force that makes the robot about to move, the robot's leg begins to lift as the inequality constraint is now active


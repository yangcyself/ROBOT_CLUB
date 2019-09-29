# CUE
-  如何坐标转换
-  
# Kinematic Chains

### model assumptions
- robots are modeled as connections of rigid links thourgh revolte joints
- each joint is assumed to be *ideal*: rigid and frictionless
- links are implicitly assumed *noninterfering*
  - individual links can be arbitrary positions and orientations without contacting one another

## kinematic chain
- *open* if doesnot contain any loops
- *closed* contains loops
  - 一个chian， 两端固定也叫loop
- **serial chain & tree structure**
- *pivot*: revolute joint that has a fixed postion
- *pinned* a kinematic chain exactly one link is connecteed to a pivot
- *freely evolving* if no point on a kineamtic chain is constrained with respect to the inertial frame.


# Kinetic and Potential Energy of a single link

The kinetic and potential energies of a **collection** of N-links are formed from the sums of the knietic and potential energies **of each individual** ink

**coordinate frame** Typically, measurements are made relative to a joint or to a link end.

with respect to the link coordinate frame, a point will be denoted by $\left(\ell^{\mathrm{h}} ; \ell^{\mathrm{v}}\right)$

Let $p_{i}=\left(p_{i}^{\mathrm{h}} ; p_{i}^{\mathrm{v}}\right) \in \mathbb{R}^{2}$ denote the Cartesian position of the origin of the coordinate frame of link-i, to a fixed coordinate frame *world frame* or *inertial frame*

坐标转换
>注意，这里面用$h,v$来表示空间中两个维度的坐标
$$
\left[\begin{array}{c}{\overline{p}_{i}^{\mathrm{h}}} \\ {\overline{p}_{i}^{\mathrm{v}}}\end{array}\right]=\left[\begin{array}{c}{p_{i}^{\mathrm{h}}} \\ {p_{i}^{\mathrm{v}}}\end{array}\right]+\mathbf{R}\left(\theta_{i}^{\mathrm{abs}}\right)\left[\begin{array}{c}{\overline{\ell}_{i}^{\mathrm{h}}} \\ {\overline{\ell}_{i}^{\mathrm{v}}}\end{array}\right]，
$$

where
$$
\mathbf{R}\left(\theta_{i}^{\mathrm{abs}}\right) :=\left[\begin{array}{cc}{\cos \left(\theta_{i}^{\mathrm{abs}}\right)} & {-\sin \left(\theta_{i}^{\mathrm{abs}}\right)} \\ {\sin \left(\theta_{i}^{\mathrm{abs}}\right)} & {\cos \left(\theta_{i}^{\mathrm{abs}}\right)}\end{array}\right]
$$


And the velocity

$$
\left[\begin{array}{c}{\dot{p}_{i}^{\mathrm{h}}} \\ {\dot{\overline{p}}_{i}^{v}}\end{array}\right]=\left[\begin{array}{c}{\dot{p}_{i}^{\mathrm{h}}} \\ {\dot{p}_{i}^{\mathrm{v}}}\end{array}\right]+\left[\begin{array}{cc}{0} & {-1} \\ {1} & {0}\end{array}\right] \mathbf{R}\left(\theta_{i}^{\mathrm{abs}}\right)\left[\begin{array}{c}{\ell_{i}^{\mathrm{h}}} \\ {\overline{\ell}_{i}^{\mathrm{v}}}\end{array}\right] \dot{\theta}_{i}^{\mathrm{abs}}
$$

## determine potential energy and kinetic energy

we use the position and velocity of the center of Mass to determine the potential and kinetic energy

The Potential of gravity
$$
V_{i}=m_{i} g_{0} p_{\mathrm{cm}, i}^{\mathrm{v}}
$$
The kinetic energy:
$$
K_{i}=\frac{1}{2} m_{i}\left(\left(\dot{p}_{\mathrm{cm}, i}^{\mathrm{h}}\right)^{2}+\left(\dot{p}_{\mathrm{cm}, i}^{\mathrm{v}}\right)^{2}\right)+\frac{1}{2} J_{\mathrm{cm}, i}\left(\dot{\theta}_{i}^{\mathrm{abs}}\right)^{2}
$$

it can be also write with the global coordinate system
$$
\begin{aligned} K_{i}=\frac{1}{2} m_{i}\left(\left(\dot{p}_{i}^{\mathrm{h}}\right)^{2}+\left(\dot{p}_{i}^{\mathrm{v}}\right)^{2}\right)+& \frac{1}{2} J_{i}\left(\dot{\theta}_{i}^{\mathrm{abs}}\right)^{2} \\ &+m_{i}\left[\begin{array}{c}{\dot{p}_{i}^{\mathrm{v}}} \\ {-\dot{p}_{i}^{\mathrm{h}}}\end{array}\right]^{\prime} \mathbf{R}\left(\theta_{i}^{\mathrm{abs}}\right)\left[\begin{array}{c}{\ell_{\mathrm{cm}, i}^{\mathrm{h}}} \\ {\ell_{\mathrm{cm}, i}^{\mathrm{v}}}\end{array}\right] \dot{\theta}_{i}^{\mathrm{abs}} \end{aligned}
$$

this is because of the parallel axis theorem
$$
J_{i}=J_{\mathrm{cm}, i}+m_{i}\left(\left(\ell_{\mathrm{cm}, i}^{\mathrm{h}}\right)^{2}+\left(\ell_{\mathrm{cm}, i}^{\mathrm{v}}\right)^{2}\right)
$$
>moment of inertia: 惯性矩

**Thus the kinetic energy of a free link can be written as**

$$
K_{i}=\frac{1}{2}\left[\begin{array}{c}{\dot{\theta}_{i}^{\mathrm{abs}}} \\ {\dot{p}_{\mathrm{Cm}, i}^{\mathrm{h}}} \\ {\dot{p}_{\mathrm{cm}, i}^{\mathrm{v}}}\end{array}\right]^{\prime}\left[\begin{array}{ccc}{J_{\mathrm{cm}, i}} & {0} & {0} \\ {0} & {m_{i}} & {0} \\ {0} & {0} & {m_{i}}\end{array}\right]\left[\begin{array}{c}{\dot{\theta}_{i}^{\mathrm{abs}}} \\ {\dot{p}_{\mathrm{cm}, i}^{\mathrm{h}}} \\ {\dot{p}_{\mathrm{cm}, i}^{\mathrm{v}}}\end{array}\right]
$$

OR:
$$
K_{i}=\frac{1}{2}\left[\begin{array}{c}{\dot{\theta}_{i}^{\mathrm{abs}}} \\ {\dot{p}_{i}^{\mathrm{h}}} \\ {\dot{p}_{i}^{\mathrm{v}}}\end{array}\right]^{\prime}\left[\begin{array}{ccc}{J_{i}} & {d_{12}} & {d_{13}} \\ {d_{12}} & {m_{i}} & {0} \\ {d_{13}} & {0} & {m_{i}}\end{array}\right]\left[\begin{array}{c}{\dot{\theta}_{i}^{\mathrm{abs}}} \\ {\dot{p}_{i}^{\mathrm{h}}} \\ {\dot{p}_{i}^{\mathrm{v}}}\end{array}\right]
$$

where
$$
\begin{aligned} d_{12} &=-\frac{m_{i}}{2}\left(\ell_{\mathrm{cm}, i}^{\mathrm{h}} \sin \left(\theta_{i}^{\mathrm{abs}}\right)+\ell_{\mathrm{cm}, i}^{\mathrm{v}} \cos \left(\theta_{i}^{\mathrm{abs}}\right)\right) \\ d_{13} &=-\frac{m_{i}}{2}\left(\ell_{\mathrm{cm}, i}^{\mathrm{v}} \sin \left(\theta_{i}^{\mathrm{abs}}\right)-\ell_{\mathrm{cm}, i}^{\mathrm{h}} \cos \left(\theta_{i}^{\mathrm{abs}}\right)\right) \end{aligned}
$$

**generalized coordinates:** when the configurations and velocities can be parameterized with fewer coordinates

# 4.3 Free Open Kinematic Chains

consider a free N-link open chain(虽然叫做一个chain但是可以是树的样子), number the joints from one to $N-1$

denote $a(j)$ and $b(j)$ as the two links connected by the j-th joint. The position of joint-j on link a(j) by $(l_{a(j),j}^h;l_{a(j),j}^v)$. joint constraints are $2(N-1)$ equations.

$$
\left[\begin{array}{c}{p_{a(j)}^{\mathrm{h}}} \\ {p_{a(j)}^{\mathrm{v}}}\end{array}\right]+\mathbf{R}\left(\theta_{a j j}^{\mathrm{abs}}\right)\left[\begin{array}{l}{\ell_{a(j), j}^{\mathrm{h}}} \\ {\ell_{a(j), j}^{v}}\end{array}\right]-\left[\begin{array}{c}{p_{b(j)}^{\mathrm{h}}} \\ {p_{b(j)}^{\mathrm{v}}}\end{array}\right]-\mathbf{R}\left(\theta_{b(j)}^{\mathrm{abs}}\right)\left[\begin{array}{c}{\ell_{b(j), j}^{\mathrm{h}}} \\ {\ell_{b(j), j}^{v}}\end{array}\right]=\left[\begin{array}{l}{0} \\ {0}\end{array}\right]
$$

for $j = 1, ..., N-1$


### express the set of all solutions
First, the set of equations iis always **consistent** (有解)

for any $i_0\in \{1,...N\}$ the solutions can be written in the form
$$
\left[\begin{array}{c}{p_{i}^{\mathrm{h}}} \\ {p_{i}^{\mathrm{v}}}\end{array}\right]=\left[\begin{array}{c}{p_{i_{0}}^{\mathrm{h}}} \\ {p_{i_{0}}^{\mathrm{v}}}\end{array}\right]+\left[\begin{array}{c}{\check{\Upsilon}_{i_{0}, i}^{\mathrm{h}}\left(\theta_{1}^{\mathrm{abs}}, \ldots, \theta_{N}^{\mathrm{abs}}\right)} \\ {\tilde{\Upsilon}_{i_{0}, i}^{\mathrm{h}}\left(\theta_{1}^{\mathrm{abs}}, \ldots, \theta_{N}^{\mathrm{abs}}\right)}\end{array}\right]
$$


也就是固定一个点的坐标，其它所有的点的(x,y)坐标可以通过这个坐标加上角度的变换得到。

$\check{\Upsilon}_{i_{0}, i}^{\mathrm{h}}\left(\theta_{1}^{\mathrm{abs}}, \ldots, \theta_{N}^{\mathrm{abs}}\right)$ 这个玩意说是仿射矩阵。

## Gerneralized coordinates
Gerneralized coordinates 就是可以唯一确定这个状态的一组变量。对于一个free chain'而言，一共有$N+2$个自由度

## kinetic and potential energy
given generalized coordinates $q_{\mathrm{f}}=\left(q_{1} ; \ldots ; q_{N+2}\right)$, we can express all the cooridnates with it.
$$
\left[\begin{array}{c}{\theta_{i}^{\mathrm{abs}}} \\ {p_{i}^{\mathrm{h}}} \\ {p_{i}^{\mathrm{v}}}\end{array}\right]=\left[\begin{array}{c}{\theta_{i}^{\mathrm{abs}}\left(q_{\mathrm{f}}\right)} \\ {p_{i}^{\mathrm{h}}\left(q_{\mathrm{f}}\right)} \\ {p_{i}^{\mathrm{v}}\left(q_{\mathrm{f}}\right)}\end{array}\right]
$$

$$
\left[\begin{array}{c}{\dot{\theta}_{i}^{\mathrm{abs}}\left(q_{\mathrm{f}}, \dot{q}_{\mathrm{f}}\right)} \\ {\dot{p}_{i}^{\mathrm{h}}\left(q_{\mathrm{f}}, \dot{q}_{\mathrm{f}}\right)} \\ {\dot{p}_{i}^{\mathrm{v}}\left(q_{\mathrm{f}}, \dot{q}_{\mathrm{f}}\right)}\end{array}\right]=\left(\frac{\partial}{\partial q_{\mathrm{f}}}\left[\begin{array}{c}{\theta_{i}^{\mathrm{abs}}\left(q_{\mathrm{f}}\right)} \\ {p_{i}^{\mathrm{h}}\left(q_{\mathrm{f}}\right)} \\ {p_{i}^{\mathrm{v}}\left(q_{\mathrm{f}}\right)}\end{array}\right]\right) \dot{q}_{\mathrm{f}}
$$

其中上面打个点是时间的导数的意思

For later use, we Note
$$
\frac{\partial}{\partial \dot{q}_{i}}\left[\begin{array}{c}{\dot{\theta}_{i}^{\mathrm{abs}}\left(q_{\mathrm{f}}, \dot{q}_{\mathrm{f}}\right)} \\ {\dot{p}_{i}^{\mathrm{h}}\left(q_{\mathrm{f}}, \dot{q}_{\mathrm{f}}\right)} \\ {\dot{p}_{i}^{\mathrm{v}}\left(q_{\mathrm{f}}, \dot{q}_{\mathrm{f}}\right)}\end{array}\right]=\frac{\partial}{\partial q_{i}}\left[\begin{array}{c}{\theta_{i}^{\mathrm{abs}}\left(q_{\mathrm{f}}\right)} \\ {p_{i}^{\mathrm{h}}\left(q_{\mathrm{f}}\right)} \\ {p_{i}^{\mathrm{v}}\left(q_{\mathrm{f}}\right)}\end{array}\right]
$$

>这个也好理解（虽然我不知道怎么严谨地表示出来），就是空间上面的变化关系，同时在时间上面求导，可以得到同样的关系。（想象一个杠杆）

>注意这里面一个导数理解成一个雅可比矩阵

**The gravity potential energy**
$$
V_{i}\left(q_{\mathrm{f}}\right)=m_{i} g_{0} p_{\mathrm{cm}, i}^{\mathrm{v}}\left(q_{\mathrm{f}}\right)
$$
the kinetic energy
$$
{K_{i}\left(q_{\mathrm{f}}, \dot{q}_{\mathrm{f}}\right)=\frac{1}{2} m_{i}\left(\left(\dot{p}_{\mathrm{cm}, i}^{\mathrm{h}}\left(q_{\mathrm{f}}, \dot{q}_{\mathrm{f}}\right)\right)^{2}+\left(\dot{p}_{\mathrm{cm}, i}^{\mathrm{v}}\left(q_{\mathrm{f}}, \dot{q}_{\mathrm{f}}\right)\right)^{2}\right)}  {+\frac{1}{2} J_{\mathrm{cm}, i}\left(\dot{\theta}_{i}^{\mathrm{abs}}\left(q_{\mathrm{f}}, \dot{q}_{\mathrm{f}}\right)\right)^{2}}
$$

Thus,
$$
K_{i}=\frac{1}{2} \dot{q}_{\mathrm{f}}^{\prime}\left[m_{i}\left(\frac{\partial p_{\mathrm{cm}, i}}{\partial q_{\mathrm{f}}}\right)^{\prime}\left(\frac{\partial p_{\mathrm{cm}, i}}{\partial q_{\mathrm{f}}}\right)+J_{\mathrm{cm}, i}\left(\frac{\partial \theta_{i}^{\mathrm{abs}}}{\partial q_{\mathrm{f}}}\right)^{\prime}\left(\frac{\partial \theta_{i}^{\mathrm{abs}}}{\partial q_{\mathrm{f}}}\right)\right] \dot{q}_{\mathrm{f}}
$$
>这里面'是转置的意思


total kinetic energy 可以表示为
$$
K_{\mathrm{f}}\left(q_{\mathrm{f}}, \dot{q}_{\mathrm{f}}\right)=: \frac{1}{2} \dot{q}_{\mathrm{f}}^{\prime} D_{\mathrm{f}}\left(q_{\mathrm{f}}\right) \dot{q}_{\mathrm{f}}
$$

## For pinned open kinematic chains
只用换成一共N个自由度就可以了


# Lagrangian and Lagrange's Equations

let $q = (q...)$ set of generalized coordinates

**Lagrangian**:
$$
\mathcal{L}(q, \dot{q}) :=K(q, \dot{q})-V(q)
$$

**Lagrange's equation**
$$
\frac{d}{d t} \frac{\partial \mathcal{L}}{\partial \dot{q}}-\frac{\partial \mathcal{L}}{\partial q}=\Gamma
$$

其中$K(q,\dot{q})$是$K(q, \dot{q})=\frac{1}{2} \dot{q}^{\prime} D(q) \dot{q}$

求导之后就得到

$$
D(q) \ddot{q}+C(q, \dot{q}) \dot{q}+G(q)=\Gamma
$$

其中
$$
C(q, \dot{q}) \dot{q}=\left(\frac{\partial}{\partial q}(D(q) \dot{q})\right) \dot{q}-\frac{1}{2}\left(\frac{\partial}{\partial q}(D(q) \dot{q})\right)^{\prime} \dot{q}
$$
>这里就看不懂了
The matrix function $C$ is not uniquely defined, but it is traditional to choose 
$$
C_{k j}=\sum_{i=1}^{\overline{N}} \frac{1}{2}\left(\frac{\partial D_{k j}}{\partial q_{i}}+\frac{\partial D_{k i}}{\partial q_{j}}-\frac{\partial D_{i j}}{\partial q_{k}}\right) \dot{q}_{i}
$$

# Generalized Forces and Torques
**The *principle* of virtual work**

- Force acting at a point
  - $\Gamma_{i}=\left(\frac{\partial p_{i}}{\partial q}\right)^{\prime} F$
  - where the force $F = (F_T; F_N)$ (这俩啥意思还未知)
  - act on point $p_i = (p_i^h;p_i^v)$
- Torque acting on a single link
  - $\Gamma_{i}=\left(\frac{\partial \theta_{i}^{\mathrm{abs}}}{\partial q}\right)^{\prime} \tau$
  - where $\theta_i^{abs}$ is the absolute orientation of the link
- Torque acting at a revolute connection of two links
  - $\Gamma_{j}=\left(\frac{\partial \theta_{j}^{\mathrm{rel}}}{\partial q}\right)^{\prime}$
  -  where $\theta_j^{rel}$ is the joint relative angle.


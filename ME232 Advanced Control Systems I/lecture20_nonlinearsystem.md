# CUE
- What is the PBH test and prove it
- For the system with controller and observer, derive the A_closeloop
- And show the separation principle from the A_closeloop
- for the example \ddot{y} =  uy - y^{2} - \cos (y), use input redefinition box to change it to a "linear system"
- What is the limitition of this method, what if our system have dot{y}?
- What is the jacobian linearization method?
# recap


$$
\Sigma : ABCD
$$

add state feed back

$$
(A+BL)BC0
$$

if $\Sigma$ controllable, then $\text{spec}(A+BL)$ can be assigned arbitrarilly

if not controllable, only the controllable part ....

$\Sigma$ stabilizable if $\exist L$: $A+BL$ is stable

**PBH test**: 
The pair (A, B) is
- **Stabilizable** if and only if rank $\left[\begin{array}c \lambda I − A &B \end{array}\right]  = n$ for all λ ∈ $C^{+}$
- **Controllable** if and only if rank $\left[\begin{array}c \lambda I − A &B \end{array}\right]  = n$ for all λ ∈ $C$


## proof

$\Leftarrow$

Suppose $\text{rk}[SI-A|B]=n \forall s\in C$

suppose $s$ is not an eigenvalue of $A$, then $SI-A$ is invertable

so we only care about the $s \in \text{spec}(A)$

suppose not stablizable

do kalman decomposition

$A_{22}$ is no stable

we can find 
$$
A_{22}v = \lambda v \qquad v \neq 0 \qquad \lambda : \text{unstable}
$$

if $A_{22}$ is stable $A_{22} ^{*}$ is unstable, 

consider 
$$
\left[\begin{array}c 0 & v^{*}  \end{array}\right]  \left[\begin{array}c \lambda I - A_{11} & - A_{12} & B_{1} \\ 0 &\lambda I-A_{22}& 0  \end{array}\right]  = \left[\begin{array}c 0 & 0 & 0 \end{array}\right] 
$$

thus we have contradiction

example:

$$
A = \left[\begin{array}c 1 & 0 & 0 \\ 0 & 2 & -1 \\ 0 & -1 &2 \end{array}\right] 
$$

if the left upper corner is $-1$ and $1$, the rank is $3$ and $2$. thus is stable and unstable
> ?? Why the sign of the value decides the rank?

## observer and controller

$$
G(s) = \left[\begin{array}{c|c} A+BL+KC &-K \\ \hline L & 0\end{array}\right] 
$$

How do you do the controller for the plant?
1. ABCD
2. L (put poles according to your design stable time)
3. K (put poles 5 time of L)
4. put together

## analysis

suppose no modeling errors

$$
\dot{\hat{x}} = (A+KC+BL)\hat{x} + Bv - Ky
\\
u = L\hat{x} + v
$$

$$
\dot{\left[\begin{array}c x \\ \hat{x} \end{array}\right] } = 
\underbrace{\left[\begin{array}c 
A & BL \\ -KC & A+BL+KC
 \end{array}\right] 
}_{A_{Close loop}}
\left[\begin{array}c x \\ \hat{x} \end{array}\right]+
\left[\begin{array}c 0 \\ K \end{array}\right] r
$$


we want to analysis the eigen values of $A$ close loop $A_{cl}$

let 
$$
T= \left[\begin{array}c I & 0 \\ I & I \end{array}\right]
$$

then 
$$
T^{-1} A_{cl} T = \left[\begin{array}c I & 0 \\ -I & I \end{array}\right] 
\left[\begin{array}c 
A & BL \\ -KC & A+BL+KC
 \end{array}\right] 
 \left[\begin{array}c I & 0 \\ I & I \end{array}\right]\\
 = \left[\begin{array}c A+BL & BL \\ 0 & A+KC \end{array}\right] 
$$

So the closed loop eigenvalues are observer poles $\text{spec}(A+KC)$ union feedback poles $\text{spec}(A+BL)$. 

this is called **separation principle**, if I want to optimize $L$ and $K$, we can do this separately

> Note that this is in the assumption that we have no modeling errors

## nonlinear systems 
> you will learn more on this in $ME237$

example

$$
\ddot{y}+\cos(\dot{y})+ y^{2}  = uy
$$

Write this in state space.

$$
\dot{x_{1} } = x_{2} \\
\dot{x}_{2}  = - x_{1}^{2} -\cos (x_{2} ) + x_{1} u\\
y = x_{1} 
$$

The more general form
$$
\dot{x}_{1} =   f_{1} (x_{1},x_{2},\dots,x_{n},u_{1},u_{2},\dots,u_{n})\\
\dot{x}_{2} =   f_{2} (x_{1},x_{2},\dots,x_{n},u_{1},u_{2},\dots,u_{n})\\
\dots\\
y_{1} = g_{1}(\dots) 
$$

We put it in compact form
$$
\dot{x} = f(x,u)\\
y = g(x,u)
$$

we can evaluate this function at a fixed point, and get a matrix



Note that $f$ is a vectorized function, multi-in multi out

> How to choose the state is beyond the scope of this class, like lie derivative

> this choice of state space will not work if $\dot{u}y$ in this example

## back to the example

$$
\ddot{y} =  uy - y^{2} - \cos (y)
$$

we let the $uy - y^{2} - \cos (y) = v$ (new input)

then 
$$
u  = \frac{v+ y^{2} + \cos (y) }{y}
$$

So the box between $v$ and $u$ it is Input redefinition box

look at the whole $\ddot{y} = v$

> if like the old example we have $\dot{y}$, then the IRB needs a input $\dot{y}$, when we need an observer\
> Experences shown Feedback linearization fails if you use an observer for $\dot{y}$\
> if you take derivative directly, it is very noisy


This is called **Feedback Linearization**

> Note that we need a very good non-linear model to make it work. (Otherwise we can not design IRB)\
> It works well in space because no winds and other stuff

# Another method: jacobian linearization


example

$$
f(x_{1} ,   x_{2} ) = x_{1}^{2} + \cos (x_{2} )x_{1} 
$$


$$
\nabla f = \left[\begin{array}c \frac{\partial f_1 }{\partial x_1 } & \frac{\partial f_1 }{\partial x_2 }\\
\frac{\partial f_2 }{\partial x_1 } & \frac{\partial f_2 }{\partial x_2 } \end{array}\right] 
$$

we can evaluate this function at a point, and get a matrix

## equilibrium point

### example:
磁悬浮

$$
m\ddot{y} = mg - \frac{cu^2}{y^2}
$$

the equilibrium point $(x^{0} ,u^{0} ,y^{0} )$

**defn:** if the plant is in state $x(0) = x^{0}$ and apply constant input $u(t) = u^{0}$, then the output $y(t) = y^{0}$ constantly
# CUE
- the lagrangian Dynamics


I attended this lecture without any preparation, this is only what I got

## overall idea
we want an differential equation, in this way, we can do the simulation and analysis

## The lagrangian Dynamics
The lagrangian Dynamics Deduces to :
$$
D(a) \ddot{q} + C(q,\dot{q})\dot{q} + C_n(q) = B(q)u
$$

where D is mass imentia matrix R(n*n) an positive definitive matrix

C is the coricllis matrix R(n*n)

B is the gravity vector, general: input mapping matrix 

## add constraints 
The constraint can be expressed as $\gamma(q)\equiv0$

we assume a constraint Toque $\mathcal{T}$

the function becomes
$$
D(q)\ddot{q} C(q,\dot{q})\dot{q} +G(q) = Bu + \left( \frac{\partial\dot{\partial(q)} }{\partial q} \right) ^T \mathcal{T}_C
$$

what is the unknown?

$\mathcal{T}_C$ and $\ddot{q}$

## form the formulation
The first constraint is the lagrange function

the second constraint is $\gamma\equiv0$, thus the $\frac{dd\gamma}{dt^2} =0$

我们使用二阶导是因为这里面有$\ddot{q}$

### get the $\ddot{\gamma}$

$$
\dot{\gamma } = \frac{d\gamma(q)}{dx} \dot{q}
$$
dot again,
$$
\ddot{\gamma} = \frac{\partial J(q) }{\partial q }\dot{q} + J(q)\ddot{q}
$$


This can be represented as a matrix
$$
\left[\begin{array}c D(q) & -J^T(q) \\
J(q) & 0
 \end{array}\right] 
\left[\begin{array}c \ddot{q}\\\lambda  \end{array}\right]  = 
\left[\begin{array}c Bu = c \dot{q} -G \\ - \dot{J} \dot{q} \end{array}\right] 
$$


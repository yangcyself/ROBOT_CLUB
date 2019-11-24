# CUE
- the joint space and task space dynamics are 
  - $A(q)\ddot{q}+b(q,\dot{q})\dot{q}+g(q) = \Gamma$
  - $\Lambda \ddot{x} + \mu + p = F$
- How is the $\Lambda$ defined?
- How is the $\bar{J}$ defined?
- what is the relationship between $\bar{J}$ and $J$
- if we want to control in the task space so that $\ddot{e} = -K_p e - K_d \dot{e}$, what $F$ should be?
- How do we add other subtasks?
## review:


joint space dynamics
$$
A(q)\ddot{q}+b(q,\dot{q})\dot{q}+g(q) = \Gamma 
$$

task space dynamics
$$
\Lambda \ddot{x} + \mu + p = F
$$



$$
\Lambda  = (JA^{-1}J^T)^{-1}
$$
the gneeralizaed inv of J
$$
\bar{J} = A^{-1}J^T\Lambda 
$$

and 
$$
\bar{J}^T \Gamma = F \quad \Gamma =\bar{J}^TF
$$


## control in task space

**Goal:** $x\rightarrow x^{\text{des}}(t)$

design $f$ $\quad \text{s.t.}\quad x$  approach $x^{\text{des}}$

from 
$$
\Lambda \ddot{x} + \mu + p = F
$$

we can let 
$$
\begin{aligned}
    \ddot{e} &= -K_p e - K_d \dot{e} \\
    &= \Lambda ^{-1}\left[ F - \mu - p \right] - \ddot{x^{\text{des}}}
\end{aligned}

$$

thus 
$$
F = \mu + p + \Lambda (-K_pe - K_d \dot{e} - \ddot{x}^{\text{des}})
$$


> why don't we use Lie-direvitives here?\
> II I think they just different in the parital thing
> > I think The $L_{f} y = \dot{x}$ because $\frac{\partial e }{\partial x }=1$, but now I don't know how to compute $\frac{\partial \dot{x} }{\partial x }$ I don't think this is 1

## How do we do subtasks?

**remember** the solution of $Ax = y$ is 
$$
x = Gy + (I - GA)x
$$

So the general force to control the robot is 
$$
\tau  = \bar{J}\dot{x}+ \underbrace{(I-\bar{J}J)}_N\dot{q}
$$

thus 
$$
\Gamma  = J^T F + N^T \Gamma _\text{null}
$$

So the robot will do the first task is possible, and if $\Gamma _\text{null} \notin \mathcal{N}(N)$ it will do other tasks.

> read the paper about the whole body control\
> Sentis, Luis, and Oussama Khatib. "Synthesis of whole-body behaviors through hierarchical control of behavioral primitives." International Journal of Humanoid Robotics2.04 (2005): 505-518.
# CUE
- what is the difference between Templates and Anchors
- list the four different conditions and say what is
  - generalized inverse
  - reflexive generalized inverse
  - pseudoinverse
- What is the condition for Ax = y to have solution?
- F is applied at x, how to compute Gamma?(force to generalized coordinates) 
- derive tasks space dynamcis from the generalized dynamics
- 
# Templates & Anchors

我的感觉这就是一些简化模型的方法论

## templates
- synergy
  - the actuators that work together
- symmetry

### **examples**
- IP
- SLIP (spring loaded inverted pendulum)
- LLS (Lateral leg spring)

## Anchors
anchors are more elaborate and representative than templates

## connecting back to Template and Anchors 

- Observation from neural commands 
- Data to derive Kinematic Relations
- Kinematic Relations to define Anchors
- Force-Platforms help define Templates

# Operational space control

>A tool that enables you to find a way to do other things while you are doing some main tasks

比如, 一个机械臂，我的task1是控制它的端点沿着什么轨迹走，但是机械臂的自由度有冗余，所以我还可以再加别的task

# Math
The dynamics for the whole robot
$$
D\ddot{q}+C\dot{q}+G = \Gamma 
$$
use the notations in paper, is 
$$
A\ddot{q}+b+g = \Gamma 
$$

and we want to get **Task space dynamics**
$$
\Lambda \ddot{x} + \mu + p = F
$$

> thus the subtasks that you can do along this is related in the null space of the dynamics

## Generalized Inverse

**Defn:** If A is a $n\times n$ matrix, then $G$ is generalized inverse of A if G satisfies.
$$
AGA = A
$$

- Pesudo inverse is one example of generalized inverse
- if A invertable then $G  = A^{-1}$
- or G exists but not unique

### **addition knowledge from [WIKI](https://en.wikipedia.org/wiki/Generalized_inverse)**
As for the different conditions for the inverse
1. $AA^gA = A$
2. $A^gAA^g = A^g$
3. $(AA^g)^* = AA^g$
4. $(A^gA)^* = A^gA$

- Satisfies first: **generalized inverse**
- Satisfies 1,2 **reflexive generalized inverse**
- Satisfies all **pseudoinverse**

### **thm**
for a fixed $y\in \mathbb{R}^n$
1. $Ax = y$ has a solution iff $A\underbrace{Gy}_x = y$
2. There exists a solution iff $x = Gy + \underbrace{(I - GA)}_{\mathcal{N}\text{projection}}z \quad z\in \mathbb{R}^n$

> 俺: From the defn of [Projection matrix](../ME232&#32;Advanced&#32;Control&#32;Systems&#32;I/[Read]Generalized_eigenspaces.md), We can show that $GAGA = GA$, thus $GA$ is indeed a projection matrix, and thus $I- GA$ is the other projection matrix


## Joint space dynamics
From 
$$
A(q)\ddot{q}+b(q,\dot{q})\dot{q}+g(q) = \Gamma 
$$
task $x: \quad x = P_{ef}(q)$
>ef stands for end effector

we compute 
$$
\dot{x} = J \dot{q}\\
\ddot{x} = J\ddot{q}+ \dot{J}\dot{q}
$$

if $F$ is applied at $x$, then $\Gamma = J^T F$

> we can get $J^T$ using virtual walk

Thus we have:

$$
\begin{aligned}
    \ddot{x} &= JA^{-1}\left[ \Gamma  -b-g \right] + \dot{J}\dot{q}\\
    &= JA^{-1}J^{T}F - JA^{-1}b - JA^{-1}g + \dot{J}\dot{q}
\end{aligned}
$$

multiply by $\left( JA^{-1}J \right)^{-1}$
> Note, this is invertable, but why?

$$
\left( JA^{-1}J \right)^{-1} \ddot{x} = F - \left( JA^{-1}J \right)^{-1} JA^{-1}b -  \left( JA^{-1}J \right)^{-1} JA^{-1}g + \left( JA^{-1}J \right)^{-1} \dot{J}\dot{q}
$$
denote $\left( JA^{-1}J \right)^{-1}$ as $\Lambda$

$$
\Lambda \ddot{x} = F - \Lambda JA^{-1}b - \Lambda JA^{-1}g + \Lambda \dot{J}\dot{q}
$$

we define $\Lambda JA^{-1}$ as $\bar{J}^T$ and get

$$
\Lambda \ddot{x} = F - \bar{J}^T b - \bar{J}^T g + \Lambda \dot{J}\dot{q}
$$
move terms
$$
\Lambda \ddot{x} + \underbrace{\bar{J}^T b - \Lambda \dot{J}\dot{q}}_\mu + \underbrace{\bar{J}^T g}_p = F  
$$

Thus, this is the task space dynamics

### **Claim** $\bar{J} = A^{-1}J^T\Lambda$

Note that $A$, $\Lambda$ are mass matrix so they are all symmetric

### **Claim** $\bar{J}$ is generalized inverse of $J$

Check 
$$
J \bar{J} J = \underbrace{J A^{-1}J^T}_{\Lambda^{-1}} \Lambda  J = J
$$

### **Claim** $F = \bar{J}^T\Gamma$
This is because
$$
\begin{aligned}
    \bar{J}^T\Gamma &= \bar{J}^T\left[ A\ddot{q}+b+g \right] \\
    &= \Lambda J\ddot{q}+ \bar{J}^Tb+ \bar{J}^Tg\\
    &= \Lambda (J\ddot{q}+\dot{J}\dot{q})+ \bar{J}^Tb - \Lambda  \dot{J}\dot{q}+ \bar{J}^Tg\\
    &= \Gamma \ddot{x} + \mu +p\\
    &= F
\end{aligned}
$$

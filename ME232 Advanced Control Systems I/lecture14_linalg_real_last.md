# CUE
- what special attention is needed when I prove some property about spectral and hermitian
- A block matrix AB0D, B neq 0, when will be this matrix be p.s.d.
- derive schur theorem
  - prove that the transition matrix $T$ in the derivation is unitary
- what does the 'ordinary' mean in LTI ODE
- what is the defn of equivalent of realizations?
- derive the expansion of (sI-A)^{-1} 
- what is Markov parameters and how are they related to the expansion?
- Given a system ABCD, what is the form of its similar realization?
  - show that they are equivalent
  - find the new basis of the state of the similar realization
- what is the defn of the controllability?
- Show the mapping relationship between init state $\xi$ and the input function
- Explain that this mapping($\mathcal{L}$) is an operator and whose range is a subspace.
- what is grammian and what is controllability grammian?
  - how can this judge the controllablity?
- what is the matrix to judge the controllability?
- how to use the matrix [A-lambdaI, B] matrix to judge controllability?

## Proof about Hermitian and spectral needs attension
example prove 
$$
p \succ 0 \Leftrightarrow T^*PT \succ 0
$$

pf $\Rightarrow$

$$
P = P^*, v^*PV\succ 0\quad \forall v \neq 0
$$

**NOTE THE $\neq  0$**, and **NOTE to PROVE HERMITIAN**

$$
(T^*PT)^* = T^*PT
$$
then every thing clear


## example,
a block matrix 
$$
\left[\begin{array}c  A&X \\ 0& B \end{array}\right] \quad X\neq 0 
$$
when will this be p.s.d.?

**ans** NO, it is not hermitian
## Schur complement

$$
\left[\begin{array}c P & X \\X^* & Q \end{array}\right] \quad P,Q \text{ square}
$$

$$
M \succ 0 \Leftrightarrow  Q\succ 0 \land P-XQ^{-1}X^*\succ 0
$$


for example:
$$
\left[\begin{array}c 8 & 1& 2 \\ 1 & 1 & 0\\ 2 &0 &1 \end{array}\right] 
$$
divide it into 
$$
\left[\begin{array}{c|cc} 8 & 1& 2 \\ \hline 1 & 1 & 0\\ 2 &0 &1 \end{array}\right] 
$$

another example

> see last time's $\left\|x \right\| ^2$


### Proof of schur throrem

$$
\left[\begin{array}c I  & -XQ^{-1} \\ 0 & I \end{array}\right]
\left[\begin{array}c P & X \\X^*& Q \end{array}\right] 
\left[\begin{array}c I  & 0 \\ -Q^{-1}X  & I \end{array}\right]
\\
= \left[\begin{array}c P - XQ^{-1}X^* & \\& Q \end{array}\right] 
$$

and note the transform matrix is unitary
$$
T = \left[\begin{array}c I  & -XQ^{-1} \\ 0 & I \end{array}\right] \text{ it's eigenvalues are 1}
$$

# LTI ODE
> what does ordinary mean?
> > it means time is the only variable

The solutions for an ABCD system

$$
x(t) = e^{At}x_0 + \int_{0}^{t}e^{A(t-\lambda)}Bu(\lambda)d\lambda 
\\
y(t) = \underbrace{Ce^{At}x_0}_{\text{free response}} + \underbrace{C \int_{0}^{t}e^{A(t-\lambda)}Bu(\lambda)d\lambda + Du(t)}_{\text{forced response}}
$$

> 老师的C在积分里面，应该没有什么问题？

## quivalent of realizations
suppose we have two realizations, they are **equivalent** when they produces the same transfer function

$$
C(sI-A )^{-1}B+D = C_1(sI-A_1 )^{-1}B_1+D_1
$$

Note 
$$
(sI-A)^{-1} = s^{-1}I+s^{-2}A+\dots+s^{-n}A^{n-1}
$$

thus 
$$
D + s^{-1}CB+s^{-2}CAB+\dots+s^{-n}CA^{n-1}B ... 
$$

all of these things 
$$
D, s^{-1}CB, s^{-2}CAB, \dots, s^{-n}CA^{n-1}B
$$
all called Markov parameters


## similar realizations

$$
\left[\begin{array}c A & B \\C & D \end{array}\right] 

\quad

\left[\begin{array}c T^{-1}AT & T^{-1}B \\ CT & D  \end{array}\right] 
$$

we can show they are equivalent

$$
CT(T^{-1}sT - T^{-1}AT)^{-1}T^{-1}B+D = ...
$$
### some thing more than equivalent

For the system ABCD

we define new state
$$
\hat{x} = T^{-1} x \\
x = T\hat{x}
$$

$$
\begin{aligned}
    \dot{\hat{x}}  &= T^{-1}Ax + T^{-1}Bu\\
    & =  T^{-1}AT \hat{x} + T^{-1}Bu
\end{aligned}
$$

> **similar realizations is more similar than the equivalent realizations**\
> in equivalent realizations you may have the states you don't need

Choosing $T$ we can get nice forms from which we can see something (conarnitcal form)

### example

$$
H(s) = \frac{4s - 9}{s^3+2s^2+7s-5} 
$$

this controllalbe canonical realization form is 
$$
\left[\begin{array}{ccc|c} 0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
5 & -7 & -2 & 1 \\
\hline
-9 & 4 & 0 & 0 \\
  \end{array}\right] 
$$

## controllability

> kalman sent to jornal but got rejected

> cantrollability is not that important but it is the stepping stone

consider a system $ABC0$

Definition, let $T>0$ a state $\xi$ is called $T$-controllable if 
$$
\exist u(t)\quad 0\leq t \leq T \text{ that drives } \Sigma
$$
from $x(0) = \xi$ to $x(T) = 0$
> what is $\Sigma$ ? 
> It is the system

> this means it can be driven to zero in T seconds

so 
$$
x(T) = e^{AT}\xi  + \int_{0}^{T}e^{A(T-\lambda)}Bu(\lambda)d\lambda =0 
$$
we can solve for $u(t)$

thus 
$$
\xi  = -\int_{0}^{T}e^{-A\lambda }Bu(\lambda )d\lambda 
$$

controllable $\Leftrightarrow$ we can solve this

we can see this as a box
$\mathbb{C}^n$ <- $\mathcal{L}$ <- u(t)
> input u(t) and out put a state vector

we can argue this that this is linear subspace

thus 
$$
\xi  = \mathcal{R}(\mathcal{L})
$$

so the T-controllable states $\xi$ is a **subspace**, the range of the box

Let $C_T$ be set of T-controllable states

### **theorem a**

**thm a:** $C_T$ is a subspace $\subset$ $\mathbb{C}^n$

this is because $u$ can add and multi -> linear

### **theorem b**

**thm b:** define 
$$
W= \int_{0}^{T}e^{-A\lambda } BB^* e^{-A^*\lambda } d\lambda  \in \mathbb{C}^{n\times n}
$$

this is hermitian

then $C_T = \mathcal{R}(W)$ 

this is called controllability Gramian

remark,
$$
W = \mathcal{L}\mathcal{L}^*
$$

$\mathcal{L}$ maps signals to $\mathbb{C}^n$

if this is non-singular, then the system is controllable

### **theorem c**

**thm (c)** 
$$
C_T = \mathcal{R}\left[\begin{array}c B & AB & A^2B & \dots & A^{n-1}B \end{array}\right] 
$$

> So, the property of T-controllable does not depend on T

**thm(d)**

if The ${n\times (n+p)}$ matrix 
$$
\left[\begin{array}{lll}{\boldsymbol{A}-\boldsymbol{\lambda} \boldsymbol{I}} & {\boldsymbol{B}}\end{array}\right]
$$
has full row rank at every eigenvalue ${\lambda }$ of ${\boldsymbol {A}}$.
>?

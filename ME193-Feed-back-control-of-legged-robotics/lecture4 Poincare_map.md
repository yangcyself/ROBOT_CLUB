# CUE
- The definition of Poincare section and poincare map
- What is the condition for a model to be ES with poincare map?
- How to compute the poincare map
# intuitiion
for a perodic orbit, with a surface s, **the surface s have only one intersecting point with the perodic orbit**

start from a point $x_0$, check where will the state hit the surface next time.

the map: 

x_0 -> the next time the state hits the surface

is called Poncare Map
# Consider a Poincare section 

## Define the time to Impact
Define the time to Impact $T_I: S\rightarrow R$

as 
$$
T_I(x_0) = \left\{\begin{aligned} 
  \min\{t>0|x(t,t_0)\in S \}  \quad & \text{if such t exits} \\
  \infty \quad & \text{if not}
 \end{aligned}\right. 
$$

In this way $X(T_I(x_0),x_0) \in \mathcal{S}$

## define poincare map
$$
P: \mathcal{S}\rightarrow \mathcal{S}
$$
for each $x_0\in \mathcal{S}$, $P(x_0)=X(T_I(x_0),x_0)\in \mathcal{S}$ 

> intuitionL S相当于一个sampling system

### The fixed point
if $x^* \in \mathcal{S}\cap\mathcal{O}$ then $p(x^*) = x^*$

we call $x^*$ a fixed point of P

## The condition to ES

take the tayler expansion

$$
P(x^* + \delta x) = P(x^*) + \frac{\partial p(x)}{\partial x}|_{x^*} \\
x_{k+1} - x_k = \frac{\partial P }{\partial x }|_{x^*} (x_k - x^*)
$$

this is same as:

$$
\delta_{k+1} = A \delta_k
$$

**ES iff $|\lambda_i(\frac{\partial P }{\partial x })|_{x^*}| <1$**

## THEOREM

$x^*$ is ES iff $\mathcal{O}$ is ES

# USE in our hybrid periodic orbits

we can set the poincare section to be impact surface $S$

## How to compute the poincare map
- analytically 
  - "for most systems you cannot really get this"
- numerically
- From Data ???

### Numberical computation

to compute $\frac{\partial P(x) }{\partial x }$

the $j$th column of matrix $A_j$ is 
$$
\frac{P(x+\delta x_ej)-P(x-\delta x_ej)}{2\delta x} 
$$
with 
$$
e_j = \left[
\begin{array}c
0\\0\\...\\1\\...\\0
\end{array}
\right] 
$$

the jth row is 1

## analytical computaion

举了一个例子是小球在地上弹，最后收敛，但是我觉得这个例子不恰当，因为这个是到一个点的收敛

# QA
有人问 How do you find x*

A: by optimization
# CUE
- norm
  - what is equivlent norm? Is all norms in finite-dim vector space equivalent? what about infinite situation?
- inner product
  - What are the four rules of inner product in complex field?
  - <av,w> = ? (complex filed)
- what are the relationships between:
  - inner product space, norm space, and vector space?
- How to show that sint and cost are perpendicular to each other?
- is the space {v = a_0 + a_1t + ... a_nt} complete?
- what are the names stands for?
  - **Banach space**: 
  - **Ailbert space**:
# review of previous
- vector space
- subspace
- span
- linear dependence/ independence
- basis dimension
- direct sum decomposition

> a geometric space needs to define two notions: **distance**, **angle**

## norm: 
measure of length

### norm of function space: 
vector space of functions
$$
\left\{f[0,t]\rightarrow \mathbb{R} \right\}
$$

for example the L2 norm
$$
\left\|f(x) \right\|_2 \int_a^b |f(x)|^2 dt
$$

### norm for matrix space

$$
Tr(A^*A) = \left\|A \right\|_F ^2
$$

Note that $A^*$ is the conjugate

#### inducednorms

$$
\sup \frac{\left\|Av \right\|_p }{\left\|v \right\|_p}
$$

#### equivleant norm

$\left\|v \right\|_a$ and $\left\|v \right\|_b$ are called equivalent if $\exist M,m\neq0$ $m\left\|v \right\|_b \leq\left\|b \right\|_a \leq M\left\|v \right\|_b$

**For all finite-dim vector space, all norms are equivalent**

>但是function space不一样， 如果过证明了这个函数在一种norm下面收敛，并不能说明在下一种norm下收敛

## inner product
captures the idea of angle

**definition**

in a complex vector space, a inner product is a function $\langle v,w \rangle \rightarrow \mathbb{C}$ such that
$$
\langle v,v \rangle \geq 0\\
\langle v,v \rangle = 0 \Leftrightarrow v=0
$$
$$
\langle v,w_1+w_2 \rangle = \langle v,w_1 \rangle+\langle v,w_2 \rangle
$$
$$
\langle v,\alpha w_1 \rangle = \alpha\langle v,w_1 \rangle
$$

$$
\langle v,w \rangle = \bar{\langle w,v\rangle }
$$

**NOTE THE CONJUGATE when change order** 

**NOTE**
$$
\langle \alpha v,w \rangle = \bar{\alpha}\langle v,w \rangle 
$$

define $\langle v,w \rangle = v^*w$ in most of the inner product that we use today

for example the **inner product in function space**

$$
\langle f,g \rangle = \int_{a}^{b}\bar{f(t)}g(t) dt
$$

## Cauchy-swatz ineq
$$
|\langle v,w \rangle |^2 \leq \langle v,v \rangle \langle w,w \rangle 
$$
### lemma
let $\mathbb{V}$ be vector space with inner product $\langle v,w \rangle$

then $\sqrt{\langle v,v \rangle}$ is a norm

*this norm is induced by its inner product*

**NOTE the relationships here**

**Inner product space** $\subset$ **norm space** $\subset$ **vector space**

> it is a common mistake in engineering that 忽略上面那一点 有了Norm，就一定已经定义了相应的inner product

## perpendicular
**inner product is 0**

example:
$$
F[0,2\pi ] \langle \sin t, \cos t \rangle 
$$
we can easily found that 
$$
\int_{0}^{2\pi }\sin(t) \cos(t) dt = 0
$$
thus the $\sin t$ and $\cos t$ are perpendicular

## complete space

for example, we have a normed vector space. We have a sequence of vectors, maybe converges to something that is not in the space.

e.g. consider the space
$$
\left\{v = a_0+a_1t+...a_nt^n \right\}
$$
$e^t$ is on the boundary (can be converged to, but not in the set)

**Complete**: the space includes its boundary

## some name
- **Banach space**: normed  vector space that complete
- **Ailbert space**: the inner product space that complete
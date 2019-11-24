# CUE
- what is the controllability grammian ($W$)
- prove that $C_T$(the T-controllable subspace) = $R(W)$
  - use function space explaination
  - prove by direct sum decomposition of vector in $C_T$
- W is the solution of what equation?
  - left add and right add a term to integrate it
- prove or counter example:
  - Rank(A) == number of nonzero eigen values ?


> even though controllable conanical form is for SISO system, you can use it as a starting point of MIMO system.

## Controllability contd

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

$C_T$ is a subspace\
**prove**: closed under vector-vector addition


## controllability grammian
$$
W= \int_{0}^{T}e^{-A\lambda } BB^* e^{-A^*\lambda } d\lambda  \in \mathbb{C}^{n\times n}
$$

this is hermitian

then $C_T = \mathcal{R}(W)$ 

this is called controllability Gramian


assertion 
$$
C_T = \mathcal{R}(W(0,T))
$$


> II if we can think u($\lambda$) as a long, inf vector that concatenateed of all $\lambda$, $n_u T$ then the integral of B can be regarded as $n_x \times n_uT$ big matrix

> in the function space, $R(\mathcal{L}) = R(\mathcal{L}\mathcal{L}^*)$


### **proof**

$$
C_T \supseteq R(W(0,T))
$$

let $\zeta \in R(W)$ 
$$
\zeta  = Wq = \int_{0}^{T} e^{-A\lambda}B\underbrace{B^*e^{-A^*\lambda }q}_{\text{regard as }u} d\lambda 
$$


$$
C_T \subseteq R(W(0,T))
$$

let $\zeta \in C_T$ 
$$
\mathbb{C}^n =  \mathcal{R}(W) + \mathcal{N}(W)\\
\zeta  = \zeta _1 + \zeta _2
$$

$$
\underbrace{\zeta  - \zeta _1}_{\zeta _3\in R(W)} = \underbrace{\zeta _2 }_{\in N(W)}
$$

> ?? W is hermitian, but is W symmetric? \
> II I think it will be easy to show that W is real?\
> 2019-11-01 20:12:56 这里我本来想问的问题是: 为什么是用$\mathcal{N}(W)$而不是$\mathcal{N}(W^T)$\
> 但是其实应该是在复数域，应该是$\mathcal{R^\perp} = \mathcal{N}(A^*)$ 而不是$\mathcal{N}(A^T)$


then we prove
$$
\zeta _3 ^* \zeta _2 = 0\\
\int_{0}^{T} u^*(\lambda)B^*e^{-A^*\lambda } d\lambda  \zeta _2 = 0
$$

From 
$$
B^*e^{-A^*\lambda }   \zeta _2  = 0
$$

by 
$$
\zeta ^*_2W\zeta _2 = 0 \text{ because in its Null space}
$$
$$
\begin{aligned}
    &\int_{0}^{T} \zeta_2^* e^{-A\lambda} BB^* e^{-A^*\lambda } \zeta_2  d\lambda  \\
    =&\int_{0}^{T} \left\|B^* e^{-A^*\lambda } \zeta_2  \right\|_2^2  d\lambda \\
\end{aligned}
$$
thus 
$$
B^* e^{-A^*\lambda } \zeta_2 = 0 \quad \forall \zeta_2
\tag*{$\square$}
$$



> However 这一坨并不好算

### **THM**

W(0,T) is the slolution of 
$$
AW + WA^* = BB^* - e^{-AT}BB^*e^{-A^*T}
$$

### Proof

$$
\begin{aligned}
    AW + WA^* &= \int_{0}^{T}\left[ Ae^{-A\lambda } BB^* e^{-A^*\lambda }+
e^{-A\lambda } BB^* e^{-A^*\lambda }A^* d\lambda   \right]\\
&=\left[ e^{-A\lambda }BB^*e^{-A^*\lambda } \right]_T^0\\
&=BB^* -  e^{-AT}BB^*e^{-A^*T}
\end{aligned}
$$

with this, we can solve for $W$ and compute its range

### **Thm**
$$
C_T = \mathcal{R}\left[\begin{array}c B & AB & A^2B & \dots & A^{n-1}B \end{array}\right] 
$$

> this looks pretty but not computational attractive

## example assertion
$$
\text{Rank}(A) = \text{number of nonzero eigen values}
$$

counter example:

$$
\left[\begin{array}c 0 & 1 \\ 0 &0 \end{array}\right] 
$$

my explaination:

rank $\rightarrow$ n - dim of 0's eigenvector space\
nonzero eigenvalues $\rightarrow$ n - zeros' multiplicity

## example:

either $P\succeq Q$ or $P\prec Q$?

**false**
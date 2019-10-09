# CUE
- what is adjoint A
- what is the defn of surjection, injection and bijection
- (AB)* = ?
- How the compute the inverse of upper trianguler matrix
- Prove trAB =trBA
- prove not exist AB - BA = I
  - but does this still hold true when AB can be infinite dim?
- calcualte (I+AB)'s inverse
- 如何把sequence和function 理解成向量
- what is the defn of directed-sum-decomposition
# linear algebra review
## some notations
$\exist$, $\forall$, $\exists!$-> uniquely exists

Field: $\mathbb{R}$, $\mathbb{C}$ real and complex field

function: $X\rightarrow x$

**image**(f) = $\{x: \exist d\in \theta,f(d)=x \}$

one-to-one: injection

on-to: surjection

**bijection**: both injection and surjection

## linear euqations
$Ax+b$

situations:
1. no sulution
2. only solution
3. many solutions

## elementry matrix algera

**adjoint** $A^* =$ complex conjugate transpose $(\bar{A})^T$

properties:
- $(A+B)^* = A^* + B^*$
- $(AB)^* = B^*A^*$

- $(AB)^{-1} = B^{-1}A^{-1}$
- $(A^*)^{-1} = (A^{-1})^*$

- $\det(AB) = \det(A)\det(B)$
- $\det(A^*) = \bar{\det(A)}$

### Block upper trangular matrix
$$
\left[\begin{array}c A&X\\0&B \end{array}\right] 
$$
we have
$$
\left[\begin{array}c A&X\\0&B \end{array}\right]^{-1} = 
\left[\begin{array}c A^{-1} & -A^{-1}XB^{-1} \\ 0 & B^{-1} \end{array}\right] 
$$

### trace
- $\operatorname{tr}(A+B) = \operatorname{tr}(A)+\operatorname{tr}(B)$
- $\operatorname{tr}(BA) = \operatorname{tr}(AB)$ (note A,B need not to be square)

#### simple exercise
if A,B finite dimension (如果不是finite dimension 后面有反例)
$$
\nexists A,B \quad i.e. \quad AB - BA = I
$$

### useful matrix inversion lemma
$$
(I+AB)^{-1} = I - A(I+BA)^{-1}B
$$
> 我还没推过

## Vector space
elements in field are called scalars

vector space $\mathbb{R}^n$ $\mathbb{C}^n$

**！！！很多其他的东西也都可以理解成向量！！！**
- matrix
- **sequence** 
  - $\left\{(u_0,u_1,....)\quad u_k\in R \right\}$
  - Note this is infinitly many dimension
- **function space**
  - $\left\{f:(0,\infty)\rightarrow R  \right\}$
  - Note this is **uncountable** large vectors

#### example
exponential family is a set of Basis

$S = \left\{f:f(1) = 0 \right\}$ is a subspace
## Subspace
theorem 
S is a subspcae iff
1. $s\in S \Rightarrow \alpha s\in S\quad \forall \alpha$
2. $s,t\in S \Rightarrow s+t \in S$

## sum of sets
$S+T = \left\{s+t: \quad s\in S, t\in T \right\}$

sum of subspaces is also subspace

### directed-sum-decomposition
$V$: vector space

$S,T$: sub space

V is a direct sum decomposition of $s$ and $t$ if $V = S+T$ and $S\cap P= \{0\}$
> Note we did note say anything about orthogonal here


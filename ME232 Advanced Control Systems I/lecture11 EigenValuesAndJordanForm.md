# CUE
- what is $\text{spec}(A)$?
- How to prove that the eigenvectors in simple jordan form is linear independent?
  - use a polynormial
- How to prove that for $A$ and $B$, the non-zero eigen values for $AB$ is the same for $BA$?
  - What is the significance of this theorem?
- What is the general case of Jordan form?
  - comment on its numerical stability
- What is the difference between Jordan form and Schur form?
- Show from the definition of generalized eigenspace the meaning of Jordan form
- Schur Construction
  - What is the inductional construction of schur form?
  - What is the numerical construction of schur form?
    - Why the operation preserves the eigenvalue?
    - How to compute $A$ and $U$ from the numerical construction?
- How the schur form help when calculating the matrix polynomials?
  - hint: nilpotent
## Eigen Values

The charactistic polynomial
$$
X_A(s) = \det(sI-A)
$$

$\text{spec}(A)$: set of all eigenvalues of A

## lemma:
let $\lambda\in \text{spec}(A)$ then $\exist v \neq 0\quad Av=\lambda v$

> **Note** the $v\neq0$ here it is very important in proof

Note that we may not found an eigenvector corresponding to a repeated eigenvalue.


# Jordan Form

## simple:
**iff all eigen Values are distinct**

## theorem
$$
A\text{ simple } \exist T \quad T^{-1}AT = \left[\begin{array}c \lambda_1 &0& 0\\ 0 & \ddots &0\\0&0&\lambda_n \end{array}\right] 
$$


### Proof
It is simple proved by construction

$$
AT = \left[\begin{array}c \uparrow & \dots &\uparrow \\ v_1 &\dots& v_n \\ \downarrow & \dots & \downarrow   \end{array}\right] 
\left[\begin{array}c \lambda _1 \\ & \ddots & \\ &&\lambda_n  \end{array}\right] 
$$

Thus 
$$
T^{-1}AT = \left[\begin{array}c \lambda _1 \\ & \ddots & \\ &&\lambda_n  \end{array}\right] 
$$

**NOTE, NOT DONE YET, we have not prove that T is invertable**

#### Prove T is invertible

Prove by controdiction suppose $\alpha_{1}v_{1}+\alpha_{2}v_{2}+\dots+\alpha_{n}v_{n} = 0$

WLOG(without loss of generality), let $\alpha_1 \leq 0$

$$
v_1 = \beta_{2}v_{2}+\beta_{3}v_{3}+\dots+\beta_{n}v_{n}
$$

**define M**

let $v$ be any eigen vector of A, $v\neq 0$

$$
M = (\lambda_{2}I-A) (\lambda_{3}I-A) \dots (\lambda_{n}I-A)
$$

$$
Mv = (\lambda_{2}I-A) (\lambda_{3}I-A) \dots v(\lambda_{n}I-\lambda)\\
 = v(\lambda_{2}I-\lambda) (\lambda_{3}I-\lambda ) \dots (\lambda_{n}I-\lambda )
$$

So we have $Mv_1\neq 0$ when we substitude $v$ into it, but from $v_1 = \beta_{2}v_{2}+\beta_{3}v_{3}+\dots+\beta_{n}v_{n}$ it should be 0. This yields controdiciton

## General case
suppose $A\in \mathbb{C}^{m\times n}$, $B\in \mathbb{C}^{n\times m}$

**then The non-zero eigen values of $AB$ is the same to that of $BA$**

> Note that we need to say nonzero, because the size of spec are not same

### Proof
let $\lambda$ be eigen value of $AB$

then $AB v=\lambda v$, $v \neq 0$
$$
AB v=\lambda v \\
BABv = \lambda B v
$$

thus ...

**We still need to show $w=Bv\neq 0$**

this is 
$$
ABv = \lambda v\\
Aw = \lambda v
$$
$\lambda, v$ are all not zero, thus $w$ is not zero

## General case of Jordan form

When the spectral allow for repetition

### Show by example:

$$
\text{spec}(A) = \left\{1,1,2,2,2,9,9,9,9 \right\}
$$

the $\exist T$, s.t.

$$
T^{-1}AT = \left[\begin{array}c 
J_1 && \\ & J_2 & \\ && J_3
 \end{array}\right] 
$$

where 
$$
J_1 = \left[\begin{array}c 1 & 1 \\ 0 & 1 \end{array}\right] \text{ or } \left[\begin{array}c 
1 & 0 \\ 0 & 1
 \end{array}\right] 
$$

$$
J_2 = \left[\begin{array}c 2& 0 & 0 \\0&2 & 0\\0& 0 & 2 \end{array}\right] \text{ or } \left[\begin{array}c 2& 0 & 0 \\0&2 & 1\\0& 0 & 2 \end{array}\right] \text{ or } \left[\begin{array}c 2& 1& 0 \\0&2 & 1\\0& 0 & 2 \end{array}\right] 
$$



So that is **we have eigen values on diagnal, and we may have 1s on the super diagnal**



### But Jordan form is very numerically unstable

example

$$
A = \left[\begin{array}c 1+\epsilon & 1 \\ 0 &1  \end{array}\right] 
$$
when $\epsilon$ is a very small value, vs $\epsilon$ is zero, one Jordan form is 1 and the other is 0.

**This discontinues means unstable**

**We use shore form to calculate, which is stable**

**Shore form have all the stuffs in the upper triangle**

# Functions of square matrix

When A is simple we can simply compute the polynomials of A

$$
p(A) = T\left[\begin{array}c p(\lambda _1) && \\ & \ddots & \\&& p(\lambda_n) \end{array}\right] T^{-1}
$$

For any function(series), if the function of the eigen value is converge, the matrix function is converge

### example:
suppose $f(S) = S^{-1}$ 必须只有所有的Evalue全都不是零的时候才存在

## When A is not simple
$$
f(A) =T \left[\begin{array}c Schur \end{array}\right]  T^{-1}
$$

## Jordan form construction when multiplicity is 2
> Found independtly by YCY hahahahah

Suppose we have a matrix $A$ and $Av_1 = \lambda_1 v_1$, but the multiplicity of $\lambda_1$ is 2 while we cannot find another vector that $Av_2 = \lambda_1 v_2$. 

We want a jordan form, so we start construction from 

$$
A\left[\begin{array}c v_1&v_2 & \dots\end{array}\right] 
=
\left[\begin{array}c v_1&v_2 & \dots\end{array}\right] 
\left[\begin{array}c \lambda _1 & 1 & \dots \\0 & \lambda _1 & \dots \end{array}\right] 
$$

Thus we have 
$$
Av_2 = v_1+ \lambda_1 v_2
$$

thus, we need 
$$
(A-\lambda_1 I)v_2 = v_1 \quad v_2\neq 0
$$


However, I don't know how to prove that $v_2$ exist .....

It is not the case that $v\in \mathcal{N}(A) \Rightarrow v\in R(A)$

But if $v_2$ exists, we can substract $v_1$ from $v_2$ because $v_1$ is in the null space of $A - \lambda _1I$

### After search
this needs [**generalized eigenvectors**](https://math.stackexchange.com/questions/4495/the-intuition-behind-generalized-eigenvectors)

> [MIT note](http://www-math.mit.edu/~dav/generalized.pdf)


check out the [Generalized_eigenspaces note](./[Read]Generalized_eigenspaces.md) for better understanding of eigenspaces.

With the generalized eigenspace
$$
(T - \lambda I)^mv = 0
$$
The $\lambda$ and $1$ in the Jordan forms can make sense.

# schur construction
from a [schur construction note](http://web.math.ucsb.edu/~padraic/ucsb_2013_14/math108b_w2014/math108b_w2014_lecture5.pdf)
## inductional construction
1. find an eigenvalue, and get $E_{\lambda }$ as all the vectors that $A \vec{v}=\lambda \vec{v}$
2. pick orthonormal basis $b_{1 \lambda_{1}}, \ldots b_{k \lambda_{1}}$ for space $E_\lambda$ and extend the whole basis to space $V$ $\left\{b_{1 \lambda_{1}}^{\rightarrow}, \ldots b_{k_{1} \lambda_{1}}^{\rightarrow}, \overrightarrow{c_{1}}, \ldots \overrightarrow{c}_{n-k_{1}}\right\}$

Then our matrix have the form 
$$
A_B = \left[\begin{array}c 
\left[\begin{array}c \lambda_1 && \\ & \ddots & \\ & & \lambda_1  \end{array}\right]_{k_1\times k_1} &
A_{\text{rem}}\\
0&
[A_2]_{n-k_1\times n-k_1}
  \end{array}\right] 
$$
3. Then $A_2$ is also a linear map from the span of the set $\left\{\overrightarrow{c_{1}}, \dots c_{n-k_{1}}\right\}$, we can induction on


The induction implementation is on the next note

## Numerical construction
```python
def findSchur_step(A):
    Q,R = np.linalg.qr(A)
    A_ = R@Q
    return A_
def findSchur(A,k):
    for i in range(k):
        A = findSchur_step(A)
    return A
np.set_printoptions(precision=3, suppress=True,linewidth=100)
A = np.random.random((10,10))
findSchur(A,10000)
```
the result
```py
[[ 4.831,  0.185,  0.325, -0.321,  0.033,  0.445, -0.06 , -0.488, -0.439,  0.728],
[ 0.   ,  0.913, -0.442, -0.312, -0.002, -0.434,  0.385,  0.269,  0.138,  0.337],
[ 0.   ,  0.   , -0.656, -0.415, -0.095,  0.325,  0.301,  0.398, -0.349, -0.112],
[ 0.   , -0.   ,  0.862, -0.677,  0.264,  0.408, -0.022,  0.503,  0.262,  0.108],
[ 0.   , -0.   ,  0.   ,  0.   , -0.622, -0.739,  0.513, -0.062, -0.126,  0.498],
[ 0.   , -0.   ,  0.   ,  0.   ,  0.003, -0.705,  0.405, -0.17 ,  0.165, -0.139],
[ 0.   , -0.   , -0.   ,  0.   , -0.   , -0.   ,  0.276,  0.615,  0.363,  0.156],
[ 0.   ,  0.   , -0.   , -0.   ,  0.   ,  0.   , -0.463,  0.553,  0.111, -0.26 ],
[ 0.   , -0.   ,  0.   , -0.   ,  0.   ,  0.   ,  0.   ,  0.   ,  0.342,  0.169],
[ 0.   , -0.   ,  0.   ,  0.   ,  0.   ,  0.   ,  0.   ,  0.   , -0.16 ,  0.245]]
```
is not a fully upper triangular matrix, but quite good.

We can do this because the core operation
$$
A_{k+1}=R_{k} Q_{k}=Q_{k}^{T}\left(Q_{k} R_{k}\right) Q_{k}=\left(Q_{k} R_{k}\right){\text {in the basis }} Q_{k}
$$
Does not change the eigenvalues

> However $AB$ always has the same nonzero eigenvalues as $BA$
> >Note that here does $AB$ and $BA$ have guarantee of the multiplicity?, but here $QR$ and $RQ$ have should be stronger than $AB$ and $BA$


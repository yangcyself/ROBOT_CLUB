# CUE
- The definition of irreducible
  - what is algebracially closed?
  - what is relatively prime?
- Prove that if p and q are two polynormials that relatively prime, then exist a and b, thus ap + bq = 1
- What the is the construction of Characteristic polynomials
- Projections
  - what is the definition of projections?
  - if P is a projection, then prove that I-P is another projection
    - use definition
    - use similar matrix understanding
- Generalized eigenvalues
  - what is the definition?
  - Prove that the spave $V$ is the direct sum of the generalized eigenspaces.
    1. construct two polynormials 
    2. use ap+bq = 1 construct two projection matrix
    3. play with the null space and range space of the two projection matrix
    4. induction

# Summary
This note is take from [this link](http://www-math.mit.edu/~dav/generalized.pdf). It covers many things about polynomials, Matrix and spaces, and systems.

Some notations:
- $\mathcal{L}(V)$: A linear transformation in vector space $V$. The linear transformation is a matrix
# Polynomials

## irreducible
**Definition**

1. deg(p) > 0, and
2. p cannot be written as a product of two polynomials of positive degree

**It is analogy to integers!**

>There is a really important analogy in mathematics between polynomials and integers. In this analogy, irreducible polynomials correspond to (plus or minus) prime numbers. Monic polynomials correspond to positive integers


the notion of irreducible depends heavily on Field $F$

## algebraically closed.
**definition:** 
when the following conditions are met

1. every polynomial of positive degree in P(F) has a root;
2. every nonzero polynomial in P(F) is a product of linear factors:
   1. $p(x)=a \prod_{j=1}^{\operatorname{deg} p}\left(x-\lambda_{j}\right) \quad\left(\lambda_{j} \in F, 0 \neq a \in F\right)$
3. the irreducible polynomials in P(F) are those of degree one 

$\mathbb{C}$ is algebraically closed

**Any monic polynomial p ∈ P(F) can be written as a product of powers of distinct monic irreducible polynomials**

**if algebraically closed, then $q_i = x- \lambda_i$**

## relatively Prime 
We say that the nonzero polynomials p1 and p2 are relatively prime if they have no common factor of positive degree; equivalently,
if there is no irreducible polynomial q that divides both p1 and p2

就和互质一样的

## Two relative prime polynomials can be scaled and sum to constant 1
Suppose p1 and p2 are relatively prime (nonzero) polynomials. Then there are polynomials a1 and a2 with the property that

$$
a_{1} p_{1}+a_{2} p_{2}=1
$$

>这个性质后面用于证明投影矩阵的 $P+Q=I$ 了

### Prove by construction
Suppose two polynomials 
$$
p_{1}(x)=\left(x-\lambda_{1}\right) \cdots\left(x-\lambda_{r}\right), \quad p_{2}(x)=\left(x-\mu_{1}\right) \cdots\left(x-\mu_{s}\right)
$$

Then we can choose two polynomials that:

$$
a_{1}\left(\mu_{j}\right)=p_{1}\left(\mu_{j}\right)^{-1} \quad(j=1, \ldots, s)\\
a_{2}\left(\lambda_{i}\right)=p_{2}\left(\lambda_{i}\right)^{-1} \quad(i=1, \ldots, r)
$$

Thus $a_{1} p_{1}+a_{2} p_{2}-1$ have $r+s$ distinct zeros, but have at most $r+s-1$ degree. Thus ...

# Characteristic polynomial

suppose $T \in \mathcal{L}(V), \text { and } 0 \neq v_{0} \in V$ 
define
$$
v_{j}=T^{j} v_{0}
$$

choose $m$ such that $v_{0}, \dots, v_{m-1}$ is *linearly independent*, and 
$$
v_{m}=-a_{0} v_{0}-\cdots-a_{m-1} v_{m-1}
$$


Then we can define 
$$
p(x)=x^{m}+a_{m-1} x^{m-1}+\cdots+a_{0}
$$
$$
\operatorname{span}\left(v_{0}, \ldots v_{m-1}\right)=_{\operatorname{def}} U
$$

Then 
> [](I???) I Still don't understand how these things are proved
1. The subspace U is preserved by $T$: $TU \subset U$
2. $p(T)=T^{m}+a_{m-1} T^{m-1}+\cdots+a_{0} I$ acts zero on $U$
3. If $z$ is a polynomial and $z(T)$ acts by zero on $U$, then $z$ is divisible by $p$.
4. **The eigenvalues of $T$ on $U$ are prescisely the roots of $p$**
5. If $q$ is an irreducible polynomial and $Null(q(T))$ has a nonzero intersection with $U$, then $q$ divides $p$.


## connect subspace $U$ to the rest of $V$

suppose $V$ is a finite-dimensional vector space, $T \in \mathcal{L}(V)$ and $U\subset V$ is an invariant subspace: $TU \subset U$

choose a basis $\left(e_{1}, \dots e_{m}\right)$ for $U$, and extend it to a basis $\left(e_{1}, \ldots, e_{m}, e_{m+1}, \ldots e_{n}\right)$ for V

Then 

1. matrix of $T$ in the basis $\left(e_{1}, \dots, e_{n}\right)$ has the form $\left(\begin{array}{ll}{A} & {B} \\ {0} & {C}\end{array}\right)$
   1. where $A$ is $m\times m$, on the subspace $U$, 
2. The set of eigenvalues of T is the union of the set of eigenvalues of A
and the set of eigenvalues of C
3. Suppose p1 and p2 are polynomials such that $p_1(A) = 0$ and $p_2(C)=0$ then $(p_1p_2)(T) = 0$

> 这里面basis的含义是不是比如做了相似矩阵分解之后中间的那个部分？ 否则的话， 怎么可能维度还变小了呢？


## The characteristic polynomial
use a definition of induction

Start from any $v_0$ and find $U\subset V$. Get the form of $\left(\begin{array}{ll}{A} & {B} \\ {0} & {C}\end{array}\right)$ and induction on $C$

# Projections
**definition**
a map $P \in \mathcal{L}(V)$ with $P^2 = P$, equivalently, a map satisfying the polynomial $x^2 = x$

**Properties:** 
The following things are
in one-to-one correspondence:
- projections  $P \in \mathcal{L}(V)$
- pairs of linear transformations $P$ and $Q$ in $\mathcal{L}(V )$ such that $P+Q=I, \quad P Q=0$
- direct sum decomposition $V=U \oplus W$, 
  - $U=\operatorname{Range}(P)=\operatorname{Null}(Q)=\operatorname{Null}(I-P)=\operatorname{Range}(I-Q)$
  - $W=\operatorname{Range}(Q)=\operatorname{Null}(P)=\operatorname{Null}(I-Q)=\operatorname{Range}(I-P)$
  - $Q = I-P$

> I think this can be understood from the similar matrix, decompose $P$ into $U\Sigma U^{-1}$ where $\Sigma$ is a diagonal matrix with only 1 and 0. Then $Q = UU^{-1}-U\Sigma U^{-1}$. \
> But this **may not be complete** I am assuming the matrix $P$ is simple

```python
U = np.random.random((5,5))
U = np.linalg.qr(U)[0]
assertEqual(U@U.T,np.eye(5))## U is the basis

P = U @ np.diag([1,1,1,0,0]) @ U.T
Q = np.eye(5) - P
assertEqual(Q@P,0) # P and Q are two projection matrix
```

# Generalized eigenvalues
**simple defn of multiplicity**

$$
\begin{aligned} V_{\lambda} &=\operatorname{def}\{v \in V | T v=\lambda v\} \\ &=\operatorname{Null}(T-\lambda) \\ &=\operatorname{Null}(q(T)) \quad(q(x)=x-\lambda) \end{aligned}
$$

### exmaple:
> 我是真的看不懂

## generalized
**generalized eigen space**
$$
V_{[\lambda]}=\operatorname{def}\left\{v \in V |(T-\lambda I)^{m} v=0(\text { some } m>0) .\right\} \subset V
$$

## Theorems
$V$ finite complex vector space,
$T\in \mathcal{L}(V)$

1. **each generalized eigenspace $V_{[λi]}$ is preserved by $T$**

2. **The space V is the direct sum of the generalized eigenspaces**

3. **The dimension of $V$ is equal to the sum of the generalized multiplicities of all the eigenvalues**


### Proofs:
#### 1 (I think proof should be like this)

$$(T - \lambda I)^mv = 0\\
(T - \lambda I)^{m+1}v = 0\\$$
$$
(T - \lambda I)^mTv - (T - \lambda I)^m \lambda v = 0\\
(T - \lambda I)^mTv = 0
$$

thus the eigenspace is preserved

#### 2
Prove by induction on $r$, because $\mathbb{C}$ is algebraically closed, the characteristic polynomial of $T$ is a product of linear factors
$$
p_{T}(x)=\left(x-\lambda_{1}\right)^{m_{1}} \cdots\left(x-\lambda_{r}\right)^{m_{r}}
$$

Consider the first eigenvalue

$$
p_{T}=p_{1} p_{2}, \quad p_{1}=\left(x-\lambda_{1}\right)^{m_{1}}, \quad p_{2}=\left(x-\lambda_{2}\right)^{m_{2}} \cdots\left(x-\lambda_{r}\right)^{m_{r}}
$$

Because $p_1$ and $p_2$ relatively prime
$$
a_{1} p_{1}+a_{2} p_{2}=1
$$

Thus we can define two linear transformations $P$ and $Q$:

$$
P=a_{2}(T) p_{2}(T), \quad Q=a_{1}(T) p_{1}(T)
$$

We can show that the $P$ and $Q$ are two projection matrix

$$
P+Q=a_{2}(T) p_{2}(T)+a_{1}(T) p_{1}(T)=1(T)=I\\
P Q=a_{2}(T) p_{2}(T) a_{1}(T) p_{1}(T)=a_{1}(T) a_{2}(T) p_{T}(T)=0
$$

So we have 
$$
\begin{aligned} U &=\operatorname{Range}(P) \\ &=\operatorname{Range}\left(p_{2}(T) a_{2}(T)\right) \\ & \subset \operatorname{Null}\left(p_{1}(T)\right)\quad \text{Why?} \\ & \subset \operatorname{Null}\left(a_{1}(T) p_{1}(T)\right) \\ &=\operatorname{Null}(Q)=U \end{aligned}
$$

Then 

$$
U=\operatorname{Null}\left(\left(T-\lambda_{1}\right)^{m_{1}}\right)=V_{\left[\lambda_{1}\right]} \\
V=U \oplus W=V_{\left[\lambda_{1}\right]} \oplus \bigoplus_{i=2}^{r} W_{\left[\lambda_{i}\right]}
$$

> the later sum i=2 to r is just induction hypothesis


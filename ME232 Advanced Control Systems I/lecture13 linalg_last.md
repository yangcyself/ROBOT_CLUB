# CUE
- Prove if H is hermitian then spec(H) are all real
- if for a matrix, the eigen values are all zero, then is this matrix O?
  - what if the matrix is hermitian
- Prove that if H is hermitian then we can find set of eigenvectors
  - by induction
- what is the first thing to check when we want to show P is psd?
- can you find a $A$ such that $\text{tr}(AA^*)<0$?
- if Spec(A) = {1,2,3}, what is spec(A^2), what is spec(AA^\*) or (A^*A)
  - what if A is hermitian
- what is the schur complement theorem?
  - under P >0 and  P - what? > 0 <=> [PV\\V*Q] >0?
## thm

Hermitan
$$
H = H^* \text{ hermitian } n\times n
$$


- $\text{spec}(H)$ are real
- Full set of eigenvectors(and T is unitary matrix)
  - $H = U\Lambda U^*$ where $U$ is unitary


### Exmaple
for any matrix $A$

if all eigenvalues are 0, is $A$ 0?

No example:

$$
\left[\begin{array}c 0 & 1\\ 0 &0 \end{array}\right] 
$$

but if a is hermitian

we have
$$
H = U 0 U^* = 0
$$

## Prove we can find full set of eigenvectors

prove by induction

$H = (k+1)\times(k+1)$ and $\lambda$ any evalue

> this may be repeated but we can find at least 1 eigenvalue

can find $v\neq 0$ $Hv = \lambda v$

then extend $v$ as $\left\{v,v_{1},v_{2},\dots,v_{k} \right\}$

so that form an orhtonormal basis for $\mathbb{C}^{k+1}$

stack all the vectors up 
$$
U =  \left[\begin{array}c v & v_{1}&v_{2}&\dots&v_{k} \end{array}\right]  \text{ this is unitery}
$$

we have 
$$
HU = \left[\begin{array}c \lambda v & *&*&*&* \end{array}\right] \\
 = \left[\begin{array}c v& v_{1}&v_{2}&\dots&v_{k} \end{array}\right] 
 \left[\begin{array}c \lambda & q^* \\ 0 & G \end{array}\right] 
$$

$G$ is $k\times k$ matrix

compute the $\left( U^* H U \right)^*$

we can find that this is hermitian, so $q^* = 0$, $G = G^*$ (we already know that $\lambda$ is real)

$$
U^*HU = \left[\begin{array}c \lambda & 0 \\ 0 & V\Lambda V^* \end{array}\right] 

=  \left[\begin{array}c 1 & 0 \\ 0 & V \end{array}\right] 
\left[\begin{array}c \lambda &0\\0&\Lambda \end{array}\right] 
\left[\begin{array}c 1 & 0 \\ 0 & V^* \end{array}\right] \\
= W \Lambda W^*
$$


thus 
$W$ unitary

multiply by $U^*$ we get 

$$
H = U^* W \Lambda W^* U = R \Lambda R^*
$$

and we can check that 

$$
RR^* = I
$$


# Positive definate matrices

Defn: $p: n\times n$ is called positive semi definite $P \succeq 0$ if 
1. $P = P^*$ **!!!The first thing to check!!!**
2. $v^*Pv \geq 0\quad \forall v$


### why are we so interested in psd?
example: spring damper

position $x$, mass $m$

total energy 
$$
E = \frac{1}{2}mv^2 + \frac{1}{2}kx^2
$$
$$
E = \left[\begin{array}c x & v \end{array}\right] \left[\begin{array}c \frac{1}{2}k & 0 \\ 0 & \frac{1}{2}m \end{array}\right] \left[\begin{array}c x \\ v \end{array}\right]
$$

> psd matrix captures the energy of the system

**positive definite**
$$
P \succ 0  \quad \text{if } v^* P v >0 \quad \forall v \neq 0\\
P = P^*
$$

## thm
let $P = P^*$
- $P\succeq 0 \Leftrightarrow \text{spec}(P)\geq 0$ 
- $P\succ 0 \Leftrightarrow \text{spec}(P)> 0$ 

**prove**:

suppose $p\succeq 0$
then 
$$
v^* P v\geq 0\quad \forall v
$$

let $\lambda \in \text{spec}(p)$  $Pv=\lambda v, v\neq 0$

for the particular v, we have ....

> $v^*Pv$ is called **quadratic form**

Notation, partial order

$$
P \succ Q \Leftrightarrow (P-Q)>0
$$

- $P\succ 0 \Rightarrow P$  is invertable
- $P\succ Q \Leftrightarrow P-Q \succ 0$
- $P \succ 0, Q\succ 0 \Leftrightarrow P+Q\succ 0$

> NOTE $P\succ 0 \nLeftrightarrow p_{ij}>0$

## Square root of p.s.d. matrices

cosider the function of matrix
$$
f(s) = s^{\frac{1}{2}}
$$

thus this function needs the eigenvalues to be greater or equal to 0

> The defn of $P^{\frac{1}{2}}$ needs the P to be hermitian

$$
P^{\frac{1}{2}} =  U \left[\begin{array}c \lambda \frac{1}{2} && \\& \ddots& \\& & \lambda_n^{\frac{1}{2}} \end{array}\right] U^* \succeq 0
$$

can check that 
$$
P^{\frac{1}{2}}P^{\frac{1}{2}} = P
$$

## exmaple
$$
A \in R^{m \times n} \text{ prove } P = A^*A \succeq 0
$$

pf:
$$
\text{check the hermitian }  P^* = (A^*A)^* = P\\
v^*Pv = v^*A^*Av = \left\|Av \right\|_2^2 \geq 0
$$

so can you find a $A$ such that $\text{tr}(AA^*)<0$? No

## example

consider the set $v = R^{3\times 3}$ is $\text{Tr}(A)$ is a norm? 

No, can be zero without be zero

$$
\left\{\text{Tr}(A) = 0 \right\} \text{is a subspace}
$$

## example of L1
$$
\max c^T x \\
s.t. \quad \left\|x \right\|_1 \leq 2
$$


the optimal solution is at one of the vertex
> **这又和压缩感知联系起来了**

## exmaple

if $\text{spec}(A) = \left\{1,2,3 \right\}$

then what is the $\text{spec}(A^2)$

what can you say about $\text{spec}(AA^*)$? 
you can say noting unless A is hermitian

## Thm schur
$$
X = \left[\begin{array}c P & V \\ V^* & Q \end{array}\right] \succ 0 
\Leftrightarrow P \succ 0 \text{ and } P - VQ^{-1}V^* \succ 0
$$


example

$$
\left[\begin{array}c 1 & x \\ x^* & I \end{array}\right] \succ 0
$$
...

$$
\left\|x \right\|_2 <1
$$


**Prove**

$$
X = \left[\begin{array}c P & V \\V^* & Q \end{array}\right] 
$$


# So how to inductively compute schur?
```python
def findAeigenvalue(A):
    return np.linalg.eigvals(A)[0]
# def findNullSpaces(A):
#     return scipy.linalg.null_space(A)
def findNullSpaces(A):
    return scipy.linalg.null_space(A)
def findRange(A):
    return scipy.linalg.orth(A)
def inductiveSchure(A):
    """
    decompose A = USU^T, where S is the schur form
    return S, U
    """
    if(A.shape[0]==1):
        return A,np.array([[1]])
    n = A.shape[0]
    e = findAeigenvalue(A)
    B = findNullSpaces(e*np.eye(n)-A) # orthogornal basis of the eigenspace e
    k = B.shape[1] # the dimension of eigenspace
    assert(np.allclose(np.eye(k),B.T.conj()@B))
    C = findNullSpaces(B.T.conj()) # R(A^T) \perp # N(A)
    assert(np.allclose(np.eye(n-k),C.T.conj()@C))
    U = np.concatenate([B,C],axis = 1) # The Basis U
    assert(np.allclose(np.eye(n),U@U.T.conj()))
    G_ = np.linalg.solve(U,A@C) # because we have A@C = U@G_ 
    # the matrix is like lambda_1 G_1   -> the whole block is called G_
    #                       0     G_2_n -> this block is called G
    G = G_[k:,:] # the bottom right block
    p = G_[:k,:] # the upper right block
    S = np.concatenate([np.concatenate([np.diag([e]*k),np.zeros((n-k,k))],axis = 0),
                            G_],axis=1)
    assert(np.allclose(A@U,U@S)) # AU = US
    S_ , U_ = inductiveSchure(G) # decompose G as U_ S_ U_.T
    q = np.linalg.solve(U_,p.T.conj()).T.conj() # V q^T = p^T
    
    SS = np.concatenate([np.concatenate([np.diag([e]*k),np.zeros((n-k,k))],axis = 0),
                         np.concatenate([q,S_],axis = 0)],axis=1) 
                         # the S that was transformed into schur form
    R = np.concatenate([np.concatenate([np.eye(k),np.zeros((n-k,k))],axis = 0),
                         np.concatenate([np.zeros((k,n-k)),U_],axis = 0)],axis=1)
#     print("R:\n",R)
#     print("R*SS*R.T\n",R@SS@R.T.conj())
#     print("S:\n",S)
    UU = U @ R
    return SS, UU
A = np.random.random((5,5))
# A = A*A.T
S,U = inductiveSchure(A)
print(A)
print(S)
print(U@S@U.T.conj())
# assert(np.allclose(A@U,U@A_))
```

this Code Took me a lot of time, the error is 

**I need not only transpose, but also Conjugate in Complex field**
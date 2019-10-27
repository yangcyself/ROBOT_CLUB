# CUE
- what is the perpendicular space of (S+T)
- is Null space of A^2 belongs to Null space of A?
  - proof or counter example?
- what is the Null space of A equal to? N(A\*A) or N(AA\*)
- what is the Range of A equal to? R(A\*A) or R(AA\*)
# perpendicular space
let a set $S\subseteq \mathbb{C}^n$

then $S^{\perp}$ is a subspace (easy to prove)

## Properties:
$$
(S+T)^\perp = S^\perp \cap T^\perp
$$
$$
(S\cap T)^\perp = S^\perp + T^\perp
$$
$$
(S^\perp)^\perp = S \text{ (Only true for finite dimentions)}
$$

# gram schmidt procedure

## example:
Gram-schmidt of function space

$S = \left\{1,t,t^2,t^3 \right\}, t\in[-1,1]$ 

then the first basis is $1$

second is $t/\sqrt{2/3}$

third...


# Range and Null space
> it's always easier to prove things with null space
 
example: $\mathcal{N}(A)\subseteq \mathcal{N}(A^2)$

**but the opposite is not true**

counter example: $A = \left[\begin{array}c 0 & 1 \\ 0 & 0 \end{array}\right]$
> this is a very common counter example

### theorem
$$
\text{if } \mathcal{N}(A^k) = \mathcal{N}(A^{k+1})\\
\text{then } \mathcal{N}(A^{k+1}) = \mathcal{N}(A^{k+2})
$$

proof: show both direction belonging

# A central theorem of matrix

$$
\mathcal{R^\perp} = \mathcal{N}(A^*)
$$

$$
\mathbb{C}^m = \mathcal{R}(A)+\mathcal{N}(A^*)
$$

$$
\mathcal{N}(A^*A) = \mathcal{N}(A)
$$

$$
\mathcal{R}(AA^*) = \mathcal{R}(A)
$$

### **the last is very important and useful!**

suppose we have a matrix that input is a funtion and output is a vector

$$
\mathbb{C}^{m}\longleftarrow A^{m\times\infty} \longleftarrow f(n)
$$

Then what is the range of $A?$

we can compute the $\mathcal{R}(AA^*)$ which is a $m\times m$ matrix and get the same range
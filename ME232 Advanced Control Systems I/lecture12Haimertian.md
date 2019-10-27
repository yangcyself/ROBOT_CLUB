# CUE
- how many terms is needed to represent the expansion of f(A) when A is nxn
- prove det(e^At) = e^(trace(At))
  - the two methods to prove the sum of evalue is trace
- calculate \dot{e^At}
- calculate the solution of \dot{x} = Ax
  - calculate (sI-A)^-1
  - connect it with e^At
- what is the solution for system ABCD
- prove $\left\|Ux \right\|_2 = \left\|x \right\|_2$
- prove $\text{spec}(X)$ are real (X is Hermitan)
# review
Function of squre matrix
$$
f(A) = T\left[\begin{array}c f(\lambda _1)& &0 \\\\& & f(\lambda _k) \end{array}\right]T^{-1} 
$$

# Cayley-Haimerttan theorem

$$
\Chi_A(S)= \det(SI-A) = s^n - \alpha _{n-1}s^{n-1}\dots \alpha _1s +\alpha _0
$$
it is easy to show that 
$$
\Chi_A(A) = 0
$$

$$
A^n = -\alpha_{0}I-\alpha_{1}A^{1}-\dots-\alpha_{n-1}A^{n-1}
$$
thus any $f(A)$ can be expressed as a linear combination of $A^{0},A^{2},\dots,A^{n-1}$


## Properties of $e^{At}$
> note this not only for simple, but for general matrix A
1. $e^{A0} = I$
2. $e^{A(t+h)} = e^{At}+e^{Ah}$
   1. this can be proved from $f(s)$
3. $\det \left[ e^{At} \right] = e^{\text{trace}(A)t}$
   - this uses trace is the sum of evalue
   - pf1 characteristic polynomials
   - pf2 $\text{tr}(T\Lambda T^{-1}) = \text{tr}(T^{-1}T\Lambda )$
4. $e^{At}$ is invertible for all $t$
   - $\left[ e^{At} \right]^{-1} = e^{-At}$
   - pf: multiplication is identity matrix
5. $\dot{\left[e^{At}  \right]} = Ae^{At} = e^{At}A$ 
   1. this can prove by power series

## The solution of dynamics
the solution of
$$
\dot{x}=Ax \quad x(0)= \xi \\
$$
is
$$
x(t) = e^{At}\xi
$$

use Laplace
$$
sX(s)-x(0) = AX(s)\\
X(s) = (sI-A)^{-1}\xi
$$

Note that 
$$
(sI-A)^{-1} = (\frac{1}{s}+\frac{A}{s^2}+\dots+\frac{A^{n-1}}{s^n})
$$
recall
$$
\int_0^tf(\tau) d \tau \longleftrightarrow \frac{F(s)}{s} \\
$$
and the step function $I \longleftrightarrow \frac{1}{s}$

thus the series can be transformed back as 
$$
I + At +\frac{A^2t^2}{2!}+ \dots  = e^{At}
$$

### the solution for state transition
$$
\left\{\begin{aligned} \dot{x} = Ax+Bu \\
y = Cx+Du \end{aligned}\right. 
\quad x(0) = \xi
$$

the solution is 
$$
x(t) = e^{At}\xi+\int_{0}^{t}e^{A(t-\tau)}Bu(\tau )d\tau \\
y(t) = Ce^{At}\xi+C\int_{0}^{t}e^{A(t-\tau)}Bu(\tau)d\tau 
$$

we can check the correctness of this solution. 
> recall the diabniz rule for derivitive of integration

## Foundamental theorems for symmetric matrix
**Unitary**

$U$ $n\times n$ is called **unitary** if 
$$
U^*U = UU^* = I
$$
this shows that
1. $U^{-1} = U^*$
2. columns of $U$ forms an orthornormal basis for $\mathbb{C}^n$
example: rotation matrix

other properties
- $\left\|Ux \right\|_2 = \left\|x \right\|_2$
- > 个人认为这个只对由内积定义的norm成立
- all eigenvalues have magnitude 1
  - $Uv = \lambda v\quad v^*U^* = \bar{\lambda}v^*$
  - then $\lambda \bar{\lambda }v^*v = v^*U^*Uv$

## Hermitan of symmetric matrix
$$
H = H^*
$$
> very useful for computation, general matrix 500x500, hermitian matrix **EXTREMELY fast** 10,000x10,000

### Thm

1. **$\text{spec}(X)$ are real**
   1. $Hv = \lambda v$ $v^*H^* = \bar{\lambda}v^*$
   2. $\lambda v^*v = v^*Hv = v^*H^*v = \bar{\lambda} v^*v$
2. can find a full set of eigenvectors form an orthornormal basis for $\mathbb{C}^n$
3. $H = U\Lambda U^*$

> if I met a problem with hermiertan matrix, this is the first thing I write

>in physics, every observable quantity is associated with hermitan matrix
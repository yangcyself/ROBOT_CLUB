# CUE
- for the controllable gramian,W if we know $\zeta  = Wq$, then what is a input that can drive the system to zero, from the init state of $\zeta$
- what is the definition of stability?
- how to connect the stability with the transition matrix A?
- what is the BIBO stability
- What is lyanupov method?
- what is the matlab command that solves the energy matrix for you?
- consider the equation $A^*P + PA + Q  = 0$ where $Q$ is any positive matrix
  - what is the theorem to prove that have a solution $\Leftrightarrow$ stability(real part of spectrum of $A\leq 0$)
- consider the free response. If we sum together the energy of the response $\int_{0}^{\infty}y^*ydt$ , what will we get?(in matrix form)
- How to solve for this matrix? use the same matlab function we just mentioned
- How can we use this matrix to do statespace reduction?

# recap
hidden in the proof of the TH2 last time

$$
C_T \supseteq R(W(0,T))
$$

let $\zeta \in R(W)$ 
$$
\zeta  = Wq = \int_{0}^{T} e^{-A\lambda}B\underbrace{B^*e^{-A^*\lambda }q}_{\text{regard as }u} d\lambda 
$$



thus if you want to control the sstate $\zeta$, and $\zeta  = Wq$, one of the input can be
$$
B^*e^{-A^*\lambda }q
$$



# stability

$\Sigma$ is called internally stable if
$$
\lim_{t\rightarrow \infty} x(t) = 0 

\\\forall \zeta  \text{ with }u(t) = 0
$$

this means the free response decays to zero

## free response

$$
\begin{aligned}
    x(t) &= e^{At}\zeta \\
    &=T\left[\begin{array}c e^{\lambda_1t}& 0 \\0& e^{\lambda_nt} \end{array}\right] T^{-1} \zeta 
\end{aligned}
$$

stable $\Leftrightarrow$ $\text{Re}(\text{spec}(A))<0$

> there are many other notions of stabilities, but in linear system, they all collapse

# BIBO stability
bounded input bounded output

A signal $u$ is called bounded if $\exist M \qquad |u(t)|\leq M$


### defn
$H(s)$ is BIBO stable if $u \text{ bounded}\Rightarrow y \text{ bounded}$ 

Thm 
BIBO stable $\Leftrightarrow$ $\int_{}^{}|\underbrace{h(t)}_\text{impulse response}|dt < \infty$

in linear system, this is equal to stable

## Lyapuov method

define an energy function
$$
V(x) \text{energy in system that is in state x}\\
V(x) \geq 0\\
V(x)= 0\Leftrightarrow  x = 0
$$

note a p.d. function can be $V(x)$, thus let
$$
V(x) = x^*Px\\
p\succ 0
$$

consider how $V$ changes
$$
\frac{dV}{dt} = \frac{\partial V }{\partial x }\frac{\partial x }{\partial t } = x^*(A^*P+PA)x < 0
$$

> How do I know that this can eventually converge to zero? exmaple $\frac{1}{x}+1$, decrease but not converge to 0

### example:
$$
\dot{x} = -x^{2} + 2x
$$
if we choose $V(x) = \frac{1}{2}(x)^{2}$
$$
\dot{V} = x\dot{x} = -x^{2} (x-2) \text{ not to well}
$$
we may try other energy functions

## To solve P
$$
\dot{x} = Ax
$$

A is stable ($\text{Re Spce}(A)<0$) $\Leftrightarrow$ $A^*P + PA + Q=0$ has a solution $P>0$ (choose any FIx $Q>0$)

> this theorem is not for checking the linear system is stable, but it is a very powerful way to design controller 

> Note that if A is stable, we can solve $P$ for **ANY** $Q$

### **Proof**
$\Leftarrow$
$$
V(X) = x^*Px \geq 0 
\\
=0 \Leftrightarrow x=0
$$

$$
\dot{V}(x) = x^*(A^*P+PA)x = -x^*Qx \leq 0\\
=0 \Leftrightarrow x=0
$$

$\Rightarrow$

Suppose $A$ stable

consider 
$$
P = \int_{0}^{\infty} e^{A^*t}Qe^{At}dt
$$

$$
A^*P + PA = \int_{0}^{\infty }\left[ A^*e^{A^*t}Qe^{At} + e^{A^*t}Qe^{At}A \right] dt\\
=e^{A^*t}Qe^{At}| _0^{\infty}  = 0-Q
$$
the zero is because $A$ is stable

now prove that $P$ is p.d
$$
v^*Pv  = \int_{0}^{\infty} \underbrace{v^*e^{A^*t}}_{w^*}Q\underbrace{e^{At}v}_{w} dt>0
$$

### example:

$$
A = \left[\begin{array}c 0 & 1 \\ -1 & -1 \end{array}\right] 
$$

let $Q = I$ let $P = \left[\begin{array}c \alpha & \gamma \\ \gamma & \beta   \end{array}\right]$

then 
$$
\left[\begin{array}c 0 & -1 \\ 1 & -1 \end{array}\right] 
\left[\begin{array}c \alpha & \gamma \\ \gamma & \beta   \end{array}\right]
+
\left[\begin{array}c 0 & 1 \\ -1 & -1 \end{array}\right] 
\left[\begin{array}c \alpha & \gamma \\ \gamma & 
\beta   \end{array}\right]
+ \left[\begin{array}c 1 & 0 \\ 0 &1 \end{array} \right]  = 0
$$


this is just solving linear quations


command in matlab `lyap`

## State space reduction
> the state space representation can be get from experiment and data, (you fit a A)

> 老师之前做了的一个项目，控制天文望远镜的镜子们，每一个镜子6个自由度，如果震荡起来了会影响到其他的镜子，数据分析过来，得到了500order model， 一般 controller一定会比plant复杂，所以500 order controller基本不可能，所以做model reduction


## thought experiments
### exp1

look at the free responds, and the energy 
$$
\int_{0}^{\infty}y^*ydt
$$

which equals to 
$$
\int_{0}^{\infty} \zeta^* e^{A^*t}C^*Ce^{At}\zeta dt\\
= \zeta^* \underbrace{\int_{0}^{\infty}  e^{A^*t}C^*Ce^{At} dt}_{W_o} \zeta 
$$

Note that 

$W_O$ is the solution of 
$$
A^*W_O + W_O A + C^*C = 0
$$

> this can solve using `lyap`

In the real system, the $W_O$ can be very large, get rid of small energy state, 

> if there is 0 limit in the output, you will not able to see them, it is called **Unobservable**

here the $W_O$ is called **obseravbility grammian**, and we have the opposide $W_C$ the **controlbility grammian**

what is important in the as the input, what is important in output?

> Note that 
> $J_{\text{output}} = \zeta ^* W_o \zeta$ So we can do experiments to get the $W_o$
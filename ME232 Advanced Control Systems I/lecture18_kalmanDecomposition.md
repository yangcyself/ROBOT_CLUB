# CUE
- In the problem of setting the initial condition, how to show that the solution with the grammian is just the minimum energy one.
- Do Kalman decomposition to get rid of the uncontrollable states
- Do Kalman decomposition to get rid of the unobservable states
- How to set the poles when you do state feedback
- What is the matlab command for this?
# recap

How to prove the second thought experiment last time

This is very easy to understand if you treate this as a least square problem in function space

$$
\zeta = \int_{-\infty}^{0}e^{-A\tau }Bu(\tau )d\tau 
$$

view $u(\tau )$ as a large vector, concatenate all $u(t)$, and let the $f$ be a huge matrix that concatenates all $e^{-A\tau }B$

then the problem becomes

$$
\min u^Tu\\
\text{s.t.}\quad \zeta  = f^T u
$$


## quike matlab tutorial:

a system ABCD

`sys = lti(ABC,0)`

`bodeplot(sys)`

`hold on;`

`sys2 = hankel??()`

`bodeplot(sys2)`

check the bodeplot and check the step response

`[y,t] = step(sys)`


# observable and controllable

$\Sigma$ is called observable if $\mathcal{VO} = \left\{0 \right\} \Leftrightarrow rk\left[\begin{array}c C \\ CA \\ \dots \\CA^{n-1} \end{array}\right] = n$ 


$\Sigma$ is calld controllable if $\mathcal{C}=R^n\Leftrightarrow rk\left[\begin{array}c B & AB B \dots & A^{n-1} B \end{array}\right]=n$

$\Sigma$ is **mimimum** if it is both controllable and observable


## Kalman decomposition

> show you hwo to get rid of the uncontrollable part, you take the trnaspose you get rid of the unobservable part

for $\Sigma$ ABC0

$\mathcal{C}$ the controllalbe subspace = $R\left[\begin{array}c B & AB &AAB &\dots & A^{n-1} B \end{array}\right]$


lemma: 
$$
\zeta \in \mathcal{C} \Rightarrow A\zeta \text{ is constrollable}
$$

> **DIRECT SUM NEED NOT TO BE PERPENDICULAR**

write $\mathbb{R}^{n} = \mathcal{C}\bigoplus\mathcal{D}$

$$
A\left[\begin{array}c b_{1}& \dots & b_{r} | &b_{r+1} & \dots &b_{n}  \end{array}\right] = \left[\begin{array}c b_{1}& \dots & b_{r} | &b_{r+1} & \dots &b_{n}  \end{array}\right] \left[\begin{array}c A_{11} & A_{12} \\ 0 & A_{22}  \end{array}\right] 
$$

Note that the zero in $A_{21}$ is because A preserves the control space


SO
$$
AT = T\left[\begin{array}c A_{11} & A_{12} \\ 0 & A_{22}  \end{array}\right] 
$$
Similarly
$$
B = T\left[\begin{array}c B_{1} \\ 0 \end{array}\right] 
$$

Then we have the set of new realization
$$
T^{-1} AT = \left[\begin{array}c A_{11} & A_{12} \\ 0 & A_{22}  \end{array}\right] \\
T^{-1} B = \left[\begin{array}c B_{1} \\ 0 \end{array}\right] \\
CT = \left[\begin{array}c C_1& C_2 \end{array}\right] 
$$

So with this $T$, the similar realization
$$
\hat{\Sigma}  = \left[\begin{array}c T^{-1} AT & T^{-1}B \\ CT & 0  \end{array}\right] 
$$

calculate the transfer function
$$
M(s) = \left[\begin{array}c C_{1} & C_{2}  \end{array}\right] 
\left[\begin{array}c SI-A_{11} & -A^{12} \\ 0 & SI-A_{_{22} }  \end{array} \right] ^{-1} 

\left[\begin{array}c B_{1} \\ 0 \end{array}\right] 
$$

Note that the inverse of the $SI-A$ is still a block upper triangluer matrix and the junk in the upper right part is canceled with the zero in B

$$
M(s) = \left[\begin{array}c C_{1} & C_{2}  \end{array}\right] 
\left[\begin{array}c (SI-A_{11})^{-1}  & ???? \\ 0 &( SI-A_{_{22} } )^{-1}  \end{array} \right] 
\left[\begin{array}c B_{1} \\ 0 \end{array}\right] = C_{1} (SI-A_{11})^{-1} B_{1} 
$$

So the reduced part realization is 
$$
A = A_{11} \qquad C = C_{1}  \qquad B = B_{1} 
$$

# control system design LTI ss model

>老师的一个学生写的chrome，基本上谷歌第八（“他也没送我一个安卓”）

Things to consider
- stabbility
- performance
  - input energy
  - e.g. overshoot in elevator, settle time in robotic arm
- Robustness
  - introlduce lagency, 
  - some noise
- > in ariplane design, the most challege is you input have little "authority" (in mark-xx you have to pump the fuel to move the CoM to control the posture of airplane)
- Professor works in modeling(not design), when it related to people, it becomes game

start with state space model, do a state space control

# futher road map
1. suppose you can observe the whole state
   1. then you do state feedback
2. you have to observe the state from the input and the output
   1. introlduce observer
   2. optimal observer is called **Kalman filter**

# close loop
$$
u = Lx +v
$$

state feed back makes the system 
$$
\Sigma _{cl} = \left[\begin{array}c A+BL & B \\ C & 0 \end{array}\right] 
$$

**to what extent can we change the matrix A**

You can change the eigen value to what ever you want, you can set the eigenvalue of A

## example

consider a system and its controllable cononical form

A's last row is the coefcient of the denominators, and A+BL can change the denominators to whatever you like.

in matlab `L = place(A,B,poles)`

There are no controllable form for MOMI systems, but you can still use `place` for MOMI system

caveotes in `place` command, it cannot handel repeat in list of poles

How do you place the poles is another problem

optimal control goes one step further

> The moon shot would not be possible without calman filter.
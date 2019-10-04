# CUE
- express ddy
- how to do IO linearazation of controller u?
  - what it is its feedforward control
  - and what it is its feedback control?
# review of the dynamics and control goal
$$
\ddot{y} = L_fL_fh(x)+L_gL_fh(x)u
$$

where 
$$
L_fh(x) = \frac{\partial h }{\partial x }f(x) 
$$

and where 
$$
L_gL_fh(x) = \frac{\partial h }{\partial \dot{q} }D^{-1}B
$$

# How to design u?
## By input output linearization
theorem
$$
\text{if } \ddot{y} = -K_D - K_P y\\
\Rightarrow y\rightarrow 0 \text{  exponentially}
$$

so we can choose 
$$
u(x) = L_gL_fh(x)^{-1}\left( -L_f^2h(x)+v \right)
$$

the previous part$L_gL_fh(x)^{-1}\left( -L_f^2h(x)\right)$ is called feed forward 

the following is called feedback

then $v$ can be $-K_D - K_P y$

# an simulation example
一个三根棍组成的劈叉机器人，甩脚和支撑脚永远对称，所以机器人的两个脚一直在地上拖，只不过是一个有力一个没有力
$$
y = \left[\begin{array}c \theta_2+\theta_1 \\ \theta_3 - c \end{array}\right] 
$$

# IO linearazation for dynamics with constraints

with the constraints torque, we have
$$
\ddot{y} = L_fL_fh(x) + L_{g_1}L_fh(x) + L_{g_2}L_fh(x) \lambda
$$

control need 
$$
u(x) = L_gL_fh(x)^{-1}\left( -L_f^2h(x)-L_{g_2}L_fh(x) \lambda +v \right)
$$

So the problem is: How do we compute the $\lambda$
# CUE
- VC with system with constraints
- 在现在的state在control target surface 的时候，controller 的输出如何
- 如何event base control？
- event based control的controller $\beta$应该满足什么
# review
## last time:
- Virtual constraint
- control to enforce VC

## Today
- IO linearization for system with constraints
- event based control

## VC with system with constraints
问题: 如果我要直接控制，我需要知道constraint 的表达式，如何求解直接控制的方程

方法：解多项式
>这玩意点破了很简单，但是在老师的故意误导下，所有举手发言的都被他带歪了

$$
\left[\begin{array}c 
D & -J^T & -B\\
J & 0&0\\
0 & l_{g_2}L_fh(x)&l_{g_1}L_fh(x) \end{array}\right] 
\left[\begin{array}c \ddot{q} \\ \lambda  \\ u \end{array}\right] 
= 
\left[\begin{array}c -C\dot{q}-G \\ -\dot{J}\dot{q} \\-K_ay - K_p\dot{y}-L_{f^2}h(x) \end{array}\right] 
$$

## intuitive explanation of controller
想象 perodic oribit

加上controller， 就是沿着perodic oribit的一个平面， controller 的任务就是把状态拉到这个平面上

注意，controller的任务分为两点
- 离开平面的点拉回到目标平面 (feed back)
- 在平面上的点保持在平面上  (feed forward)

> controller 的公式feed forward control 那一项其实是强行把一个非线性系统搞成线性控制。 cancel off nonlinear part. 如果这一部分cancel的不好，则还是有可能不稳定，然后就进入了 robust control 的范围

注意如果现在的状态在控制平面上，但不在periodic orbit上，那么控制器只会保持其在控制平面上，并不会让它靠近periodic orbit.

## Event based control
我们之前都做了什么
- open-loop hybrid system
- 加上controller, 变成 Closed-loop hybrid system
- 研究其stability

**这个时候，如果发现不是stable的，怎么办呢？**

一个方法
把控制的目标变成可以变化的

$$
y = h(q,\beta )
$$

$\beta$ is a vector that constant during the step, $\beta=0$ if the state is on the periodic orbit

> Note that we let $\beta$ be constant during step, because this is the most naive approach. If $\beta$ can be changed during the step, then it is **dynamic control**

How to understand:

in this way, the controller target surface can be changed in different steps. So we can control the state to converge from all direction.

### How to choose $\beta$
Note 
$$
x_{k+1} = P(x_k,\beta_k)
$$
where $P$ is the poincare map. Is a **non-linear discrete control system**

we also compute the $\beta$ via numerical methods

$$
X_{k+1} = P(x_k,\beta_x) =P(x^*,0) + \left.\frac{\partial P }{\partial x }\right|_{(x^*,0)}(x_k - x^*)
+\left.\frac{\partial P }{\partial \beta }\right|_{(x^*,0)}(\beta)
$$
thus we can get 
$$
\delta x_{k+1} = A\delta x_k+B\beta_k
$$

we choose $B$ so that 
$$
|\lambda(A-B_k)|\leq 1
$$

## 理解
B相当于是 整个control loop的外面又包了一层 discrete 的control
# [The 3D Linear Inverted Pendulum Mode: A simple modeling for a biped walking pattern generation](https://ieeexplore.ieee.org/document/973365)

## SUMMARY
这个文章设计了一个模型，把一个机器人建模成一个倒立摆，文章内容如下:
- 模型描述
- 模型性质研究， (没有输入时的响应)
- 设计一种步态

模型的特点:
- 一个倒立摆，generalized coordinate是$[\theta_r, \theta_p, r]$, 输入就是这些扭矩，以及沿着轴向的力
- 一个约束要求机器人的高度$z$保持$z_c$

模型性质：
- 自由响应的轨迹是双曲线

步态设计:
- 也就是基于双曲线设计的一个轨迹，思路是在一个脚撑地成倒立摆的姿势的时候把脚移动到另一个落脚点，然后这样很多个双曲线相连就得到了轨迹。

## Highlights
### 3D Linear Inverted Pendulum Mode Although
> the original dynamics were nonlinear and we derived linear dynamics with- out using any approximation

得到的过程是先得到拉格朗日方程
$$
m\left(\begin{array}{c}{\ddot{x}} \\ {\ddot{y}} \\ {\ddot{z}}\end{array}\right)=\left(\mathbf{J}^{\mathrm{T}}\right)^{-1}\left(\begin{array}{c}{\tau_{r}} \\ {\tau_{p}} \\ {f}\end{array}\right)+\left(\begin{array}{r}{0} \\ {0} \\ {-m g}\end{array}\right)
$$
同时乘J得到
$$
m\left(\begin{array}{ccc}{0} & {-r C_{r}} & {-r C_{r} S_{r} / D} \\ {r C_{p}} & {0} & {-r C_{p} S_{p} / D} \\ {S_{p}} & {-S_{r}} & {D}\end{array}\right)\left(\begin{array}{c}{\ddot{x}} \\ {\ddot{y}} \\ {\ddot{z}}\end{array}\right)= \left(\begin{array}{c}{\tau_{\mathrm{r}}} \\ {\tau_{p}} \\ {f}\end{array}\right)-m g\left(\begin{array}{c}{-r_{r} S_{r}}/D \\ {-r C_{p} S_{p} / D} \\ {D}\end{array}\right)
$$
> 我觉得原文中这里有略微差错

取第一行化简得到
$$
m\left(-r D \ddot{y}-r S_{r} \ddot{z}\right)=\frac{D}{C_{r}} \tau_{r}+r S_{r} m g
$$

。。。。。我就不抄一遍了。。。。。

总之最后的线性模型说得玄乎也好理解，就是因为控制$z_c$所以沿着倒立摆的力需要抵消垂直方向的重力，另外的力的分量是线性的？

最后的公式
$$
\ddot{y}=\frac{g}{z_{c}} y-\frac{1}{m z_{c}} u_{r}
$$
$$
\ddot{x}=\frac{g}{z_{c}} x+\frac{1}{m z_{c}} u_{p}
$$
其中
$$
\begin{aligned} \tau_{r} &=\frac{C_{r}}{D} u_{r} \\ \tau_{p} &=\frac{C_{p}}{D} u_{p} \end{aligned}
$$

$\tau$ 是扭矩

### Nature of the 3D Pendulum Mode
这个证明了自然响应是双曲线， 感觉还是挺有意思的

$$
\begin{aligned} \ddot{y} &=\frac{g}{z_{c}} y \\ \ddot{x} &=\frac{g}{z_{c}} x \end{aligned}
$$

这个式子积个分得到的就是一个守恒。并且根据**开普勒定律**
> This results well-known Kepler’s second law of planetary motion: **areal velocity conservation.**

得到能量守恒：
$$
\begin{aligned} E_{y} &=-\frac{g}{2 z_{c}} y^{2}+\frac{1}{2} \dot{y}^{2} \\ E_{x} &=-\frac{g}{2 z_{c}} x^{2}+\frac{1}{2} \dot{x}^{2} \end{aligned}
$$

最后得到双曲线形式：
$$
\frac{g}{2 z_{c} E_{x}} x^{2}+\frac{g}{2 z_{c} E_{y}} y^{2}+1=0
$$

### 步态设计
没看懂， 课程论坛问了也没人回。。。
>In the paper which is originally planned to be discussed today(Kajita2001IROS), A 3D pendulum model is defined and analysed and suddenly they gave a pattern generation and a control law, which I think is very difficult to understand.



>They give the relationship between the initial state and the final state.

>$$\left(\begin{array}{l}{x_{l}^{(n)}} \\ {v_{f}^{(n)}}\end{array}\right)=\left(\begin{array}{cc}{C_{T}} & {T_{e} S_{T}} \\ {S_{T} / T_{e}} & {C_{T}}\end{array}\right)\left(\begin{array}{l}{x_{j}^{(n)}} \\ {v_{i}^{(n)}}\end{array}\right)$$



>First, I wonder what does the superscript (n) stand for. Are they derivatives? But I have never seen a system whose derivatives have totally the same relationships. Or they just represent 'vectors of n dimension', but in the later equations, they seem like derivatives.
>For example the calculation of distance $d=v_{f}^{(1)} T_{d b l}$



>And I don't understand what is the control law doing. I don't even know this is a discrete one(selecting the next foothold) or a continues one....  



>Could anyone help with that? Any suggestion will be very appreciated. Thank you in advance.


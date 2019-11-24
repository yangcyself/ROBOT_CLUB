# CUE
- What is the difference between safety and robustness
- What is the equation for composition of barrier functions?
- How to use gait library method to make the robot take steps of different lengths?
- suppose B(x) = h_{s} - h_{\gamma } \geq 0, u's relative deg is 2, what is the problem for this B, how to change it?

>Cassie's sisters 

>In caltech, Umich all have cassie

# The difference between stability and robutness

- the safty is about consider obstacles
- the robustness is about uncertainty and disturbance

The ideas are different but the methodologies may same

>Barrier function is just one approach, There are other people using **reachabilities** and **temproal logic** for achieving safety.

> if want to prove stability for MPC, use control lyapunov functions

The different directions of study

- robust control ME237 nonlinear control
- ???? ME231A

# composition of control barrier function

$$
B_{\cup} = B_{1} +B_{2} \qquad B_{\cap} = B_{1} B_{2} 
$$

> There is also a direction about How to design safety critical vision for dynamic robotics systems

> `cvxgen` guarantee that optimizaion of QP is in real time.

> The CBF-CLF-QP used in the project is similar to LQR method(not MPC), not just do the control in just one time step

>> what is the difference between LQR and MPC? online and offline?

# How to design the robot to step on stepping stones (changing step length and height)?

## Approach1 offline gait library optimization

for example off-line optimize the gait of 
- $g_{0.3,0.7}$
- $g_{0.7,0.7}$
- $g_{0.7,0.3}$
- $g_{0.3,0.3}$

$g_{0.3,0.7}$ this means the previous step length is 0.3 and the next step length is 0.7

With the gait library, suppose we took a step of length 0.4 and then is about to take another step of length 0.6
we interpolate $g_{0.4,0.6}$ using the four gaits in the library.

interpolate -> linear interpolate the parameters

this controller has no guarantee, but it works.

## How to choose the function B

>**relative degree:** we say the input is relative degree 2 of a function $B$ if the input shows up in the second derivitive of the function $B$

For example, we want the robot to avoid overhead.

We want

$$
B(x) = h_{s} - h_{\gamma } \geq 0
$$

but because the relative degree is 2, we cannot use this to design $u$

Thus, we let, 
$$
B(x) = \gamma g(x) + \dot{g}(x)\\
\dot{B}(x) = - \gamma J \dot{q} - \dot{J}\dot{q} - J\dot{q}
$$

This $B(x)$ is better because it has $u$ involved, and 

g(x) will never go cross zero if $B$ is always positive

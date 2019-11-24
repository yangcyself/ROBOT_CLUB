# CUE
- what is control barrier functions
- what is CLF_QP
- what is CBF-CLF-QP
- what does the "safe critical" represents
# CLF-QP

$$
\min _{u} u^{T} u\\
\text{s.t.}\quad L_{f} V(x) + L_{g}V(x)u \leq 0 
$$

The constraint means that the A.S.

Note the solution can be written explicitly
$$
u^{*} = \left\{\begin{aligned} & 0 & L_{f} V(x) <0\\
& \frac{-L_{f} V(L_{g} V)^{T} }{L_{g} V(L_{g} V)^{T}} & 
 \end{aligned}\right. 
$$

We can relax on this problem to guarantee solution exists

$$
\min _{u} u^{T} u+p\delta ^{2} \\
\text{s.t.}\quad L_{f} V(x) + L_{g}V(x)u \leq \delta 
$$

# control barrier functions

The control barrier function makes it staies in the safe set $C = \left\{x|B(x)\geq 0 \right\}$ if $x(0)\in C$

$$
\dot{B}(x) = L_{f} B+L_{g} Bu
$$
> this assumes the relative degree is 1

we can choose 
$$
\dot{B}(x,\mu )\geq -\gamma B
$$

The CBF-CLF-QP

$$
u^{*}=\min _{u} u^{T} u + p\delta ^{2} \\
\text{s.t.}\quad \dot{V}(x,u)\leq -\lambda V(x)+ \delta \\
B(x,u)\geq - \gamma B(x)
$$


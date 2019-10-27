# CUE
- How to prove cauchy schwarz theorem
- how to prove that $\langle v,v \rangle^{\frac{1}{2}}$ qualifies as a norm
- how to prove that $(A^*A)^{-1}A^*b$ is the solution to least square？
## cauchy schwarz
prove

$$
|\langle v,w \rangle|^2 \leq \langle v,v \rangle \langle w,w \rangle 
$$
clear this is true when $w=0$, now consider the situation  that $w\neq0$

clear
$$
0\leq \langle v+\alpha w, v+ \alpha w \rangle  = \langle v,v \rangle + \alpha \langle v,w \rangle + \overline\alpha \langle w,v \rangle + \alpha \overline{\alpha }\langle w,w \rangle 
$$

choose $\alpha = -\frac{\langle w,v \rangle }{\langle w,w \rangle }$

then we can get the theorem

### prove $\langle v,v \rangle^{\frac{1}{2}}$ qualifies as a norm
the two properties are easily shown

this can be proved using cauchy schwarz theorem

## least squares
least square 
$$
Ax = b
\\\hat{x} = (A^*A)^{-1}A^*b
$$

Proof:

let $x = \hat{x} +q$

then 
$$
Ax-b = (A(A^*A)^{-1}A^*-I)b+Aq
$$
it can be show that $Aq$ is perpendicular to $(A(A^*A)^{-1}A^*-I)b$

thus this length reaches minimum when the length of $q$ is 0

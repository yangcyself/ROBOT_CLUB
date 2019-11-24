# CUE
- Thought experiment, what is the minimum energy of the input to set the system to a desired state?
- How to make the controllability gramian and observability gramian equal?
- what is good about this?
- what are the related matlab commands?
- Connect the controllable and observable grammian with the controllable and observable matrixes


> in the lecture the professor uses transpose instead of conjugate.
>  >Because state space realizations for physical systems have real numbers only
## another thought experiment

for the system $\Sigma$, apply the input $u$ from $-\infty <t\leq 0$ so that $x(0) = \zeta$

apply the input, to set up the initial condition of $x$ to be $\zeta$

of these input, we want to find the minimum energy $u$

$$
\min _{u(t) \;-\infty<t\leq 0} \left\|u \right\| ^2 \\
\text{s.t.}\quad x(0) = \zeta 
$$

The solution 
$$
W_c = \int_{-\infty}^{0} e^{-At}BB^*e^{-A^*t}dt
$$

$W_c$ is the only solution of $AW_c +  W_{c}A^* + BB^*=0$
> this is called controlability grammian

the $J_{\text{input}} = \zeta ^* W_c^{-1}\zeta$

> I think this can be derived from the grammian in last last lecture

Yes, this problem is quite similar to T-controllable form. The $u(t)$ that satisfies our condition is 
$$
\int_{-\infty}^{0}e^{-A\tau }Bu(\tau )d\tau  = \zeta 
$$

and similar to T-controllable form we know that $\zeta$ is in the subspace of the grammian

$$
\zeta  = W_{c} v \quad  W_{c}^{-1} \zeta  = v
$$
and 
$$
\zeta = \int_{-\infty}^{0}e^{-A\tau }B\underbrace{B^*e^{-A^*\tau }v}_{u(\tau )} d\tau 
$$

if we let  the $u(t)$ be that term, then the energy is 
$$
\begin{aligned} \int_{-\infty}^{0} u(t)^*u(t) &= \int_{-\infty}^{0} v^* e^{-A\tau }BB^*e^{-A^*\tau } v d\tau  \\

&= v^* W_{c} v\\
&= \zeta W_{c}^{-1*} W_{c} W_{c} ^{-1} \zeta \\
&= \zeta W_{c}^{-1} \zeta \text{ because W is grammian}
\end{aligned} 
$$

> I have totally no idea about how to prove that this is the minimum energy

### example
suppose 
$$
W_{c} =\left[\begin{array}c 0.01 & 0 \\ 0 & 100 \end{array}\right] 
$$

Then the first state is not easily affected by the input, (to change this state, we use $100$ energy rather than $0.01$). So we can get rid of this state

## what if the grammians are equal

Then we can get rid of the same state for this two perspective

> 这个的意思是说 controllability grammian 是要去掉一套state， 然后另外一个grammina也是要去掉一套state， 所以问题在于我们使用哪一套grammian来做state reduction呢？ 所以我们把grammian 弄成一样的就好了

we can consistently remove unimportant states, So we want make the grammians equal.

for a system $\Sigma$ ABCD stable
$$
W_{o} \; ! \text{solution of } A^*W_{o}+W_{o}A + C^*C = 0 \\
W_{c} \; ! \text{solution of } AW_{c}+W_{c}A^* + B^*B = 0 
$$

we can get similar realization of the system

The two equations become
$$
(T^{-1} AT)^* \hat{W_o} + \hat{W_o} T ^{-1} A T + T^*C^*CT = 0\\
T^* A^*T^{-*} \hat{W_o} + \hat{W_o}T^{-1} A T + T^*C^*CT = 0
$$
left mul $T^{-*}$ and right mul $T^{-1}$
$$
\Rightarrow A^* \underbrace{T^{-*}\hat{W_o}T^{-1}}_{W_o} + T^{-*}\hat{W_o}T^{-1}A +C^*C = 0
$$


thus
$$
\hat{W_o} = T^* W_oT\\
\hat{W_c} = T^{-1} W_c T^{-*} 
$$

## thm

how to choose $T$ to make them equal

1. calculate $W_{o},W_{c}$  (`lyap`)
2. Spec($W_{0} W_{c}$) are $\geq 0$
   1. Hankel singular values = $\left\{\sigma^2_{1},\sigma^2_{2},\dots,\sigma^2_{n} \right\}$
3. Choose $T$
   1. $W_{c}^{\frac{1}{2}} W_{o} W_{c}^{\frac{1}{2}} = U Q^{2} U^*$
   2. $T = W_{c}^{\frac{1}{2}}U^TQ^{-\frac{1}{2}}$ 
   3. $Q^2 = \left[\begin{array}c \sigma _{1}^{2} & 0 \\ 0& \sigma _{n}^{2}  \end{array}\right]$
   4. Then $\hat{W_o} = \hat{W_c} = Q$

### the second step 
$$
Spce(W_{o} W_{c} ) \geq 0
$$

Note that this may not be hermitian, but we can prove this by 
$$
\text{spec}(W_{o} ^{\frac{1}{2}} W_{o} ^{\frac{1}{2}} W_{c} ) = \text{spec}(W_{o} ^{\frac{1}{2}} W_{c} W_{o} ^{\frac{1}{2}})
$$

> note that here we assume that the system is observable and controllable. Otherwise there will not be the inverse operations

## treate the stable and unstable states

In a typical system you may get a range of **Hankel singular values**

you plot them, 
>matlab command is like `balrel`, or `hankel` (not exact)

Then you can keep the first $m$ important states

>in the homework, you just write about three lines matlab

## critic
there is a lot more to do in model reduction.

For example, now we only consider that the state which is easily affected by the input, but we can limit on the **certain bandwidth or spectrual** of the input.

# back to the controllable and obserable problem

if you constraint on the input, then it becomse an optimization problem

> why do we throw away the state that is not affected by the input? Is this because we also assume that noise affects the same range as input?

## uncontrollable state

in in our thought experiment that some state is not controllable, i.e. it takes inf energy to set the system to the desired state. Then it is also not controllalbe in T-controllable sense.

## unobservable state 
for a system, apply zero input,

$\zeta$ is called unobservable if $y(t) =0$

let $VO$ be the subspace of all the unobservable states $\Leftrightarrow$ $Ce^{At}\zeta =0$


Then this is a subspace of $R^n$

### Thm

$$
VO = \mathcal{N}\left[\begin{array}c C \\ CA \\ \dots \\CA^{n-1} \end{array}\right] 
$$

to prove this we can go from 
$$
Ce^{At}\zeta  = 0
$$

use caley-hamilton or differentiate the $e^{At}$

> it is beauty, but we should not seduced to beauty. Hankel model reduction is far more important
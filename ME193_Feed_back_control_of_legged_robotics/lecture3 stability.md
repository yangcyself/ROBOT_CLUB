# CUE
- definition of Perodic Orbits
- how many kind of stabilities are there?
- definition and relationship between SISL, Attractive, AS, ES
# Perodic Orbits: limit cycles
$$
\Sigma: x=f(x), x(0) = x_0\\
$$
$\mathcal{X}(t,x_0)$ the solution trajectory of $\Sigma$ starting at $x_0$


$\mathcal{X}(t,x_0)$ is period if $\exist 0<T<\infty$ s.t. $x(t+T,x_0) = x(t,x_0)\quad \forall x \geq0$ 

## Perodic oribit
A set $\mathcal{O}\in X$ is a perodic oribit (limit cycle) if
$$
O = \{x(t,x_0)|t\geq 0\}
$$

**NOTE**: this is not only an orbit, it is a perodic orbit:

**it cannot go faster or slower.**

# Stability
What it means for perodic orbit to be stable?

**SISL**: stabiltiy in a sense of Lyapunov:

For any perodic orbit,$\mathcal{O}$ for a tube $\mathcal{O}+\epsilon$, can find a smallest tube $\mathcal{O}\delta$ s.t. no matter where the initial condition is, the solution staies in the larger tube

#### defn dist
define
$$
\operatorname{dist}(x,\mathcal{O}) = \min_{x_i\in \mathcal{O}} \operatorname{dist}(x_i,x)
$$

## Lyapunov stability:
if $\forall \epsilon > 0$ $\exists \delta>0$ such that $\forall x_0: \operatorname{dist}(x_0,\mathcal{O})<\delta$, $\operatorname{dist}(x(t,x_0),\mathcal{O})<\epsilon$

## attractive:

Perodic orbit $\mathcal{O}$ is attractive if there exists $\epsilon > 0$, s.t. $\forall$ initial condition : $\operatorname{dist}(x_0,\mathcal{O})<\epsilon$

> the Lyapunov stability and attractive are two different aspect of stability

## (AS) Asymptotically stable
Perodic Oribit is asymptotically stable if it is SISL & attractive

## (ES) exponentially stable
if $\exist \epsilon>0, N>0, v>0$ s.t. $\forall x_0$: $\operatorname{dist}(x_0,\mathcal{O})<\epsilon$ we have
$\operatorname{dist}(x(t,x_0),\mathcal{O})\leq N e^{-vt}\operatorname{dist}(x_0,\mathcal{O})$

How to check ES? use **Poincare' MAP**




# Q/A
## Q
 Does Periodic orbit state contains time factor?
Suppose there is a controller that freeze the robot's input state, that is, ∀tx(t,x0)=x0. Then is this controller a stable one in the sense of Lyapunov?

I think here the key issue is the definition of the states in the periodic orbit. If the states involve the time t, then the above controller is not a stable one. 

Or does this problem have to do with time-dependent and time-invariant kind of controller? For example, the states of the time-dependent controller contain time while that of time-invariant do not?

Thank you very much!

## A
For analyzing the stability of periodic orbits, we'll look at something called orbital stability: we typically want minτ∥x(t)−x∗(τ)∥→0 where x(t) is the state of the system at time t, x∗(τ) is a state on the periodic orbit and τ is phase along the periodic orbit. You can think of τ as a substitute for time t, but is a function of the state of the system and monotonically increases from 0 to 1 along the periodic orbit.

Now, minτ∥x(t)−x∗(τ)∥ is the minimum distance of the current state of the system from a point on the periodic orbit. In your example, if the controller maintains the system state at x0 (i.e. x(t)≡x0) and if the periodic orbit begins at x0, i.e. x∗(τ)=x0, for τ=0, then minτ∥x(t)−x∗(τ)∥=0∀t, and the system is stable. 

You are correct in that if the desired state on the periodic orbit was defined in terms of the current time, then the system would be unstable since ∥x(t)−x∗(t)∥ would increase with time. 

If you are familiar with the concepts of manifolds, you can think of the periodic orbit as a manifold in the system's state space and orbital stability would imply converging to that manifold. Hope this clarifies your question!
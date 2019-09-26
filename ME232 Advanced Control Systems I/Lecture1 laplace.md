# CUE
- functions to memorize
  - step
  - impulse
  - e^{-at}
- properties
  - linearity
  - time scaling f(\alpha t) <-> 1/\alpha F(s/\alpha)
  - time-shifting
  - frequency shifting
  - time diff
    - df/dt = sF(s) - f(0)
  - freq diff
    - (-t)^n <-> d^nF(s)/ds
  - time integration
- partial functions
- stability
- initial value and final value theorem
## functions to commit to memory:

step -> 1/s

\delta -> 1

e^{-at} -> 1/(s+a)

## properties
Linearity
time scaling
time-shifting
frequency-shifting
time diff

freq diff

time integration

frequency shift

$$
\begin{aligned} \text { linearity } & \alpha f \longleftrightarrow \alpha F, \quad f+g \longleftrightarrow F+G \\ \text { time-scaling } & f(\alpha t) \longleftrightarrow \frac{1}{\alpha} F\left(\frac{s}{\alpha}\right), \text { for } \alpha>0 \\ \text { time-shirting } & f\left(t-t_{o}\right) \longleftrightarrow  e^{-s t_{o}} F(s), \text { for } t_{o}>0 \\ \text { frequency-shifting } & e^{-a t} f(t) \longleftrightarrow F(s+a) \\ \text { convolution } & f * g \longleftrightarrow F \cdot G \\ & \frac{d f}{d t} \longleftrightarrow s F(s)-f\left(0^{-}\right) \\ & f^{(n]} \longleftrightarrow s F(s)-f\left(0^{-}\right) \\ & f^{(n]} \longleftrightarrow s^{n} F(s)-s f\left(0^{-}\right)-\dot{f}\left(0^{-}\right) \\ & 
\int_0^tf(\tau) d \tau \longleftrightarrow \frac{F(s)}{s} \\ \text { frequency-diffferentiation } &(-t)^{n} f(t) \longleftrightarrow \frac{d^{n} F}{d s^{n}} \end{aligned}
$$

### partial functions to solve LTIODEs

stability:
> there are many notions for stability. For LTI system, all notions collaps

here: if free response decrease to zero for all 1/c

H is stable <-> Re{all poles} <0

#### introduce to state space

# the initial value theorem

$$
\lim _{t \rightarrow 0} f(t)=\lim _{s \rightarrow \infty} s F(s)
$$
# the final value theorem
$$
\lim _{t \rightarrow \infty} f(t)=\lim _{s \backslash 0} s F(s)
$$
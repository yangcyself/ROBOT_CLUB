rigid Impace assumptions:
- Impact is instantaneous
- Impact results is no revound/slip
- External ground comtact force can be responsed as impulse
- Actuators cannot generate impules
- impasive forces may result in instaneous change in robot volecity but no instaneous change in configuration

## hybrid Model for walking

The trajectory of state of walking:

一个impulse变化是脚和地面碰撞了，一个continuous变化是碰撞完再回到碰撞前的状态

# Use constraints to solve 
We are going to solve the **new state t+** given the **old state t-**

suppose rigid plastic impact, constraints are:
- the integral version of lagrange function
  - $D(q^+)\dot{q}^+ - D(q-+)\dot{q}^- = F_{ext}$
- the configuration remains
  - q(t^-) = q(t^+)
- the new velocity configuration at stance foot is 0 
  - $J_{c}*\dot{q}(t^+) = 0$
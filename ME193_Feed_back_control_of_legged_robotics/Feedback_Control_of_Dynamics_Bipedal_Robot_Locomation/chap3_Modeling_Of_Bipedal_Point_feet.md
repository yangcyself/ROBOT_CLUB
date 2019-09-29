# CUE
- why point feet?
# what will we model
- point feet
  - consequently, no actuation is possible at the end of the stance leg
  - system is underactuated during single support
- two distinct phase
- ground
  - smooth and perpendicular to the gravitational field
- impacts
  - not compliant and inelastic
  - compliant- nonlinear spring-dampers (tile floor地毯)
  - ONLY ASSUME rigid contact model

## Robot Gait and Impact Hypotheses
- comprisedof N rigidlinks connected by(N−1)idealrevolutejoints (i.e., rigid and frictionless) to form a **single open kinematic chain**; furthermore, each link has nonzero mass and its mass is distributed 
- planar, with motion constrained to the sagittal plane
- bipedal, with two symmetric legs connected at a common point called the hip, and both leg ends are terminated in points
- independently actuated at each of the (N−1) ideal revolute joints; and 
- the model is expressed in N−1 body coordinates qb =( q1;···;qN−1) plus one absolute angular coordinate qN.

**(1) and (2) implies that robots has (N+2)DOF**

### Hypotheses for walking
- alternating phases of single support and double support
- single support phase, the stance leg end acts as an ideal pivot
- double support phase is instantaneous and the associated impact can be modeled as a rigid contact 
-  a timpact, the **swing leg neither slips nor rebounds**, while the **former stance leg releases without interaction** with the ground
-  in steady state, the motion is symmetric with respect to the two legs

### Hypotheses for Running
- three phases : single flight impact
- ideal pivote joint
- the COM travels nonzero distance during flight
- flight terminates with former swing leg end impacting the ground
- the leg end neither slips nor rebounds
- in steady state, the motion over successive single support and ﬂight phases is symmetric with respect to the two legs; 

### Other hypotheses for impact
好多都在前面的假设里面提到了
-  the actuators cannot generate impulses and hence can be ignored during impact
-  the impulsive forces may result in an instantaneous change in the robot’s velocities, but there is no instantaneous change in the conﬁguration

这一个假设可以使用二阶线性系统来解释
$$
\ddot{x}(t)+a \dot{x}(t)+b x(t)=c \delta\left(t-t_{0}\right)
$$
书上就是全挪过去，积了一次分然后说速度是突变的，然后再积了一次分位置不突变。

其实用数分课的知识，系统写成这样，只能是速度突变

### Some remarks on Notation
generalized coordinates for stance $\left(q_{\mathrm{s}} ; \dot{q}_{\mathrm{s}}\right)$.  for flight phase: $\left(q_{\mathrm{f}} ; \dot{q}_{\mathrm{f}}\right)$


# CUE
- what is the general matlab function for optimization?
- what to do if our dynamics cannot have explicit expression of the solution?
# optimization

the matlab function `fmincon`

the nonlinear constraint is another matlabfunction

```matlab
function [cineq,ceq] = cons_simple(x)
% some calculation
[t,x] = ode45(xxxxx)
end
```
> Note, these functions have ode45 inside its body, thus it can express complex dynamics, AMAZING\
> II what is the mechanism of this? How do they get the dirivitive?

# CUE
- when can we use the function dlqr
- what is the difference between controllability and stability?
- why eta=1 bouncing is unstable?
- what is the data type of the matlabfunction `stem?`
  - what is the mechanism?
- why can't the ball return to the target height in one step? even when we have placed the holes to be at zero?
- Will the system under linear controller always converge?


# methedology
having calculated the poincare map,
$$
x_{k+1} = P(x_k+\beta_k)
$$
linearlize and get:
$$
x_{k+1}-x^* = A(x_k-x^n)+B\beta _k
$$

define a linear state feedback

for example: $\beta_k = -K\delta x_k$

where K is get from the matlab function
`K = dlqr(A,B,Q,R)`

we need $|\lambda_i(A-\beta_k)|\lt 1$

## When can we use the function dlqr?
A,B should be stabilizable

**Note:**  the difference between stability and controllability

- **Stability:** 我可以保证所有的eigenvalue都<1，尽管我可能并不能控制所有的eigenvalue
- **controlability:** 我可以控制所有的eigenvalue

# something to clearify
why is bouncing ball model $\eta=1$ unstable?

Because the stability is not about the ability to forever run in a periodic loop, but it has to go back to the loop after some little deviation.

# Example: Ball Bouncing 颠球
a ball, a paddle, assume that each time the ball hit the paddle at height 0, move the paddle(control the velocity of paddle of each collision) to control the height of the ball.
assume $\eta=1$(unstable)

use event based control $\beta = \dot{y_p}$ to control the $y_{apex}$


The matlab program might like this (recovered from my memory)
```matlab
syms yapex dyp; % yapex: y at the apex point, dyp: speed of paddel at collision
syms g;
g_value = 9.8;
y_goal = 1;
dyminus = -sqrt(2*g*yapex);
dyplus = -dyminus+2*dyp;
yapexnew = (dyplus^2)/(2*g);

% see stability when beta(i.e. dyp) is 0
% linearize around the control target
A = subs(jacobian(yapexnew,yapex),[yapex,dyp,g],{y_goal,0,g_value})
A = double(A);
B = subs(jacobian(yapexnew,dyp),[yapex,dyp,g],{y_goal,0,g_value})
B = double(B);
% A = 1, the eigenvalue is 1 means the system is not stable

% AB is controlable

% compute the control gain
K = dlqr(A,B,1,1) % 0.6456
eig(A-B*K) % 0.4167

% K = place(A,B,0.2); % pole placement method
% eig(A-B*K) % 0.2

% K = place(A,B,0.); % pole placement method
% eig(A-B*K) % 0
% have overshoot in true model, recover in one step in linear model

%% simulation
y_vec = 2;
for i=1:10
    [y_vec(i+1)  beta(i)]= poincare_ballBounce(y_vec(i),K);
end
figure; stem(y_vec); title('y_vec');
figure; stem(beta); title('beta_vec');

% function declar has to put at the end
function [y_   dyp]= poincare_ballBounce(yapex,K)
    dyp = -K*(yapex-1);
%     the following expression is generated from command:
    % subs(yapexnew,[g],{g_value}) directly copy and paste
    y_ = (5*(2*dyp + 2^(1/2)*((49*yapex)/5)^(1/2))^2)/98;
end
```
### code high light
- the use of `stem` function, amazing!
  - what type is y_vec? and beta(i)
- some controller functions `dlqr`,  `place`
- function declarations has to put at the end
## discussion
**why can't the ball return to the target height in one step?**

if we use the real model and non-linear controller, we can. But as we linearlized it, we cann't

**Will the system under linear controller always converge?**
no, for example, LQR only converge in the linear system, it may not converge in the non-linear system.
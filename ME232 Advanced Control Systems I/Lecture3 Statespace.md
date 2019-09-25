# CUE
- cramer's rule 行列式法求解方程
- 使用伴随矩阵法求逆
- from state space to classical 
- from classical to state space 

# Cramer's rule
solve $Ax = b$
$$
x_{i}=\frac{\operatorname{det}\left[\mathbf{A}^{(i)}\right]}{\operatorname{det}[\mathbf{A}]}
$$
where $A^{(i)}$ is another n × n matrix formed by replacing the ithcolumn of A with the vector b.

## 我的理解
使用det求得是空间中那堆向量张成的体积（面积）就可以很容易理解，

对于第i列， 这个式子相当于是以所有其它的向量作为底，然后剩下的b与原来的第i跟向量在垂直于基底方向上的比例

# Adjugate matrix
定义
$$
\mathbf{A} \operatorname{adj}(\mathbf{A})=\operatorname{adj}(\mathbf{A}) \mathbf{A}=\operatorname{det}(\mathbf{A}) \mathbf{I}
$$

A矩阵的的逆相当于A的伴随阵除以它的行列式

$$
[s \mathbf{I}-\mathbf{A}]^{-1}=\frac{\operatorname{adj}[s \mathbf{I}-\mathbf{A}]}{\operatorname{det}[s \mathbf{I}-\mathbf{A}]}
$$

## 例
consider a matrix
$$
\mathbf{A}=\left(\begin{array}{lll}{a_{11}} & {a_{12}} & {a_{13}} \\ {a_{21}} & {a_{22}} & {a_{23}} \\ {a_{31}} & {a_{32}} & {a_{33}}\end{array}\right)
$$

the adjecent matrix is :
$$
\left(\begin{array}{cccc}
+\left|\begin{array}{ll}{a_{22}} & {a_{23}} \\ {a_{32}} & {a_{33}}\end{array}\right|& 
-\left|\begin{array}{ll}{a_{12}} & {a_{13}} \\ {a_{32}} & {a_{33}}\end{array}\right|&
{+\left|\begin{array}{cc}{a_{12}} & {a_{13}} \\ {a_{22}} & {a_{23}}\end{array}\right|} \\ 
-\left|\begin{array}{ll}{a_{21}} & {a_{23}} \\ {a_{31}} & {a_{33}}\end{array}\right|&
+\left|\begin{array}{ll}{a_{11}} & {a_{13}} \\ {a_{31}} & {a_{33}}\end{array}\right| &
{-\left|\begin{array}{cc}{a_{11}} & {a_{13}} \\ {a_{21}} & {a_{23}}\end{array}\right|} \\ 
{+\left|\begin{array}{cc}{a_{21}} & {a_{22}} \\ {a_{31}} & {a_{32}}\end{array}\right|} & 
{-\left|\begin{array}{cc}{a_{11}} & {a_{12}} \\ {a_{31}} & {a_{32}}\end{array}\right|} & 
+\left|\begin{array}{ll}{a_{11}} & {a_{12}} \\ {a_{21}} & {a_{22}}\end{array}\right|\end{array}\right)
$$

## 我的理解
同样是使用cramer law的方式理解， adj(A)的第i行相当于是$Ax = \det(A)I_i$的求解

# from state space to classical control
$$
\begin{aligned} s \mathbf{X}(s) &=\mathbf{A} X(s)+\mathbf{B} U(s) \\ \mathbf{Y}(s) &=\mathbf{C X}(s)+\mathbf{D U}(s) \end{aligned}
$$

$$
X_{i}(s)=\frac{\operatorname{det}\left[[s \mathbf{I}-\mathbf{A}]^{(i)}\right]}{\operatorname{det}[s \mathbf{I}-\mathbf{A}]} U(s)
$$

# Transformation from Classical Form to State-Space Representation
$$
\left(a_{n} s^{n}+a_{n-1} s^{n-1}+\cdots+a_{0}\right) Y(s)=\left(b_{n} s^{n}+b_{n-1} s^{n-1}+\cdots+b_{0}\right) U(s)
$$

$$
\left.\left[\begin{array}{c}{\dot{x}_{1}} \\ {\dot{x}_{2}} \\ {\vdots} \\ {\dot{x}_{n-2}} \\ {\dot{x}_{n-1}} \\ {\dot{x}_{n}}\end{array}\right]=\left[\begin{array}{ccccc}{0} & {1} & {\cdots} & {0} & {0} \\ {0} & {0} & {\cdots} & {0} & {0} \\ {\vdots} & {\vdots} & {\ddots} & {\vdots} & {\vdots} \\ {0} & {0} & {\cdots} & {1} & {0} \\ {0} & {0} & {\cdots} & {0} & {1} \\ {-a_{0} / a_{n}} & {-a_{1} / a_{n}} & {\cdots} & {-a_{n-2} / a_{n}} & {-a_{n-1} / a_{n}}\end{array}\right]\left[\begin{array}{c}{x_{1}} \\ {x_{2}} \\ {\vdots} \\ {x_{n-2}} \\ {x_{n-1}} \\ {x_{n}}\end{array}\right]+\begin{array}{c}{0} \\ {0} \\ {\vdots} \\ {0} \\ {0} \\ {1 / a_{n}}\end{array}\right] u\left[\begin{array}{c}{0} \\ {0} \\ {\vdots} \\ {0} \\ {1 / a_{n}}\end{array}\right] u(t)
$$

$$
Y(s)=\left[\left(b_{0}-\frac{b_{n} a_{0}}{a_{n}}\right)\left(b_{1}-\frac{b_{n} a_{1}}{a_{n}}\right) \cdots\left(b_{n-1}-\frac{b_{n} a_{n-1}}{a_{n}}\right)\right]\left[\begin{array}{c}{x_{1}} \\ {x_{2}} \\ {\vdots} \\ {x_{n}}\end{array}\right]+\frac{b_{n}}{a_{n}} u(t)
$$

# The matrix transfer function
$$
\begin{aligned} \mathbf{Y}(s) &=\frac{\mathbf{C} \operatorname{adj}(s \mathbf{I}-\mathbf{A}) \mathbf{B}+\operatorname{det}[s \mathbf{I}-\mathbf{A}] \mathbf{D}}{\operatorname{det}[s \mathbf{I}-\mathbf{A}]} \mathbf{U}(s) \\ &=\mathbf{H}(s) \mathbf{U}(s) \end{aligned}s
$$
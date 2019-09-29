# CUE
- how to use the relabelling matrix
- 从y=h(q)=h0(q)−hd(θ(q))求两次导得到和u的关系
- 拉格朗日方程的几种形式相互导
- 计算 ddot(y)
# Relabelling matrix

consider the following generalized states:

$$ 
q = \left[\begin{array}c \theta_{st} \\ \theta_{sw} \\ \theta_{tor} \end{array}\right] 
$$
$$
x = \left[\begin{array}c q \\ \dot{q} \end{array}\right] 
$$

在转换的时候，理论上来说
$$
x^+ = \Delta(x^-) \quad x\in \mathcal{S}
$$

这里面计算的时候腿是对应原来的腿。

但是注意在踏了一步之后stance foot实际换掉了，所以需要relabel。 这就是relabel matrix

$$
q^+ = \left[\begin{array}c 0&1&0\\1&0&0\\0&0&1 \end{array}\right] \Delta q^-
$$

# virtual constraints
引入: 很久很久以前有通过各种机械原理的constraint

作用出来的效果的形式就是
$$
\left[\begin{array}c q_1 \\ ...\\q_n \end{array}\right]  - 
\left[\begin{array}c h_1(\theta) \\ ...\\h_n(\theta) \end{array}\right] = 0
$$

virtual constraints 就是使用反馈控制去实现constraint的效果

设计一个 angle， 其它的状态都是angle的函数，这样的话比如被推了什么之类的还可以按照原来的轨迹控制只是走路的速度不同而已

$$
y = \left[\begin{array}c q_1 \\ ...\\q_n \end{array}\right]  - 
\left[\begin{array}c h_1(\theta) \\ ...\\h_n(\theta) \end{array}\right] 
$$

## formulas
$q,\dot{q} \in R^n$, $u\in R^m$

We have the dynamic of the system
$$
D(q)\ddot{q}+c(q,\dot{q})\dot{q}+G(q) = B(q)u
$$

- if $\operatorname{rank}(B(q))<n \Rightarrow$ under constrained
- if $\operatorname{rank}(B(q))=n \quad n=m \Rightarrow$ full constrained
- if $\operatorname{rank}(B(q))<n \quad n<m \Rightarrow$ over constrained

writting in matrix form
$$
\dot{x} = \left[\begin{array}c \dot{q}\\\ddot{q} \end{array}\right] = \left[\begin{array}c \dot{q}\\D^{-1}(-c\dot{q}-G) \end{array}\right] + \left[\begin{array}c 0\\D^{-1} B \end{array}\right] u\\
\dot{x} = f(x) +  g(x)u
$$

**virtual constraints**

$y = h(q) = h_0(q) - h^d(\theta(q))$

goal: $y\longrightarrow0$

We can get the derivative

$$
\frac{\partial y }{\partial t } = \frac{dh(x)}{dt} = \frac{\partial h }{\partial x }\dot{x}\\
 = \left[\begin{array}c \frac{\partial h }{\partial q } & \frac{\partial h }{\partial \dot{q} }  \end{array}\right] \left\{f(x)+g(x)u \right\}
$$

注意后面这一项是一个向量，其中前三行是$q$后三行是$\dot{q}$, 所以分块矩阵乘

注意这里面求导是雅可比不是向量导数

then 
$$
\dot{y} = \left[\begin{array}c \frac{\partial h }{\partial q}
& \frac{\partial h }{\partial \dot{q} } \end{array}\right] \left\{ \left[\begin{array}c \dot{q}\\D^{-1}(-c\dot{q}-G) \end{array}\right] + \left[\begin{array}c 0\\D^{-1} B \end{array}\right] u \right\}
$$

becuase that $\frac{\partial h }{\partial \dot{q} } = 0$

thus, this can be written as 

$$
\dot{y} = \left[\begin{array}c \frac{\partial h }{\partial q}
& 0  \end{array}\right] \left[\begin{array}c \dot{q}\\D^{-1}(-c\dot{q}-G) \end{array}\right] + \left[\begin{array}c \frac{\partial h }{\partial q}
& 0  \end{array}\right]\left[\begin{array}c 0\\D^{-1} B \end{array}\right] u 
$$

For simplicity of writting, we can define the part before and after $+$ to be $L_fh(x)$ and $L_gh(x)$

thus 
$$
\dot{y} = L_fh(x) + L_gh(x)u
$$

this is called (没听清楚) "lie derivative"

because of all the zeros, we get.
$$
\dot{y} = \frac{\partial h }{\partial q }\dot{q}
$$

我们第一次求导是因为$y$的表达是里面没有$u$，所以不好直接控制。 现在一看，仍然没有$u$， 所以只能**继续求导**

如法炮制
$$
\ddot{y} = \frac{\partial \dot{y}}{\partial x}\dot{x}
$$
注意这里面仍然是对$x$求的偏导，而不是$\dot{x}$

这样就有了
$$
\ddot{y} = \left[\begin{array}c \frac{\partial  }{\partial q }(\dot{y}) & -\frac{\partial  }{\partial \dot{q} }(\dot{y}) \end{array}\right]\left\{f(x)+g(x)u \right\}
$$

thus 
$$
\ddot{y} = \frac{\partial  }{\partial x }L_fh(x) f(x) + \frac{\partial  }{\partial x }L_fh(x)g(x)u
$$

$$
\ddot{y} = L_fL_fh(x) + L_gL_fh(x)u
$$


## what we do to control?
design $u$ such that we have the form
$$
\ddot{y} = -K_py - K_d\dot{y}, \quad K_p, K_d >0
$$

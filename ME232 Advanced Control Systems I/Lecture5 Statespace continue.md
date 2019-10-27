# CUE
- Algebra of transfer function
  - feedback 
  - parallel
  - seriel
- controllable canonical form
  - how to derive it
  - how to construct multi-in multi-out 
  - what insight can be seen from the matrix of canonical form
- transfer function reduction
  - the process
  - $\frac{C_1(S+\sigma)+C_2}{(s+\sigma)^2+w^2}$ 如何转化
- discrete time的公式来一套
- toeplitz matrix
  - what is this 
  - How is its structure related to its properties
- Markov parameters
  - How to derive this?
  - How to do expansion of $(zI-A)^{-1}$
  - what does this stand for
# Some Review
## algebra of transfer function

### feedback
u->p->y\
y->k->u
$$
\dot{\left[\begin{array}c x_p\\x_k \end{array}\right] } = \left[\begin{array}c A_p&B_pC_k\\K_kC_p & Bp \end{array}\right] \left[\begin{array}c x_p \\ x_k \end{array}\right] + \left[\begin{array}c B_p\\0 \end{array}\right]  u
$$

### 并联
u->p1->y
u->p2->y

$$
\dot{\left[\begin{array}c x_{p1} \\ x_{p2} \end{array}\right] } = \left[\begin{array}c Ap_1 &0 \\0& Ap_2     \end{array}\right] \left[\begin{array}c x_{p1} \\ x_{p2} \end{array}\right] + \left[\begin{array}c B_{p1}\\B_{p2} \end{array}\right]  u
$$


### 串联
u->p1->p2->y
太简单不打字了

## derive contrallable canonical form
术语叫做"realization of controlable carnonical form"

suppose 
$$
H(s) = \frac{b_{n-1}s^{n-1}+...+b_0}{s^n+a_{n-1}s^{n-1}+...+a_{1}s+a_0}
$$
$$
A = \left[\begin{array}c 
0&1&0&...&0\\
0&0&1&...&0\\
...&...&...&...&...\\
0&0&0&...&1\\
-a_0&-a_1&-a_2&...&-a_{n-1}\\  \end{array}\right] 
$$

$$
B = \left[\begin{array}c 0\\0\\....\\1 \end{array}\right]
$$

$$
C = \left[\begin{array}c b_0& b_1 &...&b_{n-1} \end{array}\right] 
$$

### Multi-input multi-output
如果是一个multi in multi out的系统，比如
$$
H(s) = \left[\begin{array}c \frac{2}{s+3}&\frac{10s}{s^2+3s+4}\\0&\frac{1}{s} \end{array}\right] 
$$

得到整个的转换方程，的思路是:
1. 单独寻找carnonical form
2. side by side (多输入单输出)) construction
3. One above another (单输入多输出)) construction

# model reduction
上面的方法理论上可行，但是如果我从那样的一个矩阵中看不出什么东西

state之间可能有redundancy，如果只是把每个转换方程的state叠起来，那么很庞大
>complexity of the controller is equal to the complexity of states in model

>NASA的一个太空机械臂，80feet long，这么长一定会震动，这个震动使用有限元建模，上千个state

## 方法: "mode" form
因为有（可自己验证$C(sI-A)^{-1}B$（我还没验证过)）
$$
\frac{C_1(S+\sigma)+C_2}{(s+\sigma)^2+w^2} \Rightarrow \left[\begin{array}c -\sigma & w & 1\\ w & -\sigma & 0 \\ c_1 & c_2 & 0 \end{array}\right] 
$$

所以方法是
1. partial fraction
2. term by term realization
3. realize by ....(没记清)

总之最后得到的东西虽然还是在一个矩阵里面，但是状态其实是（每个对应的分式）相互独立的

比如像这样
$$
\left[\begin{array}c 
-p_1&& &&\\
 &-p & 1&&\\
 &1 & -p &&\\
 &&&-\sigma & w\\
 &&&w & -\sigma
 \end{array}\right] 
$$

其他位置都是0

这样你一看，哦，右下角这个形式是震荡

# To discrete time
**Totally same formulation**

只不过是把左式的导数变成下一个时刻的状态


## toeplitz matrix

$$
\left[\begin{array}c x_0 \\x_1 \\x_2\\ .... \end{array}\right]
=
\left[\begin{array}c 0&0&0&0&...\\
B&0&0&0&...\\
AB&B&0&0&...\\
A^2B&AB&B&0&...\\
.... \end{array}\right]  
\left[\begin{array}c u_0\\0\\0\\0\\... \end{array}\right] 
+
\left[\begin{array}c I \\A\\A^2\\....\\... \end{array}\right] x_0
$$

加号左边force response 加号右边 free response

这个矩阵的形式可以看出性质
- **lower triangular** -> causal
- **toeplitz** -> time invariant


$$
\left[\begin{array}c y_0 \\y_1 \\y_2\\ .... \end{array}\right]
=
\left[\begin{array}c D&0&0&0&...\\
CB&D&0&0&...\\
CAB&CB&D&0&...\\
CA^2B&CAB&CB&D&...\\
.... \end{array}\right]  
\left[\begin{array}c u_0\\0\\0\\0\\... \end{array}\right] 
+
\left[\begin{array}c I \\A\\A^2\\....\\... \end{array}\right] x_0
$$

## Markov parameters

### expension of matrix inverse
$$
(zI-A)^{-1} = z^{-1} + z^{-2}A+ z^{-3}A^2 + ... 
$$
注意上面这个式子和控制无关，只是数学性质

#### 证
$$
(zI-A)(z^{-1} + z^{-2}A+ z^{-3}A^2 + ... ) = .... I
$$

thus

$$
C(zI-A)^{-1}B+D = D + z^{-1}CB + z^{-2}CAB + ... \\
=H_0 + H_1z^{-1} + H_2z^{-2} + ...
$$

these H are called Markov parameters

带入上面的矩阵方程

可以从上面的矩阵看出来， **markov parameters are just the impulse response**

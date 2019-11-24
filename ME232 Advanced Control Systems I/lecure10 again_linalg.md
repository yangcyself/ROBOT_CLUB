# CUE
- prove R(AA*) = R(A)
- Prove Multiply by an invertible matrix T doesn't change rk
- Similar matrix
  - explain the *abstracted matrix* and *concrete matrix*
  - When we choose the transformation T matrix from C frame to B frame, why we have BT = C, where we are left multiplying the matrix
  - So how to compute A^(c) from A^(b) given the transition matrix from c to b


# NEWS:
> 老师原来MIT的跟奥本海姆，他们35个phd，导师说咱们秋天开一个小时的会，春天开一个小时的会。 
> 他上了一年MIT之后去了Florida， 那里有卡尔曼以及...., ...., ..., 等等的人, 只有两个PHD， 还有一个drop了
> "you should learn linalg", "I learned at MIT", "then you don't know linalg", 出了一道题 "you see, you don't know linalg"

## foundamental theorems

$$
\mathcal{R}({AA^*}) = \mathcal{R}({A})
$$

my proof
$$
v\in \mathcal{R}(AA^*)\\
v \perp \mathcal{N}(A^*)\\
v \perp \mathcal{N}(AA^*)
v\in \mathcal{R}(AA^*) (\text{this is because }(AA^*)^* = (AA^*))
$$

The Professors' proof

let $v\in \mathcal{R}(A)$

From b: 
$$
\mathbb{C}^m = \mathcal{R}(AA^*)+\mathcal{N}(AA^*)\\
\text{decompose v into } v = s+t\\
s = \mathcal{R}(AA^*)\quad t= \mathcal{N}(AA^*)
$$

$$
v - s = t\\
v - s  \in \mathcal{R}(A)\\
t \in \mathcal{R}^\perp(A)
$$

## Rank and Nullity

### Multiply by an invertible matrix $T$ doesn't change rk
**Proof**

$$
rank(AT) \leq rank(A) = rank(ATT^{-1}) \leq rank(AT)
$$

### $rank(AB) \leq rank(A)$, $rank(AB) \leq rank(B)$
easy to understand, when considering the boxes

## Nilpotent
$$
\exist k \quad A^k = 0
$$

for example
$$
A = \left[\begin{array}c 0 & 1& 0& 0 \\ 0 & 0& 1& 0\\ 0 & 0& 0& 1\\ 0 & 0& 0& 0\end{array}\right] 
$$

## Similar matrix

In general, your law of motion should not depend on coordinate, we suppose an Abstract matrix $\mathcal{A}$

When we choose a basis, we get a concrete matrix $A$

>我们想象世间万物的线性变化，用一个矩阵表示, 但是如果我们选择不同的基的话，矩阵是不一样的，但是我们应该想到那背后的 abstracted matrix 是一样的

### change of basis

（不知道标准的表示法什么样。。。）
$$
[b_1,b_2,b_3] x^{(b)} = [c_1,c_2,c_3] x^{(c)}
$$

其中 $[b_1,b_2,b_3], [c_1,c_2,c_3]$ 是$c$ 和$b$的基。$x^{(b)}, x^{(c)}$ 代表在b坐标系和c坐标系的坐标

这样就有

$$
[b_1,b_2,b_3] ^bT_c x^{(c)} = [c_1,c_2,c_3] x^{(c)}
$$

### similar matrix

We have abstracted matrix $\mathcal{A}$

we transform in B coordinate: $y^{(b)} \leftarrow A \leftarrow x^{(b)}$

We transform from c coordinate, change into b coordinate, use A and change back.

$$
y^{(c)} \leftarrow T^{-1}   \leftarrow y^{(b)} \leftarrow A \leftarrow x^{(b)} \leftarrow T \leftarrow x^{(c)}
$$

thus 
$$
A^{(c)} = (^bT_c)^{-1}A^b(^bT_c)
$$

> **Note:** all of these are my own notation, I don't know the right notation for these.


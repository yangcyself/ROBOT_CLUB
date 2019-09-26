
## Z transform properties

**linearity**


**delay**
$Df = \frac{1}{z}F-zf_0$

**frequancy diff**
$kf_k <-> -z\frac{dF}{dz}$

$f \times g <-> FG$


$$
\begin{array}{ll}{\text { Let } f \longleftrightarrow F, g \longleftrightarrow G, \alpha \in \mathbb{R}} \\ {\qquad \begin{aligned} \text { lincarity } & \alpha f \longleftrightarrow \alpha F, \quad f+g \longleftrightarrow F+G \\ \text { delay } & D f \longleftrightarrow z^{-1} F(z) \\ \text { delay } & D^{n} f \longleftrightarrow z^{-n} F(z) \\ & D^{-1} f \end{aligned}-z^{-n} F(z)} \\ {\text { advance }} & {D^{-2} f_{f} \longleftrightarrow z F(z)-z f_{0}} \\ {} & {D^{-2} f_{f} \longleftrightarrow z^{2} F(z)-z^{2} f_{0}-z f_{1}} \\ {} & {D^{k} f_{k} \longleftrightarrow z^{2} F(z)-z^{2} f_{0}-z f_{1}} \\ {\text { freq-scaling }} & {a^{k} f_{k} \longleftrightarrow F(z / a)} \\ {\text { convolution }} & {f * g \longleftrightarrow F \cdot G}\end{array}
$$

**When soling partial functions, work with $z^{-1}$**

# CUE:
- terminology
  - $\pi_\theta(a_t|o_t)$ 与 $\pi_\theta(a_t|s_t)$
- behavior cloning will NOT work（原理）
- behavior cloning can work (例子)
- DAgger
- 如何更好的fit 有两个因素可能考虑
  - Non markov behavior
    - 加RNN的问题
  - Multimodal behavior   
    - 三个解决办法

# some terminology
$\pi_\theta(a_t|o_t)$: o is the observation

$\pi_\theta(a_t|s_t)$: s is the state: means fully observed. Common in optimal control.

## discuss behavior cloning
behavior cloning 的描述就是一个神经网络，使用监督学习的方式训练它，什么样的输入的时候该有什么样的输出。一般是按照专家的轨迹，统计输入输出，然后训练。
### behavior cloning will NOT work
因为"mistakes can get compound", 模型的一点小小的误差导致模型到了一个自己之前没有学过的状态，后面越来越糟

### behavior cloning can work
英伟达的一个工作，车头上面摆了三个摄像头，拍驾驶员的正常行驶轨迹。 所有左边摄像头的图片标上右转的动作label

这个使用数学严格描述就是
用$p_{data}(o_t)$来训练$\pi_\theta(a_t|o_t)$
但是$p_{data}(o_t)$和$p_{\pi}(o_t)$分布不一样

### 如何解决？DAgger
1. behaviro cloning
2. run $\pi_\theta$ to get dataset 
3. Ask human to label new dataset
   1. what will you do if you see this
4. merge the train dataset

### 如何更好的fit
有两个因素可能考虑
- Non markov behavior
- Multimodal behavior

## How do we use history in models 
加RNN
### why historicall models work poorly in behavior cloning

因为模型可以找到联系，但是很难判断 the way the causality goes

比如汽车的摄像头信息里有自己的转向灯，那么很有可能学到当我的左转向灯亮的时候我要左转

有了history问题更严重。

## multimodal behavior
问题，比如神经网络输出一个高斯分布，但是有时专家的行为需要多个高斯才能拟合，要么左要么右，中间就撞墙了

解决办法:
- build一个神经网络可以输出多个（固定）高斯的信息
- latent variable models
  - 类似VAE
  - 阅读:
    - VAE
    - Normalizing flow/realNVP
    - stein variational gradient descent
- autoregressive disretization
  - 离散化，使用离散的bin来代表分布
  - 为了防止curse of dim, 使用一串网络, 第一个仅对第一个维度离散化， 然后在离散化里面的第一个维度进行采样，再经过第二个维度的离散化网络




课件和内容均来自于台湾大学李宏毅老师

[课程链接](https://www.youtube.com/watch?v=ibJpTrp5mcE)

![图1](https://github.com/Gakk1Fan/DeepLearning/blob/main/%E5%8F%8D%E5%90%91%E4%BC%A0%E6%92%AD/images/%E5%9B%BE1.png)

![图2](https://github.com/Gakk1Fan/DeepLearning/blob/main/%E5%8F%8D%E5%90%91%E4%BC%A0%E6%92%AD/images/%E5%9B%BE2.png)



其中$\frac{\partial z}{\partial w}$是很容易求出来的，比如$\frac{\partial z}{\partial w1}=x_1$,$\frac{\partial z}{\partial w2}=x_2$

难点在于如何算出$\frac{\partial C}{\partial z}$



以下是更多Forward pass的例子

![图3](https://github.com/Gakk1Fan/DeepLearning/blob/main/%E5%8F%8D%E5%90%91%E4%BC%A0%E6%92%AD/images/%E5%9B%BE3.png)



下面来看看Backward pass

![图4](https://github.com/Gakk1Fan/DeepLearning/blob/main/%E5%8F%8D%E5%90%91%E4%BC%A0%E6%92%AD/images/%E5%9B%BE4.png)

其中$a = \sigma(z)$，所以$\frac{\partial a}{\partial z} = \sigma'(z)$

这里我们假设如果$\frac{\partial C}{\partial z'}$和$\frac{\partial C}{\partial z''}$算出来了

![图5](https://github.com/Gakk1Fan/DeepLearning/blob/main/%E5%8F%8D%E5%90%91%E4%BC%A0%E6%92%AD/images/%E5%9B%BE5.png)

问题就转换成为如何计算$\frac{\partial C}{\partial z'}$和$\frac{\partial C}{\partial z''}$

这里的$\sigma'(z)$其实是一个常数，在forward pass的时候，$z=w_1x_1+w_2x_2+b$，其中$w_1, x_1, w_2, x_2, b$都是已知的



**计算$\frac{\partial C}{\partial z'}$和$\frac{\partial C}{\partial z''}$**

**Case1**：$\frac{\partial C}{\partial z'}$和$\frac{\partial C}{\partial z''}$是Output Layer

![图6](https://github.com/Gakk1Fan/DeepLearning/blob/main/%E5%8F%8D%E5%90%91%E4%BC%A0%E6%92%AD/images/%E5%9B%BE6.png)



**Case2**:$\frac{\partial C}{\partial z'}$和$\frac{\partial C}{\partial z''}$不是Output Layer

![图7](https://github.com/Gakk1Fan/DeepLearning/blob/main/%E5%8F%8D%E5%90%91%E4%BC%A0%E6%92%AD/images/%E5%9B%BE7.png)

从Output Layer从前往后开始算





**Backward pass**：建立一个反向的神经网络

![图8](https://github.com/Gakk1Fan/DeepLearning/blob/main/%E5%8F%8D%E5%90%91%E4%BC%A0%E6%92%AD/images/%E5%9B%BE8.png)

![图9](https://github.com/Gakk1Fan/DeepLearning/blob/main/%E5%8F%8D%E5%90%91%E4%BC%A0%E6%92%AD/images/%E5%9B%BE9.png)

**总结**

从Forward Pass中算出$\frac{\partial z}{\partial w}$

从Backward Pass中算出$\frac{\partial C}{\partial z}$

最终算出$\frac{\partial C}{\partial w}$




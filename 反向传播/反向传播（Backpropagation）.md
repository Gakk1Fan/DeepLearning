课件和内容均来自于台湾大学李宏毅老师

[课程链接](https://www.youtube.com/watch?v=ibJpTrp5mcE)

![image-20220130205309131](/Users/shisanyue/Library/Application Support/typora-user-images/image-20220130205309131.png)

![image-20220130205705255](/Users/shisanyue/Library/Application Support/typora-user-images/image-20220130205705255.png)



其中$\frac{\partial z}{\partial w}$是很容易求出来的，比如$\frac{\partial z}{\partial w1}=x_1$,$\frac{\partial z}{\partial w2}=x_2$

难点在于如何算出$\frac{\partial C}{\partial z}$



以下是更多Forward pass的例子

![image-20220130211407626](/Users/shisanyue/Library/Application Support/typora-user-images/image-20220130211407626.png)



下面来看看Backward pass

![image-20220130212447886](/Users/shisanyue/Library/Application Support/typora-user-images/image-20220130212447886.png)

其中$a = \sigma(z)$，所以$\frac{\partial a}{\partial z} = \sigma'(z)$

这里我们假设如果$\frac{\partial C}{\partial z'}$和$\frac{\partial C}{\partial z''}$算出来了

![image-20220130213019995](/Users/shisanyue/Library/Application Support/typora-user-images/image-20220130213019995.png)

问题就转换成为如何计算$\frac{\partial C}{\partial z'}$和$\frac{\partial C}{\partial z''}$

这里的$\sigma'(z)$其实是一个常数，在forward pass的时候，$z=w_1x_1+w_2x_2+b$，其中$w_1, x_1, w_2, x_2, b$都是已知的



**计算$\frac{\partial C}{\partial z'}$和$\frac{\partial C}{\partial z''}$**

**Case1**：$\frac{\partial C}{\partial z'}$和$\frac{\partial C}{\partial z''}$是Output Layer

![image-20220130233918380](/Users/shisanyue/Library/Application Support/typora-user-images/image-20220130233918380.png)



**Case2**:$\frac{\partial C}{\partial z'}$和$\frac{\partial C}{\partial z''}$不是Output Layer

![image-20220130234517476](/Users/shisanyue/Library/Application Support/typora-user-images/image-20220130234517476.png)

从Output Layer从前往后开始算





**Backward pass**：建立一个反向的神经网络

![image-20220130234810471](/Users/shisanyue/Library/Application Support/typora-user-images/image-20220130234810471.png)

![image-20220130235038349](/Users/shisanyue/Library/Application Support/typora-user-images/image-20220130235038349.png)

**总结**

从Forward Pass中算出$\frac{\partial z}{\partial w}$

从Backward Pass中算出$\frac{\partial C}{\partial z}$

最终算出$\frac{\partial C}{\partial w}$




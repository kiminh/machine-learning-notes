# 深度学习是怎么做特征交叉的

* [返回上层目录](../tips.md)





如果把sogmoid看成是简单的sigmoid(x)=x+x^2，仅仅凭借非线性激活函数的一阶项和二阶项通过多层就已经能起到了高阶特征交叉的作用。


$$
\sigma(w_{11}\sigma(w_{11}x_1+w_{12}x_2)+w_{21}\sigma(w_{21}x_1+w_{22}x_2))\\
\approx\sigma(\sigma(x_1+x_2)+\sigma(x_1+x_2))\\
\approx\sigma((x_1+x_2)+(x_1+x_2)^2)\ \ \  \sigma(x)=x+x^2\\
\approx\sigma(x_1+x_2+x_1^2+x_2^2+x_1x_2)\ \ \  \sigma(x)=x+x^2\\
\approx(x_1+x_2+x_1^2+x_2^2+x_1x_2)+(x_1+x_2+x_1^2+x_2^2+x_1x_2)^2\\
\approx(x_1+x_2+x_1^2+x_2^2+x_1x_2+x_1^3+x_2^3+x_1^2x_2+x_1x_2^2+x_1^4+x_2^4+x_1^2x_2^2+x_1^3x_2+x_1x_2^3)
$$


这样推导很清晰，有个问题，如果激活函数是relu的话该怎么推导呢？

是不是relu可以近似看成是exp函数，你看relu的函数图像不就有点像exp吗。严格地猜测的话，如果relu可导的话，那它的泰勒展开里，可能应该还是会有x和x^2项的，并且高阶项会有衰减，不然会指数增长的

靠relu可以实现分段线性，增加神经元个数就能增加relu拟合曲线的平化程度





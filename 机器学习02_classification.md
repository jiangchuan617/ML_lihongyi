# 机器学习02

## 1.Classification

1. 将分类当做回归来做，正类 label=1，负类label=-1

   - 缺点：

     ![image-20190414191612188](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190414191612188.png)

2. 基本思路

   ![image-20190414191757949](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190414191757949.png)

   



3. generative model 

   ​	![image-20190414192406995](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190414192406995.png)

   - 贝叶斯公式

   - 如何估计$P(x|C1)\rightarrow$ 极大似然估计

     ​	![image-20190414204505903](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190414204505903.png)

     ![image-20190414204532849](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190414204532849.png)

     ![image-20190414204620440](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190414204620440.png)

     ![image-20190414204738340](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190414204738340.png)

     

     ![image-20190414204957738](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190414204957738.png)

     

   - 实际效果并不好，做改进：公用一个协方差矩阵

     ![image-20190414205645128](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190414205645128.png)

   - 效果

     ![image-20190414205849481](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190414205849481.png)

     - 公用协方差矩阵，变成线性模型

   - 步骤

     ![image-20190414210359279](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190414210359279.png)

   - 为什么Gaussian 分布

     - 看实际情况，二值分类可以用伯努利分布

       ![image-20190414210943470](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190414210943470.png)

   - 后验概率

     ​	![image-20190414211115697](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190414211115697.png)

     ------

     ![image-20190414211238569](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190414211238569.png)

     ------

     ![image-20190414211321062](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190414211321062.png)

     ------

     ![image-20190414211702659](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190414211702659.png)

     ------

     ![image-20190414212056576](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190414212056576.png)

     ------

4. logistic regression(判别式方法 )

   1. 基础

      ​	![image-20190415093038745](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190415093038745.png)

      ------

      ![image-20190415093321940](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190415093321940.png)

      ------

      ![image-20190415093531381](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190415093531381.png)

      ------

      ![image-20190415094109494](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190415094109494.png)

      ------

      ![image-20190415094326179](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190415094326179.png)

      ------

      ![image-20190415094730057](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190415094730057.png)

      ------

      ![image-20190415094931930](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190415094931930.png)

      ------

      ![image-20190415095121850](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190415095121850.png)

      ------

      ![image-20190415095152047](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190415095152047.png)

      - 为什么逻辑回归不能用Square Error 做loss function

      ![image-20190415095540449](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190415095540449.png)

      ------

      ![image-20190415095735382](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190415095735382.png)

      - 解释：随机初始值，可能一开始距离最小值很远，但是这个时候的梯度很小，学习速度很慢；但是又不能调整学习率，因为也有可能初始值就接近最小值，此时的梯度也很小，增大学习率会无法收敛。

   2. 判别式模型和生成式模型

      ​	![image-20190415100904152](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190415100904152.png)

      - 生成式模型对采样概率做了假设(gaussain或者伯努利)，判别式模型没有做假设
      - 二者求出来的参数应该不一样。

      ![image-20190415101139629](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190415101139629.png)

      - 有人说，判别式模型一般比生成式要好
      -  例子如下

      ![image-20190415101352260](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190415101352260.png)

      ------

      ![image-20190415101525656](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190415101525656.png)

      ------

      ![image-20190415101641559](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190415101641559.png)

      ------

      ![image-20190415102024875](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190415102024875.png)

      ------

5. 多分类

   ![image-20190415102308733](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190415102308733.png)

   

   ------

   ![image-20190415102631476](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190415102631476.png)

6. logistic Regression 的限制

   ![image-20190415103011879](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190415103011879.png)

   ![image-20190415103041282](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190415103041282.png)

   1. 改进feature transformation

      ![image-20190415103244951](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190415103244951.png)

      ------

      ![image-20190415103450843](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190415103450843.png)

       

      ------

      ![image-20190415103800791](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190415103800791.png)

      ------

      ![image-20190415103818610](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190415103818610.png)

      
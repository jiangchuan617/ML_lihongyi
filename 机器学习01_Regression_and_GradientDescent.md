# 机器学习

## 1.机器学习介绍

1. 机器学习分为监督学习、半监督学习和非监督学习
   - 监督学习
     - 回归
     - 分类
       - 线性模型
       - 非线性模型
         - deep learning
         - Svm, decesion tree,KNN
     - 
     - 结构学习
   - 半监督学习
   - 迁移学习
   - 强化学习

## 2.regression

1. 回归的输出是一个数值scalar 

2. 步骤

   1. 找model(function set{$f_1,f_2,...f_n$})

      - linear model
        $$
        y = b + \sum w_i*x_i\\
        x_i:feature\\
        w_i:weight, b:bias
        $$

   2. 评价function的好坏

      - loss function L

        ​	$ L(f) = L(w,b)$

   3. 挑选最好的function(loss function 最小的)
      $$
      f^* = arg\min_{f} L(f)\\
      w^*,b^* = arg\min_{w,b}L(w,b)
      $$

      - gradient descent

        - **梯度：是一个矢量，其方向上的方向导数最大，其大小正好是此最大方向导数** 

          ![image-20190411174925963](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190411174925963.png)

      - 过拟合overfiting和欠拟合underfiting

        - 正则化regularization
          - 尽可能使weights接近0，是的当特征x变化时，loss functuin变化小。
          - lossfunction更加平滑，如果输入有噪声干扰，那么平滑的function 干扰更少
          - $\lambda$ 越大，loss function 越少考虑训练误差
          - **偏向于较平滑的loss function，但不能太平滑**
          - 不需要考虑bias,因为bias不影响平滑程度

        - Loss error的来源

          ​	

          ​	![image-20190412092934409](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190412092934409.png)

          

          - 来自bias

            ​	![image-20190412093452540](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190412093452540.png)

            - 直观解释：简单的模型(function set)区域范围sapce较小，可能不会包裹真正的中心target， 所以无论怎么采样，平均都不可能是target;复杂的模型space较大，可能包含target，虽然可能每次都不一样，但是只要在target附近，平均可能就靠近target。
            - 

            

          - 来自Variance

            ​	![image-20190412093115448](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190412093115448.png)

            

            - 越简单的model，越集中，收到data的影响越小，var越小

          - 结论

            ![image-20190412094206167](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190412094206167.png)

            1. bias大，underfiting，训练集效果不好
            2. variance大，overfiting，训练集效果好，但是测试集效果不好
            3. 改进办法
               1. bias大,增加特征，增加模型复杂度
               2. variance大，增加数据量，正则化(实际上在bias和variance取得平衡)
               3. cross validation(n-fold)

## 3. Gradient Descent

1. 基本介绍
   $$
   \nabla L(\theta) = \left[
    \begin{matrix}
      \frac{\partial L(\theta)}{\partial\theta_0}\\
      ... \\
      \frac{\partial L(\theta)}{\partial\theta_n}
     \end{matrix}
     \right] \tag{3}\\
   \theta\leftarrow\theta-\eta\nabla L(\theta)
   $$

   - Gradient方向：loss的等高线的法线方向

     ![image-20190412105146472](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190412105146472.png)

2. 学习率的调整(tune learning rate)

   1. 自适应调节

      ​	随着迭代次数(epoch)增加，减小learning rate
      $$
      \eta = \frac{\eta}{\sqrt{t+1}}
      $$
      ​	

   2. adagrd

      ![image-20190412120144883](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190412120144883.png)

      ![image-20190412120212124](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190412120212124.png)

      ![image-20190412120352929](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190412120352929.png)

      ![image-20190412120449216](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190412120449216.png)

      ![image-20190412121424260](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190412121424260.png)

3. Stochastic Gradient Descent

   ​	![image-20190412141932738](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190412141932738.png)

   ![image-20190412142203209](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190412142203209.png)

   - 优势：快

4. feature scaleing

   ​	![image-20190412142723528](/Users/jiangfeng/Library/Application Support/typora-user-images/image-20190412142723528.png)

   - 左边，不同的参数需要不同的学习率；
   - 梯度方向并不是指向最低点，是顺着等高线方向，右边梯度就向着圆心走

   

   
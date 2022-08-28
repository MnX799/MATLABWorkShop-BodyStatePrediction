# Repo: 体态分类预测

shelley.lu@sjtu.edu.cn 陆心怡

## 1.数据源

许老师的采样数据，五种运动状态：sitting(0), standing(1), walking(2), walkingdownstair(3), walkingupstair(4),括号内为训练所用标记。

<img src="C:\Users\13169\AppData\Roaming\Typora\typora-user-images\image-20220716101143910.png" alt="image-20220716101143910" style="zoom:70%;" />

## 2.特征选取

源数据包括加速度、角速度、方向、位置、磁场。经简单观察，加速度数据的区分度较大，故选取之。预处理后的数据文件**Accdata.mat**。

## 3.实验过程及结果

5折交叉验证，将Accdata数据划分为：训练95%-测试5%

加速度数据：X Y Z（由于时间因素未进一步提取特征）

训练的模型及参数如下：

<img src="C:\Users\13169\AppData\Roaming\Typora\typora-user-images\image-20220713102918497.png" alt="image-20220713102918497" style="zoom: 80%;" />

<img src="C:\Users\13169\AppData\Roaming\Typora\typora-user-images\image-20220713103059218.png" alt="image-20220713103059218" style="zoom:80%;" />

<img src="C:\Users\13169\AppData\Roaming\Typora\typora-user-images\image-20220713102509791.png" alt="image-20220713102509791" style="zoom:80%;" />

**准确度最高top3：**

| 模型        | 验证准确率 | 测试准确率 |
| ----------- | ---------- | ---------- |
| 精细高斯SVM | 84.2%      | 84.5%      |
| 可优化集成  | 83.1%      | 84.8%      |
| 神经网络    | 84.6%      | 83.9%      |

**混淆矩阵：**

精细高斯SVM

<img src="C:\Users\13169\AppData\Roaming\Typora\typora-user-images\image-20220714090953086.png" alt="image-20220714090953086" style="zoom: 67%;" />

可优化集成

<img src="C:\Users\13169\AppData\Roaming\Typora\typora-user-images\image-20220714091402181.png" alt="image-20220714091402181" style="zoom: 67%;" />

神经网络

<img src="C:\Users\13169\AppData\Roaming\Typora\typora-user-images\image-20220714094006030.png" alt="image-20220714094006030" style="zoom: 67%;" />



## 4.待改进项

在训练神经网络模型时，发现增加神经元数对表现提升有效，且宽神经网络表现不错，故若进一步训练可以往这些方向调整参数。

增加选取数据的维度，如增加选取方向数据，进行特征提取，或许可以进一步提升识别准确度。



## 5.模型文件

精细高斯SVM：**SVM.mat**

可优化集成：**bagging.mat**

神经网络：**NN.mat**

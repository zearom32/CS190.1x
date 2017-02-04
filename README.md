一年前我就看过CS190.1x了，这次终于写完了几个主要的Lab。

这个课程主要使用Spark的Python接口，对Spark的工程细节并不关心，而是用Linear Regression，Logistic Regression和PCA这几种常用算法来让人熟悉Spark应用。Spark基本屏蔽了底层分布式计算的细节，用户可以流畅地操作RDD而不必关心数据到底怎么scatter和reduce。虽然是用的Python接口，但是map和reduce的操作方式还是很容易让我感受到Spark需要用Scala来实现。

## Lab3
Linear Regression
Lab3 主要是实现一个Linear Regression。Linear Regression是有闭式解的，但在参数很多的情况下，无法计算闭式解。Gradient Descent是一个合适的方法，因为它能够分布式地计算gradient，而且对线性模型能够保证收敛到最优解。

## Lab4
Lab4 是一个CTR预测问题。
Lab 4 主要包括一下内容：

* one-hot encoding
* reduce feature dim via feature hashing

OHE 使用了SparseVector存储，这是一个稀疏的向量。为了进一步减少特征维度（sparse），使用hash函数进行sparse。

虽然是CTR预测，但是Lab的主要部分还是在于预处理数据，提取特征，和CTR关系不大。

## Lab5
Lab5 主要实现了PCA。

PCA是一种常用的降维方法，熟悉PCA算法的同学应该感觉这个Lab不难。
这里计算协方差矩阵的时候用到了np.outer, 外积在这里是为了分布式的计算矩阵乘法。

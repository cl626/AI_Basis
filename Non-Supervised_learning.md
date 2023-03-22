##### Preface

1. 无监督学习有聚类，降维，用于数据分析/监督学习的前处理

![image-20230322105836591](https://raw.githubusercontent.com/cl626/Image/master/Picgo/image-20230322105836591.png)

2. 监督学习的方法→层次聚类+k均值聚类
3. SVD用于LSA,SVD用于PCA

##### LSA

...

4. LSA👉PLSA，EM用于PLSA👉==隐Markov model==

* 以p(z|x)、p(y|x)为参量，单词-文本的出现次数为因变量，对数似然估计，数值解

5. 图的随机游走就是条件随机场吗？什么是PageRank

* 普通的markov模型，(p1,...,pk)^n+1^=(p1,...,pk)^n^·A → 特征值分解后，类似裂项相消
* 平稳分布的充要性？非周期，不可约

##### Stochastic P review

![image-20230322115814394](../../Users/c1826/AppData/Roaming/Typora/typora-user-images/image-20230322115814394.png)

* 问题与Improve——随机图上马尔科夫链未必具有平稳分布

​	==？==添加一个等概率因子就可以避免

* 什么是迭代计算→==名字==，什么是代数计算👉==R=dMR+$\frac {1-d}n \vec1$==
* R模型已定，如果让我门估计，未知数为参量，用对数似然或平方为损失函数，梯度下降极值得估计

##### SVD的性质



6. 我们的终极Boss👉LDA


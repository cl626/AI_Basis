* 我只是简单的记忆，需要理解吗，怎样才算理解？

* 其中的数学原理有哪些？

* 主要是建模，估计的方法，如何优化估计
  1. 凸优化求最小值：拟牛顿法，？，最大熵
  2. EM表示，转为凸优化
  
* Model：如何把想法转化为可度量的公式

  函数来表现优劣，sigmoid，logistic，relu，。。。

##### Perception

1. 以各节点到指定直线(矩阵范数=1)的范数平方和为损失函数
2. 用梯度下降

##### k近邻法

1. 用k个最近点种类的众数，表决改结点的种类
2. 首先构造kd树，选择每个维度的中间值 sequentially. supplement?

##### 朴素贝叶斯法

* P(y|x)=P(x,y)/P(x)

##### 决策树

**目标**：找到一组特征，使各节点按这种特征的信息熵增益最大

* <font color=green>原先的类是？</font>

**信息熵增益**：$-\sum_{i=1}^n p\ lgp$ → $-\sum_{i=1}^n c_i\sum_{j=1}^k P_{ij}\ lgP_{ij} $

**Alg**：依次比较并选出信息增益比最大的特征，再在？

**剪枝算法**：为了避免过拟合(T的结点树过大)，在损失函数后+$\alpha$|T|

1. 对每个结点，一次考虑剪去改结点前后CART<font color=green>$(C_{\alpha},符号好多)$</font>相等的$\alpha$值，取最小记为$\alpha{1}$，剪枝为T1,
   * T1和T2的关系虽然记不住，是可以推出来的
2. 在T1上按1选择$\alpha_{2}$和T2，迭代

* 为什么T1不是最小的，

* T1,T2有什么性质？

  * 在alpha<alpha1，剪去T0的任意一个结点，$C_{\alpha}\geq C_{\alpha1}$，
  
  * T1一定是$\alpha\leq\alpha_1时$剪去一个结点的$\underset {T}{min}\ C_{\alpha}$ ,
    <font color=green>T2一定是$\alpha\leq\alpha_1时$剪去2个结点的$\underset {T}{min}\ C_{\alpha}$ ？</font>
  
  * 不过T1~Tk只是使得$C_{\alpha}(T)$ 尽可能min，而非C(T)min，所以需要比较

##### 逻辑斯蒂回归和最大熵模型 

* Logistic用交叉熵于多分类，指数和形式，损失函数的GD计算用到矩阵W的求导

  最大熵模型$-\sum\widetilde{P}(x)P(y|x)logP(y|x)$

* 可以看，最大熵模型，给定(xi,yi)对，估计$\widetilde P(x) $和$\widetilde P(x,y)$，求极小化损失函数的p(x,y)值

* 用到各种极值问题的数值解方法

##### SVM(跟Perception不是一个东西)

* 硬间隔=点集到分化线的最大距离(Premium:原点集线性可分(2类点在分化线两侧))

* 软间隔=线性可分时的最大间隔/线性不可分时最小间隔值，如何建立模型来刻画不可分最小间隔值？

  用$max\ exp(yi\ast d((xi,yi),wx+b))$ ;

* 核方法=线性变换的软间隔，具有非线性表征能力，专业😀😀

##### AdBoost(分类+决策树)

* 多个分类器的线性组合，迭代中加权总体分类效果最差的点和分类总体点最优的分类器，

  如何加权，有很多函数，简单如分类错误次数占比定义点的权重，

* 可以理解为XXX模型的前向算法？

* 决策树，也前向算法\===(累加)==，求导得损失函数极小化时的值(L式种植)，相当于逼近残差，

**EM**

* Gauss混合model?

##### Recessive Markov 

$$
过程：根据隐变量表示出output的最大似然估计P(i,o|\theta)，计算其在P(i,o|\overline\theta)下期望，\\
拉格朗日乘子法求极大值得\overline\theta，来估计o对应的i，
$$

* 维比特算法==??==用动态规划求得state 1,2,...,T（近似alg不能保证整体most probably）

##### conditional random field

* 条件概率下的Markov性，只与邻点相关
* 酱紫P(y|y0,x)就可用概率链表示$ \underset{(y_{i1},y_{i2},...,y{ik})\in Path}\sum P(y|y_{ik},x)P(y_{ik}|y_{ik-1},x)...P(y_{i1}|y_0,x)$
* 如何估计P(y~ik~|y~ik-1~,x)?——(都知道模型了还不会定义学习参数和目标函数，shame)

* P(y|x)是模型，预测(x,y)之间的关系，参数是P(y~ik~|y~ik-1~,x)，有交叉熵损失函数之外的方法？
* 也可用(y-P(y|x)x)^2^作损失函数，还有0-1损失函数(不可导)，绝对值损失函数

PS：对数损失函数是交叉熵损失函数的一个特例


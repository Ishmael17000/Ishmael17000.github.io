# Introduction to Machine Learning 
## Background

Task, Performance, Experience

Examples:
数据挖掘
信用危机分析
个性化定制推荐
自动化
图像识别
搜索引擎（识图）

## General ML System Design
1. Experience
2. What to learn(Goal function)
3. Expression of the goal
4. Algorithm
5. Design


## Basic Conceps
1. Instance Space
2. Hypothesis Space
3. Sample Space

# Experiment Methods and Principles

## How to evaluate a model?
It depends on the type of tasks.
### Regression:
The prediction $p_i$ is a continuous value. We need to evaluate the difference between it and the actual value $y_i$.

MAE: Mean Absolute Error,平均绝对误差
$$ \text{MAE} = \frac{1}{n}\sum_{i=1}^n |y_i - p_i| $$
MSE: Mean Squared Error，均方误差
$$ \text{MSE} = \frac{1}{n}\sum_{i=1}^n (y_i - p_i)^2 $$
RMSE: Root Mean Squared Error，均方根误差
$$ \text{RMSE} = \sqrt{\frac{1}{n}\sum_{i=1}^n (y_i - p_i)^2} $$


### Classification:
The prediction always belongs to a discrete set of values. We need to determine whether the prediction is correct or not.

Accuracy:
$$ \text{Accuracy} = \frac{1}{n}\sum _{i=1}^n \mathbb{I}_{(y_i=p_i)}$$
$$\text{Erro Rate}=1-\text{Accuracy} $$

Precision/Recall
ROC/AUC (See 2.1 35:00/ Calculation: 41:00)

### Other specific tasks...



## How to split the data?

训练集/测试集
验证集（用来调参，从训练集中分出，避免过拟合）

## Experiment
随机重复实验
- 数据随机
- 模型随机
K-fold cross validation（K折交叉验证）



# 决策树

### 适用场景
- 非数值、离散特征的分类问题
- 没有相似度的概念
- 特征无序


总的来说，非叶子节点代表属性，分支代表属性的取值，最终叶子节点代表类别。


## 经典算法

### ID3
- 从上到下，贪心搜索
- 递归
- 核心循环：
  - $A$: 下一步**最佳决策属性**
  - 将  $A$ 作为当前节点决策属性
  - 对属性 $A(v_i)$ 的每个值，创建新子节点
  - 根据属性值将训练样本分配到各个节点
  - 如果样本**完美分类**，则退出循环，否则继续下探分裂新的节点

问题 1. 什么是最佳决策属性？

- 基本原则：简洁，树的节点最好少
- 在每个节点上，选择属性，使派生节点的数据**纯度**高，**混杂度**低
- 计算混杂度：熵
  $$ Entropy(D)=-\sum _j P(w_j)log_2P(w_j) $$
  - 是信息论中的概念，定义了信息的混杂度，越大越乱
  - 均匀分布的熵最大
- Gini 混杂度
  $$ i(N)=\sum _{i\neq j}P(w_i)P(w_j)=1-\sum _i P(w_i)^2 $$
  - 越大越乱，均匀分布取最大
- 考虑信息增益 Information Gain ，即通过对 $A$ 的不同排序带来的熵的减少量. 子节点的熵乘以对应占的比例
  $$ Gain(S,A)=Entropy(S)-\sum _{v\in Values(A)} \frac{|S_v|}{|S|}\cdot Entropy(S_v) $$

问题 2. 何时停止分裂？
- 子集中所有数据有相同的输出类别
- 子集中所有数据相同的输入特征值（相当于区分不出了）
  - 此时可能是数据有噪声
  - 可能漏掉了重要特征
- IG 相同无所谓（例如异或关系）

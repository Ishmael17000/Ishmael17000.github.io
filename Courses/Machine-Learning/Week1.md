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
-数据随机
-模型随机
K-fold cross validation（K折交叉验证）


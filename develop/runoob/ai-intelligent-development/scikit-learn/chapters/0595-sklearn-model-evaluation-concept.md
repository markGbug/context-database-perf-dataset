# Scikit-learn：Sklearn 模型评估与调优

- 来源：[Sklearn 模型评估与调优](https://www.runoob.com/sklearn/sklearn-model-evaluation.html)
- 分类：AI / 智能开发
- 技术：Scikit-learn
- 笔记类型：概念卡
- 章节序号：0595

## 本章内容

机器学习模型的评估与调优是确保模型泛化能力和预测准确度的关键步骤。

通过合适的评估指标和调优方法，可以有效提高模型性能，避免过拟合或欠拟合的风险。

本章节将详细介绍交叉验证、网格搜索、随机搜索、模型评估方法等内容。


## 1、交叉验证


### 介绍交叉验证的概念

交叉验证（Cross-Validation）是一种用于评估模型性能的技术，它通过将数据集分成多个子集（折叠），并多次训练和测试模型来获得更稳定、可靠的评估结果。

交叉验证有助于检测模型是否过拟合，并且能够更准确地评估模型的泛化能力。

常见的交叉验证方法包括：

- K-fold 交叉验证：将数据分成 K 个折叠，依次选择其中一个折叠作为测试集，其他 K-1 个折叠作为训练集，重复 K 次，最后计算 K 次的结果平均值。
- 留一法交叉验证（Leave-One-Out Cross-Validation, LOOCV）：每次只保留一个数据点作为测试集，剩余的作为训练集。这种方法非常耗时，但可以用于小数据集。
- 分层 K-fold 交叉验证：在 K-fold 中，确保每个折叠中的类别分布与整个数据集相似，适用于类别不平衡的情况。

scikit-learn 提供了多种交叉验证的方法，如 cross_val_score 和 cross_val_predict 等，可以帮助我们高效地进行交叉验证。


### 使用 cross_val_score 执行 K-fold 交叉验证

cross_val_score 函数用于执行 K-fold 交叉验证，返回每个折叠的评分结果，帮助我们评估模型的稳定性和性能。

使用 cross_val_score 执行 K-fold 交叉验证:


## 实例

- cv=5：表示进行 5 折交叉验证。
- scores：返回每一折的评分，最终结果是这些评分的平均值，表示模型的性能。

输出如下所示：

```text
Cross-validation scores: [0.96666667 0.96666667 0.93333333 0.96666667 1.        ]
Mean accuracy: 0.9666666666666668
```


## 2、网格搜索与随机搜索


### 使用 GridSearchCV 进行超参数调优

GridSearchCV 是一种通过穷举搜索所有超参数组合来找到最佳超参数的技术。

GridSearchCV 通过提供一组参数的候选值，计算每一种组合的性能，最终选择最佳的参数组合。

GridSearchCV 的常见参数:

- param_grid：待调优的超参数网格，通常是一个字典，键是参数名，值是参数的候选值。
- cv：交叉验证的折数，通常设置为 5 或 10。

scikit-learn 使用 GridSearchCV 实例：


## 实例

- grid_search.best_params_：返回网格搜索中表现最好的超参数组合。
- grid_search.best_score_：返回最佳参数组合下的交叉验证得分。

输出如下所示：

```text
Best parameters: {'C': 1, 'kernel': 'linear'}
Best score: 0.9800000000000001
```


### 使用 RandomizedSearchCV 加速调优过程

RandomizedSearchCV 是一种更高效的超参数调优方法，它通过从超参数空间中随机选择一定数量的组合进行评估，从而加速调优过程。

RandomizedSearchCV 适用于超参数空间较大时，可以节省计算时间。

RandomizedSearchCV 的常见参数：

- param_distributions：待调优的超参数分布，通常是一个字典，值可以是分布对象（如 scipy.stats 中的分布）或者离散的值列表。
- n_iter：随机搜索的迭代次数，即随机选择的超参数组合数量。

scikit-learn 使用 RandomizedSearchCV 实例：


## 实例

- random_search.best_params_：返回随机搜索中表现最好的超参数组合。
- random_search.best_score_：返回最佳参数组合下的交叉验证得分。

输出如下所示：

```text
Best parameters: {'C': 8.355688344706016, 'kernel': 'rbf'}
Best score: 0.9866666666666667
```


## 3、评估模型


### 使用 classification_report, confusion_matrix, roc_auc_score

对于分类模型，我们通常使用精度、召回率、F1 分数等指标来评估模型性能。

scikit-learn 提供了许多评估工具，帮助我们深入了解模型的表现。

classification_report - 提供了精度、召回率、F1 分数和支持度（每个类别的样本数）等信息。


## 实例

confusion_matrix - 混淆矩阵用于显示分类模型在各个类别上的表现，特别是如何将正类预测为负类，反之亦然。


## 实例

roc_auc_score - ROC AUC（接收者操作特征曲线下面积）是评估分类模型性能的指标，尤其适用于不平衡数据集。AUC 值越高，模型性能越好。


## 实例


### 回归模型评估：mean_squared_error, r2_score

对于回归问题，常用的评估指标包括 均方误差（MSE） 和 决定系数（R²）。

mean_squared_error - 均方误差是回归模型的常见评估标准，计算预测值与真实值之间的平方误差的均值。


## 实例

r2_score - 决定系数 R² 用于衡量模型对数据的拟合程度，值越接近 1，表示模型拟合得越好。


## 实例


## 记忆卡片

- 一句话定义：`Sklearn 模型评估与调优` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。

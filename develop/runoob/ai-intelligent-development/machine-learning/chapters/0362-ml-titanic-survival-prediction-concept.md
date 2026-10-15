# 机器学习：泰坦尼克号生存预测

- 来源：[泰坦尼克号生存预测](https://www.runoob.com/ml/ml-titanic-survival-prediction.html)
- 分类：AI / 智能开发
- 技术：机器学习
- 笔记类型：概念卡
- 章节序号：0362

## 本章内容

如果你刚开始学习机器学习，可能会觉得那些复杂的算法和数学公式离现实世界很遥远。但今天，我们将通过一个经典案例——泰坦尼克号生存预测，来亲手体验一次完整的机器学习项目流程。

泰坦尼克号数据集是机器学习领域最著名的入门项目之一，它基于 1912 年泰坦尼克号沉船事件中乘客的真实信息。我们的目标是：根据乘客的年龄、性别、船票等级等信息，构建一个模型来预测他们是否能在灾难中幸存。

这个项目之所以经典，是因为它完美地涵盖了机器学习项目的核心步骤：

- 数据理解与探索
- 数据清洗与预处理
- 特征工程
- 模型选择与训练
- 模型评估与优化

通过这个实战案例，你将不再只是阅读理论，而是真正理解如何将机器学习应用于解决实际问题。


## 第一步：理解我们的数据

在动手写任何代码之前，我们必须先了解手头的数据。泰坦尼克号数据集通常包含以下字段（特征）：

核心洞察：从历史知识我们知道，当时奉行"妇女和儿童优先"的原则，且头等舱乘客有优先使用救生艇的权利。因此，我们预期 Sex, Age, Pclass 等特征将对预测结果产生重大影响。


## 第二步：数据清洗与预处理

原始数据几乎从不完美。

数据清洗就像为模型准备高质量的食材，这一步至关重要。

把以下数据存储到 train.csv 文件中：

```text
PassengerId,Survived,Pclass,Name,Sex,Age,SibSp,Parch,Ticket,Fare,Cabin,Embarked
1,0,3,"Braund, Mr. Owen Harris",male,22,1,0,A/5 21171,7.25,,S
2,1,1,"Cumings, Mrs. John Bradley",female,38,1,0,PC 17599,71.2833,C85,C
3,1,3,"Heikkinen, Miss. Laina",female,26,0,0,STON/O2. 3101282,7.925,,S
4,1,1,"Futrelle, Mrs. Jacques Heath",female,35,1,0,113803,53.1,C123,S
5,0,3,"Allen, Mr. William Henry",male,35,0,0,373450,8.05,,S
6,0,3,"Moran, Mr. James",male,,0,0,330877,8.4583,,Q
7,0,1,"McCarthy, Mr. Timothy J",male,54,0,0,17463,51.8625,E46,S
8,0,3,"Palsson, Master. Gosta Leonard",male,2,3,1,349909,21.075,,S
9,1,3,"Johnson, Mrs. Oscar W",female,27,0,2,347742,11.1333,,S
10,1,2,"Nasser, Mrs. Nicholas",female,14,1,0,237736,30.0708,,C
```

把以下数据存储到 test.csv 文件中：

```text
PassengerId,Pclass,Name,Sex,Age,SibSp,Parch,Ticket,Fare,Cabin,Embarked
11,3,"Kelly, Mr. James",male,34.5,0,0,330911,7.8292,,Q
12,3,"Wilkes, Mrs. James",female,47,1,0,363272,7,,S
13,2,"Myles, Mr. Thomas Francis",male,62,0,0,240276,9.6875,,Q
14,3,"Dwyer, Miss. Ellen",female,18,0,0,330959,7.75,,Q
15,1,"Jones, Mr. Charles",male,,1,0,PC 17603,82.1708,B28,C
```

我们将使用 Python 的 pandas 和 numpy 库来完成这项工作。


## 实例

输出：

```html
训练集形状： (10, 12)
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 10 entries, 0 to 9
Data columns (total 12 columns):
 #   Column       Non-Null Count  Dtype
---  ------       --------------  -----
 0   PassengerId  10 non-null     int64
 1   Survived     10 non-null     int64
 2   Pclass       10 non-null     int64
 3   Name         10 non-null     object
 4   Sex          10 non-null     object
 5   Age          9 non-null      float64
 6   SibSp        10 non-null     int64
 7   Parch        10 non-null     int64
 8   Ticket       10 non-null     object
 9   Fare         10 non-null     float64
 10  Cabin        3 non-null      object
 11  Embarked     10 non-null     object
dtypes: float64(2), int64(5), object(5)
memory usage: 1.1+ KB
None
   PassengerId  Survived  Pclass                          Name     Sex  ...  Parch            Ticket     Fare Cabin  Embarked
0            1         0       3       Braund, Mr. Owen Harris    male  ...      0         A/5 21171   7.2500   NaN         S
1            2         1       1    Cumings, Mrs. John Bradley  female  ...      0          PC 17599  71.2833   C85         C
2            3         1       3        Heikkinen, Miss. Laina  female  ...      0  STON/O2. 3101282   7.9250   NaN         S
3            4         1       1  Futrelle, Mrs. Jacques Heath  female  ...      0            113803  53.1000  C123         S
4            5         0       3      Allen, Mr. William Henry    male  ...      0            373450   8.0500   NaN         S

[5 rows x 12 columns]
```

运行上述代码后，你可能会发现两个主要问题：缺失值 和 非数值型数据。


### 处理缺失值


## 实例


### 转换非数值型数据

机器学习模型通常只能处理数值。我们需要将 Sex 和 Embarked 这样的文本列转换为数字。


## 实例


## 第三步：特征工程

特征工程是机器学习中的"魔法"，它通过创造或转换特征来帮助模型更好地学习。我们从 Name 列中提取"称谓"就是一个经典例子。


## 实例


## 第四步：选择与训练模型

现在，我们有了干净且富含信息的数值数据。接下来，我们将其分为特征 (X) 和目标变量 (y)，然后选择一个模型进行训练。

我们将从简单且高效的 随机森林 (Random Forest) 模型开始。


## 实例


## 第五步：模型评估、优化与提交


### 评估与优化

一次训练的结果可能不是最优的。我们可以通过以下方式改进：

- 调整模型参数：例如，尝试不同的 n_estimators 或 max_depth。
- 尝试其他模型：比如逻辑回归、支持向量机、梯度提升树等。
- 进一步的特征工程：比如对 Age 或 Fare 进行分箱处理。


## 实例


### 特征重要性分析

随机森林可以告诉我们哪些特征对预测贡献最大。


## 实例

你可能会发现 Sex, Fare（关联 Pclass）, Age, Title 是最重要的特征，这与我们的历史直觉相符。


### 在测试集上生成最终预测

当我们对模型性能满意后，就用全部训练数据重新训练，并对真正的测试集进行预测。


## 实例


## 总结与项目流程图

我们已经完成了一个完整的机器学习管道，用流程图回顾整个过程：

通过这个实战项目，你不仅学会了 pandas 进行数据处理、sklearn 构建模型的技巧，更重要的是，你掌握了解决一个机器学习问题的标准思路。

这个流程——从数据理解到模型部署——是绝大多数数据科学项目的核心。


## 记忆卡片

- 一句话定义：`泰坦尼克号生存预测` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。

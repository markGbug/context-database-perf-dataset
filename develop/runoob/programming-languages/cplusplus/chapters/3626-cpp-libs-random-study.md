# C++：C++ 标准库 <random>

- 来源：[C++ <random>](https://www.runoob.com/cplusplus/cpp-libs-random.html)
- 分类：编程语言
- 技术：C++
- 笔记类型：学习笔记
- 章节序号：3626

## 本章内容

C++ 标准库中的 <random> 头文件提供了一组用于生成随机数的工具，涵盖了从简单的均匀分布到复杂的离散分布，为需要随机数的应用程序提供了广泛的选择。这些工具对于模拟、游戏开发、加密算法等领域非常有用。

<random> 不仅支持生成伪随机数，还支持种子控制、各种概率分布等，使得开发者可以灵活地生成符合特定需求的随机数序列。

<random> 库由以下三个主要组件构成：

- 随机数引擎：生成伪随机数的核心，用于控制生成过程的可重复性和随机性。
- 随机数分布：控制生成的数值遵循的概率分布类型。
- 随机数适配器：允许调整引擎行为，如 discard_block 等适配器。

在 C++ 中，随机数生成器（Random Number Generator, RNG）可以分为两大类：

- 伪随机数生成器：它们使用确定性算法生成看似随机的数列。这些数列在理论上是可预测的，但通常对于大多数应用来说足够随机。
- 真随机数生成器：它们基于物理过程（如热噪声、放射性衰变等）生成随机数，但 C++ 标准库不直接提供这类生成器。


### 常用随机数引擎

常用引擎如 std::mt19937 因为生成速度快且生成质量高，是普遍推荐的随机数生成引擎。生成器还可以使用 seed() 方法指定种子，便于生成可重复的伪随机序列。


### 随机数分布类型

1、均匀分布

```java
std::mt19937 gen(seed);
std::uniform_int_distribution<int> dist(1, 100); // 生成 1 到 100 间的整数
int random_int = dist(gen);
```

2、正态分布

```text
std::mt19937 gen(seed);
std::normal_distribution<> dist(0, 1); // 平均值为0，标准差为1
double random_normal = dist(gen);
```

3、离散分布

```java
std::mt19937 gen(seed);
std::discrete_distribution<int> dist({40, 10, 50}); // 概率为40%、10%、50%
int random_discrete = dist(gen);
```


### 语法

使用 <random> 库的基本步骤如下：

- 包含头文件 <random>。
- 创建一个随机数生成器对象。
- 使用分布类生成随机数。


## 实例


### 生成基本的随机数


## 实例

输出结果：

```text
Random number: 3499211612
```

注意：每次运行程序时，生成的随机数可能不同。


### 使用均匀分布


## 实例

输出结果：

```text
Random number: 7
Random number: 10
Random number: 6
Random number: 2
Random number: 4
```

每次运行程序时，输出的随机数序列可能不同。


### 使用正态分布


## 实例

```text
Random number: -0.15
Random number: 0.13
Random number: -1.87
Random number: 0.46
Random number: -0.21
```

使用 mt19937 引擎生成不同分布的随机数：


## 实例


### 随机数适配器

机数适配器允许调整生成行为，主要有两类适配器：

- std::discard_block_engine：丢弃一定数量的生成值，仅保留指定间隔的值，用于减少随机性。
- std::independent_bits_engine：生成指定位数的随机数，便于直接生成二进制数据。


## 实例


### 常见用法

- 使用种子生成可重复的随机序列：指定相同的种子使得每次运行生成相同序列。
- 生成不同分布的随机数：选择符合应用场景的分布函数，能更好地模拟实际问题。
- 调整生成器性能：使用不同的随机引擎来平衡生成性能与精确度。


## 复习重点

- 能说明 `C++ <random>` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

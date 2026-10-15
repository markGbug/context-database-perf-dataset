# Markdown：Markdown 数学公式

- 来源：[Markdown 数学公式](https://www.runoob.com/markdown/md-math.html)
- 分类：DevOps / 工程化
- 技术：Markdown
- 笔记类型：学习笔记
- 章节序号：1822

## 本章内容

### LaTeX 数学公式基础

在 Markdown 中，数学公式通过 LaTeX 语法来表示。LaTeX 是一个强大的排版系统，特别适用于包含复杂数学公式的文档。

- 命令：以反斜杠 \ 开头，如 \alpha、\sum
- 参数：用花括号 {} 包围，如 \frac{a}{b}
- 下标：使用 _，如 x_1
- 上标：使用 ^，如 x^2
- 分组：用花括号将多个字符组合，如 x_{i+1}

```java
\alpha, \beta, \gamma  % 希腊字母
\sum, \prod, \int      % 求和、乘积、积分
\frac{分子}{分母}      % 分数
\sqrt{表达式}          % 平方根
\sqrt[n]{表达式}       % n次根
```


### 行内公式与块级公式

行内公式使用单个美元符号 $ 包围，公式会嵌入到文本中，如：文本中的变量 $x = 5$ 和函数 $f(x) = x^2 + 2x + 1$。

```text
文本中的变量 $x = 5$ 和函数 $f(x) = x^2 + 2x + 1$。
```

块级公式使用双美元符号 $$ 包围，公式会独立成行并居中显示：

E = mc^2

\int_{-\infty}^{\infty} e^{-x^2} dx = \sqrt{\pi}

```text
$$E = mc^2$$

$$\int_{-\infty}^{\infty} e^{-x^2} dx = \sqrt{\pi}$$
```

使用 align 环境创建多行对齐公式：

\begin{align} f(x) &= ax^2 + bx + c \ f'(x) &= 2ax + b \ f''(x) &= 2a \end{align}

```text
$$
    \begin{align}
    f(x) &= ax^2 + bx + c \\
    f'(x)  &= 2ax + b \\
    f''(x)  &= 2a
    \end{align}
    $$
```


## 常用数学符号


### 基本运算符号

- 加减乘除：+, -, \times, \div
- 分数：\frac{a}{b} → $\frac{a}{b}$
- 根号：\sqrt{x}, \sqrt[n]{x} → $\sqrt{x}$, $\sqrt[n]{x}$
- 指数：x^2, e^{i\pi} → $x^2$, $e^{i\pi}$


### 比较符号

- 等于：=, \neq, \equiv → $=$, $\neq$, $\equiv$
- 大小：<, >, \leq, \geq → $<$, $>$, $\leq$, $\geq$
- 约等于：\approx, \sim → $\approx$, $\sim$


### 集合符号

- 属于：\in, \notin → $\in$, $\notin$
- 包含：\subset, \supset → $\subset$, $\supset$
- 交并：\cap, \cup → $\cap$, $\cup$
- 空集：\emptyset → $\emptyset$


### 希腊字母

常用希腊字母及其 LaTeX 表示：


### 特殊函数和符号

- 三角函数：\sin, \cos, \tan
- 对数：\log, \ln
- 极限：\lim_{x \to 0}
- 求和：\sum_{i=1}^{n}
- 积分：\int_{a}^{b}
- 无穷：\infty


## 复习重点

- 能说明 `Markdown 数学公式` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

# Julia：Julia 数学函数

- 来源：[Julia 数学函数](https://www.runoob.com/julia/julia-mathematical-functions.html)
- 分类：Python / 数据科学
- 技术：Julia
- 笔记类型：练习笔记
- 章节序号：3936

## 本章内容

Julia 提供了一套高效、可移植的标准数学函数。


## 数值比较函数

下表列出了用于数值比较的函数：

isequal 认为 NaN 之间是相等的，这一点和 == 运算符不同：


## 实例

isequal 也能用来区分带符号的零：


## 实例

isapprox 用于浮点数的近似比较，由于浮点误差，直接用 == 比较两个浮点数往往不符合预期：


## 实例


## 舍入函数

下表列出了 Julia 支持的舍入函数：


## 实例

注意：不带类型参数的 floor(3.8) 返回 Float64 类型的 3.0，只有指定类型 floor(Int, 3.8) 才返回整数 3。这与 Python 的 int() 行为不同。


## 除法函数

下表列出了 Julia 支持的除法函数：


## 实例


## 符号和绝对值函数

下表列出了 Julia 支持的符号和绝对值函数：


## 实例


## 幂、对数和根函数

下表列出了 Julia 支持的初等数学函数：


## 实例

注意：expm1 和 log1p 专门用于 x 很接近 0 的场景。此时 exp(x)-1 或 log(1+x) 会因为浮点误差丢失精度，而这两个函数能给出精确结果。


## 三角和双曲函数

Julia 也提供了所有标准的三角和双曲函数：

```text
sin    cos    tan    cot    sec    csc
sinh   cosh   tanh   coth   sech   csch
asin   acos   atan   acot   asec   acsc
asinh  acosh  atanh  acoth  asech  acsch
sinc   cosc
```

下图中以弧度为单位的角度对应于单位圆上的一个点，其坐标定义了角度的正弦和余弦。


## 实例

以上提供的函数都是单参数函数，不过 atan 也可以接收两个参数来表示传统的 atan2 函数：

```text
atan(y)
atan(y, x)
```

分别计算 y 或 y/x 的反正切。双参数版本能根据 x、y 的符号确定正确的象限：


## 实例

另外，sinpi(x) 和 cospi(x) 分别用来对 sin(pi*x) 和 cos(pi*x) 进行更精确的计算。


### 角度制三角函数

上面函数的参数都是弧度制。要计算角度制的三角函数，以 d 做后缀即可，比如 sind(x) 计算 x 度的正弦值：

```text
sind   cosd   tand   cotd   secd   cscd
asind  acosd  atand  acotd  asecd  acscd
```


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Julia 数学函数` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

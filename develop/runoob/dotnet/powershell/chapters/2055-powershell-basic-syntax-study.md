# PowerShell：PowerShell 基本语法

- 来源：[PowerShell 基本语法](https://www.runoob.com/powershell/powershell-basic-syntax.html)
- 分类：.NET
- 技术：PowerShell
- 笔记类型：学习笔记
- 章节序号：2055

## 本章内容

PowerShell 不只是一个命令行工具，它还是一个完整的脚本语言。学习它的基本语法，就像学习一门新的编程语言一样，是入门的重要一步。

本节将详细介绍 PowerShell 中最基本的语法元素，包括变量、注释、数据类型、运算符、条件判断、循环结构等内容，为后续编写脚本打下扎实基础。


## 一、注释

PowerShell 中的注释与大多数编程语言相似，用于解释代码，不会被执行。

单行注释使用 # 开头：

```text
# 这是一个单行注释
Write-Output "Hello, PowerShell"
```

多行注释使用 <# 和 #> 包裹：

```text
<#
这是多行注释
可用于文档说明
#>
```


## 二、变量


### 定义变量

PowerShell 中变量以 $ 符号开头，无需事先声明类型：

```text
$name = "Alice"
$age = 25
```


### 使用变量

```text
Write-Output "Name: $name"
```

也可以使用字符串插值：

```text
Write-Output "User: $($name), Age: $($age)"
```


## 三、数据类型

PowerShell 是弱类型语言，但变量背后都有对应的 .NET 类型。

可以使用 .GetType() 查看变量类型：

```text
$str.GetType().Name   # String
```


## 四、运算符

示例：

```text
5 -eq 5       # True
"abc" -like "a*"  # True
```


## 五、条件判断


### if 语句

```text
if ($age -ge 18) {
    Write-Output "成年人"
} else {
    Write-Output "未成年人"
}
```


### if-elseif-else

```text
if ($score -ge 90) {
    "优秀"
} elseif ($score -ge 60) {
    "及格"
} else {
    "不及格"
}
```


## 六、循环结构


### for 循环

```java
for ($i = 1; $i -le 5; $i++) {
    Write-Output "第 $i 次循环"
}
```


### foreach 循环

```text
$colors = @("Red", "Green", "Blue")
foreach ($color in $colors) {
    Write-Output "颜色：$color"
}
```


### while 循环

```java
$count = 0
while ($count -lt 3) {
    Write-Output $count
    $count++
}
```


## 七、函数定义

PowerShell 允许自定义函数，语法如下：

```javascript
function Say-Hello {
    param([string]$name)
    Write-Output "Hello, $name!"
}

Say-Hello -name "PowerShell"
```

也可以使用简洁写法：

```javascript
function Square($x) { return $x * $x }
Square 5  # 输出 25
```


## 八、错误处理

使用 try {} catch {} 块来处理可能出错的语句：

```text
try {
    Get-Item "C:\NotExist.txt"
} catch {
    Write-Output "找不到文件"
}
```


## 九、脚本文件基本格式

PowerShell 脚本文件使用 .ps1 后缀名。可以使用 VS Code 或记事本创建：

```text
# hello.ps1
$name = "World"
Write-Output "Hello, $name"
```

在 PowerShell 中运行：

```text
.\hello.ps1
```

注意：如果脚本未能执行，请检查执行策略（Get-ExecutionPolicy），必要时使用 Set-ExecutionPolicy 允许运行脚本。


## 复习重点

- 能说明 `PowerShell 基本语法` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

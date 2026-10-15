# PowerShell：PowerShell 变量和作用域

- 来源：[PowerShell 变量和作用域](https://www.runoob.com/powershell/powershell-variables-and-scope.html)
- 分类：.NET
- 技术：PowerShell
- 笔记类型：练习笔记
- 章节序号：2060

## 本章内容

变量是任何编程语言的基础工具，在 PowerShell 中也不例外。

我们可以用变量存储数字、字符串、对象、数组、哈希表……而真正让 PowerShell 变量变得强大的，是它的 作用域机制。理解作用域，可以让你写出更稳定、结构更清晰的脚本，避免变量冲突或意外覆盖。

本节将带你全面认识 PowerShell 中变量的使用方式、数据类型、作用域规则以及最佳实践。


## 一、变量基础


### 定义变量

在 PowerShell 中，变量以美元符号（$）开头，后跟变量名。

```text
$greeting = "Hello, PowerShell"
$number = 100
```

变量赋值不需要事先声明类型，PowerShell 会自动推断数据类型。


### 读取变量

直接引用变量即可读取其值：

```text
Write-Output $greeting
```

还可以插入到字符串中：

```text
Write-Output "提示信息：$greeting"
```

如果字符串使用单引号，则不会解析变量：

```text
Write-Output '提示信息：$greeting'   # 输出字面值
```


### 查看变量类型

```text
$number.GetType()
```


### 常见变量类型举例


## 二、特殊变量

PowerShell 预定义了许多有用的内置变量：


## 三、变量作用域概念


### 什么是作用域？

作用域（Scope） 指变量在何处有效。PowerShell 支持多个作用域层级，确保变量不会被无意中覆盖。

常见作用域包括：


### 示例演示：变量作用域差异

```javascript
$global:name = "Tom"       # 全局变量
$name = "Alice"            # 本地变量
function Show-Name {
    $name = "Bob"          # 函数内的局部变量
    Write-Output "函数内部：$name"
}

Show-Name
Write-Output "函数外部：$name"
Write-Output "全局变量：$global:name"
```

输出结果：

```text
函数内部：Bob
函数外部：Alice
全局变量：Tom
```


### 显式设置作用域

你可以在变量名前加作用域标识符来明确变量的可见范围：

```text
$script:dbName = "MyDatabase"  # 仅对当前脚本可见
$global:apiKey = "abcdef12345" # 对所有位置可用
```


### 查看当前作用域中的变量

```text
Get-Variable
```

或者列出全局变量：

```text
Get-Variable -Scope Global
```


## 四、常见错误与注意事项


## 五、实践示例


### 示例 1：创建一个函数并使用全局变量作为配置

```javascript
$global:Threshold = 80

function Check-CPU {
    $usage = (Get-Counter '\Processor(_Total)\% Processor Time').CounterSamples[0].CookedValue
    if ($usage -gt $global:Threshold) {
        Write-Output "CPU 使用率过高：$([math]::Round($usage, 2))%"
    } else {
        Write-Output "CPU 使用率正常：$([math]::Round($usage, 2))%"
    }
}
```


### 示例 2：函数中定义变量对外不可见（局部作用域）

```javascript
function Say-Hello {
    $message = "你好，PowerShell！"
    Write-Output $message
}

Say-Hello
Write-Output $message   # 报错：$message 不存在
```


### 示例 3：使用 $env: 设置环境变量（临时）

```text
$env:MY_ENV = "HelloWorld"
Write-Output $env:MY_ENV
```

注意：这种方式只在当前 PowerShell 会话中有效，关闭窗口后失效。


## 六、小结

- PowerShell 使用 $变量名 定义变量，类型自动推断
- 可存储任意数据类型，包括字符串、数组、哈希表、对象等
- 作用域控制变量的"生存范围"，常用的有 Local、Script、Global
- 正确理解作用域有助于编写结构清晰、可维护性强的脚本
- 内置变量和环境变量非常实用，但要注意其作用域限制


## 七、练习任务

任务 1：定义一个字符串变量 $title 并输出：

```text
$title = "PowerShell 学习之旅"
Write-Output $title
```

任务 2：在函数中定义变量，并尝试在函数外访问

```javascript
function Set-Message {
    $msg = "来自函数"
    Write-Output $msg
}
Set-Message
Write-Output $msg   # 查看是否能访问
```

任务 3：设置并读取环境变量 APP_ENV

```text
$env:APP_ENV = "Development"
Write-Output $env:APP_ENV
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `PowerShell 变量和作用域` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

# PowerShell：PowerShell 控制结构

- 来源：[PowerShell 控制结构](https://www.runoob.com/powershell/powershell-control-structures.html)
- 分类：.NET
- 技术：PowerShell
- 笔记类型：练习笔记
- 章节序号：2061

## 本章内容

控制结构是程序的"大脑"，决定代码在什么条件下执行、是否重复执行，以及如何优雅地处理错误。

PowerShell 作为现代脚本语言，提供了完整的流程控制语法，包括：

- 条件语句：if、elseif、else、switch
- 循环结构：for、foreach、while、do-while
- 错误处理机制：try-catch-finally


## 一、条件语句


### if / elseif / else

基本语法：

```text
if (条件1) {
    # 条件1为真执行
} elseif (条件2) {
    # 条件2为真执行
} else {
    # 其他情况
}
```

```text
$disk = Get-PSDrive C
if ($disk.Free -lt 5GB) {
    Write-Output "磁盘空间不足！"
} elseif ($disk.Free -lt 10GB) {
    Write-Output "磁盘空间偏低。"
} else {
    Write-Output "磁盘空间充足。"
}
```


### switch

当有多个可能值要判断时，switch 比多个 if 更清晰。

```text
switch ($value) {
    "start" { Write-Output "开始任务" }
    "stop"  { Write-Output "停止任务" }
    "exit"  { Write-Output "退出程序" }
    default { Write-Output "未知命令" }
}
```

支持匹配模式：

```text
switch -Wildcard ($filename) {
    "*.txt" { "文本文件" }
    "*.jpg" { "图片文件" }
    default { "其他类型" }
}
```


## 二、循环结构


### for 循环（经典计数循环）

```java
for ($i = 1; $i -le 5; $i++) {
    Write-Output "第 $i 次"
}
```


### foreach 循环（遍历集合）

```text
$names = "张三", "李四", "王五"
foreach ($name in $names) {
    Write-Output "你好，$name"
}
```

也可使用 ForEach-Object 管道版本：

```text
$names | ForEach-Object { Write-Output "你好，$_" }
```


### while 循环（条件为真执行）

```java
$count = 0
while ($count -lt 3) {
    Write-Output "计数：$count"
    $count++
}
```


### do-while 与 do-until

do 循环会 至少执行一次：

```java
$count = 0
do {
    Write-Output "当前值：$count"
    $count++
} while ($count -lt 3)
```

do-until：直到条件为真才停止

```java
$count = 0
do {
    Write-Output "当前值：$count"
    $count++
} until ($count -ge 3)
```


## 三、错误处理：try / catch / finally

PowerShell 提供结构化异常处理机制，用于捕获和响应运行时错误。


### 3.1 基本结构

```text
try {
    # 尝试运行可能出错的代码
}
catch {
    # 错误时执行
}
finally {
    # 无论是否出错，都会执行（可选）
}
```


### 示例：处理除零错误

```text
try {
    $result = 10 / 0
}
catch {
    Write-Output "发生错误：$($_.Exception.Message)"
}
finally {
    Write-Output "运算结束"
}
```


### 捕获特定异常类型

```text
try {
    Get-Content "不存在的文件.txt"
}
catch [System.IO.FileNotFoundException] {
    Write-Output "文件未找到！"
}
catch {
    Write-Output "其他错误：$($_.Exception.Message)"
}
```

默认一些命令只会打印错误，不会进入 catch。此时需要添加参数：

```text
Remove-Item "不存在的文件.txt" -ErrorAction Stop
```

或设置全局策略：

```text
$ErrorActionPreference = "Stop"
```


## 四、小结


## 五、练习任务

任务 1：判断一个数字是否为偶数或奇数

```text
$number = 7
if ($number % 2 -eq 0) {
    "偶数"
} else {
    "奇数"
}
```

任务 2：遍历数组并打印每项长度

```text
$items = "apple", "banana", "cherry"
foreach ($item in $items) {
    "$item 的长度是 $($item.Length)"
}
```

任务 3：处理文件读取错误

```text
try {
    Get-Content "D:\not-exist.txt"
}
catch {
    "文件读取失败：" + $_.Exception.Message
}
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `PowerShell 控制结构` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

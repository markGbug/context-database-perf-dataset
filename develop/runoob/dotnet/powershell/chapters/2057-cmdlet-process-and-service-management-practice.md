# PowerShell：Cmdlet 进程和服务管理

- 来源：[Cmdlet 进程和服务管理](https://www.runoob.com/powershell/cmdlet-process-and-service-management.html)
- 分类：.NET
- 技术：PowerShell
- 笔记类型：练习笔记
- 章节序号：2057

## 本章内容

进程和服务的管理，是系统维护和自动化运维中非常重要的一部分。

PowerShell 提供了一组简洁而强大的 Cmdlet，用于查看、启动、停止、筛选和控制本地（或远程）计算机上的进程与服务。

本节将详细讲解如何使用 PowerShell 管理进程与服务，包括基本操作命令、典型应用场景及常见问题，帮助你提升系统管理效率。


## 一、进程管理（Process）

PowerShell 使用 .NET 的进程对象来处理进程操作，常用的 Cmdlet 包括：


### 查看进程：Get-Process

查看所有正在运行的进程：

```text
Get-Process
```

查看特定进程（如 notepad）：

```text
Get-Process -Name notepad
```

查看多个进程：

```text
Get-Process -Name chrome, notepad
```

获取进程详细信息并排序：

```text
Get-Process | Sort-Object CPU -Descending | Select-Object -First 5
```

根据进程名停止：

```text
Stop-Process -Name notepad
```

根据进程 ID 停止：

```text
Stop-Process -Id 1234
```

强制终止进程（避免交互提示）：

```text
Stop-Process -Name notepad -Force
```


### 启动进程：Start-Process

打开记事本：

```text
Start-Process notepad
```

以管理员身份打开 PowerShell（需当前窗口有权限）：

```text
Start-Process powershell -Verb RunAs
```

启动网页浏览器并访问网址：

```text
Start-Process "https://learn.microsoft.com"
```


### 等待进程：Wait-Process

等待进程执行完毕后继续：

```text
Start-Process notepad
Wait-Process -Name notepad
Write-Output "记事本已关闭"
```


## 二、服务管理（Service）

PowerShell 对服务管理的支持非常完备，常用 Cmdlet 如下：


### 查看服务：Get-Service

查看所有服务：

```text
Get-Service
```

筛选正在运行的服务：

```text
Get-Service | Where-Object {$_.Status -eq "Running"}
```

查看特定服务：

```text
Get-Service -Name W32Time
```


### 启动与停止服务

启动 Windows 时间服务：

```text
Start-Service -Name W32Time
```

停止服务（如果权限不足可能会报错）：

```text
Stop-Service -Name W32Time
```


### 重启服务：Restart-Service

```text
Restart-Service -Name W32Time
```


### 更改服务设置：Set-Service

将服务启动类型设为自动：

```text
Set-Service -Name W32Time -StartupType Automatic
```

将服务禁用：

```text
Set-Service -Name W32Time -StartupType Disabled
```


## 三、服务 vs 进程的区别


## 四、实战示例


### 示例 1：检测并重启某个异常停止的服务

```text
$svc = Get-Service -Name Spooler
if ($svc.Status -ne "Running") {
    Restart-Service -Name Spooler
    Write-Output "服务已重启"
}
```


### 示例 2：关闭所有 CPU 占用高于 50 的进程（需谨慎）

```text
Get-Process | Where-Object { $_.CPU -gt 50 } | Stop-Process -Force
```

注意：这类操作务必在测试环境或确认无风险的前提下进行。


## 五、常见问题与注意事项


## 六、小结

PowerShell 通过标准化的命令集，使得进程与服务的管理变得简单而高效：

- 使用 Get-* 查看信息，Start-*/Stop-* 控制行为，Set-* 修改属性
- 管道 + 条件筛选 + 对象操作，适合批量管理任务
- 可以结合计划任务、监控脚本，构建自动化运维体系


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Cmdlet 进程和服务管理` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

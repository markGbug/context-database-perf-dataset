# PowerShell：Cmdlet 网络与系统管理

- 来源：[Cmdlet 网络与系统管理](https://www.runoob.com/powershell/cmdlets-network-and-system-management.html)
- 分类：.NET
- 技术：PowerShell
- 笔记类型：练习笔记
- 章节序号：2058

## 本章内容

PowerShell 不仅能管理本地文件、进程和服务，它还具备强大的网络功能和系统级操作能力。无论是查看 IP、测试网络连通性，还是获取系统信息、管理用户账户，PowerShell 都提供了丰富而统一的 Cmdlet。

本节将带你掌握网络和系统管理中最常用的命令，助你从"命令行使用者"迈向"系统管理高手"。


## 一、网络管理相关 Cmdlet


### 测试网络连通性：Test-Connection

类似于 ping 命令，但输出为对象，支持更多操作。

```text
Test-Connection -ComputerName www.baidu.com -Count 4
```

快速版本（PowerShell 7+）：

```text
Test-NetConnection www.baidu.com
```


### 获取本机 IP 配置：Get-NetIPAddress

```text
Get-NetIPAddress
```

仅查看 IPv4 地址：

```text
Get-NetIPAddress -AddressFamily IPv4
```

也可通过旧命令兼容方式：

```text
ipconfig
```

或者更通用的 WMI 命令：

```text
Get-WmiObject -Class Win32_NetworkAdapterConfiguration | Where-Object { $_.IPEnabled }
```


### 获取当前网络连接状态：Get-NetTCPConnection

列出所有 TCP 连接及端口状态（类似 netstat）：

```text
Get-NetTCPConnection
```

查看某个端口的连接情况：

```text
Get-NetTCPConnection -LocalPort 80
```


### 管理主机名和 DNS 缓存

获取本机主机名：

```text
$env:COMPUTERNAME
```

清除 DNS 缓存：

```text
Clear-DnsClientCache
```


## 二、系统信息查询


### 获取操作系统信息：Get-ComputerInfo

```text
Get-ComputerInfo
```

筛选关键字段（如系统版本、CPU）：

```text
Get-ComputerInfo | Select-Object OSName, WindowsVersion, CsProcessors
```


### 获取系统启动时间

```text
(Get-CimInstance -Class Win32_OperatingSystem).LastBootUpTime
```


### 获取磁盘信息：Get-Volume

```text
Get-Volume
```

也可以用：

```text
Get-PSDrive -PSProvider FileSystem
```

或：

```text
Get-CimInstance Win32_LogicalDisk | Select-Object DeviceID, VolumeName, Size, FreeSpace
```


### 获取 BIOS 和硬件信息

```text
Get-CimInstance -ClassName Win32_BIOS
Get-CimInstance -ClassName Win32_ComputerSystem
```


## 三、用户与账户管理（本地）


### 获取当前用户信息

```text
[System.Security.Principal.WindowsIdentity]::GetCurrent().Name
```

或者：

```text
$env:USERNAME
```


### 查看本地用户列表（Windows 本地账户）

```text
Get-LocalUser
```

禁用用户：

```text
Disable-LocalUser -Name "TestUser"
```

启用用户：

```text
Enable-LocalUser -Name "TestUser"
```

注意：需以管理员身份运行。


### 添加新用户（本地）

```text
New-LocalUser -Name "NewUser" -Password (Read-Host -AsSecureString "输入密码")
```


## 四、系统设置操作


### 设置系统时区

```text
Set-TimeZone -Id "China Standard Time"
```

查看支持的时区：

```text
Get-TimeZone -ListAvailable
```


### 设置系统主机名（需重启生效）

```text
Rename-Computer -NewName "MyNewPC" -Restart
```


### 设置系统时间（需要管理员权限）

```text
Set-Date -Date "2025-07-22 10:30"
```


## 五、实战场景示例


### 示例 1：测试本机到多个目标主机的连通性

```text
"192.168.1.1", "8.8.8.8", "www.baidu.com" | ForEach-Object {
    Test-Connection -ComputerName $_ -Count 2
}
```


### 示例 2：列出当前打开的 TCP 端口（状态为 Listening）

```text
Get-NetTCPConnection | Where-Object { $_.State -eq "Listen" }
```


### 示例 3：生成系统信息报告

```text
$report = Get-ComputerInfo | Select-Object OSName, OSArchitecture, CsName, CsProcessors, WindowsVersion
$report | Out-File -FilePath "C:\SystemReport.txt"
```


## 六、小结

PowerShell 提供了强大的网络与系统管理能力，远超传统命令行工具：

- 网络操作支持测试、监测、配置 IP 和端口
- 系统信息命令便于生成诊断报告和自动化审计
- 本地账户管理适合小型系统或工作组环境
- 所有命令都是对象导向、组合灵活、可脚本化


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Cmdlet 网络与系统管理` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

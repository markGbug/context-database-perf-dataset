# PowerShell：PowerShell 实际应用

- 来源：[PowerShell 实际应用](https://www.runoob.com/powershell/powershell-practice.html)
- 分类：.NET
- 技术：PowerShell
- 笔记类型：学习笔记
- 章节序号：2063

## 本章内容

PowerShell 不只是一个终端工具，它是 Windows 环境下功能最全面的自动化平台之一。

本节将通过 三大类实际应用场景，展示 PowerShell 在日常管理、远程运维、跨技术集成中的强大能力：

- 日常管理任务自动化
- 远程管理
- 与其他技术集成


## 一、日常管理任务自动化


### 1.1 批量文件重命名

将一个目录下的所有 .txt 文件重命名为统一前缀加序号的形式，如：log_001.txt、log_002.txt 等。

```text
$files = Get-ChildItem -Path "D:\Logs" -Filter "*.txt"
$count = 1
foreach ($file in $files) {
    $newName = "log_{0:D3}.txt" -f $count
    Rename-Item -Path $file.FullName -NewName $newName
    $count++
}
```


### 定时清理临时文件

```text
$targetPath = "C:\Windows\Temp"
Get-ChildItem -Path $targetPath -Recurse |
    Where-Object { $_.LastWriteTime -lt (Get-Date).AddDays(-7) } |
    Remove-Item -Force -Recurse
```

建议将脚本保存为 .ps1 文件后，使用任务计划程序（Task Scheduler）定期执行。


### 系统信息收集脚本

```text
$info = [PSCustomObject]@{
    ComputerName = $env:COMPUTERNAME
    OSVersion    = (Get-CimInstance Win32_OperatingSystem).Caption
    Uptime       = ((Get-Date) - (Get-CimInstance Win32_OperatingSystem).LastBootUpTime).ToString()
    CPU          = (Get-CimInstance Win32_Processor).Name
    RAM_GB       = [math]::Round((Get-CimInstance Win32_ComputerSystem).TotalPhysicalMemory / 1GB, 2)
}
$info | Format-List
```


### 日志分析和报告生成

```text
$logPath = "C:\inetpub\logs\LogFiles\W3SVC1\*.log"
$lines = Get-Content $logPath | Where-Object { $_ -match "500" }

$lines.Count
$lines | Out-File "C:\Reports\error_500_report.txt"
```


## 二、远程管理


### PowerShell Remoting 基础

PowerShell Remoting 是通过 WinRM 实现远程命令执行的机制。

开启远程功能（管理员运行）：

```text
Enable-PSRemoting -Force
```


### 使用 Invoke-Command 执行远程命令

```text
Invoke-Command -ComputerName "Server01" -ScriptBlock {
    Get-Service -Name "W32Time"
}
```

支持多个主机批量执行：

```text
$servers = @("Server01", "Server02")
Invoke-Command -ComputerName $servers -ScriptBlock {
    Get-Process | Where-Object { $_.CPU -gt 100 }
}
```


### 远程会话管理

建立会话：

```text
$session = New-PSSession -ComputerName "Server01"
```

进入会话：

```text
Enter-PSSession $session
```

执行命令：

```text
Invoke-Command -Session $session -ScriptBlock { Get-Date }
```

关闭会话：

```text
Remove-PSSession $session
```


### 安全考虑事项

- 使用 HTTPS 而非 HTTP（配置证书）
- 避免使用明文密码，推荐使用凭据对象：

```text
$cred = Get-Credential
Invoke-Command -ComputerName "Server01" -Credential $cred -ScriptBlock { hostname }
```


## 三、与其他技术集成


### PowerShell 与 .NET Framework

PowerShell 内建对 .NET 类库的访问能力，几乎可以调用所有 .NET API。

```javascript
function Get-FileHashMD5 {
    param ([string]$path)
    $md5 = [System.Security.Cryptography.MD5]::Create()
    $bytes = [System.IO.File]::ReadAllBytes($path)
    $hash = $md5.ComputeHash($bytes)
    return ([BitConverter]::ToString($hash)).Replace("-", "")
}

Get-FileHashMD5 "D:\file.zip"
```


### 调用 REST API

```text
$response = Invoke-RestMethod -Uri "https://api.weatherapi.com/v1/current.json?key=APIKEY&q=Beijing"
$response.location.name
$response.current.temp_c
```


### 数据库连接基础（以 SQL Server 为例）

```java
$connectionString = "Server=localhost;Database=TestDB;Integrated Security=True"
$query = "SELECT TOP 10 * FROM Users"

$connection = New-Object System.Data.SqlClient.SqlConnection $connectionString
$command = $connection.CreateCommand()
$command.CommandText = $query

$connection.Open()
$reader = $command.ExecuteReader()
while ($reader.Read()) {
    Write-Output $reader["UserName"]
}
$connection.Close()
```


### 与 Office 应用程序交互

```text
$excel = New-Object -ComObject Excel.Application
$excel.Visible = $true
$workbook = $excel.Workbooks.Add()
$sheet = $workbook.Worksheets.Item(1)

$sheet.Cells.Item(1, 1) = "Name"
$sheet.Cells.Item(1, 2) = "Score"
$sheet.Cells.Item(2, 1) = "Alice"
$sheet.Cells.Item(2, 2) = 95
```


## 四、小结


## 复习重点

- 能说明 `PowerShell 实际应用` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

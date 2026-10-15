# 知识点 63475：PowerShell：PowerShell 控制结构 - if / elseif / else

- 来源：[PowerShell 控制结构](https://www.runoob.com/powershell/powershell-control-structures.html)
- 来源章节：[2061-powershell-control-structures-practice.md](../chapters/2061-powershell-control-structures-practice.md)
- 分类：.NET
- 技术：PowerShell
- 所在小节：if / elseif / else
- 知识类型：代码
- 原章节序号：2061

## 原文片段

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

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `if / elseif / else` 这一小节和 `PowerShell 控制结构` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？

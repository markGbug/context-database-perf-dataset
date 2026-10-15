# 知识点 53975：PowerShell：PowerShell 管道和过滤 - 示例：列出正在运行的服务并排序

- 来源：[PowerShell 管道和过滤](https://www.runoob.com/powershell/powershell-pipeline-filtering.html)
- 来源章节：[2059-powershell-pipeline-filtering-practice.md](../chapters/2059-powershell-pipeline-filtering-practice.md)
- 分类：.NET
- 技术：PowerShell
- 所在小节：示例：列出正在运行的服务并排序
- 知识类型：代码
- 原章节序号：2059

## 原文片段

```text
Get-Service | Where-Object {$_.Status -eq "Running"} | Sort-Object DisplayName
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `示例：列出正在运行的服务并排序` 这一小节和 `PowerShell 管道和过滤` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？

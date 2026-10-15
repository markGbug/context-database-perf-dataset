# 知识点 81976：PowerShell：PowerShell 控制结构 - switch

- 来源：[PowerShell 控制结构](https://www.runoob.com/powershell/powershell-control-structures.html)
- 来源章节：[2061-powershell-control-structures-study.md](../chapters/2061-powershell-control-structures-study.md)
- 分类：.NET
- 技术：PowerShell
- 所在小节：switch
- 知识类型：代码
- 原章节序号：2061

## 原文片段

```text
switch ($value) {
    "start" { Write-Output "开始任务" }
    "stop"  { Write-Output "停止任务" }
    "exit"  { Write-Output "退出程序" }
    default { Write-Output "未知命令" }
}
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `switch` 这一小节和 `PowerShell 控制结构` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？

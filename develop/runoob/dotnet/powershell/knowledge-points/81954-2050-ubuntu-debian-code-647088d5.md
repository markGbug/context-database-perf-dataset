# 知识点 81954：PowerShell：PowerShell 安装 - Ubuntu / Debian

- 来源：[PowerShell 安装](https://www.runoob.com/powershell/powershell-install.html)
- 来源章节：[2050-powershell-install-study.md](../chapters/2050-powershell-install-study.md)
- 分类：.NET
- 技术：PowerShell
- 所在小节：Ubuntu / Debian
- 知识类型：代码
- 原章节序号：2050

## 原文片段

```text
# 安装依赖
sudo apt update
sudo apt install -y wget apt-transport-https software-properties-common

# 导入微软 GPG 密钥
wget -q https://packages.microsoft.com/config/ubuntu/22.04/packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb

# 安装 PowerShell
sudo apt update
sudo apt install -y powershell
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `Ubuntu / Debian` 这一小节和 `PowerShell 安装` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？

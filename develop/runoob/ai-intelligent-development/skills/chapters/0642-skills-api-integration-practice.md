# Skills（技能）：Skills 与外部 API 集成

- 来源：[Skills API 集成](https://www.runoob.com/skills/skills-api-integration.html)
- 分类：AI / 智能开发
- 技术：Skills（技能）
- 笔记类型：练习笔记
- 章节序号：0642

## 本章内容

Skill 脚本可以像普通 Python 程序一样调用外部 HTTP API，从而将 Claude 的能力与第三方服务连接起来。


## 调用外部 API 的基本模式

使用 requests 库发送 HTTP 请求，是 Skill 脚本中最常见的 API 调用方式。


## 实例


## API 密钥的安全管理

API 密钥不能直接写在脚本文件中，应通过环境变量传递。


## 实例

在 SKILL.md 中告知用户需要配置密钥：

```text
## 前置配置

本 Skill 需要外部 API 密钥，首次使用前请完成以下配置：

1. 在 [API 服务商网站] 注册并获取 API 密钥
2. 在终端中设置环境变量：
   ```bash
   export MY_API_KEY="你的密钥"
   ```
3. 若需要永久生效，将上述命令添加到 ~/.bashrc 或 ~/.zshrc

若未配置，Skill 将提示"未设置 API 密钥"并退出。
```

永远不要将 API 密钥提交到 Git 仓库。可以在 Skill 目录下创建 .gitignore 文件，将 .env 文件排除在版本控制之外。


## 处理 API 限速（Rate Limiting）

大多数 API 有请求频率限制。当批量调用 API 时，需要在请求间加入延迟。


## 实例


## 响应结果缓存

对于相同输入会返回相同结果的 API，可以将结果缓存到本地文件，避免重复请求，既省钱又提速。


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Skills API 集成` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

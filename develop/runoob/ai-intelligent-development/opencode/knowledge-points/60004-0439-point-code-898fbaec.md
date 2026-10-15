# 知识点 60004：OpenCode：OpenCode MCP 服务器配置 - 基础配置结构

- 来源：[OpenCode MCP 服务器配置](https://www.runoob.com/opencode/opencode-mcp.html)
- 来源章节：[0439-opencode-mcp-practice.md](../chapters/0439-opencode-mcp-practice.md)
- 分类：AI / 智能开发
- 技术：OpenCode
- 所在小节：基础配置结构
- 知识类型：代码
- 原章节序号：0439

## 原文片段

```text
{
  "$schema": "https://opencode.ai/config.json",
  "mcp": {
    "my-mcp-server": {         // 服务器名称（自定义，全局唯一）
      "type": "local",         // 连接类型：local 或 remote
      // ...其他配置项
      "enabled": true          // 是否启用，默认为 true
    },
    "another-mcp-server": {    // 可同时配置多个 MCP 服务器
      "type": "remote",
      // ...
    }
  }
}
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `基础配置结构` 这一小节和 `OpenCode MCP 服务器配置` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？

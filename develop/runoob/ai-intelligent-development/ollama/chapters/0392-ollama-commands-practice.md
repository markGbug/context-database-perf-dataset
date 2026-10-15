# Ollama：Ollama 相关命令

- 来源：[Ollama 相关命令](https://www.runoob.com/ollama/ollama-commands.html)
- 分类：AI / 智能开发
- 技术：Ollama
- 笔记类型：练习笔记
- 章节序号：0392

## 本章内容

Ollama 提供了多种命令行工具（CLI）供用户与本地运行的模型进行交互。

基本格式：

```html
ollama <command> [args]
```

我们可以用 ollama --help 查看包含有哪些命令：

```text
Large language model runner

Usage:
  ollama [flags]
  ollama [command]

Available Commands:
  serve       Start ollama
  create      Create a model from a Modelfile
  show        Show information for a model
  run         Run a model
  stop        Stop a running model
  pull        Pull a model from a registry
  push        Push a model to a registry
  list        List models
  ps          List running models
  cp          Copy a model
  rm          Remove a model
  help        Help about any command

Flags:
  -h, --help      help for ollama
  -v, --version   Show version information
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Ollama 相关命令` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

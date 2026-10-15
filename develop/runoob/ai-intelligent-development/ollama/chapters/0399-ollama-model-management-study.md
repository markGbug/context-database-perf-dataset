# Ollama：Ollama 模型管理

- 来源：[Ollama 模型管理](https://www.runoob.com/ollama/ollama-model-management.html)
- 分类：AI / 智能开发
- 技术：Ollama
- 笔记类型：学习笔记
- 章节序号：0399

## 本章内容

本章节我们将讲解 Ollama 的模型管理命令：拉取、查看、复制、删除，以及模型在内存中的驻留机制。


## 拉取模型：ollama pull

pull 命令只下载模型不进入对话，适合提前把模型准备好。

下载默认标签（latest）:

```text
ollama pull qwen3.5
```

下载指定规格标签:

```text
ollama pull qwen3.5:4b
```

执行后会看到标准的下载流程输出：

```text
$ ollama pull qwen3.5:4b
pulling manifest
pulling 87497c5f0e8f... 100% |████████████████████| 3.4GB
verifying sha256 digest
writing manifest
success
```

下载中断不需要从头再来，Ollama 按层校验存储，重新执行同一命令会自动续传未完成的层。

另外要说明的是，ollama run 内置了 pull 逻辑：首次运行一个模型时，下载和加载会自动完成，所以日常使用中经常不需要单独 pull。

不同规格标签对应的是官方预先做好的不同模型文件，pull 时不能额外指定量化精度。想自己把大模型压成小体积，需要用 create 命令做量化，这属于 Modelfile 定制章节的内容。


## 查看本地模型：list 与 show

list 列出本地所有模型及磁盘占用，是最常用的盘点命令。

列出本地模型:

```text
ollama list
```

例如：

```text
$ ollama list
NAME               ID            SIZE      MODIFIED
qwen3.5:0.8b       9e3f4b3a1c2d  1.0GB     5 minutes ago
qwen3.5:4b         b1c7d9e2f3a4  3.4GB     2 days ago
qwen3.5:latest     a8b2c9d3e4f5  6.6GB     2 hours ago
```

四列分别是模型名、版本指纹、磁盘占用和最后修改时间，磁盘告急时按 SIZE 列排查最直接。

想深入看某个模型的细节，用 show 命令：

```text
# 查看模型详情：能力、参数、系统提示词、许可证等
ollama show qwen3.5
```

show 能回答几个典型问题：这个模型支持哪些能力（对话、视觉、工具调用）、默认生成参数是什么、系统提示词写了什么、上下文窗口多大。

它还有一个进阶用法，把模型的完整配置导出成 Modelfile：


## 实例

这个"查看配方 - 修改 - 重建"的玩法，会在 Modelfile 定制章节完整展开。


## 查看运行中的模型：ollama ps

list 看的是磁盘，ps 看的是内存：谁被加载了、占了多少、什么时候卸载。


## 实例

```text
$ ollama ps
NAME             ID            SIZE      PROCESSOR    CONTEXT    UNTIL
qwen3.5:9b       a8b2c9d3e4f5  9.6GB     100% GPU     131072     4 minutes from now
```

各列含义如下：

PROCESSOR 列是排查"模型为什么慢"的第一入口：只要不是 100% GPU，就说明模型没有完全吃进显存。性能优化的具体手段在 GPU 与性能章节详细讨论。


## 复制与重命名：ollama cp

cp 给已有模型起一个新名字，常用于重命名或保留一份快照。


## 实例

它有一个很实用的进阶技巧：给模型"借名"。

部分工具写死了模型名（比如 gpt-3.5-turbo），用 cp 把本地模型复制成这个名字，就能让这类工具直接用上本地模型：


## 实例

cp 完成得几乎瞬时，因为它只是新建了一个模型名清单，指向原来那份模型文件，不会在磁盘上复制出第二份几个 GB 的数据。


## 删除模型与磁盘清理：ollama rm

rm 删除本地模型，是模型库"只进不出"问题的解药。


## 实例

```text
$ ollama rm qwen3.5:0.8b
deleted 'qwen3.5:0.8b'
```

清理磁盘的推荐流程是：先用 ollama list 找出体积大且不再使用的模型，再逐个 rm。

如果有多个标签共享同一批底层文件，删除其中一个标签不会影响其他标签的正常使用。

用 cp 借过名的模型要一并记得处理：删除原模型后，借名副本依然存在并继续占用空间，别让它们变成看不见的磁盘黑洞。


## 停止模型与 keep-alive 驻留机制

先看一张模型的生命周期图，管理命令各自作用在哪一步就一目了然了。

关键机制是 keep-alive：模型对话结束后并不立刻卸载，而是默认在内存或显存中驻留 5 分钟。

这 5 分钟内再次请求，响应不再有模型加载等待；超过时间没有新请求，自动卸载、释放内存。

想让模型立刻让出资源，用 stop 命令手动卸载：


## 实例

驻留时长有三种调整方式：


## 复习重点

- 能说明 `Ollama 模型管理` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

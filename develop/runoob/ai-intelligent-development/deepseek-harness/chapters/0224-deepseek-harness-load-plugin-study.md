# DeepSeek Harness：DeepSeek Harness 加载本地插件

- 来源：[DeepSeek Harness 加载插件](https://www.runoob.com/deepseek-harness/deepseek-harness-load-plugin.html)
- 分类：AI / 智能开发
- 技术：DeepSeek Harness
- 笔记类型：学习笔记
- 章节序号：0224

## 本章内容

上一篇 DeepSeek Harness 第一个插件 写好了 hello-plugin 的源码，接下来我们把它加载进 Web UI。

这里我们会用到两个东西：patch 覆盖层 cordis.yml 和 --patch 启动参数。


## scratch-plugin 目录结构

之前我们创建了 scratch-plugin/src，现在再加一个 cordis.yml。

整个临时项目的结构如下：

```text
scratch-plugin/
├── src/
│   └── my-plugin.ts    # 插件源码（上一篇写的 hello-plugin）
└── cordis.yml          # patch 覆盖层：告诉框架插入哪个插件
```


## cordis.yml 的 insert

在仓库根目录运行 pwd，拿到绝对路径。

然后创建 scratch-plugin/cordis.yml，内容如下：


## 实例

把 /absolute/path/to/deepseek-harness 替换成 pwd 打印的真实路径。

插件路径必须是绝对路径。

patch 文件只贡献配置，不会改变 loader 解析模块路径时使用的 profile 目录。


## 用 --patch 启动

用这个覆盖层启动 Web UI：

```text
pnpm dsh web --patch ./scratch-plugin/cordis.yml
```

启动期间，终端会打印 [hello-plugin] plugin loaded!。

打开 http://127.0.0.1:3080，在设置插件列表中搜索 hello，可以看到我们安装的插件。


## 工作原理

dsh 把多个配置来源按顺序叠加成一个最终配置。

--patch 传入的 cordis.yml 是一个覆盖层，在启动时叠加进 profile。

提示：--patch 适合本地开发调试。

要把插件交付给其他人时，用组合包（bundle）的方式，见第 21 篇。


## 复习重点

- 能说明 `DeepSeek Harness 加载插件` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

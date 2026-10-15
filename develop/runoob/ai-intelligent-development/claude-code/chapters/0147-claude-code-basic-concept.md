# Claude Code：Claude Code 基础用法

- 来源：[Claude Code 基础用法](https://www.runoob.com/claude-code/claude-code-basic.html)
- 分类：AI / 智能开发
- 技术：Claude Code
- 笔记类型：概念卡
- 章节序号：0147

## 本章内容

本章介绍 Claude Code 日常开发中最常用的核心功能，包括如何与 Claude 对话、读取和修改代码、执行命令、处理文件，以及一些能大幅提升效率的实用技巧。


## 基本对话方式


### 1、交互模式（最常用）

在项目目录下启动 Claude Code，进入交互模式后即可直接输入问题或指令：

```text
cd /path/to/your/project
claude
```

在交互模式中，直接输入自然语言即可，无需任何特殊格式：

```text
这个项目是做什么的？
```

```text
帮我找出 src/auth.ts 里的 bug
```

```text
给 UserService 添加一个 getUserById 方法
```

用 @ 符合可以指定文件，比如我们在 claude-test 目录下有个 test.html。

我们可以进入 claude-test：

```text
cd claude-test
```

然后询问：

```text
@test.html 这个文件是干嘛的
```


### 2、一次性任务模式

如果只需要执行一个任务，不需要进入交互模式，可以直接在命令后面带上任务描述：

```text
claude "解释一下 package.json 里的 scripts 字段"
```

执行完毕后自动退出，适合在 shell 脚本中使用或快速查询。


### 3、单次查询模式（-p）

使用 -p 参数执行一次性查询，Claude 的回答会直接输出到终端，适合与其他命令组合使用：

```text
claude -p "这段代码有什么问题" < src/utils.ts
```

```text
# 将 Claude 的分析结果保存到文件
claude -p "分析项目依赖的安全风险" > security-report.md
```


### 4、继续上一次对话（-c）

Claude Code 会保存对话历史。使用 -c 参数可以在当前目录继续最近一次未完成的对话，无需重新建立上下文：

```text
claude -c
```


## 理解和分析代码


### 1、了解项目整体情况

刚进入一个陌生项目时，可以先让 Claude 做整体分析：

```text
这个项目的架构是怎样的？
```

```text
项目用了哪些主要的技术和依赖？
```

```text
请介绍一下项目的目录结构
```

Claude Code 会自动读取项目文件进行分析，你不需要手动指定要读取哪些文件，它会自行判断需要查看哪些内容。


### 2、分析特定文件或模块

```text
解释一下 src/middleware/auth.ts 的工作原理
```

```text
UserRepository 类里有哪些方法？分别是做什么的？
```

```text
这个 SQL 查询语句是什么意思？
```


### 3、追踪代码调用链

```text
当用户登录时，代码执行流程是怎样的？从入口到数据库全部列出来
```

```text
findUserByEmail 这个函数在哪里被调用？
```

```text
这个接口的数据最终存到了哪张数据库表里？
```


### 4、理解复杂逻辑

```text
这段递归函数是什么意思？能举个例子说明吗？
```

```text
为什么这里要用 useCallback？不用会怎样？
```

```text
这个正则表达式能匹配什么格式的字符串？
```


## 修改代码


### 1、添加新功能

描述你需要的功能，Claude 会找到合适的位置并实现：

```text
在 UserService 里添加一个 updatePassword 方法，需要验证旧密码
```

```text
给登录接口添加请求频率限制，同一 IP 每分钟最多 5 次
```

```text
创建一个 formatCurrency 工具函数，支持传入货币代码参数
```


### 2、修复 Bug

描述问题现象，Claude 会定位原因并给出修复方案：

```text
用户登出后刷新页面仍然显示已登录状态，帮我找出原因并修复
```

```text
这个函数在输入为空数组时会报错，修复它
```

```text
控制台报错 "Cannot read properties of undefined (reading 'map')"，帮我定位并修复
```


### 3、重构代码

```text
把这个 500 行的组件拆分成更小的子组件
```

```text
将 callback 风格的异步代码改为 async/await
```

```text
这几个函数里有大量重复代码，帮我提取成通用函数
```


### 4、审查修改内容

Claude Code 每次修改文件前都会展示 diff，供你审查。你可以在 Claude 提出修改方案后进行讨论：

```text
先不要改代码，只告诉我你打算怎么修改
```

```text
你刚才的修改有个问题：没有处理并发情况，重新来过
```

```text
这个方案可以，但把函数名改成 validateUserCredentials
```

Claude Code 在执行任何文件修改前都会展示修改内容并请求你的确认。你可以选择接受（yes）、拒绝（no），或者在确认前继续讨论。不要觉得必须一次接受所有修改——先看，觉得没问题再确认。


## 执行命令和测试


### 1、让 Claude 运行命令

Claude Code 可以直接在终端执行命令，你可以用自然语言描述要做什么：

```text
运行测试，看看有没有失败的
```

```text
安装 dayjs 这个依赖
```

```text
把项目构建一下，看看有没有报错
```

Claude 会根据项目配置（如 package.json 中的 scripts 或 CLAUDE.md 中的命令）选择正确的命令执行。


### 2、运行特定测试

```text
运行 auth 模块的测试
```

```text
运行所有测试并生成覆盖率报告
```

```text
这个测试为什么失败了？帮我修复
```


### 3、查看命令输出

Claude 会将命令输出作为上下文，直接根据输出内容给出下一步建议：

```text
运行 npm run build，如果有报错帮我修复
```

```text
跑一下 lint，把所有警告都修复掉
```


## 文件操作


### 1、创建新文件

```text
创建 src/utils/date.ts，实现日期格式化相关的工具函数
```

```text
新建一个 Docker Compose 配置文件，包含 PostgreSQL 和 Redis 服务
```

```text
创建 .github/workflows/ci.yml，配置 GitHub Actions 自动运行测试
```


### 2、查找文件和内容

```text
项目里有没有处理文件上传的代码？在哪里？
```

```text
哪些地方用到了 localStorage？
```

```javascript
找出所有使用了 console.log 的文件
```


### 3、批量修改

```text
把所有文件里的 http://api.example.com 替换成 https://api.example.com
```

```text
把 src/components/ 下所有组件的 PropTypes 改为 TypeScript 类型定义
```

```text
给 src/api/ 目录下所有接口函数添加 JSDoc 注释
```


## Git 操作

Claude Code 深度集成了 Git，可以用自然语言完成几乎所有 Git 操作。


## 后续章节

- 1、查看变更
- 2、提交代码
- 3、分支管理
- 4、处理合并冲突
- 上下文管理技巧
- 1、手动指定文件
- 2、清除上下文
- 3、压缩上下文
- 4、合理拆分任务
- 常用斜杠命令
- 实用技巧
- 1、让 Claude 先分析，再动手
- 2、提供错误信息和日志
- 3、用截图描述 UI 问题
- 4、善用"继续"
- 5、要求解释修改内容

## 记忆卡片

- 一句话定义：`Claude Code 基础用法` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。

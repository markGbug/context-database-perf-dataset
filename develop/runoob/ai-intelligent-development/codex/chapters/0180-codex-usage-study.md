# Codex：Codex 基础入门

- 来源：[Codex 基础入门](https://www.runoob.com/codex/codex-usage.html)
- 分类：AI / 智能开发
- 技术：Codex
- 笔记类型：学习笔记
- 章节序号：0180

## 本章内容

### 启动 Codex

Codex 的界面是标准的三栏结构：左侧是任务列表，中间是对话窗口，右侧是多功能区域。

启动 Codex 应用，我们可以在左侧菜单添加项目，中间栏目输入框可以输入我们的需求：

可以设置模型或上传文件等：


### 启动 Codex CLI

安装并配置好账号后，在项目目录下打开终端，输入 codex 即可启动交互式界面：

```text
# 进入你的项目目录
cd ~/my-project

# 启动 Codex 交互界面
codex

# 带初始提示词直接启动
codex "帮我分析这个项目的结构"

# 启动时指定模型
codex --model gpt-5
```

💡 建议在项目根目录下启动 Codex，这样它能完整读取项目文件结构。

Codex 界面很简洁，光标所在处就是输入框，直接输入你的需求即可。

例如我们进入目录 codex-runoob-test 然后使用 codex 命令启动：

```text
cd codex-runoob-test
# 启动 Codex 交互界面
codex
```

然后就可以在交互界面直接输入我们的需求，比如让它解释下 test.py 文件的代码，效果如下（这些记录也会显示在 Codex App 中）：


### 三种审批模式（Approval Mode）

Codex CLI 提供三种不同级别的操作权限模式，你可以根据任务需求选择合适的模式：

```text
# 指定审批模式启动
codex --approval-mode ask        # 默认只读模式
codex --approval-mode auto-edit  # 自动编辑模式（缩写 -a auto-edit）
codex --approval-mode full-auto  # 完全自动模式

# 在交互界面中切换
/approvals  # 输入此命令切换审批模式
```


### 你的第一次对话

```text
codex "分析这个项目的目录结构，告诉我主要文件的作用"

# Codex 会自动读取文件，输出类似：
# ✓ 读取 package.json
# ✓ 扫描 src/ 目录（23 个文件）
#   项目结构分析：
# - src/index.ts：应用入口，初始化 Express 服务器
# - src/routes/：API 路由定义（共 5 个端点）
# ...
```

```text
codex "我的 login 函数有 bug，用户登录后 token 没有正确保存，帮我找出问题并修复"

# Codex 会：
# 1. 读取相关文件
# 2. 分析代码逻辑
# 3. 提出修改方案
# 4. 等待你确认后执行修改
```

```text
codex "给我的 Express 应用添加一个用户注册接口，需要验证邮箱格式，密码至少8位，并把用户信息存入数据库"

# 传入图片上下文
codex -i design.png "按照这个设计图，实现对应的 React 组件"
```


### 图片输入

Codex CLI 支持将图片作为上下文输入，这在以下场景特别有用：

- 分析报错截图
- 根据 UI 设计图生成前端代码
- 解读架构图并据此实现功能

```text
# 方法一：命令行传入图片路径
codex -i screenshot.png "解释这个报错信息，并告诉我如何修复"

# 方法二：传入多张图片
codex --image img1.png,img2.jpg "对比这两个界面的区别，实现图一的设计"

# 方法三：在交互界面中粘贴图片（macOS）
# 复制图片后，在 Codex 输入框中直接按 Cmd+V 粘贴

# 方法四：Shift + 拖拽图片到终端窗口
```


## 复习重点

- 能说明 `Codex 基础入门` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

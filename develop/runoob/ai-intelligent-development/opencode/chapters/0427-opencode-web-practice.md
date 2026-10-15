# OpenCode：OpenCode Web 使用（浏览器界面）

- 来源：[OpenCode Web 使用](https://www.runoob.com/opencode/opencode-web.html)
- 分类：AI / 智能开发
- 技术：OpenCode
- 笔记类型：练习笔记
- 章节序号：0427

## 本章内容

除了终端（TUI）之外，OpenCode 还提供了 Web 界面，可以通过浏览器直接使用 AI 编程能力。

Web 模式适合：远程访问、团队协作、可视化操作。

OpenCode Web 是 TUI 的图形化版本，让 AI 编程从终端工具升级为可视化协作平台。


## 一、什么是 OpenCode Web？

OpenCode Web 是基于 HTTP 服务的图形界面版本，本质上是：

- 后端：OpenCode 服务（CLI 启动）
- 前端：浏览器界面

可以理解为：TUI 的可视化版本


## 二、启动 Web 服务


### 1、基本启动

```text
opencode web
```

默认会：

- 启动本地 HTTP 服务
- 自动打开浏览器


### 2、自定义端口

```text
opencode web --port 4096
```


### 3、允许外部访问（重要）

```text
opencode web --hostname 0.0.0.0 --port 4096
```

可在局域网或远程访问


## 三、访问方式

启动后，在浏览器访问：

```text
http://localhost:4096
```

或：

```text
http://你的IP:4096
```


## 四、界面说明

OpenCode Web 界面通常包含：

- 输入区：输入提示词（类似 ChatGPT）
- 对话区：显示 AI 输出结果
- 文件上下文：自动读取项目代码
- 操作记录：执行命令与修改日志

本质与 TUI 一致，只是更直观


## 五、基本使用方式


### 1、提问

```text
帮我分析这个项目的结构
```


### 2、引用文件

```text
这个函数是做什么的？@src/index.js
```


### 3、执行修改

```text
把这个函数拆成三个函数，并增加错误处理
```

说明：

- Web 与 TUI 的指令完全一致
- 同样支持上下文理解


### 4、会话

在主页上查看和管理你的会话。你可以查看活跃的会话，也可以创建新的会话。


### 5、服务器状态

点击 See Servers 可以查看已连接的服务器及其状态。


## 六、认证（安全设置）

如果你在公网或团队环境使用，建议开启认证：

```text
export OPENCODE_SERVER_PASSWORD=123456
opencode web
```

说明：

- 用户名默认：opencode
- 密码：你设置的值


## 七、常见使用场景


### 1、远程开发

- 服务器运行 OpenCode
- 浏览器远程访问


### 2、团队共享

- 多人查看 AI 修改结果
- 共享对话上下文


### 3、演示 / 教学

- 比终端更直观
- 适合录屏与展示


## 八、Web vs TUI


## 九、常见问题


### 1、无法访问页面

检查：

- 端口是否开放
- 是否使用正确地址（localhost / IP）


### 2、无法远程访问

确保使用：

```text
--hostname 0.0.0.0
```


### 3、端口被占用

更换端口：

```text
opencode web --port 5000
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `OpenCode Web 使用` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

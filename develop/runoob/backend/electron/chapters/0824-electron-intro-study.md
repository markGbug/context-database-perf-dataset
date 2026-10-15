# Electron：Electron 简介

- 来源：[Electron 简介](https://www.runoob.com/electron/electron-intro.html)
- 分类：后端开发
- 技术：Electron
- 笔记类型：学习笔记
- 章节序号：0824

## 本章内容

Electron 是一个开源框架，把 Chromium（浏览器内核）＋ Node.js（服务器/系统能力） 包裹进一个桌面应用壳，让你用 HTML/CSS/JS 写跨平台的桌面程序（Windows、macOS、Linux）。

关键点：

- 前端负责界面（Renderer 进程：像浏览器标签页）。
- 主进程（Main）负责应用生命周期、窗口、原生 API 调用。
- 两者通过 IPC（进程间通信） 交互。
- 最终可打包成 .exe、.app、.deb 等安装文件。

Electron 由 GitHub 开发并维护，最初是为了构建 Atom 编辑器而创建的。

简单来说：Electron = Chromium + Node.js + Native APIs

- Chromium：提供强大的渲染引擎，负责显示界面。
- Node.js：提供后端能力，可以访问文件系统、网络等。
- Native APIs：提供操作系统级别的功能，如菜单、通知、托盘等。


## 为什么选 Electron

Electron 让 Web 开发者无需学习新语言就能构建桌面应用，大幅降低了桌面开发的门槛。

- 上手快：Web 开发者可以复用大量前端技能/组件/生态（React/Vue/Angular/TS/CSS）。
- 跨平台：写一次，构建三平台（虽然有系统差异需要调整）。
- 强大的本地能力：直接访问文件系统、进程、系统 API，而不必写本地语言绑定（绝大多数场景靠 Node.js 就够）。
- 生态成熟：大量现成库、模板、打包工具（Electron Builder / Forge 等）。
- 适合工具类应用：编辑器、通信工具、生产力软件、调试工具等。

Electron 的设计理念是"一次编写，到处运行"（Write Once, Run Everywhere）。

开发者只需要编写一套代码，就能生成 Windows、macOS 和 Linux 三个平台的应用程序。

核心优势：

- 使用熟悉的 Web 技术栈开发桌面应用。
- 无需学习平台特定的开发语言（如 C++、Objective-C、Swift）。
- 统一的开发体验和代码库。
- 快速迭代和部署。


## 应用场景

Electron 适合以下类型的桌面应用开发：

- 开发工具 / 编辑器：代码编辑器、终端、调试器（如 VS Code、Postman）。
- 即时通信/社交：聊天客户端（如 Discord、Slack）。
- 跨平台桌面客户端：需要快速把 web 产品做成桌面版。
- 原型与内部工具：公司内部运营工具、数据面板、管理台。
- 对 UI/交互要求高但不极端性能敏感的应用。

不适合的场景：对 CPU/GPU/内存极度敏感、需要极致原生体验或移动端优先的项目（如大型图形渲染、超低延迟游戏）。


## Electron 能做什么

Electron 提供了丰富的桌面端能力，以下是它支持的主要功能：

- 打开窗口、菜单、系统托盘、通知（系统通知）。
- 读写文件、操作本地数据库（SQLite、LevelDB 等）。
- 调用本机命令/二进制、启动子进程。
- 使用原生对话框（打开/保存文件）、剪贴板、拖拽、全局快捷键。
- 实现自动更新（auto-update）、热重载、打包分发。
- 加载本地或远程网页，支持现代 Web 技术（WebGL、WebRTC 等）。
- 集成原生模块（C++/Node Native Addons），接入硬件或系统功能。


## 核心概念（技术要点）

理解以下几个核心概念是掌握 Electron 开发的关键：

- Main 进程：Electron 的入口，负责创建 BrowserWindow、管理应用生命周期与原生 API。运行单实例（Node 可用）。
- Renderer 进程：每个 BrowserWindow 对应一个 renderer，运行网页（Chromium），不直接访问 Node（可通过 preload 暴露受限 API）。
- Preload 脚本 & contextIsolation：推荐用 preload 在 renderer 中注入受限 API，开启 contextIsolation 提高安全性。
- IPC（ipcMain / ipcRenderer / contextBridge）：主、渲染进程通信机制。
- 打包工具：Electron Builder / Electron Forge / electron-packager 等，用于生成安装包与自动更新。
- Auto-updater：实现应用自动升级（需服务端/发布配置）。


## 安全注意事项

Electron 同时拥有浏览器和 Node.js 的能力，安全配置至关重要。

永远不要在 renderer 中直接开启 nodeIntegration: true，默认关闭以防 XSS 导致任意系统命令执行。

- 使用 contextIsolation + preload + contextBridge 暴露最小、受控的 API。
- 对外部内容（远程 URL）进行严格校验 / 沙箱处理。
- 对文件路径、shell 命令等输入做严格校验，避免命令注入。
- 尽量使用 CSP、禁用 eval、避免不受信任的第三方脚本。


## Electron 的优势与局限

本节从优势和局限两个维度全面分析 Electron，帮助你做出合理的技术选型。


### 主要优势

以下是 Electron 相比其他桌面开发方案的核心竞争力：

1. 跨平台开发的便利性

使用 Electron，开发者可以用同一套代码库生成 Windows、macOS 和 Linux 三个平台的应用：


## 实例

节省的成本：

- 无需维护三套代码库。
- 团队不需要掌握多种平台开发技术。
- 统一的测试和部署流程。
- 更快的功能迭代速度。

2. Web 技术栈的优势

- 丰富的生态系统：npm 上有数百万个包可用。
- 成熟的框架：可以使用 React、Vue、Angular 等现代前端框架。
- 开发效率高：热重载、DevTools、丰富的调试工具。
- 人才储备充足：Web 开发者数量庞大，招聘容易。
- 快速原型开发：利用现有的 Web 组件和库。

3. 强大的功能支持

- 完整的 Node.js 能力（文件系统、网络、进程等）。
- 原生桌面功能（菜单、通知、系统托盘等）。
- 自动更新机制。
- 硬件访问能力（摄像头、USB 设备等）。
- 离线工作能力。

4. 活跃的社区和生态

- 官方文档完善。
- 大量开源项目可供参考。
- 丰富的第三方工具和库。
- 活跃的社区支持。


### 主要局限

了解 Electron 的局限性有助于判断它是否适合你的项目：

1. 性能开销

Electron 应用需要同时运行 Chromium 和 Node.js，这带来了额外的性能开销：

- 内存占用：空白的 Electron 应用通常占用 50-100MB 内存。
- CPU 使用：渲染引擎和 JavaScript 执行相比原生应用效率较低。
- 启动时间：相比原生应用，启动时间较长。

原生应用与 Electron 应用对比：

2. 安装包体积大

每个 Electron 应用都需要打包完整的 Chromium 和 Node.js 运行时：

- Windows：~50-70MB（未压缩）。
- macOS：~60-80MB（未压缩）。
- Linux：~55-75MB（未压缩）。

这意味着即使是简单的应用，安装包也不会小于 50MB。

3. 安全性考虑

由于 Electron 同时拥有浏览器和 Node.js 的能力，如果配置不当，可能存在安全风险：

- XSS 攻击可能导致系统级权限被利用。
- 需要仔细配置上下文隔离和沙箱。
- 第三方依赖的安全问题。

4. 原生体验差异

虽然可以模拟原生界面，但在某些方面仍有差异：

- 无法完美复制系统原生控件。
- 某些系统级功能难以实现。
- 平台特定的交互习惯需要额外处理。


### 权衡建议

以下表格帮助你根据项目需求判断 Electron 是否适合：


## 与其它同类工具对比

Electron 并非唯一选择，以下是主流桌面开发方案的对比：

如果你是前端/全栈开发者，需要快速把 Web 产品或工具交付到桌面、并能直接使用系统能力，Electron 是极高产、门槛低的选择。

但若你对体积、内存或极致原生体验有严格要求，应考虑 Tauri、Flutter 或原生框架作为替代。

- Tauri 核心：Rust + 系统自带 WebView（WebView2 / WebKit）。 优点：体积小、内存占用低、安全性好、适合注重轻量与性能的应用。 适合：想用 web 技术但要极致小体积或性能敏感的桌面应用。 对比：如果你想快速复用 Node.js 生态，Electron 更方便；若追求小体积，选 Tauri。
- NW.js 跟 Electron 起源相似（也是 Chromium + Node），API 风格不同。 Electron 社区与工具更活跃。
- Neutralino 极轻量，使用系统 WebView，功能比 Electron 少。 更适合简单工具或小型桌面应用。
- Flutter Desktop 使用 Dart/Flutter 渲染，原生表现好、界面一致性高。 适合需要统一跨平台 UI/性能的项目，但要重学 UI 框架（不是 web 技术）。
- React Native for Windows/Mac / .NET MAUI / Qt 更原生的桌面开发路线，适合对系统集成、性能、原生体验有高要求的项目。

选择建议：

- 想迅速把 Web 产品转桌面、或团队主要是 Web 前端 → Electron。
- 想要小体积/更低资源占用 → Tauri/Neutralino。
- 追求原生 UI & 高性能 → Flutter/Native/Qt。


## 性能与体积常见问题

以下是一些优化 Electron 应用性能和体积的实用建议：

- 打包时开启 asar 可合并资源（注意 native 模块兼容）。
- 使用懒加载、减少初始渲染资源，尽量减少主窗口加载的重资源。
- 避免在 renderer 中执行大量 CPU 密集任务，改用 子进程 / worker / native module。
- 使用 single instance、开启硬件加速或禁用视情况调整。
- 优化依赖：减少不必要的 npm 包，避免引入巨大前端库（或用按需加载）。


## 快速上手示例

通过一个最小项目快速了解 Electron 的基本结构。

项目文件结构：

```text
my-electron-app/
├─ package.json    # 项目配置与依赖
├─ main.js         # 主进程入口
├─ preload.js      # 预加载脚本（安全暴露 API）
└─ index.html      # 渲染进程界面
```

package.json（最简配置）：


## 实例

main.js（主进程）：


## 实例

preload.js（受控暴露 API）：


## 实例

index.html（渲染进程界面）：


## 实例

在主进程中监听 IPC（补充到 main.js）：


## 实例

运行：

```text
# 安装依赖
npm install

# 启动应用
npm start
```


## 打包与分发

开发完成后，需要使用打包工具将应用分发给用户。

常见打包工具对比：

打包常见步骤：

- 配置 package.json 的 build 字段（或使用各工具的 config）。
- 使用 CI/CD 构建不同平台（Windows 需在 Windows 环境打包或使用 cross-compile 服务）。
- 上线更新服务器或使用 GitHub Releases + electron-updater。


## 实战建议与最佳实践清单

以下建议来自实际项目经验，可帮助你避开常见陷阱：

- 开始时：用 TypeScript + 打包脚手架（Forge/Builder）能节省后续维护成本。
- 安全：强制 contextIsolation: true，最小化暴露给 renderer 的 API。
- 架构：把业务逻辑放到 renderer（界面）或后端服务，系统/权限操作通过主进程封装。
- 升级：用 electron-updater 做自动更新，但注意签名和发布策略（macOS 要签名、Windows 也需 code signing）。
- 测试：在多个平台真实机器上测试（尤其文件权限、路径、环境变量）。
- 资源：定期检查 Chromium 与 Electron 版本，关注安全补丁（Chromium 漏洞会影响应用）。


## 何时不要用 Electron

以下场景不建议使用 Electron：

- 你需要极低内存占用或非常小的安装包（例如内置设备或极简工具）。
- 需要极致原生 UI 与原生性能（例如 AAA 级游戏或复杂 CAD）。
- 团队不熟悉 Web 技术但熟悉原生开发，可能更适合原生框架。


## 推荐学习路线与资料

按照以下路线循序渐进，可以系统掌握 Electron 开发：

- 学会基本 Node.js 与前端（HTML/CSS/JS）/框架（React/Vue）。
- 阅读 Electron 官方文档（Main/Renderer/Preload/IPC/安全指南）。
- 搭一个最小示例（上面示例）并实验 IPC、文件操作、窗口控制。
- 学习并使用打包工具（Electron Builder / Forge）。
- 读安全最佳实践、自动更新与代码签名的教程。
- 参考成熟开源 Electron 项目（如 VS Code 的源码片段）学习架构。


## 复习重点

- 能说明 `Electron 简介` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

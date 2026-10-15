# DeepSeek Harness：DeepSeek Harness 发布插件：npm / GitHub / tarball

- 来源：[DeepSeek Harness 发布插件](https://www.runoob.com/deepseek-harness/deepseek-harness-publish.html)
- 分类：AI / 智能开发
- 技术：DeepSeek Harness
- 笔记类型：学习笔记
- 章节序号：0240

## 本章内容

本地安装已经跑通了，我们可以把插件分发给别人使用。

发布到注册表不是必须的，有三种途径：npm、tarball、Git。

三者对构建产物的要求完全不同，选错会在用户侧踩坑。


## 三种分发方式对比

官方文档给出三种分发方式，核心区别在于是否分发预构建产物。

npm 与 tarball 都不需要任何构建权限，适合不想让用户做额外授权的场景。

Git 安装最灵活，但要过"构建脚本"这道坎。


## git 安装：构建脚本这道坎

Git 安装拉取的是源码，不是构建产物。

没有任何环节运行你的 build 脚本，因此 TypeScript 包到手时没有 lib/ 输出，加载会失败。

必须两边各做一件事。

作者这边，要提供一个 prepare 脚本。

pnpm 在 git 安装后运行它，从源码构建出发布入口。

它必须自包含：不能假设仅开发环境才有的上下文，例如旁边有一份 monorepo checkout。

turtle-ui 是一个可用的例子：它的 prepare 运行一份专用的 tsdown 配置，直接转译 src/，不用项目引用，也不做类型检查。


## 实例

上面的 prepare 脚本必须自包含：直接转译 src/，不依赖旁边的 monorepo checkout。

用户这边，要为构建授权。

pnpm ≥ 10 在得到显式允许之前，拒绝运行 git 依赖的 prepare 脚本，所以第一次 add 会失败。

dsh 会指出修法：把 pnpm 打印的确切包键复制进该 profile 的 pnpm-workspace.yaml。

```text
dsh plugin --profile demo add github:you/hello-plugin
```

第一次 add 会因为 prepare 未授权而失败，pnpm 会打印确切的包键。

把它复制进 profile 的 pnpm-workspace.yaml，形如下面这样。


## 实例

然后重新执行 add。

```text
dsh plugin --profile demo add github:you/hello-plugin   # 第二次通过
```

请如实看待这项授权：它允许该包的代码在安装时于你的机器上执行，且不在 agent 运行的任何沙箱之内。

只对源码可信的包授权，并锁定 commit（github:you/hello-plugin#<sha>），让后续推送无法悄悄改变实际运行的内容。

锁定 commit 的安装写法如下。

```text
dsh plugin --profile demo add github:you/hello-plugin#a1b2c3d   # 锁定到具体 commit
```


## npm 与 tarball：免构建授权

如果不想让用户做授权，就改为分发构建产物。

以下两种形式都不需要任何构建权限。

第一种，发布到 npm。

在 pnpm publish 时构建好 lib/，用户 dsh plugin add your-package 安装的就是预构建代码。

```text
# 作者侧：先构建再发布
pnpm build
pnpm publish

# 用户侧：安装的是预构建代码，无需授权
dsh plugin add your-package
```

第二种，交付 tarball。

用 pnpm pack 打包，用户执行 dsh plugin add ./hello-plugin-0.1.0.tgz。

```text
# 作者侧：打出 tgz
pnpm pack

# 用户侧：直接安装 tarball 文件
dsh plugin add ./hello-plugin-0.1.0.tgz
```

选择建议：源码可信、想省去构建流程的，用 git 安装并锁定 commit；面向普通用户的，优先发布 npm 或交付 tarball，让用户零授权直接安装。


## 小结与自测

三种分发方式按是否分发预构建产物区分：npm 与 tarball 免构建授权，Git 安装拉源码、需要作者 prepare 自包含脚本与用户 allowBuilds 授权。

自测题：

- 为什么 git 安装对 TypeScript 包会失败？作者需要做什么？
- pnpm ≥ 10 用户第一次 add 失败时，dsh 建议怎么修？
- 为什么建议锁定 commit sha？


## 复习重点

- 能说明 `DeepSeek Harness 发布插件` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

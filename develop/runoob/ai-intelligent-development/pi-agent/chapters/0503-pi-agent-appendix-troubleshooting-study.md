# Pi Agent：Pi Agent 常见问题排查

- 来源：[Pi Agent 见问题排查](https://www.runoob.com/pi-agent/pi-agent-appendix-troubleshooting.html)
- 分类：AI / 智能开发
- 技术：Pi Agent
- 笔记类型：学习笔记
- 章节序号：0503

## 本章内容

以下是 Pi Agent 使用过程中的常见问题和解决方案。


## 安装问题

本节覆盖安装阶段的典型报错与处理路径。


### npm install 失败

现象：执行安装命令后中途报错退出，常见报错集中在版本、网络和权限三类。


### 安装后 pi 命令找不到

现象：安装提示成功，但输入 pi 提示 command not found。

先查看 npm 的全局安装前缀：

```text
$ npm prefix -g
/usr/local
```

再确认该前缀下的 bin 目录是否在 PATH 中：

```text
$ echo $PATH | grep "$(npm prefix -g)/bin"
/usr/local/bin:/opt/homebrew/bin:/usr/bin:/bin
```

目录不在 PATH 中时，这条命令没有任何输出：

```text
$ echo $PATH | grep "$(npm prefix -g)/bin"
```

没有任何输出就说明全局 bin 目录不在 PATH 里，这就是找不到 pi 命令的原因。


## 认证问题

本节覆盖 /login 登录与 API Key 认证失败的处理路径。


### /login 登录失败

表现为输入 /login 后浏览器无法完成跳转，或界面一直停留在等待授权的状态。


### API Key 不生效

现象：已经 export 了环境变量，启动时仍然提示未认证，或继续使用旧的凭证。

按以下顺序检查：

auth.json 中已保存的凭证优先级高于环境变量。

API Key 不生效时先检查 ~/.pi/agent/auth.json，不要只盯着环境变量。


### 模型不可用

现象：模型列表里找不到预期的模型，或调用时提示没有权限。


## 界面问题

本节覆盖终端渲染、图片显示与快捷键三类界面异常。


### 界面显示异常（颜色错误、对齐错乱）

现象：颜色发暗或失真，表格与文本框的边框错位。


### 图片无法显示

现象：发送或粘贴图片后终端中只看到占位符或空白。


### 快捷键不生效

现象：按下文档中描述的快捷键没有任何反应，或触发了终端自身的功能。


## 会话问题

本节覆盖会话文件膨胀与找不到历史会话两类问题。


### 会话文件过大

现象：上下文占用持续走高，响应变慢或提前触发压缩。


### 找不到之前的会话

现象：pi -r 的列表里看不到之前的工作记录。


## 性能问题

本节覆盖响应慢与长上下文下表现下降两类性能问题。


### AI 响应很慢

现象：提交请求后长时间没有首字输出，或整体耗时明显高于平时。

若走代理环境，改用 curl -x $HTTP_PROXY https://api.anthropic.com 测试。

代理环境下 ping 不通不代表 API 不可用。

ping 走的是 ICMP，API 走的是 HTTPS，此时应改用 curl 验证真实链路。


### 大量上下文后 AI 表现下降

现象：对话轮次变多后 AI 开始遗忘此前的约定，或给出重复的答案。


## 代理设置

本节说明在受限网络环境下如何让 Pi Agent 正常访问 API。


### 在国内访问 API

在 settings.json 中配置 HTTP 代理：

```text
{
  "httpProxy": "http://127.0.0.1:7890"
}
```

或者设置环境变量后启动：

```text
$ export HTTP_PROXY=http://127.0.0.1:7890
$ export HTTPS_PROXY=http://127.0.0.1:7890
$ pi
```


## 复习重点

- 能说明 `Pi Agent 见问题排查` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

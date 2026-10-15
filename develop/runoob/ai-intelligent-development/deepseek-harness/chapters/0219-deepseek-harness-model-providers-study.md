# DeepSeek Harness：DeepSeek Harness 模型配置

- 来源：[DeepSeek Harness 模型配置](https://www.runoob.com/deepseek-harness/deepseek-harness-model-providers.html)
- 分类：AI / 智能开发
- 技术：DeepSeek Harness
- 笔记类型：学习笔记
- 章节序号：0219

## 本章内容

DeepSeek Harness 可以使用 DeepSeek 官方的配置，也可以使用第三方模型。

打开 http://127.0.0.1:3080/，整个界面如下，我们可以先点击设置配置 API key：

如果你还没有 API 可以，可以去 https://platform.deepseek.com/api_keys 申请。

接着打开设置 → 模型，DeepSeek 卡片上有一个 API 密钥输入框，填完保存即可。


## 添加目录提供方

目录提供方由 dsh 的已安装目录提供端点、协议和模型列表。

选择添加提供方，选取 Anthropic 或 OpenAI 等提供方，输入其 API 密钥并保存。

已安装目录会自动带来端点、协议和模型列表，不需要你手填。

比如我们设置智谱的 coding plan 套餐：

设置完成后，我们就可以在对话框的模型列表中看到我们添加好的模型：

使用原生认证的提供方需要各自的原生凭据，只填 API 密钥字段无法完成配置。


## 添加自定义提供方

公司网关、自建服务器等目录中不存在的端点，用自定义提供方接入。

选择添加自定义提供方，填写下列字段。

Provider ID 是永久的，因为请求、已保存会话、模型默认值和凭据引用都会使用它。

如需重命名提供方，请添加新提供方并删除旧提供方。

显示名称、基础 URL、协议、凭据和模型仍可编辑。

在模型目录中选择获取可用模型，可查询表单当前显示的基础 URL 和凭据。

选择候选项只会更新草稿，保存前不会存储提供方。

目录提供方使用已安装目录，不发起网络请求。


## 图片输入：给视觉模型声明模态

手动录入的模型默认按纯文本对待，要支持图片必须显式声明。

因为没有任何环节能去询问端点接受哪些模态，所以 dsh 采取"先声明后使用"的策略。

给这类模型附加图片，会在发送前就被拒绝，并点名该模型。

自定义提供方下的视觉模型需要加一行，表单没有对应字段。

请在 $DSH_HOME/settings.yaml 中给该模型加上 input。

```text
# 文件路径：$DSH_HOME/settings.yaml
# 顶层键 llm-pi-ai 是模型路由插件的 id，providers 下按提供方 id 组织
llm-pi-ai:
  providers:
    my-gateway:
      apiKeyEnv: GATEWAY_API_KEY          # 凭据引用：从 GATEWAY_API_KEY 环境变量读取
      api: openai-completions             # API 协议：OpenAI 兼容的补全协议
      baseURL: https://gateway.runoob.example/v1  # 你的网关端点
      models:
        - id: legacy-chat                 # 纯文本模型，不写 input 即按纯文本对待
        - id: vision-preview              # 视觉模型
          input: [text, image]            # 声明同时接受文本与图片
```

input 接受 text 和 image，且只作用于该模型，因此一条路由可以同时服务两类模型。

省略它，或写成空列表，两者同义。

此时保留已安装目录为该模型记录的模态；目录未描述的模型则回退到该路由的 defaultInput。

如果你手动录入的模型全都接受图片，可以在路由上设置一次回退值。

```text
# 文件路径：$DSH_HOME/settings.yaml
# defaultInput 是回退值而不是覆盖值，默认为 [text]
llm-pi-ai:
  providers:
    vision-gateway:
      apiKeyEnv: GATEWAY_API_KEY
      api: openai-completions
      baseURL: https://vision.runoob.example/v1
      defaultInput: [text, image]         # 对本路由下目录未描述的模型生效
      models:
        - id: first-model
        - id: second-model
```

要收窄目录提供方中某个模型的模态，写在 modelOverrides 下，以模型 id 为键。

```text
# 文件路径：$DSH_HOME/settings.yaml
# 目录提供方没有可填写的 models 列表，覆盖走 modelOverrides
llm-pi-ai:
  providers:
    anthropic:
      modelOverrides:
        claude-sonnet-4-5:
          input: [text]                   # 把该模型的图片能力去掉
```

input 与 defaultInput 都是对你端点的断言，而不是对它的检查。

声明了端点并不提供的图片能力的模型，不会在这里被拦下，改由提供方拒绝该请求。


## 排错表

模型配置出错时，dsh 会给出明确的错误信息，对照下表排查。


## 复习重点

- 能说明 `DeepSeek Harness 模型配置` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

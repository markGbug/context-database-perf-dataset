# DeepSeek Harness：DeepSeek Harness 多模态

- 来源：[DeepSeek Harness 多模态](https://www.runoob.com/deepseek-harness/deepseek-harness-modality.html)
- 分类：AI / 智能开发
- 技术：DeepSeek Harness
- 笔记类型：概念卡
- 章节序号：0222

## 本章内容

DeepSeek 上线了实验性质的多模态视觉理解模型 DeepSeek-V4-Flash-Vision-Exp，并同步开放多模态 API 服务与免费的 Files API。

使用前安装最新版本：

```text
npm install -g @deepseek-ai/dsh@latest
```

更新到最新版后，可以看到模型已经有了 DeepSeek-V4-Flash-Vision-Exp：

切换到视觉模型，然后我们可以直接推动图片或者 ppt 文件到文档中，让它看看图片中的内容（ 测试图片下载）：


### 什么是多模态

要理解多模态，先要理解"模态"（modality）这个词，模态指的是信息的不同表现形式：文字是一种模态，图片、音频、视频各自也是不同的模态。

过去的大语言模型只处理文本一种模态，你发给它的所有内容都必须先变成文字。

多模态模型则可以同时接收图片和文字，把它们统一转换成 token 序列后一起处理。

关键在于：图片并不是被模型"直接看到"的，而是先由视觉编码器切成小块（patch）并转成向量，再与文本 token 拼成同一个序列。

图片也会消耗 token，一张图片最多占 384 tokens，这正是后文多模态计费规则的来源。

对 Agent 来说，多模态带来的是质变，而不是锦上添花。


## V4-Flash-Vision-Exp：多模态视觉模型上线

DeepSeek-V4-Flash-Vision-Exp 是一个实验性质的多模态视觉理解模型，现已上线 DeepSeek API 平台。

用户通过设置 model='deepseek-v4-flash-vision-exp' 即可访问该模型。

它的能力定位可以用一句话概括：文本能力不缩水，视觉能力大跃升。

在纯文本能力（Agent、推理、世界知识等）方面，它与 DeepSeek-V4-Flash 正式版持平。

在需要视觉理解的 Agent Benchmark 上，它相比 DeepSeek-V4-Flash 实现了大幅跃升，多模态 Agent 能力已接近 Opus-4.8。

测评口径说明：对于公开基准测试集中的 Code Agent 文本任务，DeepSeek 系列模型使用 DeepSeek Harness 极简模式作为框架进行测试，使用 max 档位，temperature=1.0，topp=0.95。

在 ApexBench 与 Agents' Last Exam 测评中，文本模型 DeepSeek-V4-Flash 会忽略其中的多模态元素。


## 多模态 API 快速开始

多模态 API 支持 Chat Completions、Messages、Responses 三种格式调用，可以方便地接入各类 Agent 工具。

三种格式的能力一致，按你熟悉的接口风格选择即可。

三种格式都支持图文混合输入，图片有 base64 内联、外部 URL、Files API 三种传入方式。


### 方式一：base64 内联

本地图片编码成 base64 字符串后，以 data URL 的形式直接写进请求体。


## 实例

运行输出：

```text
图片中的文字是 "RUNOOB"。
```


### 方式二：外部 URL

图片部署在可公开访问的服务器上，请求里只传一个 URL 字符串，请求体很小。


## 实例

URL 必须是平台可访问的公网地址，内网地址与本地回环地址都无法被拉取。

base64 与 URL 两种方式都可以在 image_url 里加一个可选的 detail 字段，控制图片的解析精度。

批量跑截图类任务时把 detail 设为 low，是控制多模态成本最直接的手段。


### Messages 与 Responses 格式

已有 Anthropic 或新版 OpenAI 风格代码的，几乎可以无缝切换到 DeepSeek 多模态。

Messages 格式使用 image 内容块，图片通过 source 字段传入。


## 实例

Responses 格式使用 input 数组，文本用 input_text，图片用 input_image。


## 实例


## Files API：先上传，后引用

Files API 现已开放，该 API 不收费。

用户可以先把图片上传到平台，之后在请求中通过 file_id 引用。

这样做有两个直接好处：请求里不再携带大段 base64，节省请求带宽；同一张图片在多个请求中无需重复上传。

第一步，上传图片并拿到 file_id。


## 实例

上传成功后，平台返回文件的元信息。


## 实例

上传时还可以用 expires_after 参数指定有效期，取值 1 小时到 30 天，不传则永久有效。

第二步，在多模态请求中用 file_id 引用这张图片。

```text
{
  "model": "deepseek-v4-flash-vision-exp",
  "messages": [
    {
      "role": "user",
      "content": [
        {"type": "text", "text": "这个图表的整体趋势是什么？"},
        {"type": "file", "file_id": "file-api-qw3x8v2m6n"}
      ]
    }
  ]
}
```

什么时候用 Files API？

同一张图片要在多个请求里反复使用时（比如批量跑同一批截图的 Agent 任务），先上传一次、处处引用，比每次都传 base64 更省带宽也更快。

file 块还支持 file_data 直接内联 base64（与 file_id 互斥，可搭配 filename 字段），适合偶尔绕过上传步骤的场景。

经 Anthropic 兼容的 Messages 端点引用 file_id 时，需要额外带上请求头 anthropic-beta: files-api-2025-04-14。


## 计费说明与注意事项

多模态请求按 token 计费，图片会被转换成 token 后参与计费。

图片 token 会占用上下文窗口，多图任务要留意总消耗：10 张图片最多可能占用 3840 tokens。

图片在进入模型前会被自动缩放：小于约 384×384 的图片会被放大，更大的图片会被缩小到约相当于 800×800 的总像素。

因此 token 消耗只与缩放后的尺寸相关，2000×2000 与 5000×5000 的图片消耗相同；多图请求中每张图片独立按同一规则计算。

base64 会让请求体明显变大，大图或高频调用建议改用外部 URL 或 Files API。

多模态请求还有一些硬性限制，超出会直接返回 400 错误。

V4-Flash-Vision-Exp 是实验性质的模型，能力与服务规格可能随版本迭代调整，关键生产链路建议同时评估正式版模型。

更完整的使用说明可参考官方 API 文档：API 指南 - 图像理解、API 指南 - Files API。


## 总结

V4-Flash-Vision-Exp 用"文本不缩水、视觉大跃升"的定位，把多模态能力带进了 DeepSeek 的 Agent 生态。

对开发者来说，上手成本很低：换一个 model 名称，就能让 DeepSeek Harness 里的 Agent 看懂截图、设计稿与图表。

建议先用官方三个实例找感觉，再把自己的业务图片接进来，跑通第一个"看图干活"的 Agent 任务。


## 记忆卡片

- 一句话定义：`DeepSeek Harness 多模态` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。

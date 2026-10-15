# Python：Python AI 绘画

- 来源：[Python AI 绘画](https://www.runoob.com/python3/python-ai-draw.html)
- 分类：Python / 数据科学
- 技术：Python
- 笔记类型：练习笔记
- 章节序号：4147

## 本章内容

本文我们将为大家介绍如何基于一些开发 API 或开源的库来搭建一套自己的 AI 作图工具。


## 通过文生图 API

通过文生图 API，您可以基于文本描述创造出全新的原创图像。

阿里云百炼提供两大系列模型：

- 通义千问（Qwen-Image）: 擅长渲染复杂的中英文文本，本章节以这个为例。
- 通义万相（Wan系列）: 用于生成写实图像和摄影级视觉效果。

通过运行以下命令安装 DashScope Python SDK：

```text
# 如果运行失败，您可以将pip替换成pip3再运行
pip install -U requests dashscope
```

我们需要开通阿里云百炼模型服务并获得 API-KEY。

我们可以先使用阿里云主账号访问百炼模型服务平台：https://bailian.console.aliyun.com/，然后点击右上角登录，登录成功后点击右上角的齿轮⚙️图标，选择 API key，然后复制 API key，如果没有也可以创建 API key：

开通阿里云百炼不会产生费用，仅模型调用（超出免费额度后）、模型部署、模型调优会产生相应计费。

现在要使用 API，都需要按 token 来计费，还好都不贵，我们可以先购买个最便宜的包：阿里云百炼大模型服务平台。

接下来我们通过设置提示词来生成图片：


## 实例

输出结果类似如下，会看到有个 url 的参数，我们访问它就可以下载通过提示词描述的图片了：

```text
----同步调用，请等待任务执行----
response: {"status_code": 200, "request_id": "1968746e-f434-4f77-9f8c-9b1adb80e8d7", "code": null, "message": "", "output": {"task_id": "d85c65d9-c4ff-4d66-a895-7c7746620b0c", "task_status": "SUCCEEDED", "results": [{"url": "https://dashscope-result-sh.oss-cn-shanghai.aliyuncs.com/7d/05/20250916/8d68e658/d85c65d9-c4ff-4d66-a895-7c7746620b0c-1.png?xxxxxxxxx",
...
```

以上实例生成的图片如下：

更多内容可以参考官方文档：https://help.aliyun.com/zh/model-studio/text-to-image


## Stable Diffusion

需要使用的开源库为 Stable Diffusion web UI，它是基于 Gradio 库的 Stable Diffusion 浏览器界面

Stable Diffusion web UI GitHub 地址：https://github.com/AUTOMATIC1111/stable-diffusion-webui

运行 Stable Diffusion 需要硬件要求比较高，运行时会消耗较大的资源，特别是显卡。


### Windows 环境安装

本地环境要求安装 Python 3.10.6 或以上版本，并把它加入到本机的环境变量中。

下载 Stable Diffusion web UI GitHub 源码 https://github.com/AUTOMATIC1111/stable-diffusion-webui。

```text
git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui.git
```

如果没有安装 Git ，可以在右上角下载 zip 压缩包。

解压 stable-diffusion-webui，并进入 stable-diffusion-webui 目录。

接下来我们需要下载模型，下载地址：https://huggingface.co/CompVis/stable-diffusion-v-1-4-original

将下载的模型移动到 stable-diffusion-webui/models/Stable-diffusion 目录下。

进入 stable-diffusion-webui 目录：

Windows 使用非管理员运行:

```text
webui-user.bat
```

Linux 和 Mac OS 环境执行以下命令：

```text
./webui.sh
```

接下来程序就会自动安装并启动，启动成功会看到一个可访问的 URL 地址 http://127.0.0.1:7860：

访问 http://127.0.0.1:7860，界面如下：


### Civitai 介绍

Civitai 有许多定制好的模型，而且可以免费下载，我们使用国风3模型来测试，下载地址：https://civitai.com/models/10415/3-guofeng3?modelVersionId=36644

下载完后，我们将模型移动到 stable-diffusion-webui/models/Stable-diffusion 目录下，重新启动 stable-diffusion-webui ：

```text
./webui.sh
```

这样我们就可以在模型列表中选择国风3模型了：

选择后，我们可以到模型介绍页面去拷贝一些提示词和测试参数：

​为了快速生成，我高度跟宽度都减半了，之后点生成按钮即可：

生成完整过程，可以关注我们微信视频号查看：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Python AI 绘画` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

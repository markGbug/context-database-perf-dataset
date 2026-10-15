# Ollama：Ollama 搭建类似 ChatGPT 网页应用

- 来源：[Ollama 类似 ChatGPT 应用](https://www.runoob.com/ollama/ollama-chatgpt-webapp.html)
- 分类：AI / 智能开发
- 技术：Ollama
- 笔记类型：概念卡
- 章节序号：0412

## 本章内容

本章节我们将搭建类似 ChatGPT 应用：多会话切换、历史持久化到数据库、完整前端界面，以及三种部署方式。


## 功能规划与数据模型

一个可用的聊天产品至少需要四个能力：多会话隔离、历史持久化、流式回复、会话管理（新建与删除）。

支撑这些能力的数据库模型只需要两张表：

chats 存会话列表，messages 按外键归组存每条消息。切换会话时，把对应 messages 组装成 Ollama 的 messages 数组即可恢复完整上下文。

技术栈延续最小依赖原则：Flask + sqlite3（Python 标准库）+ 原生 JavaScript 前端，零前端框架。

安装 flask 和 ollama 扩展：

```text
pip install flask ollama
```

载入模型：

```text
ollama pull qwen3.5:4b
```


## 后端：会话与消息的完整 API

后端职责清晰：管理两张表，并把 /api/chat 的流式回复逐条写库。


## 实例


## 后端核心：流式对话与历史写回

对话接口做三件事：取历史拼上下文、流式生成、把完整回复写回数据库。


## 实例


## 前端：原生 JS 的聊天界面

前端做到功能完整且足够简单：左侧会话列表，右侧消息区加输入框，fetch 流式渲染。


## 实例

启动并访问：

```text
python server.py
```

浏览器打开 http://localhost:5000 就可以看到生成的页面。

验证三个核心功能：切换左侧会话后历史完整恢复；新会话之间互不干扰；重启 server.py 后历史依然存在（已持久化到 chats.db）。


## 部署上线：三个层级

云服务器上用 systemd 让应用常驻：


## 实例

设置长期运行：

```text
sudo systemctl daemon-reload
sudo systemctl enable --now runoob-chat
```

对外部署的完整安全清单（回环端口、反代鉴权、暴露面自查）在安全与合规章节，上线前务必过一遍。


## 记忆卡片

- 一句话定义：`Ollama 类似 ChatGPT 应用` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。

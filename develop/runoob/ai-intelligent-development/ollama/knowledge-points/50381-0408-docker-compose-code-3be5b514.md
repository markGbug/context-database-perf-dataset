# 知识点 50381：Ollama：Ollama 私有化与团队部署 - Docker 与 Compose 编排

- 来源：[Ollama 私有化与团队部署](https://www.runoob.com/ollama/ollama-team-deployment.html)
- 来源章节：[0408-ollama-team-deployment-concept.md](../chapters/0408-ollama-team-deployment-concept.md)
- 分类：AI / 智能开发
- 技术：Ollama
- 所在小节：Docker 与 Compose 编排
- 知识类型：代码
- 原章节序号：0408

## 原文片段

```text
# 文件路径：docker-compose.yml
services:
  ollama:
    image: ollama/ollama          # AMD 显卡改用 ollama/ollama:rocm
    container_name: ollama
    restart: unless-stopped
    volumes:
      - ollama:/root/.ollama      # 模型持久化，升级镜像不丢模型
    ports:
      - "127.0.0.1:11434:11434"   # 只暴露给本机，交给 Nginx 对外
    # NVIDIA GPU 直通（需要先装好 NVIDIA Container Toolkit）
    deploy:
      resources:
        reservations:
          devices:
            - driver: nvidia
              count: all
              capabilities: [gpu]

volumes:
  ollama:
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `Docker 与 Compose 编排` 这一小节和 `Ollama 私有化与团队部署` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？

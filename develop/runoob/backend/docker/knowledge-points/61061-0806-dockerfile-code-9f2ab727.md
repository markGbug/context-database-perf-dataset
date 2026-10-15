# 知识点 61061：Docker：Docker Dockerfile - 使用 Dockerfile 定制镜像

- 来源：[Docker Dockerfile](https://www.runoob.com/docker/docker-dockerfile.html)
- 来源章节：[0806-docker-dockerfile-practice.md](../chapters/0806-docker-dockerfile-practice.md)
- 分类：后端开发
- 技术：Docker
- 所在小节：使用 Dockerfile 定制镜像
- 知识类型：代码
- 原章节序号：0806

## 原文片段

```text
FROM nginx
RUN echo '这是一个本地构建的nginx镜像' > /usr/share/nginx/html/index.html
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `使用 Dockerfile 定制镜像` 这一小节和 `Docker Dockerfile` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？

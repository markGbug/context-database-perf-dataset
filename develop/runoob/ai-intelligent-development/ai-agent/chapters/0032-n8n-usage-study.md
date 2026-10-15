# AI Agent（智能体）：n8n 入门教程

- 来源：[n8n 入门教程](https://www.runoob.com/ai-agent/n8n-usage.html)
- 分类：AI / 智能开发
- 技术：AI Agent（智能体）
- 笔记类型：学习笔记
- 章节序号：0032

## 本章内容

n8n（读作 "n-eight-n"，意为 "nodemation"）是目前最受技术团队青睐的开源工作流自动化平台。

n8n 的核心优势是：可视化画布 + 原生代码支持 + 完全自托管——既能让非开发者拖拽搭建，又能让开发者在任意节点写 JavaScript 或 Python，而且可以运行在你自己的服务器上，数据在本地。

n8n 是一个工作流自动化平台，让你能够将 AI 安全可控地集成到工作和流程中。

n8n 把可视化构建体验与代码能力结合在一起——可以在工作流的任意地方写 JavaScript 或 Python，在每个步骤的输入输出旁边即时查看结果。


### Dify 与 n8n 的区别

和 Dify 不同，n8n 的核心是通用自动化和系统集成，AI 是其中一个强大的组件，而 Dify 的核心是 AI 应用开发，自动化是辅助能力。

简单说：

- 需要把多个 SaaS 系统连接起来、数据在系统间流转：n8n 是更好的选择
- 需要搭建一个以 AI 对话为核心的应用（客服机器人、RAG 问答）：Dify 是更好的选择


### 适合谁用

n8n 的视觉界面让非开发者可以快速设计和测试工作流，随着复杂度增加，开发者可以用 Function 节点、外部脚本或自定义集成来扩展。

这让团队可以增量式地叠加结构、验证和控制。

最典型的用户群：


## 核心概念

在开始学习前，我们先理解这几个核心概念。


### 工作流（Workflow）

一个工作流是一系列节点的有向图，定义了「当 X 发生时，执行 Y，然后执行 Z」的逻辑。

工作流有两种状态：激活（Active）时响应触发器自动运行，非激活（Inactive）时只能手动执行用于测试。


### 节点（Node）

工作流的基本构建块，每个节点执行一个具体操作：


### 执行（Execution）

工作流的一次完整运行叫做一次执行。

n8n 的执行计费方式是：一次执行 = 工作流跑一遍，无论里面有多少个步骤或处理多少数据。


### 连接（Connection）

节点之间的箭头，定义数据流向和执行顺序。一个节点可以有多个输出，实现分支逻辑。


### 凭证（Credential）

存储 API Key、OAuth Token、数据库密码等敏感信息的安全容器。

凭证加密存储，可以被多个工作流共用，不会在工作流 JSON 里明文暴露。


### 表达式（Expression）

n8n 的动态值语法，用双花括号包裹：{{ $json.fieldName }}。

让节点参数可以引用上游节点的输出，而不是固定值。


## 安装与启动

五种安装方式，从本地快速体验到企业级高可用部署。


### 方式一：本地快速体验（最快，5 分钟）

使用 npx 或全局安装，无需额外配置。

```text
# 使用 npx，无需安装（需要 Node.js 18+）
npx n8n

# 或全局安装
npm install -g n8n
n8n start
```

打开浏览器访问 http://localhost:5678，完成账号注册即可使用。

如果忘记邮箱密码，使用 npx n8n user-management:reset 命令来重置。


### 方式二：Docker 单容器（推荐个人和小团队）

一条命令启动，数据持久化到本地目录。

```text
# 创建数据持久化目录
mkdir -p ~/.n8n

# 启动 n8n 容器
docker run -d \
  --name n8n \
  -p 5678:5678 \
  -v ~/.n8n:/home/node/.n8n \
  -e N8N_ENCRYPTION_KEY="your-random-32-char-secret-key" \
  docker.n8n.io/n8nio/n8n:latest
```

访问 http://localhost:5678 完成设置。


### 方式三：Docker Compose + PostgreSQL（推荐生产环境）

适合生产环境，数据存储在 PostgreSQL，支持更稳定的并发访问。

创建 docker-compose.yml：

```text
version: "3.8"

services:
  postgres:
    image: postgres:16-alpine
    restart: always
    environment:
      POSTGRES_DB: n8n
      POSTGRES_USER: n8n
      POSTGRES_PASSWORD: ${POSTGRES_PASSWORD}
    volumes:
      - postgres_data:/var/lib/postgresql/data
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U n8n"]
      interval: 10s
      timeout: 5s
      retries: 5

  n8n:
    image: docker.n8n.io/n8nio/n8n:latest
    restart: always
    ports:
      - "5678:5678"
    environment:
      # 数据库连接配置
      DB_TYPE: postgresdb
      DB_POSTGRESDB_HOST: postgres
      DB_POSTGRESDB_DATABASE: n8n
      DB_POSTGRESDB_USER: n8n
      DB_POSTGRESDB_PASSWORD: ${POSTGRES_PASSWORD}
      # 安全配置
      N8N_ENCRYPTION_KEY: ${N8N_ENCRYPTION_KEY}
      N8N_SECURE_COOKIE: "false"          # 如果没有 HTTPS，设为 false
      # 访问地址（替换为你的实际域名）
      WEBHOOK_URL: https://your-domain.com
      N8N_EDITOR_BASE_URL: https://your-domain.com
      # 时区设置
      GENERIC_TIMEZONE: Asia/Shanghai
      TZ: Asia/Shanghai
    volumes:
      - n8n_data:/home/node/.n8n
    depends_on:
      postgres:
        condition: service_healthy

volumes:
  postgres_data:
  n8n_data:
```

创建 .env 文件：

```text
POSTGRES_PASSWORD=your-strong-postgres-password
N8N_ENCRYPTION_KEY=your-32-char-random-encryption-key
```

生成安全的加密密钥：

```text
# 生成 24 字节的 base64 随机密钥
openssl rand -base64 24
```

启动服务：

```text
# 后台启动所有服务
docker compose up -d

# 查看日志，等待启动完成
docker compose logs -f n8n
```


### 方式四：配置反向代理（Nginx + HTTPS）

生产部署建议配置 Nginx，方便绑定域名和 HTTPS。

```text
server {
    listen 80;
    server_name n8n.yourdomain.com;
    return 301 https://$host$request_uri;
}

server {
    listen 443 ssl;
    server_name n8n.yourdomain.com;

    # SSL 证书路径（使用 Let's Encrypt 自动签发）
    ssl_certificate     /etc/letsencrypt/live/n8n.yourdomain.com/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/n8n.yourdomain.com/privkey.pem;

    # n8n WebSocket 支持
    location / {
        proxy_pass http://localhost:5678;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_read_timeout 300s;
        proxy_send_timeout 300s;
    }

    # MCP SSE 端点专项配置
    location ~* ^/mcp {
        proxy_pass http://localhost:5678;
        proxy_buffering off;
        gzip off;
        chunked_transfer_encoding off;
        proxy_set_header Connection "";
    }
}
```

申请 SSL 证书（Let's Encrypt）：

```text
# 自动配置 Nginx 并申请 SSL 证书
certbot --nginx -d n8n.yourdomain.com
```


### 方式五：Kubernetes（高可用，企业级）

对于需要高可用的团队，使用官方 Helm Chart。

```text
# 添加 n8n Helm 仓库
helm repo add n8n https://n8n-helm-chart.netlify.app

# 安装 n8n，启用 PostgreSQL 和 Redis
helm install n8n n8n/n8n \
  --set n8n.encryption_key="your-key" \
  --set postgresql.enabled=true \
  --set redis.enabled=true   # 队列模式需要 Redis
```

高可用架构需要配置「队列模式」（Queue Mode），使用 Redis 作为消息队列，允许多个 Worker 节点并行处理任务。


### 系统要求

不同使用场景的硬件推荐：

数据库建议：n8n 默认使用 SQLite，但生产环境强烈推荐 PostgreSQL。PostgreSQL 性能更好，支持并发访问，更易备份。


## 界面导览：第一次打开 n8n

了解 n8n 的主要界面区域，快速上手操作。


### 左侧导航栏

我们可以配置 API 可以，比如 DeepSeek，点击 New Chat 菜单，点击左上角的模型，在下拉列表选择 DeepSeek：

然后配置 API key：

配置成功后，点击左上角的模型，在下拉列表选择 DeepSeek 的模型：

就可以开始聊天了：


### 工作流画布

画布操作快捷键：


### 节点面板

点击任意节点打开配置面板，分为三个标签页：


### 顶部工具栏


## 构建第一个工作流

通过一个完整示例上手：每天早上 8 点自动抓取 Hacker News 热门文章，格式化后发送到 Slack 频道。


### 步骤一：创建工作流

左侧选择 Workflows，点击 New Workflow（新建工作流），重命名为「HN 早报」。


### 步骤二：添加定时触发器

点击 + 按钮，搜索「Schedule」，选择 Schedule Trigger。

配置说明：

```text
Trigger Rule：0 8 * * 1-5（周一到周五早上 8 点）
或使用界面选择器：Hour → 8，Weekday → Mon to Fri
```


## 后续章节

- 步骤三：抓取 HN 数据
- 步骤四：限制取前 5 条
- 实例
- 步骤五：并行获取每条文章详情
- 步骤六：格式化消息
- 实例
- 步骤七：发送到 Slack
- 步骤八：测试运行
- 步骤九：激活工作流
- 常用节点详解
- 触发器类节点
- 数据处理节点
- 实例
- 实例
- 数据库节点
- 凭证管理：安全连接外部服务

## 复习重点

- 能说明 `n8n 入门教程` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

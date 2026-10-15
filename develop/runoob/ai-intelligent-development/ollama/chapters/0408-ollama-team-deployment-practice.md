# Ollama：Ollama 私有化与团队部署

- 来源：[Ollama 私有化与团队部署](https://www.runoob.com/ollama/ollama-team-deployment.html)
- 分类：AI / 智能开发
- 技术：Ollama
- 笔记类型：练习笔记
- 章节序号：0408

## 本章内容

一台带显卡的服务器，可以成为整个团队的共享模型服务：容器化编排、内网共享、反向代理、模型分发，本篇把这些拼成一套完整的团队部署方案。

核心认知先建立：Ollama 自身没有鉴权机制，安全边界要靠反向代理和网络策略来搭。


## 团队部署拓扑总览

推荐的标准拓扑是三段式：成员流量先到反向代理，代理完成鉴权后转发给只听本机回环的 Ollama 服务。

这个结构的关键设计是 Ollama 只监听 127.0.0.1，所有外部访问必须经过代理，鉴权入口因此唯一且可控。


## Docker 与 Compose 编排

服务器部署首选 Docker，团队场景用 Compose 固化配置：

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

docker 相关命令：

```text
# 启动 / 查看日志 / 升级
docker compose up -d
docker compose logs -f ollama
docker compose pull && docker compose up -d
```

注意 ports 映射写的是 127.0.0.1:11434:11434 而不是 11434:11434：前者把端口限制在本机回环，外部只能经 Nginx 访问；后者等于把无鉴权服务直接暴露到网卡上，是最常见的团队安全事故来源。


## 局域网共享一台模型服务器

小团队不想搭代理时，最低成本的共享方式是让 Ollama 直接监听内网：

```text
# 服务器端：监听所有网卡
OLLAMA_HOST=0.0.0.0:11434 ollama serve
```

成员机器上把 OLLAMA_HOST 指向服务器，本地的 ollama 命令就会操作远程服务：

```text
# 成员电脑：CLI 与 SDK 都认这个变量
export OLLAMA_HOST=http://192.168.1.100:11434

# 之后所有命令都作用在服务器上
ollama run qwen3.5
```

多人共享的容量规划直接引用配置章节的公式：并发请求数乘以上下文长度决定显存占用，10 人团队不建议把 NUM_PARALLEL 开到 10，排队往往比挤爆显存更体面。


## 反向代理与隧道


### Nginx 反向代理（推荐）

```text
# 文件路径：/etc/nginx/conf.d/ollama.conf
server {
    listen 80;
    server_name model.example.com;   # 换成你的域名或内网 IP

    location / {
        proxy_pass http://localhost:11434;
        proxy_set_header Host localhost:11434;
        # Ollama 流式响应为 NDJSON，建议关闭缓冲避免"卡顿"
        proxy_buffering off;
    }
}
```


### 临时隧道：ngrok 与 Cloudflare Tunnel

演示、远程联调场景可以用隧道把本地服务临时暴露到公网：

```text
# ngrok
ngrok http 11434 --host-header="localhost:11434"

# Cloudflare Tunnel
cloudflared tunnel --url http://localhost:11434 --http-host-header="localhost:11434"
```

隧道等于把无鉴权服务开到了公网，仅建议短期演示使用，用完即关；长期外部访问请走带鉴权的 Nginx 方案。


## 鉴权：自己动手补上安全边界

Ollama 没有内建账号体系，团队部署必须自建鉴权，常见三条路：

以最常用的 Nginx Basic Auth 为例：

```text
# 生成密码文件
sudo htpasswd -c /etc/nginx/.htpasswd zhangsan

# Nginx location 块中追加两行：
# auth_basic "Ollama API";
# auth_basic_user_file /etc/nginx/.htpasswd;
```

以上鉴权方案来自社区通行实践而非 Ollama 官方功能，选择时按团队现有基础设施走，原则只有一条：不要让 11434 直接暴露在不受信网络中。


## 私有模型的分发与版本管理

团队定制的好模型需要一套分发机制，Ollama 的方案是命名空间加推送。

流程分四步：注册 ollama.com 账号；在官网设置页绑定本机公钥（~/.ollama/id_ed25519.pub）；把模型复制成带用户名的名字；推送。

```text
# 复制成带命名空间的名字，用 tag 标版本
ollama cp runoob-helper myteam/runoob-helper:v1

# 推送到 ollama.com
ollama push myteam/runoob-helper:v1

# 成员拉取使用（私有模型需登录授权账号）
ollama run myteam/runoob-helper:v1
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Ollama 私有化与团队部署` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

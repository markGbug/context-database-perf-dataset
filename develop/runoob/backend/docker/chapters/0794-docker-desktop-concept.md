# Docker：Docker Desktop

- 来源：[Docker Desktop](https://www.runoob.com/docker/docker-desktop.html)
- 分类：后端开发
- 技术：Docker
- 笔记类型：概念卡
- 章节序号：0794

## 本章内容

Docker Desktop 是 Docker 官方推出的 本地容器化开发环境，用于在 macOS / Windows（以及部分 Linux） 上：

- 运行 Docker Engine
- 构建、运行、管理容器和镜像
- 提供图形化管理界面（GUI）
- 集成 Kubernetes（可选）

一句话概括：

Docker Desktop = Docker Engine + Linux VM + GUI + 开发者体验优化

Docker Desktop 已经成为 本地 Docker 开发的事实标准。


### 为什么要使用 Docker Desktop

在没有 Docker Desktop 之前，本地使用 Docker 存在大量问题：

- macOS / Windows 不能原生运行 Docker
- 需要手动安装虚拟机（VirtualBox）
- 网络、文件挂载、端口映射配置复杂

Docker Desktop 解决了这些问题：


## Docker Desktop 的整体架构

理解架构有助于避免常见误解。

```text
宿主系统（macOS / Windows）
 └── Docker Desktop
      └── Linux 虚拟机
           └── Docker Engine
                ├── Images
                ├── Containers
                └── Volumes
```

关键点：

- Docker 实际运行在 Linux VM 中
- 本地看到的文件、端口、进程是"映射结果"
- 这也是文件挂载、性能问题的根源


## 安装 Docker Desktop


### 系统要求

- macOS（Apple Silicon / Intel）
- Windows 10 / 11（建议 WSL2）
- 至少 4GB 内存（推荐 8GB+）


### 安装流程（概念性说明）

- 下载 Docker Desktop 安装包，下载地址：https://www.docker.com/products/docker-desktop/
- 拖入应用目录 / 完成安装向导，Windows 用户在安装过程中确保勾选 "Use WSL 2 instead of Hyper-V"。
- 启动 Docker Desktop
- 等待 Docker Engine 启动完成

启动成功后：

- 菜单栏出现 Docker 图标
- docker version 能正常输出


## Docker Desktop 界面快速认识

Docker Desktop 的 GUI 主要分为以下模块：


## 核心概念：镜像与容器

理解 Docker 只需要记住这个简单的类比：


## 记忆卡片

- 一句话定义：`Docker Desktop` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。

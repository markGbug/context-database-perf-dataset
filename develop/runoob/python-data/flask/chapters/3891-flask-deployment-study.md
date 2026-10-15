# Flask：Flask 部署

- 来源：[Flask 部署](https://www.runoob.com/flask/flask-deployment.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：学习笔记
- 章节序号：3891

## 本章内容

开发完成后，需要将 Flask 应用部署到生产环境，让真实用户能够访问。

本章介绍从开发到生产的关键步骤和注意事项。


## 开发服务器 vs 生产服务器

重要：Flask 内置的开发服务器（flask run）仅适用于开发环境。它不具备生产环境所需的安全性、稳定性和性能。生产环境必须使用专业的 WSGI 服务器。


## 部署检查清单

在部署之前，确保以下事项都已完成：


## 实例

完整检查清单：


## 使用 Waitress 部署（Windows/macOS/Linux）

Waitress 是一个纯 Python WSGI 服务器，跨平台，安装简单：

```text
(.venv) $ pip install waitress
```


## 实例

启动：

```text
(.venv) $ python run.py
Serving on http://0.0.0.0:8000
```


## 使用 Gunicorn 部署（Linux/macOS）

Gunicorn 是 Linux 环境下最流行的 Python WSGI 服务器，性能优秀：

```text
(.venv) $ pip install gunicorn
```

启动 Gunicorn（直接在命令行指定应用）：

```text
# 基本用法：4 个 worker 进程
$ gunicorn -w 4 -b 0.0.0.0:8000 "app:create_app()"

# 参数说明：
# -w 4       : 启动 4 个 worker 进程（通常设为 CPU 核心数 × 2 + 1）
# -b 0.0.0.0:8000 : 监听所有网络接口的 8000 端口
# "app:create_app()" : 模块名:工厂函数（与 flask --app 语法相同）
```

Gunicorn worker 类型选择：

Gunicorn 不支持 Windows。如果你在 Windows 上部署，请使用 Waitress。


## 使用 Nginx 反向代理

在生产环境中，通常用 Nginx 作为反向代理放在 WSGI 服务器前面：

- Nginx 处理静态文件（CSS、JS、图片），效率远高于 Python
- Nginx 提供 HTTPS 终端（SSL 终结）
- Nginx 做负载均衡，分发请求到多个后端 worker

一个最小化的 Nginx 配置示例：


## 实例

启用配置并重载 Nginx：

```text
$ sudo ln -s /etc/nginx/sites-available/runoob /etc/nginx/sites-enabled/
$ sudo nginx -t          # 检查配置语法
$ sudo systemctl reload nginx
```


## 使用 systemd 管理服务（Linux）

创建 systemd 服务文件，让 Flask 应用开机自启并在崩溃后自动重启：


## 实例

启动和管理服务：

```text
$ sudo systemctl daemon-reload        # 重载配置文件
$ sudo systemctl enable runoob        # 设置开机自启
$ sudo systemctl start runoob         # 启动服务
$ sudo systemctl status runoob        # 查看服务状态
$ sudo journalctl -u runoob -f        # 实时查看日志
```


## WSGI 服务器速查


## 教程总结

恭喜你完成了 Flask 入门教程的全部内容！

回顾一下你学到的知识：

继续学习的推荐方向：

- Flask-SQLAlchemy：功能更强大的数据库集成
- Flask-Login：用户认证和权限管理
- Flask-WTF：表单处理和 CSRF 保护
- Flask-Migrate：数据库迁移管理
- Flask-RESTful 或 Flask-RESTX：构建 RESTful API
- Docker 容器化部署，进一步提升可移植性


## 复习重点

- 能说明 `Flask 部署` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

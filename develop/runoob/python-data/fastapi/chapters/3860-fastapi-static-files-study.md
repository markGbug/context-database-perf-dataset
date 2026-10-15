# FastAPI：FastAPI 静态文件

- 来源：[FastAPI 静态文件](https://www.runoob.com/fastapi/fastapi-static-files.html)
- 分类：Python / 数据科学
- 技术：FastAPI
- 笔记类型：学习笔记
- 章节序号：3860

## 本章内容

FastAPI 可以方便地提供静态文件服务（如图片、CSS、JavaScript 文件），使用 Starlette 的 StaticFiles 实现。


## 安装依赖

StaticFiles 包含在 aiofiles 中，需要安装：

```text
pip install aiofiles
```


## 挂载静态文件目录

使用 app.mount() 将静态文件目录挂载到应用上：


## 实例

代码说明：

mount 是将一个独立的"子应用"挂载到指定路径上。StaticFiles 本身就是一个 ASGI 应用，它负责处理静态文件请求。挂载后，所有以 /static 开头的请求都由 StaticFiles 处理，不会经过 FastAPI 的路由系统。


## 目录结构示例

```text
project/
├── main.py
└── static/
    ├── css/
    │   └── style.css
    ├── js/
    │   └── app.js
    └── images/
        └── logo.png
```

访问方式：


## HTML 模板渲染

FastAPI 支持 Jinja2 模板引擎，可以动态渲染 HTML 页面：


## 实例

模板文件 templates/hello.html：


## 实例

模板渲染时，必须传递 request 对象，因为模板中可能需要使用请求上下文（如生成 URL 等）。


## 小结

- 使用 StaticFiles 提供静态文件服务
- 使用 app.mount() 挂载静态文件目录到指定路径
- 挂载后的静态文件路径不受 FastAPI 路由系统管理
- 配合 Jinja2 模板引擎可以实现 HTML 页面渲染
- 静态文件适合存放 CSS、JS、图片等不会动态变化的资源


## 复习重点

- 能说明 `FastAPI 静态文件` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

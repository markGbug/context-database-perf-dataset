# Flask：Flask 静态文件

- 来源：[Flask 静态文件](https://www.runoob.com/flask/flask-static-file.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：学习笔记
- 章节序号：3884

## 本章内容

任何一个完整的 Web 应用都离不开 CSS、JavaScript 和图片等静态资源。

本章介绍 Flask 如何管理和提供静态文件。


## 默认静态文件约定

Flask 默认从应用目录下的 static/ 文件夹提供静态文件。

你只需要创建这个文件夹并将静态资源放入其中即可：

```text
myflaskapp/
├── app.py
├── templates/
│   └── index.html
└── static/
    ├── css/
    │   └── style.css          # 样式文件
    ├── js/
    │   └── main.js            # JavaScript 文件
    └── images/
        └── logo.png           # 图片文件
```


## 在模板中引用静态文件

不要硬编码路径，使用 url_for('static', filename='...') 生成静态文件的 URL。

这样做的好处是：即使将来应用挂载到子路径（如 /myapp），URL 也会自动调整。


## 实例


## 自定义静态文件路径

如果不想使用默认的 static/ 文件夹，可以在创建 Flask 应用时自定义：


## 实例


## CSS 文件示例

创建一个基本样式文件，让页面看起来更专业：


## 实例

访问 http://127.0.0.1:5000/，效果如下：


## 开发与生产环境的区别

Flask 内置的静态文件服务只适合 开发环境。

在生产环境中，应该由 Nginx、Apache 等专业 Web 服务器直接处理静态文件，这样效率远高于通过 Python 代码来服务。

生产部署的详细内容将在后续章节中介绍。


## 复习重点

- 能说明 `Flask 静态文件` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

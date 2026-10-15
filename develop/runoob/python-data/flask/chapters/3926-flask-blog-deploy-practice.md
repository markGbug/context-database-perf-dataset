# Flask：打包上线 — 部署到 Railway

- 来源：[打包上线](https://www.runoob.com/flask/flask-blog-deploy.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：练习笔记
- 章节序号：3926

## 本章内容

本章你将学会应用工厂模式、生产环境配置，并用 Railway 将 Flask 博客部署上线。


## 应用工厂模式 create_app()

到目前为止，app.py 中直接创建了 app = Flask(__name__)，这在开发时够用，但有几个问题：

- 测试时无法创建独立的 app 实例
- 无法按环境（开发/测试/生产）切换不同配置
- 扩展初始化与 app 实例紧耦合

应用工厂模式 解决了这些问题：把 app 的创建封装到一个函数中。


## 实例


### 配置文件 config.py


## 实例


### 新的入口文件 wsgi.py


## 实例

现在启动方式变为：

```text
(venv) $ flask --app wsgi run --debug      # 开发模式
(venv) $ gunicorn wsgi:app                  # 生产模式（Gunicorn）
```

注意 import 顺序：Blueprint 和 user_loader 必须在 create_app() 内部导入（而非文件顶部），否则会触发循环导入（Blueprint 引用了 models，models 引用了 db，而 db 此时尚未绑定到 app）。


## 生成 requirements.txt 与 Procfile

```text
(venv) $ pip freeze > requirements.txt
```

确保文件中包含关键依赖：Flask、Flask-SQLAlchemy、Flask-Migrate、Flask-Login、Flask-WTF、Flask-Admin、gunicorn、python-dotenv。

在项目根目录创建 Procfile：

```text
web: gunicorn wsgi:app
```


## 将项目推送到 GitHub

```text
$ git init
$ echo "venv/" > .gitignore
$ echo "__pycache__/" >> .gitignore
$ echo "*.pyc" >> .gitignore
$ echo "instance/" >> .gitignore
$ echo ".env" >> .gitignore
$ git add .
$ git commit -m "初始化 Flask 博客项目"
$ git branch -M main
$ git remote add origin https://github.com/你的用户名/flask-blog.git
$ git push -u origin main
```

务必把 .env 加入 .gitignore。.env 文件包含 SECRET_KEY 等敏感信息，一旦提交到 GitHub 就无法彻底删除（Git 历史会保留）。


## Railway 部署

- 访问 railway.app，用 GitHub 登录
- New Project → Deploy from GitHub repo → 选择 flask-blog
- Railway 自动检测 Procfile，识别 Gunicorn 启动命令
- 在 Variables 中设置环境变量
- 点击 Deploy


### 环境变量配置

快速生成 SECRET_KEY：

```text
$ python -c "import secrets; print(secrets.token_urlsafe(50))"
```

部署成功后，获得链接如 https://flask-blog.up.railway.app。


## 下一步学习方向


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `打包上线` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

# Flask：Flask 配置管理

- 来源：[Flask 配置管理](https://www.runoob.com/flask/flask-config.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：练习笔记
- 章节序号：3892

## 本章内容

任何应用都需要配置——数据库地址、密钥、调试模式开关等。

Flask 提供了灵活的配置系统，支持从多种来源加载配置，满足开发和生产的不同需求。


## Config 对象基础

Flask 应用的配置存储在 app.config 中，它像一个字典，可以用键名读写任何配置值：


## 实例

配置键名 必须全部大写，这是 Flask 的约定，配合配置加载方法使用。


## 内置配置项

Flask 内置了大量配置项来控制框架行为，以下是开发中最常用的：


## 从 Python 文件加载——from_pyfile

最常见的做法是将配置写入单独的 Python 文件，然后加载：

```text
# 文件路径：config.py（与 app.py 同级目录）
# 注意：所有键名必须大写
SECRET_KEY = "your-production-secret-key"
DATABASE_URL = "postgresql://user:pass@localhost/db"
MAX_CONTENT_LENGTH = 16 * 1024 * 1024  # 限制上传文件大小 16MB

# 开发配置
DEBUG = True
```

app.py 代码：

```text
# 文件路径：app.py
from flask import Flask

app = Flask(__name__)

# 加载 config.py 中所有大写的变量到 app.config
app.config.from_pyfile("config.py")

print(app.config["DATABASE_URL"])  # 输出: postgresql://user:pass@localhost/db
```


## 从环境变量加载——from_prefixed_env

从环境变量加载是 12-Factor App 推荐的做法，最适合生产环境部署。

Flask 默认读取 FLASK_ 前缀的环境变量，值会被尝试解析为 JSON 类型：

```text
# 在终端设置环境变量（或写入 .flaskenv 文件）
export FLASK_SECRET_KEY="prod-secret"
export FLASK_MAX_CONTENT_LENGTH=16777216
```

app.py 代码：

```text
from flask import Flask
from datetime import timedelta

app = Flask(__name__)

# 加载默认配置
app.config["PERMANENT_SESSION_LIFETIME"] = timedelta(days=7)

# 自动加载所有以 FLASK_ 开头的环境变量
# 例如 FLASK_SECRET_KEY 会成为 config["SECRET_KEY"]
app.config.from_prefixed_env()

# 也可以自定义前缀
# app.config.from_prefixed_env("RUNOOB")  # 加载 RUNOOB_ 前缀的变量
```


### 嵌套配置

使用双下划线 __ 可以设置嵌套配置：

```text
$ export FLASK_DATABASE__HOST="localhost"
$ export FLASK_DATABASE__PORT="5432"
```

加载后的结果：


## 实例


## 从 JSON/TOML 加载——from_file

除了 Python 文件和环境变量，Flask 还支持从 JSON、TOML 等格式加载配置：


## 实例


## 实例


## 从对象加载——from_object

直接从一个 Python 对象（模块或类）中加载所有大写属性：


## 实例


## instance 文件夹——私密配置

有些配置不适宜提交到代码仓库（如生产环境的密钥），可以放在 instance 文件夹中：


## 实例

```text
myflaskapp/
├── app.py
├── config.py         # 公共配置（可提交到 Git）
└── instance/          # 不提交到 Git（.gitignore）
    └── config.py     # 私密配置（密钥等）
```


## 配置加载优先级

一个实践中最常见的配置加载顺序：


## 实例

这样的优先级确保：默认值最弱，文件配置中等，环境变量最强——符合 12-Factor App 最佳实践。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Flask 配置管理` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

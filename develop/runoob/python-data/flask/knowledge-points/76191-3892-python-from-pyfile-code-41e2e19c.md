# 知识点 76191：Flask：Flask 配置管理 - 从 Python 文件加载——from_pyfile

- 来源：[Flask 配置管理](https://www.runoob.com/flask/flask-config.html)
- 来源章节：[3892-flask-config-study.md](../chapters/3892-flask-config-study.md)
- 分类：Python / 数据科学
- 技术：Flask
- 所在小节：从 Python 文件加载——from_pyfile
- 知识类型：代码
- 原章节序号：3892

## 原文片段

```text
# 文件路径：app.py
from flask import Flask

app = Flask(__name__)

# 加载 config.py 中所有大写的变量到 app.config
app.config.from_pyfile("config.py")

print(app.config["DATABASE_URL"])  # 输出: postgresql://user:pass@localhost/db
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `从 Python 文件加载——from_pyfile` 这一小节和 `Flask 配置管理` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？

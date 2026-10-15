# PyCharm：PyCharm 创建 Django 项目

- 来源：[PyCharm Django](https://www.runoob.com/pycharm/pycharm-django.html)
- 分类：DevOps / 工程化
- 技术：PyCharm
- 笔记类型：练习笔记
- 章节序号：1880

## 本章内容

PyCharm 是一款强大的 Python IDE，提供了对 Django 框架的出色支持，尤其是在其专业版（PyCharm Pro）中。


### 启动 PyCharm 并新建项目

- 打开 PyCharm，点击 "新建项目"
- 在左侧选择 "Django"
- 设置项目位置（Location）
- 配置 Python 解释器（建议新建虚拟环境）


### 配置项目参数

- 项目名称：使用小写字母和下划线组合（如 DjangoProject）
- 模板语言：默认选择 Django
- 前端框架：可根据需要选择（初学者可不选）
- 启用 Django admin：可勾选


### 等待项目初始化

PyCharm 会自动：

- 创建虚拟环境
- 安装 Django 最新稳定版
- 生成基础项目结构


## 项目结构解析

创建完成后，您会看到以下主要文件和目录：


### 项目根目录

- manage.py：Django 命令行工具
- 项目同名目录（如 DjangoProject/）：包含项目主要配置


### 项目配置目录

- init.py：标识这是一个 Python 包
- settings.py：项目配置文件
- urls.py：URL 路由配置
- wsgi.py：WSGI 服务器配置


### 其他重要文件

- requirements.txt：项目依赖文件（PyCharm 可能自动生成）
- venv/：虚拟环境目录（如果选择创建虚拟环境）


## 运行 Django 开发服务器


### 通过 PyCharm 运行

- 点击 PyCharm 右上角的运行配置下拉菜单
- 选择 "配置 -> 编辑"
- 确保配置了 Django 服务器
- 点击绿色运行按钮


### 通过命令行运行

- 打开 PyCharm 的终端
- 输入命令：python3 manage.py runserver 启动成功后，终端信息显示如下：
- 访问 http://127.0.0.1:8000 查看默认页面:


### 常见问题解决

- 端口冲突：使用 python manage.py runserver 8080 指定其他端口
- 数据库未迁移：首次运行需执行 python manage.py migrate


## 创建 Django 应用


### 创建新应用

在 PyCharm 的终端中输入：

```text
python3 manage.py startapp myapp
```

将应用添加到 settings.py 的 INSTALLED_APPS 中:

```text
INSTALLED_APPS = [
    ...
    'myapp',
]
```

在项目 urls.py 中包含应用路由：


## 实例


### 应用目录结构

- migrations/：数据库迁移文件
- admin.py：管理后台配置
- apps.py：应用配置
- models.py：数据模型定义
- tests.py：测试代码
- views.py：视图函数


### myapp 目录下配置 URL 路由

打开 myapp/models.py，定义模型。例如：


## 实例

保存后，运行 python manage.py makemigrations 和 python manage.py migrate 以更新数据库。

创建视图和 URL：

在 myapp/views.py 中定义视图：


## 实例

在 myapp/urls.py（需要手动创建）中配置 URL：


## 实例

在项目根目录创建 DjangoProject/templates/myapp/ 文件夹，然后在改文件夹下创建 post_list.html：


## 实例

确保 settings.py 中的 TEMPLATES 设置包含正确的模板目录：

```text
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [BASE_DIR / 'templates'],
        ...
    }
]
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `PyCharm Django` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

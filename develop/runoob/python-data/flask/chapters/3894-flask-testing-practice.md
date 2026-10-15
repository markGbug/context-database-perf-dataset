# Flask：Flask 测试

- 来源：[Flask 测试](https://www.runoob.com/flask/flask-testing.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：练习笔记
- 章节序号：3894

## 本章内容

测试是保证代码质量的基础。

Flask 提供了内置的测试客户端，配合 pytest 可以高效编写和运行测试。


## 测试客户端——test_client

Flask 的 test_client() 方法创建了一个模拟的 HTTP 客户端，可以在不启动服务器的情况下发送请求：


## 实例


## pytest 集成

pytest 是 Python 社区的标准测试框架，配合 Flask 使用非常方便。


### 安装 pytest

```text
(.venv) $ pip install pytest
```


### 编写测试——conftest.py（共享夹具）

使用 conftest.py 文件创建可复用的测试夹具（fixture）：


## 实例


## 测试路由


## 实例

运行测试：

```text
(.venv) $ pytest tests/test_app.py -v
====================================
tests/test_app.py::test_home_page PASSED
tests/test_app.py::test_404_page PASSED
====================================
```


## 测试 JSON API


## 实例


## 测试 Session

测试登录等需要 Session 的功能：


## 实例

client.session_transaction() 是一个非常实用的测试工具——它让你可以直接修改 Session 内容，无需通过完整的登录流程。


## 测试 CLI 命令


## 实例


## 测试最佳实践


## 运行全部测试

```text
(.venv) $ pytest tests/ -v

tests/test_app.py::test_home_page PASSED
tests/test_app.py::test_404_page PASSED
tests/test_api.py::test_create_post PASSED
tests/test_api.py::test_create_post_without_title PASSED
tests/test_api.py::test_get_posts PASSED
tests/test_api.py::test_delete_post PASSED
tests/test_auth.py::test_login PASSED
tests/test_auth.py::test_session_transaction PASSED
tests/test_cli.py::test_init_db PASSED
tests/test_cli.py::test_flask_routes PASSED

==================== 10 passed in 0.45s ====================
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Flask 测试` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

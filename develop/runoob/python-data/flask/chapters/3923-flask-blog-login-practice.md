# Flask：Flask-Login — 用户注册、登录、登出

- 来源：[Flask-Login](https://www.runoob.com/flask/flask-blog-login.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：练习笔记
- 章节序号：3923

## 本章内容

本章你将学会用 Flask-Login 实现 Session 用户认证，这是 Flask Web 开发最重要的安全保障。


## Flask-Login 是什么？

Web 应用的 HTTP 请求本质上是无状态的——服务器不会自动记住你是谁。

Flask-Login 通过 Session 机制实现用户状态的维护：登录后服务器在 Session 中存入用户 ID，后续请求自动识别当前用户。


## 安装与初始化

```text
(venv) $ pip install flask-login
```


## 实例

SECRET_KEY 是 Flask 安全体系的基石——Session 加密、CSRF Token、Flash 消息都依赖它。生产环境中必须从环境变量读取，不可硬编码。


## 定义 User 模型

Flask-Login 要求 User 模型实现 UserMixin 提供的几个方法。


## 实例

UserMixin 自动为 User 模型注入以下属性和方法：

生成迁移并执行：

```text
(venv) $ flask db migrate -m "新增 User 模型"
(venv) $ flask db upgrade
```


## 创建认证 Blueprint


## 实例


### 在设计 App 中需要的引用


## 实例

永远不要明文存储密码！generate_password_hash() 使用 PBKDF2 算法对密码做 salted hash。即使数据库泄露，攻击者也无法反向推导密码。校验密码时用 check_password_hash()。


## 创建登录和注册模板


## 实例


### 更新导航栏显示登录状态


## 实例

current_user 是 Flask-Login 自动注入的代理对象，在所有模板和视图函数中都可以直接使用。登录状态下它是一个 User 对象，未登录时是 AnonymousUserMixin 实例。


## 本章小结

本章你接入了 Flask-Login Session 认证：UserMixin + user_loader 组合用户模型、login_user/logout_user 管理 Session、werkzeug 哈希密码、@login_required 保护视图、模板中 current_user 判断状态。

现在博客有了完整的用户注册、登录、登出流程。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Flask-Login` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

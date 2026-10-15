# FastAPI：用户系统 — 注册、登录、JWT 认证

- 来源：[用户系统](https://www.runoob.com/fastapi/fastapi-blog-jwt-auth.html)
- 分类：Python / 数据科学
- 技术：FastAPI
- 笔记类型：练习笔记
- 章节序号：3871

## 本章内容

本章你将学会 FastAPI 的 JWT 认证方案，理解它和 Django/Flask Session 认证的区别。


## JWT vs Session 认证

Django 和 Flask 用的是 Session 认证：服务器存储用户状态，Cookie 中只存 Session ID。

FastAPI 推荐 JWT 认证：用户登录后获得一个 Token（令牌），后续请求携带 Token 即可认证。


## 安装依赖

```text
(venv) $ pip install passlib python-jose python-multipart
```

- passlib：密码哈希（对标 werkzeug.security）
- python-jose：JWT 的生成和验证
- python-multipart：处理表单提交（OAuth2 登录表单）


## 定义 User 模型


## 实例

生成并执行迁移：

```text
(venv) $ alembic revision --autogenerate -m "新增 User 模型"
(venv) $ alembic upgrade head
```


## JWT 工具函数


## 实例


## 注册路由


## 实例


## 登录路由（签发 JWT）


## 实例

JWT Token 中 sub 是标准的 subject 字段，存储用户标识。Token 本身不加密（只是 Base64 编码），所以绝对不能在里面放密码等敏感信息。如果你想加密，用 JWE 而非 JWT。


## 在路由中使用 JWT 保护


## 实例

对于 SSR 页面，JWT 通常存到 Cookie 中（而非 Authorization Header），在模板路由中从 Cookie 提取 Token 验证。


## 本章小结

本章你实现了 FastAPI 的 JWT 认证：passlib 哈希密码、python-jose 签发验证 JWT、OAuth2PasswordBearer 提取 Token、Depends 实现认证依赖注入。

与 Django/Flask 的 Session 认证不同，JWT 是无状态方案，更适合前后端分离场景。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `用户系统` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

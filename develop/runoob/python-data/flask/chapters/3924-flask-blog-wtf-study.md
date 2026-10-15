# Flask：表单处理 — Flask-WTF

- 来源：[表单处理](https://www.runoob.com/flask/flask-blog-wtf.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：学习笔记
- 章节序号：3924

## 本章内容

本章你将学会用 Flask-WTF 规范化处理表单：定义表单类、自动 CSRF 保护、字段校验与错误提示。


## 为什么要用 Flask-WTF？

上一章的注册和登录表单是手写的：手动从 request.form.get() 取值、手动校验、手动显示错误。

Flask-WTF 基于 WTForms 为 Flask 封装，提供：

- 表单类定义，字段 + 校验规则集中管理
- 自动 CSRF 保护
- 模板中渲染字段和错误信息
- form.validate_on_submit() 统一处理 GET/POST 判断与校验


## 安装与配置

```text
(venv) $ pip install flask-wtf
```

在 app.py 中配置 SECRET_KEY（CSRF Token 依赖此密钥）：


## 实例


## 定义表单类


## 实例


### 常用字段类型


### 常用验证器


## 在视图函数中使用表单


## 实例


## 模板中渲染表单


## 实例

Flask-WTF 的 CSRF 保护是自动的：form.hidden_tag() 会生成一个隐藏的 <input> 包含随机 Token，服务器在接受 POST 请求前验证此 Token。任何外站提交的表单都因为没有正确的 Token 而被拒绝。


## 手动 request.form vs Flask-WTF 对比


## 本章小结

本章你用 Flask-WTF 重构了认证表单：FlaskForm 定义字段和验证器、validate_xxx 自定义验证、form.validate_on_submit() 统一处理 POST 校验、form.hidden_tag() 自动 CSRF 保护、模板中渲染错误信息。

表单处理现在更规范、更安全。


## 复习重点

- 能说明 `表单处理` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

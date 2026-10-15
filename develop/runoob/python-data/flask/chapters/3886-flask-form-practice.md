# Flask：Flask 表单处理

- 来源：[Flask 表单处理](https://www.runoob.com/flask/flask-form.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：练习笔记
- 章节序号：3886

## 本章内容

在 Flask 中，表单处理是构建 Web 应用时一个常见的需求。

处理表单数据涉及到接收、验证和处理用户提交的表单。Flask 提供了基本的表单处理功能，但通常结合 Flask-WTF 扩展来简化表单操作和验证。

- 基本表单处理：使用 request.form 获取表单数据。
- 使用 Flask-WTF：结合 WTForms 进行表单处理和验证，简化表单操作。
- 表单验证：使用验证器确保表单数据的有效性。
- 文件上传：处理文件上传和保存文件。
- CSRF 保护：确保表单免受跨站请求伪造攻击。


## 1. 基本表单处理

Flask 提供了直接处理表单数据的方式，使用 request 对象来获取提交的数据。


### 创建 HTML 表单

templates/form.html 文件代码：


## 实例

action="/submit"：表单数据提交到 /submit 路径。

method="post"：使用 POST 方法提交数据。


### 处理表单数据

app.py 文件代码：


## 实例

request.form.get('name') 和 request.form.get('email')：获取提交的表单数据。


## 2. 使用 Flask-WTF 扩展

Flask-WTF 是一个封装了 WTForms 的扩展，提供了表单处理和验证的功能，使得表单处理更加简洁和强大。


### 安装 Flask-WTF

```text
pip install flask-wtf
```

app.py 文件代码：


## 实例


### 创建模板以支持 Flask-WTF 表单

templates/form.html 文件代码：


## 实例

{{ form.hidden_tag() }}：生成隐藏字段，用于保护表单免受 CSRF 攻击。

{{ form.name.label }} 和 {{ form.name(size=32) }}：渲染表单字段及其标签。


## 3. 表单验证

Flask-WTF 和 WTForms 提供了丰富的表单验证功能。你可以使用内置的验证器或自定义验证器来确保表单数据的有效性。


## 实例

- DataRequired()：确保字段不为空。
- Length(min=1, max=50)：限制字符串的最小和最大长度。
- Email()：验证字段是否为有效的电子邮件地址。


## 4. 文件上传

Flask 还支持处理文件上传。上传的文件可以通过 request.files 访问。


### 创建文件上传表单

templates/upload.html 文件代码：


## 实例

enctype="multipart/form-data"：指定表单数据的编码类型，支持文件上传。


### 处理文件上传

app.py 文件代码：


## 实例

request.files.get('file')：获取上传的文件对象。

file.save(f'uploads/{filename}')：将文件保存到指定目录。


## 5. CSRF 保护

Flask-WTF 自动为表单提供 CSRF 保护。你需要配置一个密钥来启用 CSRF 保护，并在模板中包含隐藏的 CSRF 令牌。


### 配置 CSRF 保护

```text
app.secret_key = 'your_secret_key'
```

在模板中添加 CSRF 令牌：


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Flask 表单处理` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

# Flask：Flask Session 与 Cookie

- 来源：[Flask Session 与 Cookie](https://www.runoob.com/flask/flask-session-cookie.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：学习笔记
- 章节序号：3885

## 本章内容

HTTP 协议本身是无状态的——服务器不会自动记住两次请求是否来自同一用户。

Flask 通过 Session 机制解决了这个问题，让 Web 应用能够「记住」用户的状态。


## Session 的工作原理

Flask 默认使用 SecureCookieSession，它的工作方式是：

- Session 数据被序列化后用密钥签名，保存在浏览器的 Cookie 中
- 每次请求时，浏览器自动带上这个 Cookie
- Flask 验证签名后，将数据还原为 Python 字典供你使用

用户可以看到 Cookie 中的内容（因为是 base64 编码的），但无法篡改——因为任何修改都会导致签名验证失败。


## 配置 SECRET_KEY

要使用 Session，必须先设置 SECRET_KEY——用于签名的密钥。


## 实例

重要：SECRET_KEY 必须保密且足够随机。如果密钥泄露，任何人都可以伪造你应用的 Session 数据。生产环境应从环境变量或配置文件读取，不要硬编码在代码中。

生成高质量密钥的命令：

```text
$ python -c 'import secrets; print(secrets.token_hex())'
192b9bdd22ab9ed4d12e236c78afcb9a393ec15f71bbf5dc987d54727823bcbf
```


## 读写 Session

session 是一个类似字典的对象，用法和 Python 字典基本一样：


## 实例


## 永久 Session

默认情况下，Session 在浏览器关闭后失效（浏览器会话级别）。

如果需要「记住我」功能，可以将 Session 标记为 永久（permanent）：


## 实例


## Message Flashing——一次性消息

用户提交表单后，需要显示「操作成功」或「出错」的反馈信息。

这种「显示一次后消失」的消息，Flask 提供了 flash() 机制。


## 实例

模板中渲染 flash 消息：


## 实例

Flash 消息依赖于 Session，因此必须设置 SECRET_KEY 才能使用。


## Session 常见问题

Cookie 大小限制：浏览器对单个 Cookie 的大小限制约为 4KB。不要在 Session 中存储大量数据——适合存用户 ID、偏好设置等轻量信息，不适合存文件或大型对象。


## 复习重点

- 能说明 `Flask Session 与 Cookie` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

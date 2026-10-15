# Flask：URL 定义路由 API

- 来源：[Flask 定义路由 API](https://www.runoob.com/flask/flask-url-route-registrations-api.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：练习笔记
- 章节序号：3914

## 本章内容

Flask 提供三种方式定义路由规则：@app.route() 装饰器、add_url_rule() 方法、直接操作 url_map。


## URL 变量转换器


## add_url_rule 参数


## 尾斜线行为


## 默认值路由

通过 defaults 参数实现可选的 URL 变量：


## 实例

如果默认值路由与带变量的路由都存在，访问带默认值的 URL 会被 308 重定向到简化形式。


## 自定义转换器


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Flask 定义路由 API` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

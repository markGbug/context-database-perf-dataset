# FastAPI：FastAPI 交互式 API 文档

- 来源：[FastAPI 交互式 API 文档](https://www.runoob.com/fastapi/fastapi-api-doc.html)
- 分类：Python / 数据科学
- 技术：FastAPI
- 笔记类型：练习笔记
- 章节序号：3840

## 本章内容

FastAPI 基于代码中的类型注解自动生成交互式 API 文档，默认提供 Swagger UI 和 ReDoc 两种界面。开发者可以直接在文档中测试 API，无需额外的工具。


## 访问 API 文档

运行 FastAPI 应用后，访问以下地址查看文档：


## Swagger UI

Swagger UI 提供了直观的用户界面，可以直接在浏览器中测试 API：


### 测试 API 的步骤

- 点击要测试的路由，展开详情
- 点击 "Try it out" 按钮
- 填写参数值
- 点击 "Execute" 按钮发送请求
- 查看响应结果


## ReDoc

ReDoc 注重文档的可读性，适合浏览 API 定义：


## OpenAPI 规范

FastAPI 使用 OpenAPI 标准将 API 转换为"模式"（Schema）。访问 http://127.0.0.1:8000/openapi.json 可以查看原始的 OpenAPI JSON：

```text
{
    "openapi": "3.1.0",
    "info": {
        "title": "FastAPI",
        "version": "0.1.0"
    },
    "paths": {
        "/items/{item_id}": {
            "get": {
                "responses": {
                    "200": {
                        "description": "Successful Response"
                    }
                }
            }
        }
    }
}
```

OpenAPI 规范的用途：

- 驱动 Swagger UI 和 ReDoc 文档系统
- 自动生成各种语言的客户端代码
- 与 API 测试工具（如 Postman）集成
- 兼容大量第三方工具和平台


## 自定义 API 文档信息

创建 FastAPI 实例时，可以自定义文档的元数据：


## 实例


## 为路由添加文档信息

可以在装饰器和函数中为每个路由添加详细的文档信息：


## 实例

文档参数说明：

如果同时设置了 description 和函数的 docstring，description 优先生效。docstring 支持 Markdown 格式，适合编写较长的说明。


## 使用 tags 分组

tags 参数可以将相关的路由归为一组，在文档中更清晰地展示：


## 实例

在 Swagger UI 中，路由会按标签分组显示。


## 禁用文档

在生产环境中，你可能想禁用自动文档：


## 实例


## 小结

- FastAPI 自动生成 Swagger UI 和 ReDoc 两种交互式文档
- 文档内容基于代码中的类型注解自动生成，代码更新文档自动同步
- 使用 title、description、tags 等参数自定义文档信息
- 函数的 docstring 也会出现在文档中
- 生产环境可通过 docs_url=None 禁用文档


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `FastAPI 交互式 API 文档` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

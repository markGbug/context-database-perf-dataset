# FastAPI：FastAPI 文件上传

- 来源：[FastAPI 文件上传](https://www.runoob.com/fastapi/fastapi-file-upload.html)
- 分类：Python / 数据科学
- 技术：FastAPI
- 笔记类型：学习笔记
- 章节序号：3855

## 本章内容

FastAPI 提供了 File 和 UploadFile 两种方式来处理文件上传，支持单独上传文件和表单与文件混合上传。


## 安装依赖

文件上传同样依赖 python-multipart：

```text
pip install python-multipart
```


## 使用 UploadFile

UploadFile 是推荐的方式，它提供了更丰富的文件信息访问接口：


## 实例

UploadFile 的属性和方法：

UploadFile 使用"SpooledTemporaryFile"存储文件内容，文件较小时保存在内存中，文件较大时自动写入磁盘，因此比 bytes 更节省内存。


## 使用 File 接收文件内容

File 直接将文件内容读取为 bytes，适合小文件：


## 实例

File 与 UploadFile 的对比：


## 可选文件上传

使用默认值 None 使文件上传变为可选：


## 实例


## 多文件上传

使用列表接收多个文件：


## 实例


## 表单与文件混合上传

可以在同一个路由中同时接收表单数据和文件：


## 实例


## 保存上传的文件

以下示例展示如何将上传的文件保存到磁盘：


## 实例

实际项目中，上传文件时应注意：1) 校验文件类型和大小；2) 使用安全的文件名（避免路径遍历攻击）；3) 限制上传目录的权限；4) 对于大文件使用流式处理而非一次性读取。


## 小结

- 推荐使用 UploadFile，它更节省内存且提供丰富的文件信息
- File 适合小文件场景，直接读取为 bytes
- 使用 list[UploadFile] 接收多文件上传
- 表单（Form）和文件（UploadFile）可以在同一路由中使用
- 上传文件时注意安全：校验文件类型、使用安全文件名、限制大小


## 复习重点

- 能说明 `FastAPI 文件上传` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

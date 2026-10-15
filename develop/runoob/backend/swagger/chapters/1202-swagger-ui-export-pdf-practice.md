# Swagger：Swagger UI 导出文档

- 来源：[Swagger UI 导出文档](https://www.runoob.com/swagger/swagger-ui-export-pdf.html)
- 分类：后端开发
- 技术：Swagger
- 笔记类型：练习笔记
- 章节序号：1202

## 本章内容

## 生成静态 HTML 文档


### 使用 Swagger2markup

Swagger2markup 是一个能将 Swagger JSON 或 YAML 文件转换为 AsciiDoc 或 Markdown 文档的工具。结合 AsciiDoctor，可以将文档转换为 HTML 或 PDF 格式。

添加 Maven 依赖:


## 实例

创建测试类生成文档:


## 实例

运行测试并生成文档:

```text
# 生成 AsciiDoc
mvn test

# 将 AsciiDoc 转换为 HTML
mvn asciidoctor:process-asciidoc

# 生成的文档位于 target/generated-docs 目录
```


## 生成 PDF 文档


### 使用 Asciidoctor-PDF

基于前面生成的 AsciiDoc 文件，可以使用 Asciidoctor-PDF 生成 PDF 文档:

1. 修改 Maven 配置:


## 实例

自定义 PDF 样式 src/main/resources/theme/custom-theme.yml:


## 实例

生成 PDF 文档:

```text
mvn asciidoctor:process-asciidoc@pdf
```


## 使用工具直接导出


### 使用 wkhtmltopdf 工具

1. 安装 wkhtmltopdf:

```text
# Ubuntu/Debian
sudo apt-get install wkhtmltopdf

# CentOS/RHEL
sudo yum install wkhtmltopdf

# macOS
brew install wkhtmltopdf
```

2. 创建导出脚本 export-docs.sh:


## 实例

3. 运行脚本:

```text
chmod +x export-docs.sh
./export-docs.sh
```


### 使用 Puppeteer 导出 PDF

对于 Node.js 环境，可以使用 Puppeteer 导出 PDF。

1. 创建导出脚本 export-pdf.js:


## 实例

2. 安装依赖并运行:

```text
npm install puppeteer
node export-pdf.js
```


## 总结

Swagger UI 是一个强大的 API 文档工具，通过正确配置和使用，可以大大提高 API 的可用性和开发效率。

通过以上内容我们了解了 Swagger UI 的基本概念、集成方法、文档编写、自定义配置、文档发布、样式定制以及文档导出等内容。

记住以下关键点:

- 选择适合项目技术栈的 Swagger 集成方式
- 精心设计和编写 API 文档注解或注释
- 根据需要自定义 Swagger UI 界面和样式
- 添加品牌标识使文档更具专业性
- 选择合适的文档发布和导出方式
- 遵循最佳实践，确保文档的准确性和安全性

通过合理使用 Swagger UI，您可以为您的 API 提供专业、交互式的文档，让您的 API 更易于理解和使用。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Swagger UI 导出文档` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

# Tailwind CSS：Tailwind CSS 安装(CDN)

- 来源：[Tailwind CSS 安装(CDN)](https://www.runoob.com/tailwindcss/tailwindcss-installbycdn.html)
- 分类：前端开发
- 技术：Tailwind CSS
- 笔记类型：学习笔记
- 章节序号：3096

## 本章内容

如果只想简单体验，可以直接引入 CDN 链接：

使用官网提供的 CDN 库，地址如下：

使用 jsDelivr 的 CDN 库，地址如下：

```html
<link href="https://cdn.jsdelivr.net/npm/tailwindcss@3.3.0/dist/tailwind.min.css" rel="stylesheet">
```

使用这种方式使用：

- 优点：无需配置，适合快速开发和演示。
- 缺点：不能自定义样式，文件体积较大。


### 使用实例

以下实例输出了 Hello, world!


## 实例

```html
<!doctype html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body>
  <h1 class="text-3xl font-bold underline">
    Hello world!
  </h1>
</body>
</html>
```

编辑 tailwind.config 对象可以定义自己的配置信息：


## 实例

```html
<!doctype html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <script src="https://cdn.tailwindcss.com"></script>
  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            clifford: '#da373d',
          }
        }
      }
    }
  </script>
</head>
<body>
  <h1 class="text-3xl font-bold underline text-clifford">
    Hello world!
  </h1>
</body>
</html>
```

使用 type="text/tailwindcss" 添加自定义 CSS：


## 实例

使用 plugins 参数可以设置使用的插件，如 forms（表单） 和 typography（排版）：


## 实例


## 复习重点

- 能说明 `Tailwind CSS 安装(CDN)` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

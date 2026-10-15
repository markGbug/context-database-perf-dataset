# Markdown：Markdown 链接

- 来源：[Markdown 链接](https://www.runoob.com/markdown/md-link.html)
- 分类：DevOps / 工程化
- 技术：Markdown
- 笔记类型：学习笔记
- 章节序号：1817

## 本章内容

链接是使 Markdown 文档具有交互性的关键元素。

掌握链接语法能让你创建内容丰富、易于导航的文档。

链接使用方法如下：

```text
[链接名称](链接地址)
[链接文字](链接地址 "可选的标题")
```

或者:

```text
<链接地址>
```

一个简单的链接：

```text
这是一个链接 [菜鸟教程](https://www.runoob.com)
```

显示结果如下：

直接使用链接地址：

```html
<https://www.runoob.com>
```

显示结果如下：

设置可选标题：

```text
这是一个链接 [菜鸟教程](https://www.runoob.com)
欢迎访问 [GitHub](https://github.com) 官网
这是 [百度搜索](https://www.baidu.com "百度一下，你就知道")
```

显示结果如下：

链接标题的作用：

- 当鼠标悬停在链接上时显示提示信息
- 对搜索引擎优化和无障碍访问有帮助


### 参考链接

参考式链接将链接定义与使用分离，让文档更整洁，特别适合长文档或需要多次引用相同链接的情况。

基本语法：

```text
markdown[链接文字][参考标签]

[参考标签]: URL "可选标题"
```

我们可以通过变量来设置一个链接，变量赋值在文档末尾进行：

```text
这个链接用 1 作为网址变量 [Google][1]
这个链接用 runoob 作为网址变量 [Runoob][runoob]
然后在文档的结尾为变量赋值（网址）

  [1]: http://www.google.com/
  [runoob]: http://www.runoob.com/
```

显示结果如下：

简化写法：

当参考标签与链接文字相同时，可以省略第二个方括号：

```text
markdown 我喜欢使用 [GitHub][] 来管理代码。

[GitHub]: https://github.com
```

参考链接的优势：

- 文档正文更清爽，不被长 URL 打断
- 便于链接的统一管理和更新
- 相同链接可以重复使用，避免重复定义
- 链接定义可以放在文档任意位置（通常放在末尾）

组织技巧：

```text
markdown# 学习资源推荐

## 在线教程
- [MDN Web Docs][mdn] - 权威的 Web 技术文档
- [RUNOOB][rnb] - 适合初学者的教程网站
- [freeCodeCamp][fcc] - 免费的编程学习平台

## 代码托管
- [GitHub][github] - 最受欢迎的代码托管服务
- [GitLab][gitlab] - 企业级的代码管理平台

<!-- 链接定义区域 -->
[mdn]: https://developer.mozilla.org/
[rnb]: https://www.runoob.com/
[fcc]: https://www.freecodecamp.org/
[github]: https://github.com/
[gitlab]: https://gitlab.com/
```


### 自动链接识别

现代 Markdown 解析器通常支持自动识别 URL 和邮箱地址：

URL 自动识别：

```html
markdown直接输入网址：https://www.example.com
用尖括号包围：<https://www.example.com>
```

邮箱自动识别：

```html
markdown联系邮箱：example@email.com
或者：<example@email.com>
```

注意事项：

- 自动识别功能依赖于具体的 Markdown 解析器
- 为了确保兼容性，建议使用标准的链接语法
- 某些特殊字符可能影响自动识别


### 锚点链接的使用

锚点链接用于在同一文档内跳转，特别适合长文档的导航：

跳转到标题：

```text
## 目录
- [第一章：介绍](#第一章介绍)
- [第二章：安装](#第二章安装)
- [第三章：使用方法](#第三章使用方法)

# 第一章：介绍
这里是介绍内容...

# 第二章：安装
这里是安装说明...

# 第三章：使用方法
这里是使用说明...
```

锚点规则：

- 标题会自动生成锚点
- 锚点名称通常是标题的小写形式
- 空格替换为连字符
- 移除特殊字符

手动创建锚点：

```html
<a id="custom-anchor"></a>
## 自定义锚点位置

[跳转到自定义位置](#custom-anchor)
```

页面顶部返回链接：

```text
[回到顶部](#)
```


## 复习重点

- 能说明 `Markdown 链接` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

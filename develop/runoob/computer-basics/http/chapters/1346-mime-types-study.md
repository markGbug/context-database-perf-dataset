# HTTP：MIME 类型

- 来源：[MIME 类型](https://www.runoob.com/http/mime-types.html)
- 分类：计算机基础
- 技术：HTTP
- 笔记类型：学习笔记
- 章节序号：1346

## 本章内容

MIME (Multipurpose Internet Mail Extensions) 是描述消息内容类型的标准，用来表示文档、文件或字节流的性质和格式。

MIME 消息能包含文本、图像、音频、视频以及其他应用程序专用的数据。

浏览器通常使用 MIME 类型（而不是文件扩展名）来确定如何处理URL，因此 We b服务器在响应头中添加正确的 MIME 类型非常重要。如果配置不正确，浏览器可能会无法解析文件内容，网站将无法正常工作，并且下载的文件也会被错误处理。


### 语法

MIME 类型通用结构：

```text
type/subtype
```

MIME 的组成结构非常简单，由类型与子类型两个字符串中间用 / 分隔而组成，不允许有空格。type 表示可以被分多个子类的独立类别，subtype 表示细分后的每个类型。

MIME类型对大小写不敏感，但是传统写法都是小写。

两种主要的 MIME 类型在默认类型中扮演了重要的角色：

- text/plain 表示文本文件的默认值。
- application/octet-stream 表示所有其他情况的默认值。


### 常见的 MIME 类型

- 超文本标记语言文本 .html、.html：text/html
- 普通文本 .txt： text/plain
- RTF 文本 .rtf： application/rtf
- GIF 图形 .gif： image/gif
- JPEG 图形 .jpeg、.jpg： image/jpeg
- au 声音文件 .au： audio/basic
- MIDI 音乐文件 mid、.midi： audio/midi、audio/x-midi
- RealAudio 音乐文件 .ra、.ram： audio/x-pn-realaudio
- MPEG 文件 .mpg、.mpeg： video/mpeg
- AVI 文件 .avi： video/x-msvideo
- GZIP 文件 .gz： application/x-gzip
- TAR 文件 .tar： application/x-tar

application/octet-stream, application/pkcs12, application/vnd.mspowerpoint, application/xhtml+xml, application/xml, application/pdf


## MIME 对照表


### 按照内容类型排列的 MIME 类型列表


### 按照文件扩展名排列的 MIME 类型列表


## 复习重点

- 能说明 `MIME 类型` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

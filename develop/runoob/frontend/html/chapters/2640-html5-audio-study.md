# HTML：HTML5 Audio(音频)

- 来源：[HTML5 Audio(音频)](https://www.runoob.com/html/html5-audio.html)
- 分类：前端开发
- 技术：HTML
- 笔记类型：学习笔记
- 章节序号：2640

## 本章内容

HTML5 提供了播放音频文件的标准。


## 互联网上的音频

直到现在，仍然不存在一项旨在网页上播放音频的标准。

今天，大多数音频是通过插件（比如 Flash）来播放的。然而，并非所有浏览器都拥有同样的插件。

HTML5 规定了在网页上嵌入音频元素的标准，即使用 <audio> 元素。


## 浏览器支持

Internet Explorer 9+, Firefox, Opera, Chrome, 和 Safari 都支持 <audio> 元素.

注意: Internet Explorer 8 及更早IE版本不支持 <audio> 元素.


## HTML5 Audio - 如何工作

如需在 HTML5 中播放音频，你需要使用以下代码：


## 实例

```html
<audio controls>
  <source src="horse.ogg" type="audio/ogg">
  <source src="horse.mp3" type="audio/mpeg">
您的浏览器不支持 audio 元素。
</audio>
```

control 属性供添加播放、暂停和音量控件。

在<audio> 与 </audio> 之间你需要插入浏览器不支持的<audio>元素的提示文本 。

<audio> 元素允许使用多个 <source> 元素. <source> 元素可以链接不同的音频文件，浏览器将使用第一个支持的音频文件


## 音频格式及浏览器支持

目前, <audio>元素支持三种音频格式文件: MP3, Wav, 和 Ogg:


## 音频格式的MIME类型


## HTML5 Audio 标签


## 复习重点

- 能说明 `HTML5 Audio(音频)` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

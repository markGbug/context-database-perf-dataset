# HTML：HTML5 Video(视频)

- 来源：[HTML5 Video(视频)](https://www.runoob.com/html/html5-video.html)
- 分类：前端开发
- 技术：HTML
- 笔记类型：练习笔记
- 章节序号：2639

## 本章内容

很多站点都会使用到视频. HTML5 提供了展示视频的标准。


## 检测您的浏览器是否支持 HTML5 视频：


## Web站点上的视频

直到现在，仍然不存在一项旨在网页上显示视频的标准。

今天，大多数视频是通过插件（比如 Flash）来显示的。然而，并非所有浏览器都拥有同样的插件。

HTML5 规定了一种通过 video 元素来包含视频的标准方法。


## 浏览器支持

Internet Explorer 9+, Firefox, Opera, Chrome, 和 Safari 支持 <video> 元素.

注意: Internet Explorer 8 或者更早的IE版本不支持 <video> 元素。


## HTML5 (视频)- 如何工作

如需在 HTML5 中显示视频，您所有需要的是：


## 实例

```html
<video width="320" height="240" controls>
  <source src="movie.mp4" type="video/mp4">
  <source src="movie.ogg" type="video/ogg">
您的浏览器不支持Video标签。
</video>
```

<video> 元素提供了 播放、暂停和音量控件来控制视频。

同时 <video> 元素也提供了 width 和 height 属性控制视频的尺寸.如果设置的高度和宽度，所需的视频空间会在页面加载时保留。如果没有设置这些属性，浏览器不知道大小的视频，浏览器就不能再加载时保留特定的空间，页面就会根据原始视频的大小而改变。

<video> 与</video> 标签之间插入的内容是提供给不支持 video 元素的浏览器显示的。

<video> 元素支持多个 <source> 元素. <source> 元素可以链接不同的视频文件。浏览器将使用第一个可识别的格式：


## 视频格式与浏览器的支持

当前， <video> 元素支持三种视频格式： MP4, WebM, 和 Ogg:

- MP4 = 带有 H.264 视频编码和 AAC 音频编码的 MPEG 4 文件
- WebM = 带有 VP8 视频编码和 Vorbis 音频编码的 WebM 文件
- Ogg = 带有 Theora 视频编码和 Vorbis 音频编码的 Ogg 文件


## 视频格式


## HTML5 <video> - 使用 DOM 进行控制

HTML5 <video> 和 <audio> 元素同样拥有方法、属性和事件。

<video> 和 <audio>元素的方法、属性和事件可以使用JavaScript进行控制.

其中的方法用于播放、暂停以及加载等。其中的属性（比如时长、音量等）可以被读取或设置。其中的 DOM 事件能够通知您，比方说，<video> 元素开始播放、已暂停，已停止，等等。

例中简单的方法，向我们演示了如何使用 <video> 元素，读取并设置属性，以及如何调用方法。


## 实例 1

为视频创建简单的播放/暂停以及调整尺寸控件：

上面的例子调用了两个方法：play() 和 pause()。它同时使用了两个属性：paused 和 width。

更多参考请查看 HTML5 Audio/Video DOM 参考手册。


## HTML5 Video 标签


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `HTML5 Video(视频)` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

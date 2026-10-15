# OpenCV：OpenCV 视频处理

- 来源：[OpenCV 视频处理](https://www.runoob.com/opencv/opencv-video.html)
- 分类：AI / 智能开发
- 技术：OpenCV
- 笔记类型：练习笔记
- 章节序号：0460

## 本章内容

视频是由一系列连续的图像帧组成的，每一帧都是一幅静态图像。

视频处理的核心就是对这些图像帧进行处理。常见的视频处理任务包括视频读取、视频播放、视频保存、视频帧处理等。


### 视频处理的应用

- 视频分析: 通过视频处理技术，可以分析视频中的运动、目标、事件等。
- 视频增强: 对视频进行去噪、增强、稳定化等处理，提升视频质量。
- 视频编辑: 对视频进行剪辑、拼接、添加特效等操作。
- 实时监控: 通过摄像头实时监控场景，并进行目标检测、行为分析等。

OpenCV 提供了 cv2.VideoCapture 和 cv2.VideoWriter 两个类，分别用于视频的读取和写入。此外，OpenCV 还提供了丰富的图像处理函数，可以对视频帧进行各种操作。


## 视频读取与播放


### 读取视频文件

要读取视频文件，首先需要创建一个 cv2.VideoCapture 对象，并指定视频文件的路径。


## 实例


### 读取摄像头视频

除了读取视频文件，OpenCV 还可以直接从摄像头读取视频，只需将 cv2.VideoCapture 的参数设置为摄像头的索引（通常为0）即可：


## 实例


## 视频帧处理


### 帧的基本操作

在读取视频帧后，可以对每一帧进行各种图像处理操作。

例如，可以将帧转换为灰度图像：


## 实例


### 帧的保存

在处理视频帧时，有时需要将处理后的帧保存为新的视频文件。

可以使用 cv2.VideoWriter 类来实现：


## 实例


## 视频处理的高级应用


### 视频中的物体检测

OpenCV 提供了多种物体检测算法，如 Haar 特征分类器、HOG + SVM 等。

以下是一个使用 Haar 特征分类器进行人脸检测的示例：


## 实例


### 视频中的运动检测

运动检测是视频处理中的一个重要应用。可以通过计算帧之间的差异来检测运动物体。

以下是一个简单的运动检测示例：


## 实例


## 常用函数


### cv2.VideoCapture

定义: cv2.VideoCapture 用于从视频文件或摄像头中捕获视频帧。

语法:

```text
cv2.VideoCapture(source)
```

参数说明:

- source: 视频文件路径或摄像头索引（通常为0表示默认摄像头）。


## 实例


### cv2.VideoWriter

定义: cv2.VideoWriter 用于将视频帧写入视频文件。

语法:

```text
cv2.VideoWriter(filename, fourcc, fps, frameSize)
```

参数说明:

- filename: 输出视频文件名。
- fourcc: 视频编码器（如 cv2.VideoWriter_fourcc(*'XVID')）。
- fps: 帧率。
- frameSize: 帧大小（宽度, 高度）。


## 实例


### cv2.cvtColor

定义: cv2.cvtColor 用于将图像从一种颜色空间转换为另一种颜色空间。

语法:

```text
cv2.cvtColor(src, code)
```

参数说明:

- src: 输入图像。
- code: 颜色空间转换代码（如 cv2.COLOR_BGR2GRAY）。


## 实例


### cv2.resize

定义: cv2.resize 用于调整图像大小。

语法:

```text
cv2.resize(src, dsize)
```

参数说明:

- src: 输入图像。
- dsize: 输出图像大小（宽度, 高度）。


## 后续章节

- 实例
- cv2.Canny
- 实例
- cv2.findContours
- 实例
- cv2.drawContours
- 实例
- cv2.putText
- 实例

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `OpenCV 视频处理` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

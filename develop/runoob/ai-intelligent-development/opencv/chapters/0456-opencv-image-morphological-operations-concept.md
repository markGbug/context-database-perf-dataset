# OpenCV：OpenCV 图像形态学操作

- 来源：[OpenCV 图像形态学操作](https://www.runoob.com/opencv/opencv-image-morphological-operations.html)
- 分类：AI / 智能开发
- 技术：OpenCV
- 笔记类型：概念卡
- 章节序号：0456

## 本章内容

图像形态学操作是图像处理中的一种重要技术，主要用于处理二值图像（即黑白图像）。

OpenCV 中的图像形态学操作是图像处理中的重要工具，通过腐蚀、膨胀、开运算、闭运算和形态学梯度等操作，可以实现对图像的噪声去除、对象分离、边缘检测等效果。掌握这些操作有助于更好地处理和分析图像数据。

以下是 OpenCV 中常用的形态学操作及其函数：


## 1. 腐蚀 (cv2.erode())

腐蚀操作是一种缩小图像中前景对象的过程。

腐蚀操作通过将结构元素与图像进行卷积，只有当结构元素完全覆盖图像中的前景像素时，中心像素才会被保留，否则会被腐蚀掉。


### 函数原型

```text
cv2.erode(src, kernel, iterations=1)
```

- src: 输入图像，通常是二值图像。
- kernel: 结构元素，可以自定义或使用 cv2.getStructuringElement() 生成。
- iterations: 腐蚀操作的次数，默认为1。


## 实例

腐蚀操作会使图像中的前景对象变小，边缘被腐蚀掉，常用于去除噪声或分离连接的对象。


## 2. 膨胀 (cv2.dilate())

膨胀操作与腐蚀相反，它是一种扩大图像中前景对象的过程。

膨胀操作通过将结构元素与图像进行卷积，只要结构元素与图像中的前景像素有重叠，中心像素就会被保留。


### 函数原型

```text
cv2.dilate(src, kernel, iterations=1)
```

- src: 输入图像，通常是二值图像。
- kernel: 结构元素，可以自定义或使用 cv2.getStructuringElement() 生成。
- iterations: 膨胀操作的次数，默认为1。


## 实例

膨胀操作会使图像中的前景对象变大，边缘被扩展，常用于填补前景对象中的空洞或连接断裂的对象。


## 3. 开运算 (cv2.morphologyEx() with cv2.MORPH_OPEN)

开运算是先腐蚀后膨胀的组合操作。

开运算主要用于去除图像中的小噪声或分离连接的对象。


### 函数原型

```text
cv2.morphologyEx(src, op, kernel)
```

- src: 输入图像，通常是二值图像。
- op: 形态学操作类型，开运算使用 cv2.MORPH_OPEN。
- kernel: 结构元素，可以自定义或使用 cv2.getStructuringElement() 生成。


## 实例

开运算可以去除图像中的小噪声，同时保留图像中的主要前景对象。


## 4. 闭运算 (cv2.morphologyEx() with cv2.MORPH_CLOSE)

闭运算是先膨胀后腐蚀的组合操作。

闭运算主要用于填补前景对象中的小孔或连接断裂的对象。


### 函数原型

```text
cv2.morphologyEx(src, op, kernel)
```

- src: 输入图像，通常是二值图像。
- op: 形态学操作类型，闭运算使用 cv2.MORPH_CLOSE。
- kernel: 结构元素，可以自定义或使用 cv2.getStructuringElement() 生成。


## 实例

闭运算可以填补前景对象中的小孔，同时保留图像中的主要前景对象。


## 5. 形态学梯度 (cv2.morphologyEx() with cv2.MORPH_GRADIENT)

形态学梯度是膨胀图像与腐蚀图像的差值。

形态学梯度主要用于提取图像中前景对象的边缘。


### 函数原型

```text
cv2.morphologyEx(src, op, kernel)
```

- src: 输入图像，通常是二值图像。
- op: 形态学操作类型，形态学梯度使用 cv2.MORPH_GRADIENT。
- kernel: 结构元素，可以自定义或使用 cv2.getStructuringElement() 生成。


## 实例

形态学梯度可以提取图像中前景对象的边缘，常用于边缘检测。


## 记忆卡片

- 一句话定义：`OpenCV 图像形态学操作` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。

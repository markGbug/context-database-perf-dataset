# OpenCV：OpenCV 图像阈值处理

- 来源：[OpenCV 图像阈值处理](https://www.runoob.com/opencv/opencv-image-thresholding.html)
- 分类：AI / 智能开发
- 技术：OpenCV
- 笔记类型：概念卡
- 章节序号：0454

## 本章内容

在图像处理中，阈值处理是一种常用的技术，用于将图像转换为二值图像（即黑白图像）。通过设定一个阈值，可以将图像中的像素分为两类：高于阈值的像素和低于阈值的像素。

OpenCV 提供了多种阈值处理方法，本文将详细介绍三种常见的阈值处理技术：简单阈值处理、自适应阈值处理以及 Otsu's 二值化。


## 1. 简单阈值处理 (cv2.threshold())

简单阈值处理是最基础的阈值处理方法。它通过设定一个固定的阈值，将图像中的像素分为两类。

OpenCV 提供了 cv2.threshold() 函数来实现这一功能。


### 函数原型

```text
retval, dst = cv2.threshold(src, thresh, maxval, type)
```


### 参数说明

- src: 输入图像，通常为灰度图像。
- thresh: 设定的阈值。
- maxval: 当像素值超过（或小于，根据类型）阈值时，赋予的新值。
- type: 阈值处理的类型，常见的类型有： cv2.THRESH_BINARY: 如果像素值大于阈值，则赋予 maxval，否则赋予 0。 cv2.THRESH_BINARY_INV: 与 cv2.THRESH_BINARY 相反，如果像素值大于阈值，则赋予 0，否则赋予 maxval。 cv2.THRESH_TRUNC: 如果像素值大于阈值，则赋予阈值，否则保持不变。 cv2.THRESH_TOZERO: 如果像素值大于阈值，则保持不变，否则赋予 0。 cv2.THRESH_TOZERO_INV: 与 cv2.THRESH_TOZERO 相反，如果像素值大于阈值，则赋予 0，否则保持不变。


### 返回值

- retval: 实际使用的阈值（在某些情况下可能与设定的阈值不同）。
- dst: 处理后的图像。


### 实例


## 实例


## 2. 自适应阈值处理 (cv2.adaptiveThreshold())

在某些情况下，图像的亮度分布不均匀，使用固定的阈值可能无法得到理想的效果。自适应阈值处理通过为图像的不同区域计算不同的阈值，从而更好地处理这种情况。


### 函数原型

```text
dst = cv2.adaptiveThreshold(src, maxValue, adaptiveMethod, thresholdType, blockSize, C)
```


### 参数说明

- src: 输入图像，通常为灰度图像。
- maxValue: 当像素值超过（或小于，根据类型）阈值时，赋予的新值。
- adaptiveMethod: 自适应阈值计算方法，常见的类型有： cv2.ADAPTIVE_THRESH_MEAN_C: 阈值是邻域的平均值减去常数 C。 cv2.ADAPTIVE_THRESH_GAUSSIAN_C: 阈值是邻域的加权平均值减去常数 C，权重由高斯函数确定。
- thresholdType: 阈值处理的类型，通常为 cv2.THRESH_BINARY 或 cv2.THRESH_BINARY_INV。
- blockSize: 计算阈值时使用的邻域大小，必须为奇数。
- C: 从平均值或加权平均值中减去的常数。


### 返回值

- dst: 处理后的图像。


### 实例


## 实例


## 3. Otsu's 二值化 (cv2.threshold() with cv2.THRESH_OTSU)

Otsu's 二值化是一种自动确定阈值的方法。它通过最大化类间方差来找到最佳的全局阈值，适用于双峰图像（即图像直方图有两个明显的峰值）。


### 函数原型

```text
retval, dst = cv2.threshold(src, thresh, maxval, type)
```


### 参数说明

- src: 输入图像，通常为灰度图像。
- thresh: 由于 Otsu's 方法会自动确定阈值，因此该参数通常设置为 0。
- maxval: 当像素值超过（或小于，根据类型）阈值时，赋予的新值。
- type: 阈值处理的类型，通常为 cv2.THRESH_BINARY 或 cv2.THRESH_BINARY_INV，并加上 cv2.THRESH_OTSU。


### 返回值

- retval: 自动确定的阈值。
- dst: 处理后的图像。


### 实例


## 实例


## 记忆卡片

- 一句话定义：`OpenCV 图像阈值处理` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。

# OpenCV：C++ OpenCV 图像处理

- 来源：[C++ Opencv 图像处理](https://www.runoob.com/opencv/cpp-opencv-image-operator.html)
- 分类：AI / 智能开发
- 技术：OpenCV
- 笔记类型：概念卡
- 章节序号：0468

## 本章内容

## 图像滤波

图像滤波是图像处理中的一种基本操作，主要用于去除图像中的噪声或增强图像的某些特征。常见的滤波方法包括均值滤波、高斯滤波、中值滤波以及自定义滤波器。


### 均值滤波

均值滤波是一种简单的线性滤波方法，它将图像中每个像素的值替换为其邻域内所有像素值的平均值。这种方法可以有效去除噪声，但也会使图像变得模糊。

```text
cv::Mat src = cv::imread("image.jpg", cv::IMREAD_GRAYSCALE);
cv::Mat dst;
cv::blur(src, dst, cv::Size(3, 3));  // 3x3的均值滤波
```


### 高斯滤波

高斯滤波是一种非线性滤波方法，它使用高斯函数来计算邻域内像素的权重，从而对图像进行平滑处理。高斯滤波在去除噪声的同时，能够更好地保留图像的边缘信息。

```text
cv::GaussianBlur(src, dst, cv::Size(5, 5), 0);  // 5x5的高斯滤波
```


### 中值滤波

中值滤波是一种非线性滤波方法，它将图像中每个像素的值替换为其邻域内所有像素值的中值。这种方法在去除椒盐噪声时效果非常好。

```text
cv::medianBlur(src, dst, 5);  // 5x5的中值滤波
```


### 自定义滤波器

OpenCV允许用户自定义滤波器核，通过cv::filter2D函数可以实现自定义滤波操作。

```html
cv::Mat kernel = (cv::Mat_<float>(3, 3) << 1, 0, -1, 0, 0, 0, -1, 0, 1);
cv::filter2D(src, dst, -1, kernel);
```


## 图像边缘检测

边缘检测是图像处理中的一个重要任务，用于识别图像中物体的边界。常用的边缘检测方法包括Sobel算子和Canny边缘检测。


### Sobel算子

Sobel算子是一种基于梯度的边缘检测方法，它可以检测图像中的水平和垂直边缘。

```text
cv::Mat grad_x, grad_y;
cv::Sobel(src, grad_x, CV_16S, 1, 0);  // 水平方向
cv::Sobel(src, grad_y, CV_16S, 0, 1);  // 垂直方向
cv::convertScaleAbs(grad_x, grad_x);
cv::convertScaleAbs(grad_y, grad_y);
cv::addWeighted(grad_x, 0.5, grad_y, 0.5, 0, dst);  // 合并结果
```


### Canny 边缘检测

Canny 边缘检测是一种多阶段的边缘检测算法，它能够有效地检测出图像中的边缘，并且对噪声具有较强的鲁棒性。

```text
cv::Canny(src, dst, 100, 200);  // 阈值1=100，阈值2=200
```


## 图像形态学操作

形态学操作是基于图像形状的一系列操作，常用于图像的前景和背景分离、噪声去除等任务。常见的形态学操作包括腐蚀、膨胀、开运算、闭运算和形态学梯度。


### 腐蚀

腐蚀操作可以消除图像中的小物体或细节，使得前景物体变小。

```text
cv::Mat kernel = cv::getStructuringElement(cv::MORPH_RECT, cv::Size(3, 3));
cv::erode(src, dst, kernel);
```


### 膨胀

膨胀操作可以扩大图像中的前景物体，常用于填补前景物体中的空洞。

```text
cv::dilate(src, dst, kernel);
```


### 开运算

开运算是先腐蚀后膨胀的操作，常用于去除小物体或噪声。

```text
cv::morphologyEx(src, dst, cv::MORPH_OPEN, kernel);
```


### 闭运算

闭运算是先膨胀后腐蚀的操作，常用于填补前景物体中的小孔。

```text
cv::morphologyEx(src, dst, cv::MORPH_CLOSE, kernel);
```


### 形态学梯度

形态学梯度是膨胀和腐蚀的差值，可以用于提取物体的边缘。

```text
cv::morphologyEx(src, dst, cv::MORPH_GRADIENT, kernel);
```


## 图像阈值化

图像阈值化是将图像转换为二值图像的过程，常用于图像分割。常见的阈值化方法包括二值化、自适应阈值和Otsu阈值法。


### 二值化

二值化是将图像中的像素值根据设定的阈值分为两类，通常用于简单的图像分割。

```text
cv::threshold(src, dst, 127, 255, cv::THRESH_BINARY);
```


### 自适应阈值

自适应阈值根据图像的局部区域动态计算阈值，适用于光照不均匀的图像。

```text
cv::adaptiveThreshold(src, dst, 255, cv::ADAPTIVE_THRESH_MEAN_C, cv::THRESH_BINARY, 11, 2);
```


### Otsu阈值法

Otsu阈值法是一种自动确定阈值的方法，适用于双峰直方图的图像。

```text
cv::threshold(src, dst, 0, 255, cv::THRESH_BINARY | cv::THRESH_OTSU);
```


## 图像直方图

直方图是图像处理中用于分析图像亮度分布的工具。常见的直方图操作包括计算直方图、直方图均衡化和直方图对比。


### 计算直方图

直方图可以反映图像中像素值的分布情况。

```java
cv::Mat hist;
int histSize = 256;
float range[] = {0, 256};
const float* histRange = {range};
cv::calcHist(&src, 1, 0, cv::Mat(), hist, 1, &histSize, &histRange);
```


### 直方图均衡化

直方图均衡化可以增强图像的对比度，使得图像的亮度分布更加均匀。

```text
cv::equalizeHist(src, dst);
```


### 直方图对比

直方图对比可以用于比较两幅图像的相似性。

```text
double compare = cv::compareHist(hist1, hist2, cv::HISTCMP_CORREL);
```


## 实例

OpenCV 中常见的图像处理操作，包括滤波、边缘检测、阈值化、形态学操作和轮廓检测。通过这些技术，你可以实现更复杂的图像处理任务。

以下是 C++ OpenCV 中常见的图像处理操作及其代码示例：


### 1. 图像滤波

图像滤波用于去除噪声或增强图像特征。

1.1 均值滤波


## 后续章节

- 实例
- 实例
- 实例
- 2. 边缘检测
- 实例
- 3. 图像阈值化
- 实例
- 实例
- 4. 形态学操作
- 实例
- 5. 轮廓检测
- 实例

## 记忆卡片

- 一句话定义：`C++ Opencv 图像处理` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。

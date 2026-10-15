# OpenCV：C++ OpenCV 高级图像处理

- 来源：[C++ Opencv 高级图像处理](https://www.runoob.com/opencv/cpp-opencv-advanced-image-processing.html)
- 分类：AI / 智能开发
- 技术：OpenCV
- 笔记类型：概念卡
- 章节序号：0471

## 本章内容

高级图像处理是指在基础图像处理（如滤波、边缘检测等）的基础上，进一步实现更复杂的任务，例如图像分割、轮廓检测、形态学操作、直方图处理等。这些技术广泛应用于目标检测、图像分析、医学影像处理等领域。


### 高级图像处理的应用场景

医学影像分析：

- 使用图像分割技术提取病变区域。
- 使用形态学操作去除噪声。

目标检测与跟踪：

- 使用轮廓检测和模板匹配定位目标。
- 使用直方图处理增强目标特征。

图像增强：

- 使用直方图均衡化提高图像对比度。
- 使用分水岭算法分离重叠对象。


## 图像分割

图像分割是图像处理中的一个重要步骤，它将图像划分为多个区域或对象，以便于进一步的分析和处理。常见的图像分割方法包括基于阈值的分割、基于边缘的分割和基于区域的分割。


### 基于阈值的分割

基于阈值的分割是最简单的图像分割方法之一。它通过设定一个或多个阈值，将图像的像素值分为不同的类别。常见的阈值分割方法包括全局阈值和自适应阈值。

全局阈值分割使用一个固定的阈值将图像分为前景和背景。OpenCV 提供了 cv::threshold 函数来实现这一功能。

```text
cv::Mat src = cv::imread("image.jpg", cv::IMREAD_GRAYSCALE);
cv::Mat dst;
cv::threshold(src, dst, 128, 255, cv::THRESH_BINARY);
```

以上代码中，128 是阈值，255 是最大像素值，cv::THRESH_BINARY 表示使用二值化方法。

自适应阈值分割根据图像的局部区域动态调整阈值。OpenCV 提供了 cv::adaptiveThreshold 函数来实现这一功能。

```text
cv::Mat src = cv::imread("image.jpg", cv::IMREAD_GRAYSCALE);
cv::Mat dst;
cv::adaptiveThreshold(src, dst, 255, cv::ADAPTIVE_THRESH_MEAN_C, cv::THRESH_BINARY, 11, 2);
```

以上代码中，255 是最大像素值，cv::ADAPTIVE_THRESH_MEAN_C 表示使用局部均值作为阈值，11 是邻域大小，2 是常数。


### 基于边缘的分割

基于边缘的分割通过检测图像中的边缘来分割图像。常见的边缘检测算法包括 Canny 边缘检测和 Sobel 算子。

Canny 边缘检测是一种多阶段的边缘检测算法。OpenCV 提供了 cv::Canny 函数来实现这一功能。

```text
cv::Mat src = cv::imread("image.jpg", cv::IMREAD_GRAYSCALE);
cv::Mat edges;
cv::Canny(src, edges, 100, 200);
```

以上代码中，100 和 200 是 Canny 算法的两个阈值。


### 基于区域的分割（分水岭算法）

基于区域的分割通过将图像划分为多个区域来实现分割。分水岭算法是一种常用的基于区域的分割方法。

分水岭算法将图像视为地形图，通过模拟水流的扩散来分割图像。OpenCV 提供了 cv::watershed 函数来实现这一功能。

```text
cv::Mat src = cv::imread("image.jpg");
cv::Mat markers = cv::Mat::zeros(src.size(), CV_32S);
cv::watershed(src, markers);
```

以上代码中，markers 是标记矩阵，用于存储分割结果。


## 轮廓检测

轮廓检测是图像处理中的一个重要步骤，它用于检测图像中的对象边界。OpenCV 提供了多种轮廓检测和处理的函数。


### 查找轮廓

查找轮廓是轮廓检测的第一步。OpenCV 提供了 cv::findContours 函数来实现这一功能。

```html
cv::Mat src = cv::imread("image.jpg", cv::IMREAD_GRAYSCALE);
std::vector<std::vector<cv::Point>> contours;
std::vector<cv::Vec4i> hierarchy;
cv::findContours(src, contours, hierarchy, cv::RETR_TREE, cv::CHAIN_APPROX_SIMPLE);
```

以上代码中，contours 是存储轮廓的向量，hierarchy 是存储轮廓层次结构的向量。


### 轮廓特征

轮廓特征包括面积、周长、边界框等。OpenCV 提供了多种函数来计算这些特征。

面积是轮廓的一个重要特征。OpenCV 提供了 cv::contourArea 函数来计算轮廓的面积。

```text
double area = cv::contourArea(contours[0]);
```

周长是轮廓的另一个重要特征。OpenCV 提供了 cv::arcLength 函数来计算轮廓的周长。

```text
double perimeter = cv::arcLength(contours[0], true);
```

边界框是轮廓的最小外接矩形。OpenCV 提供了 cv::boundingRect 函数来计算边界框。

```text
cv::Rect rect = cv::boundingRect(contours[0]);
```


### 轮廓绘制

轮廓绘制是将检测到的轮廓绘制到图像上。OpenCV 提供了 cv::drawContours 函数来实现这一功能。

```text
cv::Mat dst = cv::Mat::zeros(src.size(), CV_8UC3);
cv::drawContours(dst, contours, -1, cv::Scalar(0, 255, 0), 2);
```

以上代码中，dst 是绘制轮廓后的图像，cv::Scalar(0, 255, 0) 是轮廓的颜色，2 是轮廓的线宽。


## 模板匹配

模板匹配是一种在图像中查找特定模板的方法。OpenCV 提供了 cv::matchTemplate 函数来实现这一功能。


### 单模板匹配

单模板匹配是在图像中查找一个模板。OpenCV 提供了 cv::matchTemplate 函数来实现这一功能。

```text
cv::Mat src = cv::imread("image.jpg");
cv::Mat templ = cv::imread("template.jpg");
cv::Mat result;
cv::matchTemplate(src, templ, result, cv::TM_CCOEFF_NORMED);
```

以上代码中，result 是匹配结果矩阵，cv::TM_CCOEFF_NORMED 是匹配方法。


### 多模板匹配

多模板匹配是在图像中查找多个模板。可以通过遍历匹配结果矩阵来实现多模板匹配。

```java
double minVal, maxVal;
cv::Point minLoc, maxLoc;
cv::minMaxLoc(result, &minVal, &maxVal, &minLoc, &maxLoc);
```

以上代码中，maxLoc 是匹配结果的最大值位置。


## 实例


### 分水岭算法


## 实例


### 轮廓检测

轮廓检测用于提取图像中对象的边界。

OpenCV 提供了 findContours 函数来检测轮廓。


## 实例


### 形态学操作

形态学操作是基于形状的图像处理技术，常用于去除噪声、分离对象等。


## 实例


### 直方图处理

直方图处理用于分析图像的像素分布，常见的操作包括直方图均衡化、直方图匹配等。


## 实例


### 模板匹配

模板匹配用于在图像中查找与模板相似的区域。


## 实例


## 记忆卡片

- 一句话定义：`C++ Opencv 高级图像处理` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。

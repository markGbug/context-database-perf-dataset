# OpenCV：OpenCV 图像轮廓检测

- 来源：[OpenCV 图像轮廓检测](https://www.runoob.com/opencv/opencv-image-contour-detection.html)
- 分类：AI / 智能开发
- 技术：OpenCV
- 笔记类型：练习笔记
- 章节序号：0458

## 本章内容

轮廓检测是图像处理中的重要任务，用于提取图像中物体的边界。

OpenCV 提供了强大的轮廓检测功能，可以用于物体识别、形状分析、目标跟踪等应用。以下是 OpenCV 图像轮廓检测的详细说明。


### 轮廓检测的基本概念

- 轮廓: 图像中物体的边界，由一系列点组成。
- 轮廓层次结构: 轮廓之间的嵌套关系，例如一个轮廓是否包含另一个轮廓。
- 轮廓特征: 轮廓的面积、周长、边界矩形、最小外接矩形、最小外接圆等。


### 轮廓检测常用函数


## 函数详细说明


### 1. cv2.findContours()

功能描述: 该函数用于在二值图像中查找轮廓。轮廓是图像中具有相同颜色或强度的连续点的曲线。

函数定义:

```text
contours, hierarchy = cv2.findContours(image, mode, method[, contours[, hierarchy[, offset]]])
```

参数说明:

- image: 输入的二值图像（通常为经过阈值处理或边缘检测后的图像）。
- mode: 轮廓检索模式，常用的有： cv2.RETR_EXTERNAL: 只检测最外层轮廓。 cv2.RETR_LIST: 检测所有轮廓，但不建立层次关系。 cv2.RETR_TREE: 检测所有轮廓，并建立完整的层次结构。
- method: 轮廓近似方法，常用的有： cv2.CHAIN_APPROX_NONE: 存储所有的轮廓点。 cv2.CHAIN_APPROX_SIMPLE: 压缩水平、垂直和对角线段，只保留端点。
- contours: 输出的轮廓列表，每个轮廓是一个点集。
- hierarchy: 输出的层次结构信息。
- offset: 可选参数，轮廓点的偏移量。

返回值:

- contours: 检测到的轮廓列表。
- hierarchy: 轮廓的层次结构信息。


## 实例


### 2. cv2.drawContours()

功能描述: 该函数用于在图像上绘制检测到的轮廓。

函数定义:

```text
cv2.drawContours(image, contours, contourIdx, color[, thickness[, lineType[, hierarchy[, maxLevel[, offset]]]]])
```

参数说明:

- image: 要绘制轮廓的图像。
- contours: 轮廓列表。
- contourIdx: 要绘制的轮廓索引，如果为负数，则绘制所有轮廓。
- color: 轮廓的颜色。
- thickness: 轮廓线的厚度，如果为负数，则填充轮廓内部。
- lineType: 线型。
- hierarchy: 轮廓的层次结构信息。
- maxLevel: 绘制的最大层次深度。
- offset: 轮廓点的偏移量。

返回值: 无返回值，直接在输入图像上绘制轮廓。


## 实例


### 3. cv2.contourArea()

功能描述: 该函数用于计算轮廓的面积。

函数定义:

```text
area = cv2.contourArea(contour[, oriented])
```

参数说明:

- contour: 输入的轮廓点集。
- oriented: 可选参数，如果为True，返回有符号的面积。

返回值: 轮廓的面积。


## 实例


### 4. cv2.arcLength()

功能描述: 该函数用于计算轮廓的周长或弧长。

函数定义:

```text
length = cv2.arcLength(curve, closed)
```

参数说明:

- curve: 输入的轮廓点集。
- closed: 布尔值，表示轮廓是否闭合。

返回值: 轮廓的周长或弧长。


## 实例


### 5. cv2.boundingRect()

功能描述: 该函数用于计算轮廓的边界矩形。

函数定义:

```text
x, y, w, h = cv2.boundingRect(points)
```

参数说明:

- points: 输入的轮廓点集。

返回值: 边界矩形的左上角坐标 (x, y) 和宽度 w、高度 h。


## 实例


### 6. cv2.minAreaRect()

功能描述: 该函数用于计算轮廓的最小外接矩形（旋转矩形）。

函数定义:

```text
rect = cv2.minAreaRect(points)
```

参数说明:

- points: 输入的轮廓点集。

返回值: 返回一个旋转矩形，包含中心点 (x, y)、宽度、高度和旋转角度。


## 实例


### 7. cv2.minEnclosingCircle()

功能描述: 该函数用于计算轮廓的最小外接圆。

函数定义:

```text
(center, radius) = cv2.minEnclosingCircle(points)
```

参数说明:

- points: 输入的轮廓点集。

返回值: 返回圆心 (x, y) 和半径 radius。


## 实例


### 8. cv2.approxPolyDP()

功能描述: 该函数用于对轮廓进行多边形近似。

函数定义:

```text
approx = cv2.approxPolyDP(curve, epsilon, closed)
```

参数说明:

- curve: 输入的轮廓点集。
- epsilon: 近似精度，值越小，近似越精确。
- closed: 布尔值，表示轮廓是否闭合。

返回值: 返回近似后的多边形点集。


## 实例


## 轮廓检测的应用

- 物体识别: 通过轮廓检测可以识别图像中的物体，例如检测圆形、矩形等。
- 形状分析: 通过计算轮廓的特征（如面积、周长、边界矩形等），可以分析物体的形状。
- 目标跟踪: 在视频中，可以通过轮廓检测跟踪运动的目标。
- 图像分割: 通过轮廓检测可以将图像中的物体分割出来。

OpenCV 提供了强大的轮廓检测功能，可以用于提取图像中物体的边界，并计算轮廓的特征。

以下是轮廓检测的主要步骤和函数：

以下是一个完整的轮廓检测示例代码：


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `OpenCV 图像轮廓检测` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

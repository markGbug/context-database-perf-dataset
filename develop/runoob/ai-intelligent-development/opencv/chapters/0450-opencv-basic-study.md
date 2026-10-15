# OpenCV：OpenCV 基础模块

- 来源：[OpenCV 基础模块](https://www.runoob.com/opencv/opencv-basic.html)
- 分类：AI / 智能开发
- 技术：OpenCV
- 笔记类型：学习笔记
- 章节序号：0450

## 本章内容

OpenCV 是一个功能强大的计算机视觉库，包含多个模块，每个模块专注于不同的功能。

OpenCV 是由多个模块组成的，每个模块都提供了不同的功能。

以下是 OpenCV 中最常用的一些模块：

- cv2.core: 核心模块，包含了图像处理的基础功能（如图像数组的表示和操作）。
- cv2.imgproc: 图像处理模块，提供图像的各种操作，如滤波、图像变换、形态学操作等。
- cv2.highgui: 图形用户界面模块，提供显示图像和视频的功能。
- cv2.video: 提供视频处理的功能，如视频捕捉、视频流的处理等。
- cv2.features2d: 特征检测与匹配模块，包含了角点、边缘、关键点检测等。
- cv2.ml: 机器学习模块，提供了多种机器学习算法，可以进行图像分类、回归、聚类等。
- cv2.calib3d : 相机校准和 3D 重建模块。
- cv2.objdetect : 目标检测模块。
- cv2.dnn : 深度学习模块。


### 1. Core 模块

功能: 提供 OpenCV 的核心功能，包括基本数据结构、矩阵操作、绘图函数等。

主要类和函数:

- Mat: OpenCV 中用于存储图像和矩阵的基本数据结构。
- Scalar: 用于表示颜色或像素值。
- Point、Size、Rect: 用于表示点、尺寸和矩形。
- 基本绘图函数: cv.line()、cv.circle()、cv.rectangle()、cv.putText() 等。

应用场景:

- 图像的基本操作（如创建、复制、裁剪）。
- 绘制几何图形和文本。


### 2. Imgproc 模块

功能: 提供图像处理功能，包括图像滤波、几何变换、颜色空间转换等。

主要类和函数:

- 图像滤波: cv.blur()、cv.GaussianBlur()、cv.medianBlur() 等。
- 几何变换: cv.resize()、cv.warpAffine()、cv.warpPerspective() 等。
- 颜色空间转换: cv.cvtColor()（如 BGR 转灰度、BGR 转 HSV）。
- 阈值处理: cv.threshold()、cv.adaptiveThreshold()。
- 边缘检测: cv.Canny()、cv.Sobel()、cv.Laplacian()。

应用场景:

- 图像平滑、锐化、边缘检测。
- 图像缩放、旋转、仿射变换。
- 图像二值化、颜色空间转换。


### 3. HighGUI 模块

功能: 提供高层 GUI 和媒体 I/O 功能，用于图像的显示和交互。

主要类和函数:

- 图像显示: cv.imshow()、cv.waitKey()、cv.destroyAllWindows()。
- 视频捕获: cv.VideoCapture()、cv.VideoWriter()。
- 鼠标和键盘事件: cv.setMouseCallback()。

应用场景:

- 显示图像和视频。
- 捕获摄像头或视频文件。
- 处理用户交互（如鼠标点击、键盘输入）。


### 4. Video 模块

功能: 提供视频分析功能，包括运动检测、目标跟踪等。

主要类和函数:

- 背景减除: cv.createBackgroundSubtractorMOG2()、cv.createBackgroundSubtractorKNN()。
- 光流法: cv.calcOpticalFlowPyrLK()。
- 目标跟踪: cv.TrackerKCF_create()、cv.TrackerMOSSE_create()。

应用场景:

- 视频中的运动检测。
- 目标跟踪（如行人、车辆跟踪）。


### 5. Calib3d 模块

功能: 提供相机校准和 3D 重建功能。

主要类和函数:

- 相机校准: cv.calibrateCamera()、cv.findChessboardCorners()。
- 3D 重建: cv.solvePnP()、cv.reprojectImageTo3D()。

应用场景:

- 相机标定（用于去除镜头畸变）。
- 3D 重建（如从 2D 图像恢复 3D 信息）。


### 6. Features2d 模块

功能: 提供特征检测和描述功能。

主要类和函数:

- 特征检测: cv.SIFT_create()、cv.ORB_create()、cv.SURF_create()。
- 特征匹配: cv.BFMatcher()、cv.FlannBasedMatcher()。
- 关键点绘制: cv.drawKeypoints()。

应用场景:

- 图像特征提取和匹配。
- 图像拼接、物体识别。


### 7. Objdetect 模块

功能: 提供目标检测功能。

主要类和函数:

- Haar 特征分类器: cv.CascadeClassifier()（用于人脸检测）。
- HOG 特征分类器: 用于行人检测。

应用场景:

- 人脸检测、行人检测。


### 8. ML 模块

功能: 提供机器学习算法。

主要类和函数:

- 支持向量机 (SVM): cv.ml.SVM_create()。
- K 均值聚类 (K-Means): cv.kmeans()。
- 神经网络 (ANN): cv.ml.ANN_MLP_create()。

应用场景:

- 图像分类、聚类分析。


### 9. DNN 模块

功能: 提供深度学习功能，支持加载和运行预训练的深度学习模型。

主要类和函数:

- 模型加载: cv.dnn.readNetFromCaffe()、cv.dnn.readNetFromTensorflow()。
- 前向传播: net.forward()。

应用场景:

- 图像分类、目标检测、语义分割。


### 10. 其他模块

- Flann: 快速近似最近邻搜索。
- Photo: 图像修复和去噪。
- Stitching: 图像拼接。
- Shape: 形状匹配和距离计算。


## 复习重点

- 能说明 `OpenCV 基础模块` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

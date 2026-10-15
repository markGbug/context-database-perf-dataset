# C++：C++ OpenCV

- 来源：[C++ OpenCV](https://www.runoob.com/cplusplus/cpp-opencv.html)
- 分类：编程语言
- 技术：C++
- 笔记类型：练习笔记
- 章节序号：3635

## 本章内容

OpenCV（Open Source Computer Vision Library）是一个开源的计算机视觉和机器学习软件库，它由一系列 C 函数和少量 C++ 类构成，同时提供了 Python、Java 和 MATLAB 等语言的接口。

OpenCV 的设计目标是提供一套通用的计算机视觉库，帮助开发者快速构建复杂的视觉应用。

OpenCV 最初由 Intel 开发，后来由 Willow Garage 和 Itseez 支持，现在由 OpenCV.org 维护。

OpenCV 广泛应用于图像处理、视频分析、物体检测、人脸识别、机器学习等领域。


### OpenCV 的核心功能

OpenCV 的核心功能包括：

- 图像处理：如图像滤波、几何变换、颜色空间转换、边缘检测等。
- 视频处理：如视频捕获、背景减除、光流计算等。
- 特征检测与描述：如 SIFT、SURF、ORB 等算法。
- 目标检测与跟踪：如 Haar 级联检测、HOG 检测、深度学习模型等。
- 相机标定与 3D 重建：如相机标定、立体视觉、点云处理等。
- 机器学习：如 KNN、SVM、决策树等传统机器学习算法。
- 深度学习：支持加载和运行 TensorFlow、PyTorch、Caffe 等框架的模型。


### OpenCV 的模块结构

OpenCV 的功能被组织成多个模块，每个模块专注于不同的任务。以下是主要模块的简介：


## OpenCV 的主要模块

OpenCV 库由多个模块组成，每个模块专注于不同的功能。以下是 OpenCV 中的一些主要模块：


### 1. Core 模块

Core 模块是 OpenCV 的核心模块，包含了最基本的数据结构和函数。它定义了 OpenCV 中最常用的数据类型，如 Mat（矩阵）、Point、Rect 等。Core 模块还提供了基本的数学运算、内存管理、文件 I/O 等功能。

- Mat 类：Mat 是 OpenCV 中最常用的数据结构，用于存储图像和矩阵数据。它是一个多维数组，可以表示灰度图像、彩色图像、3D 矩阵等。
- 基本操作：Core 模块提供了矩阵的加减乘除、转置、求逆等基本操作。


### 2. Imgproc 模块

Imgproc 模块是图像处理模块，提供了大量的图像处理函数。这些函数可以用于图像的滤波、几何变换、颜色空间转换、直方图计算等。

- 图像滤波：包括均值滤波、高斯滤波、中值滤波等，用于去除图像中的噪声。
- 几何变换：如图像的缩放、旋转、仿射变换等。
- 边缘检测：如 Canny 边缘检测、Sobel 算子等。
- 直方图均衡化：用于增强图像的对比度。


### 3. Highgui 模块

Highgui 模块提供了图形用户界面（GUI）功能，允许开发者创建窗口、显示图像、处理鼠标和键盘事件等。

- 图像显示：使用 imshow 函数可以在窗口中显示图像。
- 视频捕获：使用 VideoCapture 类可以从摄像头或视频文件中捕获视频帧。
- 事件处理：可以处理鼠标点击、键盘输入等事件。


### 4. Video 模块

Video 模块专注于视频分析，提供了视频捕获、背景减除、光流计算等功能。

- 视频捕获：使用 VideoCapture 类可以从摄像头或视频文件中读取视频帧。
- 背景减除：用于从视频中提取前景物体。
- 光流计算：用于估计图像中物体的运动。


### 5. Calib3d 模块

Calib3d 模块提供了相机校准、3D 重建、立体视觉等功能。它主要用于处理与相机相关的几何问题。

- 相机校准：用于估计相机的内参和外参。
- 3D 重建：从多张图像中重建三维场景。
- 立体视觉：用于计算深度图。


### 6. Features2d 模块

Features2d 模块提供了特征检测和描述符提取的功能。它包含了多种特征检测算法，如 SIFT、SURF、ORB 等。

- 特征检测：检测图像中的关键点。
- 描述符提取：为每个关键点生成描述符，用于匹配不同图像中的特征。


### 7. Objdetect 模块

Objdetect 模块提供了物体检测的功能，特别是基于 Haar 特征和 LBP 特征的级联分类器。

- 人脸检测：使用 Haar 特征和级联分类器检测图像中的人脸。
- 物体检测：可以检测其他类型的物体，如眼睛、车辆等。


### 8. ML 模块

ML 模块是机器学习模块，提供了多种机器学习算法，如支持向量机（SVM）、K 近邻（KNN）、决策树等。

- 分类：使用 SVM、KNN 等算法进行分类。
- 回归：使用线性回归等算法进行回归分析。
- 聚类：使用 K-means 等算法进行聚类分析。


### 9. DNN 模块

DNN 模块是深度学习模块，提供了加载和运行深度学习模型的功能。它支持多种深度学习框架，如 TensorFlow、Caffe、ONNX 等。

- 模型加载：可以加载预训练的深度学习模型。
- 推理：使用加载的模型进行图像分类、目标检测等任务。


## OpenCV 的安装与配置

在使用 OpenCV 之前，需要先安装并配置好开发环境。


### 3.1 安装 OpenCV

在 Linux 系统上，可以使用包管理器安装 OpenCV：

```text
sudo apt-get install libopencv-dev
```

在 Windows 系统上，可以从 OpenCV 官网下载预编译的库，或者使用 vcpkg 进行安装。


### 配置开发环境

在 C++ 项目中使用 OpenCV 时，需要在编译时链接 OpenCV 库。

以下是一个简单的 CMake 配置示例：

```text
cmake_minimum_required(VERSION 3.10)
project(OpenCVExample)

find_package(OpenCV REQUIRED)

add_executable(OpenCVExample main.cpp)

target_link_libraries(OpenCVExample ${OpenCV_LIBS})
```


## 一个简单的 OpenCV 示例

以下是一个使用 OpenCV 读取并显示图像的简单示例：


## 实例

以上代码中，我们使用 imread 函数读取图像，使用 imshow 函数显示图像，并使用 waitKey 函数等待用户按键。


## OpenCV 相关内容


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `C++ OpenCV` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

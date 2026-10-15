# OpenCV：OpenCV 图像边缘检测

- 来源：[OpenCV 图像边缘检测](https://www.runoob.com/opencv/opencv-image-edge-detection.html)
- 分类：AI / 智能开发
- 技术：OpenCV
- 笔记类型：练习笔记
- 章节序号：0457

## 本章内容

图像边缘检测是计算机视觉和图像处理中的一项基本任务，它用于识别图像中亮度变化明显的区域，这些区域通常对应于物体的边界。

是 OpenCV 中常用的边缘检测函数及其说明:


## 1. Canny 边缘检测 (cv2.Canny())

Canny 边缘检测是一种多阶段的边缘检测算法，由 John F. Canny 在 1986 年提出。

Canny 边缘检测被认为是边缘检测的"金标准"，因为它能够在噪声抑制和边缘定位之间取得良好的平衡。


### 1.1 Canny 边缘检测的步骤

Canny 边缘检测算法主要包括以下几个步骤：

- 噪声抑制：使用高斯滤波器对图像进行平滑处理，以减少噪声的影响。
- 计算梯度：使用 Sobel 算子计算图像的梯度幅值和方向。
- 非极大值抑制：沿着梯度方向，保留局部梯度最大的像素点，抑制其他像素点。
- 双阈值检测：使用两个阈值（低阈值和高阈值）来确定真正的边缘。高于高阈值的像素点被认为是强边缘，低于低阈值的像素点被抑制，介于两者之间的像素点如果与强边缘相连则保留。
- 边缘连接：通过滞后阈值处理，将弱边缘与强边缘连接起来，形成完整的边缘。


### 1.2 使用 OpenCV 实现 Canny 边缘检测

在 OpenCV 中，可以使用 cv2.Canny() 函数来实现 Canny 边缘检测。

该函数的原型如下：

```text
edges = cv2.Canny(image, threshold1, threshold2, apertureSize=3, L2gradient=False)
```

- image：输入图像，必须是单通道的灰度图像。
- threshold1：低阈值。
- threshold2：高阈值。
- apertureSize：Sobel 算子的孔径大小，默认为 3。
- L2gradient：是否使用 L2 范数计算梯度幅值，默认为 False（使用 L1 范数）。


## 实例


## 2. Sobel 算子 (cv2.Sobel())

Sobel 算子是一种基于梯度的边缘检测算子，它通过计算图像在水平和垂直方向上的梯度来检测边缘。

Sobel 算子结合了高斯平滑和微分操作，因此对噪声具有一定的抑制作用。


### 2.1 Sobel 算子的原理

Sobel 算子使用两个 3x3 的卷积核分别计算图像在水平和垂直方向上的梯度：

- 水平方向的卷积核：[-1, 0, 1] [-2, 0, 2] [-1, 0, 1]
- 垂直方向的卷积核：[-1, -2, -1] [ 0, 0, 0] [ 1, 2, 1]

通过这两个卷积核，可以分别得到图像在水平和垂直方向上的梯度 Gx 和 Gy。最终的梯度幅值可以通过以下公式计算：

```text
G = sqrt(Gx^2 + Gy^2)
```


### 2.2 使用 OpenCV 实现 Sobel 算子

在 OpenCV 中，可以使用 cv2.Sobel() 函数来计算图像的梯度。该函数的原型如下：

```text
dst = cv2.Sobel(src, ddepth, dx, dy, ksize=3, scale=1, delta=0, borderType=cv2.BORDER_DEFAULT)
```

- src：输入图像。
- ddepth：输出图像的深度，通常使用 cv2.CV_64F。
- dx：x 方向上的导数阶数。
- dy：y 方向上的导数阶数。
- ksize：Sobel 核的大小，默认为 3。
- scale：缩放因子，默认为 1。
- delta：可选的 delta 值，默认为 0。
- borderType：边界填充类型，默认为 cv2.BORDER_DEFAULT。


## 实例


## 3. Laplacian 算子 (cv2.Laplacian())

Laplacian 算子是一种二阶微分算子，它通过计算图像的二阶导数来检测边缘。Laplacian 算子对噪声比较敏感，因此通常在使用之前会对图像进行高斯平滑处理。


### 3.1 Laplacian 算子的原理

Laplacian 算子使用以下卷积核来计算图像的二阶导数：

```text
[ 0,  1,  0]
[ 1, -4,  1]
[ 0,  1,  0]
```

通过这个卷积核，可以得到图像的 Laplacian 值。Laplacian 值较大的区域通常对应于图像的边缘。


### 3.2 使用 OpenCV 实现 Laplacian 算子

在 OpenCV 中，可以使用 cv2.Laplacian() 函数来计算图像的 Laplacian 值。

该函数的原型如下：

```text
dst = cv2.Laplacian(src, ddepth, ksize=1, scale=1, delta=0, borderType=cv2.BORDER_DEFAULT)
```

- src：输入图像。
- ddepth：输出图像的深度，通常使用 cv2.CV_64F。
- ksize：Laplacian 核的大小，默认为 1。
- scale：缩放因子，默认为 1。
- delta：可选的 delta 值，默认为 0。
- borderType：边界填充类型，默认为 cv2.BORDER_DEFAULT。


## 实例


## 常用边缘检测函数对比

以下是 OpenCV 中常用边缘检测函数的对比：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `OpenCV 图像边缘检测` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

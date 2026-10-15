# OpenCV：OpenCV 图像处理基础

- 来源：[OpenCV 图像处理基础](https://www.runoob.com/opencv/opencv-image-basic.html)
- 分类：AI / 智能开发
- 技术：OpenCV
- 笔记类型：学习笔记
- 章节序号：0451

## 本章内容

OpenCV 提供了丰富的图像处理和计算机视觉功能，包括图像读取、显示、颜色空间转换、滤波、边缘检测、轮廓检测等。

本章节我们将介绍 OpenCV 的基本概念和常用功能。


### 图像的表示和处理

OpenCV 通过 NumPy 数组 来表示图像数据，每个图像就是一个多维数组，其中每个元素对应图像中的一个像素。图像的尺寸和颜色模式也可以通过数组的形状来表示。

图像的基本属性：

- 图像的尺寸（Width, Height）：可以通过 img.shape 获取。
- 颜色通道（Channels）：通常为 RGB（三个通道），也可以是灰度图（单通道）。
- 数据类型（Data type）：常见的有 uint8（0-255 范围），也可以是 float32 或其他。

读取图像：

```text
import cv2
img = cv2.imread('image.jpg')
```

- cv2.imread() 读取图像文件，返回一个 NumPy 数组。
- 如果图像路径错误或文件不存在，返回 None。

显示图像：

```text
# 显示图像
cv2.imshow("Display Window", image)

# 等待按键输入
cv2.waitKey(0)

# 关闭所有窗口
cv2.destroyAllWindows()
```

cv2.imshow() 用于显示图像，cv2.waitKey(0) 等待按键事件，cv2.destroyAllWindows() 关闭所有窗口。

保存图像：

```text
# 保存图像
cv2.imwrite("output_image.jpg", image)
```

cv2.imwrite() 将图像保存到指定路径。


### 图像基本操作

1、访问和修改像素值

```text
# 获取像素值 (BGR 格式)
pixel_value = image[100, 100]  # 获取 (100, 100) 处的像素值

# 修改像素值
image[100, 100] = [255, 255, 255]  # 将 (100, 100) 处的像素设置为白色
```

2、图像 ROI（Region of Interest）

```text
# 获取 ROI
roi = image[50:150, 50:150]  # 获取 (50,50) 到 (150,150) 的区域

# 修改 ROI
image[50:150, 50:150] = [0, 255, 0]  # 将 ROI 区域设置为绿色
```

3、图像通道分离与合并

```text
# 分离通道
b, g, r = cv2.split(image)

# 合并通道
merged_image = cv2.merge([b, g, r])
```

4、图像缩放、旋转、平移、翻转

```text
# 缩放
resized_image = cv2.resize(image, (new_width, new_height))

# 旋转
rotation_matrix = cv2.getRotationMatrix2D((center_x, center_y), angle, scale)
rotated_image = cv2.warpAffine(image, rotation_matrix, (width, height))

# 平移
translation_matrix = np.float32([[1, 0, tx], [0, 1, ty]])  # tx, ty 为平移距离
translated_image = cv2.warpAffine(image, translation_matrix, (width, height))

# 翻转
flipped_image = cv2.flip(image, flip_code)  # flip_code: 0 (垂直翻转), 1 (水平翻转), -1 (双向翻转)
```


### 图像算术运算

1、图像加法

```text
result = cv2.add(image1, image2)
```

2、图像减法

```text
result = cv2.subtract(image1, image2)
```

3、图像混合

```text
result = cv2.addWeighted(image1, alpha, image2, beta, gamma)
```

alpha 和 beta 是权重，gamma 是标量值。


### 图像阈值处理

1、简单阈值处理

```text
ret, thresholded_image = cv2.threshold(image, thresh, maxval, cv2.THRESH_BINARY)
```

thresh 是阈值，maxval 是最大值。

2、自适应阈值处理

```text
thresholded_image = cv2.adaptiveThreshold(image, maxval, cv2.ADAPTIVE_THRESH_MEAN_C, cv2.THRESH_BINARY, block_size, C)
```

3、Otsu's 二值化

```text
ret, thresholded_image = cv2.threshold(image, 0, 255, cv2.THRESH_BINARY + cv2.THRESH_OTSU)
```


### 图像平滑处理

1、均值滤波

```text
blurred_image = cv2.blur(image, (kernel_size, kernel_size))
```

2、高斯滤波

```text
blurred_image = cv2.GaussianBlur(image, (kernel_size, kernel_size), sigmaX)
```

3、中值滤波

```text
blurred_image = cv2.medianBlur(image, kernel_size)
```

4、双边滤波

```text
blurred_image = cv2.bilateralFilter(image, d, sigmaColor, sigmaSpace)
```


### 图像的颜色空间与转换

OpenCV 支持多种颜色空间的转换，如从 RGB 到灰度图、HSV 等。

图像的颜色空间转换在许多图像处理任务中非常重要。

从 RGB 转换为灰度图：

```text
gray_img = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
```

从 BGR 转换为 HSV：

```text
hsv_img = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)
```

从 RGB 转换为 YUV：

```text
yuv_img = cv2.cvtColor(img, cv2.COLOR_BGR2YUV)
```

颜色空间转换是图像处理中的基础操作，用于不同的算法和视觉效果。


### 图像的大小调整与裁剪

OpenCV 提供了多种方式来调整图像大小和裁剪图像区域。

调整图像大小：

```text
resized_img = cv2.resize(img, (width, height))
```

裁剪图像：

```text
cropped_img = img[y1:y2, x1:x2]
```

可以通过切片操作裁剪图像的特定区域。


### 图像平滑与去噪（模糊处理）

图像平滑可以减少噪声，常用的模糊算法有高斯模糊、均值模糊等。

高斯模糊：

```text
blurred_img = cv2.GaussianBlur(img, (5, 5), 0)
```

均值模糊：

```text
blurred_img = cv2.blur(img, (5, 5))
```

中值模糊：

```text
blurred_img = cv2.medianBlur(img, 5)
```


### 图像边缘检测

边缘检测是一种常用的图像处理技术，用于检测图像中的边缘，最常用的方法是 Canny 边缘检测。

Canny 边缘检测：

```text
edges = cv2.Canny(img, 100, 200)
```

Canny 算法通过对图像进行梯度计算来找出边缘，返回一个二值图像，边缘处为白色，其他区域为黑色。

Sobel 算子：

```text
sobel_x = cv2.Sobel(image, cv2.CV_64F, 1, 0, ksize=5)
sobel_y = cv2.Sobel(image, cv2.CV_64F, 0, 1, ksize=5)
```

Laplacian 算子：

```text
laplacian = cv2.Laplacian(image, cv2.CV_64F)
```


### 形态学操作

形态学操作常用于二值图像的处理，常见的操作有腐蚀、膨胀、开运算、闭运算等。

腐蚀（Erosion）：将图像中的白色区域收缩。

```text
kernel = cv2.getStructuringElement(cv2.MORPH_RECT, (5, 5))
eroded_img = cv2.erode(img, kernel, iterations=1)
```

膨胀（Dilation）：将图像中的白色区域扩展。

```text
dilated_img = cv2.dilate(img, kernel, iterations=1)
```

开运算与闭运算：

- 开运算（先腐蚀再膨胀）：用于去除小物体。
- 闭运算（先膨胀再腐蚀）：用于填补图像中的小孔洞。

```text
opening_img = cv2.morphologyEx(img, cv2.MORPH_OPEN, kernel)
closing_img = cv2.morphologyEx(img, cv2.MORPH_CLOSE, kernel)
```


### 图像轮廓检测

OpenCV 提供了强大的轮廓检测功能，可以用于对象识别、图像分割等应用。

检测轮廓：

```text
gray_img = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
_, threshold_img = cv2.threshold(gray_img, 127, 255, cv2.THRESH_BINARY)
contours, _ = cv2.findContours(threshold_img, cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_SIMPLE)
```

绘制轮廓：

```text
cv2.drawContours(img, contours, -1, (0, 255, 0), 3)
```


### 视频处理

OpenCV 也支持视频的处理，可以读取视频文件、捕捉视频流并进行实时处理。

读取视频：


## 实例


## 复习重点

- 能说明 `OpenCV 图像处理基础` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

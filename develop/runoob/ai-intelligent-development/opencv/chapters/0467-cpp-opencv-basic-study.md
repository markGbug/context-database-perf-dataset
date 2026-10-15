# OpenCV：C++ OpenCV 基础操作

- 来源：[C++ OpenCV 基础操作](https://www.runoob.com/opencv/cpp-opencv-basic.html)
- 分类：AI / 智能开发
- 技术：OpenCV
- 笔记类型：学习笔记
- 章节序号：0467

## 本章内容

## 图像的基本操作


### 读取、显示和保存图像

在 OpenCV 中，图像的基本操作包括读取、显示和保存图像。这些操作是图像处理的基础。

读取图像：使用imread函数读取图像。该函数的第一个参数是图像文件的路径，第二个参数是读取图像的方式（如彩色图像、灰度图像等）。

```text
cv::Mat image = cv::imread("image.jpg", cv::IMREAD_COLOR);
```

显示图像：使用imshow函数显示图像。该函数的第一个参数是窗口的名称，第二个参数是要显示的图像。

```text
cv::imshow("Display Window", image);
cv::waitKey(0); // 等待按键按下
```

```text
cv::imwrite("output.jpg", image);
```


### 图像的基本属性

图像的基本属性包括尺寸、通道数和像素值。

尺寸：图像的尺寸可以通过rows和cols属性获取。

```java
int height = image.rows;
int width = image.cols;
```

通道数：图像的通道数可以通过channels()方法获取。

```java
int channels = image.channels();
```

像素值：可以通过at方法访问图像的像素值。

```html
cv::Vec3b pixel = image.at<cv::Vec3b>(y, x); // 访问(x, y)处的像素值
```


### 图像的创建与初始化

可以通过Mat类创建和初始化图像。

创建图像：可以创建一个指定大小和类型的图像。

```text
cv::Mat newImage(480, 640, CV_8UC3, cv::Scalar(0, 0, 255)); // 创建一个640x480的红色图像
```

初始化图像：可以使用setTo方法初始化图像。

```text
image.setTo(cv::Scalar(255, 255, 255)); // 将图像初始化为白色
```


### 图像的像素操作

图像的像素操作包括遍历像素和修改像素值。

遍历像素：可以使用双重循环遍历图像的每个像素。

```java
for (int y = 0; y < image.rows; y++) {
    for (int x = 0; x < image.cols; x++) {
        cv::Vec3b& pixel = image.at<cv::Vec3b>(y, x);
        // 对像素进行操作
    }
}
```

修改像素值：可以直接修改像素的值。

```text
pixel[0] = 255; // 将蓝色通道设置为255
pixel[1] = 0;   // 将绿色通道设置为0
pixel[2] = 0;   // 将红色通道设置为0
```


## 图像的几何变换


### 缩放、旋转、平移、翻转

图像的几何变换包括缩放、旋转、平移和翻转。

缩放：使用resize函数缩放图像。

```text
cv::Mat resizedImage;
cv::resize(image, resizedImage, cv::Size(newWidth, newHeight));
```

旋转：使用getRotationMatrix2D和warpAffine函数旋转图像。

```text
cv::Point2f center(image.cols / 2.0, image.rows / 2.0);
cv::Mat rotationMatrix = cv::getRotationMatrix2D(center, angle, 1.0);
cv::Mat rotatedImage;
cv::warpAffine(image, rotatedImage, rotationMatrix, image.size());
```

平移：使用warpAffine函数平移图像。

```html
cv::Mat translationMatrix = (cv::Mat_<double>(2, 3) << 1, 0, tx, 0, 1, ty);
cv::Mat translatedImage;
cv::warpAffine(image, translatedImage, translationMatrix, image.size());
```

翻转：使用flip函数翻转图像。

```text
cv::Mat flippedImage;
cv::flip(image, flippedImage, 1); // 1表示水平翻转，0表示垂直翻转
```


### 仿射变换与透视变换

仿射变换：仿射变换是线性变换加上平移，可以使用warpAffine函数实现。

```text
cv::Mat affineMatrix = cv::getAffineTransform(srcPoints, dstPoints);
cv::Mat affineImage;
cv::warpAffine(image, affineImage, affineMatrix, image.size());
```

透视变换：透视变换是更一般的变换，可以使用warpPerspective函数实现。

```text
cv::Mat perspectiveMatrix = cv::getPerspectiveTransform(srcPoints, dstPoints);
cv::Mat perspectiveImage;
cv::warpPerspective(image, perspectiveImage, perspectiveMatrix, image.size());
```


## 图像的颜色空间转换


### RGB、灰度、HSV等颜色空间

图像的颜色空间包括RGB、灰度和HSV等。

- RGB：RGB是最常见的颜色空间，表示红、绿、蓝三个通道。
- 灰度：灰度图像只有一个通道，表示亮度。
- HSV：HSV颜色空间表示色调（Hue）、饱和度（Saturation）和亮度（Value）。


### 颜色空间转换

使用 cvtColor 函数进行颜色空间转换。

RGB 转灰度：

```text
cv::Mat grayImage;
cv::cvtColor(image, grayImage, cv::COLOR_BGR2GRAY);
```

RGB转HSV：

```text
cv::Mat hsvImage;
cv::cvtColor(image, hsvImage, cv::COLOR_BGR2HSV);
```


### 通道分离与合并

通道分离：使用split函数将图像的通道分离。

```html
std::vector<cv::Mat> channels;
cv::split(image, channels);
```

通道合并：使用merge函数将多个通道合并为一个图像。

```text
cv::Mat mergedImage;
cv::merge(channels, mergedImage);
```


## 实例

C++ OpenCV 的基础操作包括图像的读取、显示、保存、像素操作、图像属性获取等。

以下是一些常见的 OpenCV 基础操作及其代码示例：


### 1. 图像的读取与显示


## 实例


### 2. 图像的保存


## 实例


### 3. 获取图像属性


## 实例


### 4. 访问和修改像素值


## 实例


### 5. 图像颜色空间转换


## 实例


### 6. 图像的裁剪与缩放


## 后续章节

- 实例
- 7. 图像的复制与克隆
- 实例
- 8. 图像的几何变换
- 实例

## 复习重点

- 能说明 `C++ OpenCV 基础操作` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

# OpenCV：OpenCV 安装（C++）

- 来源：[OpenCV 安装（C++）](https://www.runoob.com/opencv/opencv-install-cpp.html)
- 分类：AI / 智能开发
- 技术：OpenCV
- 笔记类型：概念卡
- 章节序号：0448

## 本章内容

OpenCV（Open Source Computer Vision Library）是一个开源的计算机视觉和机器学习软件库，包含了数百个计算机视觉算法，广泛应用于图像处理、视频分析、物体检测、人脸识别等领域。

C++ 是 OpenCV 的原始开发语言，适合高性能应用。

在 C++ 项目中使用 OpenCV 之前，首先需要安装 OpenCV 库。


### 下载 OpenCV

访问 OpenCV 的官方下载页面：https://opencv.org/releases/。

选择适合你操作系统的版本（例如 Windows、Linux、macOS）并下载，例如OpenCV 4.x 的 Windows 预编译包。 。


### Windows 安装 OpenCV

- 解压下载的 OpenCV 文件：解压到一个目录，例如 C:\opencv。
- 设置环境变量：将 OpenCV 的 bin 目录 C:\opencv\build\x64\vc15\bin（根据你的 Visual Studio 版本选择 vc14 或 vc15） 添加到系统的 PATH 环境变量中。
- 配置开发环境：如果使用 Visual Studio，需要在项目中配置 OpenCV 的头文件路径和库文件路径。右键点击"此电脑" -> "属性" -> "高级系统设置" -> "环境变量" -> 编辑Path，添加上述路径。


### 配置 Visual Studio

1、打开 Visual Studio，创建一个 C++ 项目。


## 记忆卡片

- 一句话定义：`OpenCV 安装（C++）` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。

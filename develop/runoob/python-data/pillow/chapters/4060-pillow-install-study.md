# Pillow：Pillow 安装

- 来源：[Pillow 安装](https://www.runoob.com/pillow/pillow-install.html)
- 分类：Python / 数据科学
- 技术：Pillow
- 笔记类型：学习笔记
- 章节序号：4060

## 本章内容

在安装 Pillow 之前，请确保：

- Python 3.7 或更高版本（推荐最新版本）
- pip 包管理器（通常随 Python 一起安装）
- 根据平台不同，可能需要一些额外的系统库和开发工具


### Python 版本

Pillow 需要 Python 3.7 或更高版本。

您可以通过以下命令检查 Python 版本：

```text
python --version
# 或
python3 --version
```


### pip 工具

pip 是 Python 的包管理工具，通常随 Python 一起安装。

检查 pip 是否可用：

```text
pip --version
# 或
pip3 --version
```

如果未安装 pip，可以参考 官方 pip 安装指南 进行安装。


## 安装 Pillow


### 基本安装方法

最简单的方法是使用 pip 安装：

```text
pip install pillow
```

或者针对 Python 3 明确指定：

```text
pip3 install pillow
```

如果您使用 Anaconda Python 发行版：

```text
conda install -c anaconda pillow
```


### 指定版本安装

如果需要安装特定版本的 Pillow：

```text
pip install pillow==9.0.0
```


### 在虚拟环境中安装

建议在虚拟环境中安装 Pillow，以避免依赖冲突：

```text
# 创建虚拟环境
python -m venv pillow_env

# 激活虚拟环境
# Windows:
pillow_env\Scripts\activate

# 安装 Pillow
pip install Pillow
```


### 从源代码安装

对于高级用户，可以从源代码安装：

下载源代码：

```text
git clone https://github.com/python-pillow/Pillow.git
cd Pillow
```

安装依赖：

```text
pip install -r requirements.txt
```

编译安装：

```text
python setup.py install
```


## 验证安装

安装完成后，可以通过以下方式验证 Pillow 是否成功安装：


### 方法 1：Python 交互式环境


## 实例


### 方法 2：命令行检查

```text
python3 -c "import PIL; print(PIL.__version__)"
```

如果安装成功，将显示 Pillow 的版本号。


## 常见问题解决


### 1. 安装失败

可能原因：

- 缺少依赖库（如 zlib、libjpeg 等）
- 权限问题

解决方案：

Linux/macOS 用户可能需要先安装系统依赖：


## 实例

使用 --user 参数避免权限问题：

```text
pip install --user pillow
```


### 2. 导入错误

如果遇到 ImportError: cannot import name '_imaging' from 'PIL' 等错误，尝试：

```text
pip uninstall pillow
pip install --no-cache-dir pillow
```


### 3. 性能问题

```text
pip install pillow-simd
```


## 第一个 Pillow 程序

成功安装 Pillow 后，您可以开始探索其强大的图像处理功能：


## 实例

代码解析：

- 导入模块from PIL import Image → 导入Pillow的Image模块
- 打开图像img = Image.open("example.jpg") → 加载指定路径的图片文件支持格式：JPG/PNG/GIF/BMP等
- 显示图像img.show() → 用系统默认图片查看器打开仅用于调试，生产环境不推荐
- 保存图像img.save("example.png") → 另存为指定格式格式由文件扩展名决定（如.jpg/.png）
- 调整尺寸small_img = img.resize((100,100)) → 强制调整为100×100像素注意：会改变原图比例
- 保存新图small_img.save("small_example.jpg") → 保存调整后的图片可添加quality参数控制JPEG质量


## 复习重点

- 能说明 `Pillow 安装` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

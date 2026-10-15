# TensorFlow：TensorFlow 环境搭建

- 来源：[TensorFlow 环境搭建](https://www.runoob.com/tensorflow/tensorflow-setup.html)
- 分类：AI / 智能开发
- 技术：TensorFlow
- 笔记类型：学习笔记
- 章节序号：0658

## 本章内容

TensorFlow 2.x 对 Python 版本有特定要求：

推荐使用 Python 3.9-3.11，这些版本具有最好的兼容性和稳定性。


### 检查当前 Python 版本

```text
# 检查 Python 版本
python --version
# 或
python3 --version

# 检查 pip 版本
pip --version
# 或
pip3 --version
```


### Python 安装选项

选项 1：官方 Python（推荐新手）

- 访问 python.org 下载安装
- 安装时勾选 "Add Python to PATH"
- 包含 pip 包管理器

选项 2：Anaconda/Miniconda（推荐数据科学）

- Anaconda：完整的数据科学环境
- Miniconda：轻量级版本
- 内置环境管理和包管理

选项 3：系统包管理器

```text
# Ubuntu/Debian
sudo apt update
sudo apt install python3 python3-pip

# macOS (使用 Homebrew)
brew install python3

# Windows (使用 Chocolatey)
choco install python3
```


## 虚拟环境设置（强烈推荐）


### 为什么使用虚拟环境

好处：

- 隔离依赖：避免不同项目间的包版本冲突
- 干净环境：保持系统 Python 环境整洁
- 易于管理：可以轻松删除和重建环境
- 可复现性：便于在不同机器上复现环境


### 使用 venv 创建虚拟环境

```text
# 创建虚拟环境
python -m venv tensorflow_env

# 激活虚拟环境
# Windows:
tensorflow_env\Scripts\activate
# macOS/Linux:
source tensorflow_env/bin/activate

# 确认激活（提示符会显示环境名）
which python  # 应该指向虚拟环境中的 python

# 升级 pip
python -m pip install --upgrade pip
```


### 使用 Conda 创建虚拟环境

```text
# 创建新环境
conda create -n tensorflow_env python=3.10

# 激活环境
conda activate tensorflow_env

# 列出所有环境
conda env list

# 在环境中安装包
conda install pip
```


### 虚拟环境管理

```text
# 查看已安装的包
pip list

# 生成依赖文件
pip freeze > requirements.txt

# 从文件安装依赖
pip install -r requirements.txt

# 退出虚拟环境
deactivate  # venv
conda deactivate  # conda

# 删除虚拟环境
rm -rf tensorflow_env  # venv
conda env remove -n tensorflow_env  # conda
```


## TensorFlow 安装


### CPU 版本安装（适合学习和轻量级任务）

```text
# 确保在虚拟环境中
pip install tensorflow

# 验证安装
python -c "import tensorflow as tf; print('TensorFlow version:', tf.__version__)"
```

CPU 版本特点：

- 优点：安装简单，无需额外配置
- 缺点：训练速度较慢，适合小规模数据
- 适用场景：学习、原型开发、推理部署


### GPU 版本安装（适合大规模训练）

GPU 加速可以显著提升训练速度，特别是对于深度学习任务。

硬件要求：

- NVIDIA GPU（计算能力 3.5 或更高）
- 8GB+ 显存（推荐）

查看 GPU 信息：

```text
# Windows
nvidia-smi

# Linux
lspci | grep -i nvidia
```

TensorFlow 2.15+ 与 CUDA 版本对应：

安装步骤：

- 下载和安装 CUDA Toolkit 访问 NVIDIA CUDA Toolkit 选择对应版本下载安装 添加到系统 PATH
- 下载和安装 cuDNN 访问 NVIDIA cuDNN 需要注册 NVIDIA 账户 解压到 CUDA 安装目录
- 验证 CUDA 安装 nvcc --version nvidia-smi

```text
# TensorFlow 2.10+ 统一包名
pip install tensorflow

# 验证 GPU 可用性
python -c "
import tensorflow as tf
print('TensorFlow version:', tf.__version__)
print('GPU available:', tf.config.list_physical_devices('GPU'))
print('Built with CUDA:', tf.test.is_built_with_cuda())
"
```


### 通过 Conda 安装

```text
# CPU 版本
conda install tensorflow

# 或从 conda-forge
conda install -c conda-forge tensorflow

# GPU 版本（自动安装 CUDA）
conda install tensorflow-gpu
```


### 安装特定版本

```text
# 安装特定版本
pip install tensorflow==2.14.0

# 安装预发布版本
pip install tf-nightly

# 升级到最新版本
pip install --upgrade tensorflow
```


## 开发工具安装


### upyter Notebook/Lab

Jupyter 是数据科学和机器学习的标准开发环境：

```text
# 安装 Jupyter Notebook
pip install jupyter notebook

# 或安装 JupyterLab（推荐）
pip install jupyterlab

# 启动 Jupyter
jupyter notebook
# 或
jupyter lab
```

Jupyter 扩展：

```text
# 安装有用的扩展
pip install jupyter_contrib_nbextensions
jupyter contrib nbextension install --user

# 变量检查器
pip install nbextensions
```


### IDE 选择

Visual Studio Code（推荐）：

- 安装 Python 扩展
- 安装 Jupyter 扩展
- 智能代码补全和调试

PyCharm：

- 专业的 Python IDE
- 强大的调试功能
- 内置 Git 支持

Google Colab（云端选项）：

- 免费 GPU 使用
- 预装常用库
- 无需本地配置


### 必要的 Python 包

```text
# 数据处理
pip install numpy pandas matplotlib seaborn

# 科学计算
pip install scipy scikit-learn

# 图像处理
pip install pillow opencv-python

# 进度条和实用工具
pip install tqdm

# 创建完整的要求文件
cat > requirements.txt << EOF
tensorflow>=2.12.0
numpy>=1.21.0
pandas>=1.3.0
matplotlib>=3.5.0
seaborn>=0.11.0
scikit-learn>=1.0.0
jupyter>=1.0.0
tqdm>=4.60.0
pillow>=8.0.0
EOF

# 批量安装
pip install -r requirements.txt
```


## 配置验证


### 完整的安装验证脚本

创建 verify_installation.py 文件：


## 实例

运行验证：

```text
python verify_installation.py
```


### 性能基准测试

创建简单的性能测试：


## 实例


## 常见问题和解决方案


### 安装问题

问题 1：pip 安装超时

```text
pip install --user tensorflow
```

问题 2：权限错误

```text
# 创建新的虚拟环境
python -m venv fresh_env
source fresh_env/bin/activate  # Linux/Mac
# 或 fresh_env\Scripts\activate  # Windows
pip install tensorflow
```

问题 3：版本冲突

```text
# 创建新的虚拟环境
python -m venv fresh_env
source fresh_env/bin/activate  # Linux/Mac
# 或 fresh_env\Scripts\activate  # Windows
pip install tensorflow
```


### GPU 相关问题

问题 1：CUDA 版本不匹配

- 检查 TensorFlow 和 CUDA 版本兼容性
- 重新安装匹配的 CUDA 版本

问题 2：GPU 内存不足

```text
# 设置 GPU 内存增长
gpus = tf.config.experimental.list_physical_devices('GPU')
if gpus:
    for gpu in gpus:
        tf.config.experimental.set_memory_growth(gpu, True)
```

问题 3：无法找到 GPU

```text
# 检查 NVIDIA 驱动
nvidia-smi

# 检查 CUDA 安装
nvcc --version

# 重新安装 GPU 支持
pip uninstall tensorflow
pip install tensorflow
```


## 后续章节

- Jupyter 相关问题
- 开发环境优化
- GPU 内存管理
- 性能优化设置
- 开发工具配置
- 环境维护
- 定期更新
- 环境备份和迁移

## 复习重点

- 能说明 `TensorFlow 环境搭建` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

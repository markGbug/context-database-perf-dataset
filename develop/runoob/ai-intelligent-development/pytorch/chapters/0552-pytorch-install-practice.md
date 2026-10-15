# PyTorch：PyTorch 安装

- 来源：[PyTorch 安装](https://www.runoob.com/pytorch/pytorch-install.html)
- 分类：AI / 智能开发
- 技术：PyTorch
- 笔记类型：练习笔记
- 章节序号：0552

## 本章内容

PyTorch 是一个流行的深度学习框架，支持 CPU 和 GPU 计算。


### 支持的操作系统

- Windows：Windows 10 或更高版本（64位）
- macOS：macOS 10.15 (Catalina) 或更高版本
- Linux：主流发行版（Ubuntu 18.04+、CentOS 7+、RHEL 7+等）


### Python 版本要求

- 推荐版本：Python 3.8 - 3.11
- 最低要求：Python 3.7
- 注意：Python 3.12+ 支持可能有限，建议使用稳定版本


### 硬件要求

- CPU：支持 SSE4.2 指令集的 x86_64 处理器
- 内存：至少 4GB RAM（推荐 8GB+）
- 存储：至少 3GB 可用空间
- GPU（可选）：NVIDIA GPU with CUDA Compute Capability 3.5+


### CUDA 兼容性（GPU 版本）


## 安装前的准备工作


### 检查系统信息

Windows:

```text
# 检查 Windows 版本
winver

# 检查 Python 版本
python --version

# 检查是否有 NVIDIA GPU
nvidia-smi
```

macOS

```text
# 检查 macOS 版本
sw_vers

# 检查 Python 版本
python3 --version

# 检查是否有兼容的 GPU（Apple Silicon）
system_profiler SPDisplaysDataType
```

Linux

```text
# 检查发行版信息
cat /etc/os-release

# 检查 Python 版本
python3 --version

# 检查 NVIDIA GPU
nvidia-smi

# 检查 CUDA 版本（如果已安装）
nvcc --version
```


### Python 环境管理

使用 Anaconda/Miniconda:

```text
# 下载并安装 Miniconda
# Windows: https://repo.anaconda.com/miniconda/Miniconda3-latest-Windows-x86_64.exe
# macOS: https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.sh
# Linux: https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh

# 创建专用环境
conda create -n pytorch_env python=3.10
conda activate pytorch_env
```


### 使用 venv（Python 自带）

```text
# 创建虚拟环境
python -m venv pytorch_env

# 激活环境
# Windows
pytorch_env\Scripts\activate
# macOS/Linux
source pytorch_env/bin/activate
```


## 安装 PyTorch

PyTorch 官方提供了几种安装方法，可以通过 pip 或 conda 进行安装。


### CPU 版本安装

使用 pip 安装 pytorch：

```text
# 最新稳定版本
pip install torch torchvision torchaudio

# 指定版本
pip install torch==2.1.0 torchvision==0.16.0 torchaudio==2.1.0

# 仅 CPU 版本（更小的安装包）
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cpu
```

使用 conda 安装:

如果你使用 Anaconda 或 Miniconda 管理 Python 环境，使用 conda 安装 PyTorch 可能会更加简单和高效。

```text
# 从 conda-forge 安装
conda install pytorch torchvision torchaudio cpuonly -c pytorch

# 或从 conda-forge 渠道
conda install pytorch torchvision torchaudio -c conda-forge
```

如果不了解Anaconda，可以参考： Anaconda 教程


### 通过 PyTorch 官网安装

访问 PyTorch 的官方网站 https://pytorch.org/get-started/locally/，网站提供了一个方便的工具，可以根据你的系统配置（操作系统、包管理器、Python版本以及CUDA版本）推荐安装命令。


### 从源代码安装

如果你需要从源代码安装PyTorch，或者想要尝试最新的开发版本，你可以使用以下命令：

```text
git clone --recursive https://github.com/pytorch/pytorch
cd pytorch
python setup.py install
```

这将从 GitHub 克隆 PyTorch 的源代码，并使用 setup.py 进行安装。


### GPU 版本安装（CUDA）

安装 CUDA（如果需要）:

```text
# Ubuntu/Debian
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2004/x86_64/cuda-ubuntu2004.pin
sudo mv cuda-ubuntu2004.pin /etc/apt/preferences.d/cuda-repository-pin-600
wget https://developer.download.nvidia.com/compute/cuda/12.1.0/local_installers/cuda-repo-ubuntu2004-12-1-local_12.1.0-530.30.02-1_amd64.deb
sudo dpkg -i cuda-repo-ubuntu2004-12-1-local_12.1.0-530.30.02-1_amd64.deb
sudo cp /var/cuda-repo-ubuntu2004-12-1-local/cuda-*-keyring.gpg /usr/share/keyrings/
sudo apt-get update
sudo apt-get -y install cuda

# CentOS/RHEL
sudo yum install -y https://developer.download.nvidia.com/compute/cuda/repos/rhel8/x86_64/cuda-repo-rhel8-12.1.0-1.x86_64.rpm
sudo yum clean all
sudo yum -y install cuda
```

安装 PyTorch GPU 版本:

```text
# CUDA 12.1 版本
pip install torch torchvision torchaudio

# CUDA 11.8 版本
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118

# 使用 conda
conda install pytorch torchvision torchaudio pytorch-cuda=12.1 -c pytorch -c nvidia
```


### macOS 特殊说明

Apple Silicon (M1/M2) Mac:

```text
# 使用 Metal Performance Shaders (MPS) 后端
pip install torch torchvision torchaudio

# 验证 MPS 可用性
python -c "import torch; print(torch.backends.mps.is_available())"
```

Intel Mac:

```text
# 标准安装
pip install torch torchvision torchaudio
```


### 验证安装

为了确保 PyTorch 已正确安装，我们可以通过执行以下 PyTorch 代码来验证是否安装成功：


## 实例

如果 torch.cuda.is_available() 输出 True，则说明 PyTorch 成功识别到你的 GPU。

一个简单的实例，构建一个随机初始化的张量：


## 实例

如果安装成功，输出结果类似如下：

```text
tensor([[0.3380, 0.3845, 0.3217],
        [0.8337, 0.9050, 0.2650],
        [0.2979, 0.7141, 0.9069],
        [0.1449, 0.1132, 0.1375],
        [0.4675, 0.3947, 0.1426]])
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `PyTorch 安装` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

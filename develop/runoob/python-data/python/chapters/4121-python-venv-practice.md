# Python：Python 虚拟环境的创建（venv）

- 来源：[Python 虚拟环境的创建](https://www.runoob.com/python3/python-venv.html)
- 分类：Python / 数据科学
- 技术：Python
- 笔记类型：练习笔记
- 章节序号：4121

## 本章内容

虚拟环境是一个独立的 Python 运行空间，拥有自己的解释器、安装包和配置，与系统全局环境完全隔离。

Python 虚拟环境（Virtual Environment）是一个独立的 Python 运行环境，它允许你在同一台机器上为不同的项目创建隔离的 Python 环境。

不同项目可以在各自的虚拟环境中并行运行，互不干扰。

每个虚拟环境都有自己的：

- Python 解释器
- 安装的包/库
- 环境变量

虚拟环境让每个项目拥有独立的依赖空间，彻底消除版本冲突

### 为什么需要虚拟环境

- 项目隔离：不同项目可使用不同版本的 Python 和第三方库
- 避免污染：安装的包只影响当前环境，不污染全局 Python
- 依赖可控：通过 requirements.txt 精确记录和复现环境
- 安全测试：可以放心升级或试用新包，不影响其他项目

场景举例：

- 项目 A 需要 Django 3.2 版本
- 项目 B 需要 Django 4.0 版本
- 如果在系统全局安装，两个版本会冲突

### 虚拟环境工具

若需更老版本支持，可使用 virtualenv（Python 2兼容）：

```text
pip install virtualenv  # 非必须，venv 通常够用
```

本章节我们将使用 venv 创建和管理虚拟环境。

## 创建虚拟环境

Python 3.3+ 内置了 venv 模块，无需额外安装。

### 使用流程

## 使用流程总览

检查 Python 版本：

```text
python3 --version
# 或者
python --version
```

创建虚拟环境：

```text
# 基本语法
python3 -m venv 环境名称
```

例如，创建一个名为 .venv 的虚拟环境：

## 实例

参数说明：

- -m venv：使用 venv 模块
- .venv：虚拟环境的名称（可以自定义）

### 创建后的目录结构

```text
.venv/
├── bin/            # 在 Unix/Linux 系统上
│   ├── activate    # 激活脚本
│   ├── python      # 环境 Python 解释器
│   └── pip         # 环境的 pip
├── Scripts/        # 在 Windows 系统上
│   ├── activate    # 激活脚本
│   ├── python.exe  # 环境 Python 解释器
│   └── pip.exe     # 环境的 pip
└── Lib/            # 安装的第三方库
```

## 激活虚拟环境

激活后，当前终端的 python 和 pip 命令将自动指向该虚拟环境，所有安装操作均在隔离空间内进行。

```text
source .venv/bin/activate
```

```text
.venv\Scripts\activate
```

激活成功后，命令行提示符通常会显示环境名称：

```php
(.venv) $
```

验证激活是否生效：

```text
# 查看 Python 路径，应指向 .venv 目录
which python       # macOS/Linux
where python       # Windows
→ /path/to/my_project/.venv/bin/python
```

## 使用虚拟环境

### 安装包

在激活的环境中，使用 pip 安装的包只会影响当前环境：

```text
pip install package_name
```

例如：

```text
# 安装单个包（如Django）
(.venv) pip install django==3.2.12

# 安装多个包
(.venv) pip install requests pandas

# 安装速度慢？使用国内镜像
(.venv)  pip install django -i https://pypi.tuna.tsinghua.edu.cn/simple
```

### 查看已安装的包

```text
(.venv) pip list
Package    Version
---------- -------
Django     3.2.12
pip        21.2.4

# 查看某个包的详情
(.venv) pip show django

# 升级包
(.venv) pip install --upgrade pip
```

### 导出依赖

使用 requirements.txt 记录和复现项目环境，是团队协作的标准做法：

```text
(.venv) pip freeze > requirements.txt
```

requirements.txt 文件内容示例：

```text
Django==3.2.12
requests==2.26.0
pandas==1.3.3
```

### 从文件安装依赖

```text
(.venv) pip install -r requirements.txt
```

提示：将 .venv/ 加入 .gitignore，只提交 requirements.txt。虚拟环境体积大且路径绑定，不应纳入版本控制。

## 退出虚拟环境

当完成工作后，可以退出虚拟环境：

```text
deactivate
```

退出后，命令行提示符会恢复正常，Python 和 pip 命令将使用系统全局版本。

## 删除虚拟环境

要删除虚拟环境，只需删除对应的目录即可：

```text
# 确保已退出环境
deactivate
```

### 删除虚拟环境

虚拟环境本质上是一个普通目录，删除目录即彻底移除：

```text
rm -rf .venv
```

```text
rmdir /s /q .venv
```

## 实际项目示例

假设开发一个 Django 项目：

## 实例

## 高级用法

### 指定 Python 版本

如果你安装了多个 Python 版本，可以指定使用哪个版本来创建虚拟环境：

```text
python3.8 -m venv .venv  # 使用 Python 3.8
```

### 创建不带 pip 的环境

```text
python -m venv --without-pip .venv
```

### 创建继承系统包的虚拟环境

```text
python -m venv --system-site-packages .venv
```

## 常见问题解答

### 1. 为什么我的虚拟环境没有 activate 脚本？

确保你使用的是正确的路径：

- Windows: Scripts\activate
- Unix/Linux: bin/activate

### 2. 如何知道当前是否在虚拟环境中？

检查命令行提示符是否有环境名称前缀，或运行：

```text
which python
```

### 3.安装包速度慢

使用国内镜像源：

```text
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple package_name
```

查看 Python 解释器的路径是否在虚拟环境目录中。

### 4. 虚拟环境可以移动位置吗？

不建议。虚拟环境内的脚本和配置文件中硬编码了绝对路径，移动后会失效。如需迁移，最简单的方式是重新创建环境并通过 requirements.txt 恢复依赖。

### 5. 虚拟环境会占用多少空间？

空环境约 20–50 MB，随安装的包增多而增加。数据科学项目（NumPy、Pandas、PyTorch）可能达到数 GB。定期清理不再使用的虚拟环境是个好习惯。

## 最佳实践

- 每个项目独立一个环境：避免不同项目的依赖相互影响
- 统一命名为 .venv：大多数 IDE（VS Code、PyCharm）可自动识别
- 及时更新 requirements.txt：每次 pip install 后同步导出
- 版本控制中忽略虚拟环境：在 .gitignore 中添加 .venv/
- 定期清理废弃环境：释放磁盘空间
- 生产环境固定版本号：requirements.txt 中明确写 == 版本，避免意外升级

```text
# .gitignore 推荐配置
.venv/
__pycache__/
*.pyc
.env
*.egg-info/
```

## 动手验证

- 复现 `Python 虚拟环境的创建` 中的关键示例或命令。
- 修改一个输入、参数或条件，观察结果变化。
- 记录报错信息、定位过程和修复方式。

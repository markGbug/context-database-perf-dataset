# Skills（技能）：Skills 依赖管理

- 来源：[Skills 依赖管理](https://www.runoob.com/skills/skills-dependencies.html)
- 分类：AI / 智能开发
- 技术：Skills（技能）
- 笔记类型：练习笔记
- 章节序号：0636

## 本章内容

Skill 脚本通常需要第三方库，如何声明、安装和锁定这些依赖，是保证 Skill 可靠运行的基础。


## 依赖声明文件

在 Skill 的 scripts/ 目录下创建 requirements.txt（Python）或 package.json（Node.js），集中声明所有依赖。


### Python 依赖：requirements.txt

```text
# 文件路径：scripts/requirements.txt
# 格式：包名==版本号（锁定版本，确保可重复安装）

pandas==2.1.4         # 数据处理
openpyxl==3.1.2       # Excel 读写
pypdf==3.17.0         # PDF 处理
python-docx==1.1.0    # Word 文档处理
requests==2.31.0      # HTTP 请求
```


### Node.js 依赖：package.json


## 实例


## 在 SKILL.md 中说明安装方式

```text
## 依赖安装

首次使用前，运行以下命令安装 Python 依赖：

```bash
pip install -r scripts/requirements.txt --break-system-packages
```

若运行环境已预装依赖，可跳过此步骤。
```


## 在脚本中自动安装依赖

对于需要零配置运行的 Skill，可以在脚本开头加入依赖自检和自动安装逻辑。


## 实例

```text
正在安装：python-docx...
安装成功：python-docx
所有依赖已就绪，开始执行...
```


## 版本冲突的处理策略

当 Skill 依赖的包版本与系统已有版本冲突时，有以下几种处理方式：


### 创建虚拟环境（可选）


## 实例

在 Claude 的执行环境中，通常不需要虚拟环境，因为每次会话都是相对隔离的。虚拟环境主要用于本地开发阶段，避免与开发机器上的其他项目产生冲突。


## 依赖文档规范

在 SKILL.md 或单独的 README 中，应清晰列出所有外部依赖，便于用户在安装前了解要求。

```text
## 系统要求

### 运行环境
- Python 3.8 或更高版本
- pip（Python 包管理工具）

### Python 依赖
| 包名 | 版本 | 用途 |
|------|------|------|
| pandas | >=2.0 | 数据读取与处理 |
| openpyxl | >=3.0 | Excel 文件读写 |
| python-docx | 任意 | Word 文档生成 |

### 系统工具（可选）
- pandoc：格式转换（apt-get install pandoc）
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Skills 依赖管理` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

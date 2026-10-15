# AI Agent（智能体）：Python 智能体环境配置

- 来源：[Python 智能体环境配置](https://www.runoob.com/ai-agent/ai-agent-python-setup.html)
- 分类：AI / 智能开发
- 技术：AI Agent（智能体）
- 笔记类型：概念卡
- 章节序号：0038

## 本章内容

在开始构建 AI Agent 之前，我们需要搭建合适的开发环境。

Python 是 AI 和机器学习领域最流行的语言，拥有丰富的库和工具支持。


### 1. Python 版本选择

对于 AI Agent 开发，我们推荐使用 Python 3.9 或更高版本。

以下版本是常见选择：

- Python 3.9：稳定性好，兼容性最佳
- Python 3.10：性能改进，新特性
- Python 3.11+：最新版本，性能最佳

注意：某些库可能对 Python 版本有特定要求，建议查看官方文档。


### 2. 安装 Python

- 访问 Python 官网
- 下载最新版本的 Python 安装程序（3.9 或更高版本）
- 运行安装程序，务必勾选 Add Python to PATH
- 完成安装后，打开命令提示符（CMD）或 PowerShell，输入： python --version，应显示 Python 版本号。

macOS 通常预装了 Python，但可能是旧版本。推荐使用 Homebrew 安装：

```text
# 安装 Homebrew（如果尚未安装）
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# 安装 Python
brew install python@3.9

# 验证安装
python3 --version
```

大多数 Linux 发行版已预装 Python。如需要特定版本：

```text
# Ubuntu/Debian
sudo apt update
sudo apt install python3.9 python3-pip

# CentOS/RHEL
sudo yum install python39 python39-pip

# 验证安装
python3 --version
```


### 3. 虚拟环境配置

使用虚拟环境可以隔离不同项目的依赖，避免版本冲突。

```text
# 创建项目目录
mkdir ai-agent-project
cd ai-agent-project
```

使用 uv 创建并激活虚拟环境，更多相关内容可以阅读 uv 教程。

安装 uv

```text
pip install uv
```

使用 uv 命令创建：

```text
# 创建名为 .venv 的虚拟环境（默认）
uv venv

# 激活环境（macOS/Linux）
source .venv/bin/activate

# 激活环境（Windows）
.venv\Scripts\activate
```

其他工具：

```text
# 使用 venv，Python 3.3+ 内置
python -m venv venv

# 或使用 conda（如果已安装 Anaconda/Miniconda）
conda create -n ai-agent python=3.9
conda activate ai-agent
```

Windows：

```text
venv\Scripts\activate
```

macOS/Linux：

```text
source venv/bin/activate
```

激活后，命令行提示符通常会显示虚拟环境名称（如 (venv)）。

```text
deactivate
```


### 4. 包管理工具 pip

pip 是 Python 的包管理工具，用于安装第三方库。

常用命令：

```text
# 升级 pip 到最新版本
pip install --upgrade pip

# 安装包
pip install package_name

# 安装特定版本
pip install package_name==1.2.3

# 从 requirements.txt 安装所有依赖
pip install -r requirements.txt

# 列出已安装的包
pip list

# 生成 requirements.txt
pip freeze > requirements.txt
```


### 5. 开发目录结构建议

一个良好的项目结构有助于代码管理和维护：

```text
ai-agent-project/
├── .env                    # 环境变量文件（不提交到Git）
├── .gitignore             # Git忽略文件
├── requirements.txt       # 项目依赖
├── README.md             # 项目说明
├── src/                  # 源代码目录
│   ├── __init__.py
│   ├── agents/          # Agent相关代码
│   │   ├── __init__.py
│   │   ├── base_agent.py
│   │   └── weather_agent.py
│   ├── tools/           # 工具定义
│   │   ├── __init__.py
│   │   ├── calculator.py
│   │   └── web_search.py
│   ├── memory/          # 记忆系统
│   │   ├── __init__.py
│   │   ├── short_term.py
│   │   └── vector_memory.py
│   └── utils/           # 工具函数
│       ├── __init__.py
│       ├── config.py
│       └── logger.py
├── tests/               # 测试代码
│   ├── __init__.py
│   ├── test_agents.py
│   └── test_tools.py
├── examples/            # 示例代码
│   ├── basic_agent.py
│   └── multi_tool_agent.py
└── notebooks/           # Jupyter笔记本
    └── experiments.ipynb
```


## 必备库安装

AI Agent 开发需要一系列第三方库的支持。以下是核心库的安装方法和简要介绍。


### 核心库安装

创建 requirements.txt 文件，包含以下内容：

```text
# 基础库
python-dotenv>=1.0.0      # 环境变量管理
pydantic>=2.0.0           # 数据验证和设置管理
loguru>=0.7.0             # 日志记录

# AI/ML 相关
openai>=1.0.0             # OpenAI API
anthropic>=0.7.0          # Claude API
google-generativeai>=0.3.0 # Gemini API
sentence-transformers>=2.2.0 # Embedding 模型
chromadb>=0.4.0           # 向量数据库

# Agent 框架
langchain>=0.1.0          # LangChain 框架
langchain-community>=0.0.10 # LangChain 社区工具
langchain-openai>=0.0.5   # LangChain OpenAI 集成
llama-index>=0.10.0       # LlamaIndex（可选）
semantic-kernel>=0.9.0    # Semantic Kernel（可选）

# 工具和工具
requests>=2.31.0          # HTTP 请求
beautifulsoup4>=4.12.0    # HTML 解析
pandas>=2.0.0             # 数据处理
numpy>=1.24.0             # 数值计算

# 开发工具
pytest>=7.4.0             # 测试框架
black>=23.0.0             # 代码格式化
flake8>=6.0.0             # 代码检查
jupyter>=1.0.0            # Jupyter 笔记本
```

安装所有依赖：

```text
pip install -r requirements.txt
```


### 主要库介绍

LangChain 是最流行的 AI Agent 开发框架，提供了构建链式（Chain）和代理（Agent）应用的工具。

```text
# LangChain 基本使用示例
from langchain.llms import OpenAI
from langchain.chat_models import ChatOpenAI
from langchain.agents import initialize_agent, AgentType
from langchain.tools import Tool

# 初始化 LLM
llm = ChatOpenAI(temperature=0.7, model="gpt-3.5-turbo")

# 创建工具
tools = [
    Tool(
        name="计算器",
        func=lambda x: str(eval(x)),
        description="用于数学计算"
    )
]

# 创建 Agent
agent = initialize_agent(
    tools=tools,
    llm=llm,
    agent=AgentType.ZERO_SHOT_REACT_DESCRIPTION,
    verbose=True
)

# 运行 Agent
result = agent.run("计算 25 的平方根")
print(result)
```

LlamaIndex（原 GPT Index）专注于文档索引和检索，适合构建基于文档的问答系统。

```text
# LlamaIndex 基本使用示例
from llama_index import VectorStoreIndex, SimpleDirectoryReader
from llama_index.llms import OpenAI

# 加载文档
documents = SimpleDirectoryReader("./data").load_data()

# 创建索引
index = VectorStoreIndex.from_documents(documents)

# 创建查询引擎
query_engine = index.as_query_engine()

# 查询
response = query_engine.query("文档中提到了哪些AI技术？")
print(response)
```

Semantic Kernel 是微软推出的框架，强调可扩展性和企业级应用。

```text
# Semantic Kernel 基本使用示例
import semantic_kernel as sk
from semantic_kernel.connectors.ai.open_ai import OpenAITextCompletion

# 初始化内核
kernel = sk.Kernel()
api_key = "your-openai-api-key"
kernel.add_text_completion_service(
    "dv",
    OpenAITextCompletion("text-davinci-003", api_key)
)

# 定义技能
skill = kernel.import_semantic_skill_from_directory("./skills", "ExampleSkill")

# 运行技能
context = kernel.create_new_context()
context["input"] = "介绍一下人工智能"
result = skill["Summarize"](context)
print(result)
```


### 安装验证

创建一个验证脚本 verify_installation.py：


## 实例

运行验证：

```text
python verify_installation.py
```


### 常见安装问题解决

```text
# 使用国内镜像源
pip install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple

# 或使用阿里云镜像
pip install -r requirements.txt -i https://mirrors.aliyun.com/pypi/simple/
```

```text
# 创建新的虚拟环境
python -m venv new_venv
source new_venv/bin/activate  # 或 venv\Scripts\activate

# 重新安装，让 pip 自动解决依赖
pip install --upgrade pip
pip install langchain openai
```

```text
# 对于 Apple Silicon (M1/M2/M3)，可能需要特定版本
pip install grpcio==1.48.2  # 解决某些兼容性问题

# 或使用 conda
conda install -c conda-forge grpcio
```


## API Key 管理

AI Agent 开发需要访问各种 API 服务（如 OpenAI、Anthropic、DeepSeek 等），安全、有效地管理 API Key 至关重要。


### 1. 为什么需要安全管理 API Key？

- 防止泄露：API Key 泄露可能导致经济损失
- 访问控制：不同环境使用不同的 Key
- 方便配置：团队协作时统一配置方式
- 环境隔离：开发、测试、生产环境使用不同的 Key


### 2. 环境变量管理（推荐）

使用 .env 文件管理敏感信息，不提交到版本控制系统。

```text
# API Keys
OPENAI_API_KEY=sk-你的OpenAI密钥
ANTHROPIC_API_KEY=你的Claude密钥
GOOGLE_API_KEY=你的Gemini密钥
SERPAPI_API_KEY=你的搜索API密钥

# 应用配置
APP_ENV=development
LOG_LEVEL=INFO
DEBUG=true

# 数据库配置（如使用）
VECTOR_DB_PATH=./data/vector_db
MAX_MEMORY_ITEMS=1000
```

确保 .env 文件不被提交到 Git：

```text
# Python
__pycache__/
*.py[cod]
*$py.class
*.so
.Python
env/
venv/
ENV/
env.bak/
venv.bak/

# 环境变量
.env
.env.local
.env.*.local

# 数据文件
data/
*.db
*.sqlite
*.sqlite3

# 日志
logs/
*.log

# 编辑器
.vscode/
.idea/
*.swp
*.swo
```


## 实例


### 3. 安全使用 API Key

```text
import os
from openai import OpenAI

# 从环境变量读取 API Key
api_key = os.getenv("OPENAI_API_KEY")

if not api_key:
    raise ValueError("OPENAI_API_KEY 环境变量未设置")

# 初始化 OpenAI 客户端
client = OpenAI(api_key=api_key)

# 使用客户端
response = client.chat.completions.create(
    model="gpt-3.5-turbo",
    messages=[{"role": "user", "content": "你好"}]
)
```


## 实例


### 4. 多环境配置

对于大型项目，可能需要不同的环境配置：

```text
# .env.development (开发环境)
OPENAI_API_KEY=sk-dev-key
APP_ENV=development
DEBUG=true

# .env.production (生产环境)
OPENAI_API_KEY=sk-prod-key
APP_ENV=production
DEBUG=false
```

```text
# config_manager.py
import os
from pathlib import Path
from dotenv import load_dotenv

class ConfigManager:
    """配置管理器"""

    def __init__(self, env=None):
        self.env = env or os.getenv("APP_ENV", "development")
        self.load_config()

    def load_config(self):
        """加载配置"""
        # 先加载通用配置
        load_dotenv(dotenv_path=Path('.') / '.env')

        # 加载环境特定配置
        env_file = Path('.') / f'.env.{self.env}'
        if env_file.exists():
            load_dotenv(dotenv_path=env_file, override=True)

        # 加载本地覆盖配置（不提交到Git）
        local_file = Path('.') / f'.env.{self.env}.local'
        if local_file.exists():
            load_dotenv(dotenv_path=local_file, override=True)

    def get(self, key, default=None):
        """获取配置值"""
        return os.getenv(key, default)

# 使用示例
config = ConfigManager(env="development")
print(f"当前环境: {config.get('APP_ENV')}")
print(f"API Key: {config.get('OPENAI_API_KEY')[:10]}...")  # 只显示前10个字符
```


### 5. 密钥轮换和监控

对于生产环境，建议实施密钥轮换和监控：

```text
# key_manager.py
import os
import time
from datetime import datetime, timedelta

class APIKeyManager:
    """API Key 管理器"""

    def __init__(self):
        self.keys = {}
        self.key_history = []
        self.load_keys()

    def load_keys(self):
        """加载 API Keys"""
        # 可以从环境变量、数据库或密钥管理服务加载
        self.keys = {
            "openai": {
                "current": os.getenv("OPENAI_API_KEY"),
                "previous": os.getenv("OPENAI_API_KEY_PREVIOUS"),
                "created_at": datetime.now(),
                "rotation_days": 30  # 30天轮换一次
            },
            "anthropic": {
                "current": os.getenv("ANTHROPIC_API_KEY"),
                "previous": None,
                "created_at": datetime.now(),
                "rotation_days": 30
            }
        }

    def get_key(self, service):
        """获取当前可用的 Key"""
        key_info = self.keys.get(service)
        if not key_info:
            raise ValueError(f"未配置服务 {service} 的 API Key")

        # 检查是否需要轮换
        if self.should_rotate(key_info):
            self.rotate_key(service)

        return key_info["current"]

    def should_rotate(self, key_info):
        """检查是否需要轮换 Key"""
        rotation_days = key_info.get("rotation_days", 30)
        created_at = key_info.get("created_at", datetime.now())

        age = datetime.now() - created_at
        return age.days >= rotation_days

    def rotate_key(self, service):
        """轮换 API Key"""
        # 在实际应用中，这里会从密钥管理服务获取新 Key
        print(f"轮换 {service} 的 API Key...")

        key_info = self.keys[service]
        key_info["previous"] = key_info["current"]
        # 这里应该从安全的地方获取新 Key
        # key_info["current"] = get_new_key_from_vault(service)
        key_info["created_at"] = datetime.now()

        # 记录历史
        self.key_history.append({
            "service": service,
            "rotated_at": datetime.now(),
            "old_key": key_info["previous"][:10] + "..." if key_info["previous"] else None
        })

# 使用示例
key_manager = APIKeyManager()
openai_key = key_manager.get_key("openai")
print(f"OpenAI Key: {openai_key[:10]}...")
```


## 开发工具推荐

选择合适的开发工具可以大幅提高开发效率。以下是一些推荐的开发工具。


### 1. 代码编辑器/IDE

下载地址：https://code.visualstudio.com/

推荐扩展：

- Python：Python 语言支持
- Pylance：高级 Python 语言服务器
- Jupyter：Jupyter 笔记本支持
- GitLens：Git 增强功能
- Prettier：代码格式化
- Code Spell Checker：拼写检查
- Rainbow CSV：CSV 文件高亮
- Thunder Client：API 测试工具

VS Code 配置（.vscode/settings.json）：

```text
{
    "python.defaultInterpreterPath": "${workspaceFolder}/venv/bin/python",
    "python.terminal.activateEnvironment": true,
    "python.linting.enabled": true,
    "python.linting.pylintEnabled": false,
    "python.linting.flake8Enabled": true,
    "python.formatting.provider": "black",
    "python.formatting.blackArgs": [
        "--line-length",
        "88"
    ],
    "python.testing.pytestEnabled": true,
    "[python]": {
        "editor.formatOnSave": true,
        "editor.codeActionsOnSave": {
            "source.organizeImports": "always"
        }
    },
    "files.exclude": {
        "**/__pycache__": true,
        "**/.pytest_cache": true,
        "**/.venv": true,
        "**/venv": true
    }
}
```

下载地址：https://www.jetbrains.com/pycharm/

特点：

- 专业的 Python IDE
- 强大的调试功能
- 数据库工具集成
- 科学计算支持


### 2. 版本控制：Git

Git 是必不可少的版本控制工具。

基础配置：

```text
# 配置用户信息
git config --global user.name "你的姓名"
git config --global user.email "你的邮箱"

# 配置默认编辑器（可选）
git config --global core.editor "code --wait"

# 创建 Git 仓库
cd ai-agent-project
git init

# 添加所有文件
git add .

# 提交
git commit -m "初始提交：AI Agent 项目"

# 连接到远程仓库（如 GitHub）
git remote add origin https://github.com/你的用户名/ai-agent-project.git
git branch -M main
git push -u origin main
```


### 3. 调试工具

```text
# 在代码中插入断点
import pdb

def complex_function(x):
    pdb.set_trace()  # 这里会进入调试器
    result = x * 2
    return result

# 常用 pdb 命令：
# n(ext) - 执行下一行
# s(tep) - 进入函数
# c(ontinue) - 继续执行
# l(ist) - 显示代码
# p(rint) - 打印变量值
# q(uit) - 退出调试器
```

.vscode/launch.json：

```text
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Python: 当前文件",
            "type": "python",
            "request": "launch",
            "program": "${file}",
            "console": "integratedTerminal",
            "justMyCode": true,
            "envFile": "${workspaceFolder}/.env"
        },
        {
            "name": "Python: 测试",
            "type": "python",
            "request": "launch",
            "program": "${workspaceFolder}/tests",
            "console": "integratedTerminal",
            "justMyCode": true,
            "envFile": "${workspaceFolder}/.env"
        }
    ]
}
```


### 4. 测试工具

```text
# tests/test_agent.py
import pytest
from src.agents.base_agent import BaseAgent

def test_agent_initialization():
    """测试 Agent 初始化"""
    agent = BaseAgent(name="测试Agent")
    assert agent.name == "测试Agent"
    assert agent.messages == []

def test_agent_add_message():
    """测试添加消息"""
    agent = BaseAgent()
    agent.add_message("user", "你好")

    assert len(agent.messages) == 1
    assert agent.messages[0]["role"] == "user"
    assert agent.messages[0]["content"] == "你好"
```

运行测试：

```text
# 运行所有测试
pytest

# 运行特定测试文件
pytest tests/test_agent.py

# 运行特定测试函数
pytest tests/test_agent.py::test_agent_initialization

# 显示详细输出
pytest -v

# 显示覆盖率报告
pytest --cov=src
```


## 后续章节

- 5. 代码质量和格式化
- 6. 文档工具
- 7. 容器化工具（可选）
- 8. 监控和日志

## 记忆卡片

- 一句话定义：`Python 智能体环境配置` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。

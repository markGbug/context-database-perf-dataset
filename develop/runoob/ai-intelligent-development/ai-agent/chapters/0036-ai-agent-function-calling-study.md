# AI Agent（智能体）：工具调用（Function Calling）

- 来源：[工具调用](https://www.runoob.com/ai-agent/ai-agent-function-calling.html)
- 分类：AI / 智能开发
- 技术：AI Agent（智能体）
- 笔记类型：学习笔记
- 章节序号：0036

## 本章内容

Function Calling（函数调用）是让 LLM 能够使用外部工具的核心机制。

Function Calling（函数调用）允许模型决定何时调用工具、调用哪个工具，以及传递什么参数。


### 为什么需要 Function Calling？

想象一下，LLM 是一个聪明但手无寸铁的顾问。它知道很多知识，但不能：

- 获取实时信息（如最新天气、股票价格）
- 执行计算（如复杂的数学运算）
- 操作外部系统（如发送邮件、读写文件）

Function Calling 为 LLM 提供了双手，让它能够突破自身限制，执行实际任务。


### Function Calling 的工作原理

Function Calling 的基本流程如下：


### 核心概念

- 工具定义：描述一个工具的功能、参数和返回值
- 工具选择：LLM 根据用户问题选择合适的工具
- 参数提取：LLM 从问题中提取工具所需的参数
- 结果处理：将工具执行结果整合到最终回答中


### 实例说明

假设我们有一个查询天气的工具，当用户问北京今天天气如何？时：

- LLM 识别出需要调用天气查询工具
- 从问题中提取参数：city="北京", date="今天"
- 调用天气 API 获取数据
- 将天气数据整合成友好的回答返回给用户


## 工具定义与描述编写

要让 LLM 正确使用工具，首先需要清晰地定义工具，好的工具定义应该像一份清晰的说明书，让 LLM 明白：

- 这个工具是做什么的？
- 什么时候使用它？
- 需要什么参数？
- 参数是什么格式？


### 工具定义的结构

一个完整的工具定义通常包含以下部分：


## 实例


### 编写优质的工具描述

- 不好的描述：查询天气
- 好的描述：获取指定城市在特定日期的天气信息，包括温度、湿度、风速和天气状况（晴、雨、多云等）

不好的参数描述：

```text
"city": {"type": "string"}
```

好的参数描述：

```text
"city": {
    "type": "string",
    "description": "完整的城市名称，如'北京市'、'上海市'。不要使用简称或拼音。"
}
```

对于有限的选项，使用枚举（enum）帮助 LLM 理解：

```text
"unit": {
    "type": "string",
    "description": "温度单位",
    "enum": ["celsius", "fahrenheit"],
    "default": "celsius"
}
```

在描述中提供示例，帮助 LLM 理解格式：

```text
"date": {
    "type": "string",
    "description": "日期，格式应为'YYYY-MM-DD'，例如'2024-06-15'"
}
```


### 实用工具定义示例

```text
calculator_tool = {
    "name": "calculate",
    "description": "执行数学计算，支持加减乘除、幂运算等基本运算",
    "parameters": {
        "type": "object",
        "properties": {
            "expression": {
                "type": "string",
                "description": "数学表达式，如'2 + 3 * 4'、'sqrt(16)'、'sin(30)'"
            }
        },
        "required": ["expression"]
    }
}
```

```text
search_tool = {
    "name": "search_web",
    "description": "在互联网上搜索最新信息",
    "parameters": {
        "type": "object",
        "properties": {
            "query": {
                "type": "string",
                "description": "搜索关键词，尽量具体明确"
            },
            "num_results": {
                "type": "integer",
                "description": "返回结果数量，默认为5",
                "default": 5,
                "minimum": 1,
                "maximum": 10
            }
        },
        "required": ["query"]
    }
}
```

```text
file_tool = {
    "name": "read_file",
    "description": "读取指定文件的内容",
    "parameters": {
        "type": "object",
        "properties": {
            "file_path": {
                "type": "string",
                "description": "文件的完整路径，如'/home/user/document.txt'"
            },
            "encoding": {
                "type": "string",
                "description": "文件编码，默认为'utf-8'",
                "default": "utf-8"
            }
        },
        "required": ["file_path"]
    }
}
```


### 工具定义的最佳实践

- 名称简洁明确：使用动词开头，如 get_、calculate_、search_
- 描述完整详细：说明工具的用途、适用场景和限制
- 参数验证充分：定义参数类型、范围、格式要求
- 提供默认值：为可选参数提供合理的默认值
- 考虑错误情况：在描述中说明可能出现的错误和限制


### 工具定义的验证

定义工具后，应该进行验证测试：

```text
def validate_tool_definition(tool_def):
    """验证工具定义是否完整"""
    required_fields = ["name", "description", "parameters"]

    for field in required_fields:
        if field not in tool_def:
            return False, f"缺少必要字段: {field}"

    # 检查参数结构
    if "properties" not in tool_def["parameters"]:
        return False, "参数定义缺少properties字段"

    return True, "工具定义完整"

# 测试验证
is_valid, message = validate_tool_definition(weather_tool)
print(f"验证结果: {is_valid}, 消息: {message}")
```


## 参数提取与验证

LLM 从用户问题中提取参数后，需要对这些参数进行验证和处理，确保工具能够正确执行。


### 参数提取过程

当 LLM 决定调用工具时，它会分析用户输入，提取出工具所需的参数：

```text
用户输入: "查询北京明天的天气温度"
工具: get_weather
提取参数: {"city": "北京", "date": "明天"}
```


### 参数提取的挑战

参数提取可能遇到以下问题：

- 信息缺失：用户没有提供所有必要信息
- 格式不符：用户提供的格式与工具要求不符
- 歧义解析：同一信息可能有多种解释
- 上下文依赖：参数需要结合对话历史理解


### 参数验证方法

确保参数类型符合要求：

```text
def validate_parameters(params, tool_def):
    """验证参数类型"""
    errors = []

    for param_name, param_def in tool_def["parameters"]["properties"].items():
        if param_name in params:
            param_value = params[param_name]
            expected_type = param_def.get("type")

            # 类型检查
            if expected_type == "string" and not isinstance(param_value, str):
                errors.append(f"参数'{param_name}'应为字符串类型")
            elif expected_type == "integer" and not isinstance(param_value, int):
                errors.append(f"参数'{param_name}'应为整数类型")
            elif expected_type == "number" and not isinstance(param_value, (int, float)):
                errors.append(f"参数'{param_name}'应为数字类型")
            elif expected_type == "boolean" and not isinstance(param_value, bool):
                errors.append(f"参数'{param_name}'应为布尔类型")

    return errors
```

检查参数值是否在允许范围内：

```text
def validate_range(params, tool_def):
    """验证参数范围"""
    errors = []

    for param_name, param_def in tool_def["parameters"]["properties"].items():
        if param_name in params:
            param_value = params[param_name]

            # 检查最小值
            if "minimum" in param_def and param_value < param_def["minimum"]:
                errors.append(f"参数'{param_name}'不能小于{param_def['minimum']}")

            # 检查最大值
            if "maximum" in param_def and param_value > param_def["maximum"]:
                errors.append(f"参数'{param_name}'不能大于{param_def['maximum']}")

            # 检查枚举值
            if "enum" in param_def and param_value not in param_def["enum"]:
                errors.append(f"参数'{param_name}'必须是{param_def['enum']}中的一个")

    return errors
```

确保所有必填参数都已提供：

```text
def validate_required(params, tool_def):
    """验证必填参数"""
    errors = []
    required_params = tool_def["parameters"].get("required", [])

    for param_name in required_params:
        if param_name not in params:
            errors.append(f"缺少必填参数: {param_name}")

    return errors
```


### 完整的参数验证系统


## 实例


### 参数提取与验证的完整流程


### 参数修正策略

当参数验证失败时，可以采取以下策略：

- 询问用户：直接向用户询问缺失或错误的参数
- 使用默认值：对于可选参数，使用预定义的默认值
- 智能推断：根据上下文推断合理的参数值
- 格式转换：将用户提供的格式转换为工具要求的格式

```text
def fix_parameters(params, errors, tool_def):
    """尝试修正参数错误"""
    fixed_params = params.copy()

    for error in errors:
        if "缺少必填参数" in error:
            param_name = error.split(": ")[1]
            # 尝试从上下文推断或使用默认值
            if param_name == "date":
                fixed_params[param_name] = "今天"  # 使用当天作为默认值

        elif "应为字符串类型" in error:
            param_name = error.split("'")[1]
            # 尝试转换为字符串
            fixed_params[param_name] = str(params[param_name])

    return fixed_params
```


## 错误处理与重试机制

在实际应用中，工具调用可能会失败。健全的错误处理和重试机制是构建可靠 AI Agent 的关键。


### <常见的工具调用错误

- 网络错误：API 调用超时、连接失败
- 参数错误：参数验证失败、格式不正确
- 权限错误：API 密钥无效、权限不足
- 资源错误：服务不可用、达到调用限制
- 逻辑错误：工具内部逻辑错误


### 错误处理策略

根据错误类型采取不同的处理策略：

```text
class ErrorHandler:
    """错误处理器"""

    def handle(self, error, context):
        """处理错误"""
        error_type = self.classify_error(error)

        if error_type == "network":
            return self.handle_network_error(error, context)
        elif error_type == "parameter":
            return self.handle_parameter_error(error, context)
        elif error_type == "authentication":
            return self.handle_auth_error(error, context)
        elif error_type == "resource":
            return self.handle_resource_error(error, context)
        else:
            return self.handle_unknown_error(error, context)

    def classify_error(self, error):
        """分类错误类型"""
        error_str = str(error).lower()

        if any(word in error_str for word in ["timeout", "connection", "network"]):
            return "network"
        elif any(word in error_str for word in ["parameter", "invalid", "missing"]):
            return "parameter"
        elif any(word in error_str for word in ["auth", "key", "permission"]):
            return "authentication"
        elif any(word in error_str for word in ["limit", "quota", "unavailable"]):
            return "resource"
        else:
            return "unknown"

    def handle_network_error(self, error, context):
        """处理网络错误"""
        return {
            "success": False,
            "error": "网络连接失败，请检查网络后重试",
            "retryable": True,
            "retry_after": 5  # 5秒后重试
        }

    def handle_parameter_error(self, error, context):
        """处理参数错误"""
        return {
            "success": False,
            "error": f"参数错误: {str(error)}",
            "retryable": False,
            "suggestion": "请检查输入参数是否正确"
        }

    # 其他错误处理方法类似...
```

将技术性错误转换为用户能理解的消息：

```text
def user_friendly_error(error):
    """生成用户友好的错误消息"""
    error_map = {
        "timeout": "请求超时，请稍后重试",
        "connection_error": "网络连接失败，请检查网络",
        "invalid_api_key": "API 密钥无效，请检查配置",
        "rate_limit_exceeded": "调用频率过高，请稍后再试",
        "invalid_parameters": "输入参数不正确，请检查后重试"
    }

    error_str = str(error).lower()
    for key, message in error_map.items():
        if key in error_str:
            return message

    return "系统繁忙，请稍后重试"
```


### 重试机制

对于可重试的错误，应该实现智能的重试策略：

```text
import time
import random

class ExponentialBackoffRetry:
    """指数退避重试"""

    def __init__(self, max_retries=3, base_delay=1, max_delay=30):
        self.max_retries = max_retries
        self.base_delay = base_delay
        self.max_delay = max_delay

    def retry(self, func, *args, **kwargs):
        """执行带重试的函数调用"""
        last_error = None

        for attempt in range(self.max_retries):
            try:
                return func(*args, **kwargs)

            except Exception as e:
                last_error = e

                # 检查是否可重试
                if not self.is_retryable(e):
                    raise

                # 最后一次尝试，不再重试
                if attempt == self.max_retries - 1:
                    break

                # 计算等待时间（指数退避 + 随机抖动）
                delay = min(
                    self.base_delay * (2 ** attempt) + random.uniform(0, 1),
                    self.max_delay
                )

                print(f"第{attempt + 1}次尝试失败，{delay:.1f}秒后重试...")
                time.sleep(delay)

        # 所有重试都失败
        raise last_error

    def is_retryable(self, error):
        """判断错误是否可重试"""
        error_str = str(error).lower()
        retryable_errors = ["timeout", "connection", "busy", "temporarily"]

        for retryable_error in retryable_errors:
            if retryable_error in error_str:
                return True

        return False

# 使用示例
retry = ExponentialBackoffRetry(max_retries=3)

def call_weather_api(city, date):
    """调用天气API（模拟可能失败）"""
    # 模拟API调用
    if random.random() < 0.3:  # 30%概率失败
        raise ConnectionError("API连接超时")
    return {"temperature": 25, "condition": "晴"}

try:
    result = retry.retry(call_weather_api, "北京", "今天")
    print(f"成功获取天气: {result}")
except Exception as e:
    print(f"获取天气失败: {e}")
```

防止连续失败导致系统雪崩：

```text
class CircuitBreaker:
    """熔断器"""

    def __init__(self, failure_threshold=5, reset_timeout=60):
        self.failure_threshold = failure_threshold
        self.reset_timeout = reset_timeout
        self.failure_count = 0
        self.last_failure_time = None
        self.state = "closed"  # closed, open, half-open

    def execute(self, func, *args, **kwargs):
        """通过熔断器执行函数"""
        if self.state == "open":
            # 检查是否应该尝试恢复
            if self.should_try_reset():
                self.state = "half-open"
            else:
                raise Exception("熔断器开启，服务暂时不可用")

        try:
            result = func(*args, **kwargs)

            # 成功调用，重置状态
            if self.state == "half-open":
                self.state = "closed"
                self.failure_count = 0

            return result

        except Exception as e:
            self.record_failure()
            raise e

    def record_failure(self):
        """记录失败"""
        self.failure_count += 1
        self.last_failure_time = time.time()

        if self.failure_count >= self.failure_threshold:
            self.state = "open"

    def should_try_reset(self):
        """检查是否应该尝试重置"""
        if self.last_failure_time is None:
            return True

        elapsed = time.time() - self.last_failure_time
        return elapsed > self.reset_timeout

# 使用示例
breaker = CircuitBreaker(failure_threshold=3, reset_timeout=30)

def unreliable_service():
    """模拟不可靠的服务"""
    if random.random() < 0.5:
        raise Exception("服务异常")
    return "服务正常"

for i in range(10):
    try:
        result = breaker.execute(unreliable_service)
        print(f"调用{i+1}: {result}")
    except Exception as e:
        print(f"调用{i+1}: {e}")
        time.sleep(1)
```


### 完整的工具调用框架

结合上述所有组件，我们可以构建一个完整的工具调用框架：


## 后续章节

- 实例

## 复习重点

- 能说明 `工具调用` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

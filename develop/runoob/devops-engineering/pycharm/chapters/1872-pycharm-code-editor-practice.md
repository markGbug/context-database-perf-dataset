# PyCharm：PyCharm 代码编辑

- 来源：[PyCharm 代码编辑](https://www.runoob.com/pycharm/pycharm-code-editor.html)
- 分类：DevOps / 工程化
- 技术：PyCharm
- 笔记类型：练习笔记
- 章节序号：1872

## 本章内容

PyCharm 作为专业的 Python IDE，提供了强大的代码编辑功能。

本章节将详细介绍代码编辑的核心功能，包括智能补全、快捷键操作、代码重构等高效开发技巧。


## 基本编辑功能


### 代码补全（Code Completion）

PyCharm 提供多种智能补全方式：

输入 im + Tab → 自动补全为 import:

输入 for + Tab → 生成完整 for 循环结构:


### 语法高亮（Syntax Highlighting）

PyCharm 自动对代码元素着色：

- 关键字（def, class）：蓝色
- 字符串：绿色
- 注释：灰色
- 错误语法：红色波浪线

自定义高亮：

- 设置 → 编辑器 → 配色方案（Color Scheme）
- 调整 Python 语法元素的颜色


### 代码折叠（Code Folding）

鼠标移动到编辑器代码区域的左边可以看到有个向下的箭头，点击它也能折叠：

支持折叠的代码结构：

- 函数/方法
- 类定义
- 多行注释
- 导入语句组


## 快捷键与高效操作


### 常用快捷键速查表


### 多行编辑与批量操作

- 按住 Alt（Win）或 ⌥（Mac） + 鼠标拖动
- 或使用 Alt + Shift + Insert 切换列模式

应用场景：

```text
# 批量修改多个变量前缀
old_name = 1    →  new_name = 1
old_value = 2   →  new_value = 2
```

- 按住 Alt + 鼠标点击（添加多个光标）
- 或 Ctrl + G（Win）/ ⌘ + G（Mac） 选择相同单词


## 代码格式化与重构


### 自动格式化代码

- 格式化当前文件： Ctrl + Alt + L（Win/Linux） ⌥ + ⌘ + L（Mac）
- 格式化选中代码： 选中代码 → 右键 → Reformat Code

配置格式化规则： 设置 → 编辑器 → 代码样式 → Python


### 重命名变量/函数（安全重构）

- 选中标识符（变量/函数名）
- 右键 → Refactor → Rename
- 或快捷键 Shift + F6
- 输入新名称 → 按 Enter

效果：

- 所有引用该标识符的地方同步更新
- 支持跨文件重命名


### 提取方法（Extract Method）

将选中代码片段提取为新方法：

- 选中代码块
- Ctrl + Alt + M（Win）/ ⌘ + ⌥ + M（Mac）
- 输入方法名 → 确认


## 实例


### 内联（Inline）

将方法/变量内联到调用处：

- 光标定位到方法名/变量
- Ctrl + Alt + N（Win）/ ⌘ + ⌥ + N（Mac）

```text
# 内联前
def calculate_discount(price):
    return price * 0.9

total = calculate_discount(100)  # ← 光标在此行

# 内联后
total = 100 * 0.9  # ← 方法调用被替换为实际代码
```


## 高级编辑技巧


### 实时模板（Live Templates）

快速生成常用代码模式：

- 输入缩写（如 iter） → 按 Tab
- 预置模板： main → 生成 if __name__ == '__main__' try → 生成完整 try-except 块

自定义模板： 设置 → 编辑器 → 实时模板

在代码编辑器中输入 iter 就可以显示模板信息：


### 代码意图动作（Alt+Enter）

根据上下文快速修复或优化代码：

- 自动导入缺失的包
- 转换字符串格式（f-string / format）
- 优化条件表达式

操作：光标定位到警告/建议处 → Alt + Enter


## 总结：高效编辑工作流

- 编写阶段： 用代码补全 (Ctrl + Space) 快速输入 用动态模板生成重复结构
- 优化阶段： 格式化代码 (Ctrl + Alt + L) 用 Alt + Enter 快速修复问题
- 重构阶段： 提取方法 (Ctrl + Alt + M) 安全重命名 (Shift + F6)


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `PyCharm 代码编辑` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

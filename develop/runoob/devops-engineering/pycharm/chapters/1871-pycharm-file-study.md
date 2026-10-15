# PyCharm：PyCharm 文件与文件夹操作

- 来源：[Pycharm 文件操作](https://www.runoob.com/pycharm/pycharm-file.html)
- 分类：DevOps / 工程化
- 技术：PyCharm
- 笔记类型：学习笔记
- 章节序号：1871

## 本章内容

PyCharm 提供了强大的文件管理功能，让开发者可以高效组织项目结构。

本部分将详细介绍文件与文件夹的创建、移动、重命名、搜索等操作。


## 1. 文件与文件夹基本操作


### 1.1 创建新文件/文件夹

- 在 项目工具窗口（Project View） 中右键目标目录
- 选择： 新建 → Python 文件（创建 .py 文件） 新建 → 目录（创建文件夹） 其他文件类型（HTML、JSON 等）
- 新建文件：Alt + Insert（Windows/Linux） / ⌘N（Mac）
- 新建目录：同上操作，选择 "Directory"


### 1.2 重命名文件/文件夹

- 选中文件 → 右键 → 重构（Refactor）→ 重命名（Rename）
- 或使用快捷键：Shift + F6
- 输入新名称 → 按 Enter 确认

优势：

- 自动更新所有引用该文件的代码
- 避免因手动重命名导致导入错误
- 右键 → 重命名（可能破坏代码引用）


### 1.3 移动文件/文件夹

- 选中文件 → 右键 → 重构（Refactor）→ 移动（Move）
- 或快捷键：F6
- 选择目标目录 → 点击 Refactor

效果：

- 自动修复所有导入路径
- 例如：将 utils/helper.py 移动到 core/ 下，所有 from utils.helper import xxx 会自动更新为 from core.helper import xxx
- 直接拖拽文件可能导致导入路径错误


### 1.4 删除文件/文件夹

- 选中文件 → 右键 → 重构（Refactor）→ 安全删除（Safe Delete）
- 或快捷键：Alt + Delete
- PyCharm 会检查是否有代码引用该文件 → 确认删除
- 右键 → 删除（Delete）（不会检查引用）


## 2. 文件内容操作


### 2.1 快速导航


### 2.2 代码搜索与替换

- 全局搜索：Ctrl + Shift + F（Mac：⌘ + Shift + F） 支持正则表达式、大小写匹配、文件类型过滤
- 当前文件搜索：Ctrl + F（Mac：⌘ + F）
- 全局替换：Ctrl + Shift + R（Mac：⌘ + Shift + R）
- 当前文件替换：Ctrl + R（Mac：⌘ + R）


### 2.3 文件对比

- 选中两个文件 → 右键 → 比较文件（Compare Files）
- 或使用 版本控制工具 查看文件修改差异


## 3. 高级文件管理技巧


### 3.1 文件模板

自定义新建文件时的默认内容：

- 设置 → 编辑器 → 文件和代码模板
- 选择 Python Script，修改模板： #!/usr/bin/env python # -*- coding: utf-8 -*- """ @Author: ${USER} @Date: ${DATE} @Description: """ def main(): pass if __name__ == '__main__': main()


### 3.2 本地历史记录

PyCharm 自动记录文件修改历史（无需 Git）：

- 右键文件 → 本地历史 → 显示历史（Local History → Show History）
- 可恢复任意时间点的版本


### 3.3 文件标记

- 书签（Bookmarks）： 添加书签：F11（行级）/ Ctrl + F11（带标记） 查看书签：Shift + F11
- TODO 注释： 会在 TODO 工具窗口 中集中显示


## 4. 常见问题解答


### Q1：如何隐藏特定文件/文件夹？

- 右键文件 → Mark Directory as → Excluded
- 或编辑 .idea/.gitignore


### Q2：如何批量重命名文件？

- 选中多个文件 → Shift + F6
- 使用模式替换（如 test_*.py → spec_*.py）


### Q3：如何恢复误删的文件？

- 右键项目根目录 → Local History → Show History
- 找到删除前的版本 → 恢复


## 5. 操作速查表


## 复习重点

- 能说明 `Pycharm 文件操作` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

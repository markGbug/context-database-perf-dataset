# Pillow：Pillow ImageColor 模块

- 来源：[Pillow ImageColor 模块](https://www.runoob.com/pillow/pillow-imagecolor-module.html)
- 分类：Python / 数据科学
- 技术：Pillow
- 笔记类型：练习笔记
- 章节序号：4073

## 本章内容

ImageColor 是 Python Pillow 图像处理库中的一个子模块，专门用于处理颜色相关的操作。

ImageColor 提供了一系列方法将颜色字符串转换为 RGB 或 RGBA 格式的元组，支持多种颜色表示格式。

ImageColor 模块虽然小巧，但在图像处理中扮演着重要角色，特别是在需要动态指定颜色的场景中。

可以通过以下方式导入 ImageColor 模块：

```text
from PIL import ImageColor
```


## ImageColor 模块核心方法

下表列出了 ImageColor 模块的主要方法及其功能说明：


## 方法详细说明与示例


### getrgb() 方法

getrgb() 方法是最常用的方法，它将各种格式的颜色字符串转换为标准的 RGB 元组。

支持的格式包括:

- 十六进制颜色码: "#RRGGBB" 或 "#RGB"
- RGB 函数表示: "rgb(255, 0, 0)"
- HSL 函数表示: "hsl(0, 100%, 50%)"
- 颜色名称: "red", "blue" 等

示例代码:


## 实例


### getcolor() 方法

getcolor() 方法与 getrgb() 类似，但可以指定目标颜色模式。

支持的模式包括:

- "RGB"
- "RGBA"
- "L" (灰度)
- "CMYK"
- "HSV"

示例代码:


## 实例


### colormap 属性

colormap 是一个字典，包含了 Pillow 支持的所有命名颜色及其对应的十六进制值。

示例代码:


## 实例


## 实际应用示例


### 创建单色图像


## 实例


### 动态设置绘图颜色


## 实例


## 注意事项

- 颜色字符串格式：确保颜色字符串格式正确，否则会引发 ValueError
- 颜色模式支持：不是所有颜色模式都支持所有颜色转换
- 性能考虑：频繁调用颜色转换方法可能会影响性能，建议预先转换并存储常用颜色
- 颜色名称限制：Pillow 支持的颜色名称有限，完整列表可通过 ImageColor.colormap 查看

通过掌握 ImageColor 模块，你可以更灵活地在 Pillow 图像处理中使用各种颜色表示方式，为你的图像处理程序增添更多可能性。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Pillow ImageColor 模块` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

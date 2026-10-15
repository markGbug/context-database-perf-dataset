# Matplotlib：Matplotlib 中文显示

- 来源：[Matplotlib 中文显示](https://www.runoob.com/matplotlib/matplotlib-zh.html)
- 分类：Python / 数据科学
- 技术：Matplotlib
- 笔记类型：练习笔记
- 章节序号：3974

## 本章内容

Matplotlib 中文显示不是特别友好，要在 Matplotlib 中显示中文，我们可以通过两个方法：

- 设置 Matplotlib 的字体参数。
- 下载使用支持中文的字体库。

在未设置字体，默认情况显示如下，中文部分不能正常显示：


## Matplotlib 的字体参数

我们可以先获取系统的字体库列表：


## 实例

输出结果类似如下：

```text
...
Heiti TC
Helvetica
Helvetica Neue
Herculanum
Hiragino Maru Gothic Pro
Hiragino Mincho ProN
Hiragino Sans
Hiragino Sans GB
Hoefler Text
...
```

以上代码输出 font_manager 的 ttflist 中所有注册的名字，找一个看中文字体例如：STFangsong(仿宋）、Heiti TC（黑体）,然后添加以下代码即可。

对于 Windows：

```text
plt.rcParams['font.family'] = 'SimHei'  # 替换为你选择的字体
```

在 Windows 系统上，选择 SimHei（黑体）或其他中文字体，并将其设置为 Matplotlib 的默认字体。

对于 Linux：

```text
plt.rcParams['font.family'] = 'WenQuanYi Micro Hei'  # 替换为你选择的字体
```

在Linux系统上，使用 fc-list 命令查看已安装的字体，选择一个中文字体，并将其设置为 Matplotlib 的默认字体。

对于 macOS：

```text
plt.rcParams['font.family'] = 'Heiti TC'  # 替换为你选择的字体
```

通过设置 plt.rcParams['font.family']，你告诉 Matplotlib 使用选择的字体来渲染文本，从而在图表中正确显示中文。

这样，你就能够在 Matplotlib 图表中使用系统支持的中文字体了。


## 实例

这样中文就可以正常显示了，显示如下：

各大平台系统通用方法：

```text
# -------------------------- 设置中文字体 start --------------------------
plt.rcParams['font.sans-serif'] = [
    # Windows 优先
    'SimHei', 'Microsoft YaHei',
    # macOS 优先
    'PingFang SC', 'Heiti TC',
    # Linux 优先
    'WenQuanYi Micro Hei', 'DejaVu Sans'
]
# 修复负号显示为方块的问题
plt.rcParams['axes.unicode_minus'] = False
# -------------------------- 设置中文字体 end --------------------------
```


## 实例

我们的目标是找到一条曲线（模型），能最好地描述这些蓝色散点（数据）所反映的规律。

模型对数据的描述程度，就是拟合。


## 使用字体库

Matplotlib 默认情况不支持中文，我们可以使用以下简单的方法来解决。

这里我们使用思源黑体，思源黑体是 Adobe 与 Google 推出的一款开源字体。

官网：https://source.typekit.com/source-han-serif/cn/

GitHub 地址：https://github.com/adobe-fonts/source-han-sans/tree/release/OTF/SimplifiedChinese

打开链接后，在里面选一个就好了：

你也可以在网盘下载: https://pan.baidu.com/s/10-w1JbXZSnx3Tm6uGpPGOw，提取码：yxqu。

可以下载个 OTF 字体，比如 SourceHanSansSC-Bold.otf，将该文件文件放在当前执行的代码文件中：

SourceHanSansSC-Bold.otf 文件放在当前执行的代码文件中：


## 实例

```text
import numpy as np
from matplotlib import pyplot as plt
import matplotlib

# fname 为 你下载的字体库路径，注意 SourceHanSansSC-Bold.otf 字体的路径
zhfont1 = matplotlib.font_manager.FontProperties(fname="SourceHanSansSC-Bold.otf")

x = np.arange(1,11)
y =  2  * x +  5
plt.title("菜鸟教程 - 测试", fontproperties=zhfont1)

# fontproperties 设置中文显示，fontsize 设置字体大小
plt.xlabel("x 轴", fontproperties=zhfont1)
plt.ylabel("y 轴", fontproperties=zhfont1)
plt.plot(x,y)
plt.show()
```

执行输出结果如下图：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Matplotlib 中文显示` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

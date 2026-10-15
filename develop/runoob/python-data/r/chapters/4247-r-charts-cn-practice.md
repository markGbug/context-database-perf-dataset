# R：R 绘图 - 中文支持

- 来源：[R 绘图 - 中文支持](https://www.runoob.com/r/r-charts-cn.html)
- 分类：Python / 数据科学
- 技术：R
- 笔记类型：练习笔记
- 章节序号：4247

## 本章内容

不同系统的字体库目录：

- Windows 字体在 C:\Windows\Fonts\ 文件下，直接打开就能看到了。
- mac OS 字体在 /System/Library/Fonts 和 /Library/Fonts 目录下。

系统支持的字体库，可以通过安装 showtext 来查看：

```text
> install.packages("showtext", repos = "https://mirrors.ustc.edu.cn/CRAN/")  # 安装 showtext
...
> font_files()   # 查看字体
            path              file           family    face       version
1 /Library/Fonts Arial Unicode.ttf Arial Unicode MS Regular Version 1.01x
         ps_name
1 ArialUnicodeMS
```

看到有 ArialUnicodeMS，我们就可以用了：

```text
pie3D(info,labels = names,explode = 0.1, main = "3D 图",family = "ArialUnicodeMS")
```


### 载入自定义字体

系统的字体库有时候不是支持的很好， showtext() 函数可以载入我们自定义的字体，可以下载字体包 ttf，然后使用 font_add() 函数添加。

这里我们使用思源黑体，思源黑体是 Adobe 与 Google 推出的一款开源字体。

官网：https://source.typekit.com/source-han-serif/cn/

GitHub 地址：https://github.com/adobe-fonts/source-han-sans/tree/release/OTF/SimplifiedChinese

打开链接后，在里面选一个就好了：

你也可以在网盘下载: https://pan.baidu.com/s/14cRhgYvvYotVIFkRVd71fQ 。

可以下载个 OTF 字体，比如 SourceHanSansSC-Bold.otf，将该文件文件放在当前执行的代码文件中：

柱形图使用字体库：


## 实例

3D 饼图使用中文：


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `R 绘图 - 中文支持` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

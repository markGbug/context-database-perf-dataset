# Jupyter Notebook：Jupyter Notebook 中文设置

- 来源：[Jupyter Notebook 中文](https://www.runoob.com/jupyter-notebook/jupyter-notebook-chinese.html)
- 分类：Python / 数据科学
- 技术：Jupyter Notebook
- 笔记类型：练习笔记
- 章节序号：3955

## 本章内容

默认情况下，Jupyter Notebook 界面为英文，通过设置菜单可以看到支持的是英文。

我们可以通过通过安装 Jupyter 官方中文语言包，可在不改变浏览器语言的前提下，单独将 Jupyter Notebook 界面改为中文，步骤如下：

1. 打开命令提示符（Windows）或终端（macOS/Linux），输入以下命令安装中文语言包：

```text
pip install jupyterlab-language-pack-zh-CN
```

若使用 Python3 环境（macOS/Linux 常见），则输入：

```text
pip3 install jupyterlab-language-pack-zh-CN
```

2. 安装完成后，启动 Jupyter Notebook，进入任意 Notebook 编辑界面。

```text
jupyter notebook
```

这时候启动的界面其实就是中文的了：

3. 点击菜单栏 "Settings"（设置）→ 选择"Language"→ 点击"中文（简体）"，即可实时切换为中文界面。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Jupyter Notebook 中文` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

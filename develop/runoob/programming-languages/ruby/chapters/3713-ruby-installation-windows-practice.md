# Ruby：Ruby 安装 - Windows

- 来源：[Ruby 安装 - Windows](https://www.runoob.com/ruby/ruby-installation-windows.html)
- 分类：编程语言
- 技术：Ruby
- 笔记类型：练习笔记
- 章节序号：3713

## 本章内容

下面列出了在 Windows 机器上安装 Ruby 的步骤。

下载地址：

- 官网：http://rubyinstaller.org/downloads/
- 国内：https://rubyinstaller.cn/

注意：在安装时，您可能有不同的可用版本。

- Window 系统下，我们可以使用 RubyInstaller 来安装 Ruby 环境，下载地址为：请点击这里下载。
- 下载 rubyinstaller 之后，解压到新创建的目录下：
- 双击 rubyinstaller-2.2.3.exe 文件，启动 Ruby 安装向导。
- 点击 Next，继续向导，记得勾选 Add Ruby executables to your PATH，直到 Ruby 安装程序完成 Ruby 安装为止。

如果您的安装没有适当地配置环境变量，接下来您可能需要进行环境变量的配置。

- 如果您使用的是 Windows 9x，那么请在您的 c:\autoexec.bat 中添加：set PATH="D:\(ruby 安装目录)\bin;%PATH%"
- Windows NT/2000 用户需要修改注册表。 点击控制面板|系统性能|环境变量。 在系统变量下，选择 Path，并点击 EDIT。 在变量值列表的末尾添加 Ruby 目录，并点击 OK。 在系统变量下，选择 PATHEXT，并点击 EDIT。 添加 .RB 和 .RBW 到变量值列表中，并点击 OK。
- 安装后，通过在命令行中输入以下命令来确保一切工作正常：

```text
$ ruby -v
ruby 2.2.3
```

- 如果一切工作正常，将会输出所安装的 Ruby 解释器的版本，如上所示。如果您安装了其他版本，则会显示其他不同的版本。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Ruby 安装 - Windows` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

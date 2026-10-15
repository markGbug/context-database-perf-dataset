# JSP：JSP 开发环境搭建

- 来源：[JSP 开发环境搭建](https://www.runoob.com/jsp/jsp-setup.html)
- 分类：后端开发
- 技术：JSP
- 笔记类型：练习笔记
- 章节序号：0936

## 本章内容

JSP 开发环境是您用来开发、测试和运行 JSP 程序的地方。

本节将会带您搭建 JSP 开发环境，具体包括以下几个步骤。

如果你使用的是 Eclipse 环境，可以直接参阅：Eclipse JSP/Servlet 环境搭建。


## 配置Java开发工具（JDK）

这一步涉及 Java JDK 的下载和 PATH 环境变量的配置。

您可以从 Oracle 公司的 Java 页面中下载 JDK：Java SE Downloads

Java JDK 下载完后，请按照给定的指示来安装和配置 JDK。最后，通过设置 PATH 和 JAVA_HOME环境变量来指明包括 java 和 javac 的文件夹路径，通常是 java_install_dir/bin和java_install_dir。

假如您用的是 Windows 系统并且 JDK 的安装目录为 C::\jdk1.5.0_20，那么您就需要在 C:\autoexec.bat 文件中添加以下两行：

```text
set PATH=C:\jdk1.5.0_20\bin;%PATH%
set JAVA_HOME=C:\jdk1.5.0_20
```

或者，在 Windows NT/2000/XP下，您可以直接右击我的电脑图标，选择属性，然后高级，然后环境变量，接下来您就可以很方便地设置 PATH 变量并且确定退出就行了。

在 Linux/Unix 系统下，如果 JDK 的安装目录为 /usr/local/jdk1.5.0_20 并且使用的是 C shell，那么您就需要在 .cshrc 文件中添加以下两行：

```text
setenv PATH /usr/local/jdk1.5.0_20/bin:$PATH
setenv JAVA_HOME /usr/local/jdk1.5.0_20
```

或者，假如您正在使用类似于 Borland JBuilder、Eclipse、IntelliJ IDEA 和 Sun ONE Studio 这样的集成开发环境，可以试着编译并运行一个简单的程序来确定 IDE（集成开发环境）是否已经知道 JDK 的安装目录。

本步骤你也可以参考本站Java 开发环境配置章节的教程。


## 设置Web服务器：Tomcat

目前，市场上有很多支持 JSP 和 Servlets 开发的 Web 服务器。他们中的一些可以免费下载和使用，Tomcat 就是其中之一。

Apache Tomcat 是一个开源软件，可作为独立的服务器来运行 JSP 和 Servlets，也可以集成在 Apache Web Server 中。以下是 Tomcat 的配置方法：

- 下载最新版本的 Tomcat：http://tomcat.apache.org/。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `JSP 开发环境搭建` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

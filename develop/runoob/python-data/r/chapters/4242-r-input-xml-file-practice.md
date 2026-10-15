# R：R XML 文件

- 来源：[R XML 文件](https://www.runoob.com/r/r-input-xml-file.html)
- 分类：Python / 数据科学
- 技术：R
- 笔记类型：练习笔记
- 章节序号：4242

## 本章内容

XML 指的是可扩展标记语言（eXtensible Markup Language），XML 被设计用来传输和存储数据。

如果你对 XML 还不了解，可以先查阅：XML 教程

R 语言读写 XML 文件需要安装扩展包，我们可以在 R 到控制台输入以下命令来安装：

```text
install.packages("XML", repos = "https://mirrors.ustc.edu.cn/CRAN/")
```

查看是否安装成功：

```text
> any(grepl("XML",installed.packages()))
[1] TRUE
```

创建 sites.xml 文件，xml 文件与测试脚本同一目录下，代码如下：


## 实例

```html
<sites>
    <site>
        <id>1</id>
        <name>Google</name>
        <url>www.google.com</url>
        <likes>111</likes>
    </site>

    <site>
        <id>2</id>
        <name>Runoob</name>
        <url>www.runoob.com</url>
        <likes>222</likes>
    </site>

    <site>
        <id>3</id>
        <name>Taobao</name>
        <url>www.taobao.com</url>
        <likes>333</likes>
    </site>
</sites>
```

接下来我们可以使用 XML 包来载入 xml 文件的数据：


## 实例

统计 xml 数据量：


## 实例

执行以上代码输出结果为：

```text
[1] 3
```

查看节点数据，某一行使用 [ ], 指定的行和列使用 [[ ]]:


## 实例

执行以上代码输出结果为：

```html
$site
<site>
  <id>2</id>
  <name>Runoob</name>
  <url>www.runoob.com</url>
  <likes>222</likes>
</site>

attr(,"class")
[1] "XMLInternalNodeList" "XMLNodeList"
<id>2</id>
<url>www.runoob.com</url>
```


### XML 转为数据列表


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `R XML 文件` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

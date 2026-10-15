# ASP：ASP File 对象

- 来源：[ASP File](https://www.runoob.com/asp/asp-ref-file.html)
- 分类：后端开发
- 技术：ASP
- 笔记类型：练习笔记
- 章节序号：0735

## 本章内容

File 对象用于返回关于指定文件的信息。


## 尝试一下 - 实例

文件最后被修改的时间？ 本例演示如何使用 DateLastModified 属性来取得指定文件最后被修改的日期和时间。

文件最后被访问的时间？ 此例演示如何使用 DateLastAccessed 属性来取得指定文件最后被访问的日期和时间。

返回指定文件的属性 本例演示如何使用 Attributes 来返回指定文件的属性。


## File 对象

File 对象用于返回关于指定文件的信息。

如需操作 File 对象的相关属性和方法，您需要通过 FileSystemObject 对象来创建 File 对象的实例。首先，创建一个 FileSystemObject 对象，然后通过 FileSystemObject 对象的 GetFile 方法，或者通过 Folder 对象的 Files 属性来实例化 File 对象。

下面的代码使用 FileSystemObject 对象的 GetFile 方法来实例化 File 对象，并使用 DateCreated 属性来返回指定文件的创建日期：


## 实例

File 对象的属性和方法描述如下：


### 属性


### 方法


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `ASP File` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

# ASP：ASP File 对象

- 来源：[ASP File](https://www.runoob.com/asp/asp-ref-file.html)
- 分类：后端开发
- 技术：ASP
- 笔记类型：概念卡
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


## 记忆卡片

- 一句话定义：`ASP File` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。

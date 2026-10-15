# Linux：Shell 文件包含

- 来源：[Shell 文件包含](https://www.runoob.com/linux/linux-shell-include-file.html)
- 分类：后端开发
- 技术：Linux
- 笔记类型：练习笔记
- 章节序号：0993

## 本章内容

和其他语言一样，Shell 也可以包含外部脚本。这样可以很方便的封装一些公用的代码作为一个独立的文件。

Shell 文件包含的语法格式如下：

```text
. filename   # 注意点号(.)和文件名中间有一空格

或

source filename
```


### 实例

创建两个 shell 脚本文件。

test1.sh 代码如下：

```text
#!/bin/bash
# author:菜鸟教程
# url:www.runoob.com

url="http://www.runoob.com"
```

test2.sh 代码如下：

```text
#!/bin/bash
# author:菜鸟教程
# url:www.runoob.com

#使用 . 号来引用test1.sh 文件
. ./test1.sh

# 或者使用以下包含文件代码
# source ./test1.sh

echo "菜鸟教程官网地址：$url"
```

接下来，我们为 test2.sh 添加可执行权限并执行：

```text
$ chmod +x test2.sh
$ ./test2.sh
菜鸟教程官网地址：http://www.runoob.com
```

注：被包含的文件 test1.sh 不需要可执行权限。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Shell 文件包含` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

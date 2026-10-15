# Ruby：Ruby CGI方法

- 来源：[Ruby CGI方法](https://www.runoob.com/ruby/ruby-cgi-methods.html)
- 分类：编程语言
- 技术：Ruby
- 笔记类型：学习笔记
- 章节序号：3744

## 本章内容

以下为CGI类的方法列表：

- query: 没有 HTML 生成输出
- html3: HTML3.2
- html4: HTML4.0 Strict
- html4Tr: HTML4.0 Transitional
- html4Fr: HTML4.0 Frameset


## CGI 实例化方法

以下实例中我们将 CGI::new 的对象赋值给 c 变量，方法列表如下：


## HTML 生成方法

你可以再 CGI 实例中使用相应的 HTML 标签名来创建 HTML 标签，实例如下：


## 实例

```text
#!/usr/bin/ruby

require "cgi"
cgi = CGI.new("html4")
cgi.out{
   cgi.html{
      cgi.head{ "\n"+cgi.title{"This Is a Test"} } +
      cgi.body{ "\n"+
         cgi.form{"\n"+
            cgi.hr +
            cgi.h1 { "A Form: " } + "\n"+
            cgi.textarea("get_text") +"\n"+
            cgi.br +
            cgi.submit
         }
      }
   }
}
```


## CGI 对象属性

你可以再 CGI 实例中使用以下属性：


## 复习重点

- 能说明 `Ruby CGI方法` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

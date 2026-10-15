# Ruby：Ruby CGI Session

- 来源：[Ruby CGI Session](https://www.runoob.com/ruby/ruby-cgi-sessions.html)
- 分类：编程语言
- 技术：Ruby
- 笔记类型：练习笔记
- 章节序号：3746

## 本章内容

CGI::Session 可以为用户和CGI环境保存持久的会话状态，会话使用后需要关闭，这样可以保证数据写入到存储当中，当会话完成后，你需要删除该数据。


## 实例

```text
#!/usr/bin/ruby

require 'cgi'
require 'cgi/session'
cgi = CGI.new("html4")

sess = CGI::Session.new( cgi, "session_key" => "a_test",
                              "prefix" => "rubysess.")
lastaccess = sess["lastaccess"].to_s
sess["lastaccess"] = Time.now
if cgi['bgcolor'][0] =~ /[a-z]/
  sess["bgcolor"] = cgi['bgcolor']
end

cgi.out{
  cgi.html {
    cgi.body ("bgcolor" => sess["bgcolor"]){
      "The background of this page"    +
      "changes based on the 'bgcolor'" +
      "each user has in session."      +
      "Last access time: #{lastaccess}"
    }
  }
}
```

访问 "/cgi-bin/test.cgi?bgcolor=red" 将跳转到指定背景颜色的页面。

会话数据存在在服务器的临时文件目录中，prefix 参数指定了会话的前缀，将作为临时文件的前缀。这样你在服务器上可以轻松的识别不同的会话临时文件。


## CGI::Session 类


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Ruby CGI Session` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

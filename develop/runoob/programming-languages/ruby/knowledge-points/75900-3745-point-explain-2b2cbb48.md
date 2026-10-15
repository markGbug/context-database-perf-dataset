# 知识点 75900：Ruby：Ruby CGI Cookie - 写入和读取

- 来源：[Ruby CGI Cookie](https://www.runoob.com/ruby/ruby-cgi-cookies.html)
- 来源章节：[3745-ruby-cgi-cookies-practice.md](../chapters/3745-ruby-cgi-cookies-practice.md)
- 分类：编程语言
- 技术：Ruby
- 所在小节：写入和读取
- 知识类型：解释
- 原章节序号：3745

## 原文片段

如果用户要读取Cookies，则必须使用Request对象的Cookies集合，其使用方法是： 需要注意的是，只有在服务器未被下载任何数据给浏览器前，浏览器才能与Server进行Cookies集合的数据交换，一旦浏览器开始接收Server所下载的数据，Cookies的数据交换则停止，为了避免错误，要在程序和前面加上response.Buffer=True。

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `写入和读取` 这一小节和 `Ruby CGI Cookie` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？

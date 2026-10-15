# PHP：PHP RESTful

- 来源：[PHP RESTful](https://www.runoob.com/php/php-restful.html)
- 分类：后端开发
- 技术：PHP
- 笔记类型：练习笔记
- 章节序号：1127

## 本章内容

REST（英文：Representational State Transfer，简称REST) ，指的是一组架构约束条件和原则。

符合REST设计风格的Web API称为RESTful API。它从以下三个方面资源进行定义：

- 直观简短的资源地址：URI，比如：http://example.com/resources/。
- 传输的资源：Web服务接受与返回的互联网媒体类型，比如：JSON，XML，YAM等。
- 对资源的操作：Web服务在该资源上所支持的一系列请求方法（比如：POST，GET，PUT或DELETE）。

本教程我们将使用 PHP(不用框架) 来创建一个 RESTful web service，在文章末尾你可以下载本章节使用到的代码。

通过本教程你将学习到以下内容：

- 创建一个 RESTful Webservice。
- 使用原生 PHP, 不依赖任何框架。
- URI 模式需要遵循 REST 规则。
- RESTful service 接受与返回的格式可以是 JSON, XML等。
- 根据不同情况响应对应的 HTTP 状态码。
- 演示请求头的使用。
- 使用 REST 客户端来测试 RESTful web service。


## RESTful Webservice 实例

以下代码是 RESTful 服务类 Site.php：


## 实例

```javascript
<?php
/*
 * 菜鸟教程 RESTful 演示实例
 * RESTful 服务类
 */
Class Site {

    private $sites = array(
        1 => 'TaoBao',
        2 => 'Google',
        3 => 'Runoob',
        4 => 'Baidu',
        5 => 'Weibo',
        6 => 'Sina'

    );


    public function getAllSite(){
        return $this->sites;
    }

    public function getSite($id){

        $site = array($id => ($this->sites[$id]) ? $this->sites[$id] : $this->sites[1]);
        return $site;
    }
}
?>
```


## RESTful Services URI 映射


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `PHP RESTful` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

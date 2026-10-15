# Bootstrap4：Bootstrap4 信息提示框

- 来源：[Bootstrap4 信息提示框](https://www.runoob.com/bootstrap4/bootstrap4-alerts.html)
- 分类：前端开发
- 技术：Bootstrap4
- 笔记类型：练习笔记
- 章节序号：2312

## 本章内容

Bootstrap 4 可以很容易实现信息提示框。

提示框可以使用 .alert 类, 后面加上 .alert-success, .alert-info, .alert-warning, .alert-danger, .alert-primary, .alert-secondary, .alert-light 或 .alert-dark 类来实现:


## 实例

```html
<div class="alert alert-success">
  <strong>成功!</strong> 指定操作成功提示信息。
</div>
```


## 提示框添加链接

提示框中在链接的标签上添加 alert-link 类来设置匹配提示框颜色的链接：


## 实例

```html
<div class="alert alert-success">
  <strong>成功!</strong> 你应该认真阅读 <a href="#" class="alert-link">这条信息</a>。
</div>
```


## 关闭提示框

我们可以在提示框中的 div 中添加 .alert-dismissible 类，然后在关闭按钮的链接上添加 class="close" 和 data-dismiss="alert" 类来设置提示框的关闭操作。


## 实例

```html
<div class="alert alert-success alert-dismissible">
  <button type="button" class="close" data-dismiss="alert">×</button>
  <strong>成功!</strong> 指定操作成功提示信息。
</div>
```

提示: × (×) 是 HTML 实体字符，来表示关闭操作，而不是字母 "x"。


## 提示框动画

.fade 和 .show 类用于设置提示框在关闭时的淡出和淡入效果：


## 实例

```html
<div class="alert alert-danger alert-dismissible fade show">
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Bootstrap4 信息提示框` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

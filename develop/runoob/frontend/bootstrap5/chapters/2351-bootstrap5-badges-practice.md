# Bootstrap5：Bootstrap5 徽章（Badges）

- 来源：[Bootstrap5 徽章](https://www.runoob.com/bootstrap5/bootstrap5-badges.html)
- 分类：前端开发
- 技术：Bootstrap5
- 笔记类型：练习笔记
- 章节序号：2351

## 本章内容

徽章（Badges）主要用于突出显示新的或未读的项。如需使用徽章，只需要将 .badge 类加上带有指定意义的颜色类 (如 .bg-secondary) 添加到 <span> 元素上即可。 徽章可以根据父元素的大小的变化而变化:


## 实例

```html
<h1>测试标题 <span class="badge bg-secondary">New</span></h1>
<h2>测试标题 <span class="badge bg-secondary">New</span></h2>
<h3>测试标题 <span class="badge bg-secondary">New</span></h3>
<h4>测试标题 <span class="badge bg-secondary">New</span></h4>
<h5>测试标题 <span class="badge bg-secondary">New</span></h5>
<h6>测试标题 <span class="badge bg-secondary">New</span></h6>
```


## 各种颜色类型的徽章

以下列出了所有颜色类型的徽章:


## 实例

```html
<span class="badge bg-primary">主要</span>
<span class="badge bg-secondary">次要</span>
<span class="badge bg-success">成功</span>
<span class="badge bg-danger">危险</span>
<span class="badge bg-warning">警告</span>
<span class="badge bg-info">信息</span>
<span class="badge bg-light">浅色</span>
<span class="badge bg-dark">深色</span>
```


## 药丸形状徽章

使用 .rounded-pill 类来设置药丸形状徽章:


## 实例

```html
<span class="badge rounded-pill bg-primary">主要</span>
<span class="badge rounded-pill bg-success">成功</span>
<span class="badge rounded-pill bg-info">信息</span>
<span class="badge rounded-pill bg-warning">警告</span>
<span class="badge rounded-pill bg-danger">危险</span>
```


## 徽章插入到元素内

以下实例将徽章嵌入到按钮内：


## 实例

```html
<button type="button" class="btn btn-primary">
  Messages <span class="badge bg-light">4</span>
</button>
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Bootstrap5 徽章` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

# Ionic：ionic Range

- 来源：[ionic range](https://www.runoob.com/ionic/ionic-range.html)
- 分类：移动开发
- 技术：Ionic
- 笔记类型：练习笔记
- 章节序号：3305

## 本章内容

ionic Range 是一个滑块控件，ionic 为 Range 提供了很多种默认的样式。而且你可以在许多种元素里使用它比如列表或者 Card 。


### 实例

```html
<div class="range">
  <i class="icon ion-volume-low"></i>
  <input type="range" name="volume">
  <i class="icon ion-volume-high"></i>
</div>

<div class="list" style="margin-top: 13px">
  <div class="item item-divider">
    Ranges In A List
  </div>
  <div class="item range range-positive">
    <i class="icon ion-ios-sunny-outline"></i>
    <input type="range" name="volume" min="0" max="100" value="12">
    <i class="icon ion-ios-sunny"></i>
  </div>
  <div class="item range range-calm">
    <i class="icon ion-ios-lightbulb-outline"></i>
    <input type="range" name="volume" min="0" max="100" value="25">
    <i class="icon ion-ios-lightbulb"></i>
  </div>
  <div class="item range range-balanced">
    <i class="icon ion-ios-bolt-outline"></i>
    <input type="range" name="volume" min="0" max="100" value="38">
    <i class="icon ion-ios-bolt"></i>
  </div>
  <div class="item range range-energized">
    <i class="icon ion-ios-moon-outline"></i>
    <input type="range" name="volume" min="0" max="100" value="50">
    <i class="icon ion-ios-moon"></i>
  </div>
  <div class="item range range-assertive">
    <i class="icon ion-ios-partlysunny-outline"></i>
    <input type="range" name="volume" min="0" max="100" value="63">
    <i class="icon ion-ios-partlysunny"></i>
  </div>
  <div class="item range range-royal">
    <i class="icon ion-ios-rainy-outline"></i>
    <input type="range" name="volume" min="0" max="100" value="75">
    <i class="icon ion-ios-rainy"></i>
  </div>
  <div class="item range range-dark">
    <i class="icon ion-ios-lightbulb-outline"></i>
    <input type="range" name="volume" min="0" max="100" value="88">
    <i class="icon ion-ios-lightbulb"></i>
  </div>
</div>
```

尝试一下 »

运行效果如下：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `ionic range` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

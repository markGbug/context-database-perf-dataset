# Ionic：ionic Toggle(切换开关)

- 来源：[ionic toggle](https://www.runoob.com/ionic/ionic-toggle.html)
- 分类：移动开发
- 技术：Ionic
- 笔记类型：学习笔记
- 章节序号：3302

## 本章内容

切换开关类似与 HTML 的 checkbox 标签，但它更易于在移动设备上使用。

切换开关可以使用 toggle-assertive 来指定颜色。

```html
<label class="toggle">
   <input type="checkbox">
   <div class="track">
     <div class="handle"></div>
   </div>
</label>
```

该实例有是多个切换开关列表。注意，每个选项的 item 类后需要添加 item-toggle 类。

```html
<ul class="list">

  <li class="item item-toggle">
     HTML5
     <label class="toggle toggle-assertive">
       <input type="checkbox">
       <div class="track">
         <div class="handle"></div>
       </div>
     </label>
  </li>

  ...

</ul>
```

尝试一下 »

运行效果如下：


## 复习重点

- 能说明 `ionic toggle` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

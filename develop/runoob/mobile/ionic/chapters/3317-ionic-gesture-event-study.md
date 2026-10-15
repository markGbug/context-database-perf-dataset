# Ionic：ionic 手势事件

- 来源：[ionic 手势事件](https://www.runoob.com/ionic/ionic-gesture-event.html)
- 分类：移动开发
- 技术：Ionic
- 笔记类型：学习笔记
- 章节序号：3317

## 本章内容

```html
<button
    on-hold="onHold()"
    class="button">
    Test
    </button>
```

```html
<button
    on-tap="onTap()"
    class="button">
    Test
    </button>
```

```html
<button
    on-double-tap="onDoubleTap()"
    class="button">
    Test
    </button>
```

```html
    <button on-touch="onTouch()"
    class="button">
    Test
    </button>
```

```html
<button
    on-release="onRelease()"
    class="button">
    Test
</button>
```

```html
<button
    on-drag="onDrag()"
    class="button">
    Test
</button>
```

```html
<button
    on-drag-up="onDragUp()"
    class="button">
    Test
</button>
```

```html
<button
    on-drag-right="onDragRight()"
    class="button">
    Test
</button>
```

```html
<button
    on-drag-down="onDragDown()"
    class="button">
    Test
</button>
```

```html
<button
    on-drag-left="onDragLeft()"
    class="button">
    Test
</button>
```

```html
<button
    on-swipe="onSwipe()"
    class="button">
    Test
</button>
```

```html
<button
    on-swipe-up="onSwipeUp()"
    class="button">
    Test
</button>
```

```html
<button
    on-swipe-right="onSwipeRight()"
    class="button">
    Test
</button>
```

```html
<button
    on-swipe-down="onSwipeDown()"
    class="button">
    Test
</button>
```

```html
<button
    on-swipe-left="onSwipeLeft()"
    class="button">
    Test
</button>
```


## $ionicGesture

一个angular服务展示ionicionic.EventController手势。


### 方法

```text
on(eventType, callback, $element)
```

在一个元素上添加一个事件监听器。

监听的手势事件。

当手势事件发生时触发的事件。

angular元素监听的事件。

对象。

```text
off(eventType, callback, $element)
```

在一个元素上移除一个手势事件监听器。

移除监听的手势事件。

移除监听器。

被监听事件的angular元素。


## 复习重点

- 能说明 `ionic 手势事件` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

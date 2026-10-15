# Bootstrap5：Bootstrap5 折叠

- 来源：[Bootstrap5 折叠](https://www.runoob.com/bootstrap5/bootstrap5-collapse.html)
- 分类：前端开发
- 技术：Bootstrap5
- 笔记类型：练习笔记
- 章节序号：2358

## 本章内容

Bootstrap5 折叠可以很容易的实现内容的显示与隐藏。

data-bs-toggle 和 data-bs-target 是用于定义组件行为和目标元素的自定义数据属性。

1、data-bs-toggle 属性：

- 用于定义组件的行为，指示组件在何时触发。
- 可以设置的值取决于具体的组件类型，如 "collapse"（折叠菜单）、"modal"（模态框）、"tab"（标签页）等。
- data-bs-toggle="collapse" 用于触发折叠菜单的展开与折叠。
- data-bs-toggle="modal" 用于触发模态框的显示与隐藏。
- data-bs-toggle="tab" 用于触发标签页的切换。

2、data-bs-target 属性：

- 用于指定组件的目标元素或目标选择器。
- 目标元素可以是一个 CSS 选择器，用于标识要操作的具体元素。
- 也可以是一个指定的元素 ID，以 # 开头，如 data-bs-target="#myModal"。
- data-bs-target 属性与 data-bs-toggle 属性一起使用，用于将组件行为与目标元素关联起来。

以下实例中，当按钮被点击时，data-bs-toggle="collapse" 属性触发了折叠菜单的行为，data-bs-target="#demo" 属性指定了折叠菜单的目标元素为 ID 为 demo 的 <div> 元素。


## 实例

```html
<button data-bs-toggle="collapse" data-bs-target="#demo">折叠</button>

<div id="demo" class="collapse">
这里是一些测试的内容。。。
</div>
```


### 实例解析

.collapse 类用于指定一个折叠元素 (实例中的 <div>); 点击按钮后会在隐藏与显示之间切换。

控制内容的隐藏与显示，需要在 <a> 或 <button> 元素上添加 data-bs-toggle="collapse" 属性。 data-target="#id" 属性是对应折叠的内容 (<div id="demo">)。

注意: <a> 元素上你可以使用 href 属性来代替 data-bs-target 属性:


## 实例

```html
<a href="#demo" data-bs-toggle="collapse">折叠</a>

<div id="demo" class="collapse">
这里是一些测试的内容。。。
</div>
```

默认情况下折叠的内容是隐藏的，你可以添加 .show 类让内容默认显示:


## 实例

```html
<div id="demo" class="collapse show">
这里是一些测试的内容。。。
</div>
```

以下实例通过扩展卡片组件来显示简单的手风琴。

注意: 使用 data-bs-parent 属性来确保所有的折叠元素在指定的父元素下，这样就能实现在一个折叠选项显示时其他选项就隐藏。


## 实例

```html
<div id="accordion">
    <div class="card">
        <div class="card-header">
            <a class="btn" data-bs-toggle="collapse" href="#collapseOne">
            选项一
            </a>
        </div>
        <div id="collapseOne" class="collapse show" data-bs-parent="#accordion">
            <div class="card-body">
            #1 内容：菜鸟教程 -- 学的不仅是技术，更是梦想！！！
            </div>
        </div>
    </div>
    <div class="card">
        <div class="card-header">
            <a class="collapsed btn" data-bs-toggle="collapse" href="#collapseTwo">
            选项二
        </a>
        </div>
         <div id="collapseTwo" class="collapse" data-bs-parent="#accordion">
            <div class="card-body">
            #2 内容：菜鸟教程 -- 学的不仅是技术，更是梦想！！！
            </div>
        </div>
    </div>
    <div class="card">
        <div class="card-header">
            <a class="collapsed btn" data-bs-toggle="collapse" href="#collapseThree">
            选项三
            </a>
        </div>
        <div id="collapseThree" class="collapse" data-bs-parent="#accordion">
            <div class="card-body">
            #3 内容：菜鸟教程 -- 学的不仅是技术，更是梦想！！！
            </div>
        </div>
    </div>
</div>
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Bootstrap5 折叠` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

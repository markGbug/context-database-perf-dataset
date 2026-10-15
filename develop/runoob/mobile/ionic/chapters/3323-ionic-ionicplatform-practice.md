# Ionic：ionic 平台

- 来源：[ionic 平台](https://www.runoob.com/ionic/ionic-ionicplatform.html)
- 分类：移动开发
- 技术：Ionic
- 笔记类型：练习笔记
- 章节序号：3323

## 本章内容

## $ionicPlatform

$ionicPlatform 用来检测当前的平台，以及诸如在PhoneGap/Cordova中覆盖Android后退按钮。


### 方法

```text
onHardwareBackButton(callback)
```

有硬件的后退按钮的平台，可以用这种方法绑定到它。

当该事件发生时，触发回调函数。

```text
offHardwareBackButton(callback)
```

移除后退按钮的监听事件。

最初绑定的监视器函数。

```text
registerBackButtonAction(callback, priority, [actionId])
```

注册硬件后退按钮动作。当点击按钮时，只有一个动作会执行，因此该方法决定了注册的后退按钮动作具有最高的优先级。

例如，如果一个上拉菜单已经显示，后退按钮应该关闭上拉菜单，而不是返回一个页面视图或关闭一个打开的模型。

当点击返回按钮时触发，如果该监视器具有最高的优先级。

仅最高优先级的会执行。

该id指定这个动作。默认：一个随机且唯一的id。

返回值: 函数， 一个被触发的函数，将会注销 backButtonAction。

```text
ready([callback])
```

设备准备就绪，则触发一个回调函数。

触发的函数。

返回: promise对象, 对象被构造 成功后得到解析。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `ionic 平台` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

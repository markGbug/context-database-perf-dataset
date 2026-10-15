# JavaScript：JavaScript 静态方法

- 来源：[JavaScript 静态方法](https://www.runoob.com/js/js-class-static.html)
- 分类：前端开发
- 技术：JavaScript
- 笔记类型：学习笔记
- 章节序号：2804

## 本章内容

静态方法是使用 static 关键字修饰的方法，又叫类方法，属于类的，但不属于对象，在实例化对象之前可以通过 类名.方法名 调用静态方法。

静态方法不能在对象上调用，只能在类中调用。


## 实例

```javascript
class Runoob {
  constructor(name) {
    this.name = name;
  }
  static hello() {
    return "Hello!!";
  }
}

let noob = new Runoob("菜鸟教程");

// 可以在类中调用 'hello()' 方法
document.getElementById("demo").innerHTML = Runoob.hello();

// 不能通过实例化后的对象调用静态方法
// document.getElementById("demo").innerHTML = noob.hello();
// 以上代码会报错
```

实例对象调用静态方法会报错：

如果你想在对象 noob 中使用静态方法，可以作为一个参数传递给它：


## 实例

```javascript
class Runoob {
  constructor(name) {
    this.name = name;
  }
  static hello(x) {
    return "Hello " + x.name;
  }
}
let noob = new Runoob("菜鸟教程");
document.getElementById("demo").innerHTML = Runoob.hello(noob);
```


## 复习重点

- 能说明 `JavaScript 静态方法` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

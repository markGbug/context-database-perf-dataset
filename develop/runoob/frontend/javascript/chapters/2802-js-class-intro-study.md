# JavaScript：JavaScript 类(class)

- 来源：[JavaScript 类](https://www.runoob.com/js/js-class-intro.html)
- 分类：前端开发
- 技术：JavaScript
- 笔记类型：学习笔记
- 章节序号：2802

## 本章内容

类是用于创建对象的模板。

我们使用 class 关键字来创建一个类，类体在一对大括号 {} 中，我们可以在大括号 {} 中定义类成员的位置，如方法或构造函数。

每个类中包含了一个特殊的方法 constructor()，它是类的构造函数，这种方法用于创建和初始化一个由 class 创建的对象。

创建一个类的语法格式如下：

```text
class ClassName {
  constructor() { ... }
}
```

实例：


## 实例

```text
class Runoob {
  constructor(name, url) {
    this.name = name;
    this.url = url;
  }
}
```

以上实例创建了一个类，名为 "Runoob"。

类中初始化了两个属性： "name" 和 "url"。


## 浏览器支持

表格中的数字表示支持该属性的第一个浏览器版本号。


## 使用类

定义好类后，我们就可以使用 new 关键字来创建对象：


## 实例

```javascript
class Runoob {
  constructor(name, url) {
    this.name = name;
    this.url = url;
  }
}

let site = new Runoob("菜鸟教程",  "https://www.runoob.com");
```

创建对象时会自动调用构造函数方法 constructor()。


### 类表达式

类表达式是定义类的另一种方法。类表达式可以命名或不命名。命名类表达式的名称是该类体的局部名称。


## 实例

```javascript
// 未命名/匿名类
let Runoob = class {
  constructor(name, url) {
    this.name = name;
    this.url = url;
  }
};
console.log(Runoob.name);
// output: "Runoob"

// 命名类
let Runoob = class Runoob2 {
  constructor(name, url) {
    this.name = name;
    this.url = url;
  }
};
console.log(Runoob.name);
// 输出: "Runoob2"
```

构造方法

构造方法是一种特殊的方法：

- 构造方法名为 constructor()。
- 构造方法在创建新对象时会自动执行。
- 构造方法用于初始化对象属性。
- 如果不定义构造方法，JavaScript 会自动添加一个空的构造方法。


## 类的方法

我们使用关键字 class 创建一个类，可以添加一个 constructor() 方法，然后添加任意数量的方法。

```text
class ClassName {
  constructor() { ... }
  method_1() { ... }
  method_2() { ... }
  method_3() { ... }
}
```

以下实例我们创建一个 "age" 方法，用于返回网站年龄：


## 实例

```javascript
class Runoob {
  constructor(name, year) {
    this.name = name;
    this.year = year;
  }
  age() {
    let date = new Date();
    return date.getFullYear() - this.year;
  }
}

let runoob = new Runoob("菜鸟教程", 2018);
document.getElementById("demo").innerHTML =
"菜鸟教程 " + runoob.age() + " 岁了。";
```

我们还可以向类的方法发送参数：


## 实例

```javascript
class Runoob {
  constructor(name, year) {
    this.name = name;
    this.year = year;
  }
  age(x) {
    return x - this.year;
  }
}

let date = new Date();
let year = date.getFullYear();

let runoob = new Runoob("菜鸟教程", 2020);
document.getElementById("demo").innerHTML=
"菜鸟教程 " + runoob.age(year) + " 岁了。";
```


## 严格模式 "use strict"

类声明和类表达式的主体都执行在严格模式下。比如，构造函数，静态方法，原型方法，getter 和 setter 都在严格模式下执行。

如果你没有遵循严格模式，则会出现错误：


## 实例

```javascript
class Runoob {
  constructor(name, year) {
    this.name = name;
    this.year = year;
  }
  age() {
    // date = new Date();  // 错误
    let date = new Date(); // 正确
    return date.getFullYear() - this.year;
  }
}
```

下图实例使用类未声明的变量：

更多严格模式可以参考：JavaScript 严格模式(use strict)


## 参考


### 类方法


### 类关键字


## 复习重点

- 能说明 `JavaScript 类` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

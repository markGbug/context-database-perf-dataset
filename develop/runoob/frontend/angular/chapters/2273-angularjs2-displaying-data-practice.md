# Angular：Angular 2 数据显示

- 来源：[Angular 2 数据显示](https://www.runoob.com/angularjs2/angularjs2-displaying-data.html)
- 分类：前端开发
- 技术：Angular
- 笔记类型：练习笔记
- 章节序号：2273

## 本章内容

本章节我们将为大家介绍如何将数据显示到用户界面上，可以使用以下三种方式：

- 通过插值表达式显示组件的属性
- 通过 NgFor 显示数组型属性
- 通过 NgIf 实现按条件显示


## 通过插值表达式显示组件的属性

要显示组件的属性，插值是最简单的方式，格式为：{{属性名}}。

以下代码基于 Angular 2 TypeScript 环境配置 来创建，你可以在该章节上下载源码，并修改以下提到的几个文件。


## app/app.component.ts 文件：

```html
import { Component } from '@angular/core';
@Component({
  selector: 'my-app',
  template: `
    <h1>{{title}}</h1>
    <h2>我喜欢的网站: {{mySite}}</h2>
    `
})
export class AppComponent {
  title = '站点列表';
  mySite = '菜鸟教程';
}
```

Angular 会自动从组件中提取 title 和 mySite 属性的值，并显示在浏览器中，显示信息如下：

注意：模板是包在反引号 (`) 中的一个多行字符串，而不是单引号 (')。


## 使用 ngFor 显示数组属性

我们也可以循环输出多个站点，修改以下文件：


## app/app.component.ts 文件：

```html
import { Component } from '@angular/core';
@Component({
  selector: 'my-app',
  template: `
    <h1>{{title}}</h1>
    <h2>我喜欢的网站: {{mySite}}</h2>
    <p>网站列表:</p>
    <ul>
      <li *ngFor="let site of sites">
        {{ site }}
      </li>
    </ul>
    `
})

export class AppComponent {
  title = '站点列表';
  sites = ['菜鸟教程', 'Google', 'Taobao', 'Facebook'];
  mySite = this.sites[0];
}
```

代码中我们在模板使用 Angular 的 ngFor 指令来显示 sites 列表中的每一个条目，不要忘记 *ngFor 中的前导星号 (*) 。。

修改后，浏览器显示如下所示：

实例中 ngFor 循环了一个数组， 事实上 ngFor 可以迭代任何可迭代的对象。

接下来我们在 app 目录下创建 site.ts 的文件，代码如下：


## app/site.ts 文件：

```text
export class Site {
  constructor(
    public id: number,
    public name: string) { }
}
```

以上代码中定义了一个带有构造函数和两个属性： id 和 name 的类。

接着我们循环输出 Site 类的 name 属性：


## app/app.component.ts 文件：

```html
import { Component } from '@angular/core';
import { Site } from './site';

@Component({
  selector: 'my-app',
  template: `
    <h1>{{title}}</h1>
    <h2>我喜欢的网站: {{mySite.name}}</h2>
    <p>网站列表:</p>
    <ul>
      <li *ngFor="let site of sites">
        {{ site.name }}
      </li>
    </ul>
    `
})

export class AppComponent {
  title = '站点列表';
  sites = [
      new Site(1, '菜鸟教程'),
      new Site(2, 'Google'),
      new Site(3, 'Taobao'),
      new Site(4, 'Facebook')
      ];
  mySite = this.sites[0];
}
```

修改后，浏览器显示如下所示：


## 通过 NgIf 进行条件显示

我们可以使用 NgIf 来设置输出指定条件的数据。

以下实例中我们判断如果网站数 3 个以上，输出提示信息：修改以下 app.component.ts 文件，代码如下：


## app/app.component.ts 文件：

```html
import { Component } from '@angular/core';
import { Site } from './site';

@Component({
  selector: 'my-app',
  template: `
    <h1>{{title}}</h1>
    <h2>我喜欢的网站: {{mySite.name}}</h2>
    <p>网站列表:</p>
    <ul>
      <li *ngFor="let site of sites">
       {{ site.name }}
      </li>
    </ul>
    <p *ngIf="sites.length > 3">你有很多个喜欢的网站!</p>
    `
})

export class AppComponent {
  title = '站点列表';
  sites = [
      new Site(1, '菜鸟教程'),
      new Site(2, 'Google'),
      new Site(3, 'Taobao'),
      new Site(4, 'Facebook')
      ];
  mySite = this.sites[0];
}
```

修改后，浏览器显示如下所示，底部多了个提示信息：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Angular 2 数据显示` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

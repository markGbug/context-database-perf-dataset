# TypeScript：TypeScript Map 对象

- 来源：[TypeScript Map 对象](https://www.runoob.com/typescript/ts-map.html)
- 分类：前端开发
- 技术：TypeScript
- 笔记类型：练习笔记
- 章节序号：3142

## 本章内容

Map 对象保存键值对，并且能够记住键的原始插入顺序。

任何值(对象或者原始值) 都可以作为一个键或一个值。

Map 是 ES6 中引入的一种新的数据结构，可以参考 ES6 Map 与 Set。


## 创建 Map

TypeScript 使用 Map 类型和 new 关键字来创建 Map：

```javascript
let myMap = new Map();
```

初始化 Map，可以以数组的格式来传入键值对：

```javascript
let myMap = new Map([
        ["key1", "value1"],
        ["key2", "value2"]
    ]);
```

Map 相关的函数与属性：

- map.clear() – 移除 Map 对象的所有键/值对 。
- map.set() – 设置键值对，返回该 Map 对象。
- map.get() – 返回键对应的值，如果不存在，则返回 undefined。
- map.has() – 返回一个布尔值，用于判断 Map 中是否包含键对应的值。
- map.delete() – 删除 Map 中的元素，删除成功返回 true，失败返回 false。
- map.size – 返回 Map 对象键/值对的数量。
- map.keys() - 返回一个 Iterator 对象， 包含了 Map 对象中每个元素的键 。
- map.values() – 返回一个新的Iterator对象，包含了Map对象中每个元素的值 。
- map.entries() – 返回一个包含 Map 中所有键值对的迭代器 。


### 常用函数

set(key: K, value: V): this - 向 Map 中添加或更新键值对。

```text
map.set('key1', 'value1');
```

get(key: K): V | undefined - 根据键获取值，如果键不存在则返回 undefined。

```javascript
const value = map.get('key1');
```

has(key: K): boolean - 检查 Map 中是否存在指定的键。

```javascript
const exists = map.has('key1');
```

delete(key: K): boolean - 删除指定键的键值对，成功删除返回 true，否则返回 false。

```javascript
const removed = map.delete('key1');
```

clear(): void - 清空 Map 中的所有键值对。

```text
map.clear();
```

size: number - 返回 Map 中键值对的数量。

```javascript
const size = map.size;
```


### 迭代方法

```java
for (const key of map.keys()) {
  console.log(key);
}
```

values(): IterableIterator<V> - 返回一个包含 Map 中所有值的迭代器。

```java
for (const value of map.values()) {
  console.log(value);
}
```

entries(): IterableIterator<[K, V]> - 返回一个包含 Map 中所有键值对的迭代器，每个元素是一个 [key, value] 数组。

```java
for (const [key, value] of map.entries()) {
  console.log(key, value);
}
```

forEach(callbackfn: (value: V, key: K, map: Map<K, V>) => void, thisArg?: any): void - 对 Map 中的每个键值对执行一次提供的回调函数。

```javascript
map.forEach((value, key) => {
  console.log(key, value);
});
```


### 实例


## 实例


## 实例 - test.ts 文件

```javascript
let nameSiteMapping = new Map();

// 设置 Map 对象
nameSiteMapping.set("Google", 1);
nameSiteMapping.set("Runoob", 2);
nameSiteMapping.set("Taobao", 3);

// 获取键对应的值
console.log(nameSiteMapping.get("Runoob"));     // 2

// 判断 Map 中是否包含键对应的值
console.log(nameSiteMapping.has("Taobao"));       // true
console.log(nameSiteMapping.has("Zhihu"));        // false

// 返回 Map 对象键/值对的数量
console.log(nameSiteMapping.size);                // 3

// 删除 Runoob
console.log(nameSiteMapping.delete("Runoob"));    // true
console.log(nameSiteMapping);
// 移除 Map 对象的所有键/值对
nameSiteMapping.clear();             // 清除 Map
console.log(nameSiteMapping);
```

使用 es6 编译：

```text
tsc --target es6 test.ts
```

编译以上代码得到如下 JavaScript 代码：


## 实例 - test.js 文件

```javascript
let nameSiteMapping = new Map();
// 设置 Map 对象
nameSiteMapping.set("Google", 1);
nameSiteMapping.set("Runoob", 2);
nameSiteMapping.set("Taobao", 3);
// 获取键对应的值
console.log(nameSiteMapping.get("Runoob")); //40
// 判断 Map 中是否包含键对应的值
console.log(nameSiteMapping.has("Taobao")); //true
console.log(nameSiteMapping.has("Zhihu")); //false
// 返回 Map 对象键/值对的数量
console.log(nameSiteMapping.size); //3
// 删除 Runoob
console.log(nameSiteMapping.delete("Runoob")); // true
console.log(nameSiteMapping);
// 移除 Map 对象的所有键/值对
nameSiteMapping.clear(); //清除 Map
console.log(nameSiteMapping);
```

执行以上 JavaScript 代码，输出结果为：

```text
2
true
false
3
true
Map { 'Google' => 1, 'Taobao' => 3 }
Map {}
```


### 迭代 Map

Map 对象中的元素是按顺序插入的，我们可以迭代 Map 对象，每一次迭代返回 [key, value] 数组。

TypeScript使用 for...of 来实现迭代：


## 实例 -test.ts 文件

```java
let nameSiteMapping = new Map();

nameSiteMapping.set("Google", 1);
nameSiteMapping.set("Runoob", 2);
nameSiteMapping.set("Taobao", 3);

// 迭代 Map 中的 key
for (let key of nameSiteMapping.keys()) {
    console.log(key);
}

// 迭代 Map 中的 value
for (let value of nameSiteMapping.values()) {
    console.log(value);
}

// 迭代 Map 中的 key => value
for (let entry of nameSiteMapping.entries()) {
    console.log(entry[0], entry[1]);
}

// 使用对象解析
for (let [key, value] of nameSiteMapping) {
    console.log(key, value);
}
```

使用 es6 编译：

```text
tsc --target es6 test.ts
```

编译以上代码得到如下 JavaScript 代码：


## 实例

```java
let nameSiteMapping = new Map();
nameSiteMapping.set("Google", 1);
nameSiteMapping.set("Runoob", 2);
nameSiteMapping.set("Taobao", 3);
// 迭代 Map 中的 key
for (let key of nameSiteMapping.keys()) {
    console.log(key);
}
// 迭代 Map 中的 value
for (let value of nameSiteMapping.values()) {
    console.log(value);
}
// 迭代 Map 中的 key => value
for (let entry of nameSiteMapping.entries()) {
    console.log(entry[0], entry[1]);
}
// 使用对象解析
for (let [key, value] of nameSiteMapping) {
    console.log(key, value);
}
```

执行以上 JavaScript 代码，输出结果为：

```text
Google
Runoob
Taobao
1
2
3
Google 1
Runoob 2
Taobao 3
Google 1
Runoob 2
Taobao 3
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `TypeScript Map 对象` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

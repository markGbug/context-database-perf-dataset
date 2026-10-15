# HTML5：HTML5 Web IndexedDB 数据库

- 来源：[HTML5 Web IndexedDB](https://www.runoob.com/html/html5-web-api-indexeddb.html)
- 分类：前端开发
- 技术：HTML5
- 笔记类型：练习笔记
- 章节序号：2723

## 本章内容

IndexedDB 是一种基于浏览器的 NoSQL 数据库，用于在客户端持久化存储大量结构化数据。

IndexedDB 允许通过键值对存储复杂的数据对象（如对象、数组、文件等），并支持事务、索引、版本控制和复杂查询操作。

IndexedDB 是异步的，不会阻塞主线程，适合离线应用程序、缓存等场景。

IndexedDB 非常适合需要存储大量结构化数据的应用程序，尤其是那些希望支持离线模式或处理复杂查询的 Web 应用。


### IndexedDB 特性

- 键值对存储：数据以键值对的形式存储在对象存储（object store）中。
- 事务支持：所有数据操作必须在事务内完成，以确保数据一致性和完整性。
- 异步 API：所有操作都是异步的，不会阻塞 UI 线程，使用事件回调或 Promises 来处理结果。
- 版本控制：数据库使用版本号来管理数据库的架构（如创建或修改对象存储）。
- 索引：支持对数据的字段建立索引，以加快查询速度。
- 离线支持：数据可以持久化存储并在断网情况下继续访问，非常适合构建离线 Web 应用。


### IndexedDB 语法

IndexedDB 语法说明如下：


### IndexedDB 方法

1、indexedDB.open()：用于打开现有数据库或创建新数据库。

```javascript
var request = indexedDB.open('databaseName', version);
```

2、db.createObjectStore()：在 onupgradeneeded 事件中创建对象存储（类似表）。

```javascript
var objectStore = db.createObjectStore('storeName', { keyPath: 'id' });
```

3、objectStore.add()：在事务中向对象存储中添加数据。

```text
objectStore.add({ id: 1, name: 'John Doe' });
```

3、objectStore.get()：根据键值从对象存储中获取数据。

```javascript
var request = objectStore.get(1);
```

4、objectStore.put()：更新现有记录，若记录不存在则插入。

```text
objectStore.put({ id: 1, name: 'John Updated' });
```

5、objectStore.delete()：根据键值删除记录。

```text
objectStore.delete(1);
```

6、db.transaction()：创建事务，指定对象存储名称和事务模式（readonly 或 readwrite）。

```javascript
var transaction = db.transaction(['storeName'], 'readwrite');
```

7、objectStore.createIndex()：为对象存储中的字段创建索引，以便更快的查询。

```text
objectStore.createIndex('nameIndex', 'name', { unique: false });
```


## IndexedDB 应用实例

以下是一个完整的 IndexedDB 实例，用于创建数据库、插入数据、查询数据并更新数据。


## 实例


## IndexedDB 使用场景

- 离线存储：IndexedDB 允许你存储数据以便在没有网络连接时访问，这对于离线 Web 应用至关重要。
- 缓存：可以用于存储大量缓存数据（如文件、图片、视频），提升应用的加载速度。
- 复杂数据处理：适用于需要存储和处理大量结构化数据的场景，尤其是需要索引和查询功能。
- 本地数据库：IndexedDB 可以作为前端应用的本地数据库，存储用户数据、配置信息、应用状态等。


## IndexedDB 的优势

- 大容量存储：支持更大数据存储（常常可以达到几百 MB 或更多），比 localStorage 的 5MB 限制大得多。
- 丰富的数据操作：支持事务、索引、查询、批量处理等复杂操作。
- 离线支持：数据保存在用户设备上，可以离线访问并同步到服务器。


## IndexedDB 的劣势

- API 复杂：相比 localStorage 等简单的客户端存储，IndexedDB API 相对复杂，需要更多的代码。
- 异步处理：操作异步执行，初学者可能会不习惯处理回调或 Promise。
- IndexedDB 非常适合需要存储大量结构化数据的应用程序，尤其是那些希望支持离线模式或处理复杂查询的 Web 应用。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `HTML5 Web IndexedDB` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

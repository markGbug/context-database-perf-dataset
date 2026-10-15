# Google 地图：Google 地图事件

- 来源：[Google 地图事件](https://www.runoob.com/googleapi/google-maps-events.html)
- 分类：前端开发
- 技术：Google 地图
- 笔记类型：练习笔记
- 章节序号：2566

## 本章内容

点击标记缩放地图 - 绑定在google地图上的事件。


## 点击标记缩放地图

我们仍然使用上一遍文章使用的英国伦敦的地图。

点用户点击标记时实现缩放地图的功能(点击标记时绑定地图缩放事件)。

代码如下：


## 实例

```text
// Zoom to 9 when clicking on marker
google.maps.event.addListener(marker,'click',function() {
  map.setZoom(9);
  map.setCenter(marker.getPosition());
});
```

使用 addListener() 事件处理程序来注册事件的监听。该方法使用一个对象，一个事件来监听，当指定的事件发生时 函数将被调用。


## 重置标记

我们通过给地图添加事件处理程序来改变 'center' 属性，以下代码使用 center_changed 事件在3秒后标记移会中心点:


## 实例

```text
google.maps.event.addListener(map,'center_changed',function() {
  window.setTimeout(function() {
    map.panTo(marker.getPosition());
  },3000);
});
```


## 点击标记时打开信息窗口。

点击标记在信息窗口显示一些文本信息：


## 实例

```javascript
var infowindow = new google.maps.InfoWindow({
  content:"Hello World!"
});

google.maps.event.addListener(marker, 'click', function() {
  infowindow.open(map,marker);
});
```


## 设置标记及打开每个标记的信息窗口

当用户点击地图时执行一个窗口

用户点击地图某个位置时使用 placeMarker() 函数在指定位置上放置一个标记，并弹出信息窗口：


## 实例

```html
google.maps.event.addListener(map, 'click', function(event) {
  placeMarker(event.latLng);
});

function placeMarker(location) {
  var marker = new google.maps.Marker({
    position: location,
    map: map,
  });
  var infowindow = new google.maps.InfoWindow({
    content: 'Latitude: ' + location.lat() +
    '<br>Longitude: ' + location.lng()
  });
  infowindow.open(map,marker);
}
```


## Google 地图 - 事件参考手册

Google Maps API 参考手册。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Google 地图事件` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。

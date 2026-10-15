# Vue.js：Vue.js Ajax(vue-resource)

- 来源：[Vue.js Ajax(vue-resource)](https://www.runoob.com/vue2/vuejs-ajax.html)
- 分类：前端开发
- 技术：Vue.js
- 笔记类型：学习笔记
- 章节序号：3266

## 本章内容

Vue 要实现异步加载需要使用到 vue-resource 库。

Vue.js 2.0 版本推荐使用 axios 来完成 ajax 请求。

```html
<script src="https://cdn.staticfile.org/vue-resource/1.5.1/vue-resource.min.js"></script>
```


### Get 请求

以下是一个简单的 Get 请求实例，请求地址是一个简单的 txt 文本：


## 实例

```javascript
window.onload = function(){
    var vm = new Vue({
        el:'#box',
        data:{
            msg:'Hello World!',
        },
        methods:{
            get:function(){
                //发送get请求
                this.$http.get('/try/ajax/ajax_info.txt').then(function(res){
                    document.write(res.body);
                },function(){
                    console.log('请求失败处理');
                });
            }
        }
    });
}
```

如果需要传递数据，可以使用 this.$http.get('get.php',{params : jsonData}) 格式，第二个参数 jsonData 就是传到后端的数据。

```javascript
this.$http.get('get.php',{params : {a:1,b:2}}).then(function(res){
    document.write(res.body);
},function(res){
    console.log(res.status);
});
```


### post 请求

post 发送数据到后端，需要第三个参数 {emulateJSON:true}。

emulateJSON 的作用： 如果Web服务器无法处理编码为 application/json 的请求，你可以启用 emulateJSON 选项。


## 实例

```javascript
window.onload = function(){
    var vm = new Vue({
        el:'#box',
        data:{
            msg:'Hello World!',
        },
        methods:{
            post:function(){
                //发送 post 请求
                this.$http.post('/try/ajax/demo_test_post.php',{name:"菜鸟教程",url:"http://www.runoob.com"},{emulateJSON:true}).then(function(res){
                    document.write(res.body);
                },function(res){
                    console.log(res.status);
                });
            }
        }
    });
}
```

demo_test_post.php 代码如下：

```text
<?php
$name = isset($_POST['name']) ? htmlspecialchars($_POST['name']) : '';
$city = isset($_POST['url']) ? htmlspecialchars($_POST['url']) : '';
echo '网站名: ' . $name;
echo "\n";
echo 'URL 地址: ' .$city;
?>
```


### 语法 & API

你可以使用全局对象方式 Vue.http 或者在一个 Vue 实例的内部使用 this.$http来发起 HTTP 请求。

```text
// 基于全局Vue对象使用http
Vue.http.get('/someUrl', [options]).then(successCallback, errorCallback);
Vue.http.post('/someUrl', [body], [options]).then(successCallback, errorCallback);

// 在一个Vue实例内使用$http
this.$http.get('/someUrl', [options]).then(successCallback, errorCallback);
this.$http.post('/someUrl', [body], [options]).then(successCallback, errorCallback);
```

```text
get(url, [options])
head(url, [options])
delete(url, [options])
jsonp(url, [options])
post(url, [body], [options])
put(url, [body], [options])
patch(url, [body], [options])
```

除了 jsonp 以外，另外 6 种的 API 名称是标准的 HTTP 方法。

options 参数说明:

通过如下属性和方法处理一个请求获取到的响应对象：


## 复习重点

- 能说明 `Vue.js Ajax(vue-resource)` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

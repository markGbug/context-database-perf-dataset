# 知识点 56240：Vue.js：Vue.js 实例 - 订单列表

- 来源：[Vue.js 实例](https://www.runoob.com/vue2/vue-examples.html)
- 来源章节：[3268-vue-examples-study.md](../chapters/3268-vue-examples-study.md)
- 分类：前端开发
- 技术：Vue.js
- 所在小节：订单列表
- 知识类型：代码
- 原章节序号：3268

## 原文片段

```text
<form id="main" v-cloak>

    <h1>Services</h1>

    <ul>

        <!-- 循环输出 services 数组, 设置选项点击后的样式 -->

        <li v-for="service in services" v-on:click="toggleActive(service)" v-bind:class="{ 'active': service.active}">

            <!-- 显示订单中的服务名，价格
                 Vue.js 定义了货币过滤器，用于格式化价格 -->

            {{service.name}} <span>{{service.price | currency}}</span>

        </li>
    </ul>

    <div class="total">

        <!-- 计算所有服务的价格，并格式化货币 -->

        Total: <span>{{total() | currency}}</span>

    </div>

</form>
<script>

// 自定义过滤器 "currency"
Vue.filter('currency', function (value) {
    return '$' + value.toFixed(2);
});

var demo = new Vue({
    el: '#main',
    data: {
        // 定义模型属性
        // 视图将循环输出数组的数据
        services: [
            {
                name: 'Web Development',
                price: 300,
                active:true
            },{
                name: 'Design',
                price: 400,
                active:false
            },{
                name: 'Integration',
                price: 250,
                active:false
            },{
                name: 'Training',
                price: 220,
                active:false
            }
        ]
    },
    methods: {
        toggleActive: function(s){
            s.active = !s.active;
        },
        total: function(){

            var total = 0;

            this.services.forEach(function(s){
                if (s.active){
                    total+= s.price;
                }
            });

           return total;
        }
    }
});

</script>
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `订单列表` 这一小节和 `Vue.js 实例` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？

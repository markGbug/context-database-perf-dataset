# Django：Django Form 组件

- 来源：[Django Form 组件](https://www.runoob.com/django/django-form-component.html)
- 分类：Python / 数据科学
- 技术：Django
- 笔记类型：学习笔记
- 章节序号：3820

## 本章内容

Django Form 组件用于对页面进行初始化，生成 HTML 标签，此外还可以对用户提交的数据进行校验（显示错误信息）。

报错信息显示顺序：

- 先显示字段属性中的错误信息，然后再显示局部钩子的错误信息。
- 若显示了字段属性的错误信息，就不会显示局部钩子的错误信息。
- 若有全局钩子，则全局钩子是等所有的数据都校验完，才开始进行校验，并且全局钩子的错误信息一定会显示。

使用 Form 组件，需要先导入 forms：

```text
from django import forms
```

接下来我们在 app01 目录下创建一个 My_forms.py:


## app01/My_forms.py

字段属性：

- label：输入框前面的文本信息。
- error_message：自定义显示的错误信息，属性值是字典， 其中 required 为设置不能为空时显示的错误信息的 key。


## app01/views.py

app01/urls.py 文件添加以下规则：

```text
path('add_emp/', views.add_emp)
```

HTML 模版：


## app01/add_emp.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title></title>
</head>
<body>

<h3>添加员工</h3>

{#1、自己手动写HTML页面#}
<form action="" method="post">
    <p>姓名：<input type="text" name="name"></p>
    <p>年龄：<input type="text" name="age"></p>
    <p>工资：<input type="text" name="salary"></p>
    <input type="submit">
</form>

{#2、通过form对象的as_p方法实现#}
{#<form action="" method="post" novalidate>#}
{#    {% csrf_token %}#}
{#    {{ form.as_p }}#}
{#    <input type="submit">#}
{#</form>#}

{#3、手动获取form对象的字段#}
{#<form action="" method="post" novalidate>#}
{#    {% csrf_token %}#}
{#    <div>#}
{#        <label for="id_{{ form.name.name }}">姓名</label>#}
{#        {{ form.name }} <span>{{ form.name.errors.0 }}</span>#}
{#    </div>#}
{#    <div>#}
{#        <label for="id_{{ form.age.name }}">年龄</label>#}
{#        {{ form.age }} <span>{{ form.age.errors.0 }}</span>#}
{#    </div>#}
{#    <div>#}
{#        <label for="id_salary">工资</label>#}
{#        {{ form.salary }} <span>{{ form.salary.errors.0 }}</span>#}
{#    </div>#}
{#    <input type="submit">#}
{#</form>#}


{#4、用for循环展示所有字段#}
{#<form action="" method="post" novalidate>#}
{#    {% csrf_token %}#}
{#    {% for field in form %}#}
{#        <div>#}
{#            <label for="id_{{ field.name }}">{{ field.label }}</label>#}
{#            {{ field }} <span>{{ field.errors.0 }}</span>#}
{#        </div>#}
{#    {% endfor %}#}
{#    <input type="submit">#}
{#</form>#}

</body>
</html>
```

运行结果如下图所示：


### 局部钩子和全局钩子

定义 Form 类:


## app01/My_forms.py

views.py 文件代码：


## app01/views.py

模板文件代码如下：


## app01/add_emp.html

```html
<form action="" method="post" novalidate>
    {% csrf_token %}
    <div>
        <label for="id_{{ form.name.name }}">姓名</label>
        {{ form.name }} <span>{{ form.name.errors.0 }}</span>
    </div>
    <div>
        <label for="id_{{ form.age.name }}">年龄</label>
        {{ form.age }} <span>{{ form.age.errors.0 }}</span>
    </div>
    <div>
        <label for="id_salary">工资</label>
        {{ form.salary }} <span>{{ form.salary.errors.0 }}{{ clear_errors.0 }}</span>
    </div>
    <div>
        <label for="id_r_salary">请再输入工资</label>
        {{ form.r_salary }} <span>{{ form.r_salary.errors.0 }}{{ clear_errors.0 }}</span>
    </div>
    <input type="submit">
</form>
```

运行结果如下图所示：


## 复习重点

- 能说明 `Django Form 组件` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。

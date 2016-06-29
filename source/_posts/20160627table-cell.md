---
title: diaplay:table-cell使用小结
date: 2016-06-27 10:39:22
tags:
- css
---

table-cell是display家族中的小小一员，传统布局中几剩乎是忽略它的存在。因为IE8以下是不兼容的，没错就是那个万恶的IE6和IE7。随着时间的推进，很多用户都已放弃的IE6/IE7的使用了，使table-cell沉默至今终于可以大展拳脚了。

display:table-cell其实就是让标签元素以表格单元格的形式呈现，类似于td标签。

相比于flex功能没这么强大，但相对于简单容易理解和使用，代码简略不用添加一些内核前缀，移动端主流还是flex

#### 元素自动平分填满一行

先看看实现效果图：

![](/images/cell-01.jpg)

第一眼看，你可能是想着这个用float轻松实现，单格大小就是100/个数的百分比就可以。但这样单元格的数量发生变化时，你就要重新计算了，用float还要处理清除浮动一些手尾。现在用table-cell轻松无痛实现。

<!-- more -->

html代码:

```html
<div class="container">
    <ul>
        <li>1</li>
        <li>2</li>
        <li>3</li>
        <li>4</li>
        <li>5</li>
        <li>6</li>
    </ul>
</div>
```

```css
.container {
    border: 1px solid orange;
    display: table;
    padding: 10px;
}
.container ul {
    margin: 0;
    padding: 0;
    border-right: 1px solid #ccc;
}
.container ul li {
    list-style: none;
    display: table-cell;
    height: 100px;
    vertical-align: middle;
    text-align: center;
    width: 2000px;
    border: 1px solid #ccc;
    border-right: none;
}
```
注：`width:2000px`只是任意设定的大小值，实际输出是没这么大的，只是为了让元素有宽度

[查看效果](http://codepen.io/ch563/pen/rLjRQa)

----

#### 垂直居中

垂直居中，这是一个长久的话题。css3的出现，现在有各种各样的方法可实轻松实现。现在我主要介绍一下table-cell的实现方法

![](/images/cell-02.jpg)

```html
<div class="container">
    <div>
        <p>学习前端就是要带着要填坑的思想准备</p>
        <p>任何事情都不是一帆风顺的！</p>
    </div>
</div>
<div class="container">
    <div class="black"><img src="https://assets.codepen.io/assets/logos/codepen-logo-9c0933e8569e634b75ac2eb808da908d.svg"/></div>
</div>
```

```css
.container {
    width: 500px;
    margin: 0 auto 10px;
}
.container div {
    display: table-cell;
    vertical-align: middle;
    text-align: center;
    border: 1px solid #ccc;
    width: 2000px;
    height: 150px;
    margin-bottom: 10px;
}
.container div.black {
    background: #333;
    border: none;
}
.container div.black img {
    width: 200px;
}
.container p {
    font-size: 12px;
    line-height: 1.8;
    margin: 0;
}
```
[查看效果](http://codepen.io/ch563/pen/rLjbax)

----


#### 等高布局

即然是以表格的单元格呈现，那就有单元格的相对属性，等高、跟随其他栏的变化而变化

![](/images/cell-03.jpg)

```html
<div class="container">
    <div class="item">
        <p>第一栏</p>
    </div>
    <div class="middle">
        <p>第二栏<br>即然是以表格的单元格呈现，那就有单元格的相对属性，等高、跟随其他栏的变化而变化</p>
    </div>
    <div class="item">
        <p>第三栏</p>
    </div>
</div>
```

```css
.container {
    display: table;
    width: 500px;
    margin: 0 auto;
    padding: 10px 0;
}
.container .item {
    display: table-cell;
    width: 100px;
    background: #ccc;
}
.container .middle {
    margin: 0 10px;
    background: #aaa;
    padding: 0;
}
.container p {
    margin: 0;
    text-align: center;
    font-size: 12px;
    line-height: 1.8;
    padding: 10px;
}
```
注：如果都是`table-cell`的话，可以配合着`table-row`使用来实现

[查看效果](http://codepen.io/ch563/pen/QEdPVj)


----


#### 弹性/自适应布局

这种方式实现的自适应布局，元素宽度无需定值，支持百分比宽度，且可以无限制嵌套，兼容性良好。

![](/images/cell-04.jpg)

[查看效果](http://codepen.io/ch563/pen/gMgyJV)


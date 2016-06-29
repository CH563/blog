---
title: 每日一撸:className
date: 2016-06-23 18:06:45
category:
- study
---

### className

设置或返回元素的 class属性

```javascript
HTMLElementObject.className=classname
```

常用指定的class属性。也可以是添加class属性，不替换原有的class

```javascript
HTMLElementObject.className+=classname
```
<!-- more -->

还可以利用前面学习的getAttribute()方法来改变classname

```javascript
HTMLElementObject.setAttribute('class','classname')
```

- classname检测、添加、删除的方法使用

```javascript
//检测
function hasClass(element, className) {
    var reg = new RegExp('(\\s|^)'+className+'(\\s|$)');
    return element.className.match(reg);
}
//添加
function addClass(element, className) {
    if (!this.hasClass(element, className))
    {
        element.className += " "+className;
    }
}
//删除
function removeClass(element, className) {
    if (hasClass(element, className)) {
        var reg = new RegExp('(\\s|^)'+className+'(\\s|$)');
        element.className = element.className.replace(reg,' ');
    }
}
```


className的操作，有很多各种精妙的方法，学习JQ的`addClass` `removeClass`的封装方法而加强深入了解

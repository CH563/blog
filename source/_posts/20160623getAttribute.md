---
title: 每日一撸:attribute 所有使用方法
date: 2016-06-22 16:53:58
category:
- study
---

- `attributes` 获取一个属性作为对象
- `getAttribute` 获取某一个属性的值
- `setAttribute` 建立一个属性，并同时给属性捆绑一个值
- `createAttribute` 仅建立一个属性
- `removeAttribute` 删除一个属性
- `getAttributeNode` 获取一个节点作为对象
- `setAttributeNode` 建立一个节点
- `removeAttributeNode` 删除一个节点
- `attributes` 可以获取一个对象中的一个属性，并且作为对象来调用，注意在这里要使用“[]”，IE在这里可以使用“()”，考虑到兼容性的问题，要使用“[]”。

<!-- more -->
----

### attributes

回指定节点的属性集合，即 NamedNodeMap。
- 提示：您可以使用 length 属性来确定属性的数量，然后您就能够遍历所有的属性节点并提取您需要的信息。

```html
<div id="demo"><input type="hidden" id="sss" value="aaa"></div>
```
```javascript
var d=document.getElementById("sss").attributes["value"];
document.write(d.name);
document.write(d.value);
//显示value aaa
```

----

#### 注意这几点：

1、createAttribute在使用的时候不需要基于对象的，document.createAttribute()就可以。

2、setAttribute，createAttribute在使用的时候如果是使用的时候不要使用name，type，value等单词，IE都FF的反应都奇怪的难以理解。

3、createAttribute在使用的时候如果只定义了名字，没有d.nodeValue="hello";语句定义值，FF会认为是一个空字符串，IE认为是undefined，注意到这点就可以了。

----

### getAttribute

返回指定属性名的属性值

```html
<div id="demo"><input type="hidden" id="sss" value="aaa"></div>
```
```javascript
var d=document.getElementById("sss").getAttribute("value");
document.write(d);
//显示 aaa
```

### setAttribute

添加指定的属性，并为其赋指定的值。如果这个指定的属性已存在，则仅设置/更改值。

```html
<div id="demo"><input type="hidden" id="sss" value="aaa"></div>
```
```javascript
var d=document.getElementById("sss").setAttribute("good","hello");
alert(document.getElementById("demo").innerHTML)
//多了一个名为good的属性hello
```

### createAttribute

```html
<div id ="demo"><input type="hidden" id="sss" value="aaa"></div>
```
```javascript
var d=document.createAttribute("good");
document.getElementById("sss").setAttributeNode(d);
alert(document.getElementById("demo").innerHTML)
//多了一个名为good的空属性
```


### removeAttribute

删除指定的属性。

```html
<div id="demo"><input type="hidden" id="sss" value="aaa"></div>
```
```javascript
var d=document.getElementById("sss").removeAttribute("value");
alert(document.getElementById("demo").innerHTML)
//少了一个
```

----


<div class="tip">getAttributeNode，setAttributeNode，removeAttributeNode三个方法的特点是都直接操作一个node（节点），removeAttributeNode在一开始的时候总会用错，但是充分理解了node的含义的时候，就能够应用自如了。
</div>


### getAttributeNode

```html
<div id="demo"><input type="hidden" id="sss" value="aaa"></div>
```
```javascript
var d=document.getElementById("sss").getAttributeNode("value");
document.write(d.name);
document.write(d.value);
//显示 value aaa
```

### setAttributeNode

```html
<div id="demo"><input type="hidden" id="sss" value="aaa"></div>
```
```javascript
var d=document.createAttribute("good");
document.getElementById("sss").setAttributeNode(d);
alert(document.getElementById("demo").innerHTML);
```

### removeAttributeNode

```html
<div id="demo"><input type="hidden" id="sss" value="aaa"></div>
```
```javascript
var d=document.getElementById("sss").getAttributeNode("value")
document.getElementById("sss").removeAttributeNode(d); 
alert(document.getElementById("demo").innerHTML);
```

----

学习了Attribute的几个属性，感觉对DOM的操作又撑控的多一些了，需要再接再励!

bug提示:

```javascript
    getAttribute('name') //IE6、7中会得到错误的值
    getAttributeNode('name').nodeValue  //兼容所有
```
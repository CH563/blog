---
title: 移动web开发开始
date: 2016-06-15 15:37:14
---

### meta写法：

```html
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1">
```
width属性控制视口的宽度。可以像width=600这样设为确切的像素数，或者设为device-width这一特殊值来指代比例为100%时屏幕宽度的CSS像素数值。（相应有height及device-height属性，可能对包含基于视口高度调整大小及位置的元素的页面有用。）

initial-scale属性控制页面最初加载时的缩放等级。maximum-scale、minimum-scale及user-scalable属性控制允许用户以怎样的方式放大或缩小页面。


```html
<meta name="apple-mobile-web-app-capable" content="yes">
```
这个meta的作用是让普通移动网页被添加到主屏幕后，拥有一些类native的功能，很多同学应该都很熟悉了。就是类似隐藏ios的上下状态栏，实现全屏，禁止弹性拖拽，全屏，修改顶部颜色等。


<!-- more -->


```html
<link rel="apple-touch-startup-image" href="/img/startup.png" />
```
这个属性是当用户把连接保存到手机桌面时使用的图标，如果不设置，则会用网页的截图。有了这，就可以让你的网页像APP一样存在手机里了


```html
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent" />
```
这个是APP启动画面图片，用途和上面的类似，如果不设置，启动画面就是白屏，图片像素就是手机全屏的像素


```html
<meta name="apple-touch-fullscreen" content="yes" />
<meta name="apple-mobile-web-app-capable" content="yes" />
```
这个描述是表示打开的web app的最上面的时间、信号栏是黑色的，当然也可以设置其它参数，详细参数说明请参照：Safari HTML Reference - Supported Meta Tags


### input type date的placeholder支持性

#### 桌面端：

Safari不支持datepicker，placeholder正常显示；
Firefox不支持datepicker，placeholder正常显示；
Chrome支持datepicker，显示年、月、日格式，忽略placeholder.

#### 移动端

iPhone5 IOS7 有datephicker功能，但不显示placeholder.
Andorid4.04无datepicker功能，不显示placeholder。

#### 解决方法：

先使其type为text，此时支持placeholder，当触摸或者聚焦的时候，使用JS切换使其触发datepicker功能。

```html
<input type="text" placeholder="Date" onfocus="(this.type='date')" >
```


#### 快速回弹滚动

IOS让一个元素拥有像Native的滚动效果：

```css
{
     overflow: auto; /* auto | scroll */
     -webkit-overflow-scrolling: touch;
}
```

Android考虑借助 iScrooll .
移动端取消touch高亮效果
a标签在触发点击时或者所有设置了伪类 :active 的元素，默认都会在激活状态，显示高亮，css禁止：


```css
｛
     -webkit-tap-highlight-color: rgba(0,0,0,0);
｝
```
*三星自带浏览器，点击A时，无法覆盖，还是会有阴影底色，只能换其他不使用A跳转。

禁止复制图像
通常长按图像img会弹出选项存储图像或拷贝图片，禁止方法：

```css
img{
     -webkit-touch-callout: none;
}
```

1.掌握原生属性的特性；
2.很多属性极限突破可以使用缩放，倾斜这种手段来hack，比如最小字体，比如各种自已画的伪类图；
3.能css画的不要用图；
4.大小需要自适应的图标做成字体的不要画：iconfont；
5.能flex布局的不要用浮动，不要用绝对定位（不利于页面布局的扩展）


锁定 viewport

```css
ontouchmove="event.preventDefault()" //锁定viewport，任何屏幕操作不移动用户界面（弹出键盘除外）。
```

模拟:hover伪类

因为iPhone并没有鼠标指针，所以没有hover事件。那么CSS :hover伪类就没用了。但是iPhone有Touch事件，onTouchStart 类似 onMouseOver，onTouchEnd 类似 onMouseOut。所以我们可以用它来模拟hover。使用Javascript：

```javascript

var myLinks = document.getElementsByTagName('a');
for(var i = 0; i < myLinks.length; i++){
  myLinks[i].addEventListener(’touchstart’, function(){this.className = “hover”;}, false);
  myLinks[i].addEventListener(’touchend’, function(){this.className = “”;}, false);
}
```

然后用CSS增加hover效果：

```css
a:hover, a.hover { /* 你的hover效果 */ }
```

这样设计一个链接，感觉可以更像按钮。并且，这个模拟可以用在任何元素上。


看看知乎大神的回答 [移动开发的区别](https://www.zhihu.com/question/20269059)
![](/images/6667e51ace0d1246f0b5f9b9cf5512b4_b.jpg)
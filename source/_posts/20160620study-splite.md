---
title: 每日一撸:splite() | replace() | match() 方法
date: 2016-06-20 15:00:39
category:
- study
---

### split()

用于把一个字符串分割成字符串数组。
数组切割的常用方法。

语法

```javascript
stringObject.split(separator,howmany)
```

separator:必需。字符串或正则表达式，从该参数指定的地方分割 stringObject。
howmany:可选。该参数可指定返回的数组的最大长度。如果设置了该参数，返回的子串不会多于这个参数指定的数组。如果没有设置该参数，整个字符串都会被分割，不考虑它的长度。

<!-- more -->

#### 定义和用法

split() 方法用于把一个字符串分割成字符串数组。
数组切割的常用方法。

语法

```javascript
stringObject.split(separator,howmany)
```

- separator:必需。字符串或正则表达式，从该参数指定的地方分割 stringObject。
- howmany:可选。该参数可指定返回的数组的最大长度。如果设置了该参数，返回的子串不会多于这个参数指定的数组。如果没有设置该参数，整个字符串都会被分割，不考虑它的长度。

使用方法：

```javascript
var str="How are you doing today?"
document.write(str.split(" ") + "<br />")
document.write(str.split("") + "<br />")
document.write(str.split(" ",3))
```

输出:

How,are,you,doing,today?
H,o,w, ,a,r,e, ,y,o,u, ,d,o,i,n,g, ,t,o,d,a,y,?
How,are,you

-----


### replace()

用于在字符串中用一些字符替换另一些字符，或替换一个与正则表达式匹配的子串。
用于替换字符，很好用，可以处理一些意想不到的效果.

```javascript
stringObject.replace(regexp/substr,replacement)
```

- regexp/substr:必需。规定子字符串或要替换的模式的 RegExp 对象。请注意，如果该值是一个字符串，则将它作为要检索的直接量文本模式，而不是首先被转换为 RegExp 对象。
- replacement:必需。一个字符串值。规定了替换文本或生成替换文本的函数。

*字符串 stringObject 的 replace() 方法执行的是查找并替换的操作。它将在 stringObject 中查找与 regexp 相匹配的子字符串，然后用 replacement 来替换这些子串。如果 regexp 具有全局标志 g，那么 replace() 方法将替换所有匹配的子串。否则，它只替换第一个匹配子串。


```javascript
var str="Visit Myblog!"
document.write(str.replace(/Visit/, "Welcome visit"))
```

输出：Welcome visit Myblog!


```javascript
name = "Doe, John";
document.write(name.replace(/(\w+)\s*, \s*(\w+)/, "$2 $1"));
```

输出：John Doe

-----


### match()

可在字符串内检索指定的值，或找到一个或多个正则表达式的匹配。

```javascript
stringObject.match(searchvalue)
stringObject.match(regexp)
```

```javascript
var str="Hello world!"
document.write(str.match("world") + "<br />")
document.write(str.match("World") + "<br />")
document.write(str.match("worlld") + "<br />")
document.write(str.match("world!"))
```

输出：
world
none
world!

```javascript
var str="1 plus 2 equal 3"
document.write(str.match(/\d+/g))
```

输出：1,2,3

-----

平时看别人代码，困难是因为用js的方法属性了解不够多，方法虽然比较多，但每天学几个，总会不学得完。
总比一味埋怨好，一些得付出行动。
从基本学起，一路进步，不要给看看不懂的代码给吓住...

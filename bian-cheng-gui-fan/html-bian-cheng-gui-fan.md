# HTML 编程规范

## 声明规范

### DOCTYPE 声明

HTML页面添加标准模式声明，确保在每一个浏览器中拥有一致的展示。**强制**

```HTML
<!-- bad -->
<html>
  ...
</html>

<!-- good -->
<!DOCTYPE html>
<html>
  ...
</html>
```

### 页面语言LANG

为html根元素指定lang属性，从而为页面设置正确的语言。**建议**

```HTML
<!-- bad -->
<html>
  ...
</html>

<!-- good -->
<html lang="zh-CN">
  ...
</html>
```

跟多地区语言参考：

```
zh-SG 中文 (简体, 新加坡)
zh-HK 中文 (繁体, 香港)
zh-MO 中文 (繁体, 澳门)
zh-TW 中文 (繁体, 台湾)
```

### 指定CHARSET字符编码

字符编码，设置声明字符编码meta。**强制**

```HTML
<!-- bad -->
<meta charset="utf-8">
<meta charset="utf8">
<meta charset="UTF8">

<!-- good -->
<meta charset="UTF-8">
```

### 指定IE兼容模式meta

IE兼容模式，设置IE兼容模式meta。

```HTML
<!-- good -->
<meta http-equiv="X-UA-Compatible" content="IE=Edge">
```

### 360浏览器极速模式

```
<meta name="renderer" content="webkit|ie-comp|ie-stand">
```

## 书写规范

### 使用双引号

对于属性的定义，确保全部使用双引号，不要使用单引号。**建议**

```HTML
<!-- bad -->
<img src='images/logo.png' alt='logo'>

<!-- good -->
<img src="images/logo.png" alt="log">
```

### 标签闭合

不要省略可选的结束标签（closing tag）（例如，`</li>`或`</body>`）。**强制**

```HTML
<!-- bad -->
<ul>
  <li>html编程规范，语法规范
  <li>html编程规范，语法规范
</ul>  

<!-- good -->
<ul>
  <li>html编程规范，语法规范</li>
  <li>html编程规范，语法规范</li>
</ul>
```

### 自闭合标签结尾不加斜线

自闭合的标签结尾结尾不要加斜线。**建议**

空元素：area、base、br、col、command、embed、hr、img、input、keygen、link、meta、param、source、track、wbr

```
<!-- bad -->
<img src="images/logo.png" alt="logo" />
<br />

<!-- good -->
<img src="images/logo.png" alt="logo">
<br>
```

### 类型属性

引入CSS和JavaScript文件，不需要指定type属性。**建议**

```HTML
<!-- bad -->
<link rel="stylesheet" type="text/css" href="code-guide.css">
<script type="text/javascript" src="index.js"></script>

<!-- good -->
<link rel="stylesheet" href="code-guide.css">
<script src="index.js"></script>
```

### **属性排列顺序优先级**

按照以下顺序排列属性顺序：

* `class`
* `id`,`name`
* `data-*`
* `src`,`for`,`type`,`href`,`value`
* `title`,`alt`
* `role`,`aria-*`

class 用于标识高度可复用组件，因此应该排在首位。id 用于标识具体组件，应当谨慎使用（例如，页面内的书签），因此排在第二位。**建议**

```HTML
<!-- good -->
<a class="..." id="..." data-toggle="modal" href="#">
  Example link
</a>

<input class="form-control" type="text">

<img src="..." alt="...">
```

### 布尔型属性

布尔型属性可以在声明时不赋值。XHTML 规范要求为其赋值，但是 HTML5 规范不需要。

更多信息请参考 [WhatWG section on boolean attributes](http://www.whatwg.org/specs/web-apps/current-work/multipage/common-microsyntaxes.html#boolean-attributes)：

> 元素的布尔型属性如果有值，就是 true，如果没有值，就是 false。

如果一定要为其赋值的话，请参考 WhatWG 规范：

> 如果属性存在，其值必须是空字符串或 \[...\] 属性的规范名称，并且不要在首尾添加空白符。

布尔型的属性，不赋值。**建议**

```HTML
<!-- bad -->
<input type="text" disabled="disabled">

<input type="checkbox" value="1" checked="checked">

<select>
  <option value="1" selected="selected">1</option>
</select>

<!-- good -->
<input type="text" disabled>

<input type="checkbox" value="1" checked>

<select>
  <option value="1" selected>1</option>
</select>
```

### **转义字符**

在 HTML 中不能使用小于号 “&lt;” 和大于号 “&gt;”特殊字符，浏览器会将它们作为标签解析，若要正确显示，在 HTML 源代码中使用字符实体。

```
<!-- bad -->
<a href="#">more&gt;&gt;</a>

<!-- good -->
<a href="#">more>></a>
```

## 原则

尽量减少标签的数量，但是也要注意在编写HTML时，结构与显示分离。**强制**

```HTML
<!-- bad -->
<span class="avatar">
  <img src="...">
</span>

<!-- good -->
<img class="avatar" src="avatar.png">

<div class="images-layout">
  <img class="avatar" src="avatar.png">
</div>
```

尽量避免用JavaScript生成HTML标签，因为JavaScript 生成的标签让内容变得不易查找、编辑，并且降低性能。

> 本HTML规范如有建议或补充，及时提出。




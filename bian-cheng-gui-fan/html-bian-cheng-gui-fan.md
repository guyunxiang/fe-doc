# HTML 编程规范

HTML页面添加标准模式声明，确保在每一个浏览器中拥有一致的展示。

```
// bad
<html>
  ...
</html>

// good
<!DOCTYPE html>
<html>
  ...
</html>
```

为html根元素指定lang属性，从而为页面设置正确的语言。

```
// bad
<html>
  ...
</html>

// good
<html lang="zh-cn">
  ...
</html>
```

字符编码，设置声明字符编码meta。

```
// good
<meta charset="UTF-8">
```

IE兼容模式，设置IE兼容模式meta。

```
// good
<meta http-equiv="X-UA-Compatible" content="IE=Edge">
```

对于属性的定义，确保全部使用双引号，绝不要使用单引号。

```
// bad
<img src='images/logo.png' alt='logo'>

// good
<img src="images/logo.png" alt="log">
```

不要省略可选的结束标签（closing tag）（例如，`</li>`或`</body>`）。

```
// bad
<ul>
  <li>html编程规范，语法规范
  <li>html编程规范，语法规范
</ul>  

// good
<ul>
  <li>html编程规范，语法规范</li>
  <li>html编程规范，语法规范</li>
</ul>
```

引入CSS和JavaScript文件，不需要指定type属性。

```
// good
<link rel="stylesheet" href="code-guide.css">

<style>
  ...
</style>

<src src="index.js"></script>
```

按照以下顺序排列属性顺序：

* `class`
* `id`,`name`
* `data-*`
* `src`,`for`,`type`,`href`,`value`
* `title`,`alt`
* `role`,`aria-*`

class 用于标识高度可复用组件，因此应该排在首位。id 用于标识具体组件，应当谨慎使用（例如，页面内的书签），因此排在第二位。

```
// good
<a class="..." id="..." data-toggle="modal" href="#">
  Example link
</a>

<input class="form-control" type="text">

<img src="..." alt="...">
```

布尔型属性不赋值

```
// bad
<input type="text" disabled="disabled">

<input type="checkbox" value="1" checked="checked">

<select>
  <option value="1" selected="selected">1</option>
</select>

// good
<input type="text" disabled>

<input type="checkbox" value="1" checked>

<select>
  <option value="1" selected>1</option>
</select>
```

---

尽量减少标签的数量，但是也要注意在编写HTML时，结构与显示分离。

```
// bad
<span class="avatar">
  <img src="...">
</span>

// good
<img class="avatar" src="avatar.png">

<div class="image-layout">
  <img class="avatar" src="avatar.png">
</div>
```

尽量避免用JavaScript生成HTML标签，因为JavaScript 生成的标签让内容变得不易查找、编辑，并且降低性能。

> 本HTML规范参照 [bootstrap编程规范](http://codeguide.bootcss.com/)，如有建议或补充，及时提出。




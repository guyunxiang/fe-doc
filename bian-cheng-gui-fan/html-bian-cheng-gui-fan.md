# HTML 编程规范

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
```




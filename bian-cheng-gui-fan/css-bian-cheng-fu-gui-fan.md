# CSS 编程规范

选择器分组，将单独的选择器单独放在一行。

```
// bad
.selector, .selector-secondary, .selector[type=text] {
  padding: 15px;
}

// good
.selector,
.selector-secondary,
.selector[type="text"] {
  padding: 15px;
}
```

每个声明的左花括号前添加一个空格。

```
// bad
.selector{ padding: 15px; }

// good
.selector { padding: 15px; }
```

多条样式声明块的右花括号应当单独成行。

```
// bad
.selector {
  margin: 15px;
  padding: 10px;}

// good
.selector {
  margin: 15px;
  padding: 15px;
}
```

所有声明语句都应当以分号结尾。

```
// bad
.selector {
  margin: 15px
}

// good
.selector {
  margin: 15px;
}
```

对于以逗号分隔的属性值，每个逗号后面都应该插入一个空格。

```
// bad
.selector {
  box-shadow: 0 1px 2px #ccc,inset 0 1px 0 #fff;
}

// good
.selector {
  box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
}
```

对于属性值或颜色参数，省略小于 1 的小数前面的 0。

```
// bad
.selector {
  opacity: 0.5;
}

// good
.selector {
  opacity: .5;
}
```

十六进制值全部小写，尽量使用简写形式。

```
// bad
.selector {
  background-color: #FFFFFF;
}

// good
.selector {
  background-color: #fff;
}
```

选择器中的属性添加双引号。

```
// bad
.selector[type=text] {
  padding: 15px;
}

// good
.selector[type="text"] {
  padding: 15px;
}
```

避免为0值指定单位。

```
// bad
.selector {
  margin: 0px 0px 15px 0px;
}

// good
.selector {
  margin: 0 0 15px 0;
}
```




# CSS 编程规范

## 命名

class命名准守以下原则：

* class 名称中只能出现小写字符和破折号
* class 名称应当尽可能短，但是必须意义明确，避免过度任意简写
* 基于最近的父 class 或基本（base） class 作为新 class 的前缀。
* 使用 `.js-*` class 来标识行为（与样式相对），并且不要讲这些class包含到CSS文件中。

```css
/* bad */
.t { ... }
.red { ... }
.tweet_header { ... }

/* good */
.tweet { ... }
.important { ... }
.tweet-header { ... }
```

## 声明

### 声明顺序

按照以下顺序声明样式：

1. Positioning
2. Box model
3. Typographic
4. Visual

定位（positioning）可以从正常的文档流中移除元素，并且还能覆盖盒模型（box model）相关的样式，因此排在首位。

盒模型排在第二位，因为它决定了组件的尺寸和位置。

其他属性只是影响组件的_内部（inside）_或者是不影响前两组属性，因此排在后面。

```css
/* good */
.declaration-order {
  /* Positioning */
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 100;

  /* Box-model */
  display: block;
  float: right;
  width: 100px;
  height: 100px;

  /* Typography */
  font: normal 13px "Helvetica Neue", sans-serif;
  line-height: 1.5;
  color: #333;
  text-align: center;

  /* Visual */
  background-color: #f5f5f5;
  border: 1px solid #e5e5e5;
  border-radius: 3px;

  /* Misc */
  opacity: 1;
}
```

### 简写形式的属性声明

在需要显示地设置所有值的情况下，应当尽量限制使用简写形式的属性声明。常见的滥用简写属性声明的情况如下：

* `padding`

* `margin`

* `font`

* `background`

* `border`

* `border-radius`

大部分情况下，我们不需要为简写形式的属性声明指定所有值。过度使用简写形式的属性声明会导致代码混乱，并且会对属性值带来不必要的覆盖从而引起意外的副作用。

```css
/* bad */
.element {
  margin: 0 0 10px;
  background: red;
  background: url("image.jpg");
  border-radius: 3px 3px 0 0;
}

/* good */
.element {
  margin-bottom: 10px;
  background-color: red;
  background-image: url("image.jpg");
  border-top-left-radius: 3px;
  border-top-right-radius: 3px;
}
```

### 带前缀的属性声明

通过缩进，让属性值在垂直方向上对齐。

> 在 Textmate 中，使用**Text → Edit Each Line in Selection**\(⌃⌘A\)。
>
> 在 Sublime Text 2 中，使用**Selection → Add Previous Line**\(⌃⇧↑\) 和**Selection → Add Next Line**\(⌃⇧↓\)。

```css
/* bad */
.selector {
  -webkit-box-shadow: 0 1px 2px rgba(0,0,0,.15);
  box-shadow: 0 1px 2px rgba(0,0,0,.15);
}

/* good */
.selector {
  -webkit-box-shadow: 0 1px 2px rgba(0,0,0,.15);
  box-shadow: 0 1px 2px rgba(0,0,0,.15);
}
```

### 单行声明规则

对于**只包含一条声明**的样式，为了易读性和便于快速编辑，建议将语句放在同一行。

对于带有多条声明的样式，还是应当将声明分为多行。

```css
/* bad */
.selector1 {
  margin: 10px;
}
.selector2 {
  margin: 15px;
  padding: 10px;
}

/* good */
.selector1 { margin: 10px; }
.selector2 {
  margin: 15px;
  padding: 10px;
}
```

## 选择器

选择器使用遵循以下原则：

* 对于通用元素使用 class ，这样利于渲染性能的优化。

* 对于经常出现的组件，避免使用属性选择器（例如，`[class^="..."]`）。浏览器的性能会受到这些因素的影响。

* 选择器要尽可能短，并且尽量限制组成选择器的元素个数，建议不要超过 3 。

* **只有**在必要的时候才将 class 限制在最近的父元素内（也就是后代选择器）（例如，不使用带前缀的 class 时 -- 前缀类似于命名空间）。

```css
/* bad */
span { ... }
.page-container #stream .stream-item .tweet .tweet-header .username { ... }
.avatar { ... }

/* good */
.avatar { ... }
.tweet-header .username { ... }
.tweet .avatar { ... }
```

### 选择器分组

将单独的选择器单独放在一行。

```css
/* bad */
.selector, .selector-secondary, .selector[type=text] {
  padding: 15px;
}

/* good */
.selector,
.selector-secondary,
.selector[type="text"] {
  padding: 15px;
}
```

### 媒体查询

放在尽可能相关规则的附近。

```css
/* good */
.element { ... }
.element-avatar { ... }
.element-selected { ... }

@media (min-width: 480px) {
.element { ...}
.element-avatar { ... }
.element-selected { ... }
}
```

### Less和Sass中的嵌套

避免不必要的嵌套。这是因为虽然你可以使用嵌套，但是并不意味着应该使用嵌套。只有在必须将样式限制在父元素内（也就是后代选择器），并且存在多个需要嵌套的元素时才使用嵌套。

```Less
// bad
.table {
  thead {
    tr {
      th {
        ...
      }
      td {
        ...
      }
    }
  }
}

// good
.table > thead > tr {
  > th { … }
  > td { … }
}
```

## 语法

每个声明的左花括号前添加一个空格。

```css
/* bad */
.selector{ padding: 15px; }

/* good */
.selector { padding: 15px; }
```

多条样式声明块的右花括号应当单独成行。

```css
/* bad */
.selector {
  margin: 15px;
  padding: 10px;}

/* good */
.selector {
  margin: 15px;
  padding: 15px;
}
```

所有声明语句都应当以分号结尾。

```css
/* bad */
.selector {
  margin: 15px
}

/* good */
.selector {
  margin: 15px;
}
```

对于以逗号分隔的属性值，每个逗号后面都应该插入一个空格。

```css
/* bad */
.selector {
  box-shadow: 0 1px 2px #ccc,inset 0 1px 0 #fff;
}

/* good */
.selector {
  box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
}
```

对于属性值或颜色参数，省略小于 1 的小数前面的 0。

```css
/* bad */
.selector {
  opacity: 0.5;
}

/* good */
.selector {
  opacity: .5;
}
```

十六进制值全部小写，尽量使用简写形式。

```css
/* bad */
.selector {
  background-color: #FFFFFF;
}

/* good */
.selector {
  background-color: #fff;
}
```

选择器中的属性添加双引号。

```css
/* bad */
.selector[type=text] {
  padding: 15px;
}

/* good */
.selector[type="text"] {
  padding: 15px;
}
```

避免为0值指定单位。

```css
/* bad */
.selector {
  margin: 0px 0px 15px 0px;
}

/* good */
.selector {
  margin: 0 0 15px 0;
}
```

Less和Sass中的操作符，变量，数值之间均加上空格。

```Less
// bad
.element {
  margin: 10px 0 @variable*2 10px;
}

// good
.element {
  margin: 10px 0 (@variable * 2) 10px;
}
```

## 可维护性

### 注释

代码是由人编写并维护的。请确保你的代码能够自描述、注释良好并且易于他人理解。好的代码注释能够传达上下文关系和代码目的。不要简单地重申组件或 class 名称。

对于较长的注释，务必书写完整的句子；对于一般性注解，可以书写简洁的短语。

```css
/* bad */
/* Modal header */
.modal-header {
  ...
}

/* good */
/* Wrapping element for .modal-title and .modal-close */
.modal-header {
  ...
}
```

### 代码组织

* 以组件为单位组织代码段。

* 制定一致的注释规范。

* 使用一致的空白符将代码分隔成块，这样利于扫描较大的文档。

* 如果使用了多个 CSS 文件，将其按照组件而非页面的形式分拆，因为页面会被重组，而组件只会被移动。

```css
/*
 * Component section heading
 */
.element { ... }

/*
 * Component section heading
 *
 * Sometimes you need to include optional context for the entire component. Do that up here if it's important enough.
 */
.element { ... }

/* Contextual sub-component or modifer */
.element-heading { ... }
```

> 本HTML规范参照 [bootstrap编程规范](http://codeguide.bootcss.com/#css)，如有建议或补充，及时提出。




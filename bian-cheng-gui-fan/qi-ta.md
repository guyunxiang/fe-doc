## EditorConfig

### 什么是 EditorConfig ?

[EditorConfig](http://editorconfig.org/)是用来在多人协同一项目时，帮助开发人员在不同编辑器之间定义统一的编程风格。

### 如何使用 EditorConfig？

1. 在使用editorconfig的项目根目录下新建一个.editorconfig文件。
2. 为该文件添加项目的编程规范代码。
3. 为使用的编程工具安装EditorConfig插件。

### 配置代码示例

```
# editorconfig.org

root = true

[*]
charset = utf-8
end_of_line = lf
indent_size = 2
indent_style = space
insert_final_newline = true
trim_trailing_whitespace = true

[*.md]
trim_trailing_whitespace = false

[*.py]
indent_size = 4
```




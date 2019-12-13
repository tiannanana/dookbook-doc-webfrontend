TOPICS: id attribute
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# HTML 全局属性: `id`

**`id`** [全局属性](/zh-hans/webfrontend/HTML_Global_Attributes)定义了一个全文档唯一的标识符 (ID)。它用于在链接（使用片段）、脚本和样式
（通过 CSS）中辨识元素。

!!! error ""
    该属性的值是一个透明（opaque）字符串，这意味着网页开发者不能使用它来传递人类可读的信息。

`id` 的值不得包含空白字符（[[whitespace]]，包括空格和制表符等）。浏览器会将不符合规范的 ID 中的空白字符视为 ID 的一部分。与允许以空格分隔值的 [`class`](/zh-hans/webfrontend/class_attribute)
属性不同，元素只能拥有一个 ID 值。

!!! warn "Don't try this at home"
   注意：使用除 [[ASCII]] 字母、数字、`_`、`-` 和 `.` 以外的字符可能会造成兼容性问题，因为 HTML 4 中不允许使用它们。虽然这个限制在 [[HTML5]] 中被解除了，
   但为兼容性考虑 ID 应该以字母开头。

## 参见

- 所有HTML[全局属性](/zh-hans/webfrontend/HTML_Global_Attributes).
- 反映该属性的 [`Element.id`](/zh-hans/webfrontend/Element.id)。

TOPICS: draggable attribute
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# HTML 全局属性: `draggable`

!!! warn "Don't try this at home"
    这是一个实验中的功能
    此功能某些浏览器尚在开发中，请参考浏览器兼容性表格以得到在不同浏览器中适合使用的前缀。由于该功能对应的标准文档可能被重新修订，所以在未来版本的浏览器中该功能的语法和行为可能随之改变。

[全局属性](/zh-hans/webfrontend/HTML_Global_Attributes) **`draggable`** 是一个枚举类型的属性，用于标识元素是否允许使用 [__拖放操作API__](https://wiki.developer.mozilla.org/zh-CN/docs/DragDrop/Drag_and_Drop)
拖动。它的取值如下：

- `true`，表示元素可以被拖动
- `false`，表示元素不可以被拖动

如果该属性没有设值，则默认值 为 `auto` ，表示使用浏览器定义的默认行为。

这个属性是枚举类型，而不是 布尔类型 。这意味着必须显式指定值为 `true` 或者 `false` ，像 `<label draggable>Example Label</label>`
这样的简写是不允许的。正确的用法是 `<label draggable="true">Example Label</label>`。

默认情况下，只有已选中的文本、图片、链接可以拖动。对其它的元素来说，必须按拖动机制的顺序设置 **ondragstart** 事件才能正常工作， 见[__综合示例__](https://wiki.developer.mozilla.org/zh-CN/docs/DragDrop/Drag_Operations)。

## 参见

- 所有HTML[全局属性](/zh-hans/webfrontend/HTML_Global_Attributes).

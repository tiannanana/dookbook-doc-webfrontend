TOPICS: contenteditable
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# contenteditable

[全局属性](/zh-hans/webfrontend/HTML_Global_Attribute) **contenteditable**
是一个枚举属性，表示元素是否可被用户编辑。 如果可以，浏览器会修改元素的部件以允许编辑。

该属性必须是下面的值之一：

- `true` 或空字符串，表示元素是可编辑的；
- `false` 表示元素不是可编辑的。

如果没有设置该属性，其默认值继承自父元素。

该属性是一个枚举属性，而非布尔属性。这意味着必须显式设置其值为 true、false 或空字符串中的一个，并且不允许简写为
`<label contenteditable>Example Label</label>`正确的用法是 `<label contenteditable="true">Example Label</label>`。

你可以使用CSS [caret-color](/zh-hans/webfrontend/caret-color) 属性设置用于绘制文本插入caret的颜色。

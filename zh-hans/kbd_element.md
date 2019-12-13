TOPICS: <kbd>

# `<kbd>`

HTML键盘输入元素(**`<kbd>`**) 用于表示用户输入，它将产生一个行内元素，以浏览器的默认monospace字体显示。

## 属性

该元素仅支持[全局属性](/zh-hans/webfrontend/HTML_Global_Attributes).

## 示例

```html
<p>Type the following in the Run dialog: <kbd>cmd</kbd><br />Then click the OK button.</p>

<p>Save the document by pressing <kbd>Ctrl</kbd> + <kbd>S</kbd></p>
```

## 注意

通过定义CSS规则可以改变kbd的默认字体。用户首选项设置可能会比该CSS规则具有更高优先级。

当`<kbd>`元素处于[`<samp>`](/zh-hans/webfrontend/<samp>)元素之中时，它代表着被系统回显的输入。

当`<kbd>`元素中包含[`<samp>`](/zh-hans/webfrontend/<samp>)元素时，该输入是基于系统输出的，比如调用某个菜单项。

当`<kbd>`元素处于另一个`<kbd>`元素之中时，它代表了一个实际的按键，或是该输入机制下的某个单位输入。

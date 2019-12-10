TOPICS: <label>

# `<label>`

**HTML的`<label>`元素** 表示用户界面中某个项目的标题。

将`<label>`与一个[`<input>`](/zh-hans/webfrontend/<input>)元素相关联具有一些主要优点：

- 标签文本不仅在视觉上与其对应的文本输入相关联；它也以编程方式与之关联。这意味着，例如:当用户专注于表单输入时，屏幕阅读器将读出标签，从而使辅助技术用户更容易理解应输入哪些数据。
- 您可以单击关联的标签来聚焦/激活输入以及输入本身。 这种增加的点击区域为尝试激活输入的任何人（包括使用触摸屏设备的用户）提供了优势。

要将`<label>`与一个[`<input>`](/zh-hans/webfrontend/<input>)元素相关联，您需要给该[`<input>`](/zh-hans/webfrontend/<input>)一个id属性。
然后，`<label>`需要一个`for`属性，其值与输入的ID相同。

另外，您可以将[`<input>`](/zh-hans/webfrontend/<input>)直接嵌套在`<label>`中，在这种情况下，因为关联是隐式的，所以不需要`for`和`id`属性：

```html
<label>Do you like peas?
  <input type="checkbox" name="peas">
</label>
```

其他用法说明：

- 标签正在标记的表单控件称为标签元素的标签控件。 一个输入可以与多个标签关联。
- 标签本身并不直接与表单关联。 它们仅通过与之关联的控件与表单间接关联。
- 当单击或点击`<label>`并将其与表单控件关联时，也会为关联的控件引发单击事件。

## 属性

此元素包括[全局属性](https://wiki.developer.mozilla.org/en-US/docs/HTML/Global_attributes).

| 属性 | 描述 |
| :-- | :-- |
| `for` | 与`<label>`元素在同一文档中的可标签形式相关元素的`id`。 ID为`for`属性值匹配的文档中的第一个元素是此label元素的带标签的控件（如果它是可标签的元素）。 如果它不可标记，则`for`属性无效。如果还有其他元素也与id值匹配，则在文档的后面将不考虑它们。<br> **注意:** 一个`<label>`元素可以同时具有`for`属性和包含的控制元素， 只要for属性指向所包含的控制元素。|
| `form` | 标签所关联的[`<form>`](/zh-hans/webfrontend/<form>)元素（它的表单所有者）。如果指定，则属性的值是同一文档中[`<form>`](/zh-hans/webfrontend/<form>)元素的ID。 这使您可以将标签元素放置在文档中的任何位置，而不仅仅是它们的表单元素的后代。|

## CSS样式

对于`<label>`元素没有特殊的样式注意事项-从结构上讲，它们是简单的内联元素，因此可以使用与[`<span>`](/zh-hans/webfrontend/<span>)或[`<a>`](/zh-hans/webfrontend/<a>)
元素几乎相同的方式进行样式设置。 只要不使文本难以阅读，就可以以任何方式对它们应用样式。

## 示例

### 简单标签示例

```html
<label>Click me <input type="text"></label>
```

### 使用“for”属性

```html
<label for="username">Click me</label>
<input type="text" id="username">
```

## 可达性问题

### 互动内容

请勿在“标签”内放置诸如锚点或按钮之类的交互式元素。 这样做使人们很难激活与“标签”相关联的表单输入。

错误

```html
<label for="tac">
  <input id="tac" type="checkbox" name="terms-and-conditions">
  I agree to the <a href="terms-and-conditions.html">Terms and Conditions</a>
</label>
```

正确

```html
<label for="tac">
  <input id="tac" type="checkbox" name="terms-and-conditions">
  I agree to the Terms and Conditions
</label>
<p>
  <a href="terms-and-conditions.html">Read our Terms and Conditions</a>
</p>
```

### 标题

将标题元素放置在`<label>`中会干扰多种辅助技术，因为标题通常用作导航辅助。 如果标签的文本需要在视觉上进行调整，请使用应用于`<label>`元素的CSS类。

如果表单或表单的一部分需要标题，请使用放置在[`<fieldset>`](/zh-hans/webfrontend/<fieldset>)中的[`<legend>`](/zh-hans/webfrontend/<legend>)元素。

错误

```html
<label for="your-name">
  <h3>Your name</h3>
  <input id="your-name" name="your-name" type="text">
</label>
```

正确

```html
<label class="large-label" for="your-name">
  Your name
  <input id="your-name" name="your-name" type="text">
</label>
```

### Buttons

具有`type="button"`声明和有效的`value`属性的[`<input>`](/zh-hans/webfrontend/<input>)元素不需要与之关联的标签。
这样做实际上可能会干扰辅助技术解析按钮输入的方式。 同样的情况适用于[`<button>`](/zh-hans/webfrontend/<button>)元素。

## 技术摘要

|  |  |
| :-- | :-- |
| **内容分类** | 流内容，短语内容，交互内容，与表单相关的元素，可触知的内容。|
| **允许的内容** | 短语内容，但没有后代标签元素。 除带标签的控件外，不允许带其他标签的元素。|
| **标签遗漏** | 没有，开始标签和结束标签都是必需的。|
| **允许的父元素** | 接受短语内容的任何元素。|
| **允许的 ARIA 角色** | 没有 |
| **DOM 接口** | `HTMLLabelElement` |

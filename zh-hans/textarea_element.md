TOPICS: <textarea>

# `<textarea>`

**HTML`<textarea>`元素**代表多行纯文本编辑控件，当您希望允许用户输入大量自由格式文本（例如，对评论或反馈表单的评论）时，该控件很有用。

上面的示例演示了`<textarea>`的许多功能。 第一个示例显示了最简单的用法，仅具有id属性以允许将`<textarea>`与[`<label>`](/zh-hans/webfrontend/<label>)元素相关联以实现可访问性，而`name`属性则用于设置
关联数据点的名称 提交表单后将其提交给服务器。

第二个示例显示了一些更复杂的功能：

- 使用`rows`和`cols`属性可以指定`<textarea>`要采用的确切大小。 设置这些值是保持一致性的一个好主意，因为浏览器的默认设置可能有所不同。
- `maxlength`指定允许`<textarea>`包含的最大字符数。 您还可以使用`minlength`属性设置一个被视为有效的最小长度，并使用`required`属性来指定
`<textarea>`如果为空则不会提交（并且无效）。这为`<textarea>`提供了简单的验证，它比其他表单元素更为基本（例如，您不能提供特定的正则表达式来使用`pattern`属性来验证值，
就像使用`pattern`属性一样） [`<input>`](/zh-hans/webfrontend/<input>)元素）。
- 当文本到达`<textarea>`的边缘时，`wrap`指定文本的环绕行为。
- 如果您想要`<textarea>`的默认内容，请在开始和结束标签之间输入。 `<textarea>`不支持`value`属性。

`<textarea>`元素还接受构成[`<input>`](/zh-hans/webfrontend/<input>)的几种常见属性，例如`autocomplete`、`autofocus`、`disabled`、`placeholder`、`readonly`和`required`。

## 属性

此元素包括[全局属性](https://wiki.developer.mozilla.org/en-US/docs/HTML/Global_attributes).

| 属性 | 描述 |
| :-- | :-- |
| `autocapitalize` | 这是iOS上的WebKit支持的非标准属性（因此，几乎所有在iOS上运行的浏览器，包括Safari，Firefox和Chrome）都可以控制该属性，该属性控制文本值在输入和编辑时是否自动大写。 用户。 未弃用的值在iOS 5和更高版本中可用。 可能的值为：<br>`none`：完全禁用自动大写。<br>`sentences`：自动将句子的首字母大写。<br>`words`：自动将单词的首字母大写。<br>`characters`：自动将所有字符大写。<br>`on`：自iOS 5起不推荐使用。<br>`off`：自iOS 5起不推荐使用。
| `autocomplete` | 此属性指示控件的值是否可以由浏览器自动完成。 可能的值为：<br>`off`：用户必须为每次使用在此字段中明确输入一个值，否则文档将提供其自己的自动完成方法。 <br> `on`:浏览器可以根据用户在先前使用过程中输入的值自动完成该值。<br> <br>如果未在窗口上指定`autocomplete`属性 `<textarea>`元素，然后浏览器将使用`<textarea>`元素的表单所有者的自动完成属性值。 表单所有者是该`<textarea>`元素的后代[`<form>`](/zh-hans/webfrontend/<form>)元素，或者是其id由`input`元素的`form`属性指定的[`<form>`](/zh-hans/webfrontend/<form>)元素。 有关更多信息，请参见[`<form>`](/zh-hans/webfrontend/<form>)中的`autocomplete`属性。|
| `autofocus` | 使用此布尔属性，可以指定页面加载时表单控件应具有输入焦点。 文档中只有一个与表单相关的元素可以指定此属性。|
| `cols` | 文本控件的可见宽度，以平均字符宽度为单位。 如果指定，则必须为正整数。 如果未指定，则默认值为20。|
| `disabled` | 此布尔值属性指示用户无法与控件进行交互。 如果未指定此属性，则控件从包含元素（例如[`<fieldset>`](/zh-hans/webfrontend/<fieldset>)）继承其设置。 如果在设置“禁用”属性时没有包含元素，则启用控件。|
| `form` | 与`<textarea>`元素关联的[`<form>`](/zh-hans/webfrontend/<form>)元素（它的"form owner"）。 该属性的值必须是同一文档中表单元素的ID。如果未指定此属性，则`<textarea>`元素必须是`form`元素的后代。这个属性使您可以将`<textarea>`元素放置在文档中的任何位置，而不仅仅是表单元素的后代。|
| `maxlength` | 用户可以输入的最大字符数（UTF-16代码单元）。 如果未指定此值，则用户可以输入不限数量的字符。|
| `minlength` | 用户应输入的最小字符数（UTF-16代码单元）。|
| `name` | 控件的名称。|
| `placeholder` | 向用户提示可以在控件中输入的内容。 呈现提示时，占位符文本内的回车符或换行符必须视为换行符。<br> **请注意：** 占位符仅用于显示应输入到行中的数据类型的示例。 形成; 它们不能替代绑定到输入的适当的[`<label>`](/zh-hans/webfrontend/<label>)元素。 有关完整说明，请参见[`<input>`](/zh-hans/webfrontend/<input>)中的Labels和占位符：Input（表单输入）元素。|
| `readonly` | 此布尔值属性指示用户无法修改控件的值。与`disabled`属性不同，`readonly`属性不会阻止用户单击或选择控件。 只读控件的值仍与表单一起提交。|
| `required` | 此属性指定用户在提交表单之前必须填写一个值。|
| `rows` | 控件的可见文本行数。|
| `spellcheck` | 指定`<textarea>`是否受基础浏览器/OS的拼写检查。 值可以是：<br> **`true`:** 表示该元素需要检查其拼写和语法。<br> **`default`:** 表示该元素将按照 默认行为，可能基于父元素自己的`spellcheck`值。<br> **`false`:** 指示不应对元素进行拼写检查。|
| `wrap` | 指示控件如何包装文本。 可能的值为：<br> **`hard`:** 浏览器会自动插入换行符（CR + LF），以使每行的宽度不超过控件的宽度； <br> **`soft`:** 浏览器确保值中的所有换行符均由CR + LF对组成，但不会插入任何其他字符 <br> **`off`:** 类似于`soft`，但将外观更改为空白：之前，不要包装超过`cols`的线段，并且`<textarea>`可以水平滚动。 >如果未指定此属性，则`soft`为其默认值。|

## CSS样式

`<textarea>`是一个替换的元素-它具有固有的尺寸，如光栅图像。 默认情况下，其`display`”值为`block`。 与其他表单元素相比，它的样式相对容易，其框模型，字体，配色方案等可以使用常规CSS轻松操作。

样式化HTML表单提供了一些样式化`<textarea>`的有用技巧。

### 基线不一致

HTML规范没有定义`<textarea>`的基线在哪里，因此不同的浏览器将其设置在不同的位置。 对于Gecko，将`<textarea>`基线设置在`textarea`第一行第一行的基线上，在另一个浏览器上，
可以将其设置在`<textarea>`框的底部。 请勿在其上使用`vertical-align: baseline`；行为是无法预测的。

### 控制Textarea是否可调整大小

在大多数浏览器中，`<textarea>`的大小是可调整的-您会注意到右上角的拖动手柄，可用于更改页面上元素的大小。 这由`resize` CSS属性控制-默认情况下，调整大小是启用的，但是您可以使用`none'的`resize`值显式禁用它：

```css
textarea {
  resize: none;
}
```

### 设置有效值和无效值的样式

`<textarea>`元素的有效值和无效值（例如，在`minlength`，`maxlength`或`required`所设置的边界之内和之外的值）可以使用`:valid`和`:invalid`突出显示。
伪类。 例如，根据文本区域的有效或无效来为其设置不同的边框：

```css
textarea:invalid {
  border: 2px dashed red;
}

textarea:valid {
   border: 2px solid lime;
}
```

## 示例

### 基本例子

以下示例显示了一个非常简单的文本区域，其中包含一定数量的行和列以及一些默认内容。

```html
<textarea name="textarea"
   rows="10" cols="50">Write something here</textarea>
```

### 最小和最大长度

此示例的最小和最大字符数分别为10和20。 试试看。

```html
<textarea name="textarea"
   rows="5" cols="30"
   minlength="10" maxlength="20">Write something here</textarea>
```

请注意，`minlength`不会阻止用户删除字符，从而使输入的数字超过最小值，但确实会使输入`<texttexta>`的值无效。 还要注意，即使您设置了“最小长度”值（例如3），除非您也设置了“必需”属性，否则空的`<textarea>`仍然被认为是有效的。

### 占位符

本示例设置了一个占位符。 请注意，当您开始在框中输入内容时，它是如何消失的。

```html
<textarea name="textarea"
   rows="5" cols="30"
   placeholder="Comment text."></textarea>
```

!!! warn "Don't try this at home"
    注意：占位符仅用于显示应输入表单的数据类型的示例； 它们不能替代绑定到输入的适当的[`<label>`](/zh-hans/webfrontend/<label>)元素。 有关完整说明，请参见[`<input>`](/zh-hans/webfrontend/<input>)中的Labels和占位符：Input（表单输入）元素。

### 禁用和只读

这个例子显示了两个`<textarea>`s-其中一个是`disabled`，另一个是`readonly`。 两者兼而有之，您会看到行为上的差异—禁用元素禁用为任何方式（并且其值未提交），
而只读元素可选且其内容可复制（及其 值已提交）； 您只是无法编辑内容。

!!! warn "Don't try this at home"
    注意：在非Firefox的浏览器（例如chrome）中，禁用的textarea内容可能是可选择的并且可以复制。

```html
<textarea name="textarea"
   rows="5" cols="30"
   disabled>I am a disabled textarea</textarea>
<textarea name="textarea"
   rows="5" cols="30"
   readonly>I am a readonly textarea</textarea>
```

## 技术摘要

|  |  |
| :-- | :-- |
| **内容分类** | 流内容，短语内容，交互式内容，列出的，可标记的，可重置的和可提交的与表单相关的元素. |
| **允许的内容** | 文本 |
| **标签遗漏** | 无，开始标签和结束标签都是必需的. |
| **允许的父元素** | 任何接受短语内容的元素. |
| **允许的 ARIA 角色** | 没有 |
| **DOM 接口** | `HTMLTextAreaElement` |

## 也可以看看

其他与表单相关的元素：

- [`<form>`](/zh-hans/webfrontend/<form>)
- [`<button>`](/zh-hans/webfrontend/<button>)
- [`<datalist>`](/zh-hans/webfrontend/<datalist>)
- [`<legend>`](/zh-hans/webfrontend/<legend>)
- [`<label>`](/zh-hans/webfrontend/<label>)
- [`<select>`](/zh-hans/webfrontend/<select>)
- [`<optgroup>`](/zh-hans/webfrontend/<optgroup>)
- [`<option>`](/zh-hans/webfrontend/<option>)
- [`<input>`](/zh-hans/webfrontend/<input>)
- [`<keygen>`](/zh-hans/webfrontend/<keygen>)
- [`<fieldset>`](/zh-hans/webfrontend/<fieldset>)
- [`<output>`](/zh-hans/webfrontend/<output>)
- [`<progress>`](/zh-hans/webfrontend/<progress>)
- [`<meter>`](/zh-hans/webfrontend/<meter>)

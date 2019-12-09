TOPICS: <select>
        <option>
        <optgroup>
AUTHORS: King; King.@mozilla.net; mdn:King.
         Wizard; wizardforcel@mozilla.net; mdn:wizardforcel
         Judy; pavilion2t@github.com; github:pavilion2t
         DUHUAZHI; DUHZ@mozilla.net; mdn:DUHZ
         紫云飞; ziyunfei@mozilla.net; mdn:ziyunfei

# `<select>`

**HTML `<select>` 元素**表示一个控件，提供一个选项菜单：

## 属性

包括下列全局属性。

| 属性 | 描述 |
| :-- | :-- |
| `autocomplete` | DOMString 提供用户代理自动完成功能的提示。 有关完整值的完整列表以及有关如何使用自动完成的详细信息，请参阅HTML自动完成属性。 |
| `autofocus` | 这个属性能够让一个对象在页面加载的时候获得焦点. 在一个页面上下文中, 只有一个对象可以有这个属性，并且是布尔值(true 或者 false). |
| `disabled` | 这个布尔值的属性表明一个用户是否可以操控该表单对象. 如果这个属性没有被明确定义, 则从它的父元素继承, 例如 fieldset; 如果没有父元素设置 `disabled` 属性, 那么默认该表单对象enabled. |
| `form` | select所关联的form表单 (它的"表单拥有者"). 如果这个属性被明确定义, 那么它的值一定是在同一个document中表单ID. 这样能够让你把select标签放在任何的位置, 不仅限于作为form表单的后代元素. |
| `multiple` | 这个布尔值的属性标记select是否可以多选. 默认是单选. |
| `name` | 控件名称 |
| `required` | 规定select的值不能为空(布尔值). |
| `size` | 如果控件显示为滚动列表框，则此属性表示为控件中同时可见的行数。浏览器不需要将选择元素呈现为滚动列表框。默认值为0 |

!!! warn "Don't try this at home"
    提示: 根据HTML5规范， 默认值应该为1； 但是，在实践中，这样会影响到一些网站，同时其它浏览器也没有那么处理，所以Mozilla 在Firefox中选择继续使用默认值 0 .

## 用 CSS 美化

众所周知，`<select>`元素很难用CSS进行高效的设计。你可以影响任何元素的某些方面 - 例如，操纵框模型，显示的字体等，你可以使用appearance 属性来删除默认的系统外观。

但是，这些属性不会在浏览器之间产生一致的结果，并且很难在列中将不同类型的表单元素相互排列。 `<select>`元素的内部结构复杂，难以控制。 如果你想获得完全控制，你应该考虑使用一个具有良好设施的库
来构建窗体小部件（例如jQuery UI），或者尝试使用非语义元素，JavaScript和WAI-ARIA滚动自己的下拉菜单来提供语义。

有关样式`<select>`的更多有用信息，请参阅：

- Styling HTML forms
- Advanced styling for HTML forms

## `<option>`

在web表单中,  HTML元素 `<option>`  用于定义在`<select>`,  `<optgroup>` 或[`<datalist>`](/zh-hans/webfrontend/<datalist>)
元素中包含的项。`<option>` 可以在弹出窗口和 html 文档中的其他项目列表中表示菜单项。

| 属性 | 描述 |
| :-- | :-- |
| `disabled` | 如果设置了这个布尔属性，选项就不是可选的。浏览器通常会将这种控件显示为灰色，并且不再接受任何浏览器事件，例如鼠标点击或者焦点相关的事件。如果这个属性没有设置，如果元素的祖先是禁用的
`<optgroup>` 元素，元素仍然是禁用的 。|
| `label` | 这个属性是用于表示选项含义的文本。如果 label 属性没有定义，它的值就是元素文本内容。<br>**使用注解**: `label` 属性为包含短的标签而设计，通常用在层级菜单中。 `value` 属性描述了更长的标签，为用在单选按钮附近而设计。|
| `selected` | 如果存在, 则这个布尔属性表明，这个选项初始被选中。如果 `<option>` 元素是 `<select>` 元素的后继，并且它的 `multiple` 属性没有设置，这个 `<select>`
元素只有一个 `<option>` 元素可以拥有 `selected` 属性。|
| `value` | 这个属性的内容代表这个选项选中的话，提交给表单的值。如果省略了这个属性，值就从选项元素的文本内容中获取。|

## `<optgroup>`

在一个web表单中, HTML元素 `<optgroup>` 会创建包含在一个 `<select>`元素中的一组选项

| 属性 | 描述 |
| :-- | :-- |
| `disabled` | 如果设置了这个布尔值，那么这个选项组中将没有选项是可以被选择的。通常浏览器会置灰这样的控件，它不会再接受任何浏览器事件，例如鼠标点击或者焦点相关的事件。|
| `label` | 选项组的名字，当在用户界面标记(label)选项的时候可以被浏览器使用。使用这个元素时必须加上这个属性 |

## 示例

### 简单的示例

```html
<!-- The second value will be selected initially -->
<select name="select">
  <option value="value1">Value 1</option>
  <option value="value2" selected>Value 2</option>
  <option value="value3">Value 3</option>
</select>
```

### `<optgroup>`的示例

```html
<select>
  <optgroup label="Group 1">
    <option>Option 1.1</option>
  </optgroup>
  <optgroup label="Group 2">
    <option>Option 2.1</option>
    <option>Option 2.2</option>
  </optgroup>
  <optgroup label="Group 3" disabled>
    <option>Option 3.1</option>
    <option>Option 3.2</option>
    <option>Option 3.3</option>
  </optgroup>
</select>
```

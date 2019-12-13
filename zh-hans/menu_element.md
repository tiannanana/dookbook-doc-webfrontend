TOPICS: <menu>

# `<menu>`

!!! warn "Don't try this at home"
    这是一项“实验技术”
    在生产环境中使用此功能之前，请仔细检查浏览器兼容性表。

**HTML元素`<menu>`** 代表用户可以执行或激活的一组命令。这包括可能出现在屏幕顶部的列表菜单，以及上下文菜单，例如单击按钮后可能出现在按钮下方的上下文菜单。

|  |  |
| :-- | :-- |
| **内容分类** | 流内容。此外，如果处于列表菜单状态，则可触摸的内容。(列表菜单为默认状态，除非父元素在上下文菜单状态下为`<menu>`。） |
| **允许的内容** | 如果该元素处于列表菜单状态：流内容，或者零次或多次出现[`<li>`](/zh-hans/webfrontend/<li>)，[`<script>`](/zh-hans/webfrontend/<script>)和[`<template>`](/zh-hans/webfrontend/<template>)。<br>如果该元素在上下文中 菜单状态：`<menu>`（仅上下文菜单状态），[`<hr>`](/zh-hans/webfrontend/<hr>)，[`<script>`](/zh-hans/webfrontend/<script>)和[`<template>`](/zh-hans/webfrontend/<template>)以任何顺序出现零次或多次。 |
| **标签遗漏**| 无，开始标签和结束标签都是必需的. |
| **允许的父元素** | 任何接受流程内容的元素. |
| **允许的 ARIA 角色** | 没有 |
| **DOM 接口** | `HTMLMenuElement` |

## 属性

此元素包括[全局属性](/zh-hans/webfrontend/HTML_Global_Attributes).

| 属性 | 描述 |
| :-- | :-- |
| `label` | 显示给用户的菜单名称。 在嵌套菜单中使用，以提供一个标签，通过该标签可以访问子菜单。 仅在上下文菜单状态下，当父元素为`<menu>`时才必须指定。|
| `type` | 此属性指示要声明的菜单的类型，并且可以是两个值之一。<br> `context`：指示弹出菜单状态，该状态表示通过另一个元素激活的一组命令。这可能是由[`<button>`](/zh-hans/webfrontend/<button>)元素的菜单属性引用的按钮菜单，也可能是具有`contextmenu`属性的元素的上下文菜单。 如果缺少属性，并且父元素也是`<menu>`元素，则此值为默认值。<br>`toolbar`：指示工具栏状态，代表由一系列用于用户交互的命令组成的工具栏。这可能是[`<li>`](/zh-hans/webfrontend/<li>)元素的无序列表的形式，或者，如果该元素没有[`<li>`](/zh-hans/webfrontend/<li>)子元素，则流内容描述可用的命令。 如果缺少属性，则此值为默认值。|

## 使用说明

`<menu>`和[`<ul>`](/zh-hans/webfrontend/<ul>)元素均表示无序的项目列表。关键区别在于，[`<ul>`](/zh-hans/webfrontend/<ul>)主要包含要显示的项目，而`<menu>`是用于交互项目的对象。

HTML菜单可用于创建上下文菜单（通常通过右键单击另一个元素来激活）或工具栏。

上下文菜单由一个`<menu>`元素组成，该元素包含菜单中每个可选选项的`<menuitem>`元素，菜单内子菜单的`<menu>`元素以及分隔符行的[`<hr>`](/zh-hans/webfrontend/<hr>)
元素。 将菜单内容分为几部分。 然后，将上下文菜单附加到通过使用关联元素的`contextmenu`属性激活的元素上，或者对于附加到[`<button>`](/zh-hans/webfrontend/<button>)元素的按钮激活菜单，使用菜单属性。

工具栏菜单由一个`<menu>`元素组成，其内容用以下两种方式之一描述：作为由[`<li>`](/zh-hans/webfrontend/<li>)元素表示的项目的无序列表（每个代表用户可以使用的命
令或选项），或者 （如果没有[`<li>`](/zh-hans/webfrontend/<li>)元素），则流内容描述可用的命令和选项。

此元素在HTML4中已弃用，但在HTML5.1和HTML生活标准中已重新引入。 本文档介绍了当前的Firefox实现。 根据HTML5.1，类型“列表”可能会更改为“工具栏”。

## 示例

### 上下文菜单

!!! error ""
    不再推荐此功能。 尽管某些浏览器可能仍支持它，但是它可能已经从相关的Web标准中删除，正在被删除或仅出于兼容性目的而保留。避免使用它，并尽可能更新现有代码；
    请参阅此页面底部的兼容性表以指导您做出决定。 请注意，此功能可能随时停止起作用。

### 不推荐使用

不再推荐此功能。 尽管某些浏览器可能仍支持它，但是它可能已经从相关的Web标准中删除，正在被删除或仅出于兼容性目的而保留。 避免使用它，并尽可能更新现有代码； 请参阅此页面底部的兼容性表以指导您做出决定。
请注意，此功能可能随时停止起作用。

```html
<!-- A <div> element with a context menu -->
<div contextmenu="popup-menu">
  Right-click to see the adjusted context menu
</div>

<menu type="context" id="popup-menu">
  <menuitem>Action</menuitem>
  <menuitem>Another action</menuitem>
  <hr/>
  <menuitem>Separated action</menuitem>
</menu>
```

```css
div {
  width: 300px;
  height: 80px;
  background-color: lightgreen;
}
```

### 菜单按钮

!!! error ""
    菜单按钮尚未在任何已知的浏览器中实现。`<menu>`元素上的type属性现在已过时。

!!! error ""
    `<menuitem>`元素已过时。

```html
<!-- A button, which displays a menu when clicked. -->
<button type="menu" menu="popup-menu">
  Dropdown
</button>

<menu type="context" id="popup-menu">
  <menuitem>Action</menuitem>
  <menuitem>Another action</menuitem>
  <hr/>
  <menuitem>Separated action</menuitem>
</menu>
```

### 工具列

!!! error ""
    工具栏菜单尚未在任何已知的浏览器中实现。

```html
<!-- A context menu for a simple editor,
   - containing two menu buttons. -->
<menu type="toolbar">
  <li>
    <button type="menu" menu="file-menu">File</button>
    <menu type="context" id="file-menu">
      <menuitem label="New..." onclick="newFile()">
      <menuitem label="Save..." onclick="saveFile()">
    </menu>
  </li>
  <li>
    <button type="menu" menu="edit-menu">Edit</button>
    <menu type="context" id="edit-menu">
      <menuitem label="Cut..." onclick="cutEdit()">
      <menuitem label="Copy..." onclick="copyEdit()">
      <menuitem label="Paste..." onclick="pasteEdit()">
    </menu>
  </li>
</menu>
```

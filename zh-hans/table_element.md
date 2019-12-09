TOPICS: <table>
        <thead>
        <tbody>
        <tfoot>
        <th>
        <tr>
        <td>
        <caption>
        <colgroup>
        <col>
AUTHORS: Shaolin Wu; wslsdust@163.com; github:codevvvv9
         xgqfrms; xgqfrms@github.com; github:xgqfrms
         itplus; eforegist@github.com; github:eforegist
         Dong WEI; FredWe@mozilla.net; mdn:FredWe
         Crystal-RainSlide; Crystal-RainSlide@github.com; github:Crystal-RainSlide
         砂漠の毒虫; 853419196@qq.com; github:853419196
         Nagisa(Daxiong); nagisa_tk@outlook.com; github:nagisatk
         levinit; levinit@github.com; github:levinit
         Florian Scholz; fscholz@mozilla.net; mdn:fscholz
         Bayes; 827130441@qq.com; github:coconilu
         S; soyaine@github.com; github:soyaine
         潘韬; pantao@mozilla.net; mdn:pantao

# `<table>`

**HTML**的 **`<table>`** 元素表示表格数据 — 即通过二维数据表表示的信息。

!!! warn "Don't try this at home"
    小贴士：在 CSS 创建之前， HTML `<table>` 元素常常被用于布局页面。 这种用法在 HTML 4之后不被推荐使用，并且 `<table>`元素 不应该 被用于此目的。

|  |  |
| :-- | :-- |
| **内容分类** | 流动内容 |
| **允许的内容** | 按照这个顺序：<br>一个可选的 `<caption>` 元素<br>零个或多个的 `<colgroup>` 元素<br>一个可选的 `<thead>` 元素<br>一个可选的 `<tfoot>` 元素（tfoot元素出现在tbody或tr元素前后都可以。在HTML4中，它只能出现在这些元素之前）<br>零个或多个 `<tbody>` 元素<br>一个或多个 `<tr>` 元素 |
| **标签省略** | 不允许，开始标签和结束标签都不能省略。 |
| **允许的父元素** | 任何支持流内容的元素 |
| **允许的ARIA 角色** | Any |
| **DOM 接口** | `HTMLTableElement` |

## 属性

表格标签支持 全局属性。

## `<thead>`

**HTML**的 **`<thead>`** 元素定义了一组定义表格的列头的行。

## `<tbody>`

**HTML `<tbody>` 元素**封装了一组表行`<tr>`元素，表示它们包含表的主体`<table>`。

## `<tfoot>`

HTML 元素`<tfoot>`  定义了一组表格中各列的汇总行。

## `<th>`

HTML `<th>` 元素定义表格内的表头单元格。这部分特征是由 `scope` and `headers` 属性准确定义的。

## `<tr>`

HTML `<tr>` 元素定义表格中的行。 Those can be a mix of `<td>` and `<th>` elements.

### `<td>`

HTML `<td>` 元素定义表格中的列

## `<caption>`

HTML `<caption>` 元素 (or HTML 表格标题元素) 展示一个表格的标题， 它常常作为 `<table>` 的第一个子元素出现，同时显示在表格内容的最前面，但是，它同样可以被CSS样式化，所以，它同样可以出现在任何一个一个相对于表格的做任意位置。

## `<colgroup>`

HTML 中的 表格列组（Column Group `<colgroup>`） 标签用来定义表中的一组列表。

### `<col>`

HTML `<col>` 元素 定义表格中的列，并用于定义所有公共单元格上的公共语义。它通常位于`<colgroup>`元素内。

## 示例

### 简单的表格

```html
<table>
  <tr>
    <td>John</td>
    <td>Doe</td>
  </tr>
  <tr>
    <td>Jane</td>
    <td>Doe</td>
  </tr>
</table>
```

### 更多例子

```html
<p>Table with thead, tfoot, and tbody</p>
<table>
  <thead>
    <tr>
      <th>Header content 1</th>
      <th>Header content 2</th>
    </tr>
  </thead>
  <tfoot>
    <tr>
      <td>Footer content 1</td>
      <td>Footer content 2</td>
    </tr>
  </tfoot>
  <tbody>
    <tr>
      <td>Body content 1</td>
      <td>Body content 2</td>
    </tr>
  </tbody>
</table>

<p>Table with colgroup</p>
<table>
  <colgroup span="4" class="columns"></colgroup>
  <tr>
    <th>Countries</th>
    <th>Capitals</th>
    <th>Population</th>
    <th>Language</th>
  </tr>
  <tr>
    <td>USA</td>
    <td>Washington D.C.</td>
    <td>309 million</td>
    <td>English</td>
  </tr>
  <tr>
    <td>Sweden</td>
    <td>Stockholm</td>
    <td>9 million</td>
    <td>Swedish</td>
  </tr>
</table>

<p>Table with colgroup and col</p>
<table>
  <colgroup>
    <col class="column1">
    <col class="columns2plus3" span="2">
  </colgroup>
  <tr>
    <th>Lime</th>
    <th>Lemon</th>
    <th>Orange</th>
  </tr>
  <tr>
    <td>Green</td>
    <td>Yellow</td>
    <td>Orange</td>
  </tr>
</table>

<p>Simple table with caption</p>
<table>
  <caption>Awesome caption</caption>
  <tr>
    <td>Awesome data</td>
  </tr>
</table>
```

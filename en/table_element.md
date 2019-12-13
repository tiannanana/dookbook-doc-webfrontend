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
AUTHORS: Simon Speich; speich@github.com; github:speich
         codingdudecom; codingdudecom@github.com; github:codingdudecom
         Jonathan Pool; JonathanPool@mozilla.net; mdn:JonathanPool
         Masahiro Fujimoto; mfujimot@gmail.com; github:mfuji09
         Sphinx; SphinxKnight@github.com; github:SphinxKnight
         Eric Bailey; ericwbailey@github.com; github:ericwbailey
         ExE Boss; ExE-Boss@github.com; github:ExE-Boss
         Michael[tm] Smith; mike@w3.org; github:sideshowbarker
         Eric Shepherd; eshepherd@mozilla.com; github:a2sheppy
         Teoli; teoli@mozilla.net; mdn:teoli
         Filipus Klutiero; Chealer@mozilla.net; mdn:Chealer
         Chris Mills; chrisdavidmills@mozilla.net; mdn:chrisdavidmills
         Taylor Hunt; tigt@github.com; github:tigt
         Sebastian Zartner; SebastianZ@github.com; github:SebastianZ
         Sam Eaton; sam_eaton@mozilla.net; mdn:sam_eaton
         Alex Chao; Alex1990@github.com; github:Alex1990
         Chris Rebert; cvrebert@mozilla.net; mdn:cvrebert
         Karen Scarfone; kscarfone@mozilla.net; mdn:kscarfone
         Trevor Hobson; trevorhobson@github.com; github:trevorhobson
         Keiichi; ethertank@mozilla.net; mdn:ethertank
         Les Orchard; me@lmorchard.com; github:lmorchard
         Jonathan Wilsson; jwilsson@github.com; github:jwilsson
         Janet Swisher; jmswisher@github.com; github:jmswisher
         Florian Scholz; fscholz@mozilla.net; mdn:fscholz
         Stephanie Hobson; stephaniehobson@mozilla.net; mdn:stephaniehobson
         Renoir Boulanger; renoirb@mozilla.net; mdn:renoirb
         Christophe Hurpeau; christophe@hurpeau.com; github:christophehurpeau
         Michael Beckwith; tw2113@github.com; github:tw2113
         Manuel Strehl; Boldewyn@github.com; github:Boldewyn
         Ryan Grove; yaypie@mozilla.net; mdn:yaypie
         Tzu-Hsuan (TH) Huang; thhuang@github.com; github:thhuang
         Jérémie Patonnier; Jeremie@mozilla.net; mdn:Jeremie
         Nick Shvelidze; captain@pirrate.me; github:shvelo
         sorawee; sorawee@github.com; github:sorawee
         JIM Taylor; jimtaylor1974@github.com; github:jimtaylor1974
         Daniel D. Beck; daniel@ddbeck.com; github:ddbeck
         aceman; aceman-bugzilla@mozilla.net; mdn:aceman-bugzilla
         Albert Wiersch; HTMLValidator@mozilla.net; mdn:HTMLValidator
         Irene Smith; ismith@mozilla.com; github:irenesmith
         Sean Macdonald; sean@crazyhorsecoding.com; github:sean9999
         Matt Brubeck; mbrubeck@limpet.net; github:mbrubeck
         ishita; ishita@github.com; github:ishita
         aceman; aceman-bugzilla@mozilla.net; mdn:aceman-bugzilla
         Pam Pierce; PamPierceLearnAboutGreen@github.com; github:PamPierceLearnAboutGreen
         David Rogers AKA "AL the X"; al-the-x@github.com; github:al-the-x
         Kushal; kushal.developer@gmail.com; github:9034725985
         Thierry Régagnon; tregagnon@github.com; github:tregagnon
         Christian Sonne; cers@mozilla.net; mdn:cers
         Yihang Ho; yihangho@mozilla.net; mdn:yihangho
         codeboyim; me@codeboy.im; github:me@codeboy.im
         Mo; Balfa@github.com; github:Balfa
         Hawken Rives; hawkrives@mozilla.net; mdn:hawkrives
         Fuqiao Xue; xfq@mozilla.net; mdn:xfq
         Peter; pwdst@mozilla.net; mdn:pwdst

# `<table>`

The **HTML `<table>` element** represents tabular data — that is, information presented in a
two-dimensional table comprised of rows and columns of cells containing data.

|  |  |
| :-- | :-- |
| **Content categories** | Flow content
| **Permitted content** | In this order:<br>an optional `<caption>` element,<br>zero or more `<colgroup>` elements,<br>an optional `<thead>` element,<br>either one of the following:<br>zero or more `<tbody>` elements<br>one or more `<tr>` elements<br>an optional `<tfoot>` element<br>
| **Tag omission** |None, both the starting and ending tag are mandatory. |
| **Permitted parents** | Any element that accepts flow content
| **Permitted ARIA roles** | Any |
| **DOM interface** | `HTMLTableElement` |

## Attributes

This element includes the [global attributes](/en/webfrontend/HTML_Global_Attributes).

## `<thead>`

The **HTML `<thead>` element** defines a set of rows defining the head of the columns of the table.

## `<tbody>`

The **HTML Table Body element (`<tbody>`)** encapsulates a set of table rows (`<tr>` elements),
indicating that they comprise the body of the table (`<table>`).

## `<tfoot>`

The HTML `<tfoot>` element defines a set of rows summarizing the columns of the table.

## `<th>`

The **HTML `<th>` element** defines a cell as header of a group of table cells. The exact nature of
this group is defined by the `scope` and `headers` attributes.

## `<tr>`

The **HTML `<tr>` element** defines a row of cells in a table. The row's cells can then be
established using a mix of `<td>` (data cell) and `<th>` (header cell) elements.

### `<td>`

The **HTML `<td>` element** defines a cell of a table that contains data.
It participates in the table model.

## `<caption>`

The **HTML Table Caption element (`<caption>`)** specifies the caption (or title) of a table,
and if used is always the first child of a `<table>`. Its styling and physical position relative to
the table may be changed using the CSS `caption-side` and `text-align` properties.

## `<colgroup>`

The **HTML `<colgroup>` element** defines a group of columns within a table.

### `<col>`

The **HTML `<col>` element** defines a column within a table and is used for defining common
semantics on all common cells. It is generally found within a `<colgroup>` element.

## Examples

### Simple Table

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

### More Examples

```html
<p>Simple table with header</p>
<table>
  <tr>
    <th>First name</th>
    <th>Last name</th>
  </tr>
  <tr>
    <td>John</td>
    <td>Doe</td>
  </tr>
  <tr>
    <td>Jane</td>
    <td>Doe</td>
  </tr>
</table>

<p>Table with thead, tfoot, and tbody</p>
<table>
  <thead>
    <tr>
      <th>Header content 1</th>
      <th>Header content 2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Body content 1</td>
      <td>Body content 2</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <td>Footer content 1</td>
      <td>Footer content 2</td>
    </tr>
  </tfoot>
</table>

<p>Table with colgroup</p>
<table>
  <colgroup span="4"></colgroup>
  <tr>
    <th>Countries</th>
    <th>Capitals</th>
    <th>Population</th>
    <th>Language</th>
  </tr>
  <tr>
    <td>USA</td>
    <td>Washington, D.C.</td>
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
    <col style="background-color: #0f0;">
    <col span="2">
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

## Accessibility Concerns

### Captions

By supplying a `<caption>` element whose value clearly and concisely describes the table's purpose,
it helps the people decide if they need to read the rest of the table content or skip over it.

This helps people navigating with the aid of assistive technology such as a screen reader, people
experiencing low vision conditions, and people with cognitive concerns.

- [MDN Adding a caption to your table with `<caption>`](https://wiki.developer.mozilla.org/en-US/docs/Learn/HTML/Tables/Advanced#Adding_a_caption_to_your_table_with_%3Ccaption%3E)
- [Caption & Summary • Tables • W3C WAI Web Accessibility Tutorials](https://www.w3.org/WAI/tutorials/tables/caption-summary/)

### Scoping rows and columns

The `scope` attribute on header elements is redundant in simple contexts, because scope is inferred.
However, some assistive technologies may fail to draw correct inferences, so specifying header scope
may improve user experiences. In complex tables, scope can be specified so as to provide necessary
information about the cells related to a header.

```html
<table>
  <caption>Color names and values</caption>
  <tbody>
    <tr>
      <th scope="col">Name</th>
      <th scope="col">HEX</th>
      <th scope="col">HSLa</th>
      <th scope="col">RGBa</th>
    </tr>
    <tr>
      <th scope="row">Teal</th>
      <td><code>#51F6F6</code></td>
      <td><code>hsla(180, 90%, 64%, 1)</code></td>
      <td><code>rgba(81, 246, 246, 1)</code></td>
    </tr>
    <tr>
      <th scope="row">Goldenrod</th>
      <td><code>#F6BC57</code></td>
      <td><code>hsla(38, 90%, 65%, 1)</code></td>
      <td><code>rgba(246, 188, 87, 1)</code></td>
    </tr>
  </tbody>
</table>
```

Providing a declaration of `scope="col"` on a `<th>` element will help describe that the cell is at
the top of a column. Providing a declaration of `scope="row"` on a `<td>` element will help describe
that the cell is the first in a row.

- MDN Tables for visually impaired users
- Tables with two headers • Tables • W3C WAI Web Accessibility Tutorials
- Tables with irregular headers • Tables • W3C WAI Web Accessibility Tutorials
- H63: Using the scope attribute to associate header cells and data cells in data tables | W3C
Techniques for WCAG 2.0

### Complicated tables

Assistive technology such as screen readers may have difficulty parsing tables that are so complex
that header cells can’t be associated in a strictly horizontal or vertical way. This is typically
indicated by the presence of the `colspan` and `rowspan` attributes.

Ideally, consider alternate ways to present the table's content, including breaking it apart into a
collection of smaller, related tables that don't have to rely on using the `colspan` and `rowspan`
attributes. In addition to helping people who use assistive technology understand the table's content,
this may also benefit people with cognitive concerns who may have difficulty understanding the
associations the table layout is describing.

If the table cannot be broken apart, use a combination of the `id` and `headers`
attributes to programmatically associate each table cell with the header(s) the cell is associated with.

- [MDN Tables for visually impaired users](https://wiki.developer.mozilla.org/en-US/docs/Learn/HTML/Tables/Advanced#Tables_for_visually_impaired_users)
- [Tables with multi-level headers • Tables • W3C WAI Web Accessibility Tutorials](https://www.w3.org/WAI/tutorials/tables/multi-level/)
- [H43: Using id and headers attributes to associate data cells with header cells in data tables | Techniques for W3C WCAG 2.0](https://www.w3.org/TR/WCAG20-TECHS/H43.html)
- [Creating a bar chart from a HTML table](http://www.coding-dude.com/wp/html5/bar-chart-html/)

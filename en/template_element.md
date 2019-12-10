TOPICS: <template>
AUTHORS: Eric Shepherd; eshepherd@mozilla.com; github:a2sheppy
         Janet Swisher; jmswisher@github.com; github:jmswisher
         hinell; al.neodim@gmail.com; github:hinell
         Michael[tm] Smith; mike@w3.org; github:sideshowbarker
         Chris Mills; chrisdavidmills@mozilla.net; mdn:chrisdavidmills
         Connor Lanigan; dev@connorlanigan.com; github:connorlanigan
         ExE Boss; ExE-Boss@github.com; github:ExE-Boss
         Masahiro Fujimoto; mfujimot@gmail.com; github:mfuji09
         Ariel Viera; ariel.viera@gmail.com; github:avierax
         Teoli; teoli@mozilla.net; mdn:teoli
         Thomas Tortorini; Mr21@mozilla.net; mdn:Mr21
         Sebastian Zartner; SebastianZ@github.com; github:SebastianZ
         Trevor Hobson; trevorhobson@github.com; github:trevorhobson
         Rouven Weßling; realityking@github.com; github:realityking
         Jérémie Patonnier; Jeremie@mozilla.net; mdn:Jeremie
         Sphinx; SphinxKnight@github.com; github:SphinxKnight
         Karen Scarfone; kscarfone@mozilla.net; mdn:kscarfone

# `<template>`

The **HTML Content Template (`<template>`)** element is a mechanism for holding HTML that is not to
be rendered immediately when a page is loaded but may be instantiated
subsequently during runtime using JavaScript.

Think of a template as a content fragment that is being stored for subsequent use in the document.
While the parser does process the contents of the `<template>` element while loading the page,
it does so only to ensure that those contents are valid; the element's contents are not rendered, however.

|  |  |
| :-- | :-- |
| **Content categories** | Metadata content, flow content, phrasing content, script-supporting element
| **Permitted content** | No restrictions
| **Tag omission** | None, both the starting and ending tag are mandatory.
| **Permitted parents** | [`<body>`](/en/webfrontend/<body>), [`<frameset>`](/en/webfrontend/<frameset>), [`<head>`](/en/webfrontend/<head>), [`<dl>`](/en/webfrontend/<dl>) and [`<colgroup>`](/en/webfrontend/<colgroup>) without a `span` attribute |
| **Permitted ARIA roles** | None |
| **DOM interface** | `HTMLTemplateElement` |

## Attributes

This element only includes the [global attributes](https://wiki.developer.mozilla.org/en-US/docs/HTML/Global_attributes).

## Examples

First we start with the HTML portion of the example.

```html
<table id="producttable">
  <thead>
    <tr>
      <td>UPC_Code</td>
      <td>Product_Name</td>
    </tr>
  </thead>
  <tbody>
    <!-- existing data could optionally be included here -->
  </tbody>
</table>

<template id="productrow">
  <tr>
    <td class="record"></td>
    <td></td>
  </tr>
</template>
```

First, we have a table into which we will later insert content using JavaScript code. Then comes
the template, which describes the structure of an HTML fragment representing a single table row.

Now that the table has been created and the template defined, we use JavaScript to insert rows into
the table, with each row being constructed using the template as its basis.

```javascript
// Test to see if the browser supports the HTML template element by checking
// for the presence of the template element's content attribute.
if ('content' in document.createElement('template')) {

    // Instantiate the table with the existing HTML tbody
    // and the row with the template
    var template = document.querySelector('#productrow');

    // Clone the new row and insert it into the table
    var tbody = document.querySelector("tbody");
    var clone = document.importNode(template.content, true);
    var td = clone.querySelectorAll("td");
    td0].textContent = "1235646565";
    td1].textContent = "Stuff";

    tbody.appendChild(clone);

    // Clone the new row and insert it into the table
    var clone2 = document.importNode(template.content, true);
    td = clone2.querySelectorAll("td");
    td0].textContent = "0384928528";
    td1].textContent = "Acme Kidney Beans 2";

    tbody.appendChild(clone2);

} else {
  // Find another way to add the rows to the table because
  // the HTML template element is not supported.
}
```

The result is the original HTML table, with two new rows appended to it via JavaScript:

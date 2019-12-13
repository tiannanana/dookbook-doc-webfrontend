TOPICS: <datalist>
AUTHORS: Masahiro Fujimoto; mfujimot@gmail.com; github:mfuji09
         Jacob Pratt; jhpratt@protonmail.com; mdn:jhpratt
         Sphinx; SphinxKnight@github.com; github:SphinxKnight
         Teoli; teoli@mozilla.net; mdn:teoli
         Michael[tm] Smith; mike@w3.org; github:sideshowbarker
         Eric Shepherd; eshepherd@mozilla.com; github:a2sheppy
         Sebastian Zartner; SebastianZ@github.com; github:SebastianZ
         Chris Mills; chrisdavidmills@mozilla.net; mdn:chrisdavidmills
         Jérémie Patonnier; Jeremie@mozilla.net; mdn:Jeremie
         Dan Scott; dbs@mozilla.net; mdn:dbs
         Akash Agrawal; akagr@outlook.com; github:akagr
         Karen Scarfone; kscarfone@mozilla.net; mdn:kscarfone
         Frédéric Bourgeon; FredericBourgeon@github.com; github:FredericBourgeon
         Janet Swisher; jmswisher@github.com; github:jmswisher
         Thierry Régagnon; tregagnon@github.com; github:tregagnon
         Keiichi; ethertank@mozilla.net; mdn:ethertank
         紫云飞; ziyunfei@mozilla.net; mdn:ziyunfei
         Abraham Williams; abraham@abrah.am; github:abraham
         Christian Sonne; cers@mozilla.net; mdn:cers
         Florian Scholz; fscholz@mozilla.net; mdn:fscholz
         Jonathan Wilsson; jwilsson@github.com; github:jwilsson

# `<datalist>`

The **HTML `<datalist>` element** contains a set of [`<option>`](/en/webfrontend/<option>) elements
that represent the values available for other controls.

|  |  |
| :-- | :-- |
| **Content categories** | Flow content, phrasing content. |
| **Permitted content** | Either phrasing content or zero or more [`<option>`](/en/webfrontend/<option>) elements. |
| **Tag omission** | None, both the starting and ending tag are mandatory. |
| **Permitted parents** | Any element that accepts phrasing content. |
| **Permitted ARIA roles** | None |
| **DOM interface** | `HTMLDataListElement` |

## Attributes

This element has no other attributes than the [global attributes](/en/webfrontend/HTML_Global_Attributes),
common to all elements.

## Examples

```html
<label for="myBrowser">Choose a browser from this list:</label>
<input list="browsers" id="myBrowser" name="myBrowser" />
<datalist id="browsers">
  <option value="Chrome">
  <option value="Firefox">
  <option value="Internet Explorer">
  <option value="Opera">
  <option value="Safari">
  <option value="Microsoft Edge">
</datalist>
```

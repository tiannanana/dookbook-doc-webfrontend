TOPICS: <data>
AUTHORS: Masahiro Fujimoto; mfujimot@gmail.com; github:mfuji09
         Sphinx; SphinxKnight@github.com; github:SphinxKnight
         Yuhei Yasuda; yuhei.yasuda1003@gmail.com; github:yuheiy
         Anton Ingfors; antoningfors@github.com; github:antoningfors
         Teoli; teoli@mozilla.net; mdn:teoli
         Michael[tm] Smith; mike@w3.org; github:sideshowbarker
         Sebastian Zartner; SebastianZ@github.com; github:SebastianZ
         Jérémie Patonnier; Jeremie@mozilla.net; mdn:Jeremie
         Karen Scarfone; kscarfone@mozilla.net; mdn:kscarfone
         Chris DeLuca; contact@chrisdeluca.me; github:bronzehedwick
         Thierry Régagnon; tregagnon@github.com; github:tregagnon
         Eric Shepherd; eshepherd@mozilla.com; github:a2sheppy
         Nickolay Ponomarev; asqueella@gmail.com; github:nickolay
         Trevor Hobson; trevorhobson@github.com; github:trevorhobson
         Keiichi; ethertank@mozilla.net; mdn:ethertank

# `<data>`

The **HTML `<data>` element** links a given content with a machine-readable translation. If the
content is time- or date-related, the [`<time>`](/en/webfrontend/<time>) element must be used.

|  |  |
| :-- | :-- |
| **Content categories** | Flow content, phrasing content, palpable content.
| **Permitted content** | Phrasing content.
| **Tag omission** | None, both the starting and ending tag are mandatory.
| **Permitted parents** | Any element that accepts phrasing content.
| **DOM interface** | `HTMLDataElement`

## Attributes

This element's attributes include the [global attributes](https://wiki.developer.mozilla.org/en-US/docs/HTML/Global_attributes).

| Attribute | Description |
| :-- | :-- |
| `value` | This attribute specifies the machine-readable translation of the content of the element.

## Example

The following example displays product names but also associates each name with a product number.

```html
<p>New Products</p>
<ul>
 <li><data value="398">Mini Ketchup</data></li>
 <li><data value="399">Jumbo Ketchup</data></li>
 <li><data value="400">Mega Jumbo Ketchup</data></li>
</ul>
```

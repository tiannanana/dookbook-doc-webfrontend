TOPICS: <bdo>
AUTHORS: Connor Shea; connor.james.shea@gmail.com; github:connorshea
         Yuhei Yasuda; yuhei.yasuda1003@gmail.com; github:yuheiy
         Eric Shepherd; eshepherd@mozilla.com; github:a2sheppy
         Teoli; teoli@mozilla.net; mdn:teoli
         Michael[tm] Smith; mike@w3.org; github:sideshowbarker
         Sebastian Zartner; SebastianZ@github.com; github:SebastianZ
         Jérémie Patonnier; Jeremie@mozilla.net; mdn:Jeremie
         Karen Scarfone; kscarfone@mozilla.net; mdn:kscarfone
         Onur Avsar; avsaro@mozilla.net; mdn:avsaro
         Keiichi; ethertank@mozilla.net; mdn:ethertank
         C. Stipkovic; clauber.halic@gmail.com; github:cstipkovic
         Christian Sonne; cers@mozilla.net; mdn:cers
         Jonathan Wilsson; jwilsson@github.com; github:jwilsson
         Janet Swisher; jmswisher@github.com; github:jmswisher

# `<bdo>`

The **HTML Bidirectional Text Override element (`<bdo>`)** overrides the current directionality of
text, so that the text within is rendered in a different direction.

The text's characters are drawn from the starting point in the given direction; the individual
characters' orientation is not affected (so characters don't get drawn backward, for example).

|  |  |
| :-- | :-- |
| **Content categories** | Flow content, phrasing content, palpable content. |
| **Permitted content** | Phrasing content. |
| **Tag omission** | None, both the starting and ending tag are mandatory. |
| **Permitted parents** | Any element that accepts phrasing content.
| **Permitted ARIA roles** | Any |
| **DOM interface** | `HTMLElement` Up to Gecko 1.9.2 (Firefox 4) inclusive, Firefox implements the `HTMLSpanElement` interface for this element.

## Attributes

This element's attributes include the [global attributes](https://wiki.developer.mozilla.org/en-US/docs/HTML/Global_attributes).

| Attribute | Description |
| :-- | :-- |
| `dir` | The direction in which text should be rendered in this element's contents. Possible values are:<br>`ltr`: Indicates that the text should go in a left-to-right direction.<br>`rtl`: Indicates that the text should go in a right-to-left direction.

## Examples

```html
<!-- Switch text direction -->
<p>This text will go left to right.</p>
<p><bdo dir="rtl">This text will go right
to left.</bdo></p>
```

## Notes

The HTML 4 specification did not specify events for this element; they were added in XHTML.
This is most likely an oversight.

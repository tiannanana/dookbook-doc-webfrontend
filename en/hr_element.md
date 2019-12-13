TOPICS: <hr>
AUTHORS: Masahiro Fujimoto; mfujimot@gmail.com; github:mfuji09
         Jon Petto; jpetto@mozilla.net; mdn:jpetto
         Michael[tm] Smith; mike@w3.org; github:sideshowbarker
         Sphinx; SphinxKnight@github.com; github:SphinxKnight
         Eric Shepherd; eshepherd@mozilla.com; github:a2sheppy
         Teoli; teoli@mozilla.net; mdn:teoli
         Sebastian Zartner; SebastianZ@github.com; github:SebastianZ
         Chris Rebert; cvrebert@mozilla.net; mdn:cvrebert
         Karen Scarfone; kscarfone@mozilla.net; mdn:kscarfone
         Keiichi; ethertank@mozilla.net; mdn:ethertank
         Christian Sonne; cers@mozilla.net; mdn:cers
         Janet Swisher; jmswisher@github.com; github:jmswisher
         Florian Scholz; fscholz@mozilla.net; mdn:fscholz
         Nickolay Ponomarev; asqueella@gmail.com; github:nickolay

# `<hr>`

The **HTML `<hr>` element** represents a thematic break between paragraph-level elements: for example,
a change of scene in a story, or a shift of TOPICS within a section.

Historically, this has been presented as a horizontal rule or line. While it may still be displayed
as a horizontal rule in visual browsers, this element is now defined in semantic terms, rather than
presentational terms, so if you wish to draw a horizontal line, you should do so using appropriate CSS.

|  |  |
| :-- | :-- |
| **Content categories** | Flow content. |
| **Permitted content** | None, it is an empty element. |
| **Tag omission** | It must have start tag, but must not have an end tag. |
| **Permitted parents** | Any element that accepts flow content.|
| **Permitted ARIA roles** | `presentation` |
| **DOM interface** | `HTMLHRElement` |

## Attributes

This element's attributes include the [global attributes](/en/webfrontend/HTML_Global_Attributes).

| Attribute | Description |
| :-- | :-- |
| `align` | Sets the alignment of the rule on the page. If no value is specified, the default value is left.
| `color` | Sets the color of the rule through color name or hexadecimal value.
| `noshade` | Sets the rule to have no shading.
| `size` | Sets the height, in pixels, of the rule.
| `width` | Sets the length of the rule on the page through a pixel or percentage value.

## Example

```html
<p>
  This is the first paragraph of text.
  This is the first paragraph of text.
  This is the first paragraph of text.
  This is the first paragraph of text.
</p>

<hr>

<p>
  This is the second paragraph of text.
  This is the second paragraph of text.
  This is the second paragraph of text.
  This is the second paragraph of text.
</p>
```

TOPICS: <code>
AUTHORS: Masahiro Fujimoto; mfujimot@gmail.com; github:mfuji09
         Sphinx; SphinxKnight@github.com; github:SphinxKnight
         Rory O’Kane; rory@roryokane.com; github:roryokane
         Yuhei Yasuda; yuhei.yasuda1003@gmail.com; github:yuheiy
         Cristian Trifan; criss.trifan@gmail.com; github:crissdev
         Eric Shepherd; eshepherd@mozilla.com; github:a2sheppy
         Teoli; teoli@mozilla.net; mdn:teoli
         Sebastian Zartner; SebastianZ@github.com; github:SebastianZ
         Carlo Martini; CarloMartini@mozilla.net; mdn:CarloMartini
         Michael[tm] Smith; mike@w3.org; github:sideshowbarker
         Jérémie Patonnier; Jeremie@mozilla.net; mdn:Jeremie
         Karen Scarfone; kscarfone@mozilla.net; mdn:kscarfone
         Thierry Régagnon; tregagnon@github.com; github:tregagnon
         Keiichi; ethertank@mozilla.net; mdn:ethertank
         Les Orchard; me@lmorchard.com; github:lmorchard
         Christian Sonne; cers@mozilla.net; mdn:cers
         Jonathan Wilsson; jwilsson@github.com; github:jwilsson
         Janet Swisher; jmswisher@github.com; github:jmswisher

# `<code>`

The **HTML `<code>` element** displays its contents styled in a fashion intended to indicate that
the text is a short fragment of computer code. By default, the content text is displayed using the
user agent's default monospace font.

|  |  |
| :-- | :-- |
| **Content categories** | Flow content, phrasing content, palpable content.
| **Permitted content** | Phrasing content.
| **Tag omission** | None, both the starting and ending tag are mandatory.
| **Permitted parents** | Any element that accepts phrasing content.
| **Permitted ARIA roles** | Any
| **DOM interface** | `HTMLElement` Up to Gecko 1.9.2 (Firefox 4) inclusive, Firefox implements the `HTMLSpanElement` interface for this element.

## Attributes

This element only includes the [global attributes](/en/webfrontend/HTML_Global_Attributes).

## Example

A paragraph of text that includes `<code>`:

```html
<p>The function <code>selectAll()</code> highlights all the text in the
input field so the user can, for example, copy or delete the text.</p>
```

## Notes

To represent multiple lines of code, wrap the `<code>` element within a [`<pre>`](/en/webfrontend/<pre>)
element. The `<code>` element by itself only represents a single phrase of code or line of code.

A CSS rule can be defined for the code selector to override the browser's default font face.
Preferences set by the user might take precedence over the specified CSS.

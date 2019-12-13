TOPICS: <noscript>
AUTHORS: Masahiro Fujimoto; mfujimot@gmail.com; github:mfuji09
         Florian Scholz; fscholz@mozilla.net; mdn:fscholz
         Michael[tm] Smith; mike@w3.org; github:sideshowbarker
         Sebastian Zartner; SebastianZ@github.com; github:SebastianZ
         Jérémie Patonnier; Jeremie@mozilla.net; mdn:Jeremie
         Karen Scarfone; kscarfone@mozilla.net; mdn:kscarfone
         Teoli; teoli@mozilla.net; mdn:teoli
         Eric Shepherd; eshepherd@mozilla.com; github:a2sheppy
         Keiichi; ethertank@mozilla.net; mdn:ethertank
         Pikadude No. 1; PikadudeNo1@github.com; github:PikadudeNo1
         Christian Sonne; cers@mozilla.net; mdn:cers

# `<noscript>`

The **HTML `<noscript>` element** defines a section of HTML to be inserted if a script type on the
page is unsupported or if scripting is currently turned off in the browser.

|  |  |
| :-- | :-- |
| **Content categories** | Metadata content, flow content, phrasing content. |
| **Permitted content** | When scripting is disabled and when it is a descendant of the [`<head>`](/en/webfrontend/<head>) element: in any order, zero or more [`<link>`](/en/webfrontend/<link>) elements, zero or more `style` elements, and zero or more [`<meta>`](/en/webfrontend/<meta>) elements.<br>When scripting is disabled and when it isn't a descendant of the [`<head>`](/en/webfrontend/<head>) element: any transparent content, but no `<noscript>` element must be among its descendants.<br>Otherwise: flow content or phrasing content.|
| **Tag omission** | None, both the starting and ending tag are mandatory.|
| **Permitted parents** | Any element that accepts phrasing content, if there are no ancestor `<noscript>` element, or in a [`<head>`](/en/webfrontend/<head>) element (but only for an HTML document), here again if there are no ancestor `<noscript>` element.|
| **Permitted ARIA roles** | None |
| **DOM interface** | `HTMLElement` |

## Attributes

This element only includes the [global attributes](/en/webfrontend/HTML_Global_Attributes).

```html
<noscript>
  <!-- anchor linking to external file -->
  <a href="http://www.mozilla.com/">External Link</a>
</noscript>
<p>Rocks!</p>
```

## Example

```html
<noscript>
  <!-- anchor linking to external file -->
  <a href="https://www.mozilla.com/">External Link</a>
</noscript>
<p>Rocks!</p>
```

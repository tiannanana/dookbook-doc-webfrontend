TOPICS: <progress>
AUTHORS: Jongryul Yang; urty5656@gmail.com; github:alattalatta
         Masahiro Fujimoto; mfujimot@gmail.com; github:mfuji09
         Sphinx; SphinxKnight@github.com; github:SphinxKnight
         Yuhei Yasuda; yuhei.yasuda1003@gmail.com; github:yuheiy
         Scott O'Hara; scottaohara@github.com; github:scottaohara
         Eric Shepherd; eshepherd@mozilla.com; github:a2sheppy
         Teoli; teoli@mozilla.net; mdn:teoli
         Michael[tm] Smith; mike@w3.org; github:sideshowbarker
         Chris Rebert; cvrebert@mozilla.net; mdn:cvrebert
         Sebastian Zartner; SebastianZ@github.com; github:SebastianZ
         John Whitlock; John-Whitlock@ieee.org; github:jwhitlock
         Blixa Morgan; MrMakeIt@mozilla.net; mdn:MrMakeIt
         Claude Pache; claudepache@mozilla.net; mdn:claudepache
         Karen Scarfone; kscarfone@mozilla.net; mdn:kscarfone
         Peter; pwdst@mozilla.net; mdn:pwdst
         Kumar Harsh; khs@mozilla.net; mdn:khs
         Thierry Régagnon; tregagnon@github.com; github:tregagnon
         Jérémie Patonnier; Jeremie@mozilla.net; mdn:Jeremie
         Pablo Terradillos; tehsis@github.com; github:tehsis
         Keiichi; ethertank@mozilla.net; mdn:ethertank
         紫云飞; ziyunfei@mozilla.net; mdn:ziyunfei
         Jonathan Wilsson; jwilsson@github.com; github:jwilsson
         Trevor Hobson; trevorhobson@github.com; github:trevorhobson
         Christian Sonne; cers@mozilla.net; mdn:cers
         Florian Scholz; fscholz@mozilla.net; mdn:fscholz
         Gordon P. Hemsley; GPHemsley@mozilla.net; mdn:GPHemsley
         Yann Brelière; Yann Dìnendal@mozilla.net; mdn:Yann Dìnendal

# `<progress>`

The **HTML `<progress>` element** displays an indicator showing the completion progress of a task,
typically displayed as a progress bar.

|  |  |
| :-- | :-- |
| **Content categories** | `Flow content`, `phrasing content`, labelable content, palpable content.|
| **Permitted content** | Phrasing content, but there must be no `<progress>` element among its descendants.|
| **Tag omission** | None, both the starting and ending tag are mandatory. |
| **Permitted parents** | Any element that accepts phrasing content. |
| **Permitted ARIA roles** | None |
| **DOM interface** | `HTMLProgressElement` |

## Attributes

This element includes the [global attributes](https://wiki.developer.mozilla.org/en-US/docs/HTML/Global_attributes).

| Attribute | Description |
| :-- | :-- |
| `max` | This attribute describes how much work the task indicated by the `progress` element requires. The `max` attribute, if present, must have a value greater than zero and be a valid floating point number. The default value is 1.
| `value` | This attribute specifies how much of the task that has been completed. It must be a valid floating point number between 0 and `max`, or between 0 and 1 if `max` is omitted. If there is no `value` attribute, the progress bar is indeterminate; this indicates that an activity is ongoing with no indication of how long it is expected to take.

!!! warn "Don't try this at home"
    NOTE: The minimum value is always 0 and the `min` attribute is not allowed for the progress
    element. You can use the `-moz-orient` CSS property to specify whether the progress bar
    should be rendered horizontally (the default) or vertically.

!!! warn "Don't try this at home"
    NOTE: The `:indeterminate` pseudo-class can be used to match against indeterminate
    progress bars. To change the progress bar to indeterminate after giving it a value you must
    remove the value attribute with `element.removeAttribute("value")`

## Examples

```html
<progress value="70" max="100">70 %</progress>
```

TOPICS: <output>
AUTHORS: ExE Boss; ExE-Boss@github.com; github:ExE-Boss
         Masahiro Fujimoto; mfujimot@gmail.com; github:mfuji09
         Jongryul Yang; urty5656@gmail.com; github:alattalatta
         Eric Shepherd; eshepherd@mozilla.com; github:a2sheppy
         Gerald; geraldfullam@github.com; github:geraldfullam
         Taylor Hunt; tigt@github.com; github:tigt
         Yuhei Yasuda; yuhei.yasuda1003@gmail.com; github:yuheiy
         Jan Kühle; frigus02@github.com; github:frigus02
         Teoli; teoli@mozilla.net; mdn:teoli
         Michael[tm] Smith; mike@w3.org; github:sideshowbarker
         Sebastian Zartner; SebastianZ@github.com; github:SebastianZ
         Claude Pache; claudepache@mozilla.net; mdn:claudepache
         Daniel Imms; Tyriar@github.com; github:Tyriar
         Karen Scarfone; kscarfone@mozilla.net; mdn:kscarfone
         Marat Tanalin; MTonly@mozilla.net; mdn:MTonly
         Keiichi; ethertank@mozilla.net; mdn:ethertank
         M.S.Rishikesh; msrishikesh@mozilla.net; mdn:msrishikesh
         Christian Sonne; cers@mozilla.net; mdn:cers
         Florian Scholz; fscholz@mozilla.net; mdn:fscholz
         Jonathan Wilsson; jwilsson@github.com; github:jwilsson
         Janet Swisher; jmswisher@github.com; github:jmswisher

# `<output>`

The **HTML Output element (`<output>`)** is a container element into which a site or app can inject
the results of a calculation or the outcome of a user action.

|  |  |
| :-- | :-- |
| **Content categories** | Flow content, phrasing content, listed, labelable, resettable form-associated element, palpable content.|
| **Permitted content** | Phrasing content. |
| **Tag omission** | None, both the starting and ending tag are mandatory.|
| **Permitted parents** | Any element that accepts phrasing content.|
| **Permitted ARIA roles** | Any |
| **DOM interface** | `HTMLOutputElement` |

## Attributes

This element includes the [global attributes](/en/webfrontend/HTML_Global_Attributes).

| Attribute | Description |
| :-- | :-- |
| `for` | A space-separated list of other elements’ `id`s, indicating that those elements contributed input values to (or otherwise affected) the calculation.
| `form` | The form element that this element is associated with (its "form owner"). The value of the attribute must be the id of a [`<form>`](/en/webfrontend/<form>) element in the same document. This attribute is not needed if the `<output>` element is a descendant of a [`<form>`](/en/webfrontend/<form>) element (in which case that form is the form owner), or if the `<output>` element isn't associated with a form at all.
| `name` | The element's name; used to identify this `<output>` during form submission.

## Example

This form provides a slider whose value can range between 0 and 100. and an [`<input>`](/en/webfrontend/<input>)
element into which you can enter a second number. The two numbers are added together and the result is
displayed in the `<output>` element each time the value of any of the controls changes.

```html
<form oninput="result.value=parseInt(a.value)+parseInt(b.value)">
  <input type="range" name="b" value="50" /> +
  <input type="number" name="a" value="10" /> =
  <output name="result">60</output>
</form>
```

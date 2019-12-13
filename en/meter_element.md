TOPICS: <meter>
AUTHORS: Masahiro Fujimoto; mfujimot@gmail.com; github:mfuji09
         Sphinx; SphinxKnight@github.com; github:SphinxKnight
         Teoli; teoli@mozilla.net; mdn:teoli
         Michael[tm] Smith; mike@w3.org; github:sideshowbarker
         Sebastian Zartner; SebastianZ@github.com; github:SebastianZ
         Daniel Davis; tagawa@github.com; github:tagawa
         Karen Scarfone; kscarfone@mozilla.net; mdn:kscarfone
         Thierry Régagnon; tregagnon@github.com; github:tregagnon
         Eric Shepherd; eshepherd@mozilla.com; github:a2sheppy
         Keiichi; ethertank@mozilla.net; mdn:ethertank
         Jérémie Patonnier; Jeremie@mozilla.net; mdn:Jeremie
         Trevor Hobson; trevorhobson@github.com; github:trevorhobson
         Jonathan Wilsson; jwilsson@github.com; github:jwilsson
         Christian Sonne; cers@mozilla.net; mdn:cers
         Florian Scholz; fscholz@mozilla.net; mdn:fscholz

# `<meter>`

The **HTML `<meter>` element** represents either a scalar value within a known
range or a fractional value.

|  |  |
| :-- | :-- |
| **Content categories** | Flow content, phrasing content, labelable content, palpable content.|
| **Permitted content** | Phrasing content, but there must be no `<meter>` element among its descendants.|
| **Tag omission** | None, both the starting and ending tag are mandatory. |
| **Permitted parents** | Any element that accepts phrasing content. |
| **Permitted ARIA roles** | None |
| **DOM interface** | `HTMLMeterElement` |

## Attributes

This element includes the [global attributes](/en/webfrontend/HTML_Global_Attributes).

| Attribute | Description |
| :-- | :-- |
| `value` | The current numeric value. This must be between the minimum and maximum values (`min` attribute and `max` attribute) if they are specified. If unspecified or malformed, the value is 0. If specified, but not within the range given by the `min` attribute and `max` attribute, the value is equal to the nearest end of the range.<br>**Note:** Unless the `value` attribute is between `0` and `1` (inclusive), the `min` and `max` attributes should define the range so that the `value` attribute's value is within it
| `min` | The lower numeric bound of the measured range. This must be less than the maximum value (`max` attribute), if specified. If unspecified, the minimum value is 0.
| `max` | The upper numeric bound of the measured range. This must be greater than the minimum value (`min` attribute), if specified. If unspecified, the maximum value is 1.
| `low` | The upper numeric bound of the low end of the measured range. This must be greater than the minimum value (`min` attribute), and it also must be less than the high value and maximum value (`high` attribute and `max` attribute, respectively), if any are specified. If unspecified, or if less than the minimum value, the `low` value is equal to the minimum value.
| `high` | The lower numeric bound of the high end of the measured range. This must be less than the maximum value (`max` attribute), and it also must be greater than the `low` value and minimum value (low attribute and `min` attribute, respectively), if any are specified. If unspecified, or if greater than the maximum value, the `high` value is equal to the maximum value.
| `optimum` | This attribute indicates the optimal numeric value. It must be within the range (as defined by the `min` attribute and `max` attribute). When used with the `low` attribute and `high` attribute, it gives an indication where along the range is considered preferable. For example, if it is between the `min` attribute and the `low` attribute, then the lower range is considered preferred.
| `form` | This attribute associates the element with a `form` element that has ownership of the `meter` element. For example, a `meter` might be displaying a range corresponding to an `input` element of `type` number. This attribute is only used if the `meter` element is being used as a form-associated element; even then, it may be omitted if the element appears as a descendant of a `form` element.

## Examples

### Simple example

```html
<p>Heat the oven to <meter min="200" max="500"
  value="350">350 degrees</meter>.</p>
```

### High and Low range example

Note that in this example the `min` attribute is omitted; this is allowed, as it will default to 0.

```html
<p>He got a <meter low="69" high="80" max="100"
  value="84">B</meter> on the exam.</p>
```

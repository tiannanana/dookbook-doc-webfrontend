TOPICS: <progress>

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

This element includes the [global attributes](/en/webfrontend/HTML_Global_Attributes).

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

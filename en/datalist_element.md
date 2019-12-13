TOPICS: <datalist>

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

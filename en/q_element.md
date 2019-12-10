TOPICS: <q>

# HTML Inline Quotation Element: `<q>`

The **HTML `<q>` element** indicates that the enclosed text is a **short inline quotation**. Most modern
browsers implement this by surrounding the text in quotation marks. This element is intended for
short quotations that don't require paragraph breaks; for long quotations use
the [`<blockquote>`](/en/webfrontend/<blockquote>) element.

|  |  |
| :-- | :-- |
| **Content categories** | Flow content, phrasing content, palpable content.|
| **Permitted content** | Phrasing content.|
| **Tag omission** | None, both the starting and ending tag are mandatory.|
| **Permitted parents** | Any element that accepts phrasing content.|
| **Permitted ARIA roles** | Any |
| **DOM interface** | `HTMLQuoteElement` |

!!! warn "Usage note"
    Most modern browsers will automatically add quotation marks around text inside a `<q>`
    element. A style rule may be needed to add quotation marks in older browsers.

## Attributes

This element includes the [global attributes](/en/webfrontend/HTML_Global_attribute).

| Attribute | Description |
| :-- | :-- |
| `cite` | The value of this attribute is a URL that designates a source document or message for the information quoted. This attribute is intended to point to information explaining the context or the reference for the quote.

## Example

```html
<p>According to Mozilla's website,
  <q
  cite="https://www.mozilla.org/en-US/about/history/details/">Firefox 1.0
  was released in 2004 and became a big success.</q></p>
```

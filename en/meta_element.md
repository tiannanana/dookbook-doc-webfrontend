TOPICS: <meta>

# HTML Metadata Element: `<meta>`

The HTML `<meta>` element represents **metadata** that cannot be represented by other HTML meta-related
elements, like [`<base>`](/en/webfrontend/<base>), [`<link>`](/en/webfrontend/<link>),
[`<script>`](/en/webfrontend/<script>), [`<style>`](/en/webfrontend/<style>) or [`<title>`](/en/webfrontend/<title>).

## Meta

|  |  |
| :-- | :-- |
| **Content categories** | Metadata content. If the `itemprop` attribute is present: flow content, phrasing content.
| **Permitted content** | None, it is an empty element.
| **Tag omission** | As it is a void element, the start tag must be present and the end tag must not be present.
| **Permitted parents** | [`<meta charset>`](/en/webfrontend/<meta>_charset_attribute), [`<meta http-equiv>`](/en/webfrontend/<meta>_http-equiv_attribute): a [`<head>`](/en/webfrontend/<head>) element. If the `http-equiv` is not an encoding declaration, it can also be inside a [`<noscript>`](/en/webfrontend/<noscript>) element, itself inside a [`<head>`](/en/webfrontend/<head>) element.
| **Permitted ARIA roles** | None
| **DOM interface** | `HTMLMetaElement`

## Attributes

This element includes the [global attributes](/en/webfrontend/HTML_Global_Attributes).

!!! warn "Note"
    The attribute [`name`](/en/webfrontend/<meta>_name_attribute) has a specific meaning for the
    `<meta>` element, and the `itemprop` attribute must not be set on the same `<meta>` element that
    has any existing [`name`](/en/webfrontend/<meta>_name_attribute), [`http-equiv`](/en/webfrontend/<meta>_http-equiv_attribute)
    or [`charset`](/en/webfrontend/<meta>_charset_attribute) attributes.

| Attribute | Description |
| :-- | :-- |
| **[`charset`](/en/webfrontend/<meta>_charset_attribute)** | This attribute declares the page's **[[character encoding]]**. |
| **[`http-equiv`](/en/webfrontend/<meta>_http-equiv_attribute)** | Defines a **pragma directive**. The attribute is named *"http-equiv(alent)"* because all the allowed values are names of particular **HTTP headers**.
| **[`name`](/en/webfrontend/<meta>_name_attribute)** | This attribute defines the **name of a piece of document-level metadata**. It should not be set if one of the attributes `itemprop`, [`http-equiv`](/en/webfrontend/<meta>_http-equiv_attribute) or [`charset`](/en/webfrontend/<meta>_charset_attribute) is also set.
| **`content`** | This attribute contains the value for the [`http-equiv`](/en/webfrontend/<meta>_http-equiv_attribute) or [`name`](/en/webfrontend/<meta>_name_attribute) attribute, depending on which is used.

- `color-scheme`: Specifies one or more color schemes with which the document is compatible.
The browser will use this information in tandem with the user's browser or device settings to
determine what colors to use for everything from background and foregrounds to form controls and
scrollbars. The primary use for `<meta name="color-scheme">` is to indicate compatibility with—and
order of preference for—light and dark color modes.

The value of the `content` property for `color-scheme` may be one of the following:

### Normal

The document is unaware of color schemes and should simply be rendered using the default color palette.

### Light | Dark]+

One or more color schemes supported by the document. Specifying the same color scheme more than once
has the same effect as specifying it only once. Indicating multiple color schemes indicates that the
first scheme is preferred by the document, but that the second specified
scheme is acceptable if the user prefers it.

### Only Light

Indicates that the document only supports light mode, with a light background and dark foreground
colors. By specfication, `only dark` is not valid, because forcing a document to render in dark mode
when it isn't truly compatible with it can result in unreadable content; all major browsers default
to light mode if not otherwise configured.

For example, to indicate that a document prefers dark mode but does render
functionally in light mode as well:

```html
<meta name="color-scheme" content="dark light">
```

This works at the document level in the same way that the CSS `color-scheme` property lets
individual elements specify their preferred and accepted color schemes. Your styles can adapt to the
current color scheme using the `prefers-color-scheme` CSS media feature.

## Notes

Depending on the attributes set, the kind of metadata can be one of the following:

- If [`name`](/en/webfrontend/<meta>_name_attribute) is set, it is document-level metadata, applying
  to the whole page.
- If [`http-equiv`](/en/webfrontend/<meta>_http-equiv_attribute) is set, it is a pragma directive —
  information normally given by the web
server about how the web page is served.
- If [`charset`](/en/webfrontend/<meta>_charset_attribute) is set, it is a charset declaration — the
  character encoding used by the webpage.
- If `itemprop` is set, it is user-defined metadata — transparent for the user-agent as the
semantics of the metadata is user-specific.

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

- `theme-color` which indicates a suggested color that user agents should use to customize the display
of the page or of the surrounding user interface. The content attribute contains a valid CSS `<color>`.
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

- viewport, which gives hints about the size of the initial size of the viewport.
Used by mobile devices only.

### Values for the content of `<meta name="viewport">`

| Value | Possible subvalues | Description |
| :-- | :-- | :-- |
| `width` | A positive integer number, or the text `device-width` | Defines the pixel width of the viewport that you want the web site to be rendered at.
| `height` | A positive integer, or the text `device-height` |Defines the height of the viewport. Not used by any browser.
| `initial-scale` | A positive number between `0.0` and `10.0` | Defines the ratio between the device width (device-width in portrait mode or device-height in landscape mode) and the viewport size.
| `maximum-scale` | A positive number between `0.0` and `10.0` | Defines the maximum amount to zoom in. It must be greater or equal to the minimum-scale or the behaviour is undefined. Browser settings can ignore this rule and iOS10+ ignores it by default.
| `minimum-scale` | A positive number between `0.0` and `10.0` | Defines the minimum zoom level. It must be smaller or equal to the maximum-scale or the behaviour is undefined. Browser settings can ignore this rule and iOS10+ ignores it by default.
| `user-scalable` | `yes` or `no` | If set to no, the user is not able to zoom in the webpage. The default is yes. Browser settings can ignore this rule, and iOS10+ ignores it by default.

| Specification | Status | Comment |
| :-- | :-- | :-- |
| CSS Device Adaptation The definition of '`<meta name="viewport">`' in that specification. | Working Draft | Non-normatively describes the Viewport META element

See Also: `@viewport`

!!! warn "de-facto dominance"
    Though unstandardized, this declaration is respected by most mobile browsers due to de-facto dominance.
    The default values may vary between devices and browsers.

| Attribute | Description |
| :-- | :-- |
| `scheme` | This attribute defines the scheme in which metadata is described. A scheme is a context leading to the correct interpretations of the content value, like a format.

!!! error "Warning: it is obsolete"
    Do not use this value, as it is obsolete. There is no
    replacement as there was no real usage for it.

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

## Accessibility Concerns
  
### Viewport scaling

Disabling zooming capabilities by setting `user-scalable` to a value of no prevents people
experiencing low vision conditions from being able to read and understand page content.

- [MDN Understanding WCAG, Guideline 1.4 explanations](https://wiki.developer.mozilla.org/en-US/docs/Web/Accessibility/Understanding_WCAG/Perceivable#Guideline_1.4_Make_it_easier_for_users_to_see_and_hear_content_including_separating_foreground_from_background)
- [Understanding Success Criterion 1.4.4 | W3C Understanding WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-scale.html)

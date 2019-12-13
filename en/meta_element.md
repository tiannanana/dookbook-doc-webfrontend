TOPICS: <meta>

# `<meta>`

The HTML `<meta>` element represents **metadata** that cannot be represented by other HTML meta-related
elements, like [`<base>`](/en/webfrontend/<base>), [`<link>`](/en/webfrontend/<link>),
[`<script>`](/en/webfrontend/<script>), [`<style>`](/en/webfrontend/<style>) or [`<title>`](/en/webfrontend/<title>).

## Meta

|  |  |
| :-- | :-- |
| **Content categories** | Metadata content. If the itemprop attribute is present: flow content, phrasing content.
| **Permitted content** | None, it is an empty element.
| **Tag omission** | As it is a void element, the start tag must be present and the end tag must not be present.
| **Permitted parents** | `<meta charset>`,`<meta http-equiv>`: a [`<head>`](/en/webfrontend/<head>) element. If the http-equiv is not an encoding declaration, it can also be inside a [`<noscript>`](/en/webfrontend/<noscript>) element, itself inside a [`<head>`](/en/webfrontend/<head>) element.
| **Permitted ARIA roles** | None
| **DOM interface** | `HTMLMetaElement`

## Attributes

This element includes the [global attributes](/en/webfrontend/HTML_Global_Attributes).

!!! warn "Note"
    The attribute `name` has a specific meaning for the `<meta>` element, and the
    `itemprop` attribute must not be set on the same `<meta>` element that has any existing
    `name`, `http-equiv` or `charset` attributes.

| Attribute | Description |
| :-- | :-- |
| **`charset`** | This attribute declares the page's **[[character encoding]]**. It must contain a standard [[IANA]] [[MIME]] name for character encodings. Although the standard doesn't request a specific encoding, it suggests:<br> &nbsp;- Authors are *encouraged* to use **`UTF-8`**.<br> &nbsp;- Authors *should not* use ASCII-incompatible encodings to avoid security risk: browsers not supporting them may interpret harmful content as HTML. This happens with the `JIS_C6226-1983`, `JIS_X0212-1990`,`HZ-GB-2312`, `JOHAB`, the `ISO-2022` family and the `EBCDIC` family.<br> &nbsp;- **Note:** ASCII-incompatible encodings are those that don't map the 8-bit code points `0x20` to `0x7E` to the `0x0020` to `0x007E` Unicode code points)<br> &nbsp;- **Error:** Authors *must not* use `CESU-8`, `UTF-7`, `BOCU-1` and/or `SCSU` as cross-site scripting attacks with these encodings have been demonstrated.<br> &nbsp;- Authors *should not* use `UTF-32` because not all HTML5 encoding algorithms can distinguish it from `UTF-16`.<br> &nbsp;- **Note:** The declared character encoding must match the one the page was saved with to avoid garbled characters and security holes. The `<meta>` element declaring the encoding must be inside the [`<head>`](/en/webfrontend/<head>) element and **within the first 1024 bytes** of the [[HTML]] as some browsers only look at those bytes before choosing an encoding.<br> &nbsp;- This `<meta>` element is only one part of the algorithm to determine a page's character set. The **`Content-Type`** header and any **Byte-Order Marks** override this element.<br><br>**It is strongly recommended to define the character encoding.** If a page's encoding is undefined, cross-scripting techniques are possible, such as the `UTF-7` fallback cross-scripting technique.<br><br>The `<meta>` element with a charset attribute is a synonym for the pre-HTML5 `<meta http-equiv="Content-Type" content="text/html; charset=IANAcharset">`, where `IANAcharset` contains the value of the equivalent `charset` attribute. This syntax is still allowed, although **no longer recommended**.
| **`content`** | This attribute contains the value for the `http-equiv` or `name` attribute, depending on which is used.
| **`http-equiv`** | Defines a **pragma directive**. The attribute is named *"http-equiv(alent)"* because all the allowed values are names of particular **HTTP headers**:<br><br>**`content-language`**<br>**Error:** Do not use this value, as **it is obsolete**. Prefer the `lang` attribute on the [`<html>`](/en/webfrontend/<html>) element.<br>Defines the **default language** of the page. It can be overridden by the `lang` attribute on any element.<br><br>**`content-security-policy`**<br>Allows page authors to define a **content policy** for the current page. Content policies mostly specify allowed server origins and script endpoints which help guard against *cross-site scripting attacks.*<br><br>**`content-type`**<br>**Error:** Do not use this value, as **it is obsolete**. Use the `charset` attribute on the `<meta>` element.<br>Defines the **[[MIME]] type** of the document, followed by its **[[character encoding]]**. It follows the same syntax as the HTTP `Content-Type` entity-header field, but as it is inside a HTML page, most values other than `text/html` are impossible. Therefore the valid syntax for its content is the string `'text/html'` followed by a character set with the following syntax: `; charset=IANAcharset`, where `IANAcharset` is the preferred [[MIME]] name for a character set as defined by the [[IANA]].<br>**Note:** As `<meta>` can't change documents' types in XHTML or HTML5's XHTML serialization, never set the MIME type to an XHTML MIME type with `<meta>`.<br><br>**`refresh`**<br>This instruction specifies:<br>The **number of seconds until the page should be reloaded** - only if the `content` attribute contains a *positive integer*.<br>The number of seconds until the page should redirect to another - only if the `content` attribute contains a positive integer followed by the string '`;url=`', and a valid URL.<br><br>**`set-cookie`**<br>**Error:** Do not use this instruction, as it is obsolete. Use the HTTP header `Set-Cookie` instead. It was removed from the standard.<br>Defines a **cookie** for the page. Its content must follow the syntax defined in the [[IETF]] HTTP Cookie Specification.
| **`name`** | This attribute defines the **name of a piece of document-level metadata**. It should not be set if one of the attributes `itemprop`, `http-equiv` or `charset` is also set.<br>This metadata name is associated with the value contained by the `content` attribute.<br>The possible values for the `name` attribute are:<br><br>**`application-name`** which defines the name of the application running in the web page.<br>**Note:** Browsers may use this to identify the application. It is different from the [`<title>`](/en/webfrontend/<title>) element, which usually contain the application name, but may also contain information like the document name or a status.<br>Simple web pages shouldn't define an application-name.<br><br>**`author`** which defines the name of the document's author.<br><br>**`description`** which contains a short and accurate summary of the content of the page. Several browsers, like Firefox and Opera, use this as the default description of bookmarked pages.<br><br>**`generator`** which contains the identifier of the software that generated the page.<br><br>**`keywords`** which contains words relevant to the page's content separated by commas.<br><br>**`referrer`** which controls the `Referer` HTTP header attached to requests sent from the document.

### Values for the content attribute of `<meta name="referrer">`

|  |  |
| :-- | :-- |
| `no-referrer` | Do not send a HTTP Referrer header. |
| `origin` | Send the origin of the document. |
| `no-referrer-when-downgrade` | Send the origin as a referrer to URLs as secure as the current page, (https→https), but does not send a referrer to less secure URLs (https→http). This is the default behaviour.
| `origin-when-cross-origin` | Send the full URL (stripped of parameters) for same-origin requests, but only send the origin for other cases. |
| `same-origin` | A referrer will be sent for same-site origins, but cross-origin requests will contain no referrer information. |
| `strict-origin` | Only send the origin of the document as the referrer to a-priori as-much-secure destination (HTTPS->HTTPS), but don't send it to a less secure destination (HTTPS->HTTP). |
| `strict-origin-when-cross-origin` | Send a full URL when performing a same-origin request, only send the origin of the document to a-priori as-much-secure destination (HTTPS->HTTPS), and send no header to a less secure destination (HTTPS->HTTP). |
| `unsafe-URL` | Send the full URL (stripped of parameters) for same-origin or cross-origin requests.|

!!! warn "Don't try this at home"
    - Some browsers support the deprecated values of always, default, and never for referrer.
    - Dynamically inserting `<meta name="referrer">` (with `document.write`
    or `appendChild`) makes the referrer behaviour unpredictable.
    - When several conflicting policies are defined, the no-referrer policy is applied.

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

This attribute may also have a value taken from the extended list defined on
WHATWG Wiki MetaExtensions page. Although none have been formally accepted yet,
a few commonly used names are:

- `creator` which defines the name of the creator of the document, such as an organization or
institution. If there are more than one, several `<meta>` elements should be used.
- `googlebot`, a synonym of robots, is only followed by Googlebot (the indexing crawler for Google).
- `publisher` which defines the name of the document's publisher.
- `robots` which defines the behaviour that cooperative crawlers, or "robots",
should use with the page. It is a comma-separated list of the values below:

### Values for the content of `<meta name="robots">`

| Value | Description | Used by |
| :-- | :-- | :-- |
| `index` | Allows the robot to index the page (default). | All |
| `noindex` | Requests the robot to not index the page. | All |
| `follow` | Allows the robot to follow the links on the page (default). | All |
| `nofollow` | Requests the robot to not follow the links on the page. | All |
| `none` | Equivalent to noindex, nofollow | Google |
| `noodp` | Prevents using the Open Directory Project description, if any, as the page description in search engine results.| Google, Yahoo, Bing |
| `noarchive` | Requests the search engine not to cache the page content. | Google, Yahoo, Bing|
| `nosnippet` | Prevents displaying any description of the page in search engine results. | Google, Bing|
| `noimageindex` | Requests this page not to appear as the referring page of an indexed image.| Google|
| `nocache` | Synonym of noarchive. | Bing |

!!! warn "Don't try this at home"
    - Only cooperative robots follow these rules. Do not expect to prevent e-mail harvesters with them.
    - The robot still needs to access the page in order to read these rules. To prevent bandwidth
    consumption, use a robots.txt file.
    - If you want to remove a page, `noindex` will work, but only after the robot visits the page
    again. Ensure that the `robots.txt` file is not preventing revisits.
    - Some values are mutually exclusive, like `index` and `noindex`, or `follow` and `nofollow`.
    In these cases the robot's behaviour is undefined and may vary between them.
    - Some crawler robots, like Google, Yahoo and Bing, support the same values for the HTTP header
    `X-Robots-Tag`; this allows non-HTML documents like images to use these rules.

- slurp, is a synonym of robots, but only for Slurp - the crawler for Yahoo Search.
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

- If `name` is set, it is document-level metadata, applying to the whole page.
- If `http-equiv` is set, it is a pragma directive — information normally given by the web
server about how the web page is served.
- If `charset` is set, it is a charset declaration — the character encoding used by the webpage.
- If `itemprop` is set, it is user-defined metadata — transparent for the user-agent as the
semantics of the metadata is user-specific.

## Examples

```html
<meta charset="utf-8">

<!-- Dookbook is the author of this page -->
<meta name="author" content="Dookbook">

<!-- Describe this page -->
<meta name="description" content="A Dookbook webpage">

<!-- Keywords about this page, separated by commas -->
<meta name="keywords" content="Dookbook,a,b">

<!-- Redirect page after 3 seconds -->
<meta http-equiv="refresh" content="3">
<meta http-equiv="refresh" content="3;url=https://dookbook.info">
```

## Accessibility Concerns

### Refreshing content

Pages set with a refresh value run the risk of having the time interval being too short. People
navigating with the aid of assistive technology such as a screen reader may be unable to read through
and understand the page's content before being automatically redirected. The abrupt, unannounced
updating of the page content may also be disorienting for people experiencing low vision conditions.

- [MDN Understanding WCAG, Guideline 2.1 explanations](https://wiki.developer.mozilla.org/en-US/docs/Web/Accessibility/Understanding_WCAG/Operable#Guideline_2.2_%E2%80%94_Enough_Time_Provide_users_enough_time_to_read_and_use_content)
- [MDN Understanding WCAG, Guideline 3.1 explanations](https://wiki.developer.mozilla.org/en-US/docs/Web/Accessibility/Understanding_WCAG/Understandable#Guideline_3.2_%E2%80%94_Predictable_Make_Web_pages_appear_and_operate_in_predictable_ways)
- [Understanding Success Criterion 2.2.1 | W3C Understanding WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/time-limits-required-behaviors.html)
- [Understanding Success Criterion 2.2.4 | W3C Understanding WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/time-limits-postponed.html)
- [Understanding Success Criterion 3.2.5 | W3C Understanding WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/consistent-behavior-no-extreme-changes-context.html)
  
### Viewport scaling

Disabling zooming capabilities by setting `user-scalable` to a value of no prevents people
experiencing low vision conditions from being able to read and understand page content.

- [MDN Understanding WCAG, Guideline 1.4 explanations](https://wiki.developer.mozilla.org/en-US/docs/Web/Accessibility/Understanding_WCAG/Perceivable#Guideline_1.4_Make_it_easier_for_users_to_see_and_hear_content_including_separating_foreground_from_background)
- [Understanding Success Criterion 1.4.4 | W3C Understanding WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-scale.html)

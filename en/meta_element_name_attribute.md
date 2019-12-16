TOPICS: <meta> name attribute

# `name` Attribute of `<meta>` Element

This attribute defines the **name of a piece of document-level metadata**.
It should not be set if one of the attributes `itemprop`, [`http-equiv`](/en/webfrontend/<meta>_http-equiv_attribute)
or [`charset`](/en/webfrontend/<meta>_charset_attribute) is also set.

This metadata `name` is associated with the value contained by the `content` attribute.

## `<meta name="application-name">`

**`application-name`** defines the **name of the application** running in the web page.

**Note:** Browsers may use this to identify the application. It is different from
the [`<title>`](/en/webfrontend/<title>) element, which usually contain the application name, but
may also contain information like the document *name* or a *status*.

Simple web pages shouldn't define an `application-name`.

## `<meta name="author">`

**`author`** defines the name of the **document's author**.

For example,

```html
<!-- Dookbook is the author of this page -->
<meta name="author" content="Dookbook">
```

## `<meta name="description">`

**`description`** contains **a short and accurate summary of the content** of the page. Several
browsers, like Firefox and Opera, use this as the default description of bookmarked pages.

For example,

```html
<!-- Describe this page -->
<meta name="description" content="A Dookbook webpage">
```

## `<meta name="generator">`

**`generator`** contains the **identifier of the software** that generated the page.

## `<meta name="keywords">`

**`keywords`** contains **words relevant** to the page's content separated by *commas*.

For example,

```html
<!-- Keywords about this page, separated by commas -->
<meta name="keywords" content="Dookbook,a,b">
```

## `<meta name="referrer">`

**`referrer`** controls the **`Referer` HTTP header** attached to requests sent from the document.

### Values for the `content` attribute of `<meta name="referrer">`

!!! warn "Note"
    - Some browsers support the **deprecated** values of `always`, `default`, and `never` for `referrer`.
    - Dynamically inserting `<meta name="referrer">` (with `document.write`
    or `appendChild`) makes the referrer behaviour unpredictable.
    - When several conflicting policies are defined, the `no-referrer` policy is applied.

| Value | Description |
| :-- | :-- |
| `no-referrer` | Do not send a HTTP `Referrer` header. |
| `origin` | Send the origin of the document. |
| `no-referrer-when-downgrade` | Send the `origin` as a `referrer` to URLs as secure as the current page, (https→https), but does not send a `referrer` to less secure URLs (https→http). This is the *default* behaviour.
| `origin-when-cross-origin` | Send the full URL (stripped of parameters) for same-origin requests, but only send the origin for other cases. |
| `same-origin` | A referrer will be sent for same-site origins, but cross-origin requests will contain no referrer information. |
| `strict-origin` | Only send the origin of the document as the referrer to a-priori as-much-secure destination (HTTPS->HTTPS), but don't send it to a less secure destination (HTTPS->HTTP). |
| `strict-origin-when-cross-origin` | Send a full URL when performing a same-origin request, only send the origin of the document to a-priori as-much-secure destination (HTTPS->HTTPS), and send no header to a less secure destination (HTTPS->HTTP). |
| `unsafe-URL` | Send the full URL (stripped of parameters) for same-origin or cross-origin requests.|

## `<meta name="robots">`

This attribute may also have a value taken from the extended list defined on
WHATWG Wiki MetaExtensions page. Although none have been formally accepted yet,
a few commonly used names are:

- `creator` which defines the name of the creator of the document, such as an organization or
institution. If there are more than one, several [`<meta>`](/en/webfrontend/<meta>) elements should
be used.
- `googlebot`, a synonym of robots, is only followed by **Googlebot** (the indexing *crawler* for *Google*).
- `slurp`, is a synonym of robots, but only for **Slurp** - the *crawler* for *Yahoo Search*.
- `publisher` which defines the name of the document's **publisher**.
- `robots` which defines the behaviour that **cooperative crawlers**, or "*robots*",
should use with the page. It is a *comma-separated* list of the values.

### Values for the `content` attribute of `<meta name="robots">`

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

!!! info "Note"
    - Only cooperative robots follow these rules. Do not expect to prevent e-mail harvesters with them.
    - The robot still needs to access the page in order to read these rules. To prevent bandwidth
    consumption, use a `robots.txt` file.
    - If you want to remove a page, `noindex` will work, but only after the robot visits the page
    again. Ensure that the `robots.txt` file is not preventing revisits.
    - Some values are mutually exclusive, like `index` and `noindex`, or `follow` and `nofollow`.
    In these cases the robot's behaviour is undefined and may vary between them.
    - Some crawler robots, like Google, Yahoo and Bing, support the same values for the HTTP header
    `X-Robots-Tag`; this allows non-HTML documents like images to use these rules.

## `<meta name="viewport">`

This attribute gives hints about the **size of the initial size of the viewport**.
**Used by mobile devices only**.

!!! warn "de-facto dominance"
    Though unstandardized, this declaration is respected by most mobile browsers due to de-facto dominance.
    The default values may vary between devices and browsers.

### Values for the `content` attribute of `<meta name="viewport">`

| Value | Possible sub-values | Description |
| :-- | :-- | :-- |
| `width` | A *positive integer number*, or the text `device-width` | Defines the **pixel width** of the viewport that you want the web site to be rendered at.
| `height` | A *positive integer*, or the text `device-height` | Defines the **height** of the viewport. **Not used by any browser.**
| `initial-scale` | A *positive number* between `0.0` and `10.0` | Defines the ratio between the device width (device-width in portrait mode or device-height in landscape mode) and the viewport size.
| `maximum-scale` | A *positive number* between `0.0` and `10.0` | Defines the maximum amount to zoom in. It must be greater or equal to the minimum-scale or the behaviour is undefined. Browser settings can ignore this rule and **iOS10+** ignores it by default.
| `minimum-scale` | A *positive number* between `0.0` and `10.0` | Defines the minimum zoom level. It must be smaller or equal to the maximum-scale or the behaviour is undefined. Browser settings can ignore this rule and **iOS10+** ignores it by default.
| `user-scalable` | `yes` or `no` | If set to no, the user is not able to zoom in the webpage. The default is yes. Browser settings can ignore this rule, and **iOS10+** ignores it by default.
  
### Accessibility Concerns of Viewport Scaling

Disabling zooming capabilities by setting `user-scalable` to a value of `no` prevents people
experiencing low vision conditions from being able to read and understand page content.

- [MDN Understanding WCAG, Guideline 1.4 explanations](https://wiki.developer.mozilla.org/en-US/docs/Web/Accessibility/Understanding_WCAG/Perceivable#Guideline_1.4_Make_it_easier_for_users_to_see_and_hear_content_including_separating_foreground_from_background)
- [Understanding Success Criterion 1.4.4 | W3C Understanding WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-scale.html)

## `<meta name="theme-color">`

`theme-color` indicates a **suggested color** that user agents should use to customize the display
of the page or of the surrounding [user interface]. The `content` attribute contains a valid CSS `color`.

## `<meta name="color-scheme">`

`color-scheme` specifies one or more **color schemes** with which the document is compatible.

The browser will use this information in tandem with the user's browser or device settings to
determine what colors to use for everything from background and foregrounds to form controls and
scrollbars.

The primary use for `<meta name="color-scheme">` is to indicate compatibility with—and
order of preference for — *light* and *dark* color modes.

The value of the `content` property for `color-scheme` may be one of the following:

### `normal`

The document is unaware of color schemes and should simply be rendered using the **default** color palette.

### `light` | `dark`

One or more color schemes supported by the document. Specifying the same color scheme more than once
has the same effect as specifying it only once. Indicating multiple color schemes indicates that the
first scheme is preferred by the document, but that the second specified
scheme is acceptable if the user prefers it.

### `only light`

Indicates that the document only supports *light* mode, with a light background and dark foreground
colors. By specification, `only dark` is not valid, because forcing a document to render in dark mode
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

## `<meta name="scheme">`

!!! error "Warning: it is obsolete"
    Do not use this value, as it is obsolete. There is no
    replacement as there was no real usage for it.

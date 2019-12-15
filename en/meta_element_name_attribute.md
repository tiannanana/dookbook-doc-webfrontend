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

TOPICS: <meta> charset attribute

# `charset` Attribute of `<meta>` Element

This attribute declares the page's **[[character encoding]]**. It must contain a standard [[IANA]]
[[MIME]] name for character encodings. Although the standard doesn't request a specific encoding,
it suggests:

- **Encouraged** to use **`UTF-8`**.
- **Should not** use ASCII-incompatible encodings to avoid security risk: browsers not
  supporting them may interpret harmful content as HTML. This happens with the `JIS_C6226-1983`,
  `JIS_X0212-1990`,`HZ-GB-2312`, `JOHAB`, the `ISO-2022` family and the `EBCDIC` family.
- **Must not** use `CESU-8`, `UTF-7`, `BOCU-1` and/or `SCSU` as *cross-site scripting attacks*
  with these encodings have been demonstrated.
- **Should not** use `UTF-32` because not all HTML5 encoding algorithms can distinguish it
  from `UTF-16`.
- The declared character encoding must match the one the page was saved with to avoid garbled
  characters and security holes. The [`<meta>`](/en/webfrontend/<meta>) element declaring the
  encoding must be inside the [`<head>`](/en/webfrontend/<head>) element and
  **within the first 1024 bytes** of the [[HTML]] as some browsers only look at those bytes
  before choosing an encoding.
- This [`<meta>`](/en/webfrontend/<meta>) element is only one part of the algorithm to determine a
  page's character set. The **`Content-Type`** header and any **Byte-Order Marks** override this element.

**It is strongly recommended to define the character encoding.** If a page's encoding is undefined,
cross-scripting techniques are possible, such as the `UTF-7` fallback cross-scripting technique.

## Examples

```html
<head>
  <meta charset="utf-8">

  <!-- no longer recommended in HTML5. Use charset attribute instead -->
  <meta http-equiv="Content-Type" content="text/html"; charset="IANAcharset">
  <meta http-equiv="Content-Type" content="text/html; charset=utf-8">

  <!-- Other metadata here ... -->
</head>
```

TOPICS: <map>
        <area>
AUTHORS: Masahiro Fujimoto; mfujimot@gmail.com; github:mfuji09
         Sphinx; SphinxKnight@github.com; github:SphinxKnight
         Teoli; teoli@mozilla.net; mdn:teoli
         Michael[tm] Smith; mike@w3.org; github:sideshowbarker
         Sebastian Zartner; SebastianZ@github.com; github:SebastianZ
         Andrew Pfeiffer; Andrew_Pfeiffer@mozilla.net; mdn:Andrew_Pfeiffer
         Jérémie Patonnier; Jeremie@mozilla.net; mdn:Jeremie
         Karen Scarfone; kscarfone@mozilla.net; mdn:kscarfone
         Thierry Régagnon; tregagnon@github.com; github:tregagnon
         Eric Shepherd; eshepherd@mozilla.com; github:a2sheppy
         Keiichi; ethertank@mozilla.net; mdn:ethertank
         Christian Sonne; cers@mozilla.net; mdn:cers
         Jonathan Wilsson; jwilsson@github.com; github:jwilsson

# `<map>`

The **HTML `<map>` element** is used with `<area>` elements to define an image
map (a clickable link area).

|  |  |
| :-- | :-- |
| **Content categories** | Flow content, phrasing content, palpable content. |
| **Permitted content** | Any transparent element. |
| **Tag omission** | None, both the starting and ending tag are mandatory. |
| **Permitted parents** | Any element that accepts phrasing content. |
| **Permitted ARIA roles** | None |
| **DOM interface** | `HTMLMapElement` |

## Attributes

This element includes the [global attributes](https://wiki.developer.mozilla.org/en-US/docs/HTML/Global_attributes).

| Attribute | Description |
| :-- | :-- |
| `name` | The name attribute gives the map a name so that it can be referenced. The attribute must be present and must have a non-empty value with no space characters. The value of the name attribute must not be a compatibility-caseless match for the value of the name attribute of another map element in the same document. If the id attribute is also specified, both attributes must have the same value.

## `<area>`

The **HTML `<area>` element** defines a hot-spot region on an image, and optionally associates it
with a hypertext link. This element is used only within a `<map>` element.

|  |  |
| :-- | :-- |
| **Content categories** | Flow content, phrasing content.|
| **Permitted content** | None, it is an empty element.|
| **Tag omission** | Must have a start tag and must not have an end tag.|
| **Permitted parents** | Any element that accepts phrasing content. The `<area>` element must have an ancestor `<map>`, but it need not be a direct parent. |
| **Permitted ARIA roles** | None |
| **DOM interface** | `HTMLAreaElement` |

| Attribute | Description |
| :-- | :-- |
| `alt` | A text string alternative to display on browsers that do not display images. The text should be phrased so that it presents the user with the same kind of choice as the image would offer when displayed without the alternative text. In HTML4, this attribute is required, but may be the empty string (""). In HTML5, this attribute is required only if the **href** attribute is used.
| `coords` | A set of values specifying the coordinates of the hot-spot region. The number and meaning of the values depend upon the value specified for the **shape** attribute.<br>`rect` or rectangle: the **coords** value is two x,y pairs: left, top, right, bottom.<br>`circle`: the value is `x,y,r` where `x,y` is a pair specifying the center of the circle and r is a value for the radius.<br>`poly` or polygon: the value is a set of x,y pairs for each point in the polygon: `x1,y1,x2,y2,x3,y3,` and so on.<br><br>In HTML4, the values are numbers of pixels or percentages, if a percent sign (%) is appended; in HTML5, the values are numbers of CSS pixels.
| `download` | This attribute, if present, indicates that the author intends the hyperlink to be used for downloading a resource. See `<a>` for a full description of the `download` attribute.
| `href` | The hyperlink target for the area. Its value is a valid URL. In HTML4, either this attribute or the **nohref** attribute must be present in the element. In HTML5, this attribute may be omitted; if so, the area element does not represent a hyperlink.
| `hreflang` | Indicates the language of the linked resource. Allowed values are determined by BCP47. Use this attribute only if the **href** attribute is present.
| `ping` | Contains a space-separated list of URLs to which, when the hyperlink is followed, `POST` requests with the body PING will be sent by the browser (in the background). Typically used for tracking.
| `referrerpolicy` | A string indicating which referrer to use when fetching the resource:<br>`"no-referrer"` meaning that the Referer: header will not be sent.<br>`"no-referrer-when-downgrade"` meaning that no `Referer:` header will be sent when navigating to an origin without TLS (HTTPS). This is a user agent’s default behavior, if no policy is otherwise specified.<br>`"origin"` meaning that the referrer will be the origin of the page, that is roughly the scheme, the host and the port.<br>`"origin-when-cross-origin"` meaning that navigations to other origins will be limited to the scheme, the host and the port, while navigations on the same origin will include the referrer's path.<br>`"unsafe-url"` meaning that the referrer will include the origin and the path (but not the fragment, password, or username). This case is unsafe because it can leak origins and paths from TLS-protected resources to insecure origins.
| `rel` | For anchors containing the **href** attribute, this attribute specifies the relationship of the target object to the link object. The value is a space-separated list of link types values. The values and their semantics will be registered by some authority that might have meaning to the document author. The default relationship, if no other is given, is void. Use this attribute only if the **href** attribute is present.
| `shape` | The shape of the associated hot spot. The specifications for HTML 5 and HTML 4 define the values `rect`, which defines a rectangular region; `circle`, which defines a circular region; `poly`, which defines a polygon; and `default`, which indicates the entire region beyond any defined shapes. Many browsers, notably Internet Explorer 4 and higher, support `circ`, `polygon`, and `rectangle` as valid values for **shape**; these values are .
| `target` | This attribute specifies where to display the linked resource. In HTML4, this is the name of, or a keyword for, a frame. In HTML5, it is a name of, or keyword for, a browsing context (for example, tab, window, or inline frame). The following keywords have special meanings:<br>`_self`: Load the response into the same HTML4 frame (or HTML5 browsing context) as the current one. This value is the default if the attribute is not specified.<br>`_blank`: Load the response into a new unnamed HTML4 window or HTML5 browsing context.<br>`_parent`: Load the response into the HTML4 frameset parent of the current frame or HTML5 parent browsing context of the current one. If there is no parent, this option behaves the same way as `_self`.<br>`_top`: In HTML4: Load the response into the full, original window, canceling all other frames. In HTML5: Load the response into the top-level browsing context (that is, the browsing context that is an ancestor of the current one, and has no parent). If there is no parent, this option behaves the same way as `_self`.<br><br>Use this attribute only if the **href** attribute is present.

## Example

```html
<map name="primary">
  <area shape="circle" coords="75,75,75" href="left.html">
  <area shape="circle" coords="275,75,75" href="right.html">
</map>
<img usemap="#primary" src="https://placehold.it/350x150" alt="350 x 150 pic">
```

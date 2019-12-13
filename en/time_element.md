TOPICS: <time>
AUTHORS: Masahiro Fujimoto; mfujimot@gmail.com; github:mfuji09
         albert; jalbertbowden@gmail.com; github:jalbertbowden
         Sphinx; SphinxKnight@github.com; github:SphinxKnight
         Chris Mills; chrisdavidmills@mozilla.net; mdn:chrisdavidmills
         Crystal Yungwirth; crystal-dawn@github.com; github:crystal-dawn
         Yuhei Yasuda; yuhei.yasuda1003@gmail.com; github:yuheiy
         Anton Ingfors; antoningfors@github.com; github:antoningfors
         Teoli; teoli@mozilla.net; mdn:teoli
         John Jago; hello@johnjago.com; github:johnjago
         Michael[tm] Smith; mike@w3.org; github:sideshowbarker
         Michiel Renty; mrenty@mozilla.net; mdn:mrenty
         Sebastian Zartner; SebastianZ@github.com; github:SebastianZ
         Sami Jaktholm; sjakthol@mozilla.net; mdn:sjakthol
         Eric Shepherd; eshepherd@mozilla.com; github:a2sheppy
         Mahdi Dibaiee; mdibaiee@pm.me; github:mdibaiee
         Karen Scarfone; kscarfone@mozilla.net; mdn:kscarfone
         Keiichi; ethertank@mozilla.net; mdn:ethertank
         紫云飞; ziyunfei@mozilla.net; mdn:ziyunfei
         Makoto Kato; mkato@mozilla.net; mdn:mkato
         Soki Briggs; Briggz5d@mozilla.net; mdn:Briggz5d
         Onur Avsar; avsaro@mozilla.net; mdn:avsaro
         Florian Scholz; fscholz@mozilla.net; mdn:fscholz
         Jonathan Wilsson; jwilsson@github.com; github:jwilsson

# `<time>`

The **HTML `<time>` element** represents a specific period in time. It may include the datetime
attribute to translate dates into machine-readable format, allowing for better search engine results
or custom features such as reminders.

It may represent one of the following:

- A time on a 24-hour clock.
- A precise date in the Gregorian calendar (with optional time and timezone information).
- A valid time duration.

|  |  |
| :-- | :-- |
| **Content categories** | Flow content, phrasing content, palpable content.|
| **Permitted content** | Phrasing content.|
| **Tag omission** | None, both the starting and ending tag are mandatory.|
| **Permitted parents** | Any element that accepts phrasing content.|
| **Permitted ARIA roles** | Any |
| **DOM interface** | `HTMLTimeElement` |

## Attributes

Like all other HTML elements, this element supports the [global attributes](/en/webfrontend/HTML_Global_Attributes).

| Attribute | Description |
| :-- | :-- |
| `datetime` | This attribute indicates the time and/or date of the element and must be in one of the formats described below.

## Usage Notes

This element is for presenting dates and times in a machine readable format. For example, this can
help a user agent offer to add an event to a user's calendar.

This element should not be used for dates prior to the introduction of the Gregorian calendar
(due to complications in calculating those dates).

The datetime value (the machine-readable value of the datetime) is the value of the element’s
`datetime` attribute, which must be in the proper format (see below). If the element does not have
a `datetime` attribute, **it must not have any element descendants**, and the datetime value is the
element’s child text content.

## Valid datetime Values

### a valid year string

`2011`

`0001`

### a valid month string

`2011-11`

### a valid date string

`2011-11-18`

### a valid yearless date string

`11-18`

### a valid week string

`2011-W47`

### a valid time string

`14:54`

`14:54:39`

`14:54:39.929`

### a valid local date and time string

`2011-11-18T14:54:39.929`

`2011-11-18 14:54:39.929`

### a valid global date and time string

`2011-11-18T14:54:39.929Z`

`2011-11-18T14:54:39.929-0400`

`2011-11-18T14:54:39.929-04:00`

`2011-11-18 14:54:39.929Z`

`2011-11-18 14:54:39.929-0400`

`2011-11-18 14:54:39.929-04:00`

### a valid duration string

`PT4H18M3S`

## Examples

### Simple Example

```html
<p>The concert starts at <time datetime="2018-07-07T20:00:00">20:00</time>.</p>
```

### `datetime` Example

```html
<p>The concert took place on <time
  datetime="2001-05-15T19:00">May 15</time>.</p>
```

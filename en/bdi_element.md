TOPICS: <bdi>
AUTHORS: Masahiro Fujimoto; mfujimot@gmail.com; github:mfuji09
         Gergan Zhekov; gerganzh@mozilla.net; mdn:gerganzh
         Eric Shepherd; eshepherd@mozilla.com; github:a2sheppy
         Tim Ellison; timothyellison85@gmail.com; github:timothyjellison
         Florian Scholz; fscholz@mozilla.net; mdn:fscholz
         Yuhei Yasuda; yuhei.yasuda1003@gmail.com; github:yuheiy
         Rory O’Kane; rory@roryokane.com; github:roryokane
         Teoli; teoli@mozilla.net; mdn:teoli
         Michael[tm] Smith; mike@w3.org; github:sideshowbarker
         Sebastian Zartner; SebastianZ@github.com; github:SebastianZ
         Karen Scarfone; kscarfone@mozilla.net; mdn:kscarfone
         Keiichi; ethertank@mozilla.net; mdn:ethertank
         Christian Sonne; cers@mozilla.net; mdn:cers
         Onur Avsar; avsaro@mozilla.net; mdn:avsaro

# `<bdi>`

The **HTML Bidirectional Isolate element (`<bdi>`)**  tells the browser's bidirectional algorithm to
treat the text it contains in isolation from its surrounding text. It's particularly useful when a
website dynamically inserts some text and doesn't know the directionality of the text being inserted.

Bidirectional text is text that may contain both sequences of characters that are arranged
left-to-right (LTR) and sequences of characters that are arranged right-to-left (RTL), such as an
Arabic quotation embedded in an English string. Browsers implement the
[Unicode Bidirectional Algorithm](https://www.w3.org/International/articles/inline-bidi-markup/uba-basics)
to handle this. In this algorithm, characters are given an
implicit directionality: for example, Latin characters are treated as LTR while Arabic characters
are treated as RTL. Some other characters (such as spaces and some punctuation) are treated as
neutral and are assigned directionality based on that of their surrounding characters.

Usually, the bidirectional algorithm will do the right thing without the author having to provide
any special markup but, occasionally, the algorithm needs help.
That's where `<bdi>` comes in.

The `<bdi>` element is used to wrap a span of text and instructs the bidirectional algorithm to
treat this text in isolation from its surroundings. This works in two ways:

- The directionality of text embedded in `<bdi>` does not influence the
directionality of the surrounding text.
- The directionality of text embedded in `<bdi>` is not influenced by the directionality
of the surrounding text.

For example, consider some text like:

```html
EMBEDDED-TEXT - 1st place
```

If `EMBEDDED-TEXT` is LTR, this works fine. But if `EMBEDDED-TEXT` is RTL, then   `- 1` will be
treated as RTL text (because it consists of neutral and weak characters). The result will be garbled:

```html
1 - EMBEDDED-TEXTst place
```

If you know the directionality of `EMBEDDED-TEXT` in advance, you can fix this problem by wrapping
`EMBEDDED-TEXT` in a [`<span>`](/en/webfrontend/<span>) with the dir attribute set to the known directionality.
But if you don't know the directionality - for example, because `EMBEDDED-TEXT` is being read from a
database or entered by the user - you should use `<bdi>` to prevent the
directionality of `EMBEDDED-TEXT` from affecting its surroundings.

Though the same visual effect can be achieved using the CSS rule `unicode-bidi: isolate` on a
[`<span>`](/en/webfrontend/<span>) or another text-formatting element, HTML authors should not
use this approach because it is not semantic and browsers are allowed to ignore CSS styling.

Embedding the characters in `<span dir="auto">` has the same effect as using `<bdi>`,
but its semantics are less clear.

|  |  |
| :-- | :-- |
| **Content categories** | Flow content, phrasing content, palpable content. |
| **Permitted content** | Phrasing content. |
| **Tag omission** | None, both the starting and ending tag are mandatory.
| **Permitted parents** | Any element that accepts phrasing content].
| **Permitted ARIA roles** | Any
| **DOM interface** | `HTMLElement` |

## Attributes

Like all other HTML elements, this element supports the [global attributes](https://wiki.developer.mozilla.org/en-US/docs/HTML/Global_attributes),
except that the
`dir` attribute behaves differently than normal: it defaults to auto, meaning its value is
never inherited from the parent element. This means that unless you specify a value of either
`"rtl"` or `"ltr"` for `dir`, the user agent will determine the correct directionality
to use based on the contents of the `<bdi>`.

## Examples

### No `<bdi>` with only LTR

This example lists the winners of a competition using [`<span>`](/en/webfrontend/<span>) elements only.
When the names only contain LTR text the results look fine:

```html
<ul>
 <li><span class="name">Henrietta Boffin</span> - 1st place</li>
 <li><span class="name">Jerry Cruncher</span> - 2nd place</li>
</ul>
```

### No `<bdi>` with RTL text

This example lists the winners of a competition using [`<span>`](/en/webfrontend/<span>) elements
only, and one of the winners has a name consisting of RTL text. In this case the "- 1", which
consists of characters with neutral or weak directionality, will adopt the directionality of the
RTL text, and the result will be garbled:

```html
<ul>
 <li><span class="name">اَلأَعْشَى</span> - 1st place</li>
 <li><span class="name">Jerry Cruncher</span> - 2nd place</li>
</ul>
```

### Using `<bdi>` with LTR and RTL text

This example lists the winners of a competition using `<bdi>` elements. These elements instruct the
browser to treat the name in isolation from its embedding context,
so the example output is properly ordered:

```html
<ul>
 <li><bdi class="name">اَلأَعْشَى</bdi> - 1st place</li>
 <li><bdi class="name">Jerry Cruncher</bdi> - 2nd place</li>
</ul>
```

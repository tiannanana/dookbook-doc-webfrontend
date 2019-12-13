TOPICS: <pre>
AUTHORS: Masahiro Fujimoto; mfujimot@gmail.com; github:mfuji09
         Sphinx; SphinxKnight@github.com; github:SphinxKnight
         Eric Bailey; ericwbailey@github.com; github:ericwbailey
         Eric Shepherd; eshepherd@mozilla.com; github:a2sheppy
         AJ Jordan; Strugee Strugee@mozilla.net; mdn:Strugee
         Teoli; teoli@mozilla.net; mdn:teoli
         Michael[tm] Smith; mike@w3.org; github:sideshowbarker
         Taylor Hunt; tigt@github.com; github:tigt
         Jim Holby; jamesdholby@gmail.com; github:Jimmerz28
         Sebastian Zartner; SebastianZ@github.com; github:SebastianZ
         Jérémie Patonnier; Jeremie@mozilla.net; mdn:Jeremie
         Karen Scarfone; kscarfone@mozilla.net; mdn:kscarfone
         Keiichi; ethertank@mozilla.net; mdn:ethertank
         Christian Sonne; cers@mozilla.net; mdn:cers
         Jonathan Wilsson; jwilsson@github.com; github:jwilsson

# `<pre>`

The **HTML `<pre>` element** represents preformatted text which is to be presented exactly as
written in the HTML file. The text is typically rendered using a non-proportional ("monospace")
font. Whitespace inside this element is displayed as written.

|  |  |
| :-- | :-- |
| **Content categories** | Flow content, palpable content. |
| **Permitted content** | Phrasing content. |
| **Tag omission** | None, both the starting and ending tag are mandatory. |
| **Permitted parents** | Any element that accepts flow content. |
| **Permitted ARIA roles** | Any |
| **DOM interface** | `HTMLPreElement` |

## Attributes

This element only includes the [global attributes](/en/webfrontend/HTML_Global_Attributes).

| Attribute | Description |
| :-- | :-- |
| `wrap` | Is a hint indicating how the overflow must happen. In modern browser this hint is ignored and no visual effect results in its present; to achieve such an effect, use CSS `white-space` instead. |

## Example

```html
<p>Using CSS to change the font color is easy.</p>
<pre>
body {
  color: red;
}
</pre>
```

## Accessibility Concerns

It is important to provide an alternate description for any images or diagrams created using
preformatted text. The alternate description should clearly and concisely describe
the image or diagram's content.

People experiencing low vision conditions and browsing with the aid of assistive technology such as
a screen reader may not understand what the preformatted text characters are
representing when they are read out in sequence.

A combination of the [`<figure>`](/en/webfrontend/<figure>) and [`<figcaption>`](/en/webfrontend/<figcaption>)
elements, supplemented by a
combination of an `id` and the ARIA `role` and `aria-labelledby` attributes allow the
preformatted text to be announced as an image, with the `figcaption`
serving as the image's alternate description.

```html
<figure role="img" aria-labelledby="cow-caption">
  <pre>
  ___________________________
< I'm an expert in my field. >
  ---------------------------
         \   ^__^
          \  (oo)\_______
             (__)\       )\/\
                 ||----w |
                 ||     ||
  </pre>
  <figcaption id="cow-caption">
    A cow saying, "I'm an expert in my field." The cow is illustrated using preformatted
    text characters.
  </figcaption>
</figure>
```

- [MDN Understanding WCAG, Guideline 1.1 explanations](https://wiki.developer.mozilla.org/en-US/docs/Web/Accessibility/Understanding_WCAG/Perceivable#Guideline_1.1_%E2%80%94_Providing_text_alternatives_for_non-text_content)
- [H86: Providing text alternatives for ASCII art, emoticons, and leetspeak | W3C Techniques for WCAG 2.0](https://www.w3.org/TR/WCAG20-TECHS/H86.html)

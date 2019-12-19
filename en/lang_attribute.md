TOPICS: lang attribute
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# HTML Global Attribute: `lang`

The **`lang`** [global attribute](/en/webfrontend/HTML_Global_Attributes) helps define the language
of an element: the language that non-editable elements are written in, or the language that the
editable elements should be written in by the user. The attribute contains a single “language tag” in
the format defined in [Tags for Identifying Languages (BCP47)](https://www.ietf.org/rfc/bcp/bcp47.txt).

If the attribute value is the empty string (`lang=""`), the language is set to unknown; if the
language tag is not valid according to BCP47, it is set to invalid.

!!! warn "Language tag syntax"
    The full BCP47 syntax is in-depth enough to mark extremely specific language dialects, but most
    usage is much simpler.
    A language tag is made of hyphen-separated language subtags, where each subtag indicates a
    certain property of the language. The 3 most common subtags are:
    **Language subtag**
    Required. A 2-or-3-character code that defines the basic language, typically written in all
    lowercase. For example, the language code for English is `en`, and the code for Badeshi is `bdz`.
    **Script subtag**
    Optional. This subtag defines the writing system used for the language, and is always 4
    characters long, with the first letter capitalized. For example, French-in-Braille is `fr-Brai`
    and `ja-Kana` is Japanese written with the Katakana alphabet. If the language is written in a
    highly typical way, like English in the Latin alphabet, there is no need to use this subtag.
    **Region subtag**
    Optional. This subtag defines a dialect of the base language from a particular location, and is
    either 2 letters in ALLCAPS matching a country code, or 3 numbers matching a non-country area.
    For example, `es-ES` is for Spanish as spoken in Spain, and `es-013` is Spanish as spoken in
    Central America. “International Spanish” would just be `es`.
    The script subtag precedes the region subtag if both are present — `ru-Cyrl-BY` is Russian, written
    in the Cyrillic alphabet, as spoken in Belarus.
    To find the correct subtag codes for a language, try [the Language Subtag Lookup](https://r12a.github.io/app-subtags/)

Even if the **lang** attribute is set, it may not be taken into account, as the __`xml:lang`__
attribute has priority.

For the CSS pseudo-class [`:lang`](/en/webfrontend/:lang), two
invalid language names are different if their names are different. So while `:lang(es)` matches both
`lang="es-ES"` and `lang="es-419"`, `:lang(xyzzy)` would not match `lang="xyzzy-Zorp!"`.

## See also

- All HTML [global attributes](/en/webfrontend/HTML_Global_Attributes).
- [`Content-Language` HTTP Header](/en/webfrontend/Content-Language)

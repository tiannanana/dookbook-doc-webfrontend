TOPICS: autocapitalize attribute
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# HTML Global Attribute: `autocapitalize`

The **`autocapitalize`** [global attribute](/en/webfrontend/HTML_Global_Attributes)
is an enumerated attribute that controls whether and how text input is automatically capitalized as
it is entered/edited by the user. The attribute must take one of the following values:

- `off` or none: No autocapitalization is applied (all letters default to lowercase)
- `on` or sentences: The first letter of each sentence defaults to a capital letter; all other
letters default to lowercase
- `words`: The first letter of each word defaults to a capital letter; all other letters default to lowercase
- `characters`: All letters should default to uppercase

The `autocapitalize` attribute doesn’t affect behavior when typing on a physical keyboard. Instead,
it affects the behavior of other input mechanisms, such as virtual keyboards on mobile devices and
voice input. The behavior of such mechanisms is that they often assist users by automatically
capitalizing the first letter of sentences. The `autocapitalize` attribute enables authors to
override that behavior per-element.

The `autocapitalize` attribute never causes autocapitalization to be enabled for an [`<input>`](/en/webfrontend/<input>)
element with a `type` attribute whose value is `url`, `email`, or `password`.

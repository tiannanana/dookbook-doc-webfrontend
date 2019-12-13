TOPICS: inputmode attribute
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# HTML Global Attribute: `inputmode`

The **`inputmode`** [global attribute](/en/webfrontend/HTML_Global_Attributes) is an enumerated
attribute that hints at the type of data that might be entered by the user while editing the element
or its contents. It can have the following values:

|  |  |
| :--- | :--- |
| **`none`** | No virtual keyboard. For when the page implements its own keyboard input control. |
| **`text` (default value)** | Standard input keyboard for the user's current locale. |
| **`decimal`** | Fractional numeric input keyboard containing the digits and decimal separator for the user's locale (typically !!!.!!! or !!!,!!!). Devices may or may not show a minus key (!!!-!!!). |
| **`numeric`** | Numeric input keyboard, but only requires the digits 0–9. Devices may or may not show a minus key. |
| **`tel`** | A telephone keypad input, including the digits 0–9, the asterisk (!!!*!!!), and the pound (!!!#!!!) key. Inputs that require a telephone number should typically use `<input type="tel">` instead. |
| **`search`** | A virtual keyboard optimized for search input. For instance, the return/submit key may be labeled “Search”, along with possible other optimizations. |
| **`email`** | A virtual keyboard optimized for entering email addresses. Typically includes the !!!@!!! character as well as other optimizations. Inputs that require email addresses should typically use `<input type="email">` instead. |
| **`url`** | A keypad optimized for entering URLs. This may have the !!!/!!! key more prominent, for example. Enhanced features could include history access and so on. Inputs that require a URL should typically use `<input type="url">` instead. |

## See also

- All HTML [global attributes](/en/webfrontend/HTML_Global_Attributes).

TOPICS: <dialog>
AUTHORS: Brendan Quinn; quinn.197@gmail.com; github:Mathdrquinn
         Gan Eng Chin; ecgan@mozilla.net; mdn:ecgan
         Masahiro Fujimoto; mfujimot@gmail.com; github:mfuji09
         Luis Faría; faria.luis.d@gmail.com; github:luisdfp
         Taylor Hunt; tigt@github.com; github:tigt
         Milan Raj; rajsite@mozilla.net; mdn:rajsite
         Eric Shepherd; eshepherd@mozilla.com; github:a2sheppy
         Andrew C. Dvorak; andy@andydvorak.net; github:acdvorak
         ExE Boss; ExE-Boss@github.com; github:ExE-Boss
         Emil; thatemil@mozilla.net; mdn:thatemil
         Teoli; teoli@mozilla.net; mdn:teoli
         Sebastian Zartner; SebastianZ@github.com; github:SebastianZ
         Edwin Cosme Mercado; edwinmdn1@mozilla.net; mdn:edwinmdn1
         Filipus Klutiero; Chealer@mozilla.net; mdn:Chealer
         Michael[tm] Smith; mike@w3.org; github:sideshowbarker
         Oleg Torbasow; torbasow@mozilla.net; mdn:torbasow
         Chris Rebert; cvrebert@mozilla.net; mdn:cvrebert
         Lucien Greathouse; LPGhatguy@mozilla.net; mdn:LPGhatguy
         Saurabh / Jsx; jsx@mozilla.net; mdn:jsx

# `<dialog>`

The **HTML `<dialog>` element** represents a dialog box or other interactive component,
such as an inspector or window.

|  |  |
| :-- | :-- |
| **Content categories** | Flow content, sectioning root |
| **Permitted content** | Flow content |
| **Tag omission** | None, both the starting and ending tag are mandatory. |
| **Permitted parents** | Any element that accepts flow content |
| **Permitted ARIA roles** | `alertdialog` |
| **DOM interface** | `HTMLDialogElement` |

## Attributes

This element includes the [global attributes](https://wiki.developer.mozilla.org/en-US/docs/HTML/Global_attributes).
The tabindex attribute must not be used on the `<dialog>` element.

| Attribute | Description |
| :-- | :-- |
| `open` | Indicates that the dialog is active and available for interaction. When the open attribute is not set,the dialog shouldn't be shown to the user.

## Usage Notes

- `<form>` elements can be integrated within a dialog by specifying them with the attribute
method="dialog". When such a form is submitted, the dialog is closed with its `returnValue`
attribute set to the value of the form's submit button that was used.
- he `::backdrop` CSS pseudo-element can be used to style behind a `<dialog>` element,
for example to dim inaccessible content whilst a modal dialog is active. The backdrop is only drawn
when the dialog element is displayed with `HTMLDialogElement.showModal()`.

## Examples

### Simple example

```html
<dialog open>
  <p>Greetings, one and all!</p>
</dialog>
```

### Advanced example

This example opens a pop-up dialog box containing a form when the "Update details" button is clicked.

```html
<!-- Simple pop-up dialog box containing a form -->
<dialog id="favDialog">
  <form method="dialog">
    <p><label>Favorite animal:
      <select>
        <option></option>
        <option>Brine shrimp</option>
        <option>Red panda</option>
        <option>Spider monkey</option>
      </select>
    </label></p>
    <menu>
      <button value="cancel">Cancel</button>
      <button id="confirmBtn" value="default">Confirm</button>
    </menu>
  </form>
</dialog>

<menu>
  <button id="updateDetails">Update details</button>
</menu>

<output aria-live="polite"></output>
```

```javascript
(function() {
  var updateButton = document.getElementById('updateDetails');
  var favDialog = document.getElementById('favDialog');
  var outputBox = document.getElementsByTagName('output')0];
  var selectEl = document.getElementsByTagName('select')0];
  var confirmBtn = document.getElementById('confirmBtn');

  // “Update details” button opens the <dialog> modally
  updateButton.addEventListener('click', function onOpen() {
    if (typeof favDialog.showModal === "function") {
      favDialog.showModal();
    } else {
      alert("The dialog API is not supported by this browser");
    }
  });
  // "Favorite animal" input sets the value of the submit button
  selectEl.addEventListener('change', function onSelect(e) {
    confirmBtn.value = selectEl.value;
  });
  // "Confirm" button of form triggers "close" on dialog because of method="dialog"]
  favDialog.addEventListener('close', function onClose() {
    outputBox.value = favDialog.returnValue + " button clicked - " + (new Date()).toString();
  });
})();
```

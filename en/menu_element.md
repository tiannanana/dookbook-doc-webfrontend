TOPICS: <menu>
AUTHORS: ExE Boss; ExE-Boss@github.com; github:ExE-Boss
         Masahiro Fujimoto; mfujimot@gmail.com; github:mfuji09
         Grzegorz Zapała; zapala.grzegorz@gmail.com; github:zapalagrzegorz
         Mattia; equinusocio@mozilla.net; mdn:equinusocio
         Eric Shepherd; eshepherd@mozilla.com; github:a2sheppy
         Jakub Fiala; jakubfiala@mozilla.net; mdn:jakubfiala
         Teoli; teoli@mozilla.net; mdn:teoli
         Michael[tm] Smith; mike@w3.org; github:sideshowbarker
         Sebastian Zartner; SebastianZ@github.com; github:SebastianZ
         Влад; ifantom@mozilla.net; mdn:ifantom
         Saurabh / Jsx; jsx@mozilla.net; mdn:jsx
         Anthony; crazytonyi@mozilla.net; mdn:crazytonyi
         João Tomás; Syle91@mozilla.net; mdn:Syle91
         Karen Scarfone; kscarfone@mozilla.net; mdn:kscarfone
         Florian Bender; fbender@mozilla.net; mdn:fbender
         Keiichi; ethertank@mozilla.net; mdn:ethertank
         Christian Sonne; cers@mozilla.net; mdn:cers
         Florian Scholz; fscholz@mozilla.net; mdn:fscholz
         Jonathan Wilsson; jwilsson@github.com; github:jwilsson
         Yann Brelière; Yann Dìnendal@mozilla.net; mdn:Yann Dìnendal

# `<menu>`

!!! warn "Don't try this at home"
    This is an `experimental technology`
    Check the Browser compatibility table carefully before using this in production.

The **HTML `<menu>` element** represents a group of commands that a user can perform or activate.
This includes both list menus, which might appear across the top of a screen, as well as context menus,
such as those that might appear underneath a button after it has been clicked.

|  |  |
| :-- | :-- |
| **Content categories** | Flow content. Additionally, if in the list menu state, palpable content. (list menu is the default state, unless the parent element is a `<menu>` in the context menu state.) |
| **Permitted content** | If the element is in the list menu state: flow content, or alternatively, zero or more occurrences of [`<li>`](/en/webfrontend/<li>), [`<script>`](/en/webfrontend/<script>), and [`<template>`](/en/webfrontend/<template>).<br>If the element is in the context menu state: zero or more occurrences, in any order, of `<menu>` (context menu state only), `<menuitem>`, [`<hr>`](/en/webfrontend/<hr>), [`<script>`](/en/webfrontend/<script>), and [`<template>`](/en/webfrontend/<template>). |
| **Tag omission**| None, both the starting and ending tag are mandatory. |
| **Permitted parents** | Any element that accepts flow content. |
| **Permitted ARIA roles** | None |
| **DOM interface** | `HTMLMenuElement` |

## Attributes

This element includes the [global attributes](/en/webfrontend/HTML_Global_Attributes).

| Attribute | Description |
| :-- | :-- |
| `label` | The name of the menu as shown to the user. Used within nested menus, to provide a label through which the submenu can be accessed. Must only be specified when the parent element is a `<menu>` in the context menu state.
| `type` | This attribute indicates the kind of menu being declared, and can be one of two values.<br>`context`: Indicates the popup menu state, which represents a group of commands activated through another element. This might be as a button menu referenced by a menu attribute of a `<button>` element, or as context menu for an element with a `contextmenu` attribute. This value is the default if the attribute is missing and the parent element is also a `<menu>` element.<br>`toolbar`: Indicates the toolbar state, which represents a toolbar consisting of a series of commands for user interaction. This might be in the form of an unordered list of [`<li>`](/en/webfrontend/<li>) elements, or, if the element has no [`<li>`](/en/webfrontend/<li>) element children, flow content describing available commands. This value is the default if the attribute is missing.

## Usage Notes

The `<menu>` and [`<ul>`](/en/webfrontend/<ul>) elements both represent an unordered list of items.
The key difference is that [`<ul>`](/en/webfrontend/<ul>) primarily contains items for display,
whilst `<menu>` is intended for interactive items, to act on.

An HTML menu can be used to create context menus (typically activated by
right-clicking another element) or toolbars.

Context menus consist of a `<menu>` element which contains `<menuitem>` elements for each
selectable option in the menu, `<menu>` elements for submenus within the menu, and [`<hr>`](/en/webfrontend/<hr>)
elements for separator lines to break up the menu's content into sections. Context menus are then
attached to the element they're activated from using either the associated element's contextmenu
attribute or, for button-activated menus attached to [`<button>`](/en/webfrontend/<button>) elements,
the menu attribute.

Toolbar menus consist of a `<menu>` element whose content is described in one of two ways:
either as an unordered list of items represented by [`<li>`](/en/webfrontend/<li>) elements
(each representing a command or option the user can utilize), or (if there are no
[`<li>`](/en/webfrontend/<li>) elements), flow content describing the available commands and options.

This element was deprecated in HTML4, but reintroduced in HTML5.1 and the HTML living standard.
This document describes the current Firefox implementation.
Type 'list' is likely to change to 'toolbar' according to HTML5.1.

## Examples

### Context menu

!!! error ""
    This feature is no longer recommended. Though some browsers might still support it, it may have
    already been removed from the relevant web standards, may be in the process of being dropped,
    or may only be kept for compatibility purposes. Avoid using it, and update existing code if
    possible; see the compatibility table at the bottom of this page to guide your decision. Be
    aware that this feature may cease to work at any time.

### Deprecated

This feature is no longer recommended. Though some browsers might still support it, it may have
already been removed from the relevant web standards, may be in the process of being dropped,
or may only be kept for compatibility purposes. Avoid using it, and update existing code if possible;
see the compatibility table at the bottom of this page to guide your decision.
Be aware that this feature may cease to work at any time.

```html
<!-- A <div> element with a context menu -->
<div contextmenu="popup-menu">
  Right-click to see the adjusted context menu
</div>

<menu type="context" id="popup-menu">
  <menuitem>Action</menuitem>
  <menuitem>Another action</menuitem>
  <hr/>
  <menuitem>Separated action</menuitem>
</menu>
```

```css
div {
  width: 300px;
  height: 80px;
  background-color: lightgreen;
}
```

### Menu button

!!! error ""
    Menu buttons haven't been implemented in any known browsers yet. The `type` attribute on
    the `<menu>` element is now obsolete.

!!! error ""
    `<menuitem>` element is obsolete.

```html
<!-- A button, which displays a menu when clicked. -->
<button type="menu" menu="popup-menu">
  Dropdown
</button>

<menu type="context" id="popup-menu">
  <menuitem>Action</menuitem>
  <menuitem>Another action</menuitem>
  <hr/>
  <menuitem>Separated action</menuitem>
</menu>
```

### Toolbar

!!! error ""
    Toolbar menus haven't been implemented in any known browsers yet.

```html
<!-- A context menu for a simple editor,
   - containing two menu buttons. -->
<menu type="toolbar">
  <li>
    <button type="menu" menu="file-menu">File</button>
    <menu type="context" id="file-menu">
      <menuitem label="New..." onclick="newFile()">
      <menuitem label="Save..." onclick="saveFile()">
    </menu>
  </li>
  <li>
    <button type="menu" menu="edit-menu">Edit</button>
    <menu type="context" id="edit-menu">
      <menuitem label="Cut..." onclick="cutEdit()">
      <menuitem label="Copy..." onclick="copyEdit()">
      <menuitem label="Paste..." onclick="pasteEdit()">
    </menu>
  </li>
</menu>
```

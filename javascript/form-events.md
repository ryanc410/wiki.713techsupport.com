---
title: Javascript Form Events
description: 
published: true
date: 2026-07-29T21:45:00.996Z
tags: javascript, events, form, forms
editor: markdown
dateCreated: 2026-07-29T21:45:00.996Z
---

### 🔹 **JavaScript Form Events Reference**

| **Event**    | **Description**                                                                                 | **Typical Use**                                     |
| ------------ | ----------------------------------------------------------------------------------------------- | --------------------------------------------------- |
| **submit**   | Fired when a form is submitted.                                                                 | Validate form, prevent reload, send data via AJAX.  |
| **reset**    | Fired when a form is reset.                                                                     | Reset custom UI when form fields are cleared.       |
| **change**   | Fired when value of `<input>`, `<select>`, or `<textarea>` changes **and loses focus**.         | Detect selection change, validate on blur.          |
| **input**    | Fired immediately as the user types or edits a field.                                           | Live validation, character count, instant feedback. |
| **focus**    | Fired when an input gains focus.                                                                | Highlight input, show help tooltip.                 |
| **blur**     | Fired when an input loses focus.                                                                | Validate on blur, hide tooltip.                     |
| **invalid**  | Fired when a field fails built-in HTML5 validation (e.g. `required`).                           | Custom error handling, styling invalid fields.      |
| **select**   | Fired when text inside `<input>` or `<textarea>` is selected.                                   | Show formatting tools, track text selection.        |
| **keyup**    | Fired when a key is released.                                                                   | Detect typing, shortcuts, validation.               |
| **keydown**  | Fired when a key is pressed down.                                                               | Detect Enter key (e.g. submit on Enter).            |
| **keypress** | Fired when a key that produces a character is pressed. *(Deprecated, prefer `keydown`/`keyup`)* | Legacy key input handling.                          |
| **paste**    | Fired when text is pasted into an input.                                                        | Sanitize pasted content, enforce formats.           |
| **cut**      | Fired when text is cut from an input.                                                           | Track edits, prevent cutting in secure fields.      |
| **copy**     | Fired when text is copied from an input.                                                        | Analytics, prevent copy in secure fields.           |

---

### 🔹 **Example Usage**

```html
<form id="myForm">
  <input type="text" id="username" placeholder="Enter username" required>
  <input type="password" id="password" placeholder="Enter password" required>
  <button type="submit">Submit</button>
  <button type="reset">Reset</button>
</form>

<script>
const form = document.getElementById("myForm");
const user = document.getElementById("username");

form.addEventListener("submit", e => {
  e.preventDefault();
  console.log("Form submitted!");
});

form.addEventListener("reset", () => console.log("Form reset!"));

user.addEventListener("input", () => console.log("Typing:", user.value));
user.addEventListener("focus", () => console.log("Username focused"));
user.addEventListener("blur", () => console.log("Username blurred"));
user.addEventListener("invalid", () => console.log("Username invalid"));
</script>
```

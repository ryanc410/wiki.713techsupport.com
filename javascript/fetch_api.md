---
title: Sending Formdata using Fetch API
description: 
published: true
date: 2026-07-29T21:46:20.415Z
tags: javascript, form, forms, fetch api, fetch, formdata, user input
editor: markdown
dateCreated: 2026-07-29T21:46:20.415Z
---

### **1. Sending Form Data with Fetch (FormData object)**

If you already have a `<form>` element in HTML:

```html
<form id="myForm">
  <input type="text" name="username" placeholder="Enter username">
  <input type="email" name="email" placeholder="Enter email">
  <button type="submit">Submit</button>
</form>
```

You can submit it with JavaScript:

```javascript
document.getElementById('myForm').addEventListener('submit', async function (e) {
  e.preventDefault(); // prevent default form submission

  const form = e.target;
  const formData = new FormData(form);

  try {
    const response = await fetch('process.php', {
      method: 'POST',
      body: formData // directly send FormData (includes files if present)
    });

    const data = await response.json(); // expecting JSON response from server
    console.log('Server response:', data);
  } catch (error) {
    console.error('Fetch error:', error);
  }
});
```

* `FormData` automatically encodes values as `multipart/form-data`.
* You **don’t need** to set `Content-Type` headers manually; the browser handles it.

---

### **2. Sending JSON instead of FormData**

If your backend expects **JSON** rather than form-encoded data:

```javascript
document.getElementById('myForm').addEventListener('submit', async function (e) {
  e.preventDefault();

  const form = e.target;
  const formData = new FormData(form);

  // Convert FormData to JSON
  const jsonData = Object.fromEntries(formData.entries());

  try {
    const response = await fetch('process.php', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json'
      },
      body: JSON.stringify(jsonData)
    });

    const data = await response.json();
    console.log('Server response:', data);
  } catch (error) {
    console.error('Error:', error);
  }
});
```

---

### **3. Handling File Uploads**

If your form includes a `<input type="file" name="avatar">`, `FormData` will handle it automatically:

```javascript
const formData = new FormData();
formData.append("username", "Ryan");
formData.append("avatar", fileInput.files[0]);

await fetch('upload.php', {
  method: 'POST',
  body: formData
});
```

---

⚡ Quick rule of thumb:

* Use **FormData** → if you’re uploading files or using traditional form submission.
* Use **JSON.stringify()** → if you want a clean JSON API-style request.
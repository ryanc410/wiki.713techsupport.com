---
title: Vanilla Javascript DOM Cheatsheet
description: 
published: true
date: 2026-07-29T21:44:01.110Z
tags: javascript, cheatsheet
editor: markdown
dateCreated: 2026-07-29T21:44:01.110Z
---

## 📝 JavaScript DOM Manipulation Cheat Sheet

### 🔍 Selecting Elements

```js
document.getElementById("id");              // By ID
document.getElementsByClassName("class");   // By class (HTMLCollection)
document.getElementsByTagName("tag");       // By tag
document.querySelector("cssSelector");      // First match
document.querySelectorAll("cssSelector");   // All matches (NodeList)
```

---

### ✏️ Changing Content

```js
element.textContent = "Hello World";   // Text only
element.innerHTML = "<b>Hello</b>";    // Can insert HTML
element.innerText = "Visible Text";    // Text shown to users
```

---

### ⚙️ Attributes

```js
element.setAttribute("src", "image.png");
element.getAttribute("src");
element.removeAttribute("alt");
```

---

### 🎨 Styles & Classes

```js
element.style.color = "blue";
element.style.fontSize = "18px";

element.classList.add("active");
element.classList.remove("active");
element.classList.toggle("hidden");
```

---

### ➕ Adding Elements

```js
let newDiv = document.createElement("div");
newDiv.textContent = "I’m new here!";
document.body.appendChild(newDiv);

parent.insertBefore(newDiv, referenceElement); // Insert at specific place
```

---

### ➖ Removing Elements

```js
parent.removeChild(child);
element.remove();   // Directly remove
```

---

### 🎛 Events

```js
element.addEventListener("click", () => {
  alert("Clicked!");
});

element.addEventListener("mouseover", () => {
  element.style.background = "yellow";
});
```

---

### 🔄 Traversing the DOM

```js
element.parentElement;
element.children;
element.firstElementChild;
element.lastElementChild;
element.nextElementSibling;
element.previousElementSibling;
```

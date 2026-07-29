---
title: Manipulating the DOM
description: Different jquery methods that can be used to manipulate the DOM and it's elements.
published: true
date: 2026-07-29T18:50:46.324Z
tags: jquery, dom, html, javascript, manipulate, methods
editor: markdown
dateCreated: 2026-07-29T18:50:46.324Z
---

# DOM Manipulation using Jquery

## Adding Elements to the DOM

### 1. `append()`
Adds content to the end of the selected elements.

```javascript
// Add a new paragraph to the end of a div with the id 'myDiv'
$('#myDiv').append('<p>This is a new paragraph.</p>');
```

### 2. `prepend()`
Adds content to the beginning of the selected elements.
```javascript
// Add a new paragraph to the beginning of a div with the id 'myDiv'
$('#myDiv').prepend('<p>This is a new paragraph.</p>');
```

### 3. `before()`
Inserts content before the selected eleements.
```javascript
// Add a new paragraph before a div with the id 'myDiv'
$('#myDiv').before('<p>This is a new paragraph.</p>');
```

### 4. `after()`
Inserts content after the selected element(s).
```javascript
// Add a new paragraph after a div with the id 'myDiv'
$('#myDiv').after('<p>This is a new paragraph.</p>');
```

### 5. `html()`
Replaces the inner HTML of the selected element(s).
```javascript
// Replace the entire content of a div with the id 'myDiv'
$('#myDiv').html('<p>This is a new paragraph.</p>');
```

### 6. `text()`
Replaces the text content of the selected element(s).
```javascript
// Replace the text content of a div with the id 'myDiv'
$('#myDiv').text('This is some new text.');
```

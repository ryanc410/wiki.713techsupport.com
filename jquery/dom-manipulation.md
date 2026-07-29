---
title: Jquery Front-End Snippets
description: Different jquery methods that can be used to manipulate the DOM and it's elements.
published: true
date: 2026-07-29T21:36:03.753Z
tags: jquery, dom, html, javascript, manipulate, methods
editor: markdown
dateCreated: 2026-07-29T18:50:46.324Z
---

# Jquery Front-End Snippet Collection

## Adding Elements

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
## Selecting Elements

### 1. **Select by ID**
```javascript
// Select elements by ID
var element = $('#elementId');
```

### 2. **Select By Class**
```javascript
// Select elements by class
var elements = $('.elementClass');
```

### 3. **Select by Tag Name**

```javascript
// Select elements by tag name
var elements = $('div');
```

## Changing Elements

### 1. **Changing HTML**

```javascript
// Get HTML content
var content = $('#elementId').html();

// Set HTML content
$('#elementId').html('<p>New content</p>');
```

### 2. **Change Text**

```javascript
// Get text content
var text = $('#elementId').text();

// Set text content
$('#elementId').text('New text content');
```

### 3. **Get/Set an Element Attribute**

```javascript
// Get attribute value
var src = $('#imageId').attr('src');

// Set attribute value
$('#imageId').attr('src', 'newImage.jpg');
```

### 4. **Adding and Removing CSS Classes**

```javascript
// Add class
$('#elementId').addClass('newClass');

// Remove class
$('#elementId').removeClass('oldClass');

// Toggle class
$('#elementId').toggleClass('active');
```

## Events

### 1. **Click**

```javascript
$('#buttonId').click(function() {
    alert('Button clicked!');
});
```

### 2. **Mouse Enter**

```javascript
// Mouse enter
$('#elementId').mouseenter(function() {
    console.log('Mouse entered!');
});
```

### 3. **Mouse Leave**

```javascript
// Mouse leave
$('#elementId').mouseleave(function() {
    console.log('Mouse left!');
});
```

## Form Events

### 1. **Submit**

```javascript
// Form submit
$('#formId').submit(function(event) {
    event.preventDefault(); // Prevent form from submitting
    console.log('Form submitted!');
});
```

## Keyboard Events

### 1. **Keydown**

```javascript
// Keydown
$('#inputId').keydown(function(event) {
    console.log('Key pressed: ' + event.key);
});
```

## Effects and Animations

### 1. **Show and Hide Elements**

```javascript
// Show element
$('#elementId').show();

// Hide element
$('#elementId').hide();
```

### 2. **Fade In/Out**

```javascript
// Fade in
$('#elementId').fadeIn();

// Fade out
$('#elementId').fadeOut();
```

### 3. **Slide Up/Down**

```javascript
// Slide down
$('#elementId').slideDown();

// Slide up
$('#elementId').slideUp();
```

## AJAX Requests

### 1. **GET Request**

```javascript
$.get('url', function(data) {
    console.log(data);
});
```

### 2. **POST Request**

```javascript
$.post('url', { key: 'value' }, function(data) {
    console.log(data);
});
```

### 3. **AJAX with Settings**

```javascript
$.ajax({
    url: 'url',
    type: 'POST',
    data: { key: 'value' },
    success: function(response) {
        console.log(response);
    },
    error: function(error) {
        console.error(error);
    }
});
```

## Miscellaneous

### 1. **Document Ready**

```javascript
$(document).ready(function() {
    console.log('Document is ready!');
});
```

### 2. **Chaining**

```javascript
$('#elementId')
    .css('color', 'red')
    .fadeIn()
    .text('Chained method!');
```
---
title: Toggle Button to Show/Hide
description: Example of how to use Jquery to implement a toggle button that can show and hide elements when clicked.
published: true
date: 2026-07-29T18:56:29.113Z
tags: jquery, dom, html, manipulate, toggle, button, show, hide
editor: markdown
dateCreated: 2026-07-29T18:56:29.113Z
---

# Jquery Toggle Button

A simple example of having toggle buttons show or hide specific elements when clicked.

**HTML**
- Multiple buttons are created, each with a data-target attribute pointing to the id of the element it will show.
- Three div elements with the class toggleElement represent the elements that will be shown or hidden.

```html
<button class="toggleButton" data-target="#element1">Show Element 1</button>
<button class="toggleButton" data-target="#element2">Show Element 2</button>
<button class="toggleButton" data-target="#element3">Show Element 3</button>

<div id="element1" class="toggleElement">
    This is Element 1.
</div>
<div id="element2" class="toggleElement" style="display:none;">
    This is Element 2.
</div>
<div id="element3" class="toggleElement" style="display:none;">
    This is Element 3.
</div>
```

**Jquery**
- When any button with the class toggleButton is clicked, all elements with the class toggleElement are hidden using .hide().
- The target element (determined by the data-target attribute of the clicked button) is then shown using .show().

```javascript
$(document).ready(function() {
    $(".toggleButton").click(function() {
        // Hide all elements with the class 'toggleElement'
        $(".toggleElement").hide();
        
        // Show the target element based on the button clicked
        var target = $(this).data("target");
        $(target).show();
    });
});
```

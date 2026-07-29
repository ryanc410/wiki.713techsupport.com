---
title: Custom Card Styles
description: A few examples of custom styling for the Bootstrap Card Element
published: true
date: 2026-07-29T21:38:32.751Z
tags: bootstrap, bs5, css, custom, styling, card
editor: markdown
dateCreated: 2026-07-29T21:38:32.751Z
---

# CUSTOM CARD STYLING FOR BOOTSTRAP

```css
div.card {
  border: none;
  border-radius: 1.5rem;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
  overflow: hidden;
}

div.card:hover {
  transform: translateY(-5px);
  box-shadow: 0 12px 24px rgba(0, 0, 0, 0.15);
}

div.card img {
  border-top-left-radius: 1.5rem;
  border-top-right-radius: 1.5rem;
  object-fit: cover;
  height: 200px;
}

div.card .card-body {
  background: linear-gradient(135deg, #f9f9f9, #ffffff);
  padding: 1.5rem;
}

div.card .card-title {
  color: #0d6efd;
  font-weight: 700;
  font-size: 1.25rem;
}

div.card .btn {
  border-radius: 50px;
  padding: 0.5rem 1.5rem;
  transition: 0.3s ease;
}

div.card .btn:hover {
  background-color: #0a58ca;
  color: #fff;
}
```

## GLASSMORPHISM STYLE
```css
div.card {
  background: rgba(255, 255, 255, 0.2);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.3);
}
```

## DARK CARD
```css
div.card.dark {
  background-color: #1e1e1e;
  color: #f5f5f5;
  border: 1px solid #333;
}
```
## GRADIENT BORDER
```css
div.card.gradient-border {
  border: 2px solid transparent;
  background-image: linear-gradient(#fff, #fff), 
                    linear-gradient(to right, #0d6efd, #6610f2);
  background-origin: border-box;
  background-clip: content-box, border-box;
}
```

# CUSTOM FORM STYLE IDEAS

```css
.custom-form {
  background: #fff;
  border-radius: 1rem;
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.08);
  max-width: 500px;
  margin: 40px auto;
}

.custom-form h4 {
  font-weight: 700;
  color: #0d6efd;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.custom-form .form-label {
  font-weight: 600;
  color: #333;
}

.custom-form .form-control {
  border-radius: 0.5rem;
  border: 1px solid #ddd;
  padding: 0.75rem 1rem;
  transition: all 0.3s ease;
  box-shadow: none;
}

.custom-form .form-control:focus {
  border-color: #0d6efd;
  box-shadow: 0 0 0 0.25rem rgba(13, 110, 253, 0.1);
}

.custom-form textarea.form-control {
  resize: none;
}

.custom-form .btn {
  background: linear-gradient(135deg, #0d6efd, #6610f2);
  border: none;
  color: white;
  padding: 0.75rem;
  border-radius: 0.5rem;
  font-weight: 600;
  transition: all 0.3s ease;
}

.custom-form .btn:hover {
  background: linear-gradient(135deg, #0b5ed7, #520dc2);
  transform: translateY(-2px);
}

.custom-form .form-text {
  font-size: 0.875rem;
  color: #6c757d;
}
```

## FLOATING LABELS
```html
<div class="form-floating mb-3">
  <input type="email" class="form-control" id="floatingEmail" placeholder="name@example.com">
  <label for="floatingEmail">Email address</label>
</div>
```

## INPUT ICONS
```html
<div class="input-group mb-3">
  <span class="input-group-text bg-primary text-white"><i class="bi bi-person"></i></span>
  <input type="text" class="form-control" placeholder="Username">
</div>
```

## Subtle Background Gradient
```css
.custom-form {
  background: linear-gradient(145deg, #f9fafb, #ffffff);
}
```


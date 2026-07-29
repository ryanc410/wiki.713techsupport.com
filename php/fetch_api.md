---
title: Using Fetch API
description: 
published: true
date: 2026-07-29T21:47:13.424Z
tags: 
editor: markdown
dateCreated: 2026-07-29T21:47:13.424Z
---

# Fetch API Usage

1. Handling `FormData` (`multipart/form-data`)
2. Handling JSON (`application/json`)

---

## **1. PHP Backend for FormData (multipart/form-data)**

If you send data using `FormData`, the browser automatically sends it as `multipart/form-data`.

Example Fetch:

```javascript
const formData = new FormData();
formData.append("username", "Ryan");
formData.append("email", "test@example.com");

fetch("process.php", {
  method: "POST",
  body: formData
});
```

PHP (`process.php`):

```php
<?php
header('Content-Type: application/json');

// Access POST data normally
$username = $_POST['username'] ?? null;
$email = $_POST['email'] ?? null;

// If there are files
if (!empty($_FILES['avatar'])) {
    $fileName = $_FILES['avatar']['name'];
    $tmpPath  = $_FILES['avatar']['tmp_name'];
    // You can move the uploaded file
    move_uploaded_file($tmpPath, "uploads/" . basename($fileName));
}

echo json_encode([
    "status" => "success",
    "username" => $username,
    "email" => $email
]);
```

✔ `$_POST` and `$_FILES` work as usual with `FormData`.

---

## **2. PHP Backend for JSON (application/json)**

If you send JSON with Fetch:

```javascript
const jsonData = {
  username: "Ryan",
  email: "test@example.com"
};

fetch("process.php", {
  method: "POST",
  headers: {
    "Content-Type": "application/json"
  },
  body: JSON.stringify(jsonData)
});
```

PHP (`process.php`):

```php
<?php
header('Content-Type: application/json');

// Read raw JSON input
$rawData = file_get_contents("php://input");
$data = json_decode($rawData, true);

$username = $data['username'] ?? null;
$email = $data['email'] ?? null;

echo json_encode([
    "status" => "success",
    "username" => $username,
    "email" => $email
]);
```

✔ Here, `$_POST` will **not** work. You must use `php://input` and `json_decode`.

---

## ✅ Quick Summary

* **FormData →** PHP uses `$_POST` and `$_FILES`.
* **JSON →** PHP uses `file_get_contents("php://input")` + `json_decode`.

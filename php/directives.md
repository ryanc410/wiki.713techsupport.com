---
title: PHP Config Directive Breakdown
description: Describes important directives within the php.ini file and how to secure it.
published: true
date: 2026-07-29T21:40:32.020Z
tags: 
editor: markdown
dateCreated: 2026-07-29T21:40:32.019Z
---

## 🧠 **General PHP Behavior**

| Directive                 | Recommended | Purpose                                                            |
| ------------------------- | ----------- | ------------------------------------------------------------------ |
| `engine = On`             | ✅           | Enables PHP engine. Should always be On.                           |
| `short_open_tag = Off`    | ❌           | Prevents ambiguous tag parsing; use `<?php` instead.               |
| `asp_tags = Off`          | ❌           | Deprecated and insecure alternative tag style.                     |
| `expose_php = Off`        | ❌           | Hides PHP version in HTTP headers.                                 |
| `zend.assertions = -1`    | ⚙️          | Disables assertions (saves performance and hides sensitive logic). |
| `max_execution_time = 30` | 🕐          | Prevents scripts from running indefinitely.                        |
| `max_input_time = 30`     | 🕐          | Limits input parsing time.                                         |
| `memory_limit = 128M`     | 💾          | Controls memory usage per script (adjust as needed).               |
| `output_buffering = 4096` | ⚡           | Improves performance by buffering output.                          |
| `implicit_flush = Off`    | ⚙️          | Prevents auto flushing output after each block.                    |

---

## 🧱 **File System & Paths**

| Directive                        | Recommended | Purpose                                            |
| -------------------------------- | ----------- | -------------------------------------------------- |
| `open_basedir = /var/www/:/tmp/` | 🔒          | Restricts PHP file access to allowed directories.  |
| `doc_root = /var/www/html`       | 📂          | Sets web root directory.                           |
| `user_dir =`                     | (empty)     | Disable per-user directories for simplicity.       |
| `include_path = "."`             | 🛠️         | Avoid including arbitrary directories.             |
| `enable_dl = Off`                | ❌           | Prevents dynamic loading of extensions at runtime. |

---

## ⚙️ **Error Handling**

| Directive                                             | Recommended | Purpose                                               |
| ----------------------------------------------------- | ----------- | ----------------------------------------------------- |
| `display_errors = Off`                                | ❌           | Never show errors to users (prevents info leaks).     |
| `display_startup_errors = Off`                        | ❌           | Same reason as above.                                 |
| `log_errors = On`                                     | ✅           | Logs all errors instead of showing them.              |
| `error_log = /var/log/php_errors.log`                 | 📄          | Central error log location.                           |
| `ignore_repeated_errors = On`                         | ⚙️          | Prevents log flooding.                                |
| `track_errors = Off`                                  | ❌           | Avoids exposing previous errors to scripts.           |
| `html_errors = Off`                                   | ❌           | Prevents HTML formatting in logs.                     |
| `error_reporting = E_ALL & ~E_DEPRECATED & ~E_STRICT` | 🧾          | Full error reporting but suppress deprecated notices. |

---

## 🌐 **Security Hardening**

| Directive                                                                                                                  | Recommended | Purpose                                                    |
| -------------------------------------------------------------------------------------------------------------------------- | ----------- | ---------------------------------------------------------- |
| `allow_url_fopen = Off`                                                                                                    | 🔒          | Prevents remote file inclusion (RFI) attacks.              |
| `allow_url_include = Off`                                                                                                  | 🔒          | Prevents `include()` from fetching remote files.           |
| `file_uploads = On`                                                                                                        | ✅           | Allow uploads if required; secure with restrictions below. |
| `upload_max_filesize = 10M`                                                                                                | ⚖️          | Limit upload size.                                         |
| `max_file_uploads = 5`                                                                                                     | ⚖️          | Limit simultaneous uploads.                                |
| `post_max_size = 12M`                                                                                                      | ⚖️          | Slightly larger than upload size.                          |
| `session.use_strict_mode = 1`                                                                                              | 🔐          | Prevents session fixation attacks.                         |
| `session.cookie_httponly = 1`                                                                                              | 🍪          | Restricts session cookie to HTTP only.                     |
| `session.cookie_secure = 1`                                                                                                | 🔒          | Sends cookies only over HTTPS.                             |
| `session.use_only_cookies = 1`                                                                                             | ✅           | Disables URL-based session IDs.                            |
| `session.cookie_samesite = Strict`                                                                                         | 🧭          | Protects session cookies from CSRF.                        |
| `session.gc_maxlifetime = 1440`                                                                                            | ⏱️          | Session expiration (24 min default).                       |
| `session.gc_divisor = 1000` / `session.gc_probability = 1`                                                                 | ⚙️          | Controls garbage collection probability.                   |
| `disable_functions = exec,passthru,shell_exec,system,proc_open,popen,curl_exec,curl_multi_exec,parse_ini_file,show_source` | 🚫          | Disables potentially dangerous functions.                  |
| `disable_classes =`                                                                                                        | Optional    | Disable specific classes if needed.                        |

---

## 📨 **Mail Configuration**

| Directive                                  | Recommended    | Purpose                                   |
| ------------------------------------------ | -------------- | ----------------------------------------- |
| `mail.add_x_header = Off`                  | ❌              | Hides PHP script path from email headers. |
| `sendmail_path = /usr/sbin/sendmail -t -i` | ⚙️             | Default for Linux.                        |
| `SMTP` / `smtp_port`                       | (Windows only) | Configure if using Windows server.        |

---

## 🧮 **Input & Data Handling**

| Directive                  | Recommended | Purpose                                          |
| -------------------------- | ----------- | ------------------------------------------------ |
| `max_input_vars = 1000`    | ⚖️          | Limits number of POST variables.                 |
| `variables_order = "GPCS"` | ⚙️          | Controls which superglobals are populated.       |
| `request_order = "GP"`     | ⚙️          | Restricts request order (avoid `E`/`C` sources). |
| `auto_globals_jit = On`    | ✅           | Optimizes superglobal creation.                  |

---

## 📊 **Session and Cache**

| Directive                                     | Recommended | Purpose                                           |
| --------------------------------------------- | ----------- | ------------------------------------------------- |
| `session.save_handler = files`                | ✅           | Default file-based sessions.                      |
| `session.save_path = "/var/lib/php/sessions"` | 📁          | Directory for session files.                      |
| `opcache.enable = 1`                          | ⚡           | Enables opcode caching.                           |
| `opcache.memory_consumption = 128`            | ⚙️          | Shared memory for opcache.                        |
| `opcache.interned_strings_buffer = 8`         | ⚙️          | Optimizes string handling.                        |
| `opcache.max_accelerated_files = 4000`        | ⚙️          | Number of cached files.                           |
| `opcache.validate_timestamps = 0`             | 🚀          | Disable timestamp checks (restart on deployment). |
| `realpath_cache_size = 4096K`                 | ⚡           | Speeds up path resolution.                        |

---

## 🕒 **Localization**

| Directive                       | Recommended | Purpose                  |
| ------------------------------- | ----------- | ------------------------ |
| `date.timezone = "UTC"`         | 🌍          | Always set timezone.     |
| `intl.default_locale = "en_US"` | 🗺️         | Default locale for Intl. |
| `default_charset = "UTF-8"`     | ✅           | Ensures UTF-8 encoding.  |

---

## ⚡ **Performance Optimization**

| Directive                      | Recommended | Purpose                                        |
| ------------------------------ | ----------- | ---------------------------------------------- |
| `output_buffering = 4096`      | ⚙️          | Small output buffer improves throughput.       |
| `zlib.output_compression = On` | 💨          | Enables gzip compression.                      |
| `opcache.revalidate_freq = 0`  | ⚙️          | No revalidation (deployment restarts PHP-FPM). |
| `fastcgi.logging = 0`          | 🚀          | Reduces redundant FastCGI logs.                |
| `expose_php = Off`             | 🧱          | Security measure (repeated for emphasis).      |

---

### ✅ **Bonus Tips**

* Always **use HTTPS** and set `session.cookie_secure=1`.
* Set proper **file permissions** (`www-data` should own web files, 644/755).
* Disable `phpinfo()` on public environments.
* Periodically review logs in `/var/log/php_errors.log`.
* Consider a **read-only filesystem** for `/etc/php` after setup.
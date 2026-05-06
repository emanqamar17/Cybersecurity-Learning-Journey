# Day 6 — HTTP Headers & Request Manipulation

## 🎯 Objective
Understand how HTTP headers influence request/response behavior and how to inspect and modify them.

---

## 🔹 1. Header Inspection (DevTools)

### Request Headers Observed
- Method: GET
- User-Agent: Mozilla/5.0 (later modified using Burp Suite)
- Cookie: Not present initially (only appeared after server set it)
- Referer: Not specifically observed

### Response Headers Observed
- Server: Not clearly visible
- Content-Type: text/html
- Set-Cookie: wordpress_test_cookie=WP Cookie check; path=/; secure; HttpOnly
- X-Frame-Options: Present (used for clickjacking protection)
- X-Content-Type-Options: nosniff
- X-Powered-By: PHP 8.2.30
- X-Hcdn: Present (indicates CDN/infrastructure layer)

### Key Learning
- Headers carry metadata that controls server behavior and reveals backend technology.

---

## 🔹 2. Cookie Behavior

### Observation
- `Set-Cookie` observed in response when accessing login-related pages
- Cookie value: wordpress_test_cookie=WP Cookie check
- Cookie was not present in initial request headers
- Browser stored the cookie and sent it in subsequent requests

### Attributes Meaning
- path=/ → cookie valid across entire website
- secure → sent only over HTTPS
- HttpOnly → not accessible via JavaScript

### Key Learning
- `Set-Cookie` is used by server to create cookies
- `Cookie` is sent by browser in future requests
- Cookie attributes are enforced by browser and not sent back to server

---

## 🔹 3. Endpoint Comparison (Headers + Behavior)

### /wp-admin
- Behavior: redirected to /wp-login.php
- Status: 302 → 200 (after redirect)
- Notable headers: Set-Cookie observed during login redirection

### /test123
- Behavior: 404 Not Found (custom themed page)
- Status: 404
- Notable headers: Layout still rendered (header/footer visible)

### Key Difference
- Valid endpoints trigger authentication/redirect behavior
- Invalid endpoints return 404 but still use site template

---

## 🔹 4. Burp Suite — Interception & Modification

### Setup
- Used Burp Suite Community Edition
- Proxy → Intercept ON
- Used built-in Burp browser

### Test 1 — Modify User-Agent
- Modified to: hacker
- Result: No visible change in response

### Test 2 — Remove Header
- Removed: Referer
- Result: No noticeable change

### Test 3 — Add Header
- Added: X-Forwarded-For: 127.0.0.1
- Result: No visible change

### Test 4 — Modify Cookie
- Modified: wordpress_test_cookie=modified
- Result: No noticeable effect on application behavior

### Key Learning
- Requests can be intercepted and modified before reaching server
- Not all header modifications affect server response
- Some headers are ignored or validated securely

---

## 🔹 5. Security & Infrastructure Signals

- Observed request to Google reCAPTCHA (external service)
- Status: 200 OK
- Indicates bot protection on login functionality

- Header observed:
  X-Powered-By: PHP 8.2.30

### Security Impact
- Reveals backend technology and version (information disclosure)

- X-Frame-Options:
  Protects against clickjacking attacks

- X-Hcdn:
  Indicates use of CDN or hosting infrastructure

### Key Learning
- Headers reveal both security mechanisms and backend stack
- External services (like reCAPTCHA) affect application behavior

---

## 🔹 Overall Learning

- HTTP headers control how requests and responses are handled
- Cookies are managed through response headers and enforced by browser
- Burp Suite allows interception and modification of requests
- Real-world applications include protections like CAPTCHA and input validation
- Information disclosure through headers can aid reconnaissance

---

## ✅ Status
✔ Completed Day 6

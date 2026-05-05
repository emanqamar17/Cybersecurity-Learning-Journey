# Day 5 — HTTP Status Codes & Error-Based Recon

## 🎯 Objective
Understand how web servers respond to different requests and how status codes and errors reveal backend behavior.

---

## 🔹 1. HTTP Status Codes Understanding

### Studied
- 200 → Success
- 301/302 → Redirection
- 403 → Forbidden
- 404 → Not Found
- 500 → Server Error

### Key Learning
- Status codes indicate how the server processes requests
- Visual UI does not always reflect actual server response

---

## 🔹 2. Endpoint Testing (Manual Recon)

### Tested URLs
- /admin → redirected to login page
- /wp-admin → redirected to /wp-login.php
- /test123 → returned 404

### Observations
- /admin and /wp-admin are valid endpoints
- /test123 is not a valid endpoint

---

## 🔹 3. Technology Identification

- Redirected to WordPress login page
- Identified CMS: WordPress

### Key Learning
- URL structure can reveal backend technologies

---

## 🔹 4. Error-Based Recon

### Observation
- /test123 returned 404 but still displayed:
  - Header
  - Footer
  - Site layout

### Explanation
- Website uses custom error pages (template-based rendering)

### Key Learning
- Backend response (404) ≠ Frontend appearance

---

## 🔹 5. Login Testing & SQL Injection Attempt

### Payload Tested
admin'--

### Result
- No login bypass
- No visible error message

### Analysis
- Input likely sanitized
- Errors suppressed
- Application not vulnerable to basic SQL injection

---

## 🔹 6. Security Mechanisms Observed

### Detected
- Google reCAPTCHA on login page

### Network Observation
- Request to google.com/recaptcha
- Status: 200 OK
- Method: GET

### Key Learning
- Website uses bot protection
- Some requests are triggered by JavaScript automatically

---

## 🔹 7. JavaScript & Initiator Understanding

### Observation
- Request initiated by content.js / script.js

### Meaning
- Requests triggered by JavaScript, not user actions

### Key Learning
- Applications make background requests
- DevTools "Initiator" shows source of request

---

## 🔹 Overall Learning

- Status codes reveal backend logic
- Endpoints behave differently based on validity
- Errors can expose useful information
- Real-world apps are more secure than labs
- Security mechanisms like CAPTCHA affect testing

---

## ✅ Status
✔ Completed Day 5 successfully

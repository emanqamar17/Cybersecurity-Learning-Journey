# Day 10 — Cross-Site Scripting (XSS) Fundamentals

## 🎯 Objective
Understand how Cross-Site Scripting (XSS) works and practice detecting reflected, stored, and DOM-based XSS vulnerabilities.

---

## 🔹 What is XSS?
Cross-Site Scripting (XSS) is a vulnerability that occurs when untrusted input is inserted into a web page without proper escaping or sanitization, allowing attacker-controlled JavaScript to execute in the victim's browser.

---

## 🔹 Types of XSS

### 1. Reflected XSS
The payload is included in the immediate HTTP response.

### 2. Stored XSS
The payload is saved in the application's database and later served to other users.

### 3. DOM-Based XSS
Client-side JavaScript reads attacker-controlled data and inserts it into the page using unsafe methods such as `innerHTML`.

---

## 🔹 Common Payloads

### Basic Script Tag
<script>alert(1)</script>

### Image Error Event
<img src=x onerror=alert(1)>

### SVG Load Event
<svg onload=alert(1)>

### Attribute Injection
" onmouseover="alert(1)

### JavaScript String Breakout
";alert(1);//

---

## 🔹 Important Concepts

### Source
Where untrusted input originates.
Examples:
- URL parameters
- Search input
- Form fields

### Sink
Where data is inserted into the DOM.
Examples:
- innerHTML
- document.write
- eval()

### Payload
The malicious input used to test code execution.

---

## 🔹 Local DOM XSS Demonstration

Created a file named `xss-demo.html` containing an input field and a script that inserted user input into the page using:

document.getElementById("output").innerHTML = this.value;

Tested:
- Hello Hacker
- <b>Hello</b>
- <img src=x onerror=alert(1)>

Observed that JavaScript executed when unsafe HTML was inserted.

---

## 🔹 Burp Suite Practice

- Opened Burp Suite Community Edition
- Used Burp Browser
- Intercepted requests
- Modified search parameters
- Replaced normal input with XSS payloads
- Forwarded requests
- Observed script execution

---

## 🔹 PortSwigger Labs Completed

1. Reflected XSS into HTML context with nothing encoded
2. Stored XSS into HTML context with nothing encoded
3. DOM XSS in document.write sink using source location.search
4. DOM XSS in innerHTML sink using source location.search

---

## 🔹 Real-World Impact of XSS

XSS can be used to:
- Execute arbitrary JavaScript in a victim's browser
- Perform actions as the logged-in user
- Display phishing forms
- Modify page content
- Redirect users to malicious sites

---

## 🔹 Safe vs Unsafe Output

### Safe Output
The application encodes:
&lt;script&gt;alert(1)&lt;/script&gt;

Displayed as text only.

### Unsafe Output
The application returns:
<script>alert(1)</script>

Executed by the browser.

---

## 🔹 Prevention Techniques

- Output encoding
- Context-aware escaping
- Input sanitization
- Safe DOM APIs such as `textContent`
- Content Security Policy (CSP)
- HttpOnly cookies

---

## 🔹 Overall Learning
Today I learned how XSS works in different contexts and how browsers execute injected JavaScript. I practiced reflected, stored, and DOM-based XSS using PortSwigger labs, Burp Suite, and a custom local HTML file.


---

## ✅ Status
✔ Completed Day 10

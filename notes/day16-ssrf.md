# Day 16 — Server-Side Request Forgery (SSRF)

## Objective

Understand how attackers can abuse server functionality to make requests on behalf of the server and access internal resources.

---

## Concepts Learned

- Server-Side Request Forgery (SSRF)
- Internal Network Access
- Localhost Access
- Loopback Address
- Cloud Metadata Services
- SSRF Detection
- SSRF Payloads
- Blacklist Bypass Techniques
- Open Redirect SSRF Bypass

---

## What is SSRF?

SSRF occurs when an application fetches a user-supplied URL without proper validation.

An attacker can force the server to make requests to:

- Internal systems
- Localhost services
- Cloud metadata endpoints
- Administrative interfaces

---

## Normal Request Flow

```text
User
 ↓
Website
 ↓
Internet
```

---

## SSRF Request Flow

```text
Attacker
 ↓
Vulnerable Website
 ↓
Internal Resources
```

The attacker abuses the server's trust and network access.

---

## Important Targets

### Localhost

```text
127.0.0.1
localhost
```

Meaning:

```text
The server itself
```

---

### Internal Network

Examples:

```text
192.168.x.x
10.x.x.x
172.16.x.x
```

---

### Cloud Metadata

Common cloud metadata endpoint:

```text
169.254.169.254
```

Potential exposure:

- Instance information
- Temporary credentials
- Access keys

---

## Common SSRF Parameters

Look for:

```text
url=
link=
feed=
image=
callback=
returnUrl=
website=
api=
```

---

## Practical Testing

Created:

```text
ssrf-payloads.txt
```

Added:

```text
http://127.0.0.1
http://localhost
http://127.0.0.1/admin
http://192.168.1.1
http://169.254.169.254
```

---

## Burp Suite Analysis

### Original Request

```http
POST /fetch

url=https://example.com
```

### Modified Request

```http
POST /fetch

url=http://127.0.0.1
```

---

### Testing Process

- Intercepted requests
- Sent requests to Repeater
- Modified URL parameters
- Tested localhost access
- Tested internal addresses
- Observed server responses

---

## PortSwigger Labs

### Completed

✔ Basic SSRF against local server

### Completed

✔ Basic SSRF against another back-end system

### Completed

✔ SSRF with blacklist-based input filter

### Completed

✔ SSRF with filter bypass via open redirection

---

## Key Learning

SSRF allows attackers to:

- Access internal systems
- Bypass firewalls
- Access localhost services
- Interact with cloud infrastructure
- Reach hidden administrative interfaces

Applications should:

- Use allowlists
- Restrict outbound requests
- Block internal IP ranges
- Validate URLs correctly

---

## Common Payloads

### Localhost

```text
http://127.0.0.1
http://localhost
```

### Internal Systems

```text
http://192.168.1.1
http://10.0.0.1
```

### Cloud Metadata

```text
http://169.254.169.254
```

---

## Files Created

```text
ssrf-payloads.txt
day16-ssrf.md
```
---

## Tools Used

- Burp Suite Community Edition
- PortSwigger Web Security Academy
- Google Chrome
- GitHub

---

## Interview Questions

### What is SSRF?

A vulnerability that allows attackers to force a server to make unintended requests.

### Why is SSRF dangerous?

Because servers can access internal resources unavailable to external attackers.

### What is localhost?

The local machine itself, commonly represented by 127.0.0.1.

### What is the AWS metadata IP?

169.254.169.254

### How can SSRF be prevented?

- URL validation
- Allowlisted domains
- Blocking internal IPs
- Restricting outbound requests

---

## Status

✔ Completed Day 16

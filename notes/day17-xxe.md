# Day 17 — XML External Entity (XXE)

## Objective

Understand how XML parsers process external entities and how attackers can exploit XML functionality to access sensitive files, internal systems, and backend resources.

---

## Concepts Learned

- XML (Extensible Markup Language)
- XML Structure
- XML Entities
- External Entities
- XML Parser
- XML External Entity (XXE)
- File Disclosure via XXE
- SSRF via XXE
- Blind XXE
- XXE Prevention Techniques

---

## What is XML?

XML (Extensible Markup Language) is a structured data format commonly used for:

- APIs
- Web Services
- Enterprise Applications
- Data Exchange
- SOAP Services

Example:

```xml
<?xml version="1.0"?>

<user>
    <name>Kamer</name>
    <role>Student</role>
</user>
```

---

## What is an Entity?

An entity acts like a variable inside XML.

Example:

```xml
<!DOCTYPE test [
<!ENTITY company "OpenAI">
]>

<user>
    <name>&company;</name>
</user>
```

Output:

```xml
<name>OpenAI</name>
```

---

## What is an External Entity?

An external entity references external resources such as files or URLs.

Example:

```xml
<!ENTITY xxe SYSTEM "file:///etc/passwd">
```

This instructs the XML parser to read a local file.

---

## What is XXE?

XML External Entity (XXE) is a vulnerability that occurs when an application processes user-controlled XML input and allows external entities.

An attacker can force the server to:

- Read local files
- Access internal services
- Perform SSRF attacks
- Interact with backend systems

---

## Why is XXE Dangerous?

Potential impacts include:

### Sensitive File Disclosure

Examples:

```text
/etc/passwd
/etc/hosts
```

---

### Internal Network Access

Access to:

```text
localhost
127.0.0.1
internal services
```

---

### SSRF

The vulnerable server can make requests to internal systems on behalf of the attacker.

---

### Cloud Metadata Access

Potential targets:

```text
169.254.169.254
```

This may expose cloud configuration and credentials.

---

## Typical XXE Payload

```xml
<?xml version="1.0"?>

<!DOCTYPE test [
<!ENTITY xxe SYSTEM "file:///etc/passwd">
]>

<stockCheck>
    <productId>&xxe;</productId>
</stockCheck>
```

---

## Practical Testing

Created:

```text
xxe-payloads.txt
```

Added payloads for:

- File disclosure
- Localhost access
- Internal services
- Cloud metadata testing

---

## Burp Suite Analysis

### Intercepted XML Request

Observed:

```http
Content-Type: application/xml
```

---

### Testing Process

1. Intercepted XML requests.
2. Sent requests to Repeater.
3. Inserted external entity declarations.
4. Modified XML body.
5. Sent requests and analyzed responses.
6. Observed file disclosure and backend interactions.

---

## PortSwigger Labs Completed

### Lab 1

✔ Exploiting XXE using external entities to retrieve files

### Key Learning

The server processed user-controlled XML and returned contents of a local file.

---

### Lab 2

✔ Exploiting XXE to perform SSRF attacks

### Key Learning

The vulnerable XML parser was used to interact with internal systems.

---

### Additional Concepts Studied

- Blind XXE
- Out-of-Band XXE
- Error-Based XXE

---

## Common XXE Indicators

Look for:

```http
Content-Type: application/xml
```

or

```http
Content-Type: text/xml
```

Potential XML input fields:

- Stock Check
- Product Import
- File Upload
- SOAP Requests
- API Endpoints

---

## Common Payloads

### File Disclosure

```xml
<!DOCTYPE test [
<!ENTITY xxe SYSTEM "file:///etc/passwd">
]>
```

---

### Internal Service Access

```xml
<!DOCTYPE test [
<!ENTITY xxe SYSTEM "http://127.0.0.1">
]>
```

---

### Cloud Metadata

```xml
<!DOCTYPE test [
<!ENTITY xxe SYSTEM "http://169.254.169.254">
]>
```

---

## Prevention

Applications should:

- Disable external entity processing.
- Use secure XML parsers.
- Disable DTD processing.
- Validate XML input.
- Restrict outbound network access.

---

## Key Learning

XXE is not simply an XML issue.

It demonstrates how insecure parser configurations can expose:

- Sensitive files
- Internal systems
- Backend services
- Cloud infrastructure

Understanding XML processing is critical for identifying and exploiting XXE vulnerabilities.

---

## Personal Reflection

### What did I learn today?

I learned how XML parsers process entities and how external entities can be abused to read local files or access internal systems.

### What challenged me?

Understanding XML syntax and how entities are resolved by the server.

### What will I improve?

I want to become more comfortable identifying XML-based attack surfaces and crafting XXE payloads manually.

---

## Tools Used

- Burp Suite Community Edition
- PortSwigger Web Security Academy
- Google Chrome
- GitHub

---

## Interview Questions

### What is XXE?

A vulnerability that occurs when an application processes XML input containing external entities.

### Why is XXE dangerous?

It can lead to file disclosure, SSRF, internal network access, and cloud metadata exposure.

### What file is commonly used to demonstrate XXE?

```text
/etc/passwd
```

### What HTTP header may indicate XML processing?

```http
Content-Type: application/xml
```

### How can XXE be prevented?

Disable external entities and DTD processing in XML parsers.

---

## Files Created

```text
xxe-payloads.txt
day17-xxe.md
```

---

## Status

✔ Completed Day 17

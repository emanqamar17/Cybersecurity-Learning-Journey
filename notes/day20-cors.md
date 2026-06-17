# Day 20 — Cross-Origin Resource Sharing (CORS)

## Objective

Understand Same-Origin Policy (SOP), Cross-Origin Resource Sharing (CORS), common CORS misconfigurations, attacker abuse scenarios, and how modern web applications securely share resources across different origins.

---

# Concepts Learned

## Same-Origin Policy (SOP)

Same-Origin Policy (SOP) is a browser security mechanism that prevents one website from reading sensitive data belonging to another website.

An origin consists of:

* Protocol
* Domain
* Port

Example:

Origin 1:

https://shop.com

Origin 2:

https://api.shop.com

These are different origins because the domain is different.

By default, SOP blocks cross-origin reads.

---

## Why SOP Exists

Without SOP:

* Any website could read banking information.
* Any website could access emails.
* Any website could steal social media data.

SOP creates isolation between websites.

Think of SOP as a security guard that blocks websites from reading each other's data.

---

## Cross-Origin Resource Sharing (CORS)

Modern applications often use:

Frontend:

https://app.company.com

Backend API:

https://api.company.com

These are different origins.

Because SOP would block communication, browsers support CORS.

CORS allows servers to specify which origins are trusted.

If the server explicitly trusts an origin, the browser allows the response to be accessed.

---

## Origin Header

When a browser sends a cross-origin request, it includes:

Origin: https://app.company.com

This tells the server where the request originated.

The server uses this information to decide whether the origin should be trusted.

---

## Access-Control-Allow-Origin

The server responds with:

Access-Control-Allow-Origin: https://app.company.com

This tells the browser:

"I trust this origin."

The browser then allows the response to be read.

---

## Wildcard Origins

Example:

Access-Control-Allow-Origin: *

Meaning:

"Every origin is trusted."

This is dangerous when sensitive information is exposed.

---

## Origin Reflection

A vulnerable application may reflect any supplied Origin value.

Request:

Origin: https://evil.com

Response:

Access-Control-Allow-Origin: https://evil.com

This allows attacker-controlled websites to access responses.

---

## Null Origin

Some applications trust:

Origin: null

Attackers can abuse this trust relationship to bypass restrictions.

---

# Deep Theory

The relationship between SOP and CORS is one of the most misunderstood concepts in web security.

SOP says:

"Block cross-origin reads."

CORS says:

"Allow specific exceptions."

The browser enforces SOP first.

Only if the server explicitly trusts an origin through CORS headers will the browser allow access.

Therefore:

SOP = Default Security

CORS = Controlled Exception

Security depends on making correct trust decisions.

---

# Practical Testing

Activities Performed:

* Studied Same-Origin Policy
* Learned CORS workflow
* Identified trust relationships
* Modified Origin headers
* Analyzed server responses
* Observed Access-Control-Allow-Origin behavior
* Practiced identifying vulnerable CORS configurations

---

# Burp Suite Analysis

## Headers Investigated

### Origin

Used to identify where the request originated.

Example:

Origin: https://shop.com

---

### Access-Control-Allow-Origin

Specifies trusted origins.

Example:

Access-Control-Allow-Origin: https://shop.com

---

### Access-Control-Allow-Credentials

Determines whether credentials such as cookies may be included.

---

## Testing Methodology

1. Intercept request.
2. Send request to Repeater.
3. Modify Origin header.
4. Forward request.
5. Observe response headers.
6. Determine whether arbitrary origins are trusted.

---

# PortSwigger Labs

## Lab 1

### CORS vulnerability with basic origin reflection

#### Objective

Exploit an application that reflects attacker-controlled origins.

#### Learning Outcome

Learned how improper origin validation can allow unauthorized data access.

---

## Lab 2

### CORS vulnerability with trusted null origin

#### Objective

Exploit trust placed in null origins.

#### Learning Outcome

Learned how insufficient validation of Origin headers creates security risks.

---

## Lab 3

### CORS vulnerability through excessive trust

#### Objective

Identify overly permissive CORS configurations.

#### Learning Outcome

Learned that broad trust relationships increase attack surface and risk.

---

# Attack Reasoning

An attacker asks:

Can I make the application trust my website?

If the answer is yes:

* Sensitive API responses may be exposed.
* User information may be leaked.
* Authentication data may become accessible.

The attack is not about bypassing the browser.

The attack is about abusing trust decisions made by the server.

---

# Security Mindset

## Why Does This Vulnerability Exist?

Developers trust origins they should not trust.

---

## What Trust Assumption Failed?

The application assumes incoming origins are legitimate.

Attackers can create any origin they want.

---

## What Is The Business Impact?

Potential consequences include:

* Sensitive data disclosure
* Customer information exposure
* Privacy violations
* Regulatory compliance issues

---

## How Should Developers Prevent It?

* Use strict allowlists
* Avoid wildcard trust
* Validate origins carefully
* Limit unnecessary cross-origin access

---

# Pentester View

Questions to Ask:

* Can I control the Origin header?
* Does the application reflect my origin?
* Are credentials allowed?
* Can I read sensitive responses?

---

# Application Security View

Questions to Ask:

* Why is this origin trusted?
* Is the trust relationship necessary?
* What data becomes exposed if trust fails?
* How can the trust boundary be reduced?

---

# Common Mistakes

## Mistake 1

Thinking CORS protects servers.

Reality:

CORS protects browser users.

---

## Mistake 2

Confusing SOP and CORS.

SOP blocks.

CORS allows exceptions.

---

## Mistake 3

Ignoring Origin headers during testing.

---

## Mistake 4

Assuming wildcard origins are always safe.

---

# Real Attack Model

## Scenario

A banking application exposes account information through an API.

Response:

{
"account":"12345",
"balance":"50000"
}

An attacker hosts:

https://evil.com

If the banking API trusts attacker-controlled origins, JavaScript on evil.com may access sensitive responses belonging to authenticated users.

### Result

* Information disclosure
* Privacy violations
* Potential account compromise

---

# Key Learning

* SOP blocks cross-origin access by default.
* CORS allows controlled exceptions.
* Most CORS vulnerabilities originate from broken trust decisions.
* Security depends on determining which origins should be trusted.
* The most important question is:

"Who is allowed to read this data?"

---

# Tools Used

* Burp Suite Community Edition
* PortSwigger Web Security Academy
* Browser Developer Tools

---

# Screenshots

(Add screenshots)

* Burp request with modified Origin header
* Burp response showing Access-Control-Allow-Origin
* Completed PortSwigger lab screenshots

---

# Status

✔ Completed Day 20

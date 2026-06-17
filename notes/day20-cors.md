Day 20 — Cross-Origin Resource Sharing (CORS)
Objective

Understand the relationship between Same-Origin Policy (SOP) and Cross-Origin Resource Sharing (CORS), identify common CORS misconfigurations, and learn how attackers abuse overly trusted origins to access sensitive information.

Concepts Learned
Same-Origin Policy (SOP)

A browser security mechanism that prevents one origin from reading data belonging to another origin.

Origin consists of:

Protocol
Domain
Port

Example:

https://shop.com

and

https://api.shop.com

are different origins.

Cross-Origin Resource Sharing (CORS)

A browser-controlled mechanism that allows a server to specify which external origins are permitted to read its responses.

CORS acts as an exception to SOP.

Origin Header

Browsers include an Origin header when making cross-origin requests.

Example:

Origin: https://shop.com

The server evaluates this value and decides whether the origin should be trusted.

Access-Control-Allow-Origin

Response header used by the server to specify trusted origins.

Example:

Access-Control-Allow-Origin: https://shop.com
Wildcard Origin

Example:

Access-Control-Allow-Origin: *

This means all origins are trusted.

Can become dangerous when sensitive information is exposed.

Origin Reflection

A vulnerable configuration where the server reflects any supplied Origin value.

Example:

Request:

Origin: https://evil.com

Response:

Access-Control-Allow-Origin: https://evil.com

This may allow attacker-controlled websites to read sensitive responses.

Deep Theory

SOP exists because websites should not be able to freely access data belonging to other websites.

Without SOP:

Banking information could be stolen
Private messages could be exposed
User accounts could be abused

Modern applications often separate frontend and backend components into different origins.

Because these applications still need communication, CORS was introduced.

CORS allows servers to tell browsers:

This origin is trusted.

The browser then decides whether the response should be accessible.

Practical Testing

Performed CORS testing using Burp Suite Community Edition.

Steps:

Intercept request.
Send request to Repeater.
Add custom Origin header.
Observe response headers.
Identify Access-Control-Allow-Origin.
Determine whether arbitrary origins are trusted.
Burp Suite Analysis

Headers Investigated:

Origin
Access-Control-Allow-Origin
Access-Control-Allow-Credentials

Observed how the server handles modified Origin values and whether trust decisions are properly enforced.

PortSwigger Labs
Lab 1

CORS vulnerability with basic origin reflection

Key Learning:

Server trusted attacker-controlled origins.

Lab 2

CORS vulnerability with trusted null origin

Key Learning:

Null origins can sometimes bypass insufficient validation.

Lab 3

CORS vulnerability involving excessive trust

Key Learning:

Overly permissive trust models increase risk of data disclosure.

Security Mindset Analysis
Why Does This Vulnerability Exist?

Developers incorrectly trust user-controlled origins.

What Trust Assumption Failed?

The assumption that incoming origins are always legitimate.

Business Impact

Potential consequences:

Sensitive data disclosure
Account information leakage
Exposure of private API responses
Prevention
Use strict origin allowlists
Avoid wildcard trust for sensitive applications
Validate origins carefully
Minimize unnecessary cross-origin access
Pentester Perspective

Questions to ask:

Can I modify the Origin header?
Does the server trust arbitrary origins?
Can sensitive responses be accessed?
Are credentials allowed?
Application Security Perspective

Questions to ask:

Why is this origin trusted?
Is the trust relationship necessary?
Are there safer alternatives?
Does this configuration expose business risk?
Common Mistakes
Mistake 1

Thinking CORS protects servers.

CORS primarily protects browser users.

Mistake 2

Ignoring the Origin header.

Mistake 3

Confusing SOP with CORS.

SOP blocks by default.

CORS allows specific exceptions.

Real Attack Model

Scenario:

A banking API exposes account details.

The attacker hosts:

https://evil.com

If the API trusts attacker-controlled origins, malicious JavaScript may read sensitive responses belonging to authenticated users.

Result:

Information disclosure
Privacy violations
Potential account compromise
Tools Used
Burp Suite Community Edition
PortSwigger Web Security Academy
Web Browser Developer Tools
Screenshots

Add:

Burp request showing Origin header
Burp response showing Access-Control-Allow-Origin
Successful PortSwigger lab completion screens
Personal Reflection

Today I learned how browsers enforce trust boundaries through Same-Origin Policy and how CORS provides controlled exceptions to these restrictions. I also learned that many CORS vulnerabilities originate from incorrect trust decisions rather than complex technical flaws.

Status

✔ Completed Day 20

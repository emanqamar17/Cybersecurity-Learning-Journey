Day 20 — Cross-Origin Resource Sharing (CORS)
Objective

To understand Same-Origin Policy (SOP), Cross-Origin Resource Sharing (CORS), common CORS misconfigurations, how browsers enforce trust boundaries, and how attackers exploit insecure CORS implementations to access sensitive information.

Concepts Learned
Same-Origin Policy (SOP)

Same-Origin Policy is a browser security mechanism that prevents one website from reading data belonging to another website.

An origin consists of:

Protocol
Domain
Port

Example:

https://shop.com

and

https://api.shop.com

are different origins.

SOP blocks cross-origin access by default.

Cross-Origin Resource Sharing (CORS)

CORS is a browser-controlled mechanism that allows servers to specify which external origins are allowed to access their resources.

CORS acts as an exception to SOP.

Origin Header

Browsers automatically include an Origin header when making cross-origin requests.

Example:

Origin: https://shop.com

The server evaluates this value and determines whether the origin should be trusted.

Access-Control-Allow-Origin

Response header used to specify trusted origins.

Example:

Access-Control-Allow-Origin: https://shop.com

If the browser sees its origin in this header, it allows the response to be read.

Wildcard Origins

Example:

Access-Control-Allow-Origin: *

This allows all origins to access the resource.

While useful for public resources, it can be dangerous when sensitive data is involved.

Origin Reflection

Occurs when a server blindly reflects the supplied Origin value.

Example:

Request:

Origin: https://evil.com

Response:

Access-Control-Allow-Origin: https://evil.com

This may allow attacker-controlled websites to access sensitive responses.

Null Origin

Some applications incorrectly trust:

Origin: null

Attackers may abuse this behavior to bypass origin restrictions.

Theory

Same-Origin Policy was introduced to prevent websites from reading data belonging to other websites.

Without SOP:

Banking information could be stolen
Emails could be exposed
Social media accounts could be compromised

Modern web applications often separate frontend and backend components into different origins.

Example:

https://app.company.com

communicating with:

https://api.company.com

Since SOP would block this communication, CORS allows servers to explicitly trust specific origins.

The browser checks:

Request Origin
Server Response Headers
Trust Decision

If the origin is trusted, access is granted.

Otherwise, the response is blocked.

Practical Testing

Performed CORS testing using Burp Suite Community Edition.

Activities:

Intercepted requests
Modified Origin headers
Sent requests to Repeater
Analyzed server responses
Observed Access-Control-Allow-Origin behavior
Tested origin reflection scenarios
Burp Suite Analysis

Headers Investigated:

Origin
Access-Control-Allow-Origin
Access-Control-Allow-Credentials

Testing Process:

Intercept request.
Send request to Repeater.
Modify Origin header.
Forward request.
Analyze response headers.
Determine whether arbitrary origins are trusted.
PortSwigger Labs
Lab 1

CORS vulnerability with basic origin reflection

Learning Outcome

Identified an application that trusted attacker-controlled origins by reflecting the supplied Origin header.

Lab 2

CORS vulnerability with trusted null origin

Learning Outcome

Observed how trusting null origins can create security weaknesses.

Lab 3

CORS vulnerability due to excessive trust

Learning Outcome

Learned how overly permissive trust relationships increase the risk of sensitive information disclosure.

Security Mindset
Why Does This Vulnerability Exist?

Developers often focus on functionality and unintentionally trust origins they should not trust.

What Trust Assumption Failed?

The application assumes that incoming origins are legitimate and controlled.

Attackers can create any origin they want.

Business Impact

Potential impacts include:

Exposure of customer information
Unauthorized access to sensitive API responses
Privacy violations
Increased attack surface
Prevention
Use strict allowlists
Avoid wildcard origins for sensitive data
Carefully validate trusted origins
Minimize unnecessary cross-origin access
Pentester View

Questions to ask:

Can I control the Origin header?
Does the application reflect arbitrary origins?
Are credentials allowed?
Can sensitive data be accessed cross-origin?
AppSec View

Questions to ask:

Why is this origin trusted?
Is the trust relationship required?
Can trust be restricted further?
What business data is exposed if trust fails?
Common Mistakes
Mistake 1

Confusing SOP with CORS.

SOP blocks by default.

CORS allows exceptions.

Mistake 2

Assuming CORS protects servers.

CORS protects browser users.

Mistake 3

Ignoring Origin headers during testing.

Mistake 4

Assuming wildcard origins are always safe.

Real Attack Model
Scenario

A banking application exposes account details through an API.

API Response:

{
  "account":"12345",
  "balance":"50000"
}

An attacker hosts:

https://evil.com

If the banking API trusts attacker-controlled origins, JavaScript running on evil.com may be able to access sensitive responses belonging to authenticated users.

Result
Sensitive information disclosure
Privacy violations
Potential account compromise
Key Learning
SOP blocks cross-origin reads by default.
CORS allows controlled exceptions to SOP.
CORS vulnerabilities are usually caused by broken trust decisions.
Security depends on determining which origins should be trusted.
The main security question is: "Who is allowed to read this data?"
Tools Used
Burp Suite Community Edition
PortSwigger Web Security Academy
Browser Developer Tools
Screenshots

Add:

Burp request showing modified Origin header
Burp response showing Access-Control-Allow-Origin
Completed PortSwigger lab screenshots
Status

✔ Completed Day 20

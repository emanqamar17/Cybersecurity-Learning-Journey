# Day 11 — Cross-Site Request Forgery (CSRF)

## Objective
Understand how attackers can force authenticated users to perform unwanted actions by exploiting the browser's automatic cookie handling.

## Concepts Learned
- What CSRF (Cross-Site Request Forgery) is
- How browsers automatically send session cookies
- Conditions required for CSRF attacks
- State-changing requests (change email, password, delete account)
- CSRF tokens
- SameSite cookie attribute
- Origin and Referer validation
- Difference between CSRF and XSS

## Practical Testing
- Created a local `csrf-demo.html` file
- Built an auto-submitting HTML form
- Simulated a forged request to change an email address
- Observed how hidden input fields carry attacker-controlled values

## Burp Suite Analysis
- Intercepted the `POST /my-account/change-email` request
- Sent the request to Repeater
- Removed or modified the CSRF token
- Tested whether the server accepted the request
- Generated a CSRF proof-of-concept (manually using Community Edition)

## PortSwigger Labs
- Completed: CSRF vulnerability with no defenses
- Completed: CSRF where token validation depends on request method
- Completed: CSRF where token validation depends on token being present
- Completed: CSRF where token is not tied to user session

## Key Learning
CSRF occurs when:
- a victim is logged into a website
- the browser automatically sends session cookies
- the application does not verify the legitimacy of the request

Applications should:
- use unpredictable CSRF tokens
- validate Origin and Referer headers
- implement SameSite cookies
- require re-authentication for sensitive actions

## Files Created
- `csrf-demo.html`
- `day11-cross-site-request-forgery-csrf.md`

## Screenshots
- Lab description
- Intercepted request in Burp Suite
- Repeater testing
- Generated CSRF HTML proof-of-concept
- Exploit server code
- Lab solved message
- Local `csrf-demo.html` in browser

## Status
✔ Completed Day 11

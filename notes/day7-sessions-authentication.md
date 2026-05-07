# Day 7 — Sessions & Authentication

## 🎯 Objective
Understand how websites maintain login state using cookies and sessions, and observe how authentication changes session behavior.

---

## 🔹 Authentication vs Authorization

### Authentication
Authentication means verifying user identity using credentials such as username and password.

### Authorization
Authorization means determining what an authenticated user is allowed to access.

---

## 🔹 Session Understanding

- HTTP is stateless by default
- Websites use sessions to remember users between requests
- Session data is commonly maintained using cookies

### Key Learning
- Authentication creates or modifies session state
- Sessions preserve user identity across requests

---

## 🔹 Website Used for Testing

### Demo Website
https://the-internet.herokuapp.com/login

### Valid Credentials Used
- Username: tomsmith
- Password: SuperSecretPassword!

---

## 🔹 Cookies Observed

### Before Login
Observed cookie:
- rack.session

Cookie size:
- Approximately 504 bytes

Interpretation:
- Guest session already existed before authentication

---

### Failed Login Attempt

Observation:
- No major cookie/session change observed
- No authenticated session created

Interpretation:
- Server validated credentials before modifying authentication state

---

### Successful Login

Observed:
- rack.session cookie value changed
- Cookie size increased from approximately 504 → 544 bytes

Additional session-related data observed inside encoded session structure:
- session_id
- csrf
- tracking

Interpretation:
- Successful authentication modified session state
- Additional authenticated data added to session

---

## 🔹 Logout Behavior Analysis

### Observation
- rack.session cookie did not disappear after logout
- Cookie value and size changed after logout

### Interpretation
- Authenticated session state was invalidated
- Session remained active as guest session

### Security Understanding
- Secure logout should invalidate authenticated session state
- Changing session value after logout helps prevent session reuse

---

## 🔹 Cookie Classification

### High Security Importance
- rack.session
- csrf/session-related values

### Lower Security Importance
- optimize/analytics/tracking cookies

### Key Learning
- Not all cookies are authentication-related
- Pentesters focus primarily on session/authentication cookies

---

## 🔹 Burp Suite Practical

### Activities Performed
- Intercepted login requests
- Observed POST authentication requests
- Inspected request and response headers
- Observed Set-Cookie behavior
- Modified headers and cookies manually

### Key Learning
- Burp Suite acts as a proxy between browser and server
- Requests can be intercepted and modified before reaching server
- Session and authentication behavior can be analyzed through traffic inspection

---

## 🔹 Security Concepts Learned

- Sessions maintain login state
- Authentication modifies session behavior
- Cookies preserve identity between requests
- Logout should invalidate authenticated state
- Session cookies are high-value targets in web security

---

## 🔹 Overall Learning

Today I learned how websites maintain authentication using session cookies. I observed differences between guest sessions and authenticated sessions, analyzed cookie changes after login/logout, and practiced intercepting requests using Burp Suite. I also learned how to identify high-value security-related cookies.

---

## ✅ Status
✔ Completed Day 7

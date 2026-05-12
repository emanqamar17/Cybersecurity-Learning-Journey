# Day 8 — Authentication Weaknesses

## 🎯 Objective
Understand common authentication weaknesses such as weak passwords, username enumeration, rate limiting, and account lockout.

---

## 🔹 Concepts Learned

### Weak Passwords
Examples:
- 123456
- password
- admin123
- qwerty

### Brute Force
Trying multiple username/password combinations systematically.

### Username Enumeration
Determining whether a username exists by observing differences in application responses.

### Rate Limiting
Restricting repeated login attempts.

### Account Lockout
Temporarily blocking accounts after several failed attempts.

---

## 🔹 Practical Testing

### Demo Targets Used
- The Internet Login Demo
- PortSwigger Web Security Academy labs

### Invalid Username Test
- Username: wronguser
- Password: wrongpass
- Observed the application's error response.

### Valid Username, Wrong Password
- Username: tomsmith
- Password: wrongpass
- Compared the response with the invalid username case.

### Successful Login
- Username: tomsmith
- Password: SuperSecretPassword!
- Observed redirect to authenticated area and session cookie changes.

---

## 🔹 Burp Suite Practice

### Activities Performed
- Intercepted POST login requests
- Compared responses for different credentials
- Used Repeater to resend modified requests
- Reviewed Burp Suite tabs and workflow

### Observation
- HTTP status code remained 200 for both successful and failed login attempts on some targets.
- Authentication success and failure were distinguished by response content rather than status code.

### Key Learning
- Status code alone is often insufficient.
- Response body, redirects, and cookies must also be analyzed.

---

## 🔹 PortSwigger Lab

### Completed
Authentication-related lab focusing on username enumeration and login analysis.

### Key Takeaway
Different responses can reveal valid usernames and authentication behavior.

---

## 🔹 Security Best Practices Learned

Secure authentication should:
- Use strong passwords
- Return generic error messages
- Implement rate limiting
- Support account lockout
- Require multi-factor authentication

---

## 🔹 Overall Learning

Today I learned how attackers and pentesters analyze login systems. I practiced comparing responses for invalid usernames, incorrect passwords, and successful logins. I also improved my understanding of Burp Suite, especially Intercept and Repeater.


---

## ✅ Status
✔ Completed Day 8

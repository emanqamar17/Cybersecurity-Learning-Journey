# Day 18 — Authentication & Access Control

## Objective

Understand how applications authenticate users, authorize actions, and how broken access control vulnerabilities can lead to privilege escalation and unauthorized access.

---

# Concepts Learned

- Authentication
- Authorization
- Access Control
- Horizontal Privilege Escalation
- Vertical Privilege Escalation
- Forced Browsing
- Role-Based Access Control (RBAC)
- Parameter-Based Access Control
- Broken Access Control
- IDOR Relationship with Access Control

---

# Authentication vs Authorization

## Authentication

Authentication answers:

"Who are you?"

Examples:

- Username and Password
- OTP
- MFA
- Biometrics

Authentication verifies a user's identity.

---

## Authorization

Authorization answers:

"What are you allowed to do?"

Examples:

- Access admin panel
- View invoices
- Edit profiles
- Delete users

Authorization determines permissions after login.

---

# Access Control

Access control ensures users can only perform actions they are authorized to perform.

Example:

User A should only access User A's profile.

User B should only access User B's profile.

---

# Horizontal Privilege Escalation

Occurs when a user accesses another user's resources while remaining at the same privilege level.

Example:

User A:

/profile?id=100

Changes:

/profile?id=101

Receives User B's data.

---

# Vertical Privilege Escalation

Occurs when a lower privileged user gains higher privileges.

Example:

Normal user accesses:

/admin

and gains administrator functionality.

---

# Forced Browsing

Attempting to access hidden or unlinked resources directly.

Examples:

/admin
/admin-panel
/backup
/config

Security through obscurity is not security.

---

# Parameter-Based Access Control

Applications should never trust user-controlled parameters.

Example:

role=user

changed to:

role=admin

may result in privilege escalation if validation is missing.

---

# Role-Based Access Control (RBAC)

Applications often assign permissions based on roles.

Examples:

- Guest
- User
- Moderator
- Admin

Testing objective:

Can lower privilege users perform higher privilege actions?

---

# Relationship Between IDOR and Access Control

IDOR is actually a Broken Access Control vulnerability.

Example:

/account?id=100

changed to:

/account?id=101

If another user's data becomes accessible, authorization checks are missing.

---

# Practical Testing

Created:

access-control-testing-checklist.txt

Checklist included:

- Access admin pages
- Modify user IDs
- Access other profiles
- Access invoices
- Modify role parameters
- Forced browsing tests

---

# Burp Suite Analysis

Used Burp Suite to:

- Intercept requests
- Compare user and admin requests
- Analyze parameters
- Modify identifiers
- Test authorization controls

---

# PortSwigger Labs Completed

## Lab 1

✔ Unprotected admin functionality

### Key Learning

Sensitive administrative functionality should never rely on hidden URLs alone.

---

## Lab 2

✔ Unprotected admin functionality with unpredictable URL

### Key Learning

Guessing hidden URLs can expose administrative functionality.

---

## Lab 3

✔ User role controlled by request parameter

### Key Learning

Applications should never trust client-controlled role values.

---

## Lab 4

✔ User role controlled by hidden parameter

### Key Learning

Hidden parameters are not secure because attackers can modify them.

---

## Lab 5

✔ User ID controlled by request parameter

### Key Learning

User-controlled identifiers frequently lead to IDOR vulnerabilities.

---

# Common Access Control Testing Questions

Can I:

- Access admin functionality?
- Access another user's data?
- Modify identifiers?
- Change role values?
- Perform unauthorized actions?
- Access hidden resources?

---

# Prevention

Applications should:

- Enforce server-side authorization
- Validate permissions on every request
- Use role-based access control
- Avoid trusting client-side parameters
- Log authorization failures

---

# Key Learning

Authentication identifies users.

Authorization controls what users can do.

Many serious vulnerabilities occur because applications authenticate users correctly but fail to enforce authorization checks.

---

# Personal Reflection

## What did I learn today?

I learned the difference between authentication and authorization and how broken access control vulnerabilities can expose sensitive functionality.

## What challenged me?

Understanding the distinction between horizontal and vertical privilege escalation.

## What will I improve?

I want to become faster at identifying access control weaknesses during application testing.

# Tools Used

- Burp Suite Community Edition
- PortSwigger Web Security Academy
- GitHub
- Git

---

# Interview Questions

## What is Authentication?

The process of verifying user identity.

---

## What is Authorization?

The process of determining user permissions.

---

## What is Horizontal Privilege Escalation?

Accessing another user's resources while maintaining the same privilege level.

---

## What is Vertical Privilege Escalation?

Gaining higher privileges than originally assigned.

---

## What is Forced Browsing?

Directly accessing hidden or unlinked resources.

---

## Status

✔ Completed Day 18

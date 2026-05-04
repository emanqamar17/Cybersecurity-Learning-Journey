# Day 4 — HTTP Parameters & SQL Injection Basics

## 🎯 Objective
Understand how user input flows through web applications and how improper handling can lead to vulnerabilities like SQL Injection.

---

## 🔹 1. Parameter Testing (Browser DevTools)

### What I Did
- Used browser DevTools to inspect network requests
- Modified URL parameters manually

### Example
/search?q=phone → /search?q=laptop

### Observation
- Changing parameters directly affected application output
- Confirms that user input is processed by backend

---

## 🔹 2. HTTP Fundamentals (TryHackMe)

Platform: TryHackMe

### Concepts Covered
- HTTP methods (GET, POST)
- Request & response structure
- Headers and status codes

### Key Learning
- Every web interaction is based on request-response cycle
- User input is sent via parameters

---

## 🔹 3. SQL Injection — Login Bypass (PortSwigger)

### Objective
Bypass authentication without valid credentials

### What I Did
- Tested login input fields
- Injected crafted input into email field

### Result
- Successfully logged in as administrator

### Key Concept
- SQL comment (`--`) ignored password condition
- Backend query logic was manipulated

---

## 🔹 4. SQL Injection — Data Retrieval via URL

### Objective
Understand how URL parameters affect database queries

### What I Did
- Modified URL parameter (e.g., category)
- Injected logical condition

### Example
/products?category=Gifts' OR 1=1--

### Result
- Application returned more data than expected

### Key Concept
- User input directly influences database queries
- Weak input validation leads to data exposure

---

## 🔹 Overall Learning

- Input fields and URL parameters are critical attack surfaces
- Backend logic can be manipulated if input is not sanitized
- Small changes in input can significantly affect output




## ✅ Status
✔ Completed Day 4 successfully

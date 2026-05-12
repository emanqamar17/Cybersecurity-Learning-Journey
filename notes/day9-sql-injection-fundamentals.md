# Day 9 — SQL Injection Fundamentals

## 🎯 Objective
Develop a deep understanding of SQL Injection and practice common techniques used to identify and exploit SQL Injection vulnerabilities.

---

## 🔹 Concepts Learned

### What is SQL Injection?
SQL Injection occurs when user input is inserted directly into a SQL query without proper validation or parameterized queries, allowing an attacker to modify the query logic.

### Basic SQL Keywords
- SELECT
- FROM
- WHERE
- AND
- OR
- ORDER BY
- UNION SELECT

### Special Characters
- '  (single quote)
- -- (comment)

---

## 🔹 SQL Injection Techniques Studied

### 1. Detecting SQL Injection
Used a single quote (') to trigger SQL errors or response changes.

### 2. Retrieving Hidden Data
Modified WHERE conditions to reveal additional records.

### 3. Subverting Application Logic
Bypassed login functionality using:
administrator'--

### 4. Determining Number of Columns
Used:
' ORDER BY 1--
' ORDER BY 2--
' ORDER BY 3--

Increased the column number until an error occurred.

### 5. UNION Attacks
Used UNION SELECT to combine attacker-controlled data with the original query output.

### 6. Finding Text-Compatible Columns
Used NULL placeholders and inserted strings to identify columns capable of displaying text.

### 7. Retrieving Interesting Data
Extracted information such as usernames and passwords using UNION SELECT.

---

## 🔹 Practical Work

### PortSwigger Labs Completed
- SQL injection vulnerability in WHERE clause allowing retrieval of hidden data
- SQL injection vulnerability allowing login bypass
- UNION-based SQL injection labs

### Burp Suite Activities
- Intercepted HTTP requests
- Modified parameters
- Sent requests to Repeater
- Observed response differences

---

## 🔹 Key Payload Examples

### Login Bypass
administrator'--

### Always True Condition
' OR '1'='1

### Column Count Detection
' ORDER BY 1--

### UNION Test
' UNION SELECT NULL, NULL--

---

## 🔹 Important Concepts

### ORDER BY
Used to determine the number of columns returned by the original query.

### NULL
Used as a placeholder because it is compatible with most data types.

### UNION SELECT
Combines results from two SELECT statements.

---

## 🔹 Security Impact
SQL Injection can lead to:
- Authentication bypass
- Data disclosure
- Data modification
- Administrative compromise

---

## 🔹 Prevention
- Parameterized queries
- Prepared statements
- Input validation
- Least privilege database accounts

---

## 🔹 Overall Learning
Today I developed a much stronger understanding of how SQL Injection works. I practiced detecting vulnerable parameters, bypassing authentication, determining column counts, and extracting data using UNION-based techniques.

---


## ✅ Status
✔ Completed Day 9

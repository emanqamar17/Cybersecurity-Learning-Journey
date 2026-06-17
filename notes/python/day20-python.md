# Day 20 Python — Lists

## Objective

Learn Python Lists, how data is stored inside lists, how elements are accessed, and why lists are widely used in cybersecurity automation.

---

# Concept Learned

## What Is A List?

A List is a collection of multiple values stored inside a single variable.

Example:

```python
ports = [80, 443, 8080]
```

Instead of creating multiple variables:

```python
port1 = 80
port2 = 443
port3 = 8080
```

Python allows us to store everything in one list.

---

# Why Lists Matter

Security professionals frequently store:

* Ports
* IP Addresses
* URLs
* Usernames
* Payloads
* Target Systems

inside lists.

Lists make automation possible.

---

# Example Program

```python
ports = [80, 443, 8080]

print(ports)
```

---

# Line-by-Line Explanation

## ports

Variable name.

Stores data for later use.

---

## =

Assignment operator.

Assigns data to a variable.

---

## [ ]

Square brackets create a list.

---

## 80, 443, 8080

Elements inside the list.

Each value is called an element.

---

## print()

Displays information on the screen.

---

# Output

```python
[80, 443, 8080]
```

---

# Accessing Individual Elements

Example:

```python
ports = [80, 443, 8080]

print(ports[0])
```

Output:

```python
80
```

---

# Understanding Indexes

Python starts counting from:

```python
0
```

not:

```python
1
```

Example:

| Index | Value |
| ----- | ----- |
| 0     | 80    |
| 1     | 443   |
| 2     | 8080  |

---

# Why Python Starts From Zero

This concept is called:

Zero-Based Indexing

Most programming languages use this approach because it simplifies memory management.

---

# Cybersecurity Relevance

Imagine creating a simple scanner.

Instead of testing one port:

```python
80
```

You can test many:

```python
ports = [80, 443, 8080, 3306]
```

A loop can then check each port automatically.

This is one of the foundations of security automation.

---

# Practical Exercise

Create:

```python
web_ports = [80, 443, 8080]

print(web_ports)
print(web_ports[0])
print(web_ports[1])
print(web_ports[2])
```

Observe the output.

---

# Key Learning

* Lists store multiple values in a single variable.
* Elements are accessed using indexes.
* Python indexing starts from zero.
* Lists are heavily used in cybersecurity automation.
* Many security tools use lists to store targets and payloads.

---

# Future Application

Lists will later be used for:

* Port Scanners
* URL Enumeration
* Payload Management
* Vulnerability Automation Scripts

---

# Status

✔ Completed Day 20 Python

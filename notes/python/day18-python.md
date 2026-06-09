# Day 18 — Python Loops

## Objective

Learn how Python repeats tasks using loops.

---

# What Is A Loop?

A loop repeats code multiple times.

Without loops:

```python
print("Hello")
print("Hello")
print("Hello")
```

With loops:

```python
for i in range(3):
    print("Hello")
```

---

# For Loop

## Example

```python
for i in range(5):
    print(i)
```

Output:

0
1
2
3
4

---

## Explanation

for = repeat

i = variable storing current value

range(5) = numbers from 0 to 4

---

## Memory Trick

For each value, do something.

---

# Loop Through List

## Example

```python
tools = ["Burp", "Nmap", "Wireshark"]

for tool in tools:
    print(tool)
```

Output:

Burp
Nmap
Wireshark

---

## Explanation

List contains multiple values.

Loop processes one value at a time.

---

# While Loop

## Example

```python
count = 1

while count <= 5:
    print(count)
    count += 1
```

Output:

1
2
3
4
5

---

## Explanation

while = continue while condition is true

count += 1

means:

count = count + 1

---

# Difference Between For and While

For Loop:

Use when number of repetitions is known.

Example:

```python
for i in range(5)
```

---

While Loop:

Use when condition controls repetition.

Example:

```python
while count <= 5
```

---

# Why Security Professionals Use Loops

Loops are heavily used in:

- Automation
- Scanning
- Log analysis
- Scripting
- Data processing

---

# Practical Exercise

Created:

day18.py

Included:

- For loop
- List iteration
- While loop

---

# Learning Outcome

Learned how Python automates repetitive tasks using loops.

---

# Status

✔ Completed Day 18 Python

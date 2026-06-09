# Day 18 — Linux Search Commands

## Objective

Learn how to locate files and search for information in Linux.

---

# Command 1: find

## Syntax

```bash
find . -name filename
```

## Example

```bash
find . -name users.txt
```

## Explanation

find = search for files

. = start searching from current directory

-name = search by file name

users.txt = target file

---

## What It Does

Searches folders and subfolders for matching files.

---

## Why Security Professionals Use It

Used to locate:

- Log files
- Password files
- Configuration files
- Evidence files

---

## Memory Trick

Think:

"Find this file for me."

---

# Command 2: grep

## Syntax

```bash
grep "word" filename
```

## Example

```bash
grep "admin" users.txt
```

## Explanation

grep = search text

"admin" = text to find

users.txt = file to search

---

## What It Does

Searches inside files.

---

## Example File

```text
admin
guest
user
```

Command:

```bash
grep admin users.txt
```

Output:

```text
admin
```

---

## Why Security Professionals Use It

Search:

- Logs
- Password dumps
- Configuration files
- Error messages

---

## Memory Trick

grep = "search inside file"

---

# Command 3: which

## Syntax

```bash
which command
```

## Example

```bash
which python
```

Output:

```text
/usr/bin/python
```

---

## What It Does

Shows where a program is installed.

---

## Why Security Professionals Use It

Useful for:

- Checking installed tools
- Locating executables
- Verifying paths

---

## Memory Trick

Which program am I using?

---

# Practical Exercise

```bash
echo "admin user" > users.txt

grep admin users.txt

find . -name users.txt

which python
```

---

# Learning Outcome

Learned how to:

- Search files
- Search text inside files
- Locate installed programs

---

# Status

✔ Completed Day 18 Linux

# Day 15 — Linux Basics

## Objective

Learn fundamental Linux navigation commands used in cybersecurity, penetration testing, and application security.

---

## Why Linux Matters

Linux powers most web servers, cloud infrastructure, and security tools.

Application Security Engineers frequently work with Linux systems when:

- Reviewing logs
- Testing applications
- Analyzing vulnerabilities
- Managing servers
- Running security tools

---

## Commands Practiced

### pwd

Displays the current working directory.

```bash
pwd
```

Example Output:

```text
/home/kali
```

Learning:

- Helps identify current location in the filesystem.

---

### ls

Lists files and folders.

```bash
ls
```

Example Output:

```text
Desktop
Documents
Downloads
```

Learning:

- View available files and directories.

---

### ls -la

Displays detailed information including hidden files.

```bash
ls -la
```

Learning:

- View file permissions
- View ownership
- View hidden files

---

### cd

Changes directory.

```bash
cd Desktop
```

Learning:

- Navigate through the filesystem.

---

### cd ..

Moves to the parent directory.

```bash
cd ..
```

Learning:

- Understand filesystem hierarchy.
- Similar concept used in Directory Traversal attacks.

---

## Practical Exercise

Executed:

```bash
pwd
ls
ls -la
cd Desktop
pwd
cd ..
pwd
```

---

## Key Learning

Linux navigation is a fundamental skill for:

- Web Application Security
- Application Security
- Penetration Testing
- Cloud Security

Understanding directory structures helps when testing:

- Directory Traversal
- File Upload Vulnerabilities
- Command Injection

---

## Interview Questions

### What does pwd do?

Displays the current working directory.

### What does ls do?

Lists files and folders.

### What does ls -la show?

Detailed file information including hidden files.

### What does cd .. do?

Moves to the parent directory.

---

## Status

✔ Completed Day 15 Linux Track

# Day 15 — Command Injection

## Objective

Understand how attackers exploit applications that execute user-controlled input as operating system commands.

---

## Concepts Learned

- Command Injection
- Operating System Command Execution
- Shell Operators
- Command Chaining
- Visible Command Injection
- Blind Command Injection
- Time-Based Detection
- Output Redirection
- Out-of-Band (OOB) Command Injection
- Linux Commands in Security Testing

---

## What is Command Injection?

Command Injection occurs when an application passes user input directly into a system command without proper validation.

### Vulnerable Example

```php
system("ping " . $_GET['ip']);
```

Normal Input:

```text
127.0.0.1
```

Executed Command:

```bash
ping 127.0.0.1
```

Malicious Input:

```text
127.0.0.1; whoami
```

Executed Command:

```bash
ping 127.0.0.1
whoami
```

---

## Difference Between SQL Injection and Command Injection

| SQL Injection | Command Injection |
|--------------|------------------|
| Targets databases | Targets operating system |
| Executes SQL queries | Executes OS commands |
| Database compromise | Server compromise |
| Uses SELECT, UNION | Uses whoami, id, ls |

---

## Important Linux Commands

### whoami

Displays the current user.

```bash
whoami
```

### id

Displays user information.

```bash
id
```

### pwd

Displays current directory.

```bash
pwd
```

### ls

Lists files and folders.

```bash
ls
```

### cat

Reads file contents.

```bash
cat /etc/passwd
```

---

## Command Separators

### Semicolon (;)

```text
127.0.0.1; whoami
```

Runs the second command after the first.

### AND Operator (&&)

```text
127.0.0.1 && whoami
```

Runs the second command if the first succeeds.

### Pipe (|)

```text
127.0.0.1 | whoami
```

Passes output between commands.

### Ampersand (&)

```text
127.0.0.1 & whoami
```

Runs commands in the background.

---

## Visible Command Injection

The output of the injected command is directly returned in the response.

Example Output:

```text
www-data
```

---

## Blind Command Injection

Command execution occurs but output is not visible.

Attackers use alternative methods to verify execution.

### Time Delay Technique

Payload:

```text
127.0.0.1; sleep 10
```

If the response is delayed by 10 seconds, command execution is confirmed.

---

## Out-of-Band (OOB) Command Injection

The server makes an external request to an attacker-controlled system.

Used when command output is unavailable.

Concept Studied Theoretically.

---

## Practical Testing

Created:

```text
command-injection-demo.txt
```

Tested payload examples:

```text
127.0.0.1; whoami
127.0.0.1 && id
127.0.0.1; pwd
127.0.0.1; ls
127.0.0.1; cat /etc/passwd
127.0.0.1; sleep 10
```

Learned how command separators affect execution flow.

---

## Burp Suite Analysis

- Intercepted HTTP requests
- Sent requests to Repeater
- Modified user-controlled parameters
- Tested command injection payloads
- Observed command execution behavior
- Analyzed responses for evidence of injection

Example:

Original Request:

```http
POST /check
ip=127.0.0.1
```

Modified Request:

```http
POST /check
ip=127.0.0.1;whoami
```

---

## PortSwigger Labs

### Completed

✔ OS Command Injection, Simple Case

### Completed

✔ Blind OS Command Injection with Time Delays

### Completed

✔ Blind OS Command Injection with Output Redirection

### Not Completed

⚠ Blind OS Command Injection with Out-of-Band Interaction

Reason:

Burp Collaborator is required, which is available only in Burp Suite Professional Edition.

Concept studied theoretically.

---

## Key Learning

Applications should never execute user-controlled input as operating system commands.

Command Injection can lead to:

- Information Disclosure
- Server Compromise
- Arbitrary Command Execution
- Remote Access
- Remote Shells
- Full System Takeover

---

## Linux Practice

Commands Practiced:

```bash
pwd
ls
ls -la
cd Desktop
cd ..
```

### Learning Outcome

- Navigated directories
- Viewed files
- Listed hidden files
- Understood parent directory concept

---

## Screenshots

### Web Security

- Lab Description
- Modified Request
- Successful Exploitation
- Time Delay Verification
- Output Redirection
- Lab Solved Message

### Linux

- pwd Command
- ls Command
- ls -la Command
- cd Navigation

### Python

- Python Version Verification
- Hello Cybersecurity Program
- Variables Program
- User Input Program

---

## Tools Used

- Burp Suite Community Edition
- PortSwigger Web Security Academy
- Kali Linux
- Python
- GitHub

---

## Interview Questions

### What is Command Injection?

A vulnerability that allows attackers to execute operating system commands through user-controlled input.

### Why is Command Injection dangerous?

Because it can lead to arbitrary command execution and full server compromise.

### What is Blind Command Injection?

Command execution occurs but output is not directly visible.

### How can Blind Command Injection be detected?

- Time Delays
- Output Redirection
- Out-of-Band Techniques

### Difference Between Remote Access and Remote Shell?

Remote Access is the ability to interact with a system remotely.

A Remote Shell provides an interactive command-line session on the target system.

---

## Status

✔ Completed Day 15
✔ Completed Linux Practice
✔ Completed Python Basics
✔ Completed PortSwigger Labs

# Day 14 — Directory Traversal (Path Traversal)

## Objective
Understand how attackers access files outside the intended directory by manipulating file path parameters.

## Concepts Learned
- Directory Traversal
- Path Traversal
- Relative Paths
- Parent Directory (`../`)
- Path Normalization
- URL Encoding
- Double URL Encoding
- Null Byte Injection (Legacy)
- Linux Sensitive Files
- Windows Sensitive Files

## Practical Testing
- Practiced traversal payloads using `../`
- Tested access to sensitive files such as:
  - `/etc/passwd`
  - `/etc/hosts`
  - `/proc/version`
- Learned how path normalization works
- Tested encoded traversal payloads

## Burp Suite Analysis
- Intercepted file-loading requests
- Identified filename parameters
- Modified file paths using traversal sequences
- Sent requests to Repeater
- Tested URL-encoded traversal payloads
- Analyzed server responses

## PortSwigger Labs
- Completed: File path traversal, simple case
- Completed: Traversal sequences blocked with absolute path bypass
- Completed: Traversal sequences stripped non-recursively
- Completed: Traversal sequences stripped with superfluous URL decode
- Completed: Validation of start of path
- Completed: Validation of file extension with null byte bypass

## Common Payloads Tested

### Linux
```text
../../../etc/passwd
../../../../etc/passwd
..%2f..%2f..%2fetc/passwd
..%252f..%252f..%252fetc/passwd
```

### Windows
```text
..\..\..\Windows\win.ini
```

## Key Learning

Directory Traversal occurs when applications use user-controlled input to build file paths without proper validation.

Attackers can:

- Read sensitive files
- Access configuration files
- Expose credentials
- Read source code
- Access backup files

Applications should:

- Validate file paths
- Restrict access to approved directories
- Normalize paths securely
- Use allowlisted filenames
- Reject traversal sequences

## Important Files

### Linux Targets

```text
/etc/passwd
/etc/hosts
/proc/version
```

### Windows Targets

```text
C:\Windows\win.ini
C:\Windows\System32\drivers\etc\hosts
```

## Files Created

- `path-traversal-demo.txt`
- `day14-directory-traversal.md`

## Screenshots

- Lab description
- Original request
- Modified traversal request
- Successful `/etc/passwd` response
- URL encoded payload
- Lab solved message

## Tools Used

- Burp Suite Community Edition
- PortSwigger Web Security Academy
- Google Chrome
- GitHub

## Interview Questions

### What is Directory Traversal?

A vulnerability that allows attackers to access files outside the intended directory by manipulating file paths.

### What does `../` mean?

It refers to the parent directory.

### Why is `/etc/passwd` commonly used in testing?

It is a readable Linux system file that confirms successful traversal.

### What is URL Encoding?

Encoding special characters to bypass input filters.

### What is Double URL Encoding?

Encoding already encoded characters to bypass weak filtering mechanisms.

## Status

✔ Completed Day 14

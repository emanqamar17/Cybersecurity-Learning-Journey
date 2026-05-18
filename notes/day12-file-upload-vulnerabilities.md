# Day 12 — File Upload Vulnerabilities

## Objective
Understand how insecure file upload functionality can allow attackers to upload malicious files and achieve Remote Code Execution (RCE).

## Concepts Learned
- File upload vulnerabilities
- Web shells
- Remote Code Execution (RCE)
- Multipart/form-data
- MIME types
- File extensions
- Bypass techniques
- Double extensions
- Alternate extensions
- Case variation
- Null byte injection (legacy)
- Magic bytes
- File signatures
- Content-Type manipulation

## Practical Testing
- Created a basic PHP web shell:
  `<?php system($_GET['cmd']); ?>`
- Studied how uploaded files can be executed by the server
- Tested file extension and MIME type validation
- Explored common upload bypass techniques
- Practiced identifying uploaded file URLs

## Burp Suite Analysis
- Intercepted `multipart/form-data` upload requests
- Modified the filename from an image to `shell.php`
- Changed `Content-Type` from `application/x-php` to `image/jpeg`
- Tested alternate extensions such as `.phtml`
- Forwarded requests and analyzed server responses
- Located and accessed the uploaded file

## PortSwigger Labs
- Completed: Remote code execution via web shell upload
- Completed: Web shell upload via Content-Type restriction bypass
- Completed: Web shell upload via blacklist extension bypass
- Completed: Web shell upload via obfuscated file extension

## Key Learning
File upload vulnerabilities occur when applications do not properly validate uploaded files.

Attackers may bypass weak defenses by:
- Changing file extensions
- Using alternate executable extensions
- Spoofing MIME types
- Adding valid magic bytes
- Obfuscating filenames

Secure applications should:
- Allow only trusted file types
- Validate file signatures
- Rename uploaded files
- Store uploads outside the web root
- Disable script execution in upload directories

## Files Created
- `simple-shell.php`
- `day12-file-upload-vulnerabilities.md`

## Important Terms

### Web Shell
A server-side script that allows execution of operating system commands through a web browser.

### MIME Type
A value in the HTTP request that tells the server what type of file is being uploaded, such as:
- `image/jpeg`
- `image/png`
- `application/pdf`

### File Signature (Magic Bytes)
The first few bytes of a file used to identify its actual format.

Examples:
- JPEG: `FF D8 FF`
- PNG: `89 50 4E 47`
- PDF: `%PDF`

### Bypass Techniques
Methods used to evade upload validation checks.

Examples:
- `shell.php.jpg`
- `shell.phtml`
- `shell.PHP`
- `shell.php%00.jpg` (legacy)

## Impact
Successful exploitation can lead to:
- Remote Code Execution (RCE)
- Full server compromise
- Data theft
- Website defacement
- Malware hosting

## Screenshots
- Lab description
- Original upload request
- Modified multipart/form-data request
- Successful upload response
- Accessing the uploaded web shell
- Lab solved message
- Local `simple-shell.php`
- GitHub repository update

## Tools Used
- Burp Suite Community Edition
- Google Chrome
- PortSwigger Web Security Academy
- Visual Studio Code
- Git
- GitHub

## Interview Questions

### What is a file upload vulnerability?
A security flaw that allows attackers to upload dangerous files to a server.

### What is a web shell?
A server-side script used to execute operating system commands remotely.

### What is MIME type spoofing?
Changing the `Content-Type` header to bypass weak validation.

### What are magic bytes?
The first bytes of a file that identify its format.

### What is Remote Code Execution (RCE)?
The ability to execute commands on the target server.

## Files and Paths
- Notes file: `notes/day12-file-upload-vulnerabilities.md`
- Screenshots folder: `notes/screenshots/`

## Git Commands Used
git add .
git commit -m "Add Day 12 notes on File Upload Vulnerabilities"
git push origin main

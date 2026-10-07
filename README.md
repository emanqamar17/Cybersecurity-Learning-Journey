# 🔐 Cybersecurity Learning Journey

> **120-Day Web Application Security & Application Security Learning Journey**

This repository documents my structured journey into **Web Application Security, Penetration Testing, and Application Security Engineering**.

Rather than only studying vulnerability definitions, my goal is to understand **how web applications work, why security vulnerabilities exist, how they can be identified and validated, and how developers can prevent them.**

My learning approach combines:

**Theory → Security Mindset → Manual Testing → Burp Suite → PortSwigger Labs → Linux → Python → Documentation**

---

## 📍 Current Progress

**20 / 120 Days Completed**

```text
████████░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░ 16.7%
```

**Current Stage:** Web Application Security Foundations  
**Latest Topic:** CORS, SOP & Cross-Origin Security Model  
**Next:** Day 21

> Detailed progress is maintained in [`ROADMAP-PROGRESS.md`](ROADMAP-PROGRESS.md).

---

# 🎯 Objective

The purpose of this project is to build a strong technical foundation for a career progressing toward:

```text
Web Application Security
        ↓
Junior Penetration Tester
        ↓
Web Application Security Tester
        ↓
Application Security Engineer
        ↓
Security Engineer
```

The focus is not on memorizing payloads.

For every vulnerability or security mechanism, I try to understand:

- **What** is happening?
- **How** does it work?
- **Why** does the vulnerability exist?
- What trust assumption failed?
- Where is the trust boundary?
- What can an attacker control?
- What is the realistic security impact?
- How would a penetration tester identify it?
- How would an Application Security Engineer prevent it?

---

# 🧠 Learning Philosophy

A major goal of this journey is developing a **security mindset** rather than simply collecting tools or completing labs.

For each topic, I work through the following process:

```text
UNDERSTAND
    ↓
OBSERVE
    ↓
REASON
    ↓
TEST
    ↓
VALIDATE
    ↓
ANALYZE IMPACT
    ↓
UNDERSTAND THE FIX
    ↓
DOCUMENT
```

This means learning both sides of application security:

### Offensive Perspective

How can the application be abused?

### Defensive Perspective

Why did the weakness exist, and how should the application have been designed securely?

---

# 🛡️ Web Application Security Topics

The first stage of the roadmap has covered foundations and common web vulnerability classes.

### Web & Network Foundations

- Internet fundamentals
- IP addresses
- DNS
- TCP / UDP
- Ports and protocols
- Nmap fundamentals
- HTTP requests and responses
- HTTP methods
- HTTP headers
- HTTP status codes
- Cookies and sessions
- Browser Developer Tools

### Authentication & Session Security

- Authentication fundamentals
- Weak password security
- Username enumeration
- Brute-force concepts
- Session management
- Session hijacking
- Session fixation
- Cookie security
- JWT structure
- JWT signature verification
- Weak JWT secrets
- Authentication tokens

### Web Vulnerabilities

- SQL Injection
- Cross-Site Scripting (XSS)
  - Reflected XSS
  - Stored XSS
  - DOM XSS
- Cross-Site Request Forgery (CSRF)
- File Upload Vulnerabilities
- Directory / Path Traversal
- IDOR / Broken Access Control
- OS Command Injection
- Server-Side Request Forgery (SSRF)
- XML External Entity (XXE)

### Access Control

- Authentication vs Authorization
- Horizontal Privilege Escalation
- Vertical Privilege Escalation
- Role-Based Access Control concepts

### Browser Security

- Same-Origin Policy (SOP)
- Origin Model
- Cross-Origin Resource Sharing (CORS)
- Credentialed Cross-Origin Requests
- CORS Misconfiguration

---

# 🧪 Practical Learning

Theory is combined with hands-on practice using intentionally vulnerable and authorized environments.

My primary practice platform is:

### PortSwigger Web Security Academy

Labs are used to understand:

- vulnerability discovery
- HTTP request manipulation
- exploitation logic
- application behavior
- attack validation
- security impact
- remediation concepts

The objective is not simply to obtain a **Solved** status.

For each lab I try to understand:

> **Why did the attack work?**

and:

> **What security assumption allowed it to happen?**

---

# 🧰 Burp Suite Practice

**Burp Suite Community Edition** is my primary web application testing tool.

Current practical experience includes:

- Proxy
- Intercept
- HTTP History
- Repeater
- Request modification
- Response analysis
- Header manipulation
- Cookie/session analysis
- Parameter manipulation
- Authentication testing
- Authorization testing
- Manual vulnerability validation

My focus is on developing a repeatable testing methodology rather than depending entirely on automated scanning.

---

# 🐧 Linux Track

Linux is being developed alongside web application security.

The goal is to become comfortable working in Linux environments commonly used for:

- penetration testing
- security tooling
- networking
- automation
- troubleshooting
- security engineering

Linux notes are maintained separately:

📂 [`notes/linux/`](notes/linux/)

Each lesson focuses on understanding:

```text
Command
   ↓
Syntax
   ↓
Options / Flags
   ↓
Why it exists
   ↓
Security use case
   ↓
Practical exercise
```

---

# 🐍 Python for Security

Python is another parallel learning track.

The goal is to progress from programming fundamentals toward writing small security tools and automation scripts.

Current learning emphasizes understanding code rather than copying scripts.

Topics are introduced progressively through:

```text
Programming Concept
        ↓
Syntax
        ↓
Small Program
        ↓
Security Use Case
        ↓
Practical Exercise
```

Python documentation:

📂 [`notes/python/`](notes/python/)

---

# 🔎 Security Testing Mindset

When examining an application, I am training myself to ask questions such as:

```text
What functionality exists?

What data can I control?

What does the application trust?

Where does privilege change?

What should this user NOT be able to access?

Is security enforced by the browser or the server?

What happens if I modify this request?

Can I bypass the intended workflow?

What proves this is actually vulnerable?

What is the realistic impact?

How should this have been implemented securely?
```

The long-term objective is to move from:

**"I know this vulnerability."**

to:

**"I can recognize the conditions that create this vulnerability."**

---

# ⚔️ Pentester Perspective

For each vulnerability, I practice thinking through a basic professional testing workflow:

```text
Discovery
   ↓
Observation
   ↓
Hypothesis
   ↓
Manual Testing
   ↓
Burp Validation
   ↓
Impact Confirmation
   ↓
Evidence
   ↓
Reporting
```

An unusual response is not automatically a vulnerability.

A finding needs to be validated before drawing conclusions about exploitability or impact.

---

# 🏗️ Application Security Perspective

My long-term direction is **Application Security Engineering**, so this roadmap also looks beyond exploitation.

For each vulnerability I try to understand:

- Why developers introduce it
- Which trust assumption failed
- Where the weakness exists in the application
- How secure design could prevent it
- What server-side controls are required
- How an AppSec Engineer could identify it
- How the vulnerability class can be prevented rather than fixing only one endpoint

This allows offensive security knowledge to gradually develop into defensive engineering knowledge.

---

# 🛠️ Tools & Technologies

Tools used during this learning journey include:

| Category | Tools |
|---|---|
| Web Security | Burp Suite Community Edition |
| Web Security Labs | PortSwigger Web Security Academy |
| Browser Analysis | Chrome DevTools |
| Operating System | Kali Linux |
| Network Reconnaissance | Nmap |
| Content Discovery | ffuf, SecLists |
| Version Control | Git, GitHub |

I have also gained exposure to additional offensive-security tooling through internship/lab work, but this repository primarily focuses on my **Web Application Security and AppSec learning path**.

---

# 📁 Repository Structure

```text
Cybersecurity-Learning-Journey/
│
├── README.md
├── ROADMAP-PROGRESS.md
│
└── notes/
    │
    ├── cheatsheets/
    ├── linux/
    ├── python/
    ├── screenshots/
    │
    ├── day1-...
    ├── day2-...
    ├── day3-...
    ├── ...
    └── day20-...
```

### `README.md`

Overview of the complete learning project.

### `ROADMAP-PROGRESS.md`

Tracks my progress through the 120-day roadmap, including completed topics and the current learning position.

### `notes/`

Detailed daily Web Application Security documentation.

### `notes/linux/`

Parallel Linux learning documentation.

### `notes/python/`

Parallel Python-for-security documentation.

### `notes/screenshots/`

Practical evidence and screenshots from authorized labs and learning environments.

### `notes/cheatsheets/`

Reference material created during the learning process.

---

# 📚 Daily Documentation

Each day's documentation may contain:

- Objective
- Concepts learned
- Technical theory
- Security mindset
- Real-world attack model
- Burp Suite analysis
- PortSwigger labs
- Pentester perspective
- Application Security perspective
- Common mistakes
- Interview questions
- Key takeaways
- Personal reflection
- Screenshots
- Tools used

This makes the repository both a learning record and a reference I can return to later.

---

# 📈 Current Development Areas

As the roadmap progresses, I am working toward stronger skills in:

- systematic web application testing
- vulnerability identification without lab hints
- authentication testing
- authorization testing
- API security
- business logic vulnerabilities
- advanced HTTP behavior
- vulnerability chaining
- secure coding
- threat modeling
- professional vulnerability reporting
- Linux
- Python security automation
- Application Security reasoning

These areas will be introduced progressively rather than treated as isolated skills.

---

# 🧩 Additional Practical Experience

Alongside this roadmap, I have completed a **12-week Red Team internship**, which provided exposure to areas including:

- reconnaissance and OSINT
- Nmap and service enumeration
- web reconnaissance
- OWASP Top 10
- Windows privilege escalation
- post-exploitation concepts
- Active Directory enumeration
- Kerberos security concepts
- BloodHound / SharpHound
- PowerView
- Hashcat
- Responder
- Metasploit / Meterpreter
- security reporting

This experience broadened my exposure to offensive security, while this repository remains focused primarily on developing deeper **Web Application Security and Application Security** skills.

---

# 🔐 Ethics & Scope

All practical security testing documented in this repository is performed only against:

- PortSwigger Web Security Academy
- intentionally vulnerable applications
- authorized training environments
- personal lab systems
- systems where explicit permission to test has been provided

The purpose of this repository is **education, ethical security testing, and professional skill development**.

---

# 🗺️ Long-Term Direction

The 120-day roadmap is one stage of a longer journey.

After developing stronger Web Application Security fundamentals, future areas of study may include:

- deeper API Security
- Secure Coding
- Threat Modeling
- Application Architecture
- Cloud Security
- AI / LLM Security
- advanced Application Security research

The priority remains:

> **Build strong fundamentals first. Expand later.**

---

# 📊 Roadmap Status

| Roadmap | Progress |
|---|---:|
| Total Days | 120 |
| Completed | 20 |
| Remaining | 100 |
| Current Position | Day 20 Completed |
| Next | Day 21 |

For detailed progress:

➡️ [`ROADMAP-PROGRESS.md`](ROADMAP-PROGRESS.md)

---

## Repository Status

🚧 **Active Learning Project**

This repository will continue to evolve as I progress through the remaining days of the roadmap.

---

> **Learn how the system works. Understand where trust fails. Validate the impact. Understand how to fix it.**

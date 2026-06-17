# Day 20 Linux — Network Interfaces and IP Address Discovery

## Objective

Learn how to identify network interfaces and IP addresses using Linux commands and understand why this information is important for networking, penetration testing, and cybersecurity.

---

# Concept Learned

## Network Interface

A network interface is a connection point that allows a device to communicate with a network.

Examples:

* Ethernet Interface
* Wireless Interface (Wi-Fi)
* Virtual Interfaces
* Loopback Interface

Think of a network interface as a door through which network traffic enters and leaves a system.

---

## IP Address

An IP address uniquely identifies a device on a network.

Example:

192.168.1.10

Every device connected to a network requires an IP address for communication.

---

# Command Learned

## ip a

Command:

```bash
ip a
```

---

# Command Breakdown

### ip

Linux networking utility.

Used to manage:

* Interfaces
* Routes
* Addresses

---

### a

Short form of:

```bash
address
```

Displays IP addresses assigned to interfaces.

---

# Why Security Professionals Use It

Before performing any network-related activity, a security professional needs to know:

* Current IP Address
* Available Interfaces
* Active Connections

This information helps identify:

* Network Location
* Reachable Systems
* Target Scope

---

# Example Output

```bash
2: eth0:
inet 192.168.1.15/24

3: wlan0:
inet 192.168.1.20/24
```

---

# Understanding The Output

## eth0

Ethernet network interface.

Usually represents wired network connections.

---

## wlan0

Wireless network interface.

Usually represents Wi-Fi connections.

---

## inet

Represents IPv4 address information.

Example:

```bash
inet 192.168.1.20/24
```

Means:

Current IP Address:

192.168.1.20

---

## /24

CIDR notation.

Represents subnet size.

Indicates:

```text
255.255.255.0
```

subnet mask.

---

# Cybersecurity Relevance

Pentesters commonly use:

```bash
ip a
```

to:

* Determine local IP addresses
* Identify active interfaces
* Understand network placement
* Prepare for reconnaissance activities

---

# Practical Exercise

Run:

```bash
ip a
```

Identify:

* Loopback Interface
* Ethernet Interface
* Wireless Interface
* IPv4 Address

Document your findings.

---

# Key Learning

* Every device communicates through network interfaces.
* IP addresses uniquely identify systems.
* Security professionals must understand network configuration before performing assessments.
* The ip command is one of the most important Linux networking tools.

---

# Status

✔ Completed Day 20 Linux

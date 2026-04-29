What is TCP/IP?
TCP/IP is a communication protocol that allows devices to send and receive data over networks.
TCP ensures reliable communication
UDP provides faster but less reliable communication
🔹 What are Ports?
Ports are logical endpoints used to identify specific services on a system.
Examples:
80 → HTTP
443 → HTTPS
22 → SSH
🔹 Why Ports Matter in Cybersecurity

- Attackers scan open ports to:
Identify running services
Find vulnerabilities
Exploit weak configurations
🔹 Commands Used
sudo apt update && sudo apt upgrade -y
update kali linux 
netstat
netstat -tuln
Nmap Basic Scan
nmap [scanme.nmap.org](http://scanme.nmap.org/)
Port Range Scan
nmap -p 1-1000 [scanme.nmap.org](http://scanme.nmap.org/)
Service Detection
nmap -sV [scanme.nmap.org](http://scanme.nmap.org/)

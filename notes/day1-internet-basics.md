🔹 1. What is an IP Address?

An IP (Internet Protocol) address is a unique numerical identifier assigned to every device connected to a network. It allows devices to communicate with each other over the internet.
Example:
When I pinged [google.com](http://google.com/), I received an IP address like:
142.250.187.78
This shows that websites are actually hosted on servers with specific IP addresses.

🔹 2. What is DNS?

DNS (Domain Name System) translates human-readable domain names into IP addresses.
For example:
[google.com](http://google.com/) → 142.250.187.78
Instead of remembering IP addresses, we use domain names, and DNS converts them into the correct server address.

🔹 3. What Happens When We Open a Website?

When I type a website (e.g., [google.com](http://google.com/)):

The browser sends a request to DNS
DNS returns the IP address of the server
The browser connects to that server
The server sends back website data
The browser displays the website

This process happens within milliseconds.

🔹 4. Commands Used
🔸 ping
ping [google.com](http://google.com/)
Purpose:
Checks connectivity between my system and the server
Shows response time and IP address
🔸 nslookup
nslookup [google.com](http://google.com/)
Purpose:
Finds the IP address of a domain
Shows DNS resolution
🔸 ipconfig
ipconfig
Purpose:
Displays my system’s network configuration
Shows my local IP address

🔹 5. Key Learning
Websites are hosted on servers with IP addresses
DNS translates domain names into IP addresses
Basic commands help understand network communication
This is the foundation of cybersecurity and penetration testing

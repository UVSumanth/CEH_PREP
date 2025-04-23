## 📡 1. What is Network Scanning?

**Network Scanning** is the **active process of probing a target network** to gather critical information, such as:

- **Live Hosts**
- **Open Ports**
- **Running Services**
- **Operating Systems**
- **Potential Vulnerabilities**

> 🔍 This phase follows footprinting and is essential for penetration testers to **enumerate systems and find attack vectors**.

---

## 🎯 2. Objectives of Network Scanning

| Objective                     | Purpose |
|------------------------------|---------|
| Discover Live Hosts          | Identify which IPs are active on the network |
| Port Discovery               | Check which TCP/UDP ports are open |
| Service Discovery            | Identify what services (e.g., HTTP, FTP) are running |
| OS Fingerprinting            | Determine the target's operating system |
| Vulnerability Identification | Look for exposed ports and services to exploit |

---

## 🛠️ 3. Network Scanning Tools

| Tool        | Description |
|-------------|-------------|
| **Nmap**    | Most widely used scanning tool; supports ping scans, port scanning, OS detection, service enumeration |
| **Metasploit** | Includes auxiliary scanners for services, vulnerabilities, and brute force |
| **SolarWinds Port Scanner** | GUI tool for discovering open ports and services |
| **NetScan Tools / Angry IP Scanner** | Additional tools for IP and port discovery |

---

## 🔍 4. Host Discovery

**Host Discovery** is the process of detecting active/live devices connected to a network.

### Common Host Discovery Methods:

| Technique | Description |
|-----------|-------------|
| **ICMP Echo Requests (Ping)** | Basic check to see if a host is reachable |
| **ARP Requests** | Used in LANs to find devices (Layer 2) |
| **TCP SYN Ping** | Sends SYN packets to known ports (e.g., 80) to detect active hosts |
| **UDP Ping** | Less reliable due to filtering, but used to detect services on open UDP ports |
| **hping3** | A powerful packet crafting tool for custom host discovery (TCP, UDP, ICMP) |

### ❗ CEH Key Points:
- ICMP might be **blocked by firewalls**, making it unreliable alone.
- **ARP scanning** only works within the same subnet/LAN.
- Combine methods for better coverage.

---

## 🚪 5. Port and Service Scanning

**Port Scanning** is used to identify which ports are open, closed, or filtered on a host.

| Port State  | Meaning |
|-------------|---------|
| **Open**    | A service is actively accepting connections |
| **Closed**  | No service is listening |
| **Filtered**| Packet is blocked by a firewall or filter |
| **Unfiltered** | Port is accessible, but the state cannot be determined |

### 🛎️ Common Ports & Services Table

| Port | Protocol | Service             |
|------|----------|---------------------|
| 20   | TCP      | FTP (Data)          |
| 21   | TCP      | FTP (Control)       |
| 22   | TCP      | SSH (Secure Shell)  |
| 23   | TCP      | Telnet              |
| 25   | TCP      | SMTP (Email Sending)|
| 53   | UDP/TCP  | DNS (Name Resolution)|
| 67   | UDP      | DHCP (Server)       |
| 68   | UDP      | DHCP (Client)       |
| 69   | UDP      | TFTP (Trivial FTP)  |
| 80   | TCP      | HTTP (Web Traffic)  |
| 110  | TCP      | POP3 (Email Receive)|
| 123  | UDP      | NTP (Time Protocol) |
| 135  | TCP      | Microsoft RPC       |
| 137–139 | TCP/UDP | NetBIOS (Windows SMB) |
| 143  | TCP      | IMAP                |
| 161  | UDP      | SNMP (Monitoring)   |
| 443  | TCP      | HTTPS (Secure Web)  |
| 445  | TCP      | SMB (Windows Shares)|
| 3306 | TCP      | MySQL               |
| 3389 | TCP      | RDP (Remote Desktop)|

---

## 💡 CEH Notes: Scanning Types to Know

| Scan Type         | Description |
|-------------------|-------------|
| **TCP Connect Scan** | Uses full 3-way handshake (detectable) |
| **TCP SYN Scan (Stealth)** | Sends SYN, analyzes response (more discreet) |
| **UDP Scan** | Slower and less reliable, but useful for identifying services like DNS, SNMP |
| **XMAS Scan** | Sends TCP flags (FIN, URG, PSH) to identify behavior of closed ports |
| **NULL Scan** | Sends packets with no flags set |
| **FIN Scan** | Sends only FIN flag — useful for evading filters |
| **Idle Scan** | Spoofs IP of another host to detect open ports without direct interaction |

---

## 🧠 Summary Table

| Topic                | Key Takeaways |
|----------------------|----------------|
| Network Scanning     | Actively probing the target to map systems, services, and vulnerabilities |
| Host Discovery       | Detecting live devices using ping, ARP, hping3, etc. |
| Port Scanning        | Enumerating open/closed/filtered ports on discovered hosts |
| Service Identification | Determining which service is running on each port |
| Tools                | Nmap, hping3, Metasploit, SolarWinds, Angry IP Scanner |
| CEH Tip              | Know common ports, scanning types, and stealthy techniques |

---

## 📚 Recommended Resources

- [Nmap Official Guide](https://nmap.org/book/man.html)
- [hping3 Documentation](https://linux.die.net/man/8/hping3)
- [Metasploit Unleashed](https://www.offensive-security.com/metasploit-unleashed/)
- [TCP/IP Illustrated Book by W. Richard Stevens](https://www.amazon.com/TCP-Illustrated-Vol-1/dp/0201633469)

---

✅ **Pro Tip for CEH**:  
Understand **why** and **how** scanning is done — not just what tools are used. Also, learn to recognize **stealth vs aggressive scans** and how **firewalls and IDS/IPS** detect them.


## 🔍 Purpose of Network Scanning Tools

Network scanning tools help identify:
- Live hosts on the network
- Open TCP/UDP ports
- Running services and their versions
- NetBIOS and location information
- Vulnerabilities and misconfigurations

---

## 🛠️ Tool Comparison Table

| Tool              | Functionality                                                                                   | Best Use Case / Scenario                                         |
|-------------------|--------------------------------------------------------------------------------------------------|------------------------------------------------------------------|
| **Nmap**          | Port scanning, OS detection, service version detection, network discovery                        | General-purpose scanner for mapping and reconnaissance           |
| **Hping3**        | Custom packet crafting (TCP/UDP/ICMP), firewall testing, traceroute, OS fingerprinting           | Advanced packet analysis, custom scanning, SYN flooding, ISN     |
| **Metasploit**    | Exploit development, payload delivery, penetration testing                                       | Post-reconnaissance exploitation phase                           |
| **NetScanTools Pro** | Information gathering (IPv4/IPv6, hostnames, domain names, email, ports)                        | Manual and automated network footprinting and info gathering     |

---

## 🔧 Hping3 Command Examples and Use Cases

### ✅ ICMP Ping Scan
- **Purpose:** Check if a host is online.
- **Command:** `hping3 -1 <Target IP>`
- **Notes:** Sends ICMP Echo Request.

---

### 🔥 ACK Scan
- **Purpose:** Firewall detection and rule analysis.
- **Command:** `hping3 -A -p 80 <Target IP>`
- **How it works:** 
  - RST response → Port is unfiltered.
  - No response → Port is filtered or dropped.

---

### 📤 UDP Scan
- **Purpose:** Check UDP port status.
- **Command:** `hping3 -2 <Target IP> -p 80`
- **How it works:** 
  - No reply → Port open/filtered.
  - ICMP Port Unreachable → Port closed.

---

### 📡 SYN Scan
- **Purpose:** Stealthy port scan (half-open TCP).
- **Command:** `hping3 -8 50-60 -S <Target IP> -V`
- **Alternate:** `hping3 -S <Target IP> -p 80`
- **Behavior:**
  - SYN-ACK → Port open
  - RST → Port closed

---

### 🚩 FIN, PUSH, URG Scan
- **Purpose:** Firewall/IDS evasion scan.
- **Command:** `hping3 -F -P -U <Target IP> -p 80`
- **Behavior:**
  - No reply → Port open
  - RST → Port closed

---

### 🌊 SYN Flood Attack
- **Purpose:** Perform DoS using TCP SYN flooding.
- **Command:** `hping3 -S <victim> -a <spoofed IP> -p 22 --flood`
- **Notes:**
  - Overwhelms target with half-open TCP connections.

---

### 🔍 Collect Initial Sequence Number (ISN)
- **Purpose:** TCP Session Hijacking / Reconnaissance
- **Command:** `hping3 <Target IP> -Q -p 139`
- **Note:** Collects ISN for session hijacking.

---

### 🌐 Scan Entire Subnet for Live Hosts
- **Command:** `hping3 -1 10.0.1.x --rand-dest -I eth0`
- **Notes:** Sends ICMP echo requests with random destination IPs to detect live hosts.

---

### 📡 Intercept HTTP Traffic
- **Command:** `hping3 -9 http -I eth0`
- **Purpose:** Listen mode to capture HTTP signatures on interface.

---

## 📱 Mobile Scanning Tools

| Tool              | Platform       | Use Case / Info Provided                                                                 |
|-------------------|----------------|-------------------------------------------------------------------------------------------|
| **IP Scanner**     | iOS            | Scans for active hosts on local network                                                  |
| **Fing**           | Android/iOS    | IP, MAC, device vendor, ISP info, pings, traceroute via ports like SSH, FTP              |
| **Network Scanner**| Android        | Identifies active hosts, MACs, vendor, port scanning                                     |

---

## 🧠 CEH Exam Focus Tips

- **Nmap** is a core tool for scanning and must be fully understood (flags, outputs, stealth scans).
- **Hping3** is crucial for SYN, FIN, ACK scans and **custom packet crafting**, especially in **SYN Flood attacks**.
- **Understand when and why to use each scan type**, especially in stealthy or firewall-bypassing scenarios.
- **Mobile tools** may be asked in relation to BYOD environments and rogue device detection.

---

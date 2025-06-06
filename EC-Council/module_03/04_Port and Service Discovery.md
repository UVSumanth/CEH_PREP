## 📌 Overview
Port scanning is an essential part of network reconnaissance that identifies open communication ports and associated services. Attackers use these scans to identify vulnerabilities, while defenders use them to audit and secure systems.

---

## 🚪 TCP Scans

### 🔄 TCP Connect / Full-Open Scan
- **Command:** `nmap -sT`
- **How it works:** Full TCP handshake (SYN → SYN-ACK → ACK)
- **Use Case:** Easy, does not need root; but noisy.
- **Detection:** Logs are created on the target.

### 🕵️ SYN Scan (Half-Open)
- **Command:** `nmap -sS`
- **How it works:** Sends SYN, receives SYN-ACK, sends RST
- **Use Case:** Stealthy, fast, widely used.
- **Detection:** Low visibility, bypasses basic IDS.

### ❌ Inverse TCP Flag Scans (FIN, NULL, Xmas)
- **Commands:** `-sF`, `-sN`, `-sX`
- **Behavior:** Open → No reply, Closed → RST
- **Use Case:** Bypass firewalls, works on UNIX/BSD
- **Note:** Ineffective on Windows systems.

### 🎄 Xmas Scan
- **Command:** `nmap -sX`
- **Flags Used:** FIN + URG + PSH
- **Detection:** Low; works on RFC 793-compliant systems only.

### 📘 TCP Maimon Scan
- **Command:** `nmap -sM`
- **Flags:** FIN + ACK
- **Behavior:** Open/Filtered → No response | Closed → RST

---

## 🔄 ACK Flag Probes
### 🔍 ACK Scan
- **Command:** `nmap -sA`
- **Behavior:** Filters detection (open/closed = RST | filtered = no response)

### 🪟 Window Scan
- **Command:** `nmap -sW`
- **Behavior:** Checks TCP window size in response to ACK

---

## 📤 UDP Scan
- **Command:** `nmap -sU`
- **Behavior:** Open → No reply | Closed → ICMP Port Unreachable
- **Challenges:** Slower, unreliable; used for detecting SNMP, DNS, etc.

---

## 📶 SCTP-Based Scans

### 🆕 SCTP INIT Scan
- **Command:** `nmap -sY`
- **Behavior:** Open → INIT-ACK | Closed → ABORT | Filtered → No response

### 🍪 SCTP COOKIE ECHO Scan
- **Command:** `nmap -sZ`
- **Behavior:** Closed → ABORT | Open/Filtered → No response

---

## 📡 SSDP Scan (UPnP Devices)
- **How it works:** Sends M-SEARCH over multicast
- **Purpose:** Detect smart devices (IoT)
- **Tools:** `UPnP SSDP M-SEARCH`, `Nmap scripts`

---

## 📃 List Scan
- **Command:** `nmap -sL`
- **Purpose:** Resolve IPs/hostnames without scanning
- **Detection:** Zero packets sent, stealthiest

---

## 🌐 IPv6 Scan
- **Command:** `nmap -6`
- **Purpose:** Discover and scan IPv6-enabled targets
- **Challenges:** Must collect valid IPv6 addresses manually

---

## 🔎 Service Version Detection
- **Command:** `nmap -sV`
- **Behavior:** Probes services to find name and version
- **Use Case:** Vulnerability assessment, exploit matching

---

## ⚡ Nmap Scan Time Optimization Techniques

| Technique                      | Description                                                       |
|-------------------------------|-------------------------------------------------------------------|
| Avoid Deep Scans              | Skip `-A`, `-O`, `-sV`, `-sC` unless needed                       |
| Optimize Timing               | Use `-T4` (aggressive) or `-T5` (insane) for faster scans         |
| Skip DNS Resolution           | Use `-n`                                                          |
| Skip Host Discovery           | Use `-Pn`                                                         |
| Separate UDP/TCP              | Run `-sU` separately due to ICMP rate limits                      |
| Use Latest Version            | Bug fixes, improved scan logic                                   |
| Run Internally                | Scanning from inside network improves speed and reliability       |
| Parallel Scanning             | Use multiple terminals or tools to scan ranges in parallel       |

---

## 🧠 CEH Pro Tips
- Understand stealth vs. noisy scans (SYN vs. TCP Connect)
- Know which scans bypass IDS/firewall (Xmas, NULL, FIN, ACK)
- Memorize command-line flags for each scan type (Nmap is a CEH favorite!)
- Use `-sV` after `-sS` to find vulnerable services

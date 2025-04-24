## 🧟‍♂️ 1. IDLE/IPID Scan (Zombie Scan)

### Description:
- Also known as **Zombie Scan**
- Utilizes a third-party **idle device** on the network (Zombie)
- Exploits predictable **IPID values** (IP Identification field in IP header)
- Can **scan targets without revealing the real IP address** of the attacker

### How It Works:

1. **Attacker sends SYN-ACK** to Zombie → Zombie replies with **RST**
2. Attacker records **IPID value** of the Zombie
3. Attacker sends a **SYN packet to the Target** with **Zombie’s IP as source (spoofed)**
4. Target responds to Zombie:
   - If port is **open**, the Zombie receives a response and its **IPID increases**
   - If port is **closed**, no increment occurs
5. Attacker sends another SYN-ACK to Zombie to check the new IPID

### Key Insights:
- **Silent & Stealthy**: Target sees only Zombie's IP
- **Zombie must have predictable IPID behavior** (not randomized)
- Requires **idle, quiet hosts**
- Useful for **stealth scanning behind firewalls or for anonymous enumeration**

### 🔧 Command Example:
```bash
nmap -Pn -p <port> -sI <ZombieIP> <TargetIP> --packet-trace
```

### CEH Exam Notes:
- Requires **careful Zombie selection**
- Powerful for avoiding detection and logging

---

## 🌐 2. UDP Scan (`nmap -sU`)

### Description:
- Used to scan **UDP ports**
- Unlike TCP, **UDP is connectionless** and does not use a handshake
- **Silent** when a port is open; **ICMP port unreachable** is sent if the port is closed

### How It Works:

- Send a UDP packet to target port
  - **Open port**: Usually no response
  - **Closed port**: ICMP Port Unreachable (Type 3, Code 3)
  - **Filtered**: No response or ICMP unreachable Type 3, Code 1/2/9/10/13

### Key Insights:
- **Slow and Unreliable**, but necessary to find exposed UDP services
- Requires **admin/root privileges**
- Commonly scanned UDP services:
  - DNS (53)
  - SNMP (161)
  - TFTP (69)
  - NetBIOS (137-138)
  - NTP (123)

### CEH Exam Notes:
- Open port gives **no response** (could be confusing)
- Use `-sU` flag with optional `-sS` (TCP SYN) for **hybrid scans**
- Know ICMP **Type 3 codes** for scan result interpretation

---

## 🔁 3. SCTP INIT Scan (`nmap -sY`) and COOKIE ECHO Scan (`nmap -sZ`)

### What is SCTP?
- **SCTP = Stream Control Transmission Protocol**
- Similar to TCP but with **4-way handshake**
- Supports **multi-streaming and multi-homing**
- Used in **telecom** and **VoIP**

---

### 📩 SCTP INIT Scan (`nmap -sY`)

**INIT Scan** sends an SCTP **INIT chunk** to a target port.

- **If port is open**: Target responds with **INIT-ACK**
- **If port is closed**: Target responds with **ABORT**

### 📌 Behavior:
- Used to detect **open SCTP services**
- Requires **root/admin privileges**
- Rarely monitored = **stealthy**

---

### 🍪 COOKIE ECHO Scan (`nmap -sZ`)

Mimics the **COOKIE ECHO phase** of SCTP handshake:

1. Host1 sends **INIT**
2. Host2 replies **INIT-ACK**
3. Host1 sends **COOKIE ECHO**
4. Host2 replies **COOKIE ACK**

- This scan sends **COOKIE ECHO** chunk.
- **If port is open**: Target responds with **COOKIE ACK**
- **If port is closed**: Target replies with **ABORT**

### CEH Exam Notes:
- Both scans require **elevated/root privileges**
- Useful for **VoIP and telecom audits**
- Rare, but important to understand SCTP behavior and response types
- SCTP is rarely used in web infrastructure, but **included in CEH v12 objectives**

---

## 📚 Final CEH Tips Summary

| Scan Type        | Description | Detection | Requires Root? | Usage |
|------------------|-------------|-----------|----------------|-------|
| **IDLE Scan**    | Uses a third-party Zombie's IPID to infer open ports | Very stealthy | Yes | Anonymous port scan |
| **UDP Scan**     | Sends UDP packets to detect open services | Stealthy but noisy on closed ports | Yes | Used for DNS, SNMP |
| **SCTP INIT**    | Sends INIT chunk; open port replies with INIT-ACK | Stealthy | Yes | Telecom/VoIP systems |
| **SCTP COOKIE**  | Sends COOKIE-ECHO; response is COOKIE-ACK if open | Stealthy | Yes | Confirm SCTP handshakes |

---

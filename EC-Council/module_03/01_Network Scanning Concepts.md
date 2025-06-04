## 🔍 Overview of Network Scanning

Network scanning is an **active reconnaissance technique** used by attackers and security professionals to gather information about systems within a network. It helps identify:

- Live hosts
- Open ports and services
- Running OS and system architecture
- Potential vulnerabilities and misconfigurations

**🎯 CEH Perspective:** This step helps an ethical hacker prepare a **targeted attack strategy** and simulate real-world attack scenarios legally and ethically.

---

## 📊 Types of Scanning

| Type                 | Description                                                                                         |
|----------------------|-----------------------------------------------------------------------------------------------------|
| **Port Scanning**     | Identifies open ports on a system. Helps in discovering active services (TCP/UDP) and vulnerabilities. |
| **Network Scanning**  | Discovers active hosts on the network, IPs, and hostnames.                                           |
| **Vulnerability Scanning** | Detects known vulnerabilities using databases and plugins. Helps find flaws like outdated software, default credentials, directory traversal, etc. |

---

## 🎯 Objectives of Network Scanning

- Discover **live systems** and **open ports**
- Identify **OS** and version (for vulnerability targeting)
- Find **running services and applications**
- Identify **application versions** for known exploits
- Detect **vulnerabilities** to determine potential attack paths

**🧠 Why it matters in CEH?**
CEH often tests which scan (port/host/vulnerability) to use in a scenario. Know each type’s goal and toolset.

---

## 🔁 TCP/IP Communication Essentials

### 📡 TCP Communication Flags

TCP is a **connection-oriented protocol** using flags to control communication between devices.

| Flag | Name          | Purpose                                                            |
|------|---------------|---------------------------------------------------------------------|
| SYN  | Synchronize   | Initiates a connection                                              |
| ACK  | Acknowledge   | Confirms receipt of data or SYN                                     |
| FIN  | Finish        | Gracefully ends a session                                           |
| RST  | Reset         | Abruptly terminates a connection due to an error                   |
| PSH  | Push          | Sends the data immediately to the application layer                |
| URG  | Urgent        | Marks part of the data as urgent and bypasses queue                |

> ✅ **CEH Tip:** Focus on how flags relate to different scan types (SYN, NULL, FIN scans etc.)

---

### 🔗 TCP Three-Way Handshake

1. **SYN** → Sent by client to start connection
2. **SYN-ACK** → Sent by server to acknowledge and respond
3. **ACK** → Final confirmation by client; connection established

This sequence ensures both parties are ready for data transmission.

### 🔚 TCP Termination

- Sender sends **FIN** → Receiver sends **ACK** and own **FIN**
- Sender acknowledges → Connection gracefully closed

OR

- Sender sends **RST** for abrupt termination

---

## 🔒 CEH Alert: Why Scan?

Understanding scanning is key to:

- Ethical exploitation
- Risk assessments
- Penetration testing reports

> 🔥 CEH Scenario: *You're given a target IP. What type of scan would you run to identify open ports without being detected?* → **Answer: TCP SYN or Stealth scan**

---

## ✅ Summary Cheat Sheet

- **Scanning = Active Reconnaissance**
- **3 Types**: Port, Network, Vulnerability
- **TCP Flags** = SYN, ACK, FIN, RST, PSH, URG
- **TCP Comm** = 3-Way Handshake → Communication → FIN or RST
- Use scanning to map targets, identify weaknesses, and plan exploitation phases

---

> 📘 Next Up: Port Scanning Techniques (Module 3.2) — will cover TCP scans (SYN, NULL, XMAS), UDP scans, and Nmap use cases.

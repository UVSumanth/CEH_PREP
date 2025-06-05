## 🔍 Host Discovery Overview
Host discovery is the initial step in scanning to identify which hosts are alive and active on a network. It helps attackers build a target list before launching port scans or vulnerability assessments.

---

## 🛠️ Scanning Techniques

### 1. ARP Ping Scan
- **Purpose:** Identify live devices on a local IPv4 network.
- **How:** Sends ARP requests; devices reply with MAC addresses.
- **Tool/Option:** Nmap `-PR`, `-sn` to disable port scan.
- **Bypasses firewalls** since it works at Layer 2.

---

### 2. UDP Ping Scan
- **Purpose:** Check if host is online without using TCP/ICMP.
- **How:** Sends UDP packets to default or custom ports.
- **Tool/Option:** Nmap `-PU`, Zenmap.
- **Benefit:** Works when TCP and ICMP are filtered.

---

### 3. ICMP Echo Ping Scan
- **Purpose:** Traditional ping method using Echo Request/Reply.
- **Tool/Option:** Nmap `-PE`
- **Limitation:** Often blocked by firewalls or disabled in Windows for broadcasts.

---

### 4. ICMP Echo Ping Sweep
- **Purpose:** Sweep entire subnet for live hosts.
- **Tool:** `fping`, `nmap -PE` with range.
- **Limitation:** Slow, often blocked, no broadcast support on Windows.

---

### 5. ICMP Timestamp Ping Scan
- **Purpose:** Request system time to detect host presence.
- **Tool/Option:** Nmap `-PP`
- **Use Case:** Useful if Echo is blocked; helps detect OS behavior.

---

### 6. ICMP Address Mask Ping Scan
- **Purpose:** Requests subnet mask to confirm host status.
- **Tool/Option:** Nmap `-PM`
- **Note:** Rarely used today; many systems ignore it.

---

### 7. TCP SYN Ping Scan
- **Purpose:** Send SYN to port, detect SYN-ACK.
- **Tool/Option:** Nmap `-PS<port>`
- **Stealthy:** Doesn't complete 3-way handshake (no logs).

---

### 8. TCP ACK Ping Scan
- **Purpose:** Sends ACK, awaits RST.
- **Tool/Option:** Nmap `-PA<port>`
- **Use Case:** Bypasses firewalls that block SYN.

---

## 🧠 Summary of Host Discovery Techniques

| **Technique**              | **Nmap Command**            | **Packet Sent**                     | **Expected Response (Live Host)**                         | **Best Used When...**                                                                 |
|---------------------------|-----------------------------|-------------------------------------|-----------------------------------------------------------|---------------------------------------------------------------------------------------|
| ARP Ping Scan             | `nmap -sn -PR`              | ARP Request                         | ARP Reply with MAC Address                                | Scanning on Local Network (Layer 2)                                                  |
| UDP Ping Scan             | `nmap -sn -PU`              | UDP Packet (port 40,125 by default) | UDP Response or Error Message                             | ICMP/TCP blocked; only UDP allowed                                                   |
| ICMP Echo Ping Scan       | `nmap -sn -PE`              | ICMP Echo Request                   | ICMP Echo Reply                                            | Basic ping; fast host detection                                                      |
| ICMP Echo Ping Sweep      | `nmap -sn -PE <IP Range>`   | ICMP Echo Requests to IP range      | ICMP Echo Reply                                            | Mapping all hosts in a subnet                                                        |
| ICMP Timestamp Ping Scan  | `nmap -sn -PP`              | ICMP Timestamp Request              | Timestamp Reply                                            | ICMP Echo blocked; OS/Time info needed                                               |
| ICMP Address Mask Scan    | `nmap -sn -PM`              | ICMP Address Mask Request           | Address Mask Reply                                         | Identify subnet configuration; legacy support                                        |
| TCP SYN Ping Scan         | `nmap -sn -PS<port>`        | TCP SYN                             | SYN-ACK Response                                           | ICMP blocked; stealthy discovery via TCP port (e.g. 80)                              |
| TCP ACK Ping Scan         | `nmap -sn -PA<port>`        | TCP ACK                             | RST Response                                               | SYN filtered by firewall; ACK allowed                                                |
| IP Protocol Ping Scan     | `nmap -sn -PO`              | Protocol Packets (ICMP, TCP, UDP)   | Any Protocol-Based Reply                                   | Trying all options to find live host                                                 |

---

## 🧰 Tools for Ping Sweep

| Tool                     | Platform          | Description                                                                 |
|--------------------------|-------------------|-----------------------------------------------------------------------------|
| Angry IP Scanner         | Cross-platform    | Pings IPs, resolves hostnames, shows MAC, scans ports                      |
| SolarWinds Engineer’s TS | Windows           | Enterprise-grade network discovery suite                                   |
| NetScanTools Pro         | Windows           | Advanced scanning & diagnostics                                            |
| Colasoft Ping Tool       | Windows           | Visual ICMP scanning                                                       |
| Visual Ping Tester       | Windows           | Simple tool for ping testing                                               |
| OpUtils                  | Web/Enterprise    | ManageEngine’s IP/MAC/network scanner                                      |

---

> ✅ **CEH Tip:** Firewalls often block ICMP Echo but allow other packet types like ACK or UDP. Use alternative ping scans (e.g., ARP, ACK) in stealth environments.

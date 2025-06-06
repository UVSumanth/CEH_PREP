## 🎯 What is OS Discovery & Banner Grabbing?

**Purpose:** Identify the OS and service versions running on a target system to assess vulnerabilities.

### 🔍 Techniques:

#### 🔸 Active OS Discovery
- Sends crafted packets (TCP/UDP/ICMP) and analyzes response.
- Uses: TTL, TCP window size, TCP flags, ICMP replies.
- **Tool:** `nmap -O` (OS detection)

#### 🔸 Passive OS Discovery
- Listens to traffic without sending packets (sniffing).
- Fields: TTL, Window Size, DF bit, TOS
- **Tool:** Wireshark

#### 🔸 Banner Grabbing
- Connects to services (FTP, HTTP) and reads service banners.
- **Tools:** Netcat, Telnet, Nmap (`--script=banner`), Curl

### ✅ Real-World Uses

| Role     | Purpose                                                                 |
|----------|-------------------------------------------------------------------------|
| Defender | Asset inventory, patch mgmt, compliance                                 |
| Attacker | Find OS-specific exploits, stealth recon using passive analysis         |

---

## 🧩 How to Identify OS via TTL & TCP Window Size

| OS                | TTL | TCP Window Size |
|-------------------|-----|-----------------|
| Linux             | 64  | 5840            |
| Windows           | 128 | 65535           |
| Cisco Router      | 255 | 4128            |
| Solaris/FreeBSD   | 255 | Varies          |

**Tools:** Wireshark (sniffing), Nmap, Unicornscan  
- Match observed TTL/window values with known signatures.

---

## 🧰 OS Discovery using Nmap & Unicornscan

### 🔹 Nmap
- Command: `nmap -O <target IP>`
- Analyzes: TTL, TCP options, Window size, ICMP responses

### 🔹 Unicornscan
- Command: `unicornscan <target IP>`
- Uses TTL in response (128 = Windows, 64 = Linux)

---

## 🔄 Nmap Script Engine for OS Discovery

### 🔸 What It Does:
- Uses built-in/custom scripts to gather OS info, e.g., through SMB

### 🔸 Examples:
- Default: `nmap -sC <target>`
- Custom: `nmap --script smb-os-discovery <target>`

**Tool:** Nmap Scripting Engine (NSE)

---

## 🌐 OS Discovery using IPv6 Fingerprinting

### 🔸 What It Does:
- Identifies OS using 18+ IPv6-based probes

### 🔸 How It Works:
- Probes: S1-S6 (TCP sequence), IE1, IE2 (ICMPv6 echo), U1 (UDP), T2-T7 (TCP)
- Command: `nmap -6 -O <target>`

### ✅ Notes:
- Effective in dual-stack or IPv6-only networks
- Less likely to be detected due to limited IPv6 monitoring

---

## 📌 Summary of Tools

| Tool        | Use Case                      |
|-------------|-------------------------------|
| **Nmap**    | Active OS scan, banner grab   |
| **Wireshark** | Passive fingerprinting      |
| **Netcat**  | Banner grabbing               |
| **Telnet**  | Manual banner retrieval       |
| **Unicornscan** | TTL-based OS fingerprinting |
| **NSE**     | Scripted OS detection via SMB |

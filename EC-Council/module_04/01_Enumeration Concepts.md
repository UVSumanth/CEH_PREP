## 🔍 What It Does
Enumeration is the process of **actively connecting to a system** and extracting **detailed information** such as:
- Usernames
- Network shares
- Services and ports
- DNS records
- SNMP data
- Routing tables

---

## ⚙️ How It Works
- Requires an **active connection** with the target.
- Utilizes **protocol-based queries** to extract system information.
- Common protocols and methods:
  - SMB
  - SNMP
  - LDAP
  - DNS
  - NetBIOS
- Enumeration is typically performed **after scanning**, when open ports and services are identified.

---

## 🧭 Why It’s Used

### 🛡️ Real-World Defender Use
- Audit and assess system/network configurations.
- Gather asset inventory (hostnames, users, shares).
- Perform **vulnerability management**.
- Identify weak/default credentials or open shares.
- Check for **misconfigured services**.

### 🎯 Attacker Use
- Discover **valid usernames and accounts**.
- Identify **misconfigurations** and **exposed services**.
- Target **admin shares** (e.g., `IPC$`, `ADMIN$`) for lateral movement.
- Perform **DNS zone transfers** (if misconfigured).
- Exploit **SNMP, NetBIOS, LDAP**, etc.
- Launch **brute-force or password guessing attacks**.

---

## 🧪 Common Enumeration Techniques

| Technique                          | Description                                                                 |
| ---------------------------------- | --------------------------------------------------------------------------- |
| Email harvesting                   | Extract usernames via emails (e.g., user@domain.com)                        |
| Null session exploitation          | Anonymous login to SMB for gathering data (e.g., shares, users)             |
| Default credentials usage          | Attempt factory-set credentials (admin/admin, guest/guest)                  |
| LDAP enumeration                   | Use `ldapsearch` to query directory users and structure                     |
| DNS Zone Transfer                  | Attempt `dig AXFR @dnsserver domain.com` to get full domain info            |
| SNMP Walk                          | Use `snmpwalk` for querying system info using public community strings      |
| Brute-force & error-based AD enum  | Exploit login error messages for valid username discovery                   |

---

## 🔌 Key Ports & Services for Enumeration

| Service / Protocol         | Port(s)         | Use Case / Risk                                      |
| -------------------------- | --------------- | ---------------------------------------------------- |
| **DNS (Zone Transfer)**    | TCP/UDP 53      | Can leak entire domain structure                     |
| **RPC Endpoint Mapper**    | TCP/UDP 135     | Identifies services for remote procedure calls       |
| **NetBIOS Name Service**   | UDP 137         | Used for network name resolution                     |
| **SMB over NetBIOS**       | TCP 139         | Allows file sharing, can enable null session attacks |
| **SMB Direct (Windows)**   | TCP/UDP 445     | File/printer sharing and user enumeration            |
| **SNMP**                   | UDP 161/162     | Device status, config info, community string leaks   |
| **LDAP**                   | TCP/UDP 389     | Directory structure and user enumeration             |
| **NFS**                    | TCP 2049        | Allows remote file system mounts                     |
| **SMTP**                   | TCP 25          | Can reveal usernames (via VRFY/EXPN commands)        |
| **SSH**                    | TCP 22          | Remote shell; vulnerable to brute-force              |
| **Telnet**                 | TCP 23          | Insecure remote access, also brute-forceable         |
| **TFTP**                   | UDP 69          | Often lacks auth; used in firmware and config upload |
| **BGP**                    | TCP 179         | Routing info disclosure if unprotected               |
| **SIP (VoIP)**             | 5060/5061       | Can expose voice servers and call flows              |
| **FTP**                    | TCP 20/21       | File uploads/downloads; also bruteforce target       |
| **Global Catalog (LDAP)**  | TCP/UDP 3268    | For multi-domain directory information               |

---

## 🔧 Common Tools for Enumeration

| Tool            | Use Case                                |
| --------------- | ---------------------------------------- |
| **Nmap**        | Port/service detection, scripts for enum |
| **Netcat**      | Banner grabbing, basic service queries   |
| **Enum4linux**  | SMB/NetBIOS enumeration on Windows       |
| **SNMPWalk**    | SNMP info extraction                     |
| **ldapsearch**  | LDAP querying                            |
| **Nslookup**    | DNS queries and zone transfer attempts   |
| **Net view**    | View shared resources on Windows         |
| **nbtstat**     | NetBIOS information                      |

---

## 🧠 CEH Tips
- Remember: Enumeration is **active**. Scanning is passive/probing.
- Target **ports 135, 139, 445, 389, 161** often yield the most useful results.
- DNS misconfigurations (Zone Transfers) are a **goldmine** for attackers.
- Null sessions are often tested with: `net use \\IP\IPC$ "" /u:""`

---

## ✅ Summary

- Enumeration bridges the gap between scanning and exploitation.
- Misconfigurations, weak credentials, and exposed services = attack surface.
- Learn and memorize **services/ports**, **tools**, and **protocol-based tactics**.


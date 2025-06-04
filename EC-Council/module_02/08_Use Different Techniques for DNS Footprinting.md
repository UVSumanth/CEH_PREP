## 📌 Overview

DNS (Domain Name System) footprinting involves gathering information from DNS servers to map out the network infrastructure of the target organization. By analyzing DNS records, attackers can identify server roles, internal domains, and exploit misconfigurations.

---

## 📥 Extracting DNS Information

- DNS records offer valuable details about server types, roles, and locations.
- Attackers query DNS servers to obtain DNS zone data and enumerate services.
- Data from DNS can be used for **network mapping**, **social engineering**, and **attack planning**.

---

## 📂 Common DNS Record Types

| Record Type | Description                                                                 |
|-------------|-----------------------------------------------------------------------------|
| **A**       | Maps a hostname to an IPv4 address (Address record)                         |
| **AAAA**    | Maps a hostname to an IPv6 address                                           |
| **MX**      | Identifies mail servers for a domain                                         |
| **NS**      | Specifies authoritative name servers                                         |
| **CNAME**   | Canonical name record (alias of one domain to another)                      |
| **SOA**     | Start of Authority record; contains admin details and zone info             |
| **SRV**     | Specifies location of services (host and port)                              |
| **PTR**     | Pointer record; used for reverse DNS lookup                                 |
| **RP**      | Responsible Person record; contains contact info                            |
| **HINFO**   | Host info including CPU type and OS                                          |
| **TXT**     | Unstructured text; often used for SPF, DKIM, and domain verification        |

---

## 🛠️ DNS Interrogation Tools (CEH Perspective)

| Tool             | Use Case                                                                 |
|------------------|--------------------------------------------------------------------------|
| **SecurityTrails** | Queries domains to extract DNS records, subdomains, and historical data |
| **DNSdumpster.com** | Passive DNS mapping, subdomain enumeration, and DNS recon               |
| **ViewDNS.info** | Centralized DNS lookup for multiple record types                         |
| **MXToolbox**     | Domain health, DNS, and mail server records                             |

These tools can help ethical hackers and pentesters gather DNS data **without direct interaction**, making them valuable for **passive reconnaissance**.

---

## 🔁 Reverse DNS Lookup

Reverse DNS lookup is the process of resolving an **IP address back to a domain name** using PTR (pointer) records.

### 🎯 Why It Matters
- Helps attackers **map IP ranges** to active domains
- Assists in building **network inventory**
- Can be used for **fingerprinting internal resources**

### 🔍 Reverse DNS Tools (CEH Tools)

| Tool            | Description                                                                 |
|------------------|------------------------------------------------------------------------------|
| **DNSRecon**      | Python-based tool for DNS enumeration, brute force, and reverse lookups     |
| **Reverse IP Lookup (ViewDNS/YouGetSignal)** | Maps an IP to all domains hosted on that IP        |
| **Dig (Linux CLI)** | Used with `-x` option to perform reverse lookups on IPs                   |
| **Fierce**         | Performs DNS reconnaissance, zone transfer attempts, and PTR scanning      |

---

## ✅ CEH Exam Tips

- Be able to differentiate **A, MX, NS, PTR, SOA, TXT** records.
- Understand the role of **reverse lookups** and what **PTR** records reveal.
- Memorize common **DNS interrogation tools** and how they are used for OSINT.
- Know the **passive vs active DNS footprinting** distinctions.
- Be aware of how misconfigured DNS (e.g., zone transfers) can be exploited.

---

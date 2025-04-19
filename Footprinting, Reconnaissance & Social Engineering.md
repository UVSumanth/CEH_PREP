## 📍 1. Footprinting & Reconnaissance

Footprinting is the **first phase of ethical hacking**, where the attacker (or security analyst) gathers as much information as possible about a target system to find ways to exploit vulnerabilities.

### 🔍 Common Information Gathered:

- Domain names, IP addresses
- DNS records
- Contact information (via WHOIS)
- Technology stack
- Employee details
- Metadata

---

## 🌐 2. WHOIS Lookup

**WHOIS** is a protocol used to query databases for domain ownership and registration information.

### Key Points:
- Reveals domain registration details, expiration, and contact info.
- May include registrar name, DNS servers, admin contacts.
- Useful to map **target organization structure** or to initiate **social engineering attacks**.

### Useful WHOIS Tools:
- [who.is](https://who.is)
- `whois` Linux command

---

## 🧭 3. DNS Enumeration

DNS (Domain Name System) provides information about **domain names, mail servers, subdomains, and IP addresses**.

### Useful Tools & Commands:
- `nslookup` – DNS lookup tool
- `dig` – Linux tool for querying DNS
- Online tools like MXToolbox

### 🔄 Zone Transfer

**Zone Transfer** is a mechanism for replicating DNS data between DNS servers. 

- When misconfigured, attackers can use it to extract:
  - All DNS records of a domain
  - Subdomains
  - IP addresses and hostnames

> **Command**: `dig axfr @ns1.example.com example.com`

---

## 👤 4. Social Engineering Techniques

Social engineering involves **manipulating human behavior** to gain unauthorized access or information.

### 🧰 Techniques to Know:

| Technique        | Description |
|------------------|-------------|
| **Shoulder Surfing** | Physically observing someone’s screen or keyboard to obtain credentials or sensitive data. |
| **Eavesdropping** | Listening to private conversations or electronic communications without consent. |
| **Dumpster Diving** | Retrieving confidential information from trash (e.g., shredded documents, receipts, hardware). |
| **Phishing** | Sending fake emails or links to trick users into giving up credentials. |
| **Vishing** | Voice phishing – impersonating someone over a phone call to extract data. |
| **Smishing** | SMS phishing – using text messages to trick users into clicking malicious links or revealing info. |

### 🔗 More Techniques:
- Pretexting (pretending to be someone)
- Tailgating (following someone into secure areas)
- Impersonation
- Baiting (leaving infected USBs)

---

## 🔧 5. Footprinting & Recon Tools

### 📌 FOCA (Fingerprinting Organizations with Collected Archives)
- Extracts metadata from public documents (PDFs, DOCX, etc.)
- Identifies usernames, folder paths, and software versions.

### 📌 OSINT Framework
- A collection of web-based tools and resources to aid in **open-source intelligence gathering**.
- Covers everything from social media to domain names.

🔗 [osintframework.com](https://osintframework.com)

### 📌 ReconDog
- All-in-one information gathering tool.
- Features include WHOIS, DNS, GeoIP, subdomain enumeration.

### 📌 Maltego
- Graph-based visualization tool for **link analysis**.
- Excellent for mapping relationships between people, groups, websites, etc.

### 📌 Recon-ng
- Full-featured reconnaissance framework similar to Metasploit.
- Modular design, useful for OSINT gathering in structured workflows.

---

## 🛡️ 6. Footprinting and Reconnaissance Countermeasures

Organizations must implement **security controls and awareness measures** to reduce the success of footprinting and social engineering attacks.

### 🔐 Recommended Countermeasures:

- **Strict Security Policies**  
  Ensure uniform implementation of security protocols across departments.

- **Employee Training & Awareness**  
  Educate end users on phishing, social engineering, and suspicious activities.

- **Use of Privacy Services**  
  Use WHOIS protection/privacy shields for domains to hide registrant info.

- **Network Hardening**  
  Disable unnecessary DNS zone transfers and use firewall rules.

- **Encryption**  
  Use SSL/TLS for communications and data-at-rest encryption.

- **Authentication Controls**  
  Enforce MFA (multi-factor authentication) and strong password policies.

---

## 📚 Summary Table

| Section | Highlights |
|--------|------------|
| **WHOIS** | Retrieves domain registration data |
| **DNS** | Reveals domain structure, MX, and host records |
| **Zone Transfer** | Risk if misconfigured – exposes DNS zone |
| **Social Engineering** | Human manipulation: phishing, vishing, dumpster diving |
| **Tools** | FOCA, OSINT Framework, Maltego, Recon-ng |
| **Countermeasures** | Awareness, privacy tools, encryption, authentication |

---

## ✅ Tips for CEH Exam

- Understand **how** information is gathered and **why** it's dangerous.
- Focus on **real-world scenarios** (e.g., how attackers use WHOIS + LinkedIn + metadata).
- Learn the **commands/tools** and **how to defend** against them.
- Always think **ethically and legally** — hacking is allowed only with permission.

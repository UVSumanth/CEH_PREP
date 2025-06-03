
# Cyber Kill Chain – CEH Notes and Explanation

## 📘 What is the Cyber Kill Chain?

The Cyber Kill Chain is a framework developed by **Lockheed Martin** in 2011, based on a military concept. It maps the typical steps attackers take to successfully carry out a cyberattack. It is widely used in **incident response, threat hunting, and red teaming**.

### Why It's Important for CEH:
- Helps identify and break the attack lifecycle.
- Enhances understanding of adversary behavior.
- Aids in strengthening detection, prevention, and response strategies.

---

## 🔁 The 7 Phases of the Cyber Kill Chain

### 1. Reconnaissance
- Attackers collect information about the target via **OSINT** tools and social media.
- Tools: `theHarvester`, `Hunter.io`, `OSINT Framework`
- Goal: Identify vulnerabilities, contact details, infrastructure.

### 2. Weaponization
- Malware + Exploit = Payload
- Payload is crafted (e.g., Macro documents, infected USBs).
- Adversaries may buy pre-built payloads or develop their own.

### 3. Delivery
- Transmitting the payload via:
  - **Phishing emails**
  - **USB drops**
  - **Watering hole attacks**
- Example: Fake invoice email using spoofed domain.

### 4. Exploitation
- Attackers exploit vulnerabilities (0-days or known flaws).
- Gain access and possibly escalate privileges.
- Techniques: phishing links, macro-based files, social engineering.

### 5. Installation
- Malware is installed and persistence is established.
- Methods: Web shells, backdoors (e.g., Meterpreter), registry run keys.
- Timestomping may be used to evade forensic analysis.

### 6. Command & Control (C2)
- Establish remote communication with infected system.
- C2 Channels: HTTP/HTTPS (port 80/443), DNS tunneling.
- The attacker gains full control over the victim’s system.

### 7. Actions on Objectives
- Exfiltrate data, deploy ransomware, destroy systems, or spy.
- Final step where the attacker fulfills their mission.

---

## ⚠️ Limitations of Traditional Cyber Kill Chain

- Focuses primarily on **external threats** and **malware-based attacks**.
- Less effective against:
  - **Insider threats**
  - **Cloud attacks**
  - **File-less malware**
- **Not updated since 2011** – adversaries now use advanced TTPs (tactics, techniques, procedures).

---

## 🔄 Supplementary Frameworks

- **MITRE ATT&CK**: Real-world observed techniques, tactics, and tools.
- **Unified Kill Chain**: Integrates internal and external threats for better modeling.

---

## 🎯 Example: Kill Chain in Action (Scenario)

**Scenario**: "Megatron" attacks a financial company.

| Phase | Description |
|-------|-------------|
| **Reconnaissance** | Uses theHarvester and LinkedIn to find employee emails. |
| **Weaponization** | Buys a VBA macro-based ransomware payload on the Dark Web. |
| **Delivery** | Sends a phishing email to a finance employee spoofed as an invoice from a known vendor. |
| **Exploitation** | Employee opens the document and enables macros, executing the payload. |
| **Installation** | Installs a persistent Meterpreter backdoor, modifies registry keys. |
| **Command & Control** | Malware opens a C2 channel over HTTPS. |
| **Actions on Objectives** | Encrypts critical financial documents and demands Bitcoin ransom. |

---

## ✅ Final Takeaway

The Cyber Kill Chain is **essential for understanding and disrupting** adversary actions. While it has limitations, it provides a foundation for securing systems and building layered defenses. Combine it with **MITRE ATT&CK** and real-time threat intelligence for effective protection.

---
Make sure to complete below Rooms as well
>[Windows Local Persistence](https://tryhackme.com/room/windowslocalpersistence)

>[OWASP Top 10 - TryHackMe Room](https://tryhackme.com/room/owasptop10)

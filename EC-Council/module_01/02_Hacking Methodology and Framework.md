## 📘 CEH Hacking Methodology

A structured, step-by-step process to perform ethical hacking. Each phase represents a stage in an attacker's lifecycle:

1. **Footprinting and Reconnaissance**  
   Gathering as much information as possible about a target system to find ways to infiltrate it.

2. **Scanning**  
   Actively probing the target network or system to identify open ports, services, and potential vulnerabilities.

3. **Enumeration**  
   Extracting more detailed information about the network and its resources such as users, groups, shares, and services.

4. **Vulnerability Analysis**  
   Identifying known vulnerabilities in the target systems and mapping them to possible exploits.

5. **System Hacking**  
   The actual exploitation phase which includes:  
   - **Gaining Access**: Breaking into the system.  
   - **Escalating Privileges**: Moving from a low-level user to higher privileges.  
   - **Maintaining Access**: Creating backdoors or other persistent mechanisms.  
   - **Clearing Logs**: Removing traces of the attack.

---

## 🔁 Cyber Kill Chain Methodology

Developed by Lockheed Martin, this framework describes the phases of a targeted attack:

1. **Reconnaissance**  
   Attacker gathers intelligence about the target.

2. **Weaponization**  
   Pairing malware with a delivery method (e.g., phishing email with a malicious payload).

3. **Delivery**  
   Transmitting the weapon to the target (e.g., email, USB, or exploit).

4. **Exploitation**  
   Triggering the attack, exploiting a vulnerability.

5. **Installation**  
   Installing malware on the target system.

6. **Command and Control (C2)**  
   Establishing communication with the compromised host.

7. **Actions on Objectives**  
   Completing the attack goal (e.g., data exfiltration, sabotage).

---

## 🧠 Tactics, Techniques, and Procedures (TTPs)

- **Tactics**  
  The *why* of an attack. It represents the attacker’s overall objective or strategy.  
  *Example:* Persistence – keeping access to a compromised system.

- **Techniques**  
  The *how* of an attack. It is the general way an attacker achieves a tactic.  
  *Example:* Creating new user accounts to maintain access.

- **Procedures**  
  The *specific implementation*. The actual commands or scripts used.  
  *Example:* Using `net user hacker P@ssw0rd /add` to add a user in Windows.

---

## 🎯 Adversary Behavioral Identification

Common behavioral indicators:
- Internal Reconnaissance
- Use of PowerShell
- Unspecified Proxy Activities
- Use of Command-Line Interface
- Abnormal HTTP User Agent Strings
- Communication with Command and Control Servers
- Use of DNS Tunneling
- Web Shell Deployment
- Data Staging Activities

---

## 📌 Indicators of Compromise (IoCs)

Artifacts observed in network or operating system that indicate intrusion.

### Categories:
- **Network-based IoCs**: IP addresses, domain names, URLs
- **Host-based IoCs**: File hashes, registry changes, processes
- **Email-based IoCs**: Sender address, subject line, attachments
- **Behavior-based IoCs**: Anomalous login patterns, unusual activity

---

## 🧩 MITRE ATT&CK Framework

A globally accessible knowledge base of adversary tactics and techniques based on real-world observations.

- Organized by stages of an attack (e.g., Initial Access, Execution, Persistence)
- Helps in threat detection, red teaming, and defense strategy

🔗 [https://attack.mitre.org](https://attack.mitre.org)

---

## 💎 Diamond Model of Intrusion Analysis

A model for understanding intrusions through four core features:

1. **Adversary** – The attacker
2. **Infrastructure** – The systems used by the adversary
3. **Capability** – The tools or malware used
4. **Victim** – The target of the attack

These components are interconnected and help analysts correlate incidents and attribute attacks.

---

✅ **Understand how different models (CEH Methodology, Cyber Kill Chain, MITRE, Diamond) contribute to ethical hacking and threat analysis**

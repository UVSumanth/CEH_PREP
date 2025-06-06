OS Discovery/Banner Grabbing 
What It Does: Identifies the Operating System and service versions running on a target system to find potential vulnerabilities.
How It Works:
🔹 Active OS Discovery:
  - Sends crafted packets to the target and analyzes the response.
  - Tools like Nmap send TCP/UDP/ICMP probes and compare behavior (e.g., TTL, TCP window size, TCP flags).
  - Example: Nmap -O for OS detection.

🔹 Passive OS Discovery:
  - Listens to network traffic (sniffing) without sending packets.
  - Uses data like: TTL | Window Size | DF (Don’t Fragment) Bit | TOS (Type of Service)
  - Compares these values against a signature database to guess the OS.
🔹 Banner Grabbing:
  - Connects to services (e.g., FTP, HTTP) and reads their welcome messages or headers (banners).
  - Can be done with tools like Netcat, Telnet, Nmap, or curl.
Why It’s Used:
Real World (Defender):
 - Helps identify OS/platform risks in asset management.
 - Assists in patch management and network hardening.
Attacker Use:
 - Determines OS-specific vulnerabilities to craft targeted attacks.
 - Helps in planning exploits by identifying exact versions (e.g., Apache 2.4.49 = vulnerable to path traversal).
 - Passive OS fingerprinting allows stealth reconnaissance with minimal detection.

📌 Nmap Usage:
-O → OS detection
-sV → Service version detection
--script=banner → Banner grabbing
Tools: Telnet, Netcat, Wireshark (for passive)

---

How to Identify Target System OS 
What It Does: Determines the operating system running on a target machine by analyzing network packet characteristics.
How It Works:
- Analyzes specific fields in IP and TCP headers, especially:
 - TTL (Time to Live)
 - TCP Window Size
- Different OSs set default values for these fields, which help in fingerprinting.
Example Defaults:
OS	TTL	TCP Window Size
Linux	64	5840
Windows	128	65535
Cisco Router	255	4128
Solaris/AIX/FreeBSD	255	Varies
- Tools like Wireshark, Nmap, Unicornscan, and Nmap Scripting Engine can perform this analysis.
- Passive method: Sniff a packet using tools like Wireshark and match TTL/window size with known OS signatures.
Why It’s Used:
Real World (Defender):
- Used to inventory systems, check for outdated OSs, and verify configurations.
Attacker Use:
- Helps identify OS-specific vulnerabilities.
- Enables attackers to craft targeted exploits and choose the right payloads.
Note: Also works with IPv6 fingerprinting and is effective even without active scanning (if traffic is captured).

---

OS Discovery using Nmap & Unicornscan
What It Does: Identifies the Operating System of a target system by analyzing how it responds to specific network scans.
How It Works:
🔹 Using Nmap:
  - Performs active OS fingerprinting using crafted probes.
  - Analyzes fields like: TTL | Window size | TCP options | ICMP responses
 - Nmap command: nmap -O <target IP>
 - Zenmap option: -O
🔹 Using Unicornscan:
 - Sends scan to the target and checks TTL in response.
 - TTL value hints at OS type (e.g., 128 = Windows, 64 = Linux).
 - Command: unicornscan <target IP>
Why It’s Used:
Real World (Defender):
 - Helps in asset inventory, patch management, and OS-specific hardening.
Attacker Use:
 - Used for pre-exploit reconnaissance.
 - Helps select OS-specific vulnerabilities and payloads.
 - TTL-based fingerprinting is simple and quick.
Note: TTL alone is not 100% reliable—combine with other methods for accuracy.

---

OS Discovery using Nmap Script Engine
What It Does: Uses predefined or custom scripts in Nmap to detect the OS of a target system, often through protocols like SMB.
How It Works:
- Uses Nmap Scripting Engine (NSE) to run scripts during a scan.
- Script example: smb-os-discovery (collects OS info via SMB).
- Commands:
  - Default scripts: nmap -sC <target>
  - Custom script: nmap --script <script-name> <target>
Why It’s Used:
Real World (Defender):
 - Automates network inventory and system auditing.
 - Detects OS through authenticated methods like SMB.
Attacker Use:
 - Gathers accurate OS info using protocol-specific fingerprinting.
 - Helps attackers build target-specific exploits.
Note: NSE supports hundreds of scripts for scanning, enumeration, and exploitation.

---

OS Discovery using IPv6 Fingerprinting 
What It Does: Detects the Operating System of a target using IPv6-specific scanning techniques.
How It Works:
- Sends IPv6-based probes (18+ types) to target.
- Analyzes responses and compares them to OS fingerprint database.
- Uses probes like: S1–S6 (Sequence) | ICMPv6 echo (IE1, IE2) | Neighbor Solicitation | Node Info Query | UDP (U1) and TCP (T2–T7)
- Command: nmap -6 -O <target>
Why It’s Used:
Real World (Defender):
 - Helps detect IPv6-enabled systems that may go unnoticed.
 - Supports IPv6-only networks.
Attacker Use:
 - Finds OS in IPv6-enabled environments.
 - Less likely to be detected due to fewer monitoring rules for IPv6.
Note: Many networks overlook IPv6, making this a stealthy method.

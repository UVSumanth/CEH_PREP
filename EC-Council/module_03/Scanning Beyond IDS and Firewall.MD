Scanning Beyond IDS and Firewall
Various IDS/Firewall Evasion Techniques 

Packet Fragmentation
What It Does: Splits probe packets (e.g., SYN/FIN scans) into smaller fragments to bypass firewalls and IDS that inspect complete packets.
How It Works:
- Breaks a TCP header into multiple smaller packets (fragments).
- These fragments are sent one by one to the target.
- IDS/firewalls may ignore or fail to reassemble fragmented packets.
- Target host reassembles fragments into the full packet.
Common tools:
 - Nmap --mtu <size>
 - fragroute
📌 Often used with SYN/FIN scanning to evade detection.
Why It’s Used:
Real World (Defender):
 - Helps test IDS/firewall evasion capabilities.
 - Can check how systems handle fragmented traffic (stability, logging).
Attacker Use:
 - Evades detection by signature-based IDS.
 - Helps bypass packet filters that block complete TCP headers.
 - Used to avoid false positives and trigger fewer alerts.

---

Source Routing
What It Does: Allows the sender of an IP packet to specify the route it takes through the network, rather than letting each router choose the next hop.
How It Works:
- Source routing info is stored in the IP options field of the packet.
- Two types:
 - Strict Source Routing: Packet must follow the exact route specified.
 - Loose Source Routing: Packet must pass through specified routers but can take other hops in between.
- Attackers use this to bypass firewalls or IDS by avoiding filtered paths.
- Rarely used in modern networks due to security risks.
Why It’s Used:
Real World (Defender):
 - Used in some network diagnostics or legacy routing setups.
 - Generally disabled due to security concerns.
Attacker Use:
 - Forces packets through unmonitored or vulnerable routes.
 - Helps evade security controls like firewalls and intrusion detection systems.
 - Exploits misconfigured routers or legacy devices that still honor source routing.
Note: *** Most modern routers ignore or block source-routed packets.

---

Source Port Manipulation
What It Does: Fakes the source port of a packet to make it look like it’s coming from a trusted or commonly allowed port (e.g., HTTP or DNS) to bypass firewalls/IDS.
How It Works:
- Firewalls often trust traffic from well-known ports (e.g., 53 for DNS, 80 for HTTP).
- Attackers manipulate the source port of their packets to appear as if coming from these ports.
- Misconfigured firewalls may allow this traffic assuming it's legitimate.
- Tools like Nmap allow this with -g or --source-port option.
Why It’s Used:
Real World (Defender):
 - Helps test firewall misconfigurations.
 - Used in penetration testing to simulate evasive attacks.
Attacker Use:
 - Bypasses port-based filtering by spoofing trusted ports.
 - Useful in environments where only traffic from certain ports is allowed.
 - Often targets legacy or poorly configured firewalls.
Note: *** Modern firewalls with deep packet inspection can detect and block this technique.

---

IP Address Decoy 
What It Does: Hides the real attacker’s IP by mixing it with fake (decoy) IPs — making it harder for IDS/firewalls to detect the actual source of the scan.
How It Works:
- Sends scan traffic using multiple IP addresses (real + fake).
- Logs on the target system will show all decoy IPs, not just the attacker’s.
- Tools like Nmap support:
  - Random decoys: nmap -D RND:10 [target]
  - Manual decoys: nmap -D decoy1,decoy2,ME,decoy3 [target]
Why It’s Used:
Real World (Defender):
 - Used in red teaming to simulate stealthy attacker behavior.
 - Helps test IDS effectiveness against evasion techniques.
Attacker Use:
 - Evades detection/logging by confusing defenders.
 - Makes it hard to trace the real attacker from logs.
 - Useful during stealth reconnaissance and scanning.
Limitation: If the target uses response path tracing or advanced detection systems, it may still find the real IP. Also, using many decoys can slow down the scan.

---

IP Address Spoofing
What It Does: Fakes the source IP address of a packet to appear as if it’s coming from a trusted or different host.
How It Works:
- Attacker modifies the packet header to spoof a source IP.
- Target replies to the spoofed IP, not to the attacker.
- Commonly used in DoS attacks where replies flood the spoofed IP or exhaust target resources.
Tool Example: hping3 www.target.com -a 7.7.7.7 (spoofs IP 7.7.7.7)
Why It’s Used:
Real World:
 - Used in penetration testing to evaluate how firewalls handle source IP filtering.
Attacker Use:
 - Bypasses IP-based filters and weak IDS/firewall rules.
 - Performs DoS attacks (spoofed IP causes reply flood or timeout).
 - Helps avoid detection by hiding real IP.
Limitation:  Spoofed IP cannot complete TCP 3-way handshake, so it’s mostly used for stateless attacks like DoS.

---

MAC Address Spoofing
What It Does: Fakes the source MAC address of a device to bypass MAC-based filters on firewalls or switches.
How It Works:
- Attacker uses Nmap or other tools to send packets with a forged MAC.
- Packets appear to originate from a trusted MAC address.
Nmap Examples:
  - Random MAC: nmap -sT -Pn --spoof-mac 0 [target IP]
  - Vendor-specific: nmap -sT -Pn --spoof-mac Apple [target IP]
  - Manual MAC: nmap -sT -Pn --spoof-mac 00:11:22:33:44:55 [target IP]
Why It’s Used:
Real World:
 - Test if MAC filters on a network are properly enforced.
Attacker Use:
 - Evades MAC-based filtering on LANs.
 - Avoids detection by spoofing trusted vendor MACs.
 - Useful in wireless attacks or internal recon.
Limitation: MAC spoofing only works within the same network segment (LAN).

---

Creating Custom Packets
What It Does: Creates manually crafted network packets to bypass firewalls, IDS, or test security systems.
How It Works:
- Attackers use packet crafting tools (e.g., Colasoft Packet Builder, NetScanTools Pro) to customize fields like TCP flags, TTL, ports, etc.
- Can simulate legitimate traffic or send malformed packets that normal scanners don’t generate.
- These packets are then sent to the target at custom intervals, patterns, or in fragmented form.
Why It’s Used:
Real World (Defender):
 - Used for network testing, firewall auditing, and simulating attacks for assessment.
Attacker Use:
 - Helps evade detection systems (by sending fragmented/malformed/custom traffic).
 - Bypasses firewalls that block known scanning patterns.
 - Can launch DoS attacks or probe vulnerabilities not detectable with regular scans.
Example Tool: Colasoft Packet Builder
- GUI-based tool to build, edit, and send custom packets.
- Provides Decode Editor and Hex Editor for deep customization.
- Allows sending crafted packets in loops or with delay, useful for stealthy attacks.

---

Proxy Servers & Anonymizers 
What It Does: 
Helps attackers or users:
 - Hide their real IP address
 - Bypass firewalls, IDS/IPS
 - Access restricted or censored content
 - Surf the Internet anonymously
How It Works
- A proxy server receives your request → sends it to the destination server → then forwards the response back to you.
- Logs at the destination show the proxy's IP, not yours.
- Proxy chaining: uses multiple proxies to increase anonymity.
- Anonymizers act like advanced proxies — strip identity, encrypt data, and route via other countries/servers.
Why It's Used
Real-World Use
 - Protect internal networks (NAT, firewalls)
 - Content filtering (schools/orgs)
 - Bandwidth control
 - Anonymized research or data scraping
Attacker Use
 - Evade detection
 - Hide true source IP
 - Bypass geo-restrictions or corporate firewalls
 - Conduct scans or attacks anonymously
 - Chain proxies or use VPNs to avoid being traced
Common Tools
Proxy Tools
 - Proxy Switcher: Rotate between proxies
 - CyberGhost VPN: Masks IP, encrypts connection
 - Shadowsocks: Lightweight, secure proxy (good for mobile)
 - Burp Suite: Intercept and modify web traffic (also used in testing)

Anonymizers
 - Tor: Onion routing network for deep anonymity
 - Whonix: VM-based OS routing all traffic through Tor
 - Orbot (Mobile Tor), Psiphon Pro, Tails OS

Proxy vs. Anonymizer
Feature	Proxy	Anonymizer
Use case	Hides IP, controls access	Privacy & censorship bypass
Advanced routing	Manual or single proxy	Networked (Tor/I2P)
Encryption	Optional (HTTPS/SOCKS)	Often encrypted
Risk of trace	Medium	Low (multi-hop routing)

---

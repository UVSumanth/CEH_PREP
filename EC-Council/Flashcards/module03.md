### Network Scanning Concepts
| **Question (Front)**                                            | **Answer (Back)**                                                         |
| --------------------------------------------------------------- | ------------------------------------------------------------------------- |
| What are the three steps of the TCP Three-Way Handshake?        | SYN → SYN-ACK → ACK                                                       |
| What TCP flag is used to **gracefully** terminate a connection? | FIN                                                                       |
| What does the RST flag indicate in a TCP connection?            | It abruptly terminates the connection due to an error                     |
| What is the role of the PSH flag in TCP communication?          | It forces the system to deliver data immediately to the application layer |

---

### Network Scanning Tools
| **Term**             | **Definition**                                                                                     |
| -------------------- | -------------------------------------------------------------------------------------------------- |
| **Hping3 SYN Scan**  | Sends SYN packets to detect open ports without completing handshake; stealthier than full scan     |
| **ACK Scan**         | Used to analyze firewall rules; RST = port unfiltered, No response = port filtered or dropped      |
| **Metasploit**       | Post-recon tool used for crafting and delivering exploits and testing system vulnerabilities       |
| **NetScanTools Pro** | Tool used for passive info gathering like hostnames, email addresses, domain info, and IP scanning |

| **Flashcard Topic** | **Question**                                    | **Answer**                                                      |
| ------------------- | ----------------------------------------------- | ---------------------------------------------------------------- |
| Nmap                | What is Nmap used for in network scanning?      | Mapping hosts, open ports, services, OS detection. It's a general-purpose and foundational CEH tool.                             |
| Hping3 - SYN Scan   | What does a SYN scan do and why is it stealthy? | Sends SYN packets to identify open ports without completing the handshake (half-open scan), avoiding detection by IDS/firewalls. |
| Hping3 - ACK Scan   | How does an ACK scan help identify firewalls?   | Sends ACK packets; RST → port is unfiltered, no response → filtered/firewalled.                                                  |
| Mobile Tools        | How is Fing useful in a mobile environment?     | Identifies IPs, MACs, vendor details, performs pings, traceroutes, and scans specific ports (SSH, FTP, etc.).                    |

---

### Host Discovery
| **Question (Front)**                                            | **Answer (Back)**                                                         |
| --------------------------------------------------------------- | ------------------------------------------------------------------------- |
| What scan finds live hosts on LAN using MAC address replies?    | ARP Ping Scan                                                             |
| Which scan checks if a host is online by sending UDP packets (default port 40, 125)? | UDP Ping Scan                                        |
| Which scan uses Echo Request to check if a host is online?      | ICMP Echo Ping Scan                                                       |
| What scan checks a full subnet for live hosts using ICMP Echo Requests? | ICMP Echo Ping Sweep                                              |
| What ICMP scan checks if a host is alive by requesting its subnet mask? | ICMP Address Mask Ping Scan                                       |
|  What scan uses TCP SYN to check host status and ends with RST for stealth? | TCP SYN Ping Scan                                             |
| What scan sends an ACK to detect live hosts, expecting an RST reply? | TCP ACK Ping Scan                                                    |

---

### Port & Services Discovery
| **Question (Front)**                                            | **Answer (Back)**                                                         |
| --------------------------------------------------------------- | ------------------------------------------------------------------------- |
| Which scan uses TCP 3-way handshake and is most detectable?     | TCP Connect (Full Open) Scan                                              |
| What scan sends SYN and aborts with RST to stay stealthy?       | Stealth Scan (Half-Open / SYN Scan)                                       |
| What scan sends FIN/NULL/Xmas flags to detect open ports by avoiding replies? | Inverse TCP Flag Scan                                       |
| What scan uses FIN, URG, and PSH flags and expects no reply if port is open? |  Xmas Scan                                                   |
| What scan sends ACK and analyzes TTL or Window in RST to find port state? | ACK Flag Probe Scan                                             |





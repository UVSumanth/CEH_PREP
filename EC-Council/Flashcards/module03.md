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
| **Question (Front)**                                            | **Answer (Back)**                                 |
| --------------------------------------------------------------- | ------------------------------------------------  |
| Which scan uses TCP 3-way handshake and is most detectable?     | TCP Connect (Full Open) Scan                      |
| What scan sends SYN and aborts with RST to stay stealthy?       | Stealth Scan (Half-Open / SYN Scan)               |
| What scan sends FIN/NULL/Xmas flags to detect open ports by avoiding replies? | Inverse TCP Flag Scan               |
| What scan uses FIN, URG, and PSH flags and expects no reply if port is open? |  Xmas Scan                           |
| What scan sends ACK and analyzes TTL or Window in RST to find port state? | ACK Flag Probe Scan                     |
|What scan uses a zombie’s IP to stay anonymous and tracks IPID changes? | Idle/IPID Header Scan (-sI)                |
| What scan treats no reply as open,filtered and ICMP error as closed?   | UDP Scan (-sU)                             |
| What scan uses INIT chunk to check SCTP port status?               | SCTP INIT Scan (-sY)                           |
| What scan uses COOKIE ECHO and treats ABORT as closed, no response as open,filtered? |  SCTP COOKIE ECHO Scan (-sZ) |
| What scan finds UPnP-enabled devices using multicast queries?   |  SSDP Scan                                        |
| Which scan only lists IPs and hostnames without scanning?       |  List Scan (-sL)                                  |
| What Nmap scan is used to scan IPv6 addresses?                  |  IPv6 Scan (-6)                                   |
| What Nmap option is used for detecting service versions on open ports? | -sV (Service Version Discovery)            |
| Which Nmap option controls scan timing and aggressiveness?   |  -T (0 to 5)                                         |

---

### OS Discovery 
| **Question (Front)**                                            | **Answer (Back)**                                 |
| --------------------------------------------------------------- | --------------------------------------------------|
| What does active OS discovery rely on?                          | Sending packets and analyzing responses (Nmap -O) |
| What does passive OS discovery rely on?               | Capturing and analyzing network traffic (e.g., TTL, DF bit) |
| What is banner grabbing?                             | Reading welcome headers from services to identify OS/version |
| What two values are commonly used to identify the OS from network packets? |  TTL and TCP Window Size               |
| Which tool helps in passive OS detection by analyzing packet headers? |  Wireshark                                  |
| What Nmap option is used for OS discovery?                       |  -O                                              |
| In Unicornscan, what does a TTL of 128 suggest?                  | Target OS is likely Windows                      |
| What script in NSE is used to detect OS via SMB?                 | smb-os-discovery                                 |
| What Nmap options are used for IPv6 OS fingerprinting?           |  -6 -O                                           |

---

### Scanning Beyond IDS and Firewall
| **Question (Front)**                                            | **Answer (Back)**                                 |
| --------------------------------------------------------------- | --------------------------------------------------|
| What is the purpose of packet fragmentation in scanning? | To evade IDS/firewall detection by sending split TCP headers|
| Which tools support packet fragmentation?                | Nmap and fragroute                                       |
| What does source routing allow?               | Sender defines the route the packet takes through the network       |
| Why is source routing a security risk?        | It can bypass firewalls/IDS by taking attacker-defined paths        |
| What is source port manipulation?             | Spoofing a trusted source port to bypass firewall/IDS               |
| Which Nmap option sets the source port manually? | -g or --source-port                                              |
| What is the purpose of IP address decoy in scanning? | To hide the real scanning IP by using fake IPs               |
| Which Nmap option is used for IP address decoy?   |  -D                                                             |
| What is the key limitation of IP spoofing in TCP connections? | Cannot complete handshake                           |
| Which Nmap flag is used to spoof MAC addresses?               | --spoof-mac                                         |
| What is a major purpose of MAC address spoofing?              |     To bypass MAC-based filtering on LANs           | 
| What are packet crafting tools used for? | Creating and sending custom network packets to test or evade firewalls/IDS |
| Name a tool for creating custom packets                       | Colasoft Packet Builder                             |
| What does proxy chaining do?                | Increases anonymity by routing traffic through multiple proxy servers |
| Which tool routes all traffic through the Tor network?    | Whonix                                                  |
| What’s the main benefit of using an anonymizer in attacks? | Conceals real IP and identity to avoid tracing         |

---

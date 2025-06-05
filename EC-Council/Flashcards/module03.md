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



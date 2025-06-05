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


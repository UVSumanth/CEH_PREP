Host Discovery Scanning Techniques
Host Discovery is initial part of scanning to know active and alive host 

Host Discovery Techniques 

ARP Ping Scan 
What It Does: Identifies live (active) devices on a local network (IPv4) by sending ARP requests and checking who replies.
How It Works:
- Sends ARP request: “Who has this IP?”
- If a device is active, it replies with its MAC address | If no reply, it’s assumed inactive.
- Works at Layer 2 (Data Link Layer), bypassing firewall restrictions that may block ICMP.
- Nmap uses argument -PR for ARP scan
Why It’s Used:
Real World (Defender):
 - Network admins use it to map all connected devices on LAN, even if they block pings.
Attacker Use:
 - Attackers use it for host discovery in stealthy scans before launching further attacks.
 - Useful in restricted environments where ICMP is blocked but ARP is not.
NOTE:
- -sn is the Nmap command to disable the port scan. 
- you can use --disable-arp-ping.
  
---

UDP Ping Scan
What It Does: Sends UDP packets to a target to check if a host is online or responsive without using TCP or ICMP.
How It Works:
- Nmap sends a UDP packet (default port: 40, 125) to the target.
- If a UDP response is received, host is considered active.
- If host is offline, errors like "host unreachable" or "TTL exceeded" may be returned.
- Zenmap option: -PU
- Nmap default port can be changed during compile time using DEFAULT_UDP_PROBE_PORT_SPEC.
Why It’s Used:
Real World (Defender):
 - Used to discover active devices in networks where ICMP and TCP are blocked, but UDP is still open.
 - Helpful in environments with strict TCP filtering.
Attacker Use:
 - Bypasses TCP-based firewalls.
 - Used to find live hosts when other ping methods (ICMP/TCP) are blocked or filtered.
   
---

ICMP Echo Ping Scan
What It Does: Checks if a host is online by sending an ICMP Echo Request and waiting for an Echo Reply (like the classic "ping" command).
How It Works:
- Sends an ICMP Echo Request to the target.
- If the host is alive, it replies with an ICMP Echo Reply.
- No reply = host is offline or ICMP is blocked.
- Nmap option: -PE (ICMP Echo), -P (ping scan), Zenmap uses -PE.
Why It’s Used:
Real World (Defender):
 - Used to check host availability or test firewall filtering.
 - Helps in basic network troubleshooting and device discovery.
Attacker Use:
 - Used during reconnaissance to find live hosts before scanning for open ports.
 - Avoids more suspicious scans like TCP/UDP probes.
 - Note: Doesn’t work reliably on Windows broadcast addresses (due to TCP/IP stack behavior).
   
---

ICMP ECHO Ping Sweep
What It Does: Scans an entire network or subnet by sending ICMP Echo Requests to multiple IPs to identify which hosts are live/active.
How It Works:
- Sends ICMP Echo Request to each IP in a subnet.
- Live systems respond with ICMP Echo Reply.
- No reply = Host is offline or ICMP is blocked.
- Works like a "network roll call" – whoever replies is up.
- Tools like fping or Nmap (-PE + list of IPs) are used.
Why It’s Used:
Real World (Defender):
 - Helps admins map active devices across a network.
 - Used in network diagnostics and inventory management.
Attacker Use:
 - Used during reconnaissance to find all reachable devices.
 - Useful for creating a target list before launching deeper scans or attacks.
Note:
It’s slow and often blocked by firewalls.
Doesn’t work with broadcast address on Windows systems.

---

ICMP Timestamp Ping Scan
What It Does:
Sends an ICMP Timestamp Request to get the system time from the target. If a Timestamp Reply is received, the host is alive.
How It Works:
- Sends an ICMP Timestamp Request packet.
- Target replies with its system time in a Timestamp Reply.
- If a reply is received, host is active.
- Works even if ICMP Echo is blocked.
- Zenmap/Nmap option: -PP
Why It’s Used:
Real World (Defender):
 - Used for time synchronization between network devices.
 - Helpful in network time diagnostics.
Attacker Use:
 - Used to detect live hosts when traditional ping is blocked.
 - Can reveal time zone, OS behavior, or even uptime indirectly.
Note: Many systems disable timestamp replies for security, so results can vary.

---

ICMP Address Mask Ping Scan
What It Does: Sends an ICMP Address Mask Request to a host to retrieve its subnet mask. A reply confirms the host is alive.
How It Works:
- Sends an ICMP Address Mask Request.
- If the host responds with a mask reply, it is considered active.
- The response depends on host configuration.
- Zenmap/Nmap option: -PM
Why It’s Used:
Real World (Defender):
 - Rarely used, but can help in diagnosing subnet configuration issues.
 - Might assist in older network discovery tools.
Attacker Use:
 - Used to find live hosts when ICMP Echo is blocked.
 - Also reveals network configuration details like subnet mask, which helps in further network mapping.
Note: Many modern systems are configured to ignore this request for security reasons.

---

TCP SYN Ping Scan
What It Does: Sends a TCP SYN packet to check if a host is alive by initiating (but not completing) a connection.
How It Works:
- Sends a TCP SYN to a port (default: 80).
- If host is up, it replies with SYN-ACK.
- Attacker immediately sends RST to terminate the handshake.
- No actual session is created, keeping the scan stealthy.
- Nmap option: -PS<port> (e.g., -PS80, -PS22-25,80)
 Why It’s Used:
Real World (Defender):
 - Used by admins to test if a service (like a web server on port 80) is reachable and responsive.
 - Helps in network mapping or service monitoring.
Attacker Use:
 - Identifies live hosts and firewall rules without completing full TCP connections.
 - Leaves minimal logs, making it a stealthy host discovery method.
 - Can probe multiple ports in parallel, saving time and avoiding timeout errors.
Note - the logs are not recorded at the system or network level, enabling the attacker to leave no traces for detection.

---

TCP ACK Ping Scan
What It Does: Checks if a host is alive by sending a TCP ACK packet and waiting for a RST response.
How It Works:
- Sends an ACK packet to the target (default port: 80).
- No handshake is initiated.
- If host is up, it sends a RST (reset) packet back.
- RST = host is alive.
- Nmap option: -PA<port> (e.g., -PA80)
Why It’s Used:
Real World (Defender):
 - Rarely used in regular IT ops.
 - May help test firewall behavior for ACK responses.
Attacker Use:
 - Bypasses firewalls that block SYN scans, as ACK packets are less suspicious.
 - Helps find live hosts in stealth mode.
 - Often combined with SYN for better host detection.
Note: Firewalls often block SYN but allow ACK, so this method can be more effective in restricted environments.

---

Ping Sweep Tools
Angry IP Scanner
Angry IP Scanner pings each IP address to check if any of these addresses are live. Then, it optionally resolves hostnames, determines the MAC address, scans ports, etc.
Ping Sweep Tools
SolarWinds Engineer’s Toolset (https://www.solarwinds.com)
NetScanTools Pro (https://www.netscantools.com) Colasoft Ping Tool (https://www.colasoft.com) Visual Ping Tester (http://www.pingtester.net) OpUtils (https://www.manageengine.com)


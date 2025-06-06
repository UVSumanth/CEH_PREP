Port and Service Discovery 

Port Scanning Techniques - Categorization is based on the type of protocol used for communication in the network.

TCP Scan
TCP Connect/Full-Open Scan 
What It Does: Attempts to fully connect to a target port using the standard TCP 3-way handshake to check if the port is open.
How It Works:
- Sends SYN to the target port.
- If port is open, target replies with SYN+ACK.
- Scanner responds with ACK → connection is fully established.
- Then scanner sends RST to close the connection.
- Uses OS’s built-in connect() call.
- Nmap option: -sT
Why It’s Used:
Real World (Defender):
 - Used for accurate port status checking.
 - No need for root/admin privileges – works with standard user access.
 - Helps confirm firewall behavior or service availability.
Attacker Use:
 - Reliable for finding open ports/services.
 - Easy to detect and log, so not stealthy.
 - May be used in quick, non-root scans, or when stealth is not a concern.
Note: Logs are created on the target system, making it highly detectable.

---

Stealth Scan (Half-Open / SYN Scan) 
What It Does: Checks if a port is open or closed by sending a SYN but never completing the 3-way TCP handshake — making it “half-open” and stealthy.
How It Works:
- Sends SYN to target port.
- If port is open, target replies with SYN+ACK → scanner sends RST to abort.
- If port is closed, target replies with RST.
- No full connection is established.
- Nmap option: -sS
Why It’s Used:
Real World (Defender):
 - Used for testing ports without alerting applications.
 - Helps in silent monitoring and firewall rule validation.
Attacker Use:
 - Bypasses firewall logging and detection systems.
 - Appears like normal background traffic.
 - Often used in stealthy reconnaissance to map live services without detection.
Note: Considered one of the most popular and effective scanning techniques for attackers.

---

Inverse TCP Flag Scans (FIN, NULL, Xmas)
What It Does: Checks if a port is open or closed by sending non-standard TCP flag combinations (FIN, NULL, or Xmas).
These scans aim to avoid detection by firewalls and IDS.
How It Works:
- Sends a TCP packet with unusual flags:
- FIN Scan: only FIN flag set
- NULL Scan: no flags set
- Xmas Scan: FIN + URG + PSH flags set
If port is closed → Target replies with RST.
If port is open → No response is sent.
Based on RFC 793 behavior (mainly works on UNIX/BSD systems).
Why It’s Used:
Real World (Defender):
 - Rarely used by defenders. Might be simulated in penetration testing.
 - Helps test if firewall/IDS can detect stealth scans.
Attacker Use:
 - Used for stealthy port scanning — often bypasses firewall/IDS logs.
 - Helps identify open ports without triggering alerts.
 - Works well on UNIX/BSD targets but fails on Windows systems.
Note:
- Requires root/superuser privileges.
- Ineffective on Windows, which does not follow RFC 793 behavior.

---

Xmas Scan
What It Does: Sends a TCP packet with FIN, URG, and PSH flags set to check if a port is open or closed, while staying stealthy.
How It Works:
- Sends a TCP packet with FIN + URG + PSH flags ("lit up like a Christmas tree").
- If port is open → No response.
- If port is closed → Target replies with RST.
- Based on RFC 793 (works on UNIX/BSD systems, not on Windows).
- Nmap option: -sX
Why It’s Used:
Real World (Defender):
 - Rarely used in normal operations.
 - May be simulated by penetration testers to assess firewall or IDS evasion.
Attacker Use:
 - Used to bypass firewalls and IDS logs (no SYN sent).
 - Effective for stealthy scanning on UNIX-based systems.
 - Helps identify closed ports through RST responses.
Note:
- Fails on Windows systems → may falsely show all ports as open.
- Requires superuser/root access.

---

TCP Maimon Scan
What It Does: A stealthy scan using FIN/ACK flags to check if a port is open, closed, or filtered, mostly on BSD-based systems.
How It Works:
- Sends a TCP probe with FIN and ACK flags.
- If port is closed → Target sends RST.
- If port is open or filtered → No response (packet dropped).
- If ICMP unreachable is returned → Port is filtered.
- Nmap option: -sM
Why It’s Used:
Real World (Defender):
 - Not typically used operationally.
 - May be included in advanced pentesting to test IDS/firewall evasion.
Attacker Use:
 - Bypasses SYN-based detection mechanisms.
 - Useful on BSD systems where dropped packets = open ports.
 - Helps detect firewalls, filtering behavior, and open|filtered ports.
Note:
- Rare and system-specific.
- Most effective on UNIX/BSD-based targets.

---

ACK Flag Probe Scan
What It Does: Sends TCP ACK packets to detect whether a port is filtered, open, or closed by analyzing the response’s TTL or Window value in the returned RST packet.
How It Works:
- Send ACK packet to target port.
- If RST received → Analyze:
  - TTL-based:
    - TTL < 64 → Port is open
    - TTL ≥ 64 → Port is closed
  - Window-based:
    - Non-zero window → Port is open
    - Zero window → Port is closed
No response or ICMP unreachable → Port is filtered
Nmap options:
- -sA → ACK scan (to test firewall/filtering)
- -sW → Window scan
- --ttl → TTL-based analysis
Why It’s Used:
Real World (Defender):
 - Used to test firewall rules (especially stateful firewalls).
 - Helps detect if ports are filtered or unfiltered.
Attacker Use:
 - Stealthy way to detect filtering/firewalls.
 - Can sometimes detect open ports indirectly (via TTL or window).
 - Helps evade SYN-based firewall detection.
Note:
- Works mainly on systems using BSD-based TCP/IP stacks.
- Not reliable on modern OSs like Windows.
- Slow and used mostly for research or evasion.

---
## Idle/IPID Header Scan
What It Does: Performs a stealthy TCP port scan by spoofing another host's IP address (called a zombie) to scan the target without revealing the attacker’s IP.
How It Works:
- Choose a zombie (host with predictable global IPID behavior).
- Probe zombie's current IPID using a SYN+ACK (gets RST response with IPID).
- Send spoofed SYN to the target (spoofed to look like it came from zombie):
  - If target port is open, it replies SYN+ACK to zombie → zombie replies with RST → IPID increases by 1.
  - If port is closed, target sends RST → zombie remains idle → no IPID change.
- Probe zombie's IPID again:
  - If IPID increased by 2, port is open.
  - If IPID increased by 1, port is closed.
- Nmap option: -sI <zombie IP>
Why It’s Used:
Real World (Defender):
 - Not commonly used for defense but helpful in testing IDS evasion.
 - Can simulate stealth attacks to validate network monitoring.
Attacker Use:
 - Provides complete anonymity (target only sees zombie’s IP).
 - Bypasses firewalls/IDS because no traffic comes directly from the attacker.
 - Ideal for covert reconnaissance in highly monitored environments.
Note:
- Requires a suitable zombie host with predictable IPID behavior.
- Rare, but highly stealthy when executed correctly.

---

UDP Scan
What It Does: Scans for open or closed UDP ports on a target system without using a handshake, since UDP is connectionless.
How It Works:
- Sends a UDP packet to target port.
- If port is closed → Target usually replies with ICMP "Port Unreachable".
- If no reply → Port is open or filtered (because UDP doesn’t send acknowledgments).
- Nmap option: -sU
- Use -sV for version detection and -O for OS fingerprinting to get more info.
Why It’s Used:
Real World (Defender):
 - Helps detect open UDP services (e.g., DNS, SNMP, DHCP).
 - Often used to identify misconfigured or forgotten UDP services.
Attacker Use:
 - Used to find exposed UDP ports running vulnerable services.
 - Stealthier than TCP (less noisy, no handshake), but slower and less reliable.
 - Can be used to bypass TCP-focused firewalls.
Notes:
- Less efficient than TCP scans — open ports don’t respond, so attackers must retransmit and guess based on no replies.
- Requires root/privileged access to perform raw socket scans.

---

SCTP INIT Scan 
What It Does: Scans target ports using the SCTP protocol to detect whether ports are open, closed, or filtered, similar to TCP SYN scan but for SCTP-based services.
How It Works:
- Sends INIT chunk to start SCTP’s 4-way handshake:
- INIT → INIT+ACK → COOKIE-ECHO → COOKIE-ACK
- If port is open → receives INIT+ACK
- If port is closed → receives ABORT
- If no response or ICMP unreachable → port is filtered
- No full connection is made (half-open scan), making it stealthy
- Nmap option: -sY
Why It’s Used:
Real World (Defender):
 - Used to detect SCTP-based services, such as:
   - VoIP, IP telephony, SIGTRAN
 - Helpful in securing telecom and real-time apps using SCTP.
Attacker Use:
 - Identifies open SCTP ports with low detection risk
 - Bypasses many traditional TCP/UDP-based firewall rules
 - Useful when targeting telecom systems or VoIP infrastructure
Note:
- SCTP is less common than TCP/UDP, so often overlooked by security tools
- Requires network support for SCTP protocol

---

 SCTP COOKIE ECHO Scan
What It Does: Checks SCTP port status using the COOKIE ECHO chunk. Helps find closed ports while staying stealthier than INIT scans.
How It Works:
- Sends COOKIE ECHO chunk to the target port.
- If port is open → no response (packet silently dropped).
- If port is closed → ABORT chunk is returned.
- If no response or ICMP unreachable → port is open|filtered
- Nmap option: -sZ
Why It’s Used:
Real World (Defender):
 - Used to assess SCTP service exposure in VoIP, telecom, or signaling networks.
 - Helps identify closed ports with low noise.
Attacker Use:
- Bypasses basic firewalls (not blocked like INIT scans).
- Stealthier—harder to detect by non-advanced IDS.
- Useful for low-profile reconnaissance on SCTP-enabled systems.
Note: Cannot clearly tell between open and filtered ports — both result in no response.

---

SSDP Scan (Simple Service Discovery Protocol)
What It Does: Detects UPnP-enabled devices on a network and gathers their service details via multicast queries.
How It Works:
- Sends M-SEARCH requests via IPv4/IPv6 multicast.
- Devices using UPnP respond with service information.
- Attackers use tools like UPnP SSDP M-SEARCH to collect data.
Why It’s Used:
Real World (Defender):
 - Helps identify smart devices, IoT, or UPnP-enabled hosts.
 - Used to detect unintended network exposure.
Attacker Use:
 - Used to exploit UPnP vulnerabilities (e.g., DoS, buffer overflow).
 - Helps map internal services and bypass firewall protections if UPnP is open.
Note: Can sometimes work through firewalls, depending on config.

---

List Scan (-sL)
What It Does: Prints a list of target IPs/hostnames without performing any actual scan or ping.
How It Works:
- Generates list from input range.
- Performs reverse DNS lookup for each IP.
- Marks all hosts as "not scanned".
Why It’s Used:
Real World (Defender):
 - Used to verify target list before scanning.
 - Helps avoid syntax errors or scanning wrong IPs.
Attacker Use:
 - Helps plan scans without being detected.
 - Used to confirm naming info before launching actual probes.
Note: No packets sent = zero chance of detection.

---

IPv6 Scan
What It Does: Performs scanning on IPv6 addresses instead of IPv4 to discover live hosts or open ports in an IPv6-enabled network.
How It Works:
- Uses Nmap with the -6 option to scan IPv6 targets.
- Unlike IPv4, brute-force scanning is not feasible due to the huge address space (2⁶⁴ hosts per subnet).
- Attackers must harvest IPv6 addresses from:
- Logs, emails, DNS, or packet captures.
- Once IPv6 addresses are known, normal port scanning can proceed.
Why It’s Used:
Real World (Defender):
 - To verify if systems using IPv6 are exposed.
 - Checks for dual-stack configurations (IPv4 + IPv6).
 - Helps detect shadow services not visible via IPv4.
Attacker Use:
 - Attackers target known IPv6 addresses, not the entire range.
 - IPv6 services may be less protected or overlooked by security teams.
 - Used to scan email headers, DNS responses, or logs for valid IPv6 IPs to probe.
Note:  Random scanning of IPv6 space is impractical — takes millions of years to scan a full subnet blindly.

---

Service Version Discovery 
What It Does: Identifies the exact version of services running on open ports of a target system.
How It Works:
- Sends probes to open TCP/UDP ports using Nmap’s service-probes database.
- Matches the service response to a known banner or signature.
- Reports service name and version number (e.g., Apache 2.4.49).
- Nmap option: -sV
Why It’s Used:
Real World (Defender):
 - Helps assess software versions to find outdated or vulnerable services.
 - Useful in asset inventory and vulnerability management.
Attacker Use:
 - Helps find services running known vulnerabilities.
 - Used to map target systems and choose the right exploit or payload.
Note:
- Highly valuable for vulnerability scanning and exploit matching.
- Can be used after a basic port scan to get detailed intelligence.

---

 Nmap Scan Time Reduction Techniques 
What It Does: Helps speed up Nmap scans and improve efficiency without losing accuracy.
How It Works (Key Techniques):
- Omit Non-Critical Tests
  - Avoid deep scans (-A, -O, -sV, -sC) unless needed.
  - Use limited port ranges.
  - Skip DNS (-n) or host discovery (-Pn) when not required.
- Optimize Timing (-T0 to -T5)
  - Use faster modes like -T4 (aggressive) or -T5 (insane) for speed.
  - Slower modes like -T0 or -T1 for stealth.
- Separate UDP and TCP Scans
  - Scan UDP (-sU) separately — it's slower and more prone to ICMP rate-limiting.
- Use Latest Nmap Version
  - New versions include bug fixes, better algorithms, and faster performance.
- Parallel/Concurrent Scanning
  - Split targets into groups and scan in parallel.
- Scan from Inside the Network
  - Scans from internal network are faster and more reliable than external scans.
- Increase System Resources
  - Free up CPU and bandwidth for smoother scanning.
  - Use verbose mode (-v) to monitor performance.

---

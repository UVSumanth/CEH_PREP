### ICMP scan
## Purpose
- a simple method to find out if a host is online by sending a ping request and waiting for a reply
- The ICMP ping scan is used to check if a device (like a computer, router, or server) is alive or reachable on a network.
- It sends an ICMP Echo Request (like a "ping") to the target, and if the device is up, it replies with an ICMP Echo Reply.
## How the Scan Works
If the device is online, it replies with an Echo Reply just like the standard ping command would.  
```
Syntax - hping3 -1 <Target IP Address>
```
--ICMP or -1 argument could be used

---

### ACK scan 
If Ping does not work use ACK scan
## Purpose 
- determines existence of Firewall and understand how it’s filtering traffic | ACK scan helps you detect the presence of firewalls and how they might be filtering traffic without establishing a full connection
- Simple packet filters might allow ACK packets  to pass | as ACK is a TCP connection attempt
- Advanced firewalls will block these packets if no connection has been established
## How the ACK Scan Works
If a firewall exists, it might:
- Allow the ACK packet through and return an RST (reset) response if the port is open.
- Drop the packet entirely if the firewall blocks such traffic or the port is filtered.
If you don’t get a response, it could mean that either the host is behind a firewall or it's not responsive.
```
Syntax - hping3 -A -p 80 192.168.1.1
```

---

### UDP scan
In general Hping uses TCP as its default protocol.
## Purpose
- check if a UDP port on a device is open or closed
- UDP is a connectionless protocol, so no handshake, harder to detect.
## How the Scan Works
- If port is closed, will get an ICMP Port Unreachable message.
- If port is open, there will be no response (since UDP doesn’t establish connections).
```
Syntax -  hping3 -2 <Target IP> –p 80
```
--udp or -2 as the argument 

---

### SYN scan
## Purpose
- SYN Scan is a way to check which ports on a target are open or closed by sending SYN packets to a range of ports.
- It is a stealthy scan because it doesn’t complete the TCP handshake, making it harder for firewalls or IDS to detect.
## How the Scan Works
SYN packets are sent to the target
- Open port: If a port is open, the target will respond with a SYN-ACK.
- Closed port: If a port is closed, the target will respond with a RST (Reset) packet.
- It’s a quick way to identify open ports without establishing a full connection, making it less likely to be detected by firewalls and intrusion detection systems.
```
Syntax - hping3 -8 50-60 -S 10.0.0.25 -V [Enables verbose output, showing more details.]
```
Dont get confused with SYN Scan(--scan or -8) and SYN Flag(-S)
hping3 -8 192.168.1.100 -p 1-1000 -> would scan ports 1 to 1000 on the target and try to detect open ports based on the response to SYN packets.
hping3 -S 192.168.1.100 -p 80 -> just sends a SYN packet to port 80 of the target, and you’d analyze the response (SYN-ACK or RST) to determine if the port is open or closed.

---

### FIN, PUSH and URG scan
## purpose
- These scans use FIN, PUSH, and URG flags to send unusual TCP packets, testing how the target responds to packets
- This type of scan is often used to bypass firewalls or intrusion detection systems because these packets are less likely to trigger alarms.
## How It Works
- Open Port: No response will be received.
- Closed Port: You will get an RST (Reset) response, indicating the port is closed.
- FIN, PUSH, and URG scans use non-standard flags. If the port is open, it stays silent | if closed, you’ll get an RST response
```
Syntax - hping3 -F -P -U 10.0.0.25 -p 80
```

---

### SYN Flooding Attack 
## Purpose 
- employs TCP SYN flooding techniques using spoofed IP addresses to perform a DoS attack
## How it works
- the attacker sends a huge number of SYN packets (the first step of a TCP handshake) to the victim's port.
- The target system responds as if it's expecting a connection, but the attacker doesn't complete the handshake, causing the target to keep resources tied up, 
- eventually overloading the system and causing a Denial of Service (DoS).
```
Syntax - hping3 -S 192.168.1.1 -a 192.168.1.254 -p 22 --flood
```
-S: Sends SYN packets (start of the TCP handshake).
192.168.1.1: The target IP address (victim).
-a 192.168.1.254: Spoofs the source IP address (making it appear like it's coming from another machine).
-p 22: Targets port 22 (usually used for SSH).
--flood: Sends packets continuously and rapidly, overwhelming the target.

---

### Collecting Initial Sequence Number 
## Purpose 
- Initial Sequence Number (ISN) is a unique number used in TCP connections to keep track of the data being sent.
- useful for network security analysis, reconnaissance, or network troubleshooting.
- Collecting the ISN can provide useful information about the target system's TCP behavior, but it isn't always necessary for basic network operations or common security scans.
-  It is more crucial in situations like session hijacking, where an attacker needs to predict and inject valid TCP packets into an ongoing session.
- TCP Session Hijacking, Reconnaissance and Network Troubleshooting
```
Syntax - hping3 192.168.1.103 -Q -p 139
```
argument -Q tells hping3 to collect the ISN

---

### Scan entire subnet for live host
- This command  hping3 -1 10.0.1.x --rand-dest –I eth0 is used to scan an entire subnet for live hosts by sending randomized ICMP requests across the subnet (10.0.1.0/24) on the eth0 interface. 
- The randomization of the destination IPs helps to evade detection and bypass security measures such as firewalls and intrusion detection systems that might look for predictable scanning patterns.
- The scan checks for active hosts that respond with ICMP Echo Replies, without targeting specific services or ports.

### Intercept all traffic containing HTTP signature
- The -9 argument in hping3 puts the tool in listen mode, and when combined with the HTTP signature, it allows for the interception of all packets containing HTTP traffic. 
- This enables monitoring of HTTP packets flowing across the network connected to the eth0 interface. It’s useful for traffic analysis and network monitoring.
